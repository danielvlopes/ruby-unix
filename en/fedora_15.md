RUBY AND RAILS ON FEDORA (15)
===

Step by step guide to install Rails (last version) and Ruby (1.9.2) on Fedora. We also cover some GEdit setting with GMate plugin.

**1º Update yum**

Open the terminal and run:

    sudo yum update

**2º Install GIT and Curl**

    sudo yum install git curl

**3º Install RVM (Ruby Version Manager)**

RVM let you install and manage more than one Ruby version. But here we'll use only one:

    bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer)

**4º Loading RVM**

Run de code below

    echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"' >> ~/.bashrc

Reload the file (in Terminal):

    . ~/.bashrc

**5º Installing the other essential packages**

    rvm notes

The above command will display the missing packages to install. Just copy and paste the line like below:

    sudo yum install bison openssl openssl-devel readline readline-devel curl git zlib zlib-devel libyaml libyaml-devel libsqlite3x libsqlite3x-devel sqlite libxml2-devel libxslt-devel autoconf ncurses-devel

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

    sudo yum install mysql mysql-libs

And after:

    gem install mysql2

For PostgreSQL:

    sudo yum install postgresql postgresql-libs

And after:

    gem install pg


Setup GEdit
===

**GMATE IS NOT YET SUPPORTED ON GNOME3. THIS IS A KNOWN PROBLEM AND, I HOPE, WILL BE FIXED SOON.**

For GEdit we'll use GMate plugin. In Terminal:

    sudo yum install pywebkitgtk python-sexy python-inotify ack
    git clone https://github.com/gmate/gmate.git
    cd gmate
    ./install.sh

Now open GEdit got Edit/Preferences menu and in Plug-ins check all. Now everything is ready.
