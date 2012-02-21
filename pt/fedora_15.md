RUBY e RAILS NO FEDORA (15)
===

Passo a passo para a instalação do Rails (última versão) e Ruby (1.9.2) no Fedora. Também envolve aos ajustes do GEdit com instalação do GMate.

**1º Atualizando yum**

Abra o terminal e rode:

    sudo yum update

**2º Instalando GIT e Curl**

    sudo yum install git curl

**3º Instalando RVM (Ruby Version Manager)**

O RVM permite instalar e gerenciar várias versões do Ruby. Mas nós usaremos só uma:

    bash < <(curl -s https://rvm.beginrescueend.com/install/rvm)

**4º Carregando RVM no seu Terminal**

Execute no terminal o comando abaixo:

    echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"' >> ~/.bashrc

Agora basta recarregar o arquivo (no Terminal digite):

    . ~/.bashrc

**5º Instalando os outros pacotes essenciais**

    rvm notes

Comando acima ao final mostrará quais pacotes faltam. Basta copiar e colar no terminal ou copiar a linha abaixo:

    sudo yum install bison openssl openssl-devel readline readline-devel curl git zlib zlib-devel libyaml libyaml-devel libsqlite3x libsqlite3x-devel sqlite libxml2-devel libxslt-devel autoconf ncurses-devel

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

    sudo yum install mysql mysql-libs

Depois:

    gem install mysql2

Se pretende usar PostgreSQL faça:

    sudo yum install postgresql postgresql-libs

Depois:

    gem install pg

Configurando GEdit
===

**O GMATE AINDA NÃO É COMPATÍVEL COM O GNOME3. ESSE É UM PROBLEMA CONHECIDO E, ASSIM ESPERO, EM BREVE SERÁ CORRIGIDO**

Para o GEdit usaremos o plugin GMate que tratará snippets, colorização e uma série de coisas úteis para o dia a dia. Para instalar o GMate basta executar os seguintes comandos no terminal:

    sudo yum install pywebkitgtk python-sexy python-inotify ack
    git clone https://github.com/gmate/gmate.git
    cd gmate
    ./install.sh

Abra o GEdit vá em Editar/Edit Preferências/Preferences e em Plug-ins habilite todos. Agora você pode criar sua primeira aplicação Rails e trabalhar com um bom editor.
