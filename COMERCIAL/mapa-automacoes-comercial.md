# Mapa de automações do comercial — Campanhas ON

> Documento vivo. Objetivo: automatizar o comercial **por etapas**, do jeito que
> o Carlos pediu — implementar aos poucos, cada bloco validado por **smoke test**
> (testa → deu certo, implementa; não deu, remodela). Foco na dor nº 1:
> **gestão de tempo** (oportunidades perdidas por sobrecarga).
>
> Ferramenta principal do funil: **Kommo**. O ClickUp fica para processos
> internos (não é o funil de vendas).

---

## 0. Onde paramos (última atualização: 2026-07-14)

- **Base da empresa** documentada (`../empresa.md`) e áreas criadas.
- **Atendimento inicial** (ex-"Recebimento") revisado e **auditado na Kommo** —
  ver `ATENDIMENTO-INICIAL/CLAUDE.md` (as-is + auditoria + bots + veredito).
- **Etapa 1 (Qualificação)** em `QUALIFICACAO/` — **auditoria feita (14/07)**:
  campos reais da Kommo mapeados (14 já existem, criar só 3), escopo do smoke
  test fechado (**só inbound**, bot [BOT] Boas-vindas). Falta criar os campos e
  rodar o smoke test com 3 leads inbound.
- **Auditoria do funil (Etapa 0):** feita — 2 pipelines, 14 etapas, bots
  inventariados. Respostas em `ATENDIMENTO-INICIAL/CLAUDE.md`.
- **Decisão (14/07):** separar a base **TPE** (outbound) do funil principal para
  não inflar o pipeline nem distorcer a qualificação.

---

## 1. Processo atual (as-is) — jul/2026

1. **Entrada do lead:** vem do **tráfego** ou do **link da bio** do Instagram e
   cai direto no **WhatsApp comercial** (vinculado à Kommo). Contatos por
   WhatsApp e Instagram caem **direto na Kommo**, na etapa **"Lead de entrada"**.
2. **Atendimento inicial:** já existe um **Sales Bot** que faz o primeiro
   atendimento do lead. ✅ (já automatizado)
3. **Qualificação:** há um robô que faz uma **qualificação parcial**, mas o
   Carlos ainda **reforça a qualificação manualmente** antes de liberar para
   reunião.
4. **Agendamento:** o Carlos entra em contato **manualmente** para marcar a
   reunião.
5. **Pipeline:** o Carlos **move o lead pelas etapas manualmente**. Dúvida em
   aberto: as etapas atuais estão boas? Falta configurá-las melhor?
6. **Recursos disponíveis mas subutilizados:**
   - **Follow-ups programados** (e agendar reunião automática se o lead responder).
   - **WhatsApp IA** para atendimento automático.

**Gargalos de tempo (o que mais consome o Carlos hoje):** reforço manual da
qualificação, marcação manual de reunião, movimentação manual do pipeline e
follow-ups não sistematizados (= oportunidades perdidas).

---

## 2. Princípios do plano

- **Por etapas:** um bloco de cada vez, do mais fundamental ao mais avançado.
- **Smoke test antes de escalar:** cada bloco é testado com poucos leads reais
  (ou um lead-teste) antes de virar padrão.
- **Base antes de topo:** automação depende de o pipeline estar bem definido.
- **Tom alinhado aos valores:** transparência e honestidade (nada de "lábia"),
  inclusive nos bots.

---

## 3. Mapa por etapas

Legenda de status: ⬜ não iniciado · 🔄 em teste · ✅ implementado

### Etapa 0 — Fundação: pipeline e critérios ⬜
Base de tudo. Sem etapas bem definidas, as automações quebram.
- **0.1** Auditar as etapas atuais do funil na Kommo (o que existe hoje).
- **0.2** Confirmar/redefinir as etapas ideais. Rascunho a validar:
  `Lead de entrada → Atendido (bot) → Pré-qualificado → Reunião agendada →
  Reunião realizada → Proposta enviada → Fechamento (Ganho / Perdido)`.
- **0.3** Definir o **critério objetivo** de entrada/saída de cada etapa
  (o "quando o card move").
- **Smoke test:** pegar ~3 leads reais recentes e encaixá-los nas etapas novas;
  se todos couberem sem gambiarra, a base está boa.

### Etapa 1 — Qualificação automática 🔄  *(maior ganho de tempo)*
Tira do Carlos o reforço manual de qualificação.
> Detalhada em `QUALIFICACAO/` (roteiro, campos e smoke test). Smoke test
> pendente na sessão com Kommo.
- **1.1** Escrever o **roteiro de qualificação** (as perguntas que o Carlos faz
  hoje), ancorado no ICP (`../empresa.md`): capacidade de investimento,
  segmento, produz conteúdo / tem social media, expectativa, etc.
- **1.2** Aprimorar o Sales Bot para coletar essas respostas no WhatsApp e
  **gravar em campos personalizados** do card na Kommo.
- **1.3** Regra: só quem passa nos critérios avança para "apto a reunião"; os
  demais vão para nutrição ou descarte.
- **Smoke test:** rodar o roteiro com alguns leads e conferir se as respostas
  caem nos campos certos e se a triagem bate com o julgamento do Carlos.

### Etapa 2 — Agendamento automático de reunião ⬜
Tira a marcação manual.
- **2.1** Criar **link de agendamento** com os horários do Carlos.
- **2.2** O bot oferece o agendamento automaticamente ao lead **qualificado**.
- **2.3** Ao agendar, o card move sozinho para "Reunião agendada" e cria o
  evento/tarefa.
- **Smoke test:** um lead-teste agenda pelo link; verificar se entra na agenda e
  move o card.

### Etapa 3 — Movimentação automática no pipeline ⬜
Tira o "arrastar card" manual.
- **3.1** Automações por gatilho: respondeu → move; qualificou → move; agendou
  → move; compareceu → move.
- **3.2** Tarefa automática para o Carlos em cada transição (ex.: "enviar
  proposta").
- **Smoke test:** simular um lead passando pelos gatilhos e ver se ele anda
  sozinho pelo funil.

### Etapa 4 — Follow-ups automáticos ⬜  *(quick win: recupera oportunidades)*
Ataca diretamente as "oportunidades perdidas por sobrecarga".
- **4.1** Sequência de follow-ups programados para quem não responde
  (ex.: D+1, D+3, D+7).
- **4.2** Se o lead responder → agendar reunião automática / notificar o Carlos.
- **4.3** Encerrar leads frios após X tentativas (higiene do funil).
- **Smoke test:** lead-teste que não responde; ver se a sequência dispara nos
  tempos certos e para assim que responde.

### Etapa 5 — Atendimento com WhatsApp IA ⬜  *(avançado / cautela)*
- **5.1** Avaliar o recurso de WhatsApp IA (o que faz, limites, custo).
- **5.2** Definir escopo: até onde a IA atende sozinha e **quando passa para
  humano**.
- **5.3** Ajustar o tom de voz aos valores (transparência/honestidade).
- **Smoke test:** conversas-piloto controladas e revisão das transcrições antes
  de soltar para leads reais.

### Etapa 6 — Painel/visão do funil ⬜
Decisão sem esforço — apoia a gestão de tempo.
- **6.1** Definir os números que importam (conversão por etapa, tempo em cada
  etapa, leads parados).
- **6.2** Automatizar um **resumo periódico** que chega pronto para o Carlos.
- **Smoke test:** gerar o resumo uma vez e ver se ele responde "onde estou
  perdendo lead".

---

## 4. Ordem recomendada

1. **Etapa 0** (rápida, destrava tudo).
2. **Etapa 1** (maior economia de tempo) **ou Etapa 4** (quick win mais fácil,
   nativo da Kommo) — dá para fazer a 4 em paralelo com a 1.
3. Etapas 2 e 3 (agendamento + movimentação).
4. Etapa 5 (WhatsApp IA) e Etapa 6 (painel) por último.

> Nada é feito "de uma vez". Cada etapa só vira padrão depois do smoke test.

## 5. Observação técnica

A **configuração** dos bots/automações é feita na **interface da Kommo**. O
Claude apoia em: desenhar o fluxo, escrever roteiros/mensagens, definir campos e
critérios, e **verificar via API** (`KOMMO_TOKEN`) se o pipeline, os campos e a
movimentação dos cards estão como o esperado. A auditoria da Etapa 0 (ler as
etapas reais) precisa da sessão com o `KOMMO_TOKEN` disponível.

---

_Documento iniciado em 2026-07-14. Atualizar o status de cada etapa conforme os
smoke tests forem validando._
