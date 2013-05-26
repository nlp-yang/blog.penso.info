---
layout: post
author: Fabien Penso
title: Quelques projets en cours
date: 2007-09-04 13:54:30.000000000 +02:00
categories:
- Uncategorized
---
Ce qui occupe mon temps libre (j'en ai pas beaucoup) actuellement :
<ul>
	<li>Réécriture du générateur d'identification <a href="http://penso.info/en/auth_generator">auth_generator</a> en plugin, nommé auth_workflow. Le système de cookie est conservé, le format de la base de donnée aussi, mais le tout passe en plugin pour permettre de modifier le plugin pour ses besoins personnels, tout en continuant de mettre à jour en conservant ses propres modifications. La partie gestion des utilisateurs se fera par le plugin <a href="http://activescaffold.com/">active_scaffold</a> (tache rake pour générer les templates d'administration). Sera disponible dès le départ la gestion de roles, de taches et d'utilisateurs. Les roles seront hierarchisés pour permettre d'avoir User > Moderator > Administrator. Les taches seront détectés automatiquement sous la forme Controller::Action. Bientôt disponible ...</li>
	<li>Écriture d'un script greasemonkey (déjà fait) couplé à un daemon local (en cours) pour permettre d'écouter la musique envoyée sur <a href="http://binsearch.info/">binsearch.info</a>, le tout en cliquant sur un bouton "écouter".</li>
	<li>Réecriture de <a href="http://linuxfr.org">LinuxFr</a> en Ruby on Rails, avec en tête l'idée de pouvoir tenir la charge actuelle du site (importante...). Bon ce n'est pas en première priorité mais quelques templates sont faits, ainsi que des tests de transfert de la base actuelle. Mais il faudra d'abord que auth_workflow soit terminé.</li>
</ul>
