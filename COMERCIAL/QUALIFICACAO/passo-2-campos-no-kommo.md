# Passo 2 — Campos personalizados no Kommo

> Os campos do card (lead) onde o bot grava as respostas do passo 1. Assim a
> qualificação fica **registrada e pesquisável**, e o Carlos vê tudo pronto sem
> reperguntar.

---

## ⚠️ Auditoria da Kommo (14/07/2026) — a maioria dos campos JÁ EXISTE

Auditei os campos reais via API (`GET /api/v4/leads/custom_fields`, 24 campos).
Boa parte do que o passo 1 pede **já está criado na Kommo** — só que com **nomes
diferentes** e, em vários casos, como **texto livre** (preenchido na mão), não
como lista que o bot consegue mapear e triar.

**Regra desta etapa:** **reaproveitar o que existe**, criar só o que falta e
**converter os eliminatórios de texto → lista** (para o bot classificar sozinho).

### Mapa: pergunta (passo 1) → campo real na Kommo

| Pergunta / campo do passo 1 | Já existe? | Campo real na Kommo (id) | Ação recomendada |
|---|---|---|---|
| P1 `Empresa/Segmento` | ❌ não | — (usa o nome do lead) | Opcional criar (texto) |
| P2 `Localização` | ✅ sim | **Cidade** (2034336, smart_address) | Usar o existente |
| P3 `Já investe? / quanto` | ⚠️ parcial | **Investimento em trafégo** (2033012, num) | Usar; valor > 0 = já investe |
| P4 `Verba de mídia mensal` | ❌ não | — (≠ Honorários) | **Criar (numérico)** — eliminatório |
| P5 `Quem atende os leads` | ⚠️ parcial | **Conseguiria suprir a demanda?** (2032434, texto) | Reaproveitar/renomear |
| P6 `Produz conteúdo` | ❌ não | — | Criar (lista) — sinal positivo |
| P7 `Objetivo` | ⚠️ parcial | **Principal dor** (2032430, texto) | Reaproveitar |
| P8 `É o decisor` | ⚠️ parcial | **Sócio(s)? Qual(is)?** (2032436, texto) | Melhor **criar lista Sim/Não** |
| P8 `Urgência` | ✅ sim | **Urgência** (2032432, **texto livre**) | **Converter p/ lista** |
| `Classificação` (apto/nutrir/descartar) | ❌ não | — | **Criar (lista)** — chave da triagem |

### Campos úteis que já existem (contexto, não precisam ser recriados)

`Média mensal de clientes` (2032428) · `Honorários` (2033016) ·
`Data Reunião/Horário` (2033014) · `Data de Follow Up` (2031860) ·
`Instagram` (2032962) · `Observação` (2034554) · `Data Contrato Fechado` (2049794).

> Rastreio: os 10 campos de UTM/tracking (utm_source, utm_campaign, fbclid…)
> **existem mas estão vazios** em 100% da amostra recente — furo de atribuição a
> tratar depois (não é desta etapa).

---

## O que criar / ajustar (comece ENXUTO)

Para o smoke test, mexer só no essencial:

**Criar (3 campos novos):**
1. `Verba de mídia` — numérico (R$) — **eliminatório**.
2. `É o decisor` — lista (Sim / Não / Tem acesso) — **eliminatório**.
3. `Classificação` — lista (Apto / Nutrir / Descartar) — **saída da triagem**.

**Converter (1 campo):**
4. `Urgência` (2032432) — de texto livre → lista (Agora / 30 dias / Sem pressa).

**Reaproveitar como estão:** `Cidade`, `Investimento em trafégo`,
`Conseguiria suprir a demanda?`, `Principal dor`.

> Menos campos = bot mais leve no smoke test. O resto entra depois se necessário.

## Como configurar (na interface da Kommo)

1. Abrir um Lead → **Configurar campos** do cartão.
2. Criar/ajustar os 4 campos acima com o tipo indicado.
3. No **Sales Bot**, mapear cada resposta para o campo correspondente.

## Verificação via API (sessão com KOMMO_TOKEN)

- Listar os campos para confirmar criação/ajuste: `GET /api/v4/leads/custom_fields`
- Após um lead-teste, ler o card e conferir a gravação:
  `GET /api/v4/leads/{id}?with=...`

> O Claude pode criar os 3 campos novos via API (escopo `crm`) se o Carlos
> autorizar — ou o Carlos cria na interface. A leitura de validação o Claude faz
> sozinho na sessão com Kommo.
