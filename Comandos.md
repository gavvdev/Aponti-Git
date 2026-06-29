# Comandos Git
São ferramentas de linha de comando essenciais para o controle de versão distribuído, permitindo gerenciar alterações no código-fonte, colaborar com equipes e manter um histórico detalhado do projeto.

<p align="center">
  <img src="assets/principais-comandos-git.jpg" alt="comandos Git" width="100%">
</p>

> Nesta página, será explicado cada comando passo a passo para determinados contextos.

## Criando o Projeto
Você pode obter um projeto Git fazendo uso de um projeto ou diretório existente e o importando para o Git ou clonando um repositório Git existente a partir de outro servidor (Github).

---

## Inicializando Repositório em um Diretório Existente
Caso você esteja iniciando o monitoramento de um projeto existente com Git, você precisa ir para o diretório do projeto e digitar: 

```bash
git status
```
Isso cria um novo subdiretório chamado `.git` que contem todos os arquivos necessários de seu repositório, um esqueleto de repositório Git.

## Criando o arquivo .gitignore

O arquivo `.gitignore` é utilizado para informar ao Git quais arquivos e pastas **não devem ser monitorados ou enviados para o repositório**.

### 1. Criar o arquivo

```bash
touch .gitignore
```

**Finalidade:** Cria um arquivo vazio chamado `.gitignore` na pasta atual do projeto.

> **Observação:** O comando `touch` é utilizado em sistemas Linux e macOS. No Windows, você pode criar o arquivo manualmente pelo VS Code ou pelo Explorador de Arquivos.

---

### 2. Adicionar o arquivo ao Git

```bash
git add .gitignore
```

**Finalidade:** Adiciona o arquivo `.gitignore` à área de preparação (*Staging Area*), indicando que ele fará parte do próximo commit.

---

### 3. Salvar o arquivo no histórico do projeto

```bash
git commit -m "Adiciona arquivo .gitignore"
```

**Finalidade:** Cria um novo commit contendo o arquivo `.gitignore`.

> A opção `-m` permite informar uma mensagem descrevendo a alteração realizada.

Exemplo:

```bash
git commit -m "Adiciona arquivo .gitignore"
```

### Exemplo completo

```bash
touch .gitignore
git add .gitignore
git commit -m "Adiciona arquivo .gitignore"
```

> Após esses comandos, o arquivo `.gitignore` passa a fazer parte do histórico do projeto e o Git passa a ignorar os arquivos e pastas especificados nele.

Caso você queira começar a controlar o versionamento dos arquivos existentes, você provavelmente deve começar a monitorar esses arquivos e fazer um commit inicial. Você pode realizar isso com poucos comandos.

```bash
touch .gitignore
git add .gitignore
git commit -m "Mensagem"
```
> Agora, você possui um repositório Git com arquivos monitorados e um commit inicial.

# Clonando um Repositório
Você pode clonar um repositório com `git clone <URL>`. Por exemplo, caso você queira clonar o repositório do curso de Git e Github do Gustavo Guanabara, você pode executar da seguinte forma:
```bash
git clone https://github.com/gustavoguanabara/git-github.git
```
> Quando um repositório é inicialmente clonado, todos os seus arquivos estarão monitorados e inalterados porque você simplesmente os obteve e ainda não os editou.

# Registrando Alterações
Conforme você edita os arquivos do seu clone local de um repositório, o Git passa a vê-los como modificados, porque você os alterou desde seu ultimo commit. Você seleciona esses arquivos modificados e então faz o commit de todas as alterações selecionadas e ao longo do projeto esse ciclo passa a se repetir.

Para passar a monitorar um novo arquivo, use o comando `git add`. Para monitorar o arquivo README, você pode rodar isso:
```bash
git add README
```
Caso queira adicionar todas as modificações feitas no projeto use o comando:
```bash
git add .
```

Se você rodar o comando `git status`, você verá quer o seu arquivo `README` agora está sendo monitorado. Os arquivos monitorados faram parte do commit.

## Verificando o Status
A principal ferramenta utilizada para determinar quais arquivos estão em quais estados é o comando:
```bash
git status
```
> O comando mostra em qual branch você se encontra. Vamos dizer que você adicione um novo arquivo em seu projeto, um simples arquivo README. 

Caso o arquivo não existe e você execute `git status`, você verá o arquivo não monitorado dessa forma:

`#On branch master`

`#Untracked files:`

`# (use "gid add {files}..." to include in what will be commited)`

`#`

`#README`

`nothing added to commit but untracked files presente (use"git add" to track)`

Pode ver que o seu novo arquivo `README` não está sendo monitorado, pois está listado sob o cabeçalho "**Untracked files**" na saída do comando status. Não monitorado significa basicamente que o Git está vendo um arquivo que não existia na ultima captura (commit).

> O Git não vai inclui-lo nas suas capturas de commit até que você o diga explicitamente que assim o faça. Ele faz isso para que você não inclua acidentalmente arquivos binários gerados, ou outros arquivos que você não tem a intenção de incluir.

## Verificando Mudanças
Se o comando `git status` for muito vago, você quer saber exatamente o que você alterou, não apenas quais arquivos foram alterados. Você pode utilizar o comando:
```bash
git diff
```
Apesar do comando `git status` responder essas duas perguntas de maneira geral, o `git diff` mostra as linhas exatas que foram adicionadas e removidas, o patch, por assim dizer.

Se você quer ver o que selecionou que irá no seu próximo commit, pode utilizar:
```bash
git diff --cached`
```

# Commits
> Armazena o conteúdo atual do índice em um novo commit, juntamente com uma mensagem de registro do usuário que descreve as mudanças.

- Se usa o commit depois de já ter feito o `git add`, para fazer o commit:
```bash
git commit -m "Mensagem"
```
- Para commitar também os arquivos versionados mesmo não estando no Stage basta adicionar o parâmetro `-a`:
```bash
git commit -a -m "Mensagem"
```

- Refazer commit quando esquecer de adicionar um arquivo no Stage (Diretório de Trabalho, Repositório):
```bash
git commit -m "Mensagem" --amend
```
> O **amend** é destrutivo e só deve ser utilizado antes do commit ter sido enviado ao servidor remoto.

# Como Reverter Alterações
Em qualquer fase do projeto, você pode querer desfazer alguma coisa. Veremos algumas ferramentas básicas para desfazer modificações que você fez. 
**Cuidado**, porque você pode desfazer algumas dessas mudanças. Esta é uma das raras situações no Git onde um deslize pode causar a perda definitiva de código.

- Para apagar o último histórico e resetar tudo:
```bash
git reset --hard HEAD~1
```

- Para desfazer o último commit, mas manter as alterações salvas no Stage:
```bash
git reset --soft HEAD~1
```

- Para forçar o projeto a voltar ao estado de um commit específico (via Hash):
```bash
git reset --hard XXXXXXXXXXX
```

# Recuperando commit apagado pelo git reset
Para visualizar os hashs:
```bash
git reflog
```

e para aplicar:
```bash
git merge <hash>
```

# Removendo Arquivos
> Apagar arquivos no fluxo do Git exige um pouquinho de atenção. Para sumir com um arquivo do seu repositório, você precisa tirá-lo da área de seleção (_stage_) e commitar a mudança. O comando `git rm` facilita isso, deletando o arquivo do Git e do seu diretório local ao mesmo tempo.

- Força a exclusão do arquivo no Git e no seu computador:
```bash
git rm -f <arquivo>
```

- Desfaz o monitoramento do arquivo, ou seja, o Git deixa de segui-lo, mas o arquivo físico continua intacto na sua máquina.
```bash
git rm --cached + <arquivo>
```
- Comando terminal direto (fora do Git) para apagar uma pasta inteira instantaneamente.
```bash
`rm -rf <arquivo>`
```

> Nota de Segurança: Se você alterou um arquivo e já o adicionou ao _stage_, o Git vai bloquear a remoção comum para proteger seu trabalho. Para prosseguir mesmo assim, você deve forçar a barra usando o argumento `-f`. Como esses dados ainda não estão em um _snapshot_ (commit), eles não poderão ser recuperados depois.

# Movendo e renomeando arquivos

Diferentemente de muitos sistemas de controle de versão (VCS), o Git não monitora explicitamente arquivos movidos ou renomeados.

Apesar disso, o Git possui o comando `git mv`, que permite mover ou renomear arquivos de forma prática.

## Sintaxe

```bash
git mv arquivo_origem arquivo_destino
```

### Exemplo

```bash
git mv README.txt README.md
```

**Finalidade:** O comando `git mv` move ou renomeia um arquivo e prepara automaticamente essa alteração para o próximo commit.

Após executar o comando, você pode verificar a alteração utilizando:

```bash
git status
```

O Git identificará que o arquivo foi renomeado.

---

## Como o `git mv` funciona?

Internamente, o comando `git mv` equivale à execução dos seguintes comandos:

```bash
mv README.txt README.md
git rm README.txt
git add README.md
```

O Git identifica automaticamente que se trata de um renomeamento. Portanto, você pode renomear o arquivo manualmente utilizando o explorador de arquivos ou o terminal e, em seguida, executar os comandos `git rm` e `git add` antes de criar um commit.

A principal vantagem do `git mv` é a praticidade, pois ele executa essas etapas em um único comando.

## Fazendo Stash
Muitas vezes, quando você está trabalhando em uma parte do seu projeto, as coisas estão em um estado confuso e você quer mudar de branch por um tempo para trabalhar em outra coisa. O problema é, você não quer fazer o commit de um trabalho incompleto somente para voltar a ele mais tarde. A resposta para esse problema é o comando `git stash`.

Você quer mudar de branch, mas não quer fazer o commit do que você ainda está trabalhando; você irá fazer o stash das modificações. Para fazer um novo stash na sua pilha, execute:
```bash
git stash
```
> Seu diretório de trabalho estará limpo. Neste momento, você pode facilmente mudar de branch e trabalhar em outra coisa; suas alterações estão armazenadas na sua pilha.

- Para ver stashes que você guardou, você pode usar:
```bash
git stash list
```
Você pode aplicar aquele que acabou de fazer o stash com o comando mostrado na saída de ajuda do comando stash original:

```bash
git stash apply
```
> Se você quer aplicar um dos stashes mais antigos, você pode especifica-lo, assim:  `git stash apply stash@{2}`. 
Se você não especificar um stash, Git assume que é o stash mais recente e tenta aplicá-lo.

## Tag
O Git tem a habilidade de criar tags em pontos específicos na história do código como pontos importantes. Geralmente as pessoas usam esta funcionalidade para marcar pontos de release (v1.0, e por ai vai). Nesta seção, mostraremos como listar as tags disponíveis, como criar novas tags, e quais são os tipos diferentes de tags.

- Para listar as `tags` execute:
```bash
git tag
```
- Para criar uma`tag` basta executar o seguinte comando, caso não queira criar a `tag anotada`, somente retire os parâmetro `-a` e `-m`.
```bash
git tag -a v1.4 -m 'my version 1.4'`.
```
# Compartilhar e Atualizar Projetos

#### Fazendo o Fetch
- Para pegar dados dos seus projetos remotos, você pode executar:
```bash
git fetch origin
```
Esse comando vai até o projeto remoto e pega todos os dados que você ainda não tem. Depois de fazer isso, você deve ter referencias para todos os branches desse remoto, onde você pode fazer o merge ou inspecionar a qualquer momento.

## Atualizando local
Incorpora as alterações de um repositório remoto no branch atual. Em seu modo padrão, `git pull` é uma abreviação para `git fetch` seguindo de git merge `FETCH_HEAD`. Por exemplo, se eu estiver em uma branch chamada `develop` e quiser atualizar caso haja atualizações remotamente:
```bash
`git pull origin develop`
```
## Empurrando seus commits
```bash
git push
``` 
> é o comando em que você transfere commits a partir do seu repositório local para um repositório remoto. É a contrapartida do `git fetch`, que busca importações e comprometem as agencias locais, utilizando o `git push` as exportações comprometem as filiais remotas.

Para fazer isso, você executa o `git push <nome_do_repositorio><nome_da_sua_branch-_local>`, que vai tentar fazer que `<nome_do_repositorio_remoto>` receba a sua branch `<nome_da_sua_branch_local>` contendo todos seus commits com alterações. 

Por exemplo:
```bash
git push origin develop
```

# Repositórios Remotos
Para ver quais servidores remotos você configurou, execute o comando `git remote`. Ele lista os nomes abreviados de cada repositório remoto que você configurou. 

- Para ver as URLs que o Git armazenou para leitura e escrita, adiciona `-v`:
```bash
git remote -v
```
- Para adicionar um novo repositório remoto com um nome abreviado que você pode referências facilmente:
```bash
git remo add <apelido> <URL>
```
- Para remover uma referencia de repositório remoto:
```bash
git remote remove <nome>`
```
- Para ver informações destalhadas sobre um repositório remoto específico:
```bash
git remote show <nome>
```
# Submódulos
> Os submódulos permitem que você inclua um repositório Git como um subdiretório de outro repositório Git. Isso é útil quando você precisa incorporar bibliotecas externas ou projetos separados dentro do seu projeto principal.

- Para adicionar um submódulo ao seu projeto:
```bash
git submodule add <URL> <caminho>`
```
- Ao clonar um repositório que contém submódulos, você precisa inicializá-los e atualizá-los:
```bash
git submodule init
git submodule update
```
Ou você pode clonar recursivamente, o que faz tudo em um só passo:
```bash
git clone --recurse-submodule <URL>
```
- Para atualizar todos os submódulos para as ultimas versões remotas:
```bash
git submodule update --remote
```

# Exibindo Objetos
O comando `git show` exibe informações sobre objetos do Git (commits, tags, árvores, blobs). 

- Para ver os detalhes de um commit específico, incluindo o diff das alterações:
```bash
git show <hash_do_commit>
```
- Para ver o conteúdo de um arquivo em um commit específico:
```bash
git show <hash>:<caminho/do/arquivo>`
```
- Para exibir as informações de uma tag anotada:
```bash
git show v1.0
```
- Sem argumentos, exibe os detalhes do último commit:
```bash
git show`
```
# Log Avançado
Além do uso básico, o `o git log` oferece várias opções para personalizar a visualização do histórico. 

- Para ver um resumo compacto com uma linha por commit:
```bash
git log --oneline`
```
- Para exibir um gráfico das branches e merges:
```bash
git log --oneline --graph --all
```
- Para filtrar commits por autor:
```bash
git log --author=="Nome"
```
- Para filtrar por data:
```bash
git log --since="2024-01-01" --until="2024-12-31"
```
- Para ver quais arquivos foram alterados em cada commit:
```bash
git log --start
```
- Para buscar commits cuja mensagem contenha um texto específico:
```bash
git log --grep="texto"
```

# Diff Avançado
O `git diff` pode ser utilizado de várias formas avançadas. 

- Para comparar dois branches:
```bash
git diff <branc1h>..<branch2>
```
- Para comparar dois commits específicos:
```bash
git diff <hash1> <hash2>
```
- Para ver apenas os nomes dos arquivos alterados:
```bash
git diff --name-only
```
- Para ver um resumo estatístico das alterações:
```bash
git diff --start
```
- Para comparar o stage (área de seleção) com o último commit:
```bash
git diff --staged
```

# Solicitando Pull
Antes de existirem as interfaces visuais de plataformas como GitHub ou GitLab, os desenvolvedores já solicitavam a inclusão de seus códigos usando o próprio terminal. 
O `git request-pull` serve justamente para isso: ele gera uma mensagem pronta que avisa ao dono de um projeto que você tem melhorias para enviar.
```bash
git request-pull <commit_inicial> <url_do_repositorio> <branch>`
```
> Se você quiser gerar um relatório comparando o que mudou desde a versão `v1.0` na sua branch `master`, por exemplo, o comando seria:

Exemplo prático:
```bash
git request-pull v1.0 https://github.com/user/repo master
```

O resultado inclui a lista de commits, os arquivos alterados e a URL de onde o mantenedor pode fazer o pull.

# Importação Rápida
Se você precisa trazer o histórico de um projeto antigo (como SVN ou Mercurial) para o Git, usar os comandos tradicionais pode ser muito lento. É aí que entra o `git fast-import`, uma ferramenta de baixo nível feita sob medida para processar e criar objetos do Git.

Ele lê um fluxo de dados formatado e cria objetos Git rapidamente:
```bash
git fast-import < dados_exportados.txt
```
> O formato de entrada é específico e geralmente gerado por scripts de migração. Cada entrada define commits, blobs (arquivos) e referências no formato que o Git espera.

- Após a importação, verifique o resultado com:
```bash
git log --oneline --all
```

# Limpando o Diretório
Com o tempo, o diretório do seu projeto pode acumular arquivos temporários ou testes que não foram adicionados ao Git. Para limpar essa bagunça de uma só vez, usamos o `git clean`. Como esse comando apaga arquivos permanentemente do disco, ele possui algumas travas de segurança importantes.

> Antes de apagar qualquer coisa, rode um "simulado" com `git clean -n`. O Git vai te mostrar exatamente o que será jogado fora.

Veja como usá-lo com segurança:

- Para ver quais arquivos seriam removidos sem realmente removê-los:
```bash
git clean -n
```
- Para remover os arquivos não monitorados (requer o parâmetro **-f** por segurança):
```bash
git clean -f
```
- Indo um passo além e apagando também as pastas inteiras que não foram adicionadas ao Git, digite:
```bash
git clean -fd
```

A limpeza mais profunda. Além de arquivos e pastas comuns, ele deleta inclusive aquilo que você mandou o Git ignorar no arquivo `.gitignore` (ótimo para quando você quer resetar o ambiente do zero).
`git clean -fdx`
