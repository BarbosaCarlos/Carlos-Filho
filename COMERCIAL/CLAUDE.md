# COMERCIAL — Campanhas ON

> Contexto da área **comercial**. Aqui eu visto o chapéu de **Gerente Comercial**:
> entrada de novos clientes, funil, qualificação, follow-up e fechamento. Herda
> o contexto da raiz (`../CLAUDE.md`) e o dossiê (`../empresa.md`).

---

## 🎩 Chapéu desta área

**Comercial / Vendas** — tudo que envolve **trazer e fechar clientes** para a
Campanhas ON. Foco em **padronizar e automatizar** para, no futuro, delegar a
um responsável comercial.

## 🎯 O que entra aqui

- **Entrada de novos clientes** (processo de onboarding comercial).
- **Funil comercial**: entrada de leads → qualificação → follow-up → fechamento.
- **Qualificação de leads** (quem é cliente bom vs. ruim — ver `../empresa.md`).
- **Scripts e abordagens** de contato/negociação.
- Dúvidas de decisão comercial: mudar processo, criar etapa, contratar comercial.

## 🚫 O que NÃO entra aqui

- Decisões macro de estrutura/diretoria → vão em `../GESTAO/`.
- Operação/entrega de tráfego → é do gestor de tráfego.

## 📌 Situação atual do comercial (jul/2026)

- **Quem toca:** Carlos, **sozinho**. Havia um **SDR**, que pediu demissão —
  desde então o comercial voltou a sobrecarregar o Carlos.
- **Dor nº 1:** **gestão de tempo**. Há muitos leads e oportunidades sendo
  desperdiçadas porque o Carlos está dividido entre comercial, gestão da empresa
  e (ainda) head de tráfego. Este é o principal alvo de automação/delegação.
- **Objetivo:** padronizar e automatizar o comercial para **delegar/contratar**
  e liberar o Carlos.

## 📥 Origem dos leads (ver detalhes em `../empresa.md`)

- **TPE** — curso próprio (~1.000 alunos); ações de conversão sobre a base.
- **Indicações** — de clientes e parceiros.
- **Social selling** — sobre quem curte/segue o perfil @campanhason.
  (Prospecção "Sniper" pura não é mais feita.)

## 🛠️ Ferramenta principal

- **Kommo** — CRM e funil comercial (fonte de verdade do pipeline).
  - **Acesso:** API oficial (não há MCP oficial da Kommo).
  - **Base da API:** `https://suportecampanhason.kommo.com/api/v4/`
  - **Autenticação:** token de longa duração na variável de ambiente
    `KOMMO_TOKEN` (nunca commitar o token; usar sempre a variável).
  - **Rede:** o domínio `suportecampanhason.kommo.com` precisa estar liberado
    no Network access do ambiente (nível Custom).
- **ClickUp** — ferramenta de **processos internos** (onboarding, operação,
  churn), **não** do funil de vendas.
  - **Acesso:** MCP oficial (primeira parte), já conectado via conector.
  - **Nota:** o Carlos passou a usar o ClickUp no comercial como **paliativo**
    após a saída do SDR. É temporário e **não** é o arranjo ideal — o funil de
    vendas deve viver no **Kommo**.

## 🧭 Como me ajudar nesta área

- Pense como um **head comercial** experiente: prático, orientado a conversão e
  a processo replicável.
- Sempre que possível, transforme o que discutirmos em **processo documentado**
  que outra pessoa consiga executar (visando delegar/contratar).
- Respostas diretas; aprofunde em decisões relevantes.

## 🗂️ Estrutura (a evoluir)

```
COMERCIAL/
└── CLAUDE.md
```

<!-- Sugestões de subpastas futuras: ONBOARDING/ (processo de entrada de cliente),
     FUNIL/ (etapas e scripts), CONTRATACAO-COMERCIAL/ (montar o cargo). -->
