---
layout: post
author: Fabien Penso
title: ! 'LinuxFr : crash serveur, site suspendu'
date: 2007-10-09 00:27:01.000000000 +02:00
categories:
- Uncategorized
---
Après avoir rinçé un serveur HP LT6000 gentillement donné par la marque pour le site <a href="http://linuxfr.org/">LinuxFr</a> il y a plus de 5 années (je n'ai plus la date exacte), il semblerait que celui ci soit en train de lacher, l'horloge interne boucle sur un interval de 5 secondes et ça ne plait pas du tout à Linux. Peut être dû à une défaillance de la carte mère? Une page temporaire sera affichée le temps de réfléchir à la situation, qui sera sans doute résolue par l'achat d'un nouveau serveur, neuf cette fois ci. Mais même si l'achat se fait d'ici la fin de semaine, le serveur prendra sûrement une 10aine de jours minimum pour être livré.

Évidemment cela devait arriver pendant que je m'occupais du serveur de backup (lui aussi donné par HP) qui a explosé (c'est une image) lors d'une mise à jour de B. Sibaud pour un passage en Etch, et sur lequel on a ensuite perdu la main. Shell root qui pointe sur /bin/bash3, bash3 et sudo ayant sauté lors de la mise à jour. Impossible alors de passer root en local (même en utilisant des exploites divers et variés...), je dois encore me déplacer chez nos amis Iliad.

Néanmoins l'association étant limitée financièrement, cela passera d'abord par un appel aux dons. Comme on dit chez nous, pas de bras, pas de chocolat.

<strong>Mise à jour</strong>: il semblerait que le serveur ait bien voulu repartir après un reboot, plus de nouvelles dans l'après-midi quand nous aurons backupé les disques.

<strong>Mise à jour 2</strong>: la page linuxfr a été mise à jour pour indiquer les informations pour faire des dons. Donnez des sous (facon Les Nuls). Je lance l'initiative en mettant 100€ sur a table. Qui fait mieux ?

<strong>Mise à jour 3</strong>: on aurait trouvé un serveur digne de ce nom DELL disponible dans la semaine. J'ai décidé de remettre les DNS sur l'ancien serveur dont le backup complet se termine. Un reboot l'ayant revitalisé, on va tourner dessus encore le temps de trouver, installer, tester le serveur final. Les DNS se seront propagés demain matin j'espère.

<strong>Mise à jour 4</strong>: il semblerait que la possibilité du serveur DELL se confirme, généreusement offert par une société de photo Française qui utilise beaucoup Linux (comme tous les bons sites web). Les dons serviront sans doute à acheter un serveur de backup, l'actuel étant aussi vieux quasiement que notre serveur de production. Si nous n'en n'avions pas besoin, il serait proposé aux donateurs actuels de les rembourser (nous avons reçu 1,000 € de dons environ actuellement) s'ils le souhaitent, en indiquant que l'association a toujours besoin d'une trésorerie d'avance en cas de problème hardware, sachant que nous ne mettons volontairement pas de publicités sur le site et que nous n'avons donc aucun revenu régulier. De plus <a href="http://linuxfr.org">LinuxFr</a> est désormais de retour depuis ce matin, si vous continuez à voir la page temporaire, votre DNS n'est pas à jour.
