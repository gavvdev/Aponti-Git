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