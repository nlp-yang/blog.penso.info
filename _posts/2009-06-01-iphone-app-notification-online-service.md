---
layout: post
author: Fabien Penso
title: iPhone app notification online service
date: 2009-06-01 03:34:07.000000000 +02:00
categories:
- Uncategorized
---
<img class="alignleft" src="http://devimages.apple.com/iphone/program/images/sdk_icon3.png" alt="" width="66" height="79" />While I worked on my apple push notification Ruby on Rails plugin, I wondered if it would make sense to create a service which allow independent developers to send notifications. Independent developer would not have to worry about sending those anymore, they would just call a XML/JSON friendly url with the message, etc, and the service would take care of the rest.

You'd setup your application once on the service, and then would have a specific url to call for sending notifications, or could use an HTML page to send them manually.

Would you use it, and if yes what feature would you look for? You can register for the service at <a href="http://appnotifications.com/">Apple Push Notification online service</a>.
