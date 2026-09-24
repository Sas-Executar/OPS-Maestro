# PRE-COMMIT AUDIT REPORT — Risco Cognitivo Launch

## Decisão

**STATUS: READY_FOR_REVIEW — NÃO COMMITAR AINDA**

O pacote foi inventariado, classificado e normalizado em staging. Nenhuma alteração foi enviada ao repositório nesta etapa.

## Resumo

- ZIP de origem: `Risco-Cognitivo-Lauch.zip`
- SHA-256 da origem: `2ab2dc2d84b906e20eb5fc0743d46e4bc450027f245fbad144a2244819005ced`
- 36 entradas no ZIP externo.
- 17 arquivos úteis externos + 1 pacote técnico ZIP aninhado.
- 17 entradas `__MACOSX/._*` (AppleDouble): **DESCARTAR**.
- Pacote técnico interno: 94 arquivos.
- Nenhum segredo/token aparente detectado por varredura textual.
- Filename corrompido do estudo de topologia: corrigido apenas no nome canônico; bytes preservados.
- Documento `PD-CLB-... (1).docx`: byte-a-byte idêntico à cópia já conhecida; nome canônico preserva o ID e remove `(1)`.

## Pacote técnico full stack

`EXECUTAR_BLOG_CLAUDE_DESIGN_REACT_FULLSTACK_001` declara `PREPARED_AND_STRUCTURALLY_VERIFIED`, mas o relatório interno está em `PARTIALLY_VERIFIED`.

Validações internas observadas:
- PACKAGE_STRUCTURE: PASS
- TOKEN_STRUCTURE: PASS
- TOKEN_PROJECTION_SYNC: PASS
- REACT_REQUIRED_FILES: PASS
- SELF_CONTAINED_DEPLOY_ROOT: PASS
- NPM_BUILD: BLOCKED
- DEPLOY: NOT_SUBMITTED

Portanto, **não promover para DONE/100% VERIFIED** antes de `npm run build`, revisão de rotas e preview deploy.

## Duplicações internas conhecidas

Foram encontrados 15 grupos de arquivos byte-idênticos dentro do handoff. Dez são golden screens repetidos entre `01_CLAUDE_DESIGN/golden-screens/` e `04_SOT_VISUAL/mockups/`; os demais são projeções de tokens/contratos e `CLAUDE.md`.

**Ação:** preservar nesta primeira ingestão. O próprio pacote usa essas cópias como SOT/projeção runtime; deduplicação só deve ocorrer após validar referências e intenção arquitetural.

## Política de nomes

Arquivos soltos usam o padrão:

`RC-BLOG-<AREA>-<TIPO>-<SEQ>-V<NN>.<ext>`

IDs canônicos existentes são preservados. O pacote full stack mantém seus nomes internos para não quebrar referências.

## Fonte bruta

O ZIP bruto não foi duplicado dentro do staging. `90-source-archive/SOURCE_ARCHIVE.yaml` registra nome, tamanho e SHA-256. Para retenção integral, prefira armazenamento de archive/release separado do working tree.

## Próximo Gate

Antes do commit:
1. Revisar `00-control/RENAME_MAP.csv`.
2. Confirmar a topologia de diretórios.
3. Aprovar o tratamento do pacote full stack como handoff expandido.
4. Só então executar commit/push.
