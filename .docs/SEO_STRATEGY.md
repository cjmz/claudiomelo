# SEO_STRATEGY — claudiomelo.com

**Última atualização:** 2026-07-02
**Fundação criada em:** 2026-07-02 (decisão do dono, sessão `/seo-estrategista`)

> Tático-estratégico: clusters, banco de keywords, metas, riscos. O replanejamento mensal é do `/seo-cluster-planner`; mudanças de pilar/tese são do `/seo-estrategista` (ver `POSITIONING.md`).

---

## Baseline (2026-07-02 — ponto de partida honesto)

| Métrica | Valor | Fonte |
|---|---|---|
| Cliques orgânicos (16 meses) | 7 | GSC export 2026-07-02 |
| Impressões (16 meses) | ~364 | GSC |
| Keywords não-branded ranqueando | 0 | Ubersuggest |
| "claudio melo" (branded) | pos. 14.45, 122 impr., 2 cliques | GSC |
| Domain Authority / backlinks | 2 / 6 (1 dofollow) | Ubersuggest |
| Posts publicados | 2 | repo |
| Geografia das impressões | US 151, BR 44 (pos. 29), CA 21, UK 20 | GSC |

**Expectativa registrada (decisão do dono):** este é um jogo de *audiência certa*, não de volume. Teto realista de 12 meses: **centenas de visitas orgânicas/mês**, não milhares — o nicho tem volumes de 10-1.000/keyword com CPC $10-36 (audiência minúscula e valiosa). Ninguém pivota em pânico no mês 4 por tráfego baixo; os KPIs de sucesso estão abaixo.

## Metas 12 meses (até 2027-07)

1. **DA 2 → ~25-30** (destrava primeira página das SERPs-alvo, onde hoje ranqueiam chalk.ai DA 26, featurestore.org DA 31, qwak DA 33).
2. **Branded "claudio melo": pos. 14 → top 3** (quick win, trimestre 1).
3. **12 âncoras publicadas** (1/mês — o KPI de processo mais importante).
4. ≥ 3 âncoras com tração de distribuição (front page HN, ou >10k impressões LinkedIn, ou backlink editorial espontâneo).
5. 10-15 keywords da cauda (tier entrada) no top 10.
6. Primeiras citações em AI Overviews/LLMs para queries do cluster C1/C2 (verificação manual trimestral).

## Clusters

### C1 — Feature Store (núcleo, ~40% do esforço)
O head "feature store" (1.000/mês, SD 33) é navigational e vendor-dominado; a SERP não tem **nenhuma voz individual** (Databricks DA 77, IBM 93, Microsoft 98 — mas também chalk.ai DA 26 em #9). Entrada pela cauda informacional/comparativa que vendors não cobrem com honestidade.

### C2 — ML Infrastructure / Model Serving (~30%)
SERP mais fraca do espaço ("what is ml infrastructure": ranqueiam DA 26-42; AI Overview presente). Inclui o subtema carreira ("ml infrastructure engineer", 110/mês, SD 29 — atrai pares e recrutadores, a audiência-fim).

### C3 — Monitoring / Drift / Fraud ML (~20%)
Heads difíceis ("model monitoring" SD 72, "machine learning fraud detection" SD 59), cauda operacional aberta (SD 5-7). É onde a estatística do MBA entra em produção (drift = estatística aplicada) e onde mora a carta "modelos adversariais". Entrada pela experiência, não pela keyword.

### C4 — Jornada SWE→ML/Data (~10%)
Pilar 2 do POSITIONING: learning in public do MBA, transição de carreira. **Sem meta de ranking** — mede-se por engajamento de distribuição (LinkedIn/X), não por posição.

## Banco de keywords (Ubersuggest, US/en, coletado 2026-07-02)

### Tier ENTRADA (DA atual já compete — SD ≤ 15; alvos dos suportes via /seo-writer)
| Keyword | Vol/mês | SD | Cluster |
|---|---|---|---|
| feature store vs data warehouse | 10 | 10 | C1 |
| online vs offline feature store | 10 | 5 | C1 |
| real time feature store | 10 | 5 | C1 |
| feature store example | 20 | 13 | C1 |
| feature store pricing | 20 | 13 | C1 |
| feature store gcp | 20 | 13 | C1 |
| what is feature store in machine learning | 20 | 10 | C1 |
| offline feature store | 10 | 13 | C1 |
| model serving vs inference | 10 | 6 | C2 |
| machine learning model serving patterns and best practices | 10 | 10 | C2 |
| ml model monitoring metrics | 20 | 7 | C3 |
| model monitoring in production | 10 | 5 | C3 |
| machine learning model monitoring in production | 10 | 5 | C3 |

### Tier INTERMEDIÁRIO (DA ~15+; semestre 2)
| Keyword | Vol/mês | SD | Cluster |
|---|---|---|---|
| what is ml infrastructure | 50 | 23 | C2 |
| what is feature store | 50 | 27 | C1 |
| open source feature store | 30 | 37 | C1 |
| feature store machine learning | 40 | 30 | C1 |
| ml infrastructure engineer | 110 | 29 | C2 |
| model monitoring tools | 70 | 34 | C3 |
| mlflow model serving | 40 | 26 | C2 |
| what is model serving | 50 | 33 | C2 |

### Tier HEAD (DA ~30+; ano 2 — não atacar antes)
| Keyword | Vol/mês | SD | Cluster |
|---|---|---|---|
| feature store | 1.000 | 33 | C1 |
| ml infrastructure | 390 | 31 | C2 |
| feast feature store | 590 | 43 | C1 |
| databricks feature store | 390 | 24 | C1 |
| what is a feature store | 210 | 52 | C1 |
| model serving | 170 | 43 | C2 |
| machine learning fraud detection | 720 | 59 | C3 |
| model monitoring | 210 | 72 | C3 |

### Exclusões deliberadas (não atacar — ver POSITIONING/anti-posicionamento)
- `feature engineering` (2.400/mês, SD 38) — prática DS, fora do escopo.
- `data engineering` (22.200/mês, SD 70) — oceano vermelho.
- `statistics for machine learning` (320/mês, SD 59) e cauda "pdf/book/course" — intenção didática, sem jogo para blog pessoal.
- `jvm stack vs heap` e afins (10/mês) — commodity de AI Overview.

## Cadência e produção

- **1 âncora/mês** — sessão guiada com o dono (war story anonimizada, benchmark de lab próprio, deep-dive com diagramas). QA via `/seo-auditor`. Distribuição obrigatória: LinkedIn + X; HN quando o formato couber (benchmarks/custos têm o melhor perfil).
- **2-3 suportes/mês** — `/seo-writer` contra o tier ENTRADA, sempre linkando para a âncora do cluster.
- Ideias de âncora prioritárias (lacunas sem dono, ver MARKET_RESEARCH): serving de features para anti-fraude em tempo real (p99, point-in-time correctness); custos reais de serving de ML; "you don't need a feature store (yet)"; migração GKE nodepool → Workload Identity (war story já vivida); JVM tuning para serving de baixa latência.

## Quick wins (trimestre 1)

1. **Branded search**: schema Person no Hugo, about page otimizada e consistente com LinkedIn, links dofollow dos perfis (LinkedIn, GitHub, X) para o domínio.
2. **Reotimizar o post da JVM** para o contexto ML serving (título/ângulo: JVM memory management *for low-latency model serving*) — sai de commodity para o C2.
3. `llms.txt` + article schema em todos os posts.
4. Google Search Console: conectar snapshot mensal em `.docs/seo/gsc-snapshots/` (rotina do `/seo-cluster-planner`).

## Estratégia de backlinks (médio prazo)

Backlink vem de âncora citável, não de outreach frio: benchmarks com dados originais e breakdowns de custo são os formatos que featurestore.org, newsletters de MLOps e agregadores citam. Meta: 6→30+ refDomains em 12 meses. Sem compra de links, sem guest post de farm.

## Riscos registrados

| Risco | Sinal | Mitigação |
|---|---|---|
| **Cadência zero (histórico)** | 2 meses sem âncora | Replanejar capacidade com o estrategista — não pivotar tese |
| Pivô impulsivo antes da maturação | Ansiedade com tráfego baixo < mês 6 | Expectativa registrada no baseline; KPI é processo + DA |
| AI Overviews comendo cliques definicionais | CTR baixo em "what is X" | Definicional é suporte/autoridade; âncoras carregam o valor |
| Conteúdo de esteira diluindo a marca | Suporte lido como AI-slop por par sênior | Gates do seo-writer + revisão do dono; âncora nunca sai de esteira |
| Exposição do empregador | Qualquer dado além do teto LinkedIn | Regra de anonimização no POSITIONING |

## Histórico de decisões

- **2026-07-02 (fundação — decisão do dono):** criação da estratégia. Tese ML Infrastructure em inglês p/ mercado exterior; pilares 70/30; cadência 1 âncora + 2-3 suportes; pilar estatística rebaixado de aposta SEO para combustível do P1 (dado: "statistics for data engineering" volume nulo); exclusão de feature engineering/data engineering/tutoriais genéricos; expectativa de tráfego modesto registrada. Ressalva do estrategista: risco dominante é cadência, não estratégia.
