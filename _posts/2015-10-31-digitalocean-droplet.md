--- 
layout: post
title: "Which Droplet should you get at DigitalOcean?"
categories: 
- computer
description: I've just acquired
author: Fabien Penso
date: 2015-10-31 17:00:00 +02:00
photo: http://blog.penso.info/img/digitalocean.png
---
TL;DR — **If you think paying more at DigitalOcean gets you more CPU or IO,
think again. The 512M instance gets you the most bang for your bucks, as I'm
going to show you in this article. It's actually also the best virtual server 
price/performance wise within multiple providers as long as you can manage the
512M of RAM and the disk size.**

Disclaimer: this post **has not** been sponsored by DigitalOcean, and I don't get
paid for it. I'm only giving informations about what I noticed using
[Cloudscreener](http://www.cloudscreener.com) products.

I've recently joined [Cloudscreener](http://www.cloudscreener.com) as the CTO.
We benchmark public cloud providers, look at what CPU/RAM/IO performance you
get from each instance types, and what ratio (bang for your buck) you get for
each of them. We do this on 12 public providers, on multiple regions and most
instance types. Our product isn't publicly available yet, but you can get early
access visiting
[our product page](https://www.cloudscreenerapp.com/benchmark) and registering
for free.  At the time of this blog post, this is not fully optimized and you
may experience slow page loading. I suggest trying later or waiting we optimize
it within the next week.

#### Context

I own an iOS application named [Faast](http://www.faast.io) which is like a RSS
reader so I have online servers to fetch feeds and process other stuff to
deliver pushes to my users. Since the creation of this application (about 2009)
and in general for all my side projects, I was using bare metal servers[^1] for
about €3,400 per year. Those would be upgraded every 2 years or so for the same
cost. That is expensive, the app doesn't generate revenue and I keep it online only
because I use it myself. I also thought all my side projects (like this blog)
would benefit from faster servers.

**This is a *2008* way of thinking: fewer servers, fast servers. It's easier to
maintain as a solo developer, and I don't have to install/configure them on a
regular basis. Don't think like this today, we're in 2015 and things changed a
lot.**

#### Today

In 2015 spawning servers on the cloud has never been easier. The spawning time for Amazon [takes about 60sec](https://www.cloudscreenerapp.com/benchmark#%7B%22type%22%3A%22api%22%2C%22since%22%3A30%2C%22filter%22%3A%5B%22provider%3Aamazon-web-services%22%5D%7D) in average, [Google 40sec](https://www.cloudscreenerapp.com/benchmark#%7B%22type%22%3A%22api%22%2C%22since%22%3A30%2C%22filter%22%3A%5B%22provider%3Agoogle-compute-engine%22%5D%7D) and [DigitalOcean 120sec](https://www.cloudscreenerapp.com/benchmark#%7B%22type%22%3A%22api%22%2C%22since%22%3A30%2C%22filter%22%3A%5B%22provider%3Agoogle-compute-engine%22%5D%7D). Provision them automatically with tools like
[Ansible](http://www.ansible.com) is really easy, and I even have friends and coworkers using Ansible to provision their
daily Linux development laptop (some Facebook employees). I usually keep my
[ansible playbooks](http://docs.ansible.com/ansible/playbooks_intro.html)
within the same repository as my app.

[Ansible](http://www.ansible.com) runs from your own laptop, it doesn't need a
*master* server to pull recipes from. It will also help you to move/reinstall
your code on other servers if you wanted to change them later on. Even if you
use *Chef* or *Puppet* you should look at it. [Ansible](http://www.ansible.com)
has recently been acquired by
[Redhat](https://www.redhat.com/en/about/blog/why-red-hat-acquired-ansible) and
is here to stay. It is of course open source.

If you think using public cloud servers will be more expensive you're wrong.
I've personnaly selected [DigitalOcean](http://www.digitalocean.com) as my
cloud hosting, since their ratio benchmark/price are one of the bests, and I
saved a lot of money...

#### How much did I save?

Since April 2015 I've lowered the price of my hosting to €1,700 (half
cheaper!), with comparable performances[^2]. I then looked at my instance
types choice again, and I've found out I should actually switch
from the bigger instances to the smallest one. I've moved to €1,300 and I think
I should be able to save more when I figured out how to make
[Rails](http://www.rubyonrails.org) use less memory. That's €2,100 euros a year
I saved on my server spending[^3] (or 60% of my cost), and I believe you can
achieve similar results yourself.

Try it looking at the graph at the top of this page shows you the best bang for
your buck as a yellow line, the blue chart being the performance you get. You
can also use our [online product](https://www.cloudscreenerapp.com/benchmark).

#### Amazon

[Amazon](http://aws.amazon.com) is of course a very popular choice for public
clouds. They have a lot of managed services, and they allow you to move faster
with your product instead of spending time to manage them yourself (MySQL
servers, DynamoDB, etc). But how do you decide which VM you should be using?

The following graph shows all instances with 2 vcpus maximum. Looking at the
yellow line, you'll notice you can have a 10x price/performance ratio. Using
smaller servers is usually better, and the t2.small instances are really good.[^4]

<a href="/img/cloudscreener-amazon.png" target="_new"><img src="/img/cloudscreener-amazon.png" alt="Amazon servers" /></a>

If you are able to move to multiple servers with queue processing (I use
[sidekiq](http://www.sidekiq.org)) then I highly recommend you rethinking your
choices and move to smaller instances.

* * *

Well this blog post became much longer than I expected, I hope you found it
useful. If you did, drop me a note at
[@fabienpenso](http://twitter.com/fabienpenso). If you didn't, drop me a note
anyway telling me how to improve it.

You can stay up to date via [my RSS feed](/atom.xml).

Thanks for reading.

[^1]: Two servers with 8 Xeon CPUs and 32G of RAM, and SSD drives.
[^2]: I'm now using 5 digitalocean droplets, 3x4GB and 2x2GB.
[^3]: With the same performance and my users noticed no changes.
[^4]: However they have limitations, see [this page](https://aws.amazon.com/ec2/instance-types/t2/)
