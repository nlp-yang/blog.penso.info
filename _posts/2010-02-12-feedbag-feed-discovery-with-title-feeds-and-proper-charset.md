---
layout: post
author: Fabien Penso
title: ! 'Feedbag: feed discovery with title, feeds, and proper charset'
date: 2010-02-12 02:26:48.000000000 +01:00
categories:
- computer
- rails
---
Just released <a href="http://gemcutter.org/gems/penso-feedbag">http://gemcutter.org/gems/penso-feedbag</a> to discover feeds for specific website, with proper charset, a fork from <a href="http://github.com/tatemae/muck-feedbag">muck-feedbag</a>, which was a fork from <a href="http://axiombox.com/feedbag/">feedbag</a>.

Yes, I love Ruby, Git, Gem and GitHub.

[sourcecode language="ruby"]
>> require 'feedbag'
>> Feedbag.find("http://lemonde.fr")[3]
=> #<struct Feedbag::Feed url="http://www.lemonde.fr/rss/sequence/0,2-3224,1-0,0.xml", title="Le Monde.fr: Société">
[/sourcecode]
