---
layout: post
author: Fabien Penso
title: Export vCard corrompu - mac os x
date: 2008-02-17 18:25:47.000000000 +01:00
categories:
- computer
---
Besoin d'importer des vCards générées de votre AddressBook mac os x ? Vous avez sûrement dû vous apercevoir que les fichiers comprennent pleins de caractères de !$%&! Un bout de Ruby vous réglera le problème :
<blockquote>#!/usr/bin/env ruby

for line in STDIN do
line.gsub!("\000",'' )
line.gsub!("\015",'' )
puts line
end</blockquote>
Et à lancer avec  cat all.vcf | ./ruby/fix_mac_vcards.rb > all_fixed.vcf. Le tout s'importera beaucoup plus facilement dans Evolution, etc. D'ailleurs je n'ai toujours pas trouvé la solution sous Linux pour gérer ses contacts. Evolution n'est pas terrible, mais meilleur que Kontact, lui même meilleur que Evolution pour la partie calendrier distant caldav. Quelle tristesse ...
