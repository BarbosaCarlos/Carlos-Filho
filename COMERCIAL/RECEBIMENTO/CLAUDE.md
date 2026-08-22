# RECEBIMENTO DE LEADS — processo comercial

> Topo do funil: como o lead entra e é atendido antes da qualificação. Herda
> `../CLAUDE.md`, `../../CLAUDE.md` e `../../empresa.md`. Este documento registra
> o **as-is**, a **revisão** (jul/2026) e as **perguntas em aberto** a resolver
> na sessão com o `KOMMO_TOKEN`.

---

## Processo atual (as-is)

- Lead vem de **tráfego** ou do **link da bio** do Instagram e cai no **WhatsApp
  comercial** (vinculado à Kommo). Contatos por WhatsApp e Instagram caem
  **direto na Kommo**, na etapa **"Lead de entrada"**.
- Um **Sales Bot** faz o **1º atendimento**.
- Um **robô** faz uma **qualificação parcial**.
- Daí em diante é manual (ver `../mapa-automacoes-comercial.md`).

## Revisão (jul/2026) — o que faz sentido

- Centralizar todos os canais num CRM único (Kommo). ✅
- Bot respondendo na entrada (resposta imediata = maior conversão). ✅
- Etapa de entrada bem definida. ✅

## Revisão — pontos a verificar / possíveis furos

1. **Rastreio de origem (crítico p/ agência de tráfego):** a Kommo etiqueta de
   qual **canal/campanha/anúncio** veio cada lead? Se todos caem no mesmo
   WhatsApp sem marcação, perde-se a atribuição. **Maior lacuna provável.**
2. **Dois bots:** o "Sales Bot" (atendimento) e o "robô de qualificação" são o
   mesmo fluxo ou dois? Risco de redundância/mensagem repetida. Avaliar unificar.
3. **Handoff bot → Carlos:** qual gatilho avisa que é a vez do humano? Se for
   abrupto, leads ficam parados. Ideal: criar tarefa/notificação automática.
4. **Duplicidade:** mesma pessoa no WhatsApp e no Instagram vira 2 cards ou a
   Kommo une? Duplicata infla o funil.
5. **Lead que não responde ao bot:** morre ali ou entra em follow-up? (liga com
   a Etapa 4 do mapa).
6. **Fora do horário:** o bot segura e dá sequência sozinho de madrugada/fds?

## Veredito

Esqueleto correto (canais → Kommo → bot na entrada). O que falta não é refazer,
e sim **fechar as bordas** — principalmente **rastreio de origem** e **clareza no
handoff**. Duplicidade e "dois bots" são pontos de verificar na prática.

## Perguntas em aberto (responder na sessão com Kommo)

- [ ] A Kommo marca a **origem** de cada lead (tráfego x bio x campanha)?
- [ ] "Sales Bot" e "robô de qualificação" são **um** fluxo ou **dois**?
- [ ] Existe **gatilho de handoff** bot → Carlos hoje?
- [ ] Há **controle de duplicidade** ligado?

## Como auditar de verdade (na sessão com KOMMO_TOKEN)

- Ler o pipeline e as etapas: `GET /api/v4/leads/pipelines`
- Ver campos personalizados (inclui origem?): `GET /api/v4/leads/custom_fields`
- Amostrar leads recentes e checar a origem/canal preenchidos:
  `GET /api/v4/leads?with=source_id,contacts`
