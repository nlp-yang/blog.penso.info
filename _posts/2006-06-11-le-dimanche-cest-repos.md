---
layout: post
author: Fabien Penso
title: Le dimanche, c'est repos
date: 2006-06-11 15:18:00.000000000 +02:00
categories:
- photography
- computer
---
<p>Quelques sites photographiques à visiter:</p>

<ul>
<li>“Le collectif SIC”:http://www.collectifsic.com/ et “le blog”:http://francois-cs.blogspot.com/ de l’un de ses membres ; </li>
<li>La photographe “Heidi Good”:http://www.heidigood.com/, d’incroyables portraits ;</li>
<li>La page “digitalrailroad”:http://www.digitalrailroad.net/bruno/ de Bruno Stevens, avec deux reportages récents faits en Angola, sur le choléra ainsi que la tuberculose. Hasselblad et Tri-x au rendez-vous ;</li>
<li>“un autre”:http://www.lagaraje.com/ pour la route.</li>
</ul>

<p>Le soir, quand mon emploi du temps le permet, j’aide un peu “Shinji”:http://kuwayama.com/ à améliorer la rapidité de “lightstalkers”:http://www.lightstalkers.org/. Du “rails”:http://www.rubyonrails/, évidemment. Les erreurs que je peux y voir et que vous pourriez être intéressés de ne pas reproduire lors de vos propres développements :</p>

La révision, c’est bon. L’utilisation d’outils de gestion de révisions tels que CVS ou “Subversion”:http://subversion.tigris.org/ (préférez Subversion) est <em>primordiale</em>. Sans cela, pas de développements à plusieurs, pas d’historique, pas de possibilité de backuper votre travail facilement. Bref, sans ça, <em>ne commencez</em> même pas à développer, même pour un projet à une personne.

La gestion de tickets: “trac”:http://www.edgewall.com/trac/, le 2ème outil à mettre en place. Il vous permettra de noter les bugs, fonctionnalités à développer ultérieurement, et de concentrer tout ça sur <em>une seule page</em>. Vous pourrez de plus naviguer dans les sources, controler les derniers travaux effectués sur le projet (timeline), gérer votre <em>TODO</em> list. Le matin en arrivant à votre bureau (ou en vous déplaçant du lit à l’ordinateur), il vous suffit d’aller voir les fonctionnalités à rajouter, en les listant par ordre de priorité. Tous les acteurs du projets pourront faire de même.

Attention à votre code source, n’utilisez que tabulations ou espaces, pas les deux. La consistance dans vos sources et quelques commentaires bien placés faciliteront grandement le travail de vos collegues (futurs ou actuels).

Plus spécifiquement rails. D’abord l’utilisation de find(), ensuite et seulement ensuite, pour des raison d’optimisation, l’usage de find_by_sql(). Pas l’inverse.

Pas de code dans les fichiers views/, comme l’indique le pattern MVC. Pas de @comments = Comment.find() dans les vues, <em>jamais</em>. Les vues se contentent de l’affichage.

La première chose à vérifier quand vous développez votre site, le nombre de requêtes SQL dans le fichier de log (log/development.log) et l’utilisation pour celles-ci de clé (DESC SELECT … dans la console mysql). L’usage de :includes => [] dans le code rails est souvent requis. Conseil: il est souvent plus rapide d’avoir 2 requetes SQL plus simples, qu’une seule très compliquée avec beaucoup de :includes.

L’utilisation massive de caches, et particulièrement pour la page principale du site (caches_page). L’affichage d’information personnelle pourra toujours se faire en javascript directement, ou en Ajax. Qui n’apprécie pas un site qui se charge instantanément, plutôt qu’un autre ou il faut, pour chaque page, attendre 2 secondes?

<p>Un petit rappel: j’effectue toujours des conseils autour de développements logiciels (web ou non). Ce que mes clients devraient attendre de leurs prestataires :</p>

<ul>
<li>Un accès permanent et complet au code source en développement ;</li>
<li>Un accès permanent au site en cours de développement, pour vérifier au quotidien l’avancement du projet ;</li>
<li>Un accès à une interface de gestion de ticket, pour remonter le plus rapidement possible les mauvaises surprises ;</li>
<li>De manière générale, une relation étroite entre vous, et nous.</li>
</ul>

<p>Et ça tombe bien, vous aurez tout ça ici.</p>
