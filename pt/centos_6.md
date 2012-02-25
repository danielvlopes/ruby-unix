# RUBY e RAILS NO CentOS (6)

Passo a passo para a instalação do Rails (última versão) e Ruby (1.9.3) no CentOS. Também envolve aos ajustes do GEdit com instalação do GMate.

Instruções baseadas no passo a passo para Fedora 15.

## 1º Atualizando yum

Abra o terminal e rode:

    sudo yum update


## 2º Instalando GIT e Curl

Tente primeiramente instalar o git pelo yum:

    sudo yum install git curl

Caso ocorra erros de dependência tente instalar manualmente, veja a ultima versão do git em http://code.google.com/p/git-core/downloads/list substituindo git-x.x.x.x pela ultima versão:

    cd ~/
    wget http://git-core.googlecode.com/files/git-x.x.x.x.tar.gz
    tar -zxf git-x.x.x.x.tar.gz
    sudo rm git-x.x.x.x.tar.gz
    cd git-x.x.x.x
    ./configure
    make
    make install
    cd ..
    sudo rm -r git-x.x.x.x


## 3º Instalando RVM (Ruby Version Manager)

O RVM permite instalar e gerenciar várias versões do Ruby. Mas nós usaremos só uma:

    bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer)


## 4º Carregando RVM no seu Terminal

Execute no terminal o comando abaixo:

    source /usr/local/rvm/scripts/rvm

Confirme a instalacao executando o comando abaixo, (a saida deverá ser "rvm is a function"):

    type rvm | head -1


## 5º Instalando os outros pacotes essenciais

    rvm requirements

O comando acima ao final mostrará quais pacotes faltam, conforme VM desejada. Basta copiar as dependencias para ruby e colar no terminal ou copiar a linha abaixo:

    sudo yum install -y gcc-c++ patch readline readline-devel zlib zlib-devel libyaml-devel libffi-devel openssl-devel make bzip2 autoconf automake libtool bison iconv-devel ## NOTE: For centos >= 5.4 iconv-devel is provided by glibc


## 6º Instalando o Ruby

Rode o comando abaixo (poderá demorar alguns minutos)

    rvm install 1.9.3

Coloque o ruby 1.9.3 como default do seu user:

    rvm --default use 1.9.3

Agora o comando abaixo deve mostrar a versão do ruby:

    ruby -v


## 7º Instalando o Rails

    gem install rails

Confirme a instalação com o comando abaixo:

    rails -v

## 8º MySQL e PostgreSQL (OPICIONAL)

Para modo de desenvolvimento a maioria das vezes sqlite é suficiente e já foi instalado. Se você pretende usar MySQL a Gem correta é mysql2 mas antes deve rodar:

    sudo yum install mysql mysql-libs

Depois:

    gem install mysql2

Se pretende usar PostgreSQL faça:

    sudo yum install postgresql postgresql-libs

Depois:

    gem install pg


## Configurando GEdit

**O GMATE AINDA NÃO É COMPATÍVEL COM O GNOME3. ESSE É UM PROBLEMA CONHECIDO E, ASSIM ESPERO, EM BREVE SERÁ CORRIGIDO**

Para o GEdit usaremos o plugin GMate que tratará snippets, colorização e uma série de coisas úteis para o dia a dia. Para instalar o GMate basta executar os seguintes comandos no terminal:

    sudo yum install pywebkitgtk python-sexy python-inotify ack
    git clone https://github.com/gmate/gmate.git
    cd gmate
    ./install.sh

Abra o GEdit vá em Editar/Edit Preferências/Preferences e em Plug-ins habilite todos. Agora você pode criar sua primeira aplicação Rails e trabalhar com um bom editor.
