# RUBY e RAILS NO UBUNTU (11.X)

Passo a passo para a instalação do Rails (última versão) e Ruby (1.9.3) no Ubuntu. Também envolve aos ajustes do GEdit com instalação do GMate.

## 1º Atualizando apt-get

Abra o terminal e rode:

    sudo apt-get update

## 2º Instalando GIT e Curl

    sudo apt-get install build-essential git-core curl

## 3º Instalando RVM (Ruby Version Manager)

O RVM permite instalar e gerenciar várias versões do Ruby. Mas nós usaremos só uma:

    bash < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer)

## 4º Recarregando RVM no seu Terminal

Execute o código abaixo para garantir que o RVM será carregado ao abrir um novo terminal:

    echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"' >> ~/.bashrc

Recarregue o arquivo de configuração (no Terminal digite):

    . ~/.bashrc

## 5º Instalando os outros pacotes essenciais

    sudo apt-get install build-essential openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison subversion

## 6ºInstalando o Ruby

Rode o comando abaixo (vai demorar alguns minutos)

    rvm install 1.9.3

Coloque o ruby 1.9.3 como default do seu user:

    rvm --default use 1.9.3

Agora o comando abaixo deve funcionar:

    ruby -v
    ruby 1.9.3p0 (2011-10-30 revision 33570) [x86_64-linux]

## 7º Instalando o Rails (sempre rode o comando gem sem SUDO)

    gem install rails

## 8º Primeira aplicação

Agora você pode testar criando a sua primeira aplicação:

    rails new minha_nova_app

Agora basta navegar para o diretório da minha_nova_app e iniciar o servidor. No entanto desde o Rails 3.1 é necessário uma runtime de javascript. Para isso abra o arquivo Gemfile de dentro do diretório da sua app e acrescente:

    gem 'execjs'
    gem 'therubyracer'

Salve, feche e rode o comando abaixo no Terminal:

    bundle install

Agora você pode rodar:

    rails server

## Installing Databases (OPCIONAL)

### Para MySQL
Para modo de desenvolvimento, na maioria das vezes, o sqlite é suficiente e já foi instalado. Se você pretende usar MySQL a Gem correta é a mysql2, mas antes deve rodar:

    sudo apt-get install libmysqlclient16-dev

Depois:

    gem install mysql2

### Para PostgreSQL
O PostgreSQL normalmente é utilizando em aplicações com deploy no Heroku. Antes de instalar a gem você deve instalar o banco de dados da seguinte forma:
Se pretende usar PostgreSQL faça:

    sudo apt-get install libpq-dev

Depois:

    gem install pg

### Para MongoDB:
O pacote do mongodb no repositório padrão do Ubuntu normalmente estão desatualizados, é aconselhável instalar a versão do repositório da 10Gen, mas infelizmente eles não tem um PPA. Para adicionar o repositório deles, antes você deve copiar a chave e depois adicionar o endereço na sua lista:

    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10
    sudo sh -c "echo 'deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen' >> /etc/apt/sources.list"

Depois disso, atualize a lista de pacotes e instale o mongo:

    sudo apt-get update 
    sudo apt-get install mongodb-10gen

Essas instruções irão baixar e instalar o pacote, criar um usuário mongodb e configurá-lo para rodar como um serviço usando o upstart. Você pode verificar o status e iniciar/parar o banco com os seguintes comandos:

    service mongodb status
    sudo service mongodb stop
    sudo service mongodb start

Tenha em mente que o MongoDB irá criar arquivos de journaling em /var/lib/mongodb/journal que ocuparão um total de 3.1 GB, garanta que há espaço suficiente no seu disco. Você pode ver as instruções oficiais em http://www.mongodb.org/display/DOCS/Ubuntu+and+Debian+packages

# Configurando GEdit

Para o GEdit usaremos o plugin GMate que tratará snippets, colorização e uma série de coisas úteis para o dia a dia. Ainda no Terminal:

    sudo apt-add-repository ppa:ubuntu-on-rails/ppa
    sudo apt-get update
    sudo apt-get install gedit-gmate

Abra o GEdit vá em Editar/Edit Preferências/Preferences e em Plug-ins habilite todos. Agora você pode criar sua primeira aplicação Rails e trabalhar com um bom editor.
