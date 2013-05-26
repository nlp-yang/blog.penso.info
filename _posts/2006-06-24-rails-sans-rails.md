---
layout: post
title: Rails, sans rails!
date: 2006-06-24 16:08:41.000000000 +02:00
categories:
- rails
---
Alors voilà, vous avez un site développé sous [rails](http://www.rubyonrails.org/) et vous avez besoin d’exécuter des scripts régulièrement. Vous avez donc besoin de vous connecter à la base de donnée, d’utiliser des modèles, etc. Voilà qui va vous changer la vie, la possibilité de faire ça plus rapidement (des bouts de code ont été pris sur usenet). L’exemple est dans le cas ou vous avez un modèle appelé “Zone”.

En gros, vous voilà à utiliser activerecord, sans rails.

{% highlight ruby %}
#!/usr/bin/ruby
# Fabien Penso <penso@linuxfr.org>
# Debut des scripts pour ecrire les fichiers de configurations

dir = File.dirname __FILE__
# Put the root of the RAILS directory
railsroot = '../uucpssh-1.0'
# Set the mode (development / production)
databasemode = "development"

# We need activerecord
require 'rubygems'
require_gem 'activerecord'

# Load files from the models
$:.insert(0,"#{dir}")
$:.insert(0,"#{dir}/#{railsroot}/app/models/")
$:.insert(0,"#{dir}/#{railsroot}/app/helpers/")

# Read database config via YAML
@dbs = YAML::load(ERB.new(IO.read(railsroot+'/config/database.yml')).result)

curr_db = @dbs[databasemode]

# these parameters are mysql-specific, figure out how to improve
ActiveRecord::Base.establish_connection(:adapter => curr_db["adapter"], 
:database => curr_db["database"],
:host => curr_db["host"], 
:username => curr_db["username"], 
:password => curr_db["password"])

Zone.find(:all).each do |zone|
 puts zone
end

{% endhighlight %}
