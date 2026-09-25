# ADR-001: Claude Code autorizado a operar diretamente na main

- **Status:** Aceito
- **Data:** 2026-09-24
- **Decisão:** Permitir que o Claude Code modifique, faça commit e envie alterações diretamente para a branch `main`, sem abertura obrigatória de Pull Request e sem solicitar autorização humana a cada alteração.

## Contexto

O fluxo de desenvolvimento utiliza Claude Code como agente autônomo para implementação, manutenção, correções e evolução do projeto.

A exigência de abrir Pull Requests ou solicitar confirmação antes de cada commit/push introduz interrupções no fluxo autônomo e exige intervenção manual mesmo quando a tarefa já foi delegada explicitamente ao agente.

O objetivo desta decisão é tornar o Claude Code capaz de concluir tarefas ponta a ponta sem depender de aprovação intermediária.

## Decisão

O Claude Code está explicitamente autorizado a:

- trabalhar diretamente sobre a branch `main`;
- criar, modificar, mover e remover arquivos necessários para concluir a tarefa;
- executar testes, linters, formatadores, builds e ferramentas de validação;
- criar commits diretamente na `main`;
- executar `git push` diretamente para `main`;
- realizar múltiplos commits quando necessário;
- corrigir erros encontrados durante a execução sem solicitar nova autorização;
- refatorar código relacionado à tarefa quando necessário para entregar uma solução consistente.

O Claude Code não deve abrir Pull Request como etapa padrão.

O Claude Code não deve solicitar confirmação antes de commit ou push quando a ação estiver dentro do escopo da tarefa recebida.

A solicitação inicial da tarefa pelo usuário deve ser considerada autorização suficiente para executar as alterações necessárias até sua conclusão.

## Regras operacionais

Antes de enviar alterações para `main`, o agente deve, sempre que aplicável:

1. verificar o estado atual do repositório;
2. preservar alterações existentes que não façam parte da tarefa;
3. executar as validações relevantes disponíveis no projeto;
4. evitar incluir segredos, credenciais ou arquivos sensíveis no commit;
5. produzir commits com mensagens claras;
6. interromper apenas quando existir uma decisão material impossível de inferir com segurança a partir do código, documentação ou tarefa recebida.

Falhas em testes preexistentes que não tenham relação com a tarefa não bloqueiam automaticamente o trabalho, mas devem ser reportadas ao final.

## Ações destrutivas

A autorização para operar diretamente na `main` não implica autorização irrestrita para ações externas irreversíveis.

O agente deve solicitar confirmação antes de operações como:

- apagar dados de produção;
- executar migrações destrutivas irreversíveis;
- remover infraestrutura de produção;
- alterar ou revogar credenciais;
- modificar faturamento ou recursos pagos;
- publicar externamente algo que produza efeito jurídico ou financeiro.

Alterações normais de código e configuração versionadas no repositório não exigem essa confirmação.

## Pull Requests

Pull Requests somente devem ser usados quando:

- o usuário pedir explicitamente;
- uma política técnica do repositório impedir push direto;
- uma integração externa depender obrigatoriamente de PR.

O agente não deve criar PR apenas por convenção quando possuir permissão para concluir a tarefa diretamente na `main`.

## Consequências

### Positivas

- menor necessidade de intervenção humana;
- execução ponta a ponta das tarefas;
- menor latência entre solicitação e entrega;
- fluxo adequado para desenvolvimento orientado por agentes.

### Riscos

- alterações incorretas podem chegar diretamente à `main`;
- erros de automação podem afetar imediatamente o branch principal;
- há menor oportunidade de revisão humana antes da integração.

Esses riscos são aceitos deliberadamente em troca de maior autonomia operacional.

## Princípio de operação

Quando uma tarefa for delegada ao Claude Code, a autorização cobre implementação, validação, commit e push diretamente para `main`, salvo quando o usuário estabelecer explicitamente uma restrição diferente.
