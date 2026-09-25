# MASTER INDEX — OPS-Maestro

> **Propósito:** ponto de entrada obrigatório para agentes de IA operando neste repositório.
> **Atualizado:** 2026-09-25
> **Branch canônica:** `main`
> **Estado indexado:** commit `cc8b0e8b6bc30ec7f4df4744bc9738a953441406`

## 1. Ordem de leitura para agentes

1. `MASTER_INDEX.md` — mapa do repositório, estado e prioridades.
2. `CLAUDE.md` — contrato operacional/autonomia.
3. `docs/adr/ADR-001-claude-code-direto-main.md` — decisão normativa sobre operação na `main`.
4. `00-control/VALIDATION_REPORT.md` — gates técnicos atuais.
5. `00-control/PRECOMMIT_AUDIT_REPORT.md` — auditoria do pacote Risco Cognitivo Launch.
6. `00-control/RENAME_MAP.csv` — destino canônico planejado para o staging.
7. `00-control/SUBMISSION_AUTHORIZATION.md` — autorização humana registrada.
8. `inputs/README.md` — catálogo dos inputs existentes.
9. `docs/referencias/auditoria-bpm-e-qualidade.md` — referência de BPM/qualidade.

## 2. Estrutura atual

```text
OPS-Maestro/
├── MASTER_INDEX.md
├── CLAUDE.md
├── .github/workflows/
│   └── reconstruct-copiloto-bundle.yml
├── 00-control/
│   ├── PRECOMMIT_AUDIT_REPORT.md
│   ├── RENAME_MAP.csv
│   ├── SUBMISSION_AUTHORIZATION.md
│   └── VALIDATION_REPORT.md
├── docs/
│   ├── adr/
│   │   └── ADR-001-claude-code-direto-main.md
│   └── referencias/
│       └── auditoria-bpm-e-qualidade.md
└── inputs/
    ├── README.md
    ├── docs/
    │   ├── SOP EXECUTAR Operating System.pdf
    │   ├── audotria > BPM e Qualidade(1).md
    │   └── PD-CLB-20260906-F01-DOC-V01__process-doc-padrao-multiplataforma.docx
    ├── packages/
    │   └── copiloto-executar-solution-store.zip
    └── skills/
        ├── executar-prompt.skill.zip
        ├── executar-safe-frameworks.zip
        └── product-code-development.skill.zip
```

## 3. Contrato operacional vigente

`CLAUDE.md` e ADR-001 autorizam o Claude Code a implementar, validar, fazer commit e push diretamente na `main` dentro do escopo da tarefa delegada. PR não é etapa padrão.

Confirmação humana continua obrigatória para ações externas irreversíveis/materialmente destrutivas, como exclusão de dados de produção, migração destrutiva, remoção de infraestrutura, alteração/revogação de credenciais, faturamento/recursos pagos e publicação com efeito jurídico ou financeiro.

## 4. Estado de governança

O pacote `Risco-Cognitivo-Lauch.zip` foi auditado antes da ingestão:
- 36 entradas externas;
- 17 arquivos úteis + 1 ZIP técnico aninhado;
- 17 entradas AppleDouble descartáveis;
- pacote técnico interno com 94 arquivos;
- 15 grupos de duplicações internas conhecidos;
- nenhum segredo/token aparente detectado pela varredura registrada.

O Gate humano de submissão foi autorizado e a governança correspondente já está na `main`.

## 5. Pendências técnicas conhecidas

**Não interpretar a presença dos documentos de governança como ingestão completa do staging.**

O payload canônico descrito em `00-control/RENAME_MAP.csv` ainda não está materializado integralmente no working tree atual.

O handoff `EXECUTAR_BLOG_CLAUDE_DESIGN_REACT_FULLSTACK_001` permanece **PARTIALLY_VERIFIED**:
- estrutura: PASS;
- tokens/projeções: PASS;
- arquivos React requeridos: PASS;
- deploy root autocontido: PASS;
- `npm run build`: BLOCKED;
- deploy: NOT_SUBMITTED.

Não promover para DONE/100% VERIFIED até build, revisão de rotas e preview deploy serem comprovados.

## 6. Inputs e função

| Input | Função |
|---|---|
| SOP EXECUTAR Operating System | referência operacional/governança |
| auditoria BPM e Qualidade | referência de processo, qualidade e agentic workflow |
| Process Doc multiplataforma | processo/editorial de lançamento |
| executar-prompt.skill.zip | skill de contratos/prompts |
| product-code-development.skill.zip | skill de desenvolvimento de produto/código |
| executar-safe-frameworks.zip | catálogo/frameworks seguros |
| copiloto-executar-solution-store.zip | snapshot/bundle de entrada; não assumir como fonte canônica |

## 7. Regras para próximo agente

- Ler este índice antes de executar alterações.
- Não inventar arquivos/estados ausentes.
- Tratar `00-control/` como evidência de governança, não como prova de implementação.
- Preservar IDs canônicos e hashes registrados.
- Não remover duplicações do handoff sem validar referências.
- Verificar a `main` atual antes de modificar arquivos.
- Atualizar este `MASTER_INDEX.md` quando houver mudança estrutural, novo ADR, novo Gate ou alteração relevante de estado.
- Reportar evidência de validação no encerramento de cada tarefa.

## 8. Próxima prioridade derivada do estado atual

Materializar e reconciliar o staging aprovado descrito em `00-control/RENAME_MAP.csv`, preservando hashes e estrutura; depois executar as validações técnicas ainda bloqueadas do full stack.

Este índice descreve somente o conteúdo e os estados comprováveis no repositório atual. Dependências cross-repo devem ser verificadas em suas respectivas fontes antes de serem tratadas como estado vigente.
