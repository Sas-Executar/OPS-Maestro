# CLAUDE.md

## Autonomia operacional

Este repositório autoriza o Claude Code a executar tarefas ponta a ponta diretamente na branch `main`, conforme `docs/adr/ADR-001-claude-code-direto-main.md`.

### Regra padrão

Quando o usuário delegar uma tarefa, essa solicitação constitui autorização suficiente para:

- trabalhar diretamente na `main`;
- criar, modificar, mover ou remover arquivos dentro do escopo;
- executar testes, linters, formatadores, builds e validações;
- corrigir erros e refatorar código relacionado à tarefa;
- criar um ou mais commits claros;
- fazer push diretamente para `main`.

Não abrir Pull Request nem solicitar confirmação para commit/push por convenção.

### Antes do push

Sempre que aplicável:

1. verificar o estado atual do repositório;
2. preservar alterações não relacionadas;
3. executar as validações relevantes;
4. verificar que segredos, credenciais e arquivos sensíveis não serão versionados;
5. usar mensagens de commit claras;
6. reportar falhas preexistentes não relacionadas sem bloqueá-las automaticamente.

### Quando usar Pull Request

Usar PR somente se:

- o usuário pedir explicitamente;
- uma política técnica impedir push direto;
- uma integração externa exigir PR.

### Confirmação obrigatória

Solicitar confirmação antes de ações externas irreversíveis ou materialmente destrutivas, incluindo:

- apagar dados de produção;
- executar migrações destrutivas irreversíveis;
- remover infraestrutura de produção;
- alterar ou revogar credenciais;
- modificar faturamento ou recursos pagos;
- publicar externamente conteúdo com efeito jurídico ou financeiro.

Alterações normais de código e configuração versionadas no repositório não exigem confirmação adicional.

### Escalada

Interromper somente quando houver decisão material impossível de inferir com segurança a partir da tarefa, código ou documentação.

## Fonte normativa

Em caso de dúvida sobre autonomia de commit/push, prevalece o ADR aceito:

`docs/adr/ADR-001-claude-code-direto-main.md`
