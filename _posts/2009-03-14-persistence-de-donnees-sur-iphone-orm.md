---
layout: post
author: Fabien Penso
title: Persistence de donnÃ©es sur iPhone (ORM)
date: 2009-03-14 03:24:18.000000000 +01:00
categories:
- computer
- iphone
---
Si vous cherchez des outils <a href="http://en.wikipedia.org/wiki/Object-relational_mapping">ORM</a> qui se rapprochent de <a href="http://en.wikipedia.org/wiki/ActiveRecord_(Rails)">ActiveRecord</a> pour vos développements <a href="http://www.apple.com/fr/iphone/">iPhone</a>, c'est un peu le désert (peut être que le firmware 3.0 annoncé pour le 17 mars apportera un équivalent de <a href="http://en.wikipedia.org/wiki/Core_Data">CoreData</a>). Vous finirez par tomber sur <a href="http://code.google.com/p/sqlitepersistentobjects/">http://code.google.com/p/sqlitepersistentobjects/</a>, mais alors la à titre personnel le code n'inspire pas trop confiance.

D'ailleurs n'utilisez pas de '_' dans les noms de vos "properties" sinon ça fera planter toute la persistence... <a href="http://groups.google.com/group/sqlitepersistentobjects-user/browse_thread/thread/89c83492cf760b43">J'ai envoyé un email</a> sur <a href="http://groups.google.com/group/sqlitepersistentobjects-user">leur liste</a> à ce propos, je viens de perdre 6h à me demander pourquoi ça ne marchait pas.

En attendant mon côté fainéant me fera l'utiliser encore un peu, mais vivement un truc plus rapide et plus fiable.
