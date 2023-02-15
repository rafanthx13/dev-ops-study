# Comandos Linux

## Links

+ (10 Comandos para usar no seu dia a dia!)[https://www.tabnews.com.br/Lobo/dica-10-comandos-para-usar-no-seu-dia-a-dia]
+ (Seu Terminal Linux não será mais o mesmo!)[https://www.youtube.com/watch?v=k8SycT32-yA&ab_channel=Diolinux]
+ (bat: clone do cat com synatx highlight)[https://diolinux.com.br/sistemas-operacionais/bat-clone-cat-comando-linux.html]

## Artigo - Comandos top

**Template**

````sh

````

**Lista comandos mais usados**

> Infelismente é só a 1 letra do comando

````sh
history | awk '{a[$2]++}END{for(i in a){print a[i] " " i}}' | sort -rn | head
````

Print

````sh
338 git
236 sudo
69 npm
40 history
29 ls
29 jupyter
23 curl
15 python
15 cd
12 htop
````

**Árvore de sub-diretórios**

> este comando lista os sub-diretórios de uma pasta, sem necessidade de instalar nada!
> OBS: A saida é menor e mais compacto que o `tree`, pois ele coloca muito espaçamento apra cada pasta

````sh
ls -R | grep ":$" | sed -e 's/:$//' -e 's/[^-][^\/]*\//--/g' -e 's/^/   /' -e 's/-/|/'
````

Saida
````sh
   .
   |-aqui
   |-Icaro ONM
   |---CES - Conquistando o Emprego dos Sonhos - 2021
   |-----Modulo 1
   |-----Modulo 2
   |---O Mapa da Riqueza - Icaro de Carvalho - ONM - 2021
   |-Ignite Lab Node Nest Dez-2022
   |-Master Class para Vagas Internacionais
   |---Leandro Batista
   |---Lucas Galindo
   |-ULTRA TORRENTS
   |---Formacao.de.Inteligencia.Artificial
   |-----4 - Deep Learning I
   |-------6. Deep Neural Networks
   |-------7. Redes Neurais Convolucionais - Parte 1
   |-------8. Redes Neurais Convolucionais - Parte 2
   |-----5 -  Deep Learning II
   |-------01 Introdução

````

**Criar Pasta e entrar nela**

> OBS: `$_` é o último argumento digitado do comando que está se escrevendo, no caso, será o nome da pasta
> OBS: `&&` concatena comandos

````sh
mkdir new-folder && cd $_
````

**Pesquisar no histórico**

Muito útil para encontrar um comando específico já utilizado

````sh
history | grep [texto de busca]
````

**Listar arquivos pesados**

Este comando lista os 10 arquivos mais pesados em seu diretório atual

````sh
du -ahx . | sort -rh | head -10
````

**Exibir processos**

Mostra todos os processos que estão rodando:
````sh
ps aux
````

**Encontrar caminho dos comandos linux**

> Este comando mostra o diretório de onde um programa está instalado
> OBS: `which` mostra o caminho completo de um comando, mas a busca se restringe aos diretórios que estão na variável de ambiente PATH (que pode inclusive ter diretórios que whereis não procura). Já `whereis` procura também por outros arquivos relacionados, como fontes e man pages ("manuais"), independente do que está no PATH.

Executável:

````sh
which [programa]
````

Binário:

````sh
whereis [programa]
````

Exemplo para o comando do terminal `npm`

````sh
$ which npm
# OUTPUT ==> /usr/local/bin/npm
$ whereis npm
# OUTPUT ==> npm: /usr/bin/npm /usr/local/bin/npm /usr/share/man/man1/npm.1
```

## `ALIAS` de comandos linux

Você deve editar o arquivo `~/.baschrc` e colocar os *alaias* lá dentro. 

Em boa parte das distribuiçôes linux tem uma linha escrita `~/.bash_aliases`. O linux recomenda você colocar seus alaias nesse arquivo separado, para não bagunçar o arquivo principal .baschrc.  Caso nâo tiver esse arquivo .bash_aliases, crie ele.

Dentro do `.bash_aliases` coloque os alais e use \# para comentar e separar em blocos

**Lista de comandos do Dio Linux**

````
### Abre este arquivo de configrauçÂo com gedit

alias aliasconf='gedit ~/.bash_aliases'

### Comandos do dio Linux

````
alias cat='batcat'
alias ..='cd ..'
alias gh='history | grep'

````

## Bat: cat com syntax highlight

Como baixar:
$ wget https://github.com/sharkdp/bat/releases/download/v0.9.0/bat_0.9.0_amd64.deb
$ sudo dpkg -i bat_0.9.0_amd64.deb

Restart e use `$ batcat filename`


==============================

## ?????



## Terminal

- Chamado de cmd, prompt de comando ou cli (command-line)
  - CLI que significa *command-line interface* (interface de linha de comando), ele é resumidamente uma interface que suporta passagem de parâmetros via linha de comando em terminais e/ou semelhantes.
- Você abre o prompt do windows com `Windows + r (executar)  ` e depois digitar cmd (No windows)
- Porém, saber os comandos do teminal do Windows não é muito útil pois diferem do Linux, então, de preferência, instale use o terminal do **Git Bash** pois ele simula os comandos do UNIX que é universal para qualquer SO.

## Terminal Git Bash

- O terminal do Git bash simula os comandos do UNIX, que são os mesmo do Mac e Linux
- `tab` : Tanto no git bash como windows, voce pode usa `tab` para auto-preencher com o nome de arquivo/pasta (de acordo com o local em que está) ou para commandos. 
- `Home ~ ` qual longe esta do diretorio home, que é a pasta do Rafael/ no meu caso 


- `up e down` : Voce poode suar as teclas `up` `down` para usar um ultimo comando já digitado
- Para qualque comando, voce pode dar:
  - `[command] --help` que vai listar informaçao sobre o comandos e todos os seus parametros adicionais

##### Comandos

`pwd` : print work directory : print o caminho completo até onde se estar

`cl`: limpa a tela ou `clear` (Pode ser feito com `CTRL + L`)

`ls` : lista arquivos do diretorio atual

`ls -a` : Lista pastas e arquivos e tambem pastas e arquivos ocultas (que começam com `.` como /git)

`ls -a -l` : Alem de lsitar tudo, voce lista tambem outras informações

`cd [nome_pasta]` (change directory)

`cd ..`: Volta um nível acima

`cd ~` : Atalho para ir para a pasta home

`mkdir [Nome_pasta]` : Cria a pasta

`echo ` : Serve para escrever, por padrao escreve na tela

`echo [escreve algo] > index.html` : Vai escrever no arquivo index.html, para isso voce usa o > index.html. Ele reescreve todo o arquivo

`echo [something] >> arquivo` faz um *append*, ou seja, o que for digitado é adicionado no fim do arquivo

`touch [arquvivo.ext]` cria arquivo vazio

`cat index.html` vai mostrar o que esta escrito noa rquivo index.html

`rm [arquiv.ext]` apaga o arquivo

`mv [file] [folder]`: Move arquivo para outra pasta

- Voce tambem pode criar varias pastas como `mkdir`, isso torna até mais facil de criar pasta do que cliacando e pondo nome
  - `mkdir pasta1 pasta2 pasta3 pasta4 past5`

`rmdir {Nome_pasta}`: Remove pasta, so que só consegue remover uma pasta vazia. Para remover os arquivos e a pasta tambem, podemos fazer `rm -rf [pasta]` o r quer dizer recurso e o f de force para forçar a remoçao, assim vai remover arquivos e a pasta

###### Varios Comandos

- `&&` : pode usar o operador `&&` para executar varios comandos numa mesma linha
  - Exemplo: `mkdir Projteo && cd Projeto` : Assim vai criar e entrar na pasta no git bach 







=================== MY COMANDS

# Comandos Linux

## Principais Comandos

=> Desligar bancos de dados
$ sudo systemctl stop mysql.service && sudo service postgresql stop

=> Desativar processo que deixam lento
$ sudo rmmod intel_powerclamp

=> Configurara para lembrar do Cache
$ git config credential.helper store (so usar isso antes do 1 commit)

=> Remover Cache do pip (pois ocupa espaço)
$ rm -rf ~/.cache/pip

+ .ipynb to .html
  - ipython nbconvert — to script pyfile.ipynb 
+ .ipynb to .py
  - ipython nbconvert pyfile.ipynb --to python
+ ShutDown MySql/postgres
  - systemctl stop mysql.service
  - sudo service postgresql stop
+ Problema da Wifi
 - service lightdm restart
+ Salvar senha do Git
 - git config credential.helper store
+ Tirar problema de kindle_inject:
 - sudo rmmod intel_powerclamp
+ GIT
 - git add --all && git commit -m "a commit" && git push
 - git init && git add --all & git commit -m "First Commit" && git remote add origin https://github.com/rafanthx13/myText.git && git config credential.helper store & git push -u origin master

+ `clear` : limpa a tela 
+ `ls` : lista arquivos da pasta
 - `ls -a`: lista arquivos e arquivos escondidos da pasta
+ `gedit a_file.extention`: Qualquer arquivo pode ser aberto com o gedit, melhor que fazer o nano que abre no terminal.
+ `cd ..`: Sai da pasta
+ CLTR + ALT + T : Atalho para abrir o terminal
+ pwd : mostra o file_path do diretorio em que se esta
+ tree: mostra diretorio uma árqvore de todos os arquivos a partir de onde está de forma recursiva (mostra tudo, cuidado  com se tiver node_modules, vai mostrar tudo)

+ tty terminal
 - O ubuntu tem terminais 6 padrões que são acessados a partir de CTRL+ALT+(F1 à F6) para sair deles use CTRL+ALT+F7

Extrar arquivos rar(quando der problema)
+ Parece que o 'extrair aqui' do unbuntu as vezes trava para arquivos .rar. Para funcionar baie unrar
+ sudo apt-get install unrar
+ execute: unrar x file_un.rar 

+ Dica de escrever nome com espaço/space " "
 - Há 2 forma de fazer:
   1. Usar \  para representar o espaço, exemplocd October\ Fall
   2. Usar "" ou '' > cd 'October Fall' ou > cd "October Fall"

+ Desligar tela do Linux
 - sleep 1 && xset dpms force off

+ Configurar o Mouse
 - xset mouse m 1 || #Movimento mais lento
 - xset mouse m 5 || #Movimentar mais rapidamente

+ Trocar Tema
 - Busque nos apps: gnome tweak (Ferramentas de Ajustes)

+ Zipar um Arquivo
 - `zip nome_arquivo_zipado.zip file1 fil2 file3`
 - Para zipar uma pasta, coloque -r depois do 'zip' e antes de 'nome_file.zip'

+ Gerenciador de Tarefas do Ubuntu / CTRL + SHIFT + T 
 - Busque por: gnome-system-monitor

+ `chmod 777 yourfile.txt`
 - Habilitar todas as permissões
 - Se for uma pasta tem que colocar nome/ (por a barra no final)

+ Linguagem C
 - gcc --help
 - Compilar:
  * gcc programa.c -o executavel
 - Executar:
  * ./executavel

+ Copiar arquivo
  - cp [OPTION] Source Destination

+ Saber se é 32bits ou 64bits
  - uname -m

CONFIGURAR VARIÁVEIS DE AMBIENTE NO UBUNTU
+ Você terá que abrir um arquivo e editar os diretorios de onde ele vai ler:
 - Acessar o arqguivo: `gedit ~/.bashrc`
+ No *final** do arquivo você coloca (por exemplo, o anaconda):
 - export PATH=~/anaconda3/bin:$PATH
Problema no Anaconda
+ Executei esse código: `export PATH=~/anaconda3/bin:$PATH` além de outros
+ https://stackoverflow.com/questions/35313876/after-installing-with-pip-jupyter-command-not-found
+ verificar se ta tudo certo: `conda info`

Executar Jupyter
+ export PATH=~/anaconda3/bin:$PATH && jupyter notebook

lista se tem um processo na porta 8080
$ lsof - -i :8080

mata o processo 'pid'
$ kill -9 pid

Permisoes recursiva numa pasta
$ sudo chmod -R  777  nlw-mobile/ 

Lisar arquivos mais pesados
$ sudo  du -a /home/rhavel/Documentos | sort -n -r | head -n 40
$ du -aBM 2>/dev/null | sort -nr | head -n 50 | more

$ history
+ lista uma lista enorme dos últimos comandas





==================================

# Comando lnux

## Links

https://www.youtube.com/watch?v=M7CkkeECodk&ab_channel=Rocketseat

CTRL + L : dar o coamndo clean e limpa a tela

+ Hyper + Oh My Zsh + Spaceship + Theme Dracula



Linux/GitBash
+ Entrar numa pasta: `cd NomeDaPasta/`
+ Subir de diretorio: `cd ..`
+ Ver o que tem no diretorio: `dir`a


cat [file.extension]
   + Serve para abirir o conteudo do arquivo, semelhante ao Notepad++

CTRL + C
   + kill o ultimo processo executado no cmd

dir
   + lsita diretorios (arquivos e pastas de onde se esta

cd nome_pasta
   + entra na pasta

------------
ATALHOS
+ CLTR + L: Lmpa  teclado
+ Seta para cima e Baixo: navegar pelos comandos anteriores

COMANDOS
+ pwd : mostra o caminho da pasta que está atualmente
+ mkdir: make diretory
+ ls: lista tudo quue tem no diretorio atual
+ ls -l: mostra mais informaçôes
+ ls -a: ver arquivos até mesmo ocultos (com '.' na frente)
+ ls -la : usa os dois
+ touch: criar arquivos
  + Criar varios arquivos com mesma extensão : touch {sobre,produtos,contato}.html
+ nano:
  + editor do terminal, usado sobre arquivo como `nano index.html`
  + Ele mostra talahos em baixo, onde ^ = CRTL
   + Assim ^O = Salvar
   + ^X = Sair
+ cat: ver arquivo
+ cd
   + cd directory
   + cd .. :: sair
   + cd ... :sube doi niveis
   + cd .... : sobre 3 niveis

+ cp : copiar