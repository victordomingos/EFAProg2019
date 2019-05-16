
# Repositório da turma EFA NS - Programador(a) de Informática (2019/2020)

O objetivo principal deste repositório é ajudar os formandos desta turma a familiarizarem-se com o GitHub, com o conceito de controlo de versões e com a utilização básica do comando `git`. Adicionalmente, todos os membros da turma estão convidados a dar o seu contributo para os conteúdos deste repositório, adicionando mais dicas ou propondo alterações a algum dos guias ou programas existentes.


## 1. ANTES DE COMEÇAR: Instalar o comando `git`

O comando `git` é um programa de linha de comandos que pode ser instalado nos vários sistemas operativos e que permite interagir com repositórios git. Existem IDEs e outras aplicações que oferecem interfaces de ambiente gráfico (GUI), mas neste momento basta usar a linha de comandos, que muitas vezes é até mais prática. Os instaladores do comando `git` podem ser obtidos na página [git-scm.com](https://git-scm.com/), que também inclui documentação sobre o seu uso. Alternativamente, o Visual Studio Installer permite instalar facilmente esta aplicação em ambiente Windows.


## 2. Repositórios
### a) Criar uma cópia local de um repositório (clone)

Quando pretendemos criar uma cópia local de um repositório remoto, para explorarmos o código e a documentação no nosso próprio computador, para compilarmos e usarmos a aplicação ou para posteriormente colaborarmos com esse projeto, utilizamos o comando `git clone`:

```console
$ git clone https://github.com/victordomingos/EFAProg2019
Cloning into 'EFAProg2019'...
remote: Enumerating objects: 12, done.
remote: Counting objects: 100% (12/12), done.
remote: Compressing objects: 100% (7/7), done.
remote: Total 12 (delta 2), reused 3 (delta 1), pack-reused 0
Unpacking objects: 100% (12/12), done.
```

Este comando irá criar uma nova pasta na pasta de trabalho atual, contendo cópias de todos os ficheiros que se encontravam no repositório. Por isso, pode ser boa ideia usar antes o comando `cd` para mudar para a pasta onde vamos guardar os nossos vários repositórios `git`.


### b) Criar um novo repositório local

Se o que pretendemos é criar um novo repositório no nosso próprio computador, mesmo que posteriormente o pretendamos disponibilizar através do Github ou de outro servidor, primeiro precisamos de criar a pasta do projeto (caso ainda não exista). De seguida, usamos o comando `cd` para irmos para essa pasta. Finalmente, o seguinte comando irá inicializar um novo repositório local a partir da pasta do projeto:

```console
$ mkdir Brinquedo6
$ cd Brinquedo6/
$ git init
Initialized empty Git repository in C:/Users/victor/dev/Brinquedo6/.git/
```


### c) Criar um novo repositório local a partir de uma pasta existente

Se já temos uma pasta no nosso próprio computador que queremos transformar num repositório, também é possível. Primeiro inicializamos o repositório com `git init` e, seguidamente, adicionamos o seu conteúdo `git add .` (este comando adiciona todo o conteúdo da pasta atual). O comando `git commit`, que exemplificaremos mais abaixo, guardará esse estado inicial do repositório.



## 3. Alterar ficheiros num repositório

### a) Obter as alterações mais recentes a partir do repositório remoto

Para garantir que estamos a trabalhar com a versão mais recente do projeto, isto é, que o código no nosso repositório local está sincronizado com o repositório remoto, começamos por navegar até à pasta do repositório e usamos o comando `git fetch`.

```console
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

O comando `git status` permite-nos perceber se há alterações pendentes:

```console
$ git status
On branch master
Your branch is behind 'origin/master' by 1 commit, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working tree clean

```

Havendo alterações mais recentes no repositório remoto, o comando `git pull` atualiza o nosso repositório local com essas mesmas alterações.

```console
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



### b) Enviar para o repositório remoto as alterações locais

Depois de efetuar alterações no nosso repositório local, por exemplo, criando, apagando ou mudando o nome a ficheiros, ou editando alguns deles, podemos guardar o estado atual com uma operação designada `commit`. Mas primeiro precisamos de preparar esse `commit`, adicionando as pastas e/ou ficheiros a considerar:

```console
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

Uma vez mais, o comando `git status` permite-nos consultar as alterações pendentes ou, neste caso, em preparação:

```console
$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   README.md
```

Com `git commit` guardamos o estado atual do repositório (relativamente aos ficheiros/pastas que adicionamos com `git add`):

```console
$ git commit -m "Conteúdo adicional no ficheiro README.md"
[master ef23443] Conteúdo adicional no ficheiro README.md
 1 file changed, 131 insertions(+), 94 deletions(-)
 rewrite README.md (67%)
```

Neste momento, uma consulta rápida ao `git status` esclarece que apesar de não haver ficheiros ou pastas para registar num novo `commit`, o nosso repositório está adiantado em relação ao repositório remoto:

```console
$ git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
``` 

Para enviar as nossas alterações para o repositório remoto (neste caso o GitHub), basta usar o comando `git push`:

```console
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

Este guia, cuja elaboração se encontra em curso, é uma introdução muito sucinta a uma ferramenta complexa. Há claramente muitos aspetos por explicar e diversos procedimentos que seria interessante abordar. Assim, quaisquer sugestões de melhoramento deste documento serão muito bem-vindas. Erros, questões e ideias podem ser submetidos na página [Issues](https://github.com/victordomingos/EFAProg2019/issues).

Por outro lado, se tem já alguma conhecimento que gostaria de partilhar, sobre controlo de versões e colaboração com `git`, os seus [Pull requests](https://github.com/victordomingos/EFAProg2019/pulls) serão muito bem-vindos. Dicas introdutórias poderão ser acrescentadas a este mesmo ficheiro. Já explicações mais extensas ou mais aprofundadas deverão ser submetidas como ficheiros separados, por temas.
