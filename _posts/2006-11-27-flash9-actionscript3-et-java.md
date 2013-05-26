---
layout: post
author: Fabien Penso
title: Flash9, ActionScript3, et Java.
date: 2006-11-27 01:07:00.000000000 +01:00
categories:
- flash
- java
---
<p>Flash9 apporte une nouveauté, ActionScript3. Quand on voit ce qu'est
ActionScript2, on comprend le besoin d'avoir une version plus cohérente, plus
orientée objet, et plus propre. Des nouveautés ; par exemple une classe Socket qui
permet de faire des appels réseaux (enfin), et une classe ByteArray qui permet
de mettre en mémoire des binaires.</p>

<p>C'est chouette ! J'ai besoin de faire un player MP3 en Flash qui récupère les fichiers
par un protocol maison (je laisse votre imagination faire le reste du chemin
sur mon idée). Je prends Flex2 (Adobe file des versions de 30jours de test)
basé sur l'excellent Eclipse, pas comme l'immondice de Flash fait pour les
graphistes. En quelques heures j'ai mon code qui fonctionne, AS3 est proche de
Java et je m'y fais vite.</p>

<p>Si tout pouvait être aussi rose. Pas de bol, si AS3 permet de stocker des informations
en binaire, après on ne peut rien en faire... Impossible de jouer un MP3 stocké dans un ByteArray,
la classe Sound() ne prend qu'un URLRequest en argument (un fichier ou une url <em>http</em>), classe
qui est 'final' et dont on ne peut pas hériter pour faire la sienne. La seule
solution serait d'encapsuler le MP3 dans un SWF, le charger par Loader.loadBytes() et le jouer, comme indiqué <a href="http://www.flashcodersbrighton.org/wordpress/?p=9">par ici</a>.
Les spécifications du SWF Flash8 ne sont pas vraiment documentée, celle de Flash9 encore moins. Passer des jours juste pour cette fonctionnalité, non merci.</p>

<p>Je me suis même ennuyé à aller à une conférence Flex par Adobe lundi dernier après-midi, organisée à l'étage 56 de la tour Montparnasse, pour rencontrer Thibault Imbert de <a href="http://www.bytearray.org">ByteArray</a> qui
a la mauvaise idée de ne pas laisser son adresse email en ligne. Je lui pose ma question "jouer un mp3
stocké en ByteArray" et il me promet de revenir vers moi. Dès la première pause de la conférence
(j'ai attendu 2H quand même), je me faufile dehors, j'ai déjà perdu trop de temps (et Thibault ne m'a pas répondu, mais je n'espère pas de réponse supplémentaire).</p>

<p>Conclusion ? Je n'avais pas envie particulièrement de faire du Flash, language
propriétaire (on remarque d'ailleurs que s'il était libre, j'aurais sans aucun
doute pu jouer mon MP3 sans problème), je voulais juste un truc rapide pour les
utilisateurs, sans sensation de lenteur. Ca va se terminer en applet Java (si
ça se termine) pour laquelle j'ai trouvé toutes les librairies nécessaires en
quelques heures. Ca tombe bien, Java est désormais sous une licence libre.
J'espererais juste qu'on améliore le chargement des applets dans les
navigateurs, pour que j'ai pas l'impression que ça consomme mes 2Gigs de RAM, et que je recoche
l'option Firefox "Activer Java" que je laisse vide.</p>
