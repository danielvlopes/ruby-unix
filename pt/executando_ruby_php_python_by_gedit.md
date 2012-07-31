# EXECUTANDO RUBY DIRETO DO GEDIT

Passo a passo para a instalação e configuração do GEdit no Ubuntu.

## 1º Atualizando apt-get

Abra o terminal e rode:

    sudo apt-get update

## 2º Configurando GEdit

Para o GEdit usaremos o plugin GMate que tratará snippets, colorização e uma série de coisas úteis para o dia a dia. Ainda no Terminal:

    sudo apt-add-repository ppa:ubuntu-on-rails/ppa
    sudo apt-get update
    sudo apt-get install gedit-gmate

Abra o GEdit vá em Editar/Edit Preferências/Preferences e em Plug-ins habilite todos. 


## 3º Executando Ruby pelo GEdit

Primeiro você tem que habilitar um Plugins, que aceita inserir comandos no GEdit. 
    
    Para isso vai em: "Edit > Preferences > Plugins > External Tool ou ( Ferramentas externas ) " 

Feito isso, seu GEdit, já aceita criar novos comandos, como por exemplo, apertar F5 e executar um código Ruby.


Agora, temos que criar o comando para essa execução dos códigos Ruby. Basta ir em "Tools > Manager External Tools". Com o gerenciador de comandos do GEdit aberto, é possível criar comando para execução. É só clicar o sinal de "+" ou "Adicionar" e adicione um novo comando. 

Informe o nome do comando, por exemplo "Ruby" e copie e cole no campo "Command(s)" o código abaixo. Em seguida, escolha a tecla de atalho, por exemplo "F5". 
No campo de seleção de entrada coloca "Documento Atual" e no de saida, "Mostrar no painel inferior". 
Deixe para "todos os documento e todas as linguagem" na área de Aplicabilidade.

		################################## 
		#!/usr/bin/env ruby 
		
		current_file = ENV['GEDIT_CURRENT_DOCUMENT_PATH'] 
		
		if not current_file 
		puts "The current file cannot be runned." 
		elsif current_file =~ /\.(php|py|rb|html|htm|xml)$/i 
		commands = { 
		'php' => "php -f #{current_file}", 
		'rb' => "ruby #{current_file}", 
		'py' => "python #{current_file}", 
		'browser' => "gnome-open #{current_file}" 
		} 
		extension = $1 
		extension = 'browser' if ['xml', 'html', 'htm'].include?(extension) 
		
		command = commands[extension] 
		
		puts "Running command #{command}\n\n" 
		system(command) 
		end 


Fecha e cria um código de puts "Estou executando Ruby pelo GEdit!!" e veja seja feliz!!