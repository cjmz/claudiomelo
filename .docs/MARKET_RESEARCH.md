# MARKET_RESEARCH — claudiomelo.com

**Última atualização:** 2026-07-02
**Método:** varredura web (2026-07-02) + Ubersuggest (US/en). Tudo com fonte; o que não foi confirmado está marcado.

---

## 1. Benchmark: marcas pessoais vencedoras em ML Infrastructure/MLOps

| Pessoa | Site | Posicionamento | Cadência | O que destravou a marca | Empregador na fase de crescimento |
|---|---|---|---|---|---|
| Chip Huyen | huyenchip.com | Referência em ML/AI systems em produção | ~3-5 posts/ano, definitivos | Curso CS 329S Stanford → livro *Designing ML Systems* (O'Reilly) | NVIDIA → Snorkel → Netflix |
| Eugene Yan | eugeneyan.com | "Ghost knowledge" de ML em produção (RecSys, evals) | ~10-11/ano, o mais consistente; ativo em 2026 | Repo `applied-ml` (GitHub) + "Patterns for LLM Systems" (2023) | **Amazon** (blog pessoal em paralelo) → Anthropic |
| Vicki Boykis | vickiboykis.com | Voz "normcore": ceticismo + profundidade | Alta, ativa em 2025 | Newsletter Normcore Tech + e-book "What are embeddings?" (HN front page) | Automattic, Duo, Mozilla.ai |
| Hamel Husain | hamel.dev | "O cara de evals" | Ativa 2025-2026 | Post "Your AI Product Needs Evals" (2024) → curso Maven + O'Reilly | Airbnb → GitHub → consultoria própria |
| Shreya Shankar | sh-reya.com | Ponte academia↔indústria em MLOps | Blog esparso; papers + curso | Paper "Operationalizing ML: An Interview Study" (2022) | Google Brain → Viaduct → PhD Berkeley |
| Jeremy Jordan | jeremyjordan.me | Explicações canônicas atemporais ("living documents") | Baixa; evergreen | "Effective testing for ML systems" (ranqueia há anos) | NVIDIA |
| Maria Vechtomova | marvelousmlops.io | MLOps prático, modelo LinkedIn-first | Semanal | 65k+ seguidores LinkedIn + Substack + O'Reilly | Tech Lead na Holanda |

Fontes: huyenchip.com/blog · eugeneyan.com/writing · github.com/eugeneyan/applied-ml · vickiboykis.com · hamel.dev/blog/posts/evals · sh-reya.com · arxiv.org/abs/2209.09125 · jeremyjordan.me · marvelousmlops.io
Não confirmado: posts de Chip Huyen em 2026; atividade do blog da Shreya em 2025-2026.

### Resposta à pergunta "engenheiros de big tech escrevem publicamente?"
Sim, mas o padrão dominante é o blog corporativo (Uber Michelangelo definiu a categoria em 2017; Google escreve via Cloud Architecture Center e papers). As exceções em canal próprio *enquanto empregados* — **Eugene Yan na Amazon** e **Lak Lakshmanan no Google Cloud** (lakshmanok.medium.com, livro *ML Design Patterns*) — são exatamente o modelo do Claudio no Meli: padrões e lições, sem segredos internos. Mike Del Balso (Uber) só construiu voz própria depois de fundar a Tecton.

### Padrões comuns dos vencedores
1. Long-form definitivo (2-8k palavras) > frequência — o post vira *a* referência do tema.
2. Domínio próprio, design espartano (nada de Medium como casa).
3. Diagramas originais de arquitetura, re-compartilhados e citados separadamente.
4. Autoridade vem de experiência de produção real (war stories, "ghost knowledge"), não de tutoriais reproduzidos.
5. Curadoria/agregação como alavanca de descoberta (applied-ml, interview study).
6. Funil: posts → HN/X/LinkedIn → livro/curso (O'Reilly, Maven).
7. **Distribuição via HN + X + LinkedIn + newsletter; SEO chega depois, como consequência de backlinks.**
8. Migraram para o tema quente (evals/LLMs em 2023-2025) sem abandonar a base.

## 2. Quem ocupa as SERPs (2026-07-02)

**"feature store"** (1.000/mês, SD 33): Databricks (#1, DA 77), IBM (#3, DA 93), Reddit (#4), Microsoft Learn (#5, DA 98), featurestore.org (#6, DA 31 — mantido pela Hopsworks), Feast (#8, DA 40), **chalk.ai (#9, DA 26)**, qwak (#12, DA 33). **Zero vozes individuais.** Sites DA 26-33 na primeira página ⇒ alcançável com DA ~25-30.

**"what is ml infrastructure"** (50/mês, SD 23): **AI Overview no topo**; depois Reddit, iguazio (DA 42), everpuredata (55), sei.cmu.edu (91), northflank (35), openlayer (26). SERP fraca/fragmentada — a mais aberta do espaço.

**"mlops best practices"**: ml-ops.org (INNOQ), Google Cloud Architecture Center, Databricks, AWS — conteúdo checklist sem experiência operacional real.

**Engineering blogs que definem a categoria** (fonte citada por todos): Uber Michelangelo, Netflix Tech Blog, DoorDash Engineering (feature store Gigascale/Redis), Google Cloud Architecture Center.

## 3. Lacunas / oportunidades (ângulos sem dono)

1. **Feature serving para anti-fraude em tempo real** — o caso de uso citado em todo pitch de vendor, sem ninguém com experiência operacional real escrevendo (p99, point-in-time correctness, custo de serving online).
2. **Custos reais em dólares** de rodar infra de ML — vendors não podem publicar, big techs não divulgam; perfil clássico de HN front page.
3. **"ML infra fora do Vale"** — engenharia com orçamento/equipe restritos (perspectiva LatAm); a SERP de "ml infrastructure" não tem dono.
4. **Monitoring/avaliação de modelos adversariais** (fraude: o adversário se adapta) — interseção entre a onda de evals (2025-2026) e a experiência do dono. Nicho defensável.
5. **Contra-conteúdo**: "you don't need a feature store (yet)" — trade-offs honestos que nenhum vendor do item 2 pode publicar; formato que fez Vicki/Hamel crescerem.

## 4. Dados Ubersuggest de suporte (US/en, 2026-07-02)

- claudiomelo.com: DA 2, 6 backlinks (1 dofollow), 0 keywords orgânicas.
- Termos validados e exclusões: ver banco de keywords e exclusões em `SEO_STRATEGY.md` (fonte única, não duplicar aqui).
- Sinais de valor do nicho: CPCs $10-36 em toda a cauda de feature store/serving/monitoring — audiência pequena e comercialmente valiosa.
- "statistics for data engineering": volume nulo; "statistics for machine learning" 320/mês SD 59 com cauda "pdf/book/course" ⇒ fundamentou o rebaixamento do pilar estatística (ver POSITIONING, nota 2026-07-02).
- "feature engineering" 2.400/mês SD 38 ⇒ excluída (prática DS, fora do posicionamento).
