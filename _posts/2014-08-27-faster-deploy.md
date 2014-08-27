--- 
layout: post
title: Faster capistrano deploys
categories: 
- computer
description: Faster capistrano deploys
---

TL;DR — **I reduced deploy times from five minutes to less than fifteen
seconds by replacing the standard Capistrano deploy tasks with a simpler,
Git-based workflow and avoiding slow, unnecessary work.**[^1]

I worked on this deploy recipes while working for
[@mickael](http://twitter.com/mickael) from
[ProcessOne](http://www.process-one.net/en/). If you enjoy challenges and look
for a Ruby job, you should talk to us.

I've recently went from 5 minutes to about 15 seconds for my deploys. That
feels much better... Spending minutes (or longer) for deploying a regular Rails
application was pissing me off, I want to deploy within seconds. [This great
article](http://blog.codeclimate.com/blog/2013/10/02/high-speed-rails-deploys-with-git/)
from Code Climate convinced me I should just change the way capistrano works,
and do it my own way.

What I thought would take me a few hours work ended up taking me days of full
time work, and a lot of hassles. I first looked at
[recap](http://gofreerange.com/recap/docs/recap.html), but it's based on
capistrano2, looked at [mina](http://nadarei.co/mina/) but it's single host
based. [Fabric](http://www.fabfile.org/) seems nice but I didn't feel like it
either.

I ended up using [capistrano3](http://capistranorb.com/) and tweaking it a lot.
What capistrano now really is is a bunch of gems combined, the most important
being [sshkit](https://github.com/capistrano/sshkit).

The benefit of keeping capistrano3 while doing your own way is you get all the
capistrano3 plugins. The downside is you must be extra careful when adding any.
One example amongs many is
[capistrano-rails](https://github.com/capistrano/rails/), it runs `rake
db:migrate` on your server for every single deploy, even you don't need to run
it. That task alone takes at least 4 seconds (loading the rails stack), even
you don't need it for most of your deploys. It also run
`deploy:assets:precompile` every time, boom goes for another 4 seconds. You've
just lost 8 seconds looking at your console for no reason.

Another issue with `capistrano3` is the way it manages `git`, it doesn't keep
the `.git` subdirectory, it caches a local clone and copies files on deploy.
That's slower, but it also means I can't edit files on server to _try things
out_ quickly and use `git diff` to view my changes.[^2]

What I want for my deploys:

 - git based
 - done within seconds, not minutes
 - being able to rollback
 - locks, should prevent multiple deploys at once

What I found was slowing the deploys with capistrano2:

 - Everytime you run a remote rails task, it takes 4 to 5 seconds to just load
	 the Rails stack. `rake db:migrate` even you don't need to? 5 seconds extras,
	 `rake assets:precompile`? here goes another 5 seconds, etc.
 - Every `run` you use does a single SSH connection, and capistrano 2 doesn't
	 have a `connection_pool`. It's easy to forget about that, add `run` commands,
	 and end up with a minute spent connecting new ssh connections. I suggest
	 upgrading to `capistrano3` and `sshkit` just for that connection_pool feature. I
	 was looping to do extra `ln` for multiple files and each one would take an
	 extra second.
 - On my setup, compiling assets on the server side is painfully slow.
	 Compiling on my laptop and using `rsync` to copy the compiled files remotely
	 vastly improved speed.
 - Remote assets compilation was broken, it wasn't using the cache directory
	 and would be rerun for every deploys.
 - Be extra careful about your assets, try to make them small instead of just
	 using `require_tree .` or `@import`. I suggest you use public CDN for known
	 projects like jQuery, Bootstrap, etc. It will be faster for your website too.
 - Using an old `sidekiq` way to restart was slow, it would also load the
	 Rails stack, I've moved that to using an instant `kill -USR1` and you can benefit from
	 it as [my
	 patch](https://github.com/seuros/capistrano-sidekiq/commit/03d3ba127508064cbeb596c54ffc8f6af7029aa9)
	 is now included in
	 [capistrano-sidekiq](https://github.com/seuros/capistrano-sidekiq) since
	 0.2.7. Just use `set :sidekiq_use_signals, true` in your deploy file.

What my new deploys do:

 - Create a lock file on the server for not running multiple deploys at once
 - Quiet sidekiq
 - Fetch the git repo, and checkout the proper commit
 - Check if bundle install is required, if yes run it
 - Check if asset compilation is required, if yes run it
 - Check if migration is required, if yes run it
 - Check if whenever crontab should be changed, if yes run it
 - Tag the local git repo to view past deploys, but doesn't push those tags back to the git server
 - Restart rainbows/unicorn/puma
 - Stop sidekiq (gets started by `monit`)
 - Remove the lock

My new deploys now take 20 seconds or less:

	$ time cap staging deploy
	INFO [c3948833] Running /usr/bin/env [ ! -e /<deploy_dir>/shared/.deploy-lock ] && echo 'Deploying at 2014/04/28 18:00:39 by penso' > /<deploy_dir>/shared/.deploy-lock on <host>
	INFO [c3948833] Finished in 0.228 seconds with exit status 0 (successful).
	INFO Currently deployed: 67ca6a8df804efb1944c8f6df835767fffa20e63 tag: deploy-20140428170118 Deployed at 2014/04/28 17:01:18 by penso
	INFO Deploying 67ca6a8df804efb1944c8f6df835767fffa20e63
	INFO [28edf818] Running /usr/bin/env kill -USR1 `cat /<deploy_dir>/shared/pids/sidekiq.pid` on <host>
	INFO [28edf818] Finished in 0.231 seconds with exit status 0 (successful).
	INFO [87854387] Running /usr/bin/env git fetch on <host>
	INFO [87854387] Finished in 0.945 seconds with exit status 0 (successful).
	INFO [801f90f1] Running /usr/bin/env git reset --hard 67ca6a8df804efb1944c8f6df835767fffa20e63 on <host>
	INFO [801f90f1] Finished in 0.265 seconds with exit status 0 (successful).
	INFO No bundle install needed
	INFO No asset compilation needed
	INFO No migration needed
	INFO No whenever set needed
	INFO Not tagging deployed repository: same commit
	INFO rainbows is running...
	INFO rainbows restarting...
	INFO [9d09a00f] Running /usr/bin/env kill -s USR2 `cat /<deploy_dir>/shared/pids/unicorn.pid` on <host>
	INFO [9d09a00f] Finished in 0.230 seconds with exit status 0 (successful).
	INFO [18234646] Running /usr/bin/env sleep 3 on <host>
	INFO [18234646] Finished in 3.237 seconds with exit status 0 (successful).
	INFO [965de68b] Running /usr/bin/env kill -s QUIT `cat /<deploy_dir>/shared/pids/unicorn.pid.oldbin` on <host>
	INFO [965de68b] Finished in 0.266 seconds with exit status 0 (successful).
	INFO [620a7e3f] Running /usr/bin/env kill -TERM `cat /<deploy_dir>/shared/pids/sidekiq.pid` on <host>
	INFO [620a7e3f] Finished in 0.236 seconds with exit status 0 (successful).
	INFO [e2024f60] Running /usr/bin/env rm /<deploy_dir>/shared/.deploy-lock on <host>
	INFO [e2024f60] Finished in 0.233 seconds with exit status 0 (successful).
	
	cap staging deploy  2.30s user 0.48s system 13% cpu 20.099 total


I have not published any code but might if enough people is interested. I've
just wrote my set of capistrano tasks and replaced the default `cap deploy` using


	Rake::Task["deploy:rollback"].clear rescue nil

	namespace :deploy do
	  desc "Update"
	  task :update_code do
	    # Do your own set of rules
	  end
	end

	# Replacing the default cap deploy task
	Rake::Task["deploy"].clear rescue nil
	desc 'Deploy current version'
	task :deploy do
	  invoke "deploy:update_code"
	end

* * * *

You can stay up to date via [my RSS feed](/atom.xml).

Thanks for reading.

[^1]: This quote is stolen from [this great article](http://blog.codeclimate.com/blog/2013/10/02/high-speed-rails-deploys-with-git/) from [Code Climate](http://www.codeclimate.com/). It's also the article who convinced me to do the same way they did, except they used capistrano2 and I used capistrano3
[^2]: I know, I know. You shouldn't do that but sometimes you need to anyway, or you're just modifying files on your staging servers.
