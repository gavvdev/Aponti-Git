# Instalando o Git

<p align="center">
  <img src="assets/config-git.png" alt="Git" width="180">
</p>

Caso o Git ainda não esteja instalado em seu computador:

1. Acesse:

```text
https://git-scm.com/downloads
```

2. Baixe a versão correspondente ao seu sistema operacional;
3. Execute a instalação mantendo as configurações padrão.

---

## Configurando o Git

Após instalar o Git, abra o terminal (Prompt de Comando, PowerShell ou Terminal do VS Code) e execute:

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seuemail@email.com"
```

Exemplo:

```bash
git config --global user.name "Mariana Monteiro"
git config --global user.email "mariana@email.com"
```

Para verificar as configurações:

```bash
git config --global --list
```

Ou consultar cada informação individualmente:

```bash
git config --global user.name
git config --global user.email
```

---

## Fazendo login no GitHub pelo VS Code

<p align="center">
  <img src="assets/vscode.jpg" alt="Vscode" width="180">
</p>

1. Abra o Visual Studio Code;
2. Clique no ícone de **Conta**;
3. Selecione **Sign in with GitHub**;
4. Autorize o acesso no navegador.

Após o login, será possível:

* Clonar repositórios;
* Criar branches;
* Fazer commits;
* Enviar alterações para o GitHub (`git push`);
* Criar Pull Requests.

---

### Dica:

Antes de iniciar qualquer projeto, confirme se o Git está configurado corretamente:

```bash
git config --global user.name
git config --global user.email
```

> Essas informações serão utilizadas para identificar a autoria de todos os commits realizados no repositório.

---

## Arquivos Especiais de Configuração

1. `.gitignore`
é um arquivo de texto onde você lista explicitamente todos os arquivos, formatos ou pastas que o Git **deve ignorar**. Tudo o que estiver documentando aqui não será rastreado pelo Git e não irá para o repositório
	
	> **Para que serve:** Evitar o envio de arquivos gerados automaticamente (como as pastas e arquivo`.env, node_modules, dist` e `build`) e arquivos do própio sistema operacional (como`.DS_Store` no Mac)
2. `.env`
é o arquivo utilizado para armazenar as **variáveis de ambiente** do seu projeto.
	
	> **Para que serve:** Ele guarda dados sensíveis e configurações específicas da sua máquina local, como senhas de bancos de dados, chaves de APIs privadas e portas de servidores.
		**Atenção**: O arquivo `.env` **NUNCA deve ser enviado para o Git**. Por conter dados secretos, o nome `.env` deve ser obrigatoriamente adicionado dentro do seu arquivo `.gitignore`.

---

## Instalação e Configuração
Instalar o Git na sua máquina é muito simples. Basta acessar o site: https://git-scm.com/install/windows e realizar o download de acordo com seu SO.

> Após concluir a instalação, você terá tanto uma versão command line (linha de comando, incluindo um cliente SSH que será útil depois) e uma GUI padrão.

A primeira coisa que você deve fazer quando instalar o Git é definir o seu nome de usuário e endereço de e-mail. Isso é importante porque todos os commits no Git utilizam essas informações, e está imutavelmente anexado nos commits que você realiza.

`git config --global user.name "Fulano De Tal"`
`git config --global user.email "fulanodetal@exemplo.com"`

> Lembrando, você precisa fazer isso uma vez caso passe a opção `--global,` pois o Git sempre usará essa informação para qualquer coisa que você faça nesse sistema. Caso você queira sobrepor estas com um nome ou endereço de e-mail diferentes para projetos especifico, você pode executar a opção `--global` quando estiver no próprio projeto.

Se você precisar de ajuda ao usar o Git, existem três maneiras de obter a ajuda para qualquer um dos comandos Git.

- `git help <comando>`
- `git <comando> --help`
- `man git <comando>`

Extra: O comando principal para listar a lista de comandos disponíveis no Git é: `git help -a`

---

## Verificação
Depois de instalar e configurar o Git, É importante garantir que o terminal do seu sistema operacional consegue reconhecê-lo. Para isso, basta abrir o seu Terminal(Prompt de Comando, Powershell ou Git Bash) e digitar um dos comandos abaixo:

`git --version`

Se tudo estiver correto, o terminal retornará o texto indicando a Versão do Git instalada na sua máquina, algo parecido com:

`git version 2.54.0.windows.1`

Se o terminal retornar uma mensagem de erro como "*commando not found*" ou "*Não é reconhecido como um comando interno*", significa que o Git não foi instalado corretamente ou que o caminho dele não foi adicionado as variáveis de ambiente do seu sistema.

