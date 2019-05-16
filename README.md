# EFAProg2019
## Repositório `git` da turma EFA NS - Programador de Informática (2019-2010). 

O objetivo principal deste repositório privado é ajudar os formandos desta turma a familiarizarem-se com o GitHub, com o conceito de controlo de versões e com a utilização básica do comando `git`. Adicionalmente, todos os membros da turma estão convidados a dar o seu contributo para os conteúdos deste repositório, adicionando mais dicas ou propondo alterações a algum dos guias ou programas existentes.

## 1. ANTES DE COMEÇAR: Instalar o comando `git`

O comando `git` é um programa de linha de comandos que pode ser instalado nos vários sistemas operativos e que permite interagir com repositórios git. Existem IDEs e outras aplicações que oferecem interfaces de ambiente gráfico (GUI), mas neste momento basta usar a linha de comandos, que muitas vezes é até mais prática.


## 2. Repositórios
### a) Criar uma cópia local de um repositório (clone)

Quando pretendemos criar uma cópia local de um repositório remoto, para explorarmos o código e a documentação no nosso próprio computador, para compilarmos e usarmos a aplicação ou para posteriormente colaborarmos com esse projeto, utilizamos o comando `git clone`:

```
git clone https://github.com/victordomingos/EFAProg2019
```

Este comando irá criar uma nova pasta na pasta de trabalho atual, contendo cópias de todos os ficheiros que se encontravam no repositório. Por isso, pode ser boa ideia usar antes o comando `cd` para mudar para a pasta onde vamos guardar os nossos vários repositórios `git`.


### b) Criar um novo repositório local

Se o que pretendemos é criar um novo repositório no nosso próprio computador, mesmo que posteriormente o pretendamos disponibilizar através do Github ou de outro servidor, primeiro precisamos de criar a pasta do projeto (caso ainda não exista). De seguida, usamos o comando `cd` para irmos para essa pasta. Finalmente, o seguinte comando irá inicializar um novo repositório local a partir da pasta do projeto:

```
git init
```

## 3. Alterar ficheiros num repositório
### a) Obter as alterações mais recentes a partir do repositório remoto

Para garantir que estamos a trabalhar com a versão mais recente do projeto, isto é, que o código no nosso repositório local está sincronizado com o repositório remoto, navegamos até à pasta do repositório e usamos este comando:

```
git fetch
```



##


## Como contribuir

O primeiro passo para poder usufruir dos conteúdos deste repositório e colaborar na sua criação ou manutenção consiste em criar uma cópia (`clone`) do mesmo. Mas, antes, convém instalar o `git`.

