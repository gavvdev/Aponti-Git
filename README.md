# Guia de comandos Git

# Foco no ambiente de terminal
Interface de Linha de Comando (CLI) que permite que você interaja diretamente com o sistema operacional do seu computador através de comandos.
## Atalhos
⚠️**Atenção (caminhos com espaços)** - Envolva caminhos que contenham espaços entre aspas
Ex: `cd "C:\Program Files\Meu App"`

**Seta para cima e para baixo no terminal** - revisita o histórico de comandos digitados anteriormente no terminal, possibilitando uma execução mais rápida de comandos.

**Tab para auto-complete** - Pode-se usar o atalho Tab para completar automaticamente o nome de alguma pasta ou algum comando

**Ctrl+L**  - Limpa o terminal

## Comandos (CMD)
- `dir` - Listar tudo que está no seu diretório (pasta) atual, dependendo do terminal ele pode mostrar o tipo de arquivo com alguma cor diferente. O parâmetro `/ah` exibe arquivos e diretórios ocultos
	- Ex: `dir`
- `cls` - Limpa o terminal
	- Ex: `cls`
- `cd` - Mudar de um diretório para outro.
	- Ex: `cd diretorio`
	Pode ser usado com `..` para voltar um diretório anterior
	- Ex: `cd ..`
- `del` - Deleta um arquivo
	- Ex: `del arquivo.txt`
- `rmdir` - Deleta um diretório.
	- Ex: `rmdir diretorio`
- `mkdir` - Cria um novo diretório.
	- Ex: `mkdir novadir`
- `move` - Move arquivos/diretórios
	 - Ex: `move arquivo.txt C:\NovaPasta\`
## Comandos (Bash)
- `ls` Listar tudo que está no seu diretório atual, dependendo do terminal ele pode mostrar diferentes tipos de arquivos com cores diferentes. O parâmetro `-a` exibe arquivos e diretórios ocultos
	- Ex: `ls`
-  `clear` Limpa o terminal
	-  Ex: `clear`
- `cd` - Mudar de um diretório para outro. Pode ser usado com `..` para voltar um diretório anterior
	Ex: `cd diretorio`
- `rm` - Deleta um arquivo.
	Ex: `rm arquivo.txt`
- `rmdir` - Deleta um diretório.
	Ex: `rmdir diretorio`
- `mkdir` - Cria um novo diretório.
	Ex: `mkdir novadir`
- `mv` - Move arquivos/diretórios ou renomear arquivos/diretórios. Use o parâmetro `-i` para que o terminal pergunte antes de sobrescrever algo com o mesmo nome. 
	- Ex (movendo arquivo): `mv -i arquivo.txt /home/usuario/Documentos/`
	- Ex (renomeando arquivo): `mv -i foto_antiga.jpg foto_nova.jpg`
- `nano` - Abre o editor de texto do terminal linux, pode ser usado para ver e editar o conteúdo de um arquivo. (Se não houver arquivo com o nome, um novo arquivo pode ser salvo com esse nome após fechar o editor)
	Ex: `nano lista.txt`
- `touch` - Cria um arquivo vazio.
	- Ex: `touch novo_arquivo.txt`
- `cp` - Copia arquivos e diretórios.
	- Ex: `cp arquivo.txt copia.txt`
	
# O que é Controle de Versão?
O controle de versão, também conhecido como versionamento, é uma prática importante no desenvolvimento de software para rastrear e gerenciar as mudanças feitas no código e em outros arquivos. 

Ele registra todas as alterações feitas no código-fonte, permitindo consultar o histórico, comparar mudanças e restaurar versões anteriores quando necessário. Funciona como uma **“fonte única de verdade”** e uma rede de segurança, possibilitando que equipes experimentem e desenvolvam sem risco de perdas irreversíveis.

Quando há alterações simultâneas ou conflitos, o sistema ajuda a identificar problemas, rastrear quem fez cada modificação e reverter rapidamente o código para um estado estável. Também facilita revisões de código e a análise da evolução do projeto ao longo do tempo.

O versionamento funciona como uma rede de segurança para proteger o código-fonte de danos irreparáveis, proporcionando a equipe de desenvolvimento a liberdade de experimentar sem medo de causar danos ou criar conflitos de código.

### Como funciona um controle de versão?
Basicamente, os arquivos do projeto ficam armazenados em um repositório (local ou remoto) e o histórico de suas versões é salvo nele. Os desenvolvedores podem acessar e resgatar a versão mais recente e fazer uma cópia local, na qual poderão trabalhar em cima dela e continuar o processo de desenvolvimento.

 A cada alteração feita, é possível enviar novamente ao repositório, atualizando a versão a partir de outras feitas pelos demais colaboradores.

Dependendo das necessidades específicas de uma equipe e do processo de desenvolvimento, um VCS (sistema de controle de versão) pode ser **local**, **centralizado** ou **distribuído**. O VCS local armazena os arquivos em um sistema local, o VCS centralizado armazena as alterações em um servidor único e o VCS distribuído permite que cada desenvolvedor tenha uma cópia completa do repositório, como no **Git**.

### Por que usar o controle de versão? Como simplifica a colaboração?
À medida que as empresas aceleram a entrega de software com DevOps, fica cada vez mais díficil controlar e gerenciar as diferentes versões dos artefatos da aplicação, desde o código e a configuração até o design e a implantação.

O controle de versão coordena todas as mudanças em um projeto de software, rastreando efetivamente as alterações nos arquivos-fonte, designs e outros ativos digitais necessários para um projeto, além dos metadados relacionados. Sem ele, os projetos podem facilmente se tornar uma confusão de diferentes versões dos arquivos, prejudicando a capacidade da equipe de desenvolvimento de software de entregar resultados.

Com um VCS robusto, as equipes de software podem reunir rapidamente todos os arquivos críticos do projeto e promover uma comunicação eficaz para melhorar a qualidade de código. E, como ele oferece uma fonte única de verdade, os stakeholders de toda a equipe DevOps podem colaborar para criar soluções inovadoras: desde os responsáveis pelo planejamento até os profissionais responsáveis pela implementação e manutenção do sistema.
# O que é Git

# Comandos Git 

Os comandos Git são utilizados para controlar as versões de projetos, registrar alterações e facilitar o trabalho em equipe. A seguir estão os principais comandos utilizados no dia a dia de um desenvolvedor. 
`git config` - Configura informações do usuário que serão associadas aos commits.
```bash
git config --global user.name "Seu Nome"
git config --global user.email "seuemail@email.com"
git config --local user.name "Seu Nome"
git config --local user.email "seuemail@email.com"
```
`git init` - Inicializa um novo repositório Git na pasta atual. 
```bash
git init
```
`git clone` - Cria uma cópia local de um repositório remoto. 

```bash
git clone https://github.com/usuario/repositorio.git
```
`git status` - Exibe o estado atual do repositório, mostrando arquivos modificados, adicionados e não rastreados. 
```bash
git status
```
`git add` - Adiciona arquivos para a área de preparação (staging area).
```bash
git add arquivo.txt (Adicionar um arquivo)
git add . (Adicionar todos os arquivos alterados)
```
`git commit` - Registra as alterações adicionadas ao histórico do projeto. 
```bash
git commit -m "Adiciona tela de login"
```
`git log` - Mostra o histórico de commits do repositório. 
```bash
git log
git log --oneline (Versão resumida)
```
`git diff` - Mostra as diferenças entre versões de arquivos. 

```bash
git diff
```
`git branch` - Lista, cria ou remove branches.
```bash
git branch (Listar branches)
git branch nova-feature (Criar uma branch)
git branch -d nova-feature (Deleta uma branch)
```
`git checkout` - Permite trocar de branch. 
```bash
git checkout nova-feature
git checkout -b nova-feature (Cria e muda para a branch criada)
```
`git switch` - Alternativa moderna para trocar de branch. 
```bash
git switch nova-feature
```
`git merge` - Mescla alterações de uma branch com outra. 
```bash
git merge nova-feature
```
`git remote add origin` - Conecta o repositório local a um repositório remoto. 
```bash
git remote add origin https://github.com/usuario/repositorio.git
```
`git push` - Envia commits locais para o repositório remoto. 
```bash
git push origin main
```
`git pull` - Baixa e integra alterações do repositório remoto. 
```bash
git pull origin main
```
`git fetch` - Baixa alterações do repositório remoto sem aplicá-las automaticamente. 
```bash
git fetch
```
`git reset` - Remove arquivos da área de preparação ou retorna o projeto para um estado anterior. 
```bash
git reset HEAD arquivo.txt
```
`git restore` - Descarta alterações realizadas em arquivos. 
```bash
git restore arquivo.txt
```

## Desafio: Desfazer um commit sem apagar o histórico

## Cenário

Pedro realizou um commit e enviou para o GitHub. Após alguns testes, percebeu que a alteração causou erros no sistema. Como outros membros da equipe já baixaram esse commit, ele não quer apagar o histórico do repositório.

## Solução: git revert

o comando `git revert` cria um novo commit que desfaz as alterações de um commit anterior, mantendo o histórico do projeto intacto.

## Passo a passo

1. Verificar o histórico de commits

```bash
git log --oneline
``` 

Exemplo de saída: 

a1b2c3d Adiciona tela de login 
e4f5g6h Corrige erro no cadastro

2. Reverter o commit problemático
```bash 
git revert: a1b2c3d