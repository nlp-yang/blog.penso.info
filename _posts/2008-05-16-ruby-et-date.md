---
layout: post
author: Fabien Penso
title: Ruby et Date
date: 2008-05-16 10:07:31.000000000 +02:00
categories:
- computer
---
Sur une machine Debian Etch :
<blockquote>~$ ruby --version
ruby 1.8.5 (2006-08-25) [i486-linux]</blockquote>
<blockquote>~$ ruby -rdate -e "p Date.parse('Sin Aba 15 17:13:48 CEST 2008').month"
/usr/lib/ruby/1.8/date.rb:650:in `new_with_hash': 3 elements of civil date are necessary (ArgumentError)</blockquote>
Sur une Ubuntu :
<blockquote>~$ ruby --version
ruby 1.8.6 (2007-09-24 patchlevel 111) [i486-linux]
~$ ruby -rdate -e "p Date.parse('Sin Aba 15 17:13:48 CEST 2008').month"
5</blockquote>
Conclusion, Debian en plus d'avoir des bugs dans SSL se contente d'un Ruby 1.8.5 antédiluvien et qui ne sait pas lire les dates à un format étranger, sauf si les locales sont positionnées, chose qu'on ne peut pas faire en Ruby. ruby-locale trouvé sur Internet et publié au siècle dernier me donne :
<blockquote>irb(main):003:0> Locale.setlocale(Locale::LC_ALL, "fr_FR.UTF-8")
SystemCallError: unknown error - call to setlocale failed for args (6, fr_FR.UTF-8)</blockquote>
Alors que la locale est installée sur le serveur. Ruby 1.8.6 n'est pas disponible dans les backports. 2h de perdu pour comprendre d'où venait ce bug... Et il m'en faudra une de plus pour compiler Ruby sur le serveur.
