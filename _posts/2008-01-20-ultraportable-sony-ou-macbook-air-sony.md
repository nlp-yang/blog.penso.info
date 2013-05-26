---
layout: post
author: Fabien Penso
title: ! 'Ultraportable: Sony ou Macbook Air ? Sony...'
date: 2008-01-20 21:47:58.000000000 +01:00
categories:
- computer
---
J'attendais avec impatience le nouveau ultraportable Apple. Quelle déception... Les lecteurs de ce blog savent que j'ai acquis il y a quelques mois un Sony VAIO TZ90 (il est nommé <a href="http://vaio.sony.fr/view/ShowProduct.action?product=VGN-TZ21VN%2FX&site=voe_fr_FR_cons&pageType=Overview&category=VN+TZ+Series">TZ21</a> en France), dont je suis très content. Un développeur a même récemment fait des <a href="http://wiki.mediati.org/R5u870">drivers r5u870</a> pour la webcam, qui n'était pas supporté avant. J'ai tout qui fonctionne, micro (alsa 0.15) avec un "options snd-hda-intel model=hippo" dans <span style="font-style: italic">/etc/modprobe.d/alsa-base</span>, la mise en veille, etc. Bon toujours rien pour remplacer QuickSilver et quelques applications Mac (<a href="http://do.davebsd.com/">Gnome-do</a> c'est pas encore ça du tout).

Du côté du MacBook Air nous avons un port USB, pas de batterie interchangeable, 1,4kg, pas de firewire, pas de port ethernet (sauf par l'USB mais 100M maxi), pas de lecteur d'empreinte (encore que celui du Sony marche pas sous Linux pour l'instant), pas de lecteur SD, pas de port PC card. Il est plus fin que le Sony mais beaucoup plus large et profond.

Le Sony a 160Gigs de disque, 2Gigs de ram pas soudés comme sur le Mac, 3 ports USB, 1 port Firewire, un port ethernet gigabit, un port pc card, 1.1Kg, un lecteur SD et MagicGate (bon celui là ne m'a jamais servi). Un superbe écran, une batterie longue durée de 9h (en vrai) amovible, 2 boutons mais pas de multitouch sur le trackpad. Je conseille d'ailleurs d'utiliser un noyau récent pour le VAIO, et j'ai mis des fichiers debian du noyau linux compilé à <a href="http://penso.info/tmp/tz90/">http://penso.info/tmp/tz90/</a> (2.6.24-rc7) si vous avez le même. Le module pour la carte wireless est iwl3945, il marche bien dans les cas de suspend/resume. Installez alsa ensuite et le driver r5u870 et hop.

Par contre il est vrai que le VAIO est beaucoup plus cher, ma configuration me donne un 3400€ alors que au Japon il m'a coûté 1400€. Sic :(

Bref vous l'aurez compris, le Air ne passera pas par moi, je suis <strong>très content</strong> du VAIO sous Ubuntu. Et avec Leopard/Tiger sous Vmware...
