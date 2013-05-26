---
layout: post
author: Fabien Penso
title: Point de vue sur l'état de la VoIP en France
date: 2006-06-11 16:18:00.000000000 +02:00
categories:
- computer
---
<p>La “VoIP”:http://fr.wikipedia.org/wiki/Voip en France, tout le monde connait, tout le monde en parle, mais personne ne fait ça comme il faut ; je m’explique.</p>

<p>A la fin de mon année de master spécialisée en architecture logicielle, j’ai eu l’opportunité d’effectuer un stage de 4 mois chez “Wengo”:http://www.wengo.fr/. J’ai eu l’occasion de travailler autour d’une “modélisation idéale”:http://penso.info/code/wengofr d’un outil de téléphonie sur IP, et de m’intéresser de loin à ce sujet. Pendant cette periode, j’ai réfléchis à la manière d‘“effectuer des appels”:http://penso.info/tmp/DESS/softphone-csharp/diagrams/Model/Base/SQ<em>makeCall</em>patterns.gif et à toutes les fonctionnalités que vous voudriez avoir sur un tel logiciel, dans les limites du temps qui m’était donné. Ne cherchez pas mon nom pas les crédits donnés aux développeurs Wengo, je n’y suis pas (je suis juste un peu “par la”:http://dev.openwengo.com/trac/openwengo/trac.cgi/browser/old/wengophone-csharp).</p>

<p>Après un court séjour en Inde, j’ai proposé à Wengo de travailler pour eux et de continuer cette modélisation et mon travail général d’architecture logicielle pour eux. Nous étions d’accord sur les points qui ne convenaient actuellement pas chez eux, mais j’ai reçu une réponse négative à ma proposition. Passons…</p>

<p>Les acteurs actuels de la VoIP en France sont :</p>

<ul>
<li>“Ekiga”:http://www.ekiga.org/ (bon c’est Belge, mais on n’en veut pas à “Damien”:http://blog.gnomemeeting.net/index.php?cat=7 ;).</li>
<li>Wengo</li>
<li>Free, par l’intermédiaire de leur Freebox</li>
<li>Neuf Telecom, dont Wengo fait parti, avec leur NeufBox</li>
<li>les autres prestataires (club-internet), Wanadoo, etc.</li>
<li>Skype. C’est le leader mondial incontesté, il n’est pas Français, mais j’imagine que c’est en France aussi le logiciel le plus utilisé (moi même je l’utilise, sous le pseudo fabienpenso, et j’y ai même acheté des minutes).</li>
<li>D’autres logiciels propriétaires qu’il n’est pas nécessaire de mentionner.</li>
</ul>

<p>Dissocions tout de suite les prestataires qui fournissent un logiciel (Skype, Ekiga, Wengo) de ceux qui facilitent l’accès aux non informaticiens par l’intermédiaire d’une boite (free, club-internet, wanadoo). Seuls les premiers m’intéressent dans cet article.</p>

<p>La VoIP devient aussi important que le web, le mail, le transfert de fichiers (P2P, FTP, système web). Qu’attendez-vous d’un logiciel qui permet de transmettre votre vie privée et tant d’autres informations confidentielles? Personnellement j’attends :</p>

<ul>
<li><p><em>Un logiciel libre</em>, que tout le monde puisse vérifier. Plus que libre, j’attends un logiciel libre qui permettent à la communauté de participer avec de la documentation en ligne, un code clair et propre, l’utilisation de design patterns, l’utilisation d’un language objet haut niveau, la facilité de pouvoir le compiler sous plusieurs systèmes d’exploitations, une séparation type MVC. Combien de logiciels libres sont inmaintenables, de par leur architecture.
<em>Je note</em> que ce critère est <em>très important</em> pour les laboratoires informatiques français (Le haut secrétariat de la défense a interdit l’usage de Skype pour les chercheurs, mais les chercheurs ont changé d’avis en indiquant que ce n’était à appliquer que pour les communications importantes). Comment peut-on imaginer que ces laboratoires puissent communiquer entre eux ou avec leurs collaborateurs à l’aide de logiciels propriétaires, dont il est impossible de vérifier qu’ils sont sûrs, ou qu’ils n’effectuent pas d’écoutes illégales.</p></li>
<li><p>La possibilité de <em>chiffrer mes communications</em>. Les sociétés Françaises seront bien emmerdés, il est probable qu’ils subiront des pressions du gouvernement pour laisser la possibilité d’activer des écoutes entre des interlocuteurs. Et alors? Proposez un plugin de chiffrage aux utilisateurs qu’ils peuvent activer ou non. Quelque chose de “ce type”:http://www.philzimmermann.com/EN/zfone/ par exemple.</p></li>
<li><p>Evidemment, l’utilisation de protocols libres (jabber ou SIP, mais SIP a une préférence sauf pour Google et leur GTalk).</p></li>
<li><p>Une autre fonctionnalité plus général et qui ne s’applique par qu’à la VoIP. <em>LA SIMPLICITE</em>, et que <em>CA MARCHE</em>. Skype a très bien réussi dans le domaine, les autres, n’en parlons pas.</p></li>
</ul>

<p>Et bien dans la liste des acteurs Français, aucun ne remplit ces critères. Le plus étonnant c’est qu’il est probable que si l’un d’eux remplissait ces critères, ils pourraient avoir des <em>financements</em> publiques, et l’<em>aide de laboratoires</em> tels l’INRIA qui a déjà, en interne, demandé à quelques personnes de regarder le protocole Skype de plus près (ça montre bien qu’ils s’intéressent au sujet). Les acteurs qui se lanceront dans le domaine seront:</p>

<ul>
<li><p>Des sociétés dont l’unique but est de faire de l’argent, et dont ceux qui tiendront les manettes n’auront que faire que le logiciels soient développé correctement, dans les règles de l’art, remplis de tests unitaires, fonctionnels, de design patterns, de systèmes de plugin, avec une interface correcte et intuitive.</p></li>
<li><p>Des indépendants, des développeurs, ou de petites sociétés (Ekiga?) qui ont envie de faire les choses correctement, mais qui n’ont pas les financements pour attirer des développeurs seniors, et pour investir le matériel requis (serveurs SIP, bande passante, etc).</p></li>
</ul>

<p>Je suis pessimiste, et nous verrons bien l’état de la VoIP en France dans quelques années, mais pour l’instant à part pour les fournisseurs (freebox), et malgré les apparences, il va plutôt mal.</p>
