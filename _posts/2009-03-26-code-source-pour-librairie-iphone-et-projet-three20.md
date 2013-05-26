---
layout: post
author: Fabien Penso
title: Code source pour librairie iPhone et projet Three20
date: 2009-03-26 14:19:12.000000000 +01:00
categories:
- iphone
---
<img class="alignright size-medium wp-image-358" src="http://blog.penso.info/wp-content/uploads/2009/03/3378940896_8ccb5ea1c8_o.jpg" alt="" width="229" height="438" />

<a href="http://joehewitt.com">Joe Hewitt</a>, développeur de <a href="http://www.facebook.com/apps/application.php?id=6628568379">l'application Facebook</a> pour <a href="http://www.apple.com/fr/iphone/">iPhone</a>, a publié <a href="http://joehewitt.com/post/the-three20-project/">un ensemble de classes</a> qu'il a repris de son application et dont il se servira pour la "refactoriser" pour une v2. Elles sont disponible sur <a href="http://www.github.com">github</a> (<em>note</em>: <a href="http://www.github.com">github</a> je t'aime), sous le nom de code de <a href="http://github.com/joehewitt/three20/">Three20</a> (320, la largeur de l'écran de l'<a href="http://www.apple.com/fr/iphone/">iPhone</a> actuel). Au menu un controlleur pour la recherche <a href="http://github.com/joehewitt/three20/blob/fe727213f441f3eb46b4e357a62f5d3978966ac4/src/TTSearchBar.m">TTSearchBar</a> bien pratique que j'étais en train de faire de mon côté, des <a href="http://developer.apple.com/iphone/library/documentation/UIKit/Reference/UITableView_Class/Reference/Reference.html">UITableView</a> à état, etc. Son code est propre, et deviendra un must-have rapidement.

<a href="http://joehewitt.com">Joe</a> a aussi mis à disposition <a href="http://developers.facebook.com/connect.php?tab=iphone">iPhone connect</a>, qui permet en quelques lignes d'intégrer <a href="http://www.facebook.com/">Facebook</a> dans vos applications. Testé par votre serviteur, ça marche très bien.

Tant qu'on est dans les librairies, <a href="http://www.cloudmade.com/">CloudeMade</a> a mis à disposition <a href="http://developers.cloudmade.com/projects/show/iphone-api">une librairie</a> pour intégrer des cartes à la manière de <a href="http://www.google.com/mobile/gmm/index.html">Maps.app</a>, et qui semble aboutie.

En vrac :
<ul>
	<li>Dois-je aller à la <a href="http://en.oreilly.com/rails2009/">RailsConf 2009 Las Vegas</a> si je ne suis pas loin?</li>
	<li>Je me suis inscris sur <a href="http://www.meetup.com/sfruby/">ce groupe</a> (San Francisco Ruby and Ruby on Rails enthusiasts) pour tenter de trouver des contacts sur place.</li>
	<li>Suite au message précédent sur la Californie, le créateur d'un "geektrip" m'a twitté. 4 000E la semaine. Gloups.</li>
	<li>Besoin de faire du code pour iPhone 3.0 ?#ifdef __IPHONE_3_0
//3.0+
#else
//pre 3.0
#endif</li>
	<li><a href="http://www.richkidsondrugs.com/2008/10/14/upgrading-sqlite-to-support-math-functions-on-cocoa-iphone-mac-os-x/">Mettre à jour SQLite</a> pour avoir les fonctions mathématiques sur <a href="http://www.apple.com/fr/iphone/">iPhone</a> (pour le calcul des distances).</li>
	<li><a href="http://www.richardhyland.com/diary/2008/12/21/some-cool-tips-and-tricks-for-the-iphone-sdk/">Quelques astuces</a> sur le SDK <a href="http://www.apple.com/fr/iphone/">iPhone</a>.</li>
	<li><a href="http://scobleizer.com/">Un blog</a>, <a href="http://blog.newzwag.com/">un autre</a>, <a href="http://www.connectblogs.com/">un autre</a>, <a href="http://appcubby.com/blog/">un autre</a>, <a href="http://gusmueller.com/blog/">un autre</a>.</li>
	<li><a href="http://ipredator.se/">iPredator</a> en provenance de <a href="http://www.thepiratebay.org/">ThePirateBay</a>, pour protéger vos connexions Internet. Par les temps qui cours, ça devient indispensable. Encore que <a href="http://www.giganews.com/">Giganews</a> propose du <a href="http://fr.wikipedia.org/wiki/OpenSSL">OpenSSL</a>.</li>
</ul>
