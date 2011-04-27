RUBY e RAILS NO UBUNTU (10.10)
===

Passo a passo para a instalação do Rails (última versão) e Ruby (1.9.2) no Ubuntu. Também envolve aos ajustes do GEdit com instalação do GMate.

**1º Atualizando apt-get**

Abra o terminal e rode:

    sudo apt-get update

**2º Instalando GIT e Curl**
    
    sudo apt-get install build-essential git-core curl
    
**3º Instalando RVM (Ruby Version Manager)**

O RVM permite instalar e gerenciar várias versões do Ruby. Mas nós usaremos só uma:

    bash < <(curl -s https://rvm.beginrescueend.com/install/rvm)

**4º Carregando RVM no seu Terminal**

Abrindo o arquivo .bashrc:

    gedit ~/.bashrc

Coloque a primeira linha como abaixo, salve e feche:

    echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"' >> ~/.bashrc
    
Agora basta recarregar o arquivo (no Terminal digite):

    . ~/.bashrc

**5º Instalando os outros pacotes essenciais**

    rvm notes
    
Comando acima ao final mostrará quais pacotes faltam. Basta copiar e colar no terminal ou copiar a linha abaixo:

    sudo apt-get install build-essential bison openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev
    
**6ºInstalando o Ruby**

Rode o comando abaixo (vai demorar alguns minutos)

    rvm install 1.9.2
    
Coloque o ruby 1.9.2 como default do seu user:

    rvm --default use 1.9.2
    
Agora o comando abaixo deve funcionar:

    ruby -v
    ruby 1.9.2p136 (2010-12-25 revision 30365) [x86_64-linux]
    
**7º Instalando o Rails**

    gem install rails
    
    
**8ºMySQL e PostgreSQL (OPICIONAL)**

Para modo de desenvolvimento a maioria das vezes sqlite é suficiente e já foi instalado. Se você pretende usar MySQL a Gem correta é mysql2 mas antes deve rodar:

    sudo apt-get install libmysqlclient16-dev 

Depois:

    gem install mysql2
    
Se pretende usar PostgreSQL faça:

    sudo apt-get install libpq-dev 

Depois:

    gem install pg
    
    
Configurando GEdit
===

Para o GEdit usaremos o plugin GMate que tratará snippets, colorização e uma série de coisas úteis para o dia a dia. Ainda no Terminal:

    sudo apt-add-repository ppa:ubuntu-on-rails/ppa
    sudo apt-get update
    sudo apt-get install gedit-gmate
    
Abra o GEdit vá em Editar/Edit Preferências/Preferences e em Plug-ins habilite todos. Agora você pode criar sua primeira aplicação Rails e trabalhar com um bom editor.
