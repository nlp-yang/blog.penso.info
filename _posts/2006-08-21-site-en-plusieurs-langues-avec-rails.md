---
layout: post
author: Fabien Penso
title: Site en plusieurs langues avec rails?
date: 2006-08-21 11:58:00.000000000 +02:00
categories:
- rails
- languages
- langues
- multilangues
---
<p>Vous avez un site rails que vous désirez faire en multi-langues. Voici un plugin qui vous permettra d’avoir des fichiers de “views” et de “layout” différents. De plus le plugin redirigera l’utilisateur vers la langue de son navigateur (on peut configurer les langues avec un ordre de priorité que le plugin utilise).</p>


	<p>Plus d’information vers <a href="http://penso.info/svn/rails/plugins/multi_lang/">http://penso.info/svn/rails/plugins/multi_lang/</a>. Pour l’installation effectuez simplement un :</p>


<pre>
script/plugin install http://penso.info/svn/rails/plugins/multi_lang/
</pre>

	<p>Le reste est dans le <span class="caps">README</span>. Le plugin marchera pour des sites existants, vous n’avez pas besoin de déplacer les fichiers immédiatement.</p>


	<p><strong>mise à jour</strong> on m’indique l’existance de <a href="http://www.yotabanana.com/hiki/ruby-gettext-howto-rails.html#Localized+templates+for+Views%2FActionMailer">ce plugin</a> qui ferait la même chose (Ruby-GetText-Package). Je n’ai pas vérifié.</p>
