---
layout: post
author: Fabien Penso
title: Passage de ce blog de typo Ã  Wordpress
date: 2007-08-26 06:20:57.000000000 +02:00
categories:
- Uncategorized
---
On peut avoir le meilleur framework du monde, ça n'évite pas de l'utiliser pour faire de mauvais logiciels. <a href="http://typosphere.org/">typo</a> est un bon exemple de mauvais logiciel (ce que j'ai utilisé pour ce blog pendant de nombreux mois). Beaucoup de problèmes, peu de plugins, et des bugs. De plus le site était inaccessible pendant longtemps, le trac aussi. Les process Mongrel qui le faisaient tourner prenaient parfois 80Mo par process. J'ai donc décidé d'utiliser un autre logiciel qui même s'il utilise un language peu appréciable (PHP) et est surement buggé de partout inclut des soucis de sécurité, a l'avantage de marcher : <a href="http://www.wordpress.org/">Wordpress</a>. Quelques heures pour installer quelques plugins, un lien vers <a href="http://" title="http://www.feedburner.com/">feedburner</a>, un thème adéquat, et c'est parti. Import des anciens articles par l'import RSS, les commentaires sont perdus ( mais je les réinjecterai plus tard ). Quelques modifications du code (ouch, c'est moche PHP), mais j'ai enfin un truc qui marche.

Les choses que je n'aimais vraiment pas avec Typo :
<ul>
	<li>Pas de cache statique, surtout pour les flux RSS qui sont appelés constamment.</li>
	<li>Une réelle lenteur du site (même Wordpress est plus rapide... sic)</li>
	<li>Peu de plugins</li>
	<li>Quasi plus développé (sauf neuro qui se bat tout seul sur IRC)</li>
	<li>Pleins de bugs</li>
</ul>
J'avais testé <a href="http://mephistoblog.com/">Mephisto</a> rapidement mais le projet semble peu développé, buggué (l'import de mon typo posait des soucis à cause des accents), et donc peu attractif. Évidemment on pourra toujours me dire que je pouvais développer ma propre solution, mais non, je n'ai pas envie d'y passer du temps. Je préfère passer ce temps sur d'autres projets, pour peu que j'en ai le temps.

Migration engagée.
