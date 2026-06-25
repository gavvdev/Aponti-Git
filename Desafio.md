## Desafio: Desfazer um commit sem apagar o histórico

## Cenário

Pedro realizou um commit e enviou para o GitHub. Após alguns testes, percebeu que a alteração causou erros no sistema. Como outros membros da equipe já baixaram esse commit, ele não quer apagar o histórico do repositório.

## Solução: git revert

O comando `git revert` cria um novo commit que desfaz as alterações de um commit anterior, mantendo o histórico do projeto intacto.

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
git revert a1b2c3d
```
O git criará automaticamente um novo commit desfazendo as alterações.

3. Enviar a correção para o GitHub
```bash
git push origin main
```

## Resultado 

Utilizando o `git revert`, Pedro consegue desfazer um commit incorreto sem alterar o histórico do projeto, garantindo que todos os membros da equipe continuem sincronizados.

## Desafio 2: Aproveitar apenas um commit de outra branch

## Cenário

Pedro está trabalhando na branch `nova-feature`, onde realizou vários commits. Durante o desenvolvimento, percebe que um dos commits contém uma correção importante que também precisa estar na branch `main`.

No entanto, ele não quer mesclar toda a branch, apenas aquele commit específico.

## Solução: git cherry-pick

O comando `git cherry-pick` permite copiar um commit específico de uma branch para outra.

## Passo a passo

1. Visualizar o histórico da branch
```bash
git log --online
```

Exemplo:

a1b2c3d Corrige erro no login 
e4f5g6h Adiciona tela de cadastro

2. Trocar para a branch que receberá a correção
```bash
git checkout main
```

3. Aplicar apenas o commit desejado
```bash
git cherry-pick a1b2c3d
```

O git copiára apenas as alterações daquele commit para a branch atual.

4. Enviar a atualização para o repositório remoto
```bash
git push origin main
```

## Resultado

Utilizando `git cherry-pick`, Pedro consegue reaproveitar uma correção importante sem precisar mesclar toda a branch `nova-feature`, evitando alterações desnecessárias na `main`.