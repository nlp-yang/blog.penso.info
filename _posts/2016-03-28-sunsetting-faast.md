--- 
layout: post
title: Sunsetting Faast
categories: 
- computer
description: Faast is an iOS app to receive push notification from Twitter, Facebook, RSS Feeds and more
photo: /img/faast_icon.png
---

TL;DR — **I've decided to sunset [Faast](http://www.faast.io), the Push app
I've been running for years.  Expect it to stop working within weeks, probably
by the end of April. I'll switch to using [Reeder](http://reederapp.com) myself
for my RSS feeds, I didn't find anything for push.**

[Faast](http://www.faast.io) is a push application I've created years ago, with
its previous version Push4 back to 2009. The Appstore has changed a lot since,
and you've probably already read many blog posts from indie developers saying
they can't make a living from it. That's true now more than ever, and the only
sustainable way to be an iOS developer full time is to freelance for other
bigger brands (I'm glad I don't have to do that, I've been a CTO for various
projects for years).

I've been running Faast at my loss for years, mostly because I use it daily. The
difference between Faast and most other mobile apps is it required servers, and
those are very expensive to run. They gathered RSS feeds, tweets and emails for
you, and sent pushes through Apple Push Notification servers. Faast had a
specific case: it required high server-wise skills, and high frontend-wise
skills as well. I know both sides, but it still involves way too much work and
[Apple](http://www.apple.com) makes it hard for developers. You have to spend
time every year to update your app, add features and make sure new iOS releases
don't break your app.

AppStore users aren't willing to pay for products any more, unless it includes
candies and expensive in-app purchases for skipping levels. They don't
understand how difficult it is to write an application like Faast, and they
complain very easily without remembering the app developer is a real Human, who
they don't need to threat. I'm happy to be out of the Apple Appstore too. 

I'd like to publicly thanks [K. Payandeh](http://twitter.com/kavehpd) who
designed the Application icon and helped so much about the design. I love this
icon and I'm sad to see it go, it felt like part of my iPhone for so long.

# Faast servers and technologies

Server wise, Faast used 12 servers (used to be on 2 but I switch back to more
smaller servers) and its monthly cost went from €350 per month to about €160
recently, but I'd expect most other developers to pay more than that. I've
optimized them a lot.

A lot of technologies were involved in Faast, like:

* [PubSubHubBub](https://en.wikipedia.org/wiki/PubSubHubbub): trying to make
	RSS feeds real-time, I'd say about 30% of the feeds I was fetching had it
	enabled;

* [Apple Push Notifications](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ApplePushService.html);

* [Ansible](https://www.ansible.com): for provisioning;

* [DigitalOcean](https://www.digitalocean.com): for cheaper servers, I used to
	have bare-metal servers but these days they don't make sense;

* A [Ruby on Rails](http://www.rubyonrails.org) 4.2 stack (the upgrade from
  previous version was painful);

* [Sidekiq](http://www.sidekiq.org): This is a must use for anyone using a Ruby
	framework. I processed hundreds of millions jobs through it;

If I had to write this project from the ground up now, I would probably move to
[AWS Lambdas](https://aws.amazon.com/documentation/lambda/) with 
[ServerLess](https://github.com/serverless/serverless) or [Google Cloud
Functions](https://cloud.google.com/functions/docs).

# Numbers at the time of this post

* 92,665 users, 99 paid users (monthly plans). That's 0.1% but it includes
  users all the way back from June 2009;
* 158,668 RSS feeds;
* 10,326 Twitter accounts;
* 6,050 connected devices;

Thank you if you were one of the user, I'm as sad to see it go than you are.
I'll trash the servers, delete all pushes, all tokens and credentials by the
end of April.
