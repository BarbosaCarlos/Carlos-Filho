# Passo 2 — Campos personalizados no Kommo

> Os campos do card (lead) onde o bot grava as respostas do passo 1. Assim a
> qualificação fica **registrada e pesquisável**, e o Carlos vê tudo pronto sem
> reperguntar.

---

## Campos a criar na Kommo (no cartão de Lead)

| Campo | Tipo sugerido | Vem da pergunta |
|-------|---------------|-----------------|
| `Empresa/Segmento` | Texto | P1 |
| `Localização` | Texto | P2 |
| `Já investe em tráfego` | Lista (Sim/Não) | P3 |
| `Valor investido hoje` | Numérico (R$) | P3 |
| `Verba de mídia mensal` | Numérico (R$) | P4 |
| `Quem atende os leads` | Lista (Dono / Vendedor / Time / Ninguém) | P5 |
| `Produz conteúdo` | Lista (Sim, com responsável / Sim, informal / Não) | P6 |
| `Objetivo` | Texto | P7 |
| `É o decisor` | Lista (Sim / Não / Parcial) | P8 |
| `Urgência` | Lista (Agora / 30 dias / Sem pressa) | P8 |
| `Classificação` | Lista (Apto / Nutrir / Descartar) | calculado no passo 3 |

## Como configurar (na interface da Kommo)

1. Abrir um Lead → **Configurar campos** do cartão.
2. Criar cada campo acima com o tipo indicado.
3. No **Sales Bot**, mapear cada resposta para o campo correspondente.

## Verificação via API (sessão com KOMMO_TOKEN)

- Listar os campos personalizados para confirmar que foram criados:
  `GET /api/v4/leads/custom_fields`
- Após um lead-teste, ler o card e conferir se as respostas foram gravadas:
  `GET /api/v4/leads/{id}?with=...`

> O Claude pode rodar essas leituras na sessão com Kommo para validar sem você
> precisar conferir na mão.

## Observação

- Comece **enxuto**: se achar muitos campos, dá para começar só com os
  eliminatórios (`Verba de mídia mensal`, `É o decisor`, `Localização`) e
  crescer depois. Menos campos = bot mais leve no smoke test.
