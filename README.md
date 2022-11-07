# GIT

## Introdução

### SCM (Source Code Management)

`Sistemas para gerenciamento de código fonte` são utilizados para evitar a perda de trabalho em arquivos, seja por falha em disco, edição indevida ou exclusão acidental.

Existem diversos sistemas que são utilizados para este fim, e basicamente temos eles funcionando em dois modelos:

- **Centralizados**: São sistemas que só trabalham conectados a um servidor e não possibilitam que dois usuários alterem o mesmo arquivo. Ex.: SVN, TFS
![SCM Centralizado](images/centralized.png)

- **Distribuídos**: Possibilitam o trabalho offline e com vários usuários editando o mesmo arquivo. Ex.: GIT
![SCM Distribuído](images/distributed.png)

### GIT

O GIT é o SCM distribuído mais utilizado no mundo. Ele foi criado inicialmente pelos desenvolvedores do kernel Linux, principalmente por `Linus Torvalds`.

Para o versionamento do código do kernel eles utilizavam uma ferramenta proprietária chamada **BitKeeper** que por alegações de violação de licença teve o acesso gratuito removido.

Então Linus resolveu desenvolver uma ferramenta que fosse similar, porém mais rápida, confiável e com alto desempenho, visto que o BitKeeper tinha muitos problemas de performance.

## Hands-on

### Criar repositório
Um repositório de arquivos pode ser criado em qualquer pasta do sistema operacional com o comando abaixo:

```sh
git init
```

Com isso a pasta atual se torna um repositório do GIT e já está apta a receber os comandos de versionamento.

### Comandos operacionais

Em um repositório GIT temos algumas areas para trabalhar:

- **Working Directory**: Onde estão os arquivos brutos onde serão realizadas as alterações.

- **Staging Area**: Onde ficam as alterações que foram marcadas para serem persistidas no commit.

- **Repository (.git)**: É onde estão os commits realizados.

![Areas](images/areas.png)

#### **git add**

Insere as alterações dos arquivos na Staging Área. Geralmente é utilizado com parametro "`.` " indicando assim que todas as alterações devem ser enviadas para staging.
Também pode ser especificado qual arquivo deve ser enviado.

```sh
# Adiciona todas as alterações
git add .

# Adiciona somente as alterações do arquivo.txt
git add arquivo.txt

# Possibilita adicionar linhas específicas
git add -p
```

#### **git commit**

Persiste todas as alterações adicionadas a Staging Area, informando uma mensagem para essa alteração e é criado um HASH desse commit para garantir que seja imutável e único no repositório.

```sh
git commit -m "Criação de um arquivo de teste"
```

#### **git branch**

Os commits de um repositório GIT podem ser visualizados em uma estrutura de árvore, assim podemos derivar trechos de código a partir de um commit específico, gerando assim uma ramificação do código.

As branches (ramos) são uma nova linha do tempo do código fonte e temos diversas estratégias para gerenciá-las.

![Branches](images/flow.png)

Podemos criar uma branch à partir de praticamente qualquer ponto da árvore de commits.

```sh
# Criar uma branch chamada release a partir da branch main
git branch -c main release

# Deletar a branch release
git branch -D release

# Cria uma branch a partir de um commit específico
git branch -f release <codigo-do-commit>
```

#### **git checkout**
Checkout pode ser utilizado para trocar branches, remover arquivos do Staging Área e até criar branches.

```sh
# Troca para a branch main
git checkout main

# Remove o arquivo.txt do Staging Área (já foi adicionado antes pelo git add)
git checkout -- arquivo.txt

# Cria uma branch chamada release a partir da branch atual
git checkout -b release
```

#### **git merge**

### Resolvendo conflitos

### Desfazendo alterações

```sh
git reset
git revert
```

### Trabalhando com Servidor

```sh
git remote
git push
git fetch 
git pull
```