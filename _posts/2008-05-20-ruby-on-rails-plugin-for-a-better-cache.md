---
layout: post
author: Fabien Penso
title: Ruby on Rails plugin for a better cache
date: 2008-05-20 14:32:17.000000000 +02:00
categories:
- computer
---
The Ruby on Rails caches_page is broken in many ways (to my believes), first of all it has a RACE bug because it does not create the cached filename atomically, and you will end up with 0 byte size cached filename. It also does not create lock files to have other process waiting instead of generating the same pages.

If you have 3 mongrel processes delivering the same non-existing (yet) page, you'll end up with 3 mongrel processes for the same page. The following plugin does create lock files to have the 2 other waiting for a short amount of time, which should lower your cpu usage on high traffic servers.

Code is available at <a href="http://github.com/penso/caches_page_fix/">http://github.com/penso/caches_page_fix/</a>
