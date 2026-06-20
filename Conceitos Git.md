# Conceito Git
É um sistema de versionamento, organiza os arquivos de um projeto e salva o histórico de alterações de tudo. O git pode tanto ser operado com interface grafica em IDE's quanto via [[Terminal]] 
# Arquivos Especiais de Configuração
1. [[.gitignore]]
É um arquivo de texto onde você lista explicitamente todos os arquivos, formatos ou pastas que o Git **deve ignorar**. Tudo o que estiver documentando aqui não será rastreado pelo Git e não irá para o repositório
	**Para que serve:** Evitar o envio de arquivos gerados automaticamente (como as pastas e arquivo`.env, node_modules, dist` e `build`) e arquivos do própio sistema operacional (como`.DS_Store` no Mac)
2. [[.env]]
É o arquivo utilizado para armazenar as **variáveis de ambiente** do seu projeto.
	**Para que serve:** Ele guarda dados sensíveis e configurações específicas da sua máquina local, como senhas de bancos de dados, chaves de APIs privadas e portas de servidores.
		**Atenção**: O arquivo `.env` **NUNCA deve ser enviado para o Git**. Por conter dados secretos, o nome `.env` deve ser obrigatoriamente adicionado dentro do seu arquivo `.gitignore`.

# Instalação e Configuração
Instalar o Git na sua máquina é muito simples. Basta acessar o site: https://git-scm.com/install/windows e realizar o download de acordo com seu SO.

Após concluir a instalação, você terá tanto uma versão command line (linha de comando, incluindo um cliente SSH que será útil depois) e uma GUI padrão.

A primeira coisa que você deve fazer quando instalar o Git é definir o seu nome de usuário e endereço de e-mail. Isso é importante porque todos os commits no Git utilizam essas informações, e está imutavelmente anexado nos commits que você realiza.

`git config --global user.name "Fulano De Tal"`
`git config --global user.email "fulanodetal@exemplo.com"`

Lembrando, você precisa fazer isso uma vez caso passe a opção `--global,` pois o Git sempre usará essa informação para qualquer coisa que você faça nesse sistema. Caso você queira sobrepor estas com um nome ou endereço de e-mail diferentes para projetos especifico, você pode executar a opção `--global` quando estiver no próprio projeto.

Se você precisar de ajuda ao usar o Git, existem três maneiras de obter a ajuda para qualquer um dos comandos Git.

- `git help <comando>`
- `git <comando> --help`
- `man git <comando>`
	Extra: O comando principal para listar a lista de comandos disponíveis no Git é: `git help -a`

# Verificação
Depois de instalar e configurar o Git, É importante garantir que o terminal do seu sistema operacional consegue reconhece-lo. Para isso, basta abrir o seu [[Terminal]](Prompt de Comando, Powershell ou Git Bash) e digitar um dos comandos abaixo:

`git --version`

Se tudo estiver correto, o terminal retornará o texto indicando a Versão do Git instalada na sua máquina, algo parecido com:

`git version 2.54.0.windows.1`

Se o terminal retornar uma mensagem de erro como "*commando not found*" ou "*Não é reconhecido como um comando interno*", significa que o Git não foi instalado corretamente ou que o caminho dele não foi adicionado as variáveis de ambiente do seu sistema.
# Comandos Git
São ferramentas de linha de comando essenciais para o controle de versão distribuído, permitindo gerenciar alterações no código-fonte, colaborar com equipes e manter um histórico detalhado do projeto.

Nesta página, será explicado cada comando passo a passo para determinados contextos.

# Criando o Projeto
Você pode obter um projeto Git fazendo uso de um projeto ou diretório existente e o importando para o Git ou clonando um repositório Git existente a partir de outro servidor ([[Trabalho Aponti/Github|Github]]).

#### Inicializando Repositório em um Diretório Existente
Caso você esteja iniciando o monitoramento de um projeto existente com Git, você precisa ir para o diretório do projeto e digitar

`git init`
	Isso cria um novo subdiretório chamado `.git` que contem todos os arquivos necessários de seu repositório, um esqueleto de repositório Git.

Caso você queira começar a controlar o versionamento dos arquivos existentes, você provavelmente deve começar a monitorar esses arquivos e fazer um commit inicial. você pode realizar isso com poucos comandos.

`touch .gitignore`
`git add .gitignore`
`git commit -m "Mensagem"`

Agora, você possui um repositório Git com arquivos monitorados e um commit inicial.

#### Clonando um Repositório
Você pode clonar um repositório com `git clone <URL>`. Por exemplo, caso você queira clonar o repositório do curso de Git e Github do Gustavo Guanabara, você pode executar da seguinte forma:

`git clone https://github.com/gustavoguanabara/git-github.git`
	Quando um repositório é inicialmente clonado, todos os seus arquivos estarão monitorados e inalterados porque você simplesmente os obteve e ainda não os editou.

#### Registrando Alterações
Conforme você edita os arquivos do seu clone local de um repositório, o Git passa a vê-los como modificados, porque você os alterou desde seu ultimo commit. Voce seleciona esses arquivos modificados e então faz o commit de todas as alterações selecionadas e ao longo do projeto esse ciclo passa a se repetir.

Para passar a monitorar um novo arquivo, use o comando `git add`. Para monitorar o arquivo README, você pode rodar isso:

`git add README` 
	Caso queira adicionar todas as modificações feitas no projeto use o comando:
	`git add .`

Se você rodar o comando `git status`, você verá quer o seu arquivo `README` agora está sendo monitorado. Os arquivos monitorados faram parte do commit.

#### Verificando o Status
A principal ferramenta utilizada para determinar quais arquivos estão em quais estados é o comando:

`git status`
	O comando mostra em qual branch você se encontra. Vamos dizer que você adicione um novo arquivo em seu projeto, um simples arquivo README. 

Caso o arquivo não existe e você execute `git status`, você verá o arquivo não monitorado dessa forma:

``#On branch master
`#Untracked files:`
`# (use "gid add {files}..." to include in what will be commited)`
`#`
`#README`
`nothing added to commit but untracked files presente (use"git add" to track)`

Pode ver que o seu novo arquivo `README` não está sendo monitorado, pois está listado sob o cabeçalho "**Untracked files**" na saída do comando status. Não monitorado significa basicamente que o Git está vendo um arquivo que não existia na ultima captura (commit).

O Git não vai inclui-lo nas suas capturas de commit até que você o diga explicitamente que assim o faça. Ele faz isso para que você não inclua acidentalmente arquivos binários gerados, ou outros arquivos que você não tem a intenção de incluir.

#### Verificando Mudanças
Se o comando `git status` for muito vago, você quer saber exatamente o que você alterou, não apenas quais arquivos foram alterados. Você pode utilizar o comando:

`git diff`
	Apesar do comando `git status` responder essas duas perguntas de maneira geral, o `git diff` mostra as linhas exatas que foram adicionadas e removidas, o patch, por assim dizer.

Se você quer ver o que selecionou que irá no seu próximo commit, pode utilizar:
`git diff --cached`

#### Commits
Armazena o conteúdo atual do índice em um novo commit, juntamente com uma mensagem de registro do usuário que descreve as mudanças.

Se usa o commit depois de já ter feito o `git add`, para fazer o commit:
`git commit -m "Mensagem"`

Para commitar também os arquivos versionados mesmo não estando no Stage basta adicionar o parâmetro `-a`:
`git commit -a -m "Mensagem"`

Refazer commit quando esquecer de adicionar um arquivo no Stage (Diretório de Trabalho, Repositório):
`git commit -m "Mensagem" --amend`

O **amend** é destrutivo e só deve ser utilizado antes do commit ter sido enviado ao servidor remoto.

#### Como Reverter Alterações
Em qualquer fase do projeto, você pode querer desfazer alguma coisa. Veremos algumas ferramentas básicas para desfazer modificações que você fez. **Cuidado**, porque você pode desfazer algumas dessas mudanças. Esta é uma das raras situações no Git onde um deslize pode causar a perda definitiva de código.

Para apagar o último histórico e resetar tudo:
`git reset --hard HEAD~1`

Para desfazer o último commit, mas manter as alterações salvas no Stage:
`git reset --soft HEAD~1`

Para forçar o projeto a voltar ao estado de um commit específico (via Hash):
`git reset --hard XXXXXXXXXXX`

#### Recuperando commit apagado pelo git reset
Para visualizar os hashs:
`git reflog`

e para aplicar:
`git merge <hash>`

#### Removendo Arquivos
Apagar arquivos no fluxo do Git exige um pouquinho de atenção. Para sumir com um arquivo do seu repositório, você precisa tirá-lo da área de seleção (_stage_) e commitar a mudança. O comando `git rm` facilita isso, deletando o arquivo do Git e do seu diretório local ao mesmo tempo.

Força a exclusão do arquivo no Git e no seu computador:
`git rm -f <arquivo>
	Desfaz o monitoramento do arquivo, ou seja, o Git deixa de segui-lo, mas o arquivo físico continua intacto na sua máquina.
	`git rm --cached + <arquivo>`
		Comando terminal direto (fora do Git) para apagar uma pasta inteira instantaneamente.
		`rm -rf <arquivo>`

**Nota de Segurança:** Se você alterou um arquivo e já o adicionou ao _stage_, o Git vai bloquear a remoção comum para proteger seu trabalho. Para prosseguir mesmo assim, você deve forçar a barra usando o argumento `-f`. Como esses dados ainda não estão em um _snapshot_ (commit), eles não poderão ser recuperados depois.
#### Movendo Arquivos
Diferente de muitos sistemas VCS, o Git não monitora explicitamente arquivos movidos.
É um pouco confuso que o Git tenha um comando `mv`. 

Se você quiser renomear um arquivo no Git, voce pode fazer isso com:
`git mv arquivo_origem arquivo_destino`
	E funciona. De fato, se você fizer algo desse tipo e consultar o status, você verá que o Git considera que o arquivo foi renomeado.

No entanto, isso é equivalente a rodar algo como:

`mv README.txt README`
`git rm README.txt`
`git add README`

O Git descobre que o arquivo foi renomeado implicitamente, então ele não se importa se você renomeou por este caminho ou com o comando `mv`. A única diferença real é que o comando `mv` é mais conveniente, executa três passos de uma vez. O mais importante, você pode usar qualquer ferramenta para renomear um arquivo, e usar add/rm depois, antes de consolidar com o commit.

#### Fazendo Stash
Muitas vezes, quando você está trabalhando em uma parte do seu projeto, as  coisas estão em um estado confuso e você quer mudar de branch por um tempo para trabalhar em outra coisa. O problema é, você não quer fazer o commit de um trabalho incompleto somente para voltar a ele mais tarde. A resposta para esse problema é o comando `git stash`.

Você quer mudar de branch, mas não quer fazer o commit do que você ainda está trabalhando; você irá fazer o stash das modificações. Para fazer um novo stash na sua pilha, execute:

`git stash`
	Seu diretório de trabalho estará limpo.
	Neste momento, voce pode facilmente mudar de branch e trabalhar em outra coisa; suas alterações estão armazenadas na sua pilha.

Para ver stashes que você guardou, você pode usar:
`git stash list`
	Você pode aplicar aquele que acabou de fazer o stash com o comando mostrado na saída de ajuda do comando stash original : `git stash apply`. Se voce quer aplicar um dos stashes mais antigos, você pode especifica-lo, assim:  `git stash apply stash@{2}`. Se você não especificar um stash, Git assume que é o stash mais recente e tenta aplicá-lo.

#### Tag
Gite tem a habilidade de criar tags em pontos específicos na história do código como pontos importantes. Geralmente as pessoas usam esta funcionalidade para marcar pontos de release (v1.0, e por ai vai). Nesta seção, mostraremos como listar as tags disponíveis, como criar novas tags, e quais são os tipos diferentes de tags.

Para listar as `tags` execute:
`git tag`
	Para criar uma`tag` basta executar o seguinte comando, caso não queira criar a `tag anotada`, somente retire os parâmetro `-a` e `-m`.
	`git tag -a v1.4 -m 'my version 1.4'`.

# Compartilhar e Atualizar Projetos
#### Fazendo o Fetch
Para pegar dados dos seus projetos remotos, você pode executar:
`git fetch origin`
	Esse comando vai até o projeto remoto e pega todos os dados que você ainda não tem. Depois de fazer isso, você deve ter referencias para todos os branches desse remoto, onde você pode fazer o merge ou inspecionar a qualquer momento.
#### Atualizando local
Incorpora as alterações de um repositório remoto no branch atual. Em seu modo padrão, `git pull` é uma abreviação para `git fetch` seguindo de git merge `FETCH_HEAD`. Por exemplo, se eu estiver em uma branch chamada `develop` e quiser atualizar caso haja atualizações remotamente:

`git pull origin develop`

#### Empurrando seus commits
`git push` é o comando em que você transfere commits a partir do seu repositório local para um repositório remoto. É a contrapartida do `git fetch`, que busca importações e comprometem as agencias locais, utilizando o `git push` as exportações comprometem as filiais remotas.

Para fazer isso, voce executa o `git push <nome_do_repositorio><nome_da_sua_branch-_local>`, que vai tentar fazer que `<nome_do_repositorio_remoto>` receba a sua branch `<nome_da_sua_branch_local>` contendo todos seus commits com alterações. 

Por exemplo:
`git push origin develop`

#### Repositórios Remotos
Para ver quais servidores remotos você configurou, execute o comando `git remote`. Ele lista os nomes abreviados de cada repositório remoto que você configurou. 

Para ver as URLs que o Git armazenou para leitura e escrita, adiciona `-v`:
`git remote -v`

Para adicionar um novo repositório remoto com um nome abreviado que voce pode referencias facilmente:
`git remo add <apelido> <URL>`

Para remover uma referencia de repositório remoto:
`git remote remove <nome>`

Para ver informações destalhadas sobre um repositório remoto específico:
`git remote show <nome>`

#### Submódulos
Os submódulos permitem que você inclua um repositório Git como um subdiretório de outro repositório Git. Isso é útil quando você precisa incorporar bibliotecas externas ou projetos separados dentro do seu projeto principal.

Para adicionar um submódulo ao seu projeto:
`git submodule add <URL> <caminho>`

Ao clonar um repositório que contém submódulos, voce precisa inicializá-los e atualizá-los:
`git submodule init`
`git submodule update`

Ou você pode clonar recursivamente, o que faz tudo em um só passo:
`git clone --recurse-submodule <URL>`

Para atualizar todos os submódulos para as ultimas versões remotas:
`git submodule update --remote`

# Exibindo Objetos
O comando `git show` exibe informações osbre objetos do Git (commits, tags, árvores, blobs). 

Para ver os detalhes de um commit específico, incluindo o diff das alterações:
`git show <hash_do_commit>`

Para ver o conteúdo de um arquivo em um commit específico:
`git show <hash>:<caminho/do/arquivo>`

Para exibir as informações de uma tag anotada:
`git show v1.0`

Sem argumentos, exibe os detalhes do último commit:
`git show`

# Log Avançado
Além do uso básico, o `o git log` oferece várias opções para personalizar a visualização do histórico. 

Para ver um resumo compacto com uma linha por commit:
`git log --oneline`

Para exibir um gráfico das branches e merges:
`git log --oneline --graph --all`

Para filtrar commits por autor:
`git log --author=="Nome"`

Para filtrar por data:
`git log --since="2024-01-01" --until="2024-12-31"`

Para ver quais arquivos foram alterados em cada commit:
`git log --start`

Para buscar commits cuja mensagem contenha um texto específico:
`git log --grep="texto"`

# Diff Avançado
O `git diff` pode ser utilizado de várias formas avançadas. 

Para comparar dois branches:
`git diff <branc1h>..<branch2>`

Para comparar dois commits específicos:
`git diff <hash1> <hash2>`

Para ver apenas os nomes dos arquivos alterados:
`git diff --name-only`

Para ver um resumo estatístico das alterações:
`git diff --start`

Para comparar o stage (área de seleção) com o último commit:
`git diff --staged`

# Solicitando Pull
Antes de existirem as interfaces visuais de plataformas como GitHub ou GitLab, os desenvolvedores já solicitavam a inclusão de seus códigos usando o próprio terminal. O `git request-pull` serve justamente para isso: ele gera uma mensagem pronta que avisa ao dono de um projeto que você tem melhorias para enviar.

`git request-pull <commit_inicial> <url_do_repositorio> <branch>`

Se você quiser gerar um relatório comparando o que mudou desde a versão `v1.0` na sua branch `master`, por exemplo, o comando seria:
Exemplo prático:
`git request-pull v1.0 https://github.com/user/repo master`

O resultado inclui a lista de commits, os arquivos alterados e a URL de onde o mantenedor pode fazer o pull.

# Importação Rápida
Se você precisa trazer o histórico de um projeto antigo (como SVN ou Mercurial) para o Git, usar os comandos tradicionais pode ser muito lento. É aí que entra o `git fast-import`, uma ferramenta de baixo nível feita sob medida para processar e criar objetos do Git.

Ele lê um fluxo de dados formatado e cria objetos Git rapidamente:
`git fast-import < dados_exportados.txt`

O formato de entrada é específico e geralmente gerado por scripts de migração. Cada entrada define commits, blobs (arquivos) e referências no formato que o Git espera.

Após a importação, verifique o resultado com:
`git log --oneline --all`

# Limpando o Diretório
Com o tempo, o diretório do seu projeto pode acumular arquivos temporários ou testes que não foram adicionados ao Git. Para limpar essa bagunça de uma só vez, usamos o `git clean`. Como esse comando apaga arquivos permanentemente do disco, ele possui algumas travas de segurança importantes.

Antes de apagar qualquer coisa, rode um "simulado" com `git clean -n`. O Git vai te mostrar exatamente o que será jogado fora.

Veja como usá-lo com segurança:

Para ver quais arquivos seriam removidos sem realmente removê-los:
`git clean -n`

Para remover os arquivos não monitorados (requer o parâmetro **-f** por segurança):
`git clean -f`

Vai um passo além e apaga também as pastas inteiras que não foram adicionadas ao Git:
`git clean -fd`

A limpeza mais profunda. Além de arquivos e pastas comuns, ele deleta inclusive aquilo que você mandou o Git ignorar no arquivo `.gitignore` (ótimo para quando você quer resetar o ambiente do zero).
`git clean -fdx`



