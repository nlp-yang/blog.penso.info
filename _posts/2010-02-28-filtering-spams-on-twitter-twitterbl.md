---
layout: post
author: Fabien Penso
title: ! 'How to filter SPAMs on Twitter efficiently : TwitteRBL ?'
date: 2010-02-28 02:25:22.000000000 +01:00
categories:
- computer
---
I'm working on a service using the <a href="http://apiwiki.twitter.com/Streaming-API-Documentation">streaming API</a> from <a href="http://www.twitter.com/">Twitter</a>, a great feature as it gives you instant access to Tweets. But then you get overloaded by Tweets, and because I'm looking for Tweets talking about money, I get <strong>lots</strong> of noise.

Looking at <a href="http://www.twitblock.org/">TwitBlock</a>, I filtered out lots of it :
<ol>
	<li>Ignore tweets from recent users (if created less than 24 hours ago)</li>
	<li>Ignore tweets from users with default profile image</li>
	<li>Ignore if fewer than 10 followers</li>
	<li>Ignore if user description and name are blank</li>
	<li>Ignore if followers fewer than 100, and friends count is > (2*followers_count)</li>
	<li>Ignore if followers count over 100, and friends count is > (5*followers_count)</li>
	<li>Ignore if the user sends more than 20 tweets per day in average, since its creation</li>
</ol>
Some of these is working for me, but might not work for you at all. However, I think there could be a better way for a mass use. I ran mail servers for years, a very reliable way to handle this is to use <a href="http://en.wikipedia.org/wiki/DNSBL">DNSBL</a> (also called RBL). You could have different RBLs for different use, and any twitter client could implement this <strong>very easily</strong>. Please note this could probably not work for Direct Messages except if <a href="http://www.twitter.com/">Twitter</a> grant specific access to the service, which they would probably never will.

<img class="aligncenter size-full wp-image-496" title="twitterbl" src="http://blog.penso.info/wp-content/uploads/2010/02/twitterbl.png" alt="twitterbl" />
