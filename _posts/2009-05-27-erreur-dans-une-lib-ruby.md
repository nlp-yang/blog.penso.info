---
layout: post
author: Fabien Penso
title: Erreur dans une lib Ruby
date: 2009-05-27 06:33:43.000000000 +02:00
categories:
- computer
---
Sur mon Mac le fichier /System/Library/Frameworks/Ruby.framework/Versions/1.8/usr/lib/ruby/1.8/resolv.rb a le code suivant :

[sourcecode language='ruby']
597         while (now = Time.now) < timelimit
598           timeout = timelimit - now
599           if !IO.select([@sock], nil, nil, timeout)
600             raise ResolvTimeout
601           end
602           reply, from = recv_reply
[/sourcecode]

La ligne 600 me laisse perplexe, voyez-vous pourquoi?
