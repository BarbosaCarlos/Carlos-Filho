# Passo 3 — Regra de avanço + smoke test

> Como o bot decide **apto / nutrir / descartar** a partir das respostas, e como
> validar tudo com um smoke test antes de virar padrão.

---

## Critérios (baseados no ICP — ver `../../empresa.md`)

**Eliminatórios (se falhar, não vai para reunião):**
- **Verba compatível:** consegue honorário a partir de **R$ 2.000/mês** +
  **verba de mídia** de forma contínua. Sem isso → `Nutrir` ou `Descartar`.
- **Acesso ao decisor:** é o decisor ou tem acesso direto a ele. Se não →
  `Nutrir`.

**Sinais positivos (reforçam "Apto"):**
- Produz conteúdo / tem social media.
- Tem quem atenda os leads (comercial minimamente estruturado).
- Visão de resultado (objetivo claro de faturamento/clientes, não só "leads").

**Sinais de risco (atenção, mesmo se passar):**
- Histórico de parar/voltar investimento; expectativa irreal; quer resultado
  imediato sem estrutura.

## Tabela de decisão (simplificada)

| Situação | Classificação | Ação do bot |
|----------|---------------|-------------|
| Verba compatível **+** decisor | **Apto** | Oferecer agendamento de reunião |
| Interesse real, mas sem verba **agora** | **Nutrir** | Entra em trilha de follow-up |
| Sem verba e sem perspectiva / fora do perfil | **Descartar** | Encerrar com cordialidade |
| Não é decisor, mas tem acesso | **Nutrir/Apto** | Pedir contato do decisor |

> Regra prática: **na dúvida, classifica como Nutrir** (não descarta cedo demais
> nem manda lead cru para a reunião do Carlos).

## Escopo (definido na auditoria de 14/07)

- **Só leads INBOUND** — os que **chegam** ao Carlos (WhatsApp/tráfego/bio),
  atendidos pelo bot **[BOT] Boas-vindas Campanhas ON**.
- **NÃO** rodar sobre a base **TPE** (outbound / cold call — bot
  `[BOT] Abordagem TPE`). O TPE tem abordagem própria e vive em outro CRM; a
  régua de qualificação aqui não se aplica a ele.

## Smoke test (rodar na sessão com KOMMO_TOKEN)

**Meta:** provar que o bot qualifica e classifica sozinho, sem o Carlos.

1. **Preparar:** criar/ajustar os 4 campos do passo 2 (Verba de mídia, É o
   decisor, Classificação, Urgência→lista) e mapear o roteiro (passo 1) no
   **[BOT] Boas-vindas**.
2. **Rodar 3 leads inbound** (teste ou reais recentes — nunca TPE), cobrindo:
   um claramente Apto, um Nutrir (sem verba), um Descartar.
3. **Conferir (via API):** para cada lead, checar se:
   - os campos foram preenchidos com as respostas;
   - a `Classificação` bateu com o que o Carlos decidiria na mão.
4. **Critério de sucesso:** ≥ 2 dos 3 classificados igual ao julgamento do
   Carlos, e nenhum "Apto" claramente cru chegando à reunião.

**Se passar:** promover para padrão e seguir para a Etapa 2 (agendamento).
**Se falhar:** ajustar perguntas/critérios e repetir (remodelar, não forçar).

## Registro do teste

<!-- Preencher após rodar o smoke test -->
- Data:
- Leads testados:
- Resultado (acertos/total):
- Ajustes necessários:
- Decisão: (promover / remodelar)
