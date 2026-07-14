# ATENDIMENTO INICIAL — processo comercial

> Topo do funil: como o lead **entra** e é **atendido pelo bot** antes da
> qualificação. Herda `../CLAUDE.md`, `../../CLAUDE.md` e `../../empresa.md`.
> Registra o **as-is**, a **revisão** (jul/2026) e a **auditoria na Kommo**.
>
> _(Antes chamado "Recebimento". Renomeado em 14/07 — é só o nome da pasta de
> documentação; não altera nada na Kommo nem no bot.)_

---

## Processo atual (as-is)

- Lead vem de **tráfego** ou do **link da bio** do Instagram e cai no **WhatsApp
  comercial** (vinculado à Kommo). Contatos por WhatsApp e Instagram caem
  **direto na Kommo**, na etapa **"Leads de entrada"**.
- Um **Sales Bot** faz o **1º atendimento**.
- Um **robô** faz uma **qualificação parcial**.
- Daí em diante é manual (ver `../mapa-automacoes-comercial.md`).

## Revisão (jul/2026) — o que faz sentido

- Centralizar todos os canais num CRM único (Kommo). ✅
- Bot respondendo na entrada (resposta imediata = maior conversão). ✅
- Etapa de entrada bem definida. ✅

## ✅ Auditoria na Kommo (14/07/2026) — o que a API mostrou

Medido via API (eventos, tarefas, criação de leads, bots). Respostas às
perguntas que estavam em aberto:

- **A Kommo marca a origem?** → **Parcial.** Sim no **nível de canal**
  (`source_id` preenchido em ~86% dos leads recentes); **não** no nível de
  **campanha/anúncio** (todos os campos UTM/`fbclid`/`gclid` **vazios**). Furo de
  atribuição confirmado — a tratar depois (não é desta etapa).
- **"Sales Bot" e "robô de qualificação" são um ou dois fluxos?** → São **bots
  separados** na Kommo (inventário abaixo). O atendimento inicial é o
  **[BOT] Boas-vindas Campanhas ON**.
- **Existe gatilho de handoff bot → Carlos?** → **Fraco.** Só 18 tarefas no
  total, todas do Carlos, antigas (março), 5 abertas. Não há criação sistemática
  de tarefa/notificação quando o lead esquenta → depende do Carlos ver o chat.
- **Controle de duplicidade?** → Há eventos de `entity_linked` (vínculo de
  contatos/leads), mas não dá pra confirmar 100% a deduplicação só pela API.

### Como o recebimento realmente funciona (dois caminhos no mesmo funil)

1. **Inbound (funciona bem):** leads criados **automaticamente** pela integração
   de chat (`created_by=0`), todo dia. O bot faz o grosso — **~90% das mensagens
   recentes são do bot**. A etapa "Leads de entrada" fica com **0 parados**.
2. **Outbound TPE (à parte):** base do TPE trabalhada por **transmissão/cold
   call** (bot próprio). Foi **importada em lote** (122 leads em ~2 min no 22/05).
   Vive em CRM separado (Excel) — **fora do escopo** da automação inbound.
   → Decisão (14/07): separar o TPE do funil principal.

### Inventário de bots (Kommo, via `GET /api/v4/bots`)

- **[BOT] Boas-vindas Campanhas ON** (ativo) — atendimento inicial dos leads que chegam.
- **[BOT] Follow-up Eterno** (ativo) — follow-up já rodando (adianta a Etapa 4).
- **[BOT] Abordagem TPE** + **Transmissão Abordagem TPE** + **Transmissão (22/05/2026)** — máquina de outbound do TPE.
- Outros: TestBot, Robô de NPS, [BOT] Site ON, Salesbot #10.

> Limite: a API mostra os bots (nome + ativo), mas **não** o roteiro/mensagens de
> dentro. Para revisar o **texto** do Boas-vindas, pegar um print do fluxo.

## Veredito

Esqueleto correto e **o bot inbound funciona bem** — não precisa refazer. O que
falta é **fechar as bordas**: (1) **handoff com gatilho** (tarefa/aviso quando o
lead esquenta), (2) **atribuição de campanha** (UTMs vazios), e (3) manter o
**TPE separado** para não inflar o funil nem distorcer a qualificação.

## Perguntas ainda abertas (para print/interface)

- [ ] Qual o **texto/lógica** do [BOT] Boas-vindas? (não visível via API)
- [ ] O handoff hoje é manual mesmo? (confirmar na interface)
