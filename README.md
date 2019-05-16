# EFAProg2019
## Reposit�rio `git` da turma EFA NS - Programador de Inform�tica (2019-2010). 

O objetivo principal deste reposit�rio privado � ajudar os formandos desta turma a familiarizarem-se com o GitHub, com o conceito de controlo de vers�es e com a utiliza��o b�sica do comando `git`. Adicionalmente, todos os membros da turma est�o convidados a dar o seu contributo para os conte�dos deste reposit�rio, adicionando mais dicas ou propondo altera��es a algum dos guias ou programas existentes.

## 1. ANTES DE COME�AR: Instalar o comando `git`

O comando `git` � um programa de linha de comandos que pode ser instalado nos v�rios sistemas operativos e que permite interagir com reposit�rios git. Existem IDEs e outras aplica��es que oferecem interfaces de ambiente gr�fico (GUI), mas neste momento basta usar a linha de comandos, que muitas vezes � at� mais pr�tica.


## 2. Reposit�rios
### a) Criar uma c�pia local de um reposit�rio (clone)

Quando pretendemos criar uma c�pia local de um reposit�rio remoto, para explorarmos o c�digo e a documenta��o no nosso pr�prio computador, para compilarmos e usarmos a aplica��o ou para posteriormente colaborarmos com esse projeto, utilizamos o comando `git clone`:

```
$ git clone https://github.com/victordomingos/EFAProg2019
Cloning into 'EFAProg2019'...
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (12/12), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 12 (delta 2), reused 3 (delta 1), pack-reused 0
Unpacking objects: 100% (12/12), done.
```

Este comando ir� criar uma nova pasta na pasta de trabalho atual, contendo c�pias de todos os ficheiros que se encontravam no reposit�rio. Por isso, pode ser boa ideia usar antes o comando `cd` para mudar para a pasta onde vamos guardar os nossos v�rios reposit�rios `git`.


### b) Criar um novo reposit�rio local

Se o que pretendemos � criar um novo reposit�rio no nosso pr�prio computador, mesmo que posteriormente o pretendamos disponibilizar atrav�s do Github ou de outro servidor, primeiro precisamos de criar a pasta do projeto (caso ainda n�o exista). De seguida, usamos o comando `cd` para irmos para essa pasta. Finalmente, o seguinte comando ir� inicializar um novo reposit�rio local a partir da pasta do projeto:

```
$ mkdir Brinquedo6
$ cd Brinquedo6/
$ git init
Initialized empty Git repository in C:/Users/victor/dev/Brinquedo6/.git/
```


### c) Criar um novo reposit�rio local a partir de uma pasta existente

Se j� temos uma pasta no nosso pr�prio computador que queremos transformar num reposit�rio, tamb�m � poss�vel. Primeiro inicializamos o reposit�rio com `git init` e, seguidamente, adicionamos o seu conte�do `git add .` (este comando adiciona todo o conte�do da pasta atual). O comando `git commit`, que exemplificaremos mais abaixo, guardar� esse estado inicial do reposit�rio.



## 3. Alterar ficheiros num reposit�rio

### a) Obter as altera��es mais recentes a partir do reposit�rio remoto

Para garantir que estamos a trabalhar com a vers�o mais recente do projeto, isto �, que o c�digo no nosso reposit�rio local est� sincronizado com o reposit�rio remoto, come�amos por navegar at� � pasta do reposit�rio e usamos o comando `git fetch`.

```
$ cd EFAProg2019/
$ git fetch
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
From https://github.com/victordomingos/EFAProg2019
   ed77901..121f33d  master     -> origin/master
```

O comando `git status` permite-nos perceber se h� altera��es pendentes:

```
$ git status
On branch master
Your branch is behind 'origin/master' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working tree clean

```

Havendo altera��es mais recentes no reposit�rio remoto, o comando `git pull` atualiza o nosso reposit�rio local com essas mesmas altera��es.

```
$ git pull
Updating ed77901..121f33d
Fast-forward
 README.md | 14 ++++++++++++--
 1 file changed, 12 insertions(+), 2 deletions(-)

$ git status
On branch master
Your branch is up to date with 'origin/master'.

nothing to commit, working tree clean
```




### b) Enviar para o reposit�rio remoto as altera��es locais

Depois de efetuar altera��es no nosso reposit�rio local, por exemplo, criando, apagando ou mudando o nome a ficheiros, ou editando alguns deles, podemos guardar o estado atual com uma opera��o designada `commit`. Mas primeiro precisamos de preparar esse `commit`, adicionando as pastas e/ou ficheiros a considerar:

```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")

$ git add README.md
```

Uma vez mais, o comando `git status` permite-nos consultar as altera��es pendentes ou, neste caso, em prepara��o:

```
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   README.md
```

Com `git commit` guardamos o estado atual do reposit�rio (relativamente aos ficheiros/pastas que adicionamos com `git add`):

```
$ git commit -m "Conte�do adicional no ficheiro README.md"
[master ef23443] Conte�do adicional no ficheiro README.md
 1 file changed, 131 insertions(+), 94 deletions(-)
 rewrite README.md (67%)
```

Neste momento, uma consulta r�pida ao `git status` esclarece que apesar de n�o haver ficheiros ou pastas para registar num novo `commit`, o nosso reposit�rio est� adiantado em rela��o ao reposit�rio remoto:

```
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
``` 

Para enviar as nossas altera��es para o reposit�rio remoto (neste caso o GitHub), basta usar o comando `git push`:

```
$ git push
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 2 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 382 bytes | 95.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/victordomingos/EFAProg2019
   c638269..cb2faf6  master -> master
```

## Contribuir

Este guia, cuja elabora��o se encontra em curso, � uma introdu��o muito sucinta a uma ferramenta complexa. H� claramente muitos aspetos por explicar e diversos procedimentos que seria interessante abordar. Assim, quaisquer sugest�es de melhoramento deste documento ser�o muito bem-vindas. Erros, quest�es e ideias podem ser submetidos na p�gina [Issues](https://github.com/victordomingos/EFAProg2019/issues).

Por outro lado, se tem j� alguma conhecimento que gostaria de partilhar, sobre controlo de vers�es e colabora��o com `git`, os seus [Pull requests](https://github.com/victordomingos/EFAProg2019/pulls) ser�o muito bem-vindos. Dicas introdut�rias poder�o ser acrescentadas a este mesmo ficheiro. J� explica��es mais extensas ou mais aprofundadas dever�o ser submetidas como ficheiros separados, por temas.