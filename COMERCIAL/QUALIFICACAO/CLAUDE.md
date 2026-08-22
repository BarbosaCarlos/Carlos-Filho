# QUALIFICAÇÃO — processo comercial

> Processo (Etapa 1 do `../mapa-automacoes-comercial.md`). Objetivo: fazer o bot
> qualificar o lead **no automático**, coletando o que o Carlos hoje pergunta na
> mão, para que ele **não precise mais requalificar** antes da reunião. Herda o
> contexto de `../CLAUDE.md`, `../../CLAUDE.md` e `../../empresa.md`.

---

## 🎯 Objetivo

Transformar a etapa de qualificação (hoje manual) em algo que o **Sales Bot da
Kommo** faz sozinho: pergunta, registra as respostas em **campos do card** e
**triagem** o lead (apto / nutrir / descartar) segundo o ICP. O Carlos só recebe
para reunião quem já chegou qualificado.

## 🧩 Como se encaixa no funil

`Lead de entrada` → **[QUALIFICAÇÃO automática]** → `Pré-qualificado (apto)` →
agendamento de reunião. Quem não passa vai para `Nutrição` ou `Descartado`.

## 📥 Entrada / 📤 Saída

- **Entrada:** lead novo no WhatsApp/Kommo (etapa "Lead de entrada"), após o
  primeiro atendimento do bot.
- **Saída:** card com os **campos de qualificação preenchidos** + classificado
  em apto / nutrir / descartar.

## 🛠️ Onde é configurado

- **Roteiro e regras:** definidos aqui (passos abaixo).
- **Execução:** Sales Bot + campos personalizados na **Kommo** (interface).
- **Verificação:** via API (`KOMMO_TOKEN`) — conferir se os campos existem e se
  as respostas estão sendo gravadas nos cards.

## 🗂️ Passos deste processo

1. `passo-1-roteiro-qualificacao.md` — as perguntas do bot (roteiro).
2. `passo-2-campos-no-kommo.md` — os campos personalizados para guardar as
   respostas.
3. `passo-3-regra-de-avanco-e-smoke-test.md` — critério de apto/nutrir/descartar
   e o smoke test de validação.

## ✅ Status

🔄 Em construção / a testar (smoke test pendente na sessão com Kommo).
