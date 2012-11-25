# RUBY e RAILS NO UBUNTU (12.X)

Step by step guide to install Rails (last version) and Ruby (1.9.3) on Ubuntu. We also cover some GEdit setting with GMate plugin.

## 1º Updating apt-get

Open the terminal and run:

    sudo apt-get update

## 2º Installing some important packages

    sudo apt-get install build-essential openssl libreadline6 libreadline6-dev curl git-core \
    zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf \
    libc6-dev ncurses-dev automake libtool bison subversion nodejs

## 3º Instaling RVM (Ruby Version Manager)

RVM lets you install and manage more than one Ruby version. But here we'll use only one:

    curl -L https://get.rvm.io | bash -s stable --ruby

## 4º Defining the default Ruby

    rvm --default use 1.9.3
    
Now the command below should print the ruby version 1.9.3:

    ruby -v

## 5º Installing Rails

    gem update --system
    gem install rails

## 6º Installing Rails

Just for test purposes, you can creating your first app:

    rails new minha_nova_app

Now, you could navigate to the directory of my_new_app and start the server. But, since Rails 3.1, you need to have a javascript runtime. To install only thing you need to do is open the Gemfile from the root of your app and add:

    gem 'execjs'
    gem 'therubyracer'

Save,close and then run the command bellow:

    bundle install

Now you can run:

    rails s

## Installing Databases (OPTIONAL)

### For MySQL

In development mode most of the time sqlite is enough. If you want to use MySQL the right Gem is mysql2 but before you should do:

    sudo apt-get install libmysqlclient18-dev

And after that:

    gem install mysql2

### For PostgreSQL

The PostgreSQL database is also used for most deployments on Heroku. Before installing the gem you should install the database with:

    sudo apt-get install libpq-dev

And after that:

    gem install pg

# Setup GEdit

For GEdit we'll use GMate plugin. In Terminal:

    sudo apt-add-repository ppa:ubuntu-on-rails/ppa
    sudo apt-get update
    sudo apt-get install gedit-gmate

Now open GEdit got Edit/Preferences menu and in Plug-ins check all. Now everything is ready.