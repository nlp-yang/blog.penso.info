---
layout: post
title: Capistrano deployment and rainbows support
date: 2013-05-12
categories:
- computer
description: Capistrano deployment and rainbows support
---
Deploying using Capistrano and rainbows is almost trouble free, include the
following in your deploy.rb:

{% highlight ruby %}
require 'capistrano-unicorn'
set :unicorn_bin, "rainbows"
{% endhighlight %}

Make sure your `Gemfile` includes `gem 'capistrano-unicorn'`, and you have to
make sure you created a settings file in `config/unicorn/production.rb` (yes, a
unicorn directory).

#### Update 29th May, 2013

[A patch](https://github.com/sosedoff/capistrano-unicorn/commit/8b9104066980e9a19a4654865382a77e460f5737) applied to `capistrano-unicorn` today allows you to specify the
configuration file, you can use for capistrano-unicorn ~> 0.1.9:

{% highlight ruby %}
set :unicorn_config_filename, 'rainbows/production.rb'
{% endhighlight %}

#### Configuration file

Mine includes using EventMachine, as I want an async stack for using
`sinatra-sse`.

{% highlight ruby %}
# rainbows/production.rb
Rainbows! do
  use :EventMachine
  worker_connections 1024
end
worker_processes 5

app_directory = '/www/app'

working_directory "#{app_directory}/current"

listen "unix:#{app_directory}/shared/unicorn.sock", :backlog => 2048

timeout 600

preload_app true

pid "#{app_directory}/shared/pids/unicorn.pid"

stderr_path "#{app_directory}/shared/log/unicorn.stderr.log"
stdout_path "#{app_directory}/shared/log/unicorn.stdout.log"

if GC.respond_to?(:copy_on_write_friendly=)
  GC.copy_on_write_friendly = true
end

before_fork do |server, worker|
  old_pid = "#{app_directory}/shared/pids/unicorn.pid.oldbin"
  if File.exists?(old_pid) && server.pid != old_pid
    begin
      Process.kill("QUIT", File.read(old_pid).to_i)
    rescue Errno::ENOENT, Errno::ESRCH
      # someone else did our job for us
    end
  end
  # the following is recomended for Rails + "preload_app true"
  # as there's no need for the master process to hold a connection
  if defined?(ActiveRecord::Base)
    ActiveRecord::Base.connection.disconnect!
  end
end

after_fork do |server, worker|
  # see http://petelacey.tumblr.com/post/3073967460/on-forking-application-servers-and-memcached-in-rails
  ActiveRecord::Base.establish_connection if defined?(ActiveRecord::Base)
end
{% endhighlight %}
