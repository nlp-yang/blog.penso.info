---
layout: post
author: Fabien Penso
title: Ecrire une fonction r&#233;cursive
date: 2006-08-28 15:10:00.000000000 +02:00
categories:
- ruby
- redcloth
---
<p>Il arrive régulièrement qu’un développeur ait à faire une fonction récursive.
Il y a deux méthodes pour les écrire, la bonne et la mauvaise. La mauvaise
c’est dans le genre de :</p>


<pre>
def ma_super_fonction(variant = 0)
  (...) pleins de code 
  if qqch 
    ma_super_fonction(variant+1)
  end
end
</pre>

	<p>C’est bien, mais comment sait-on que la partie algorythmique de la fonction
n’est pas foireuse, et qu’il n’y a pas de boucle? Et bien on ne sait pas.
D’ailleurs comme on ne vérifie pas du tout le nombre de fois que la fonction
s’appelle, le bug n’est pas loin.  Vous pensez être sûr que votre code est bon 
et que ça ne bouclera pas? Faux.</p>


	<p>Maintenant la bonne méthode c’est quelque chose du genre de :</p>


<pre>
def ma_super_fonction(variant = 100)
  if variant < 0
    return  
  end
  (...) pleins de code 
  if qqch 
    ma_super_fonction(variant-1)
  end
end
</pre>

	<p>Là on sait que ça se terminera forcément un jour, pas de boucle infinie. Alors
pourquoi parler de tout ça ? Parce que dans une libraire utilisée régulièrement
dans Ruby (RedCloth, fichier redcloth.rb) on trouve <em>exactement</em> la mauvaise
manière de faire les choses :</p>


<pre>
def glyphs_textile( text, level = 0 )
  (...) pleins de code 
  glyphs_textile( line, level + 1 )
  (...) pleins de code 
end
</pre>

	<p>Je viens de perdre 10H de temps à essayer de debuger mon blog Typo (qui utilise 
RedCloth), dont les process prenaient régulièrement 500M de ram et plus,
faisait swaper mon serveur, que j’avais plus qu’à rebooter à distance par un
gestion à distance des APCs (en fait c’est Yann qui s’occupait de désactiver
l’APC) pendant plusieurs jours.</p>


	<p>Merci RedCloth et son développeur…</p>
