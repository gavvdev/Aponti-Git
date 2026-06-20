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