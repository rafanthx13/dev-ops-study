# Git

## Histórico

+ 2023-02-15 = Start projeto definitivo de git

## Links

+ (Várias Alias)[https://haacked.com/archive/2014/07/28/github-flow-aliases/]
+ [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/)

## Index & TOC

- [Git](#git)
  * [Padronização de Mensagens do Git](#padroniza--o-de-mensagens-do-git)
  * [Git Alias](#git-alias)
  * [Editar e Adicionar atalhos ao git](#editar-e-adicionar-atalhos-ao-git)
  * [Git Configs](#git-configs)
  * [Git Commands](#git-commands)
  * [Mensagem super irritante de erro em commit](#mensagem-super-irritante-de-erro-em-commit)
  * [.gitignore](#gitignore)


==============================================
==============================================
==============================================


## Padronização de Mensagens do Git

```
correct format: <type>[scope]: <subject>
  example: docs: update README to add developer tips
  MY EXAMPLE  : <type>: [verb] <content>
  
  verbs: add, create, remove, improve, refact, 

  type:
    feat     A new feature.
    fix      A bug fix.
    docs     Documentation only changes.
    style    Changes that do not affect the meaning of the code (white-space, formatting, ...)
    refactor A code change that neither fixes a bug nor adds a feature.
    test     Adding missing tests or correcting existing ones.
    chore    Changes to the build process or auxiliary tools and libraries such as documentation generation.
    perf     A code change that improves performance.
    ci       Changes to your CI configuration files and scripts.
    build    Changes that affect the build system or external dependencies (example scopes: gulp, npm).
    temp     Temporary commit that won't be included in your CHANGELOG.

  scope:
    Optional, can be anything specifying the scope of the commit change.
    For example $location, $browser, $compile, $rootScope, ngHref, ngClick, ngView, etc.
    In App Development, scope can be a page, a module or a component.

  subject:
    Brief summary of the change in present tense. Not capitalized. No period at the end.
````

Reprodução de : https://www.conventionalcommits.org/pt-br/v1.0.0-beta.4/

As palavras-chaves “DEVE” (“MUST”), “NÃO DEVE” (“MUST NOT”), “OBRIGATÓRIO” (“REQUIRED”), “DEVERÁ” (“SHALL”), “NÃO DEVERÁ” (“SHALL NOT”), “PODEM” (“SHOULD”), “NÃO PODEM” (“SHOULD NOT”), “RECOMENDADO” (“RECOMMENDED”), “PODE” (“MAY”) e “OPCIONAL” (“OPTIONAL”), nesse documento, devem ser interpretados como descrito na [RFC 2119](http://tools.ietf.org/html/rfc2119).

### Resumo 

1. A mensagem de commit DEVE ser prefixado com um tipo, que consiste em um substantivo, `feat`,`fix`, etc., seguido por um escopo OPCIONAL, e OBRIGATÓRIO terminar com dois-pontos e um espaço.
2. O tipo `feat` DEVE ser usado quando um commit adiciona um novo recurso ao seu aplicativo ou biblioteca.
3. O tipo `fix` DEVE ser usado quando um commit representa a correção de um problema em seu aplicativo ou biblioteca.

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

Exemplos:

```
fix(release): need to depend on latest rxjs and zone.js

The version in our package.json gets copied to the one we publish, and users need the latest of these.
```

```
docs(): update changelog to beta.5
```

### Descrições de Tags

+ `build`:  Alterações que afetam o sistema de construção ou dependências externas (escopos de exemplo: gulp, broccoli, npm)
+ `ci`: Alterações nos arquivos e scripts de configuração do CI (escopos de exemplo: Travis, Circle, BrowserStack, SauceLabs)..
+ `docs`: Somente alterações na documentação
+ `feat`: Um novo recurso
+ `fix`: uma correção de bug
+ `perf`: uma alteração de código que melhora o desempenho
+ `refactor`: uma alteração de código que não corrige um bug nem adiciona um recurso
+ `style`: alterações que não afetam o significado do código (espaço em branco, formatação, ponto e vírgula ausente etc.)
+ `test`: adicionando testes ausentes ou corrigindo testes existentes

### Outros Exemplos de Commits

```
feat(lang): adiciona tradução para português brasileiro
```

```
refactor(core): assert TNode is not a container when setting attribute on element (#37111)

This PR provides a more helpful error than the one currently present:
`el.setAttribute is not a function`. It is not valid to have directives with host bindings
on `ng-template` or `ng-container` nodes. VE would silently ignore this, while Ivy
attempts to set the attribute and throws an error because these are comment nodes
and do not have `setAttribute` functionality.

It is better to throw a helpful error than to silently ignore this because
putting a directive with host binding on an `ng-template` or `ng-container` is most often a mistake.
Developers should be made aware that the host binding will have no effect in these cases.

Note that an error is already thrown in Ivy, as mentioned above, so this
is not a breaking change and can be merged to both master and patch.
```
### Commit com mais de uma linha

Se o commit tem uma linha, use \" no final da linha

`commit -m "message"`

Se tem mais de uma linha use \'

````
$ commit -m ' fix: algo
> 
> algo
> 
'
````

Quando voc^der enter para dar um new-line vai descer com o síbmolo `>` continuando na mensagem do commit


### Dicas de descrição de commits

+ não use letra maiúscula a não ser em nome de classe
+ Sem pontuação
+ Começa com verbo no presente

**Exemplos**

```
$ git c "chore: add npm"

$ git c "chore: add typescript"
```

### Git Lib: `git-commit-msg-linter`

```
$ npm i -D git-commit-msg-linter
```

+ Vai garantir que meus commits vão respeitar a diretriz do **conventional commits**
+ para evitar commits fora do padrão...s


### Sair do `END`

Se você fizer `git l` e mostrar muita coisa na tela, no final, haverá os caracters `END` que vai travar tudo e não vai ter como sair com `CTRL+C`.

Para sari aperte `'q' ou'z'`

==============================================
==============================================
==============================================


## Git Alias


Listar atalhos do git
```
$ git config --list
```

**Git Config**

São as configurações do git. há 3 níveis e configurações:

+ `--system`: git para qualquer usuário
+ `--local`: para somente o projeto
+ `--global`: para o usuário atual e em qualquer projeto

**Por o VSCODE como editor do git**

```
git config --global core.editor code
```

**Editar configurações do git config**

```
git config --global --edit
```

Após isso, no `code` coloque a flag de `--wait` para garantir que o vscode rode corretamente



## Editar e Adicionar atalhos ao git

```
[alias]
	[alias]
	s = !git status -s
	p = !git pull
	c = !git add --all && git commit -m 
	l = !git log --pretty=format:'%C(blue)%h%C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
	send = "!f() { git add --all && git commit -m 'RandomCommit' && git push; }; f"
	k = !gitk --all &
	credential = !git config credential.helper store
```

+ s
  + Vai mostrar de forma resumida
  + $ git s
+ c
  + Vai fazer o add + commit numa mesma linha
  + `$ git c "re"`
+ l
  + Vai mostrar o log de forma resumida com só as informações interessante de forma a ocupar menos espaço
  + `$ git l`

==============================================
==============================================
==============================================


## Git Configs

Add Credenciais

````
git config credential.helper store
````

==============================================
==============================================
==============================================

## Git Commands

$ git commit --amend --no-edit
+ Comando para commitar sobre o commit anterior
	+ ammend: adaicionar ao commit anterior
	+ no-edit: nao abrir o editor para editar a mensagem
	+ Assim eu junto commits e evito repetir outra coisa

Iniciar Repositório
- `git init` : Voce cria o `/.git` uma pasta oculta (Voce pode configurar su máquinca para mostrar pastas ocultas mas em geral nao vai presisar). Nessa pasta ira ser salvo os snapshots do git, os commits
- Para remover um repositorio do git, basta deletar a pasta .git/, é mais facil fazer isso no bash

- `git status` : Mostra arquivos que nao estoa na área de estage e que nao estao comitados. A area de stage é onde o git começa a monitroar as alteraçoes. Se voce altera o arquivo ele ja sai do stage area, entao, toda vez tenho que dar add. 

- A vantagem é que asism posso separar arquivos para commit diferentes

- ` git add [arquivo]/ git add --all`: Adiciona arquivo no stage

- `commit` é como se fosse uma fotografia de seu arquivo, e o commit é o registro, é o aato de bater a foto. `git commit -m ´´[mensagem]´`

- Dependencias nao presisam ser versionadas, entao, colocamos no .gitignore. o .gitignore precisa ser versionado

  `echo "node_modules" > .gitignore`

  ```
  node_modules/
  ```

Criar arquivo README.md 
- `echo -e '#Titulo \n '#subtitulo\n\nInicio do projeto' > README.md` 
+ Cria do zero se nao existir e poe as tags e texto markdow rescrevendo o que esta la. Pod fazer append com >> no lugar de `>`

Renomear branch
````
git branch -m old_name new_name 
````

delete the old branch on remote - where <remote> is eg. origin
````
git push <remote> --delete old_name
````

push the new branch to remote         
````
git push <remote> new_name
````

+ Funciona sertinho com sua branh local
````
git branch -m nome_da_branch_antiga novo_nome
````
 Discartar mudanças do Git
 
 Discard all local changes, but save them for possible re-use later

  `git stash`

Discarding local changes (permanently) to a file

  `git checkout -- <file>`

Discard all local changes to all files permanently

  `git reset --hard`

  Se tudo der certo tente fazer um checkout forçadao
  
   checkout forçado
  
  `git checkout -f <branch_destiny>`
  
## Mensagem super irritante de erro em commit
  
  Quando aparecer o seguinte:
  
  please enter a commit message to explain why this merge is necessary ...
  
  Faça os seguintes passsos
1. press "i"
2. write your merge message
3. press "esc"
4. write ":wq"
5. then press enter


## .gitignore

 Dicas para escrever .gitignore e REAME.MD no git Bash Rapidamente

 .gitignore

- O arg `-e` serve para interpretar comandos com \\, como o `\\n` para quebra de linha
- `echo -e '.png\n .class\n node_modules' > .gitignore`: cria o .gitignore e ja coloca texto, se usar  `>> ` voce pode fazer um append