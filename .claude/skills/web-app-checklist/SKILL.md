---
name: web-app-checklist
description: Checklist de decisões técnicas para sistemas web com cadastros, autenticação e permissões (CRUD, painel administrativo, portal de cliente). Use como apoio durante brainstorming/planejamento quando o projeto for desse tipo, para não deixar autenticação, RBAC, soft delete, auditoria, uploads, migrations ou logs de segurança sem decisão antes de codificar. Não substitui a skill de brainstorming — complementa com as perguntas específicas de sistema web que ela não cobre.
allowed-tools: Read, Grep, Glob
---

# Web App Checklist — decisões técnicas de sistema web

Complemento de domínio para sistemas do tipo "cadastro + autenticação + permissões"
(painel administrativo, portal de cliente, sistema interno de agência/empresa).
Não é um gate: não bloqueia código, não substitui `brainstorming` nem `writing-plans`.
Use durante a fase de design/plano quando o projeto for desse tipo, pra garantir que
estas decisões fiquem explícitas antes da implementação em vez de serem inventadas
no meio do código.

## Quando usar

- O projeto tem cadastro de usuários, login, ou mais de um perfil de acesso.
- O `brainstorming` do Superpowers (ou outra skill de design) já entendeu o problema,
  mas ainda não decidiu autenticação/permissões/dados sensíveis.
- Alguém vai pedir pra "criar um sistema de [gestão de algo]" com múltiplos usuários.

## Como conduzir

Pergunte uma decisão por vez, só as que ainda não estiverem claras pelo contexto/spec.
Para cada uma: explique por que importa, dê exemplos de resposta, e sugira um padrão
razoável caso o usuário não tenha preferência — mas não presuma stack, banco ou
hospedagem por conta própria; extraia isso do que já foi decidido no projeto (spec,
`CLAUDE.md`, código existente) ou pergunte.

## Checklist de decisões

### 1. Autenticação
- Tipo: e-mail e senha / OAuth / magic link / API token / combinação.
- Recuperação de senha existe? Como funciona?
- Bloqueio por tentativas inválidas?
- Tempo de sessão / expiração de token.

### 2. Perfis e permissões (RBAC)
- Quais perfis existem (ex: admin, operador, cliente)?
- Matriz: cada perfil pode ver/criar/editar/excluir/aprovar o quê?
- Isolamento de dados: usuário só vê o que é seu, ou o que for da sua conta/empresa?
- Permissão validada no servidor, não só escondida no menu.

### 3. Soft delete vs exclusão definitiva
- Quais entidades usam soft delete (registro fica marcado, não some do banco)?
- Quem pode restaurar? Quem pode excluir definitivamente, se alguém puder?

### 4. Auditoria
- Registros principais precisam de `created_at`/`created_by`/`updated_at`/`updated_by`?
- Precisa de histórico de alteração (quem mudou o quê e quando)?

### 5. Logs
- Log de erro: o que é registrado, onde fica, quem pode consultar?
- Se log de erro é gravado em banco: existe fallback em arquivo se o banco cair?
  (ver skill `security-check` para os critérios de proteção desse arquivo)
- Log de segurança: login inválido, acesso negado, bloqueio por tentativas, alteração
  de permissão, exclusão/restauração de registro importante.

### 6. Configuração e segredos
- Onde ficam credenciais (banco, SMTP, API keys)? Secret Manager, env var, ou —
  em stacks sem esse recurso — arquivo de configuração em código fora da pasta
  pública, nunca `.env` exposto por engano.

### 7. Uploads e anexos (só se o projeto tiver)
- Tipos de arquivo permitidos, tamanho máximo.
- Quem envia, quem vê, quem exclui.
- Vínculo do arquivo com o registro do sistema.

### 8. Relatórios e exportações (só se o projeto tiver)
- Só tela, ou precisa exportar (CSV/PDF/Excel)?
- Exportação respeita os mesmos filtros e permissões da tela.

### 9. Migrations / estrutura de banco
- O projeto usa alguma forma de migration versionada (em vez de mexer direto
  em produção)? Como evita rodar a mesma migration duas vezes?
- Migrations não ficam acessíveis por URL pública.

### 10. APIs e integrações externas (só se o projeto tiver)
- Quais sistemas externos, o que é enviado/recebido, como falhas são tratadas.

## Saída

Não gera documento obrigatório. Se o projeto já usa `docs/` para specs (FSD, design
doc do Superpowers, etc.), registre as respostas lá, na seção apropriada. Se não
houver convenção de docs ainda, um resumo direto na conversa é suficiente — o
importante é a decisão ficar explícita, não o formato do arquivo.

## O que NÃO fazer

- Não presuma stack, banco de dados ou hospedagem — isso vem do projeto, não desta skill.
- Não pergunte tudo de uma vez. Uma decisão por vez, só as que ainda estão em aberto.
- Não inclua uploads, exportações ou APIs na conversa se o projeto não tiver isso.
- Não vire gate obrigatório antes de código — isso é papel do `brainstorming`/`writing-plans`, esta skill só supre o que eles não cobrem.
