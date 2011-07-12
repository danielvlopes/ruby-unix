RUBY e RAILS NO UBUNTU (10.x and 11.x)
===

Step by step guide to install Rails (last version) and Ruby (1.9.2) on Ubuntu. We also cover some GEdit setting with GMate plugin.

**1º Update apt-get**

Open the terminal and run:

    sudo apt-get update

**2º Install GIT and Curl**

    sudo apt-get install build-essential git-core curl

**3º Install RVM (Ruby Version Manager)**

RVM let you install and manage more than one Ruby version. But here we'll use only one:

    bash < <(curl -s https://rvm.beginrescueend.com/install/rvm)

**4º Loading RVM**

Run de code below

    echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"' >> ~/.bashrc

Reload the file (in Terminal):

    . ~/.bashrc

**5º Installing the other essential packages**

    rvm notes

The above command will display the missing packages to install. Just copy and paste the line like below:

    sudo apt-get install build-essential bison openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev

**6º Installing Ruby**

Run (this command will take a couple of minutes)

    rvm install 1.9.2

Set ruby 1.9.2 as the default to your user:

    rvm --default use 1.9.2

Now this should work:

    ruby -v
    ruby 1.9.2p136 (2010-12-25 revision 30365) [x86_64-linux]

**7º Installing Rails**

    gem install rails


**8ºMySQL and PostgreSQL (OPTIONAL)**

In development mode most of the time sqlite is enough. If you want to use MySQL the right Gem is mysql2 but before you should do:

    sudo apt-get install libmysqlclient16-dev

And after:

    gem install mysql2

For PostgreSQL:

    sudo apt-get install libpq-dev

And after:

    gem install pg

**9º MongoDB (OPTIONAL)**

In Terminal type the commands bellow:

    sudo echo "deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen" >> /etc/apt/sources.list
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
    sudo apt-get update
    sudo apt-get install mongodb-10gen


Setup GEdit
===

For GEdit we'll use GMate plugin. In Terminal:

    sudo apt-add-repository ppa:ubuntu-on-rails/ppa
    sudo apt-get update
    sudo apt-get install gedit-gmate

Now open GEdit got Edit/Preferences menu and in Plug-ins check all. Now everything is ready.
