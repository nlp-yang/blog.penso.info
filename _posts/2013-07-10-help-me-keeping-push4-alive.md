--- 
layout: post
title: Help me keeping Push4 alive
categories: 
- computer
description: I started Push4 in 2009 and I need your help to keep it alive on the AppStore.
photo_social: http://blog.penso.info/img/push4_ios7.png
---

#### Short version

<a
href="https://docs.google.com/forms/d/1PNpQBckxJOMt9jpjC_hoDnypPiqaR6FWhwrUlKd2Msw/viewform"
target="_new">Fill up this form</a> and help me finding out if I should sunset
[Push4](http://2apn.com) or not. I'm trying to find out if spending months of
my life for an iOS7 rewrite, and lots of time the next years, is a good idea. I
don't want to create a [KickStarter](http://www.kickstarter.com/) campaign
about this, and I'm based in France anyway. I just want to see how excited
you'd be about this.

If there isn't enough people willing to pay monthly for such an application,
I'll remove it from the AppStore.

#### Long version

2009, I started working on what is now named [Push4](http://2apn.com) but, 
at the time, was simply called *AppNotifications*. An iOS Push Notification
application to receive push for Twitter, RSS, Email and even use an API. This
app has about 60,000 total users[^1] and was even listed in
the [Top 100 Feed & RSS Technologies of
2011](http://readwrite.com/2011/12/18/top_10_feed_rss_technologies_of_2011).

I've always cared about my users, trying to make everyone happy. But running
this app is costly (server) and involves a lot of my time. It's a niche market,
and everyone who tried to do something similar failed so far. I feel it's both
because it's a niche market, and because most users don't care about
paying for such feature. It's also technically very difficult to implement
well[^2].

The release of iOS7 will make a lot of existing iOS apps at minimum ugly and
sometimes even useless. [Push4](http://2apn.com) isn't immune to this, and
require a complete rewrite if I want to keep it live for the upcoming years.
The current code includes a client side (the iOS app itself), and a server
side. Both now require profound updates, and the client side even requires a
complete rewrite for iOS7. 

You probably use the app for years, and you're very aware of how useful it can
be for your daily routine. I am very excited about working a complete rewrite,
but it's **months of full time work**, and unless you are willing to be charged
per month for the cost of running servers, there is just no point for me to do
it.

Help me finding out about this. <a
href="https://docs.google.com/forms/d/1PNpQBckxJOMt9jpjC_hoDnypPiqaR6FWhwrUlKd2Msw/viewform" target="_new">Fill
up this form</a> and let me know if, based on your current use, you would be
willing to have a recurrent monthly payment to keep using it. If enough people
are interested about an iOS7 focused version of [Push4](http://2apn.com), I
will work full time on it and will fix all existing issues and add features
like:

* iOS7 compatible UI
* Using native iOS Twitter account
* Not having to restart the app anymore
* Background fetching of articles, you get them right away when approving the push
* Easier settings
* Focus even more on real time, more pubsub hubs and more frequent RSS updates for pulls
* Better layout for reading articles
* Super fast app when using it


* * * 

#### Early screenshot of an iOS7 prototype for Push4

![iOS7 screenshot](/img/push4_ios7.png)

* * * 

If you liked this post, drop me a note at
[@fabienpenso](http://twitter.com/fabienpenso). If you didn't, drop me a note
anyway telling me how to improve it.

You can stay up to date via [my RSS feed](/atom.xml).

Thanks for reading.

[^1]: But much less active, and that includes a high purcentage of Hackers who never paid for it. The first weeks I had 99.8% of Hackers!
[^2]: Try fetching 50,000 RSS feeds every 10 minutes with low CPU resources and you'll understand.
[^3]: I actually already [asked this](http://appnotifications.tumblr.com/post/42681775228/should-i-remove-push4-from-the-appstore-or-continue).
