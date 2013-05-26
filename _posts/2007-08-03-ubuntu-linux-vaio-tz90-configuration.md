---
layout: post
author: Fabien Penso
title: ! 'Ubuntu Linux - VAIO TZ90 : Configuration'
date: 2007-08-03 13:01:00.000000000 +02:00
categories:
- sony
- vaio
- TZ90
- ubuntu
- linux
---
L’installation se passe bien, rien à signaler de ce côté là. Je conseille l’installation de Compiz Fusion qui est une merveille.

Comparé à mon powerbook 12” le TZ90 est une fusée, c’est super rapide. J’ai transféré mes contacts du Mac grace à un export en vCards puis à quelques lignes de sed (le format des vCards du mac sont pourris), et j’ai transférés mon agenda par des exports ICS. Le tout a été importé tranquillement sous Evolution.

Ubuntu a fait beaucoup de progrès en terme de desktop, même si ce n’est pas encore ça. Les outils idéals que j’avais sur mon mac et leur remplacant potentiels :
<ul>
	<li><a href="http://quicksilver.blacktree.com/">Quicksilver</a> : rien de tel sous Linux. Néanmoins je m’en servais surtout comme lanceur d’applications, Alt F2 fait pareil sous Ubuntu, et propose aussi la complétion. Pas aussi aboutit que Quicksilver, mais fait le travail. Pourquoi personne n’a t-il encore fait de lanceur like sous Compiz ?</li>
	<li><a href="http://www.adiumx.com/">Adium</a> : <a href="http://pidgin.im">Gaim</a> (renommé pidgin), mais Gaim est une horreur en terme d’ergonomie (alors que Adium se sert des librairies de Gaim) … Donc non, rien du tout, pas de remplaçant. J’utilise Gaim à contre coeur…</li>
	<li>Spotlight : <a href="http://raphael.slinckx.net/deskbar/">deskbar</a> avec beagle fait le travail pas mal du tout.</li>
	<li>Exposé and co : compiz-fusion en tunant un peu fait quelques trucs sympa, c’est pas encore aboutit pour certaines fonctionnalités, mais c’est clairement le top pour ce que ça fait déjà. Enfin un truc qui déchire sous Linux en terme d’interface. Super rapide en plus.</li>
	<li>Trouver des wifi : le Mac est très bon pour proposer des wifi ouverts, ubuntu propose un truc réseau mais il ne marche pas si bien. Je suis obligé de lancer Kismet en ligne de commande régulièrement…</li>
	<li>iCal + Contact : Evolution semble pouvoir faire le travail, pas aussi joli et simplifié que iCal, mais on dira que ça ira.</li>
</ul>
Pour ce qui est de la configuration du Linux on a …

Ce qui marche :
<ul>
	<li>La carte son : snd_hda_intel (installez la dernière version d’Alsa, j’ai la 1.0.14. Puis rajoutez “options snd-hda-intel model=sony-assamd” dans les options de chargement des modules)</li>
	<li>La mise en veille (installez suspend2, apparemment c’est mieux même si ça marche sans)</li>
	<li>La gestion de la luminuosité avec les Fn keys (installez linux-laptop en module, et non sonypi), mais j’ai du modifier /etc/acpi/sonybright.sh pour pointer sur les bons fichiers</li>
	<li>Le touchpad synaptics, mais c’est un ALPS ce qui signifie qu’il ne rapporte pas les touchés à deux doigts (point de scroll down à la mac)</li>
	<li>Carte gigabit sky2 Marvell</li>
	<li>La carte wireless avec le driver ipw3945, j’ai tout recompilé de <a href="http://ipw3945.sourceforge.net/">ipw3945</a> par contre Kismet se plaint
de pas avoir de Monitor mode. Il faut activer ce mode dans ipw3945-1.2.1/Makefile manuellement lorsqu’on recompile.</li>
</ul>
Ce qui ne marche pas :
<ul>
	<li>La webcam (j’ai testé le driver <a href="http://lsb.blogdns.net/ry5u870/">r5u870</a> sans succès, même en bidouillant les sources)</li>
	<li>Le lecteur de carte SD (j’ai testé le driver de <a href="http://sdricohcs.sourceforge.net/">sdricohcs</a> sans succès)</li>
	<li>Le micro (sûrement inclus avec la webcam ?), donc point de VoIP, Skype, etc :(</li>
	<li>Le lecteur fingerprint</li>
</ul>
Ce qui ne marche pas mais devrait :
<ul>
	<li>framebuffer en 1366x768, là j’ai toujours des barres de chaque côté … :(</li>
	<li>Les touches multimédias sur le devant du portable</li>
</ul>
Pas testé :
<ul>
	<li>Le modem</li>
</ul>
J’ai environ 2h30 d’autonomie avec la batterie slim (la plus petite) et un peu moins de 9H avec celle de grande capacité.

Quelques fichiers qui pourraient vous être utiles se trouvent a<a href="http://penso.info/tmp/tz90/"> http://penso.info/tmp/tz90/</a> (y compris un package pour le noyau 2.6.22)

Quelques liens qui m’ont aidé sur <a href="http://del.icio.us/penso/vaio">mon feed delicious</a>. Si vous avez réussi à configurer un truc que je n’ai pas fait, n’hésitez pas à me
contacter…
