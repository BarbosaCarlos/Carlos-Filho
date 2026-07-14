# 🗂️ Estrutura do workspace — Carlos Filho (Campanhas ON)

> Mapa único de todas as pastas e arquivos deste repositório. Serve pra você ver
> o panorama inteiro **sem depender da aba Diff** (que só mostra o que mudou).
> Documento vivo — atualizar quando criar/renomear pastas.

_Última atualização: 2026-07-14._

---

```
Carlos-Filho/                                (raiz = workspace pessoal do Carlos)
├── CLAUDE.md                                # contexto raiz (papel do Claude + escopo)
├── empresa.md                               # dossiê da Campanhas ON (referência)
├── ESTRUTURA.md                             # este mapa
├── checklist-setup.html                     # checklist de setup (HTML)
│
├── COMERCIAL/                               # chapéu: Gerente Comercial (funil e vendas)
│   ├── CLAUDE.md                            # contexto da área comercial
│   ├── mapa-automacoes-comercial.md         # plano-mestre: automação por etapas
│   │
│   ├── RECEBIMENTO/                         # topo do funil: entrada + bot atende
│   │   └── CLAUDE.md                        #   as-is + furos + perguntas em aberto
│   │
│   └── QUALIFICACAO/                        # Etapa 1 (em teste) — qualificação automática
│       ├── CLAUDE.md                        #   visão geral da etapa
│       ├── passo-1-roteiro-qualificacao.md  #   perguntas do bot
│       ├── passo-2-campos-no-kommo.md       #   campos (mapeados aos reais da Kommo)
│       └── passo-3-regra-de-avanco-e-smoke-test.md   #   triagem + smoke test inbound
│
└── GESTAO/                                  # chapéu: Diretor (decisões macro)
    ├── CLAUDE.md
    └── AVALIACAO-DE-PROCESSOS/              # delegar / automatizar / eliminar / manter
        └── CLAUDE.md
```

## Como navegar

- **Contexto de cada área:** cada pasta tem um `CLAUDE.md` que explica o "chapéu"
  dela. As áreas (`COMERCIAL`, `GESTAO`) são **irmãs** — nenhuma acima da outra.
- **Onde estamos no comercial:** ver `COMERCIAL/mapa-automacoes-comercial.md`
  (seção "0. Onde paramos").
- **Referência da empresa:** `empresa.md` (proposta, ICP, preços, time, canais).

## Legenda de status (comercial)

- **RECEBIMENTO/** — revisado; auditado na Kommo (14/07). Bot de entrada ativo.
- **QUALIFICACAO/** — 🔄 em teste; campos reais mapeados, smoke test inbound pendente.
