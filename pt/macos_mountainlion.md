Ruby e Rails Mac OSX Mountain Lion
===

Este é um guia passo-a-passo para a instalação do Ruby 1.9.3 e da última versão do Rails, no Mac OSX Mountain Lion.

**1º Instalando o XCode**

Durante a instalação de algumas gems e pacotes serão necessárias algumas ferramentas que estão disponíveis no XCode, como por exemplo o git. O XCode está disponível na App Store, gratuitamente, então simplesmente abra a App Store e baixe-o.

Depois de instalar o XCode, abra-o, entre em "Preferences", aba "Downloads" e clique no botão "Install" do item "Command Line Tools" e espere a instalação. Depois disso, você já pode fechar o XCode.

Confira se tudo está ok, verificando a versão do git no terminal:

    git --version

**2º Instalando o RVM**

O Mac OSX já vem com o Ruby e o Rails instalados, mas utilizaremos o RVM para podermos instalar (de forma fácil) mais de uma versão do Ruby e ter mais controle das gems. Para instalar o RVM, rode no terminal:

    curl -L https://get.rvm.io | bash -s stable

**3º Instalando o Homebrew**

Homebrew é um gerenciador de pacotes para Mac OSX. Através dele, é possível instalar várias ferramentas úteis. Para instalar, rode no terminal:

    ruby <(curl -fsSkL raw.github.com/mxcl/homebrew/go)

Antes de instalar o Ruby 1.9.3, precisamos instalar o libksba e para isso, rode no terminal:

    brew install libksba

**4º Instalando o Ruby**

Rode o comando abaixo (pode demorar alguns minutos):

    rvm install 1.9.3

Defina o Ruby 1.9.3 (que você acabou de instalar) como o default. Dessa forma, seu terminal vai ignorar o Ruby que já vem no Mac OSX e vai passar a usar a versão nova:

    rvm --default 1.9.3

Para verificar se tudo está ok, rode o seguinte comando no terminal:

    ruby -v

**Instalando versões antigas do Ruby**

Caso você tenha problemas pra instalar versões antigas do Ruby, instale o gcc antigo:
    brew tap homebrew/dupes
    brew install apple-gcc42

Depois, adicione a linha a seguir no seu arquivo ~/.profile (ou similar):

    export CC=/usr/local/bin/gcc-4.2

E finalmente instale a versão antiga do Ruby que você precisa:

    CFLAGS="-I/opt/X11/include" rvm reinstall ree

Mais informações neste post: http://coderwall.com/p/dtbuqg

**5º Instalando o Rails**

    gem install rails

Para verificar se tudo está ok, rode o seguinte comando no terminal:

    rails -v

E pronto! Tudo está configurado!
