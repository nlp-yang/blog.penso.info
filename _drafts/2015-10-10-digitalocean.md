--- 
layout: post
title: "Which Droplet should you get at DigitalOcean?"
categories: 
- computer
description: I've just acquired
---
TL;DR — ** Bla **

I've recently joined [Cloudscreener](http://www.cloudscreener.com) as the CTO.
We benchmark public cloud providers, and look at what CPU/RAM/IO performance
you get from each instance types, and what ratio (bang for your buck) you get
for each of them.

I own an iOS application named [Faast](http://www.faast.io) which is like a RSS
reader, and I have online servers to fetch feeds and process other stuff. A
year ago, and since the creation of this application, I was using bare metal
servers [^1] for about €3,400 per year from my own pocket. That was expensive (the
app doesn't make money but since I use it daily I keep it online), but I
thought all my side projects (like this blog) would benefit from faster
servers. This was a 2008 way of thinking.

In 2015 you shouldn't think like this, spawning servers on the cloud has never
been easier as you can create new instances within seconds, and if you think it
will be more expensive you're wrong. I've personnaly selected
[DigitalOcean](http://www.digitalocean.com) as my cloud hosting, since their
ratio benchmark/price are one of the bests.

Since April 2015 I've lowered the price of my hosting to €1,700 (half
cheaper!), with comparable performances. Recently I've looked at my instance
type choice again at DigitalOcean, and I've found out I should actually switch
from the bigger instances to the smallest one. The following graph shows you
the best bang for your buck as a yellow line, the blue chart being the
performance you get. If you are able to move to multiple servers with queue
processing (I use sidekiq) then I highly recommend you rethinking your choice.

* * *

[^1]: Two servers with 8 Xeon CPUs and 32G of RAM, and SSD drives
[^2]: I'm using 5 servers, 3 4GB and 2 2GB ones.
