---
layout: post
title: Vagrant for Rails development
categories:
- computer
description: Vagrant for Rails development including MySQL, rvm, nginx and ruby2.1
---

I used to use VMWare with a Debian guest for all my Rails development. It
allowed me to have a similar configuration than on my servers, and contained my
code so I could update my MacOS laptop or move my development computer without
losing any time reinstalling anything except VMware.

However a coworker would have to install VMWare and his own Linux to start
coding (or use anything else of his choice). Vagrant allows you to commit your
Vagrantfile inside your git repository, making sure everyone use the same
environment and allowing your new coworker to start coding right away after a
simple `vagrant up`.

The following [Vagrantfile for
Rails](https://gist.github.com/penso/e9a76fc69679f46a42cc) allows just that. It
sets a root password for MySQL without the need to use the ncurses interface,
installs `rvm` and runs `bundler`. If you want to reuse this you should:

* Install [Vagrant](http://www.vagrantup.com/downloads.html)
* Install [Virtualbox](https://www.virtualbox.org/wiki/Downloads)
* Execute `vagrant init` in your Rails directory.

If everything went smooth:

* Replace the `Vagrantfile` with my [Vagrantfile for Rails](https://gist.github.com/penso/e9a76fc69679f46a42cc) 
* Run `vagrant up`.
* SSH into your VM with `vagrant ssh`
* Execute `cd /vagrant` and start your Rails instance with `rails s -b 0.0.0.0` (rails binds to localhost by default and it won't work as you want to bind on the VM internal IP)

I use nginx with puma, so a simple
[http://localhost:8080/](http://localhost:8080) gives me my Rails code. The
only remaining issue is using `livereload`, the `Guard` process inside the VM
won't get the file change notification. I have yet to fix this in a proper way
and not polling every X seconds for file changes.

Let me know on [@fabienpenso](http://twitter.com/fabienpenso) how to improve
this and how you use Vagrant.

******

My Vagrantfile if needed.

{% highlight ruby %}
# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "hashicorp/precise32"

	#config.vm.synced_folder ".", "/vagrant", type: "rsync", rsync__exclude: ".git/"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  config.vm.network "forwarded_port", guest: 80, host: 8080 #nginx
  config.vm.network "forwarded_port", guest: 3000, host: 3000 #rails
  config.vm.network "forwarded_port", guest: 35729, host: 35729 #livereload
  config.vm.network "forwarded_port", guest: 4000, host: 4000 #guard

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:

	config.vm.provider :virtualbox do |vb|
		vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
		vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]

		vb.customize ["modifyvm", :id, "--cpus", "2"]
		vb.customize ["modifyvm", :id, "--memory", "1024"]
	end

  #
  # config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
  #   vb.memory = "1024"
  # end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install debconf-utils

    echo "mysql-server-5.5 mysql-server/root_password_again password Som3Passw0rd" | sudo debconf-set-selections
    echo "mysql-server-5.5 mysql-server/root_password password Som3Passw0rd" | sudo debconf-set-selections

    sudo apt-get install -y curl git build-essential mysql-server-5.5 libmysqlclient-dev nginx nodejs

    curl -sSL https://get.rvm.io | bash
		source /usr/local/rvm/scripts/rvm
    rvm requirements
    rvm install 2.1
    rvm use 2.1 --default

    echo "gem: --no-ri --no-rdoc" > ~/.gemrc
    gem install bundler
    cd /vagrant
    bundle

    rake db:create db:migrate db:seed

    # If you use nginx like I am
    sudo ln -s /vagrant/config/nginx.conf /etc/nginx/sites-enabled/csapi
    sudo rm /etc/nginx/sites-available/default
    sudo /etc/init.d/nginx restart
  SHELL
end
{% endhighlight %}
