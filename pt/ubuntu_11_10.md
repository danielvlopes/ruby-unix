RUBY e RAILS NO UBUNTU (11.X)
===

Passo a passo para a instalação do Rails (última versão) e Ruby (1.9.2) no Ubuntu. Também envolve aos ajustes do GEdit com instalação do GMate.

**1º Atualizando apt-get**

Abra o terminal e rode:

    sudo apt-get update

**2º Instalando GIT e Curl**

    sudo apt-get install build-essential git-core curl

**3º Instalando RVM (Ruby Version Manager)**

O RVM permite instalar e gerenciar várias versões do Ruby. Mas nós usaremos só uma:

  curl -L https://get.rvm.io | bash -s stable

**4º Recarregando RVM no seu Terminal**

Basta recarregar o arquivo (no Terminal digite):

    . ~/.bashrc

**5º Instalando os outros pacotes essenciais**

    sudo apt-get install build-essential openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion

**6ºInstalando o Ruby**

Rode o comando abaixo (vai demorar alguns minutos)

    rvm install 1.9.3

Coloque o ruby 1.9.3 como default do seu user:

    rvm --default use 1.9.3

Agora o comando abaixo deve funcionar:

    ruby -v

**7º Instalando o Rails (sempre rode o comando gem sem SUDO)**

    gem install rails

**8º Primeira aplicação **

Agora você pode testar criando a sua primeira aplicação:

    rails new minha_nova_app

Agora basta navegar para o diretório da minha_nova_app e iniciar o servidor. No entanto desde o Rails 3.1 é necessário uma runtime de javascript. Para isso abra o arquivo Gemfile de dentro do diretório da sua app e acrescente:

    gem 'execjs'
    gem 'therubyracer'

Salve, feche e rode o comando abaixo no Terminal:

    bundle install

Agora você pode rodar:

    rails server

**MySQL e PostgreSQL (OPICIONAL)**

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
