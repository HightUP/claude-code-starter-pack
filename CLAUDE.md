# <Nome do Projeto>

> Esse arquivo é lido pelo Claude no início de toda conversa.
> **Mantenha curto e humano.** Para regras determinísticas, use `settings.json`.
> Para conhecimento sob demanda, use `.claude/skills/`.

## Stack

- **Backend:** 
- **Frontend:** 
- **Infra:** 
- **Padrão:** 

## Comandos essenciais

```bash
# Setup
make install            # instala deps Python + Node
make dev                # sobe dev server (ambos)

# Qualidade
make lint               # ruff + eslint
make typecheck          # mypy + tsc
make test               # pytest + vitest

# Deploy
make deploy-staging
make deploy-prod        # roda smoke tests primeiro
```

## Convenções

- **Branches:** `feat/<slice>-<short-desc>`, `fix/<short-desc>`, `chore/<short-desc>`
- **Commits:** Conventional Commits (`feat:`, `fix:`, `chore:`, `docs:`)
- **PRs:** Sempre referencie a issue, descreva o "porquê", não só o "o quê"
- **Tests:** TDD onde a complexidade pede; testes lêem como spec

## Estrutura

```

```

## Protocolo de continuidade (arquivos vivos)

Contexto de sessão reseta, comprime ou muda de chat. Estes dois arquivos existem pra sobreviver a isso — mantenha sempre atualizados, independente de qual skill/fluxo estiver conduzindo o trabalho (inclusive Superpowers, se instalado no projeto):

- **`docs/STATUS.md`** — estado atual do projeto: o que já foi feito, o que falta, fase/tarefa atual, próximo passo recomendado, data da última atualização.
- **`docs/ERROS.md`** — memória de erros: sintoma, causa, solução aplicada, como evitar no futuro. Antes de investigar um bug, confira se ele já apareceu aqui.

**Antes de qualquer tarefa não-trivial:** leia `docs/STATUS.md` e `docs/ERROS.md` se existirem.
**Ao terminar qualquer tarefa não-trivial:** atualize `docs/STATUS.md`; se apareceu erro, registre em `docs/ERROS.md` no formato:

```
## <data> - <título curto do erro>
- Sintoma:
- Causa:
- Solução aplicada:
- Como evitar no futuro:
```

Se esses arquivos não existirem ainda no projeto, crie-os na primeira tarefa em vez de pular a etapa.

## Se o plugin Superpowers estiver ativo neste projeto

Superpowers (brainstorming → writing-plans → subagent-driven-development) já é uma metodologia completa de spec→plano→build com seu próprio doc de design (`docs/superpowers/specs/`) e plano (`docs/superpowers/plans/`). Não crie um segundo pipeline concorrente por cima dele.

- Deixe o Superpowers conduzir spec/plano/execução quando ele disparar.
- O protocolo de `docs/STATUS.md`/`docs/ERROS.md` acima é complementar, não concorrente — mantenha atualizado mesmo quando for o Superpowers quem está fazendo o trabalho.
- Pra decisões técnicas específicas de sistema web (auth, RBAC, soft delete, auditoria, uploads, migrations), use a skill `web-app-checklist` como apoio — ela não faz gate, só complementa as perguntas do `brainstorming` quando fizer sentido.

## Quando pedir ajuda

- Para revisão: invoque a skill `code-review-b2`.
- Para auditoria de segurança: invoque a skill `security-check`.
- Para decisões técnicas de sistema web (auth, permissões, dados): invoque a skill `web-app-checklist`.
- Para regras determinísticas (formatação, secrets, comandos perigosos): já há hooks rodando.

## O que NÃO fazer

- Não criar arquivos `.env*` — use Secret Manager / Supabase secrets.
- Não usar `any` em TypeScript sem comentário justificando.
- Não fazer `git push --force` em `main`.
- Não adicionar deps sem rodar audit primeiro.
