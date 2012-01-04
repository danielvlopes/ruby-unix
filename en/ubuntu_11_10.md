# RUBY e RAILS NO UBUNTU (10.x and 11.x)

Step by step guide to install Rails (last version) and Ruby (1.9.3) on Ubuntu. We also cover some GEdit setting with GMate plugin.

## 1º Update apt-get

Open the terminal and run:

    sudo apt-get update

## 2º Install GIT and Curl

    sudo apt-get install build-essential git-core curl

## 3º Install RVM (Ruby Version Manager)

RVM let you install and manage more than one Ruby version. But here we'll use only one:

    bash < <(curl -s https://rvm.beginrescueend.com/install/rvm)

## 4º Loading RVM

Run de code below to make sure RVM will be loaded when opening a new terminal: 

    echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"' >> ~/.bashrc

Reload the configuration file (in Terminal):

    . ~/.bashrc

## 5º Installing the other essential packages

    sudo apt-get install build-essential openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion

## 6º Installing Ruby

Run (this command will take a couple of minutes)

    rvm install 1.9.3

Set ruby 1.9.333 as the default to your user:

    rvm --default use 1.9.3

Now this should work:

    ruby -v
    ruby 1.9.3p0 (2011-10-30 revision 33570) [x86_64-linux] 

## 7º Installing Rails

    gem install rails

## 8º First app

To test everything you can creating your first app:

    rails new my_new_app

Now, you could navigate to the directory of my_new_app and start the server. But, since Rails 3.1, you need to have a javascript runtime. To install only thing you need to do is open the Gemfile from the root of your app and add:

    gem 'execjs'
    gem 'therubyracer'

Save,close and then run the command bellow:

    bundle install

Now you can run:

    rails server

## Installing ruby-debug19 (OPTIONAL)

There's an issue when installing ruby-debug19 that breaks when compiling linecache19, which as of this writing is not solved yet. To get around this problem you should do the following:

    gem install ruby-debug19 -- --with-ruby-include=$rvm_path/src/ruby-1.9.3-p0

You should keep the "--" in the middle of the command. These instructions came from StackOverflow http://stackoverflow.com/questions/6650567/installing-linecache19-for-ruby-1-9-2-via-rvm

## Installing Databases (OPTIONAL)

### For MySQL
In development mode most of the time sqlite is enough. If you want to use MySQL the right Gem is mysql2 but before you should do:

    sudo apt-get install libmysqlclient16-dev

And after that:

    gem install mysql2

### For PostgreSQL:
The PostgreSQL database is also used for most deployments on Heroku. Before installing the gem you should install the database with:

    sudo apt-get install libpq-dev

And after that:

    gem install pg

### For MongoDB:
The mongodb package on the regular Ubuntu repositories is usually out of date, you should install it from 10Gen's repository, unfortunately, they don't have a PPA. To add their repo first you need to get 10gen's key and then add the source servers to your list:

    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
    sudo sh -c "echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' >> /etc/apt/sources.list"

After that, update your package list and install it:

    sudo apt-get update 
    sudo apt-get install mongodb-10gen

These instructions will download and install the package, create a mongodb user and configure MongoDB to run as a service using upstart. You can check its status and start/stop it using:

    service mongodb status
    sudo service mongodb stop
    sudo service mongodb start

Note that MongoDB will create journaling files on /var/lib/mongodb/journal occupying a total of 3.1 GB, make sure you have enough space on your disk. You can see the official instructions at http://www.mongodb.org/display/DOCS/Ubuntu+and+Debian+packages

# Setup GEdit

For GEdit we'll use GMate plugin. In Terminal:

    sudo apt-add-repository ppa:ubuntu-on-rails/ppa
    sudo apt-get update
    sudo apt-get install gedit-gmate

Now open GEdit got Edit/Preferences menu and in Plug-ins check all. Now everything is ready.
