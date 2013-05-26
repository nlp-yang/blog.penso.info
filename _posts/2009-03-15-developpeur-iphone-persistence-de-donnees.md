---
layout: post
author: Fabien Penso
title: ! 'DÃ©veloppeur iPhone: Persistence de donnÃ©es'
date: 2009-03-15 14:46:10.000000000 +01:00
categories:
- computer
- iphone
---
Une suite au <a href="http://blog.penso.info/2009/03/14/persistence-de-donnees-sur-iphone-orm/">message précédent</a> qui mentionne <a href="http://code.google.com/p/sqlitepersistentobjects/">sqlpo</a>. Après quelques tests j'ai fini par abandonner son utilisation dans mon application, et je vous invite à ne pas l'utiliser, ni même à essayer. En effet le chargement d'une table de 150 lignes prend ... 3 secondes ! Il est bugué, le code n'inspire pas confiance, et il est d'une lenteur phénoménale.

Une methode similaire que j'ai développée rapidement en utilisant <a href="http://gusmueller.com/blog/archives/2008/03/fmdb_for_iphone.html">FMDB</a> (un wrapper <a href="http://www.sqlite.org/">sqlite</a>) prend ... 0.20 seconde. Pas besoin d'en rajouter.
