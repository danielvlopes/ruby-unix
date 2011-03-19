RUBY e RAILS NO MacOSX SnowLeopard
===

Guia passo a passo de instalação do Rails (última versão) e Ruby (1.9.2) no MacOSX SnowLeopard. Eu utilizarei o Textmate como Editor mas você pode utilizar qualquer um que desejar (TextEdit, Vim ou qualquer outro).

**1º Instalando XCode**

Durante a instalação de algumas gems e pacotes será necessário um compilador. Ele está disponível através do SDK de desenvolvimento da Apple no DVD do Sistema Operacional ou baixando o XCode no site da Apple.

**2º Instalando RVM**

OSX já vem com Ruby e Rails instalados mas utilizaremos o RVM para termos maior controle sobre versão do Ruby e Gems. Rode o comando abaixo no Terminal.app :

    bash < <( curl http://rvm.beginrescueend.com/releases/rvm-install-head )

**3º Carregando RVM no seu Terminal**

Ainda no Terminal digite 

    mate ~/.bash_profile

Coloque a primeira linha como abaixo, salve e feche:

    echo '[[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"' >> ~/.bash_profile
    
Agora basta recarregar o arquivo (no Terminal digite):

    . ~/.bash_profile
    
**4º Instalando o Ruby**

Rode o comando abaixo (vai demorar alguns minutos)

    rvm install 1.9.2
    
Coloque o ruby 1.9.2 como default do seu user, dessa forma seu terminal vai ignorar o Ruby da Apple:

    rvm --default use 1.9.2
    
Agora o comando abaixo deve funcionar:

    ruby -v
    
**5º Instalando o Rails**

    gem install rails
    
**6 ºMySQL (OPICIONAL)**

Para modo de desenvolvimento a maioria das vezes sqlite é suficiente e já foi instalado. Se você pretende usar MySQL a Gem correta é mysql2 (instale a Gem depois de instalar o DMG do MySQL):

    gem install mysql2    
    
Configurando Editor de Texto
===

Como Editor de Texto utilizo o Textmate mas editor é uma questão de gosto e aprender a dominar o que escolheu. Como MacOS não possui nenhum editor gráfico mais robusto por default e o XCode não é simples de configurar para Ruby vamos deixar a decisão entre qual editor com você.