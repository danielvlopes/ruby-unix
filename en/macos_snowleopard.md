RUBY and RAILS on MacOSX SnowLeopard
===

Step by step guide to install Rails(last version) and Ruby (1.9.2) on MacOSX SnowLeopard. I'll use Textmate as text editor but you could use anything you want(TextEdit, Vim ou anything else).

**1º Installing XCode**

When install some gems you'll need a compiler and other development tools. In Mac OSX install disk you can optionally install the development tools that include XCode and the compiler. You can also download from Apple's site.

**2º Installing RVM**

OSX comes with Ruby and Rails pre-installed but I'll use RVM to have more controle over Ruby versions. Run the command below in Terminal.app :

    bash < <(curl -s https://rvm.beginrescueend.com/install/rvm)

**3º Loading RVM with your Terminal**

In Terminal type:

    mate ~/.bash_profile

On the first line put:

    echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"' >> ~/.bash_profile
    
Now you need to load the file (in Terminal run):

    . ~/.bash_profile
    
**4º Installing Ruby**

Run (this command will take a couple of minutes)

    rvm install 1.9.2
    
Now set ruby 1.9.2 as default for your user, in this way every time you load a new Terminal session Ruby 1.9.2 will be the default:

    rvm --default use 1.9.2
    
Now this should work:

    ruby -v
    
**5º Installing Rails**

    gem install rails
    
**6 ºMySQL(OPICIONAL)**

In development mode, most of the time, sqlite is enough but if you want to use MySQL the right gem is mysql2 (before install the gem you should install MySQL DMG from Oracle's site):

    gem install mysql2    
    
Text Editor
===

For text editing my choice is TextMate but this is a matter of taste and how MacOS don't come with a good and simple builtin Text Editor and XCode is not easy to setup to run well with Ruby you can choose anything you want (MacVim, Emacs or even IDE's).