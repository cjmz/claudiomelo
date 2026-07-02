# POSITIONING — claudiomelo.com

**Última atualização:** 2026-07-02
**Dono/decisor:** Claudio Melo

> Documento âncora da estratégia. Mudanças aqui são decisões macro (via `/seo-estrategista`), nunca táticas.

---

## Tese

**Claudio Melo é o engenheiro que constrói Machine Learning Infrastructure em escala — e está adicionando fundamento estatístico por cima.**

A ponte entre software engineering de alta performance (Java/Spring, GKE, Terraform, BigTable, 4.000+ RPS, SLO 100ms) e o mundo dos dados/ML, contada **em inglês** para o mercado internacional (EUA, Canadá, Europa).

O site é um ativo de **carreira** (prioridade #1 do dono), não um canal comercial. O modelo de referência é o de engenheiros que construíram marca pessoal escrevendo a partir de experiência de produção enquanto trabalhavam em big techs — Eugene Yan (Amazon → Anthropic), Lak Lakshmanan (Google Cloud). Ver `MARKET_RESEARCH.md`.

## Objetivo primário (decisão do dono, 2026-07-02)

Alavancar a carreira como engenheiro de **ML Infrastructure / ML Platform**, com horizonte de oportunidades no exterior (US/CA/EU). Não é canal de vendas da Stagency nem da Demeit.

**Racional do enquadramento "ML Infrastructure" (não "data engineer genérico"):**
- "data engineering" tem SD 70 e uma multidão estabelecida (dbt, Databricks, criadores com anos de vantagem).
- O nicho ML infra/feature stores tem SD 5-33, SERPs sem vozes individuais, CPC $10-36 (audiência pequena e valiosa) — e o Claudio tem experiência primária real operando isso (feature serving para anti-fraude no Mercado Livre).
- O MBA em Data Analytics (até 12/2027) **completa** esse perfil, não o substitui.

## ICP / Audiência-alvo

1. **Hiring managers e engenheiros sêniores** de times de ML Platform/Infra em empresas US/EU/CA — a audiência que abre portas.
2. **Pares**: engenheiros backend/plataforma migrando para ML infra (a keyword "ml infrastructure engineer", 110/mês, SD 29, mostra essa busca ativa).
3. Secundária: recrutadores técnicos verificando o nome (branded search).

Idioma: **inglês**. O GSC confirma: 172 das ~364 impressões históricas vêm de US+CA+UK; Brasil tem posição média 29 e zero cliques.

## Pilares e pesos

| Pilar | Peso | O que é | Papel |
|---|---|---|---|
| **P1 — ML Infrastructure na prática** | ~70% | Feature stores, feature serving de baixa latência, model serving, monitoring/drift, capacity planning, JVM/performance *aplicada a serving de ML*, GKE/Terraform/BigTable. Estatística aplicada a produção (drift, métricas) **embutida aqui** | O jogo de SEO/GEO. Entrada pela cauda SD 5-15 (ver SEO_STRATEGY) |
| **P2 — Jornada SWE → ML/Data, learning in public** | ~30% | O MBA de Data Analytics como fábrica de pauta, transição de carreira, bastidores de estudo | Marca e distribuição (LinkedIn/X). **Sem meta de ranking** — decisão baseada em dados (ver nota abaixo) |

**Nota do realinhamento 2026-07-02 (decisão do dono):** o pilar de estatística foi rebaixado de aposta SEO para combustível do P1 + conteúdo de distribuição. Dados: "statistics for data engineering" tem volume nulo; "statistics for machine learning" (320/mês) tem SD 59 com cauda inteira de intenção "pdf/book/course" (terreno de material didático, não de blog pessoal DA 2). O ponto de fusão entre estatística e P1 é monitoring/drift — estatística operando em produção.

## Formato editorial (decisão do dono, 2026-07-02)

- **1 peça-âncora/mês**: long-form (2.000+ palavras), experiência primária, diagramas originais, escrita guiada pelo dono (o padrão do post da JVM). É o que se distribui em HN/LinkedIn/X. **Não sai de esteira automatizada.**
- **2-3 peças de suporte/mês** via `/seo-writer`: conteúdo de cluster (definições, comparativos, how-tos da cauda longa) que constrói autoridade topical e linka para as âncoras.
- Racional: no nicho, vence long-form definitivo + distribuição, não volume (padrão comum a Chip Huyen, Eugene Yan, Vicki Boykis, Hamel Husain — ver MARKET_RESEARCH). A evidência interna também sustenta: a esteira de 8 posts/mês da Stagency gera tráfego mas não converteu o objetivo de negócio.

## Anti-posicionamento (o que este site NÃO é)

- **Não** é vitrine da Stagency nem da Demeit — nada de CTA comercial, `productSection.enabled: false`.
- **Não** disputa "feature engineering" (2.400/mês, SD 38) — é prática de data science (encoding, scaling), terreno de Kaggle/TDS/material didático, e não é o que o Claudio faz. O alvo é a **infraestrutura** (feature store/serving).
- **Não** publica tutoriais genéricos de Java/JVM ("what is stack vs heap") — commodity respondida por AI Overviews; JVM só entra aplicada a serving de ML.
- **Não** cobre mídia paga/growth marketing (caminho que o dono decidiu não seguir).
- **Não** escreve em português (conteúdo; docs internos são pt-BR).

## Regra de anonimização (decisão do dono, 2026-07-02)

- **Teto de exposição = o que já está público no LinkedIn do dono** (4.000+ RPS, SLO 100ms, BigTable, GKE→PaaS, capacity p/ 50k RPS). Nada de arquitetura interna identificável, números não publicados ou detalhes de anti-fraude que exponham o empregador.
- Acima do teto, a rota é **benchmark reproduzível em lab próprio** (ex.: latência BigTable vs alternativas em ambiente sintético, experimentos de GC tuning sob carga) — que também é o formato com melhor perfil de backlink/citação.

## GEO (LLMs e AI Overviews)

- Queries definicionais do nicho **já têm AI Overview** ("what is ml infrastructure") — conteúdo definicional é meio (autoridade topical + citação), não fim (clique).
- O que LLMs citam: dados originais, benchmarks, definições cristalinas com estrutura clara. As âncoras com números próprios são a aposta GEO.
- Infra técnica: schema Person + article schema, `llms.txt`, about page consistente com LinkedIn/GitHub.

## Ressalvas registradas do estrategista

1. **Risco #1 é cadência, não estratégia**: histórico de 2 posts em 18 meses. Se a âncora mensal falhar por 2 meses seguidos, tratar como sinal de replanejamento de capacidade (não de pivô de tese).
2. A onda quente 2025-2026 do nicho é **evals/LLMs**; a carta guardada é a interseção com a experiência do dono: monitoring/avaliação de modelos **adversariais** (fraude). Não surfar hype fora da experiência própria.
