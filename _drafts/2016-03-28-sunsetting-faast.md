--- 
layout: post
title: Sunsetting Faast
categories: 
- computer
description: Faast is an iOS app to receive push notification from Twitter, Facebook, RSS Feeds and more
photo: /img/faast_icon.png
---

TLDR: I've decided to sunset Faast, the Push app I've been running for years.
Expect it to stop working within weeks, probably by the end of April. I'll switch
to using Reeder myself for my RSS feeds.

# Sunsetting Faast

Faast is a push application I've created years ago, with its previous
version Push4 back to 2009. The Appstore has changed a lot since, and you've
probably already read many blog posts from indie developers saying they can't
make a living from it. That's more true now than ever, and the only sustainable
way to be an iOS developer full time is to freelance for other bigger brands.

I've been running Faast at my loss for years, because I was its first user. The
difference between Faast and other mobile app is it requires servers, and those
are very expensive to run. Those servers gathered RSS feeds, tweets and emails
for you, and send those through Apple Push Notification servers. Faast had a
specific case: it required high server-wise skills, and high frontend-wise
skills as well. I know both sides, but it still involves way too much work.

AppStore users aren't willing to pay for products any more, unless it includes
candies and expensive in-app purchases for skipping levels. They don't
understand how difficult it is to write an application like Faast, and they
complain very easily without remembering the app developer is a real Human, who
you don't need to threat. I could list a lot of downsides having such an app on
the store, and I must say not having it online will free my mind a lot.

I'm happy to be out of the Apple Appstore too.

# Faast servers and technologies

Server wise, Faast used 12 servers (used to be on 2 but I switch back to more
smaller servers) and its monthly cost went from €350 per month to about €200
recently, but I'd expect most other developers to pay more than that. I've
optimized them a lot.

A lot of technologies were involved in Faast, like:

* [PubSubHubBub](https://en.wikipedia.org/wiki/PubSubHubbub): trying to make
	RSS feeds real-time, I'd say about 30% of the feeds I was fetching had it
	enabled;

* [Apple Push Notifications](https://developer.apple.com/library/ios/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/Chapters/ApplePushService.html);

* [Ansible](https://www.ansible.com): for provisioning;

* [DigitalOcean](https://www.digitalocean.com): for cheaper servers, I used to
	have bare-metal servers but these days they don't make sense. I'd actually
	recommend the cheapest DO if RAM isn't an issue;

* A [Ruby on Rails](http://www.rubyonrails.org) 4.2 stack (the upgrade from
  previous version was painful), MySQL;

* [Sidekiq](http://www.sidekiq.org): This is a must use for anyone using a Ruby
	framework. I processed hundreds of millions jobs through it;

# Numbers at the time of the writing of this post

* 92,665 users, 99 paid users (monthly plans);
* 158,668 RSS feeds;
* 10,326 Twitter accounts;
* 6,050 connected devices;
