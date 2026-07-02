# Auditoria Técnica + SEO — claudiomelo.com

**Data:** 2026-07-02
**Escopo:** Diagnóstico (sem correção automática)
**Stack:** Hugo 0.151.0 + tema PaperMod (submodule) · deploy Netlify · GA4 (`G-NHFJSXSGGR`)
**Fontes:** código local + Ubersuggest (tier2) + PageSpeed + site audit (crawl 22 págs)

---

## ⚙️ Auditoria FUNCIONAL — verificada em produção (2026-07-02)

Foco solicitado: garantir que tudo funciona (analytics, eventos, formulário, integrações).
Testes reais via `curl` contra `claudiomelo.com` + build local (Hugo 0.151.0, = produção).

### 🔧 PROBLEMA-RAIZ: `public/` (build artifact) versionado no git

Não há `.gitignore`. O diretório `public/` — que é o **output do build do Hugo** — está commitado
(**94 arquivos, 4,6 MB**). A Netlify builda com `hugo --minify` **sem `--cleanDestinationDir`**,
então ao fazer checkout do repo (que já traz `public/`) e rodar o build por cima, **arquivos órfãos
sobrevivem**. Consequências verificadas:

- **Divergência source × produção:** o que está no ar ≠ o que está em `static/`.
- **`trends.png` só existe em `public/` commitado, NÃO em `static/`.** Renderiza em produção
  (HTTP 200) só por acidente → **some num build limpo**.
- **Lixo público (HTTP 200 confirmado em produção):**
  - `…/Unconfirmed 203376.crdownload` — download **incompleto do Chrome**, exposto publicamente.
  - `…/ml-lifecile` — duplicata sem extensão de `ml-lifecile.jpg`.
  - `…/diagnos.pdf` — "Oracle JRockit JVM Diagnostics Guide" (2,95 MB), não usado por post nenhum.

### O que está QUEBRADO (confirmado ao vivo)

| Item | Status verificado | Detalhe |
|---|---|---|
| Favicon `.ico` | **HTTP 404** | Referenciado em `extend_head.html`, arquivo não existe em `static/` |
| Favicon `.svg` | **HTTP 404** | idem |
| `apple-touch-icon.png` | **HTTP 404** | idem |
| OG image `/images/og-image.png` | **HTTP 404** | `hugo.toml` aponta p/ ela → link compartilhado sai **sem preview** |
| `trends.png` (post statistics) | **200 hoje, frágil** | Só existe em `public/` commitado; falta em `static/`. Path com barra dupla `//` (feio, mas funciona) |
| Eventos de analytics | **inexistentes** | Só `pageview` automático do GA4. Share buttons, code-copy, cliques externos, uso da busca → **não medidos** |
| Formulário de contato | **não existe** | Contato só via links (LinkedIn/GitHub) + `mailto`. Nenhum `<form>` nem Netlify Forms |
| Search Console | **não conectado** | GA4 existe, GSC não (via Ubersuggest) |

### ⚠️ CORREÇÃO ao meu diagnóstico inicial (eu errei — verifiquei depois)

- **As 7 imagens do post JVM NÃO estão quebradas.** São **data URIs base64 embutidos**
  (`[image1]: <data:image/png;base64,…>` no fim do arquivo) e **renderizam em produção**
  (confirmado por screenshot do usuário). Meu grep inicial estourou 240 KB *por causa* do base64,
  e o preview de 2 KB cortou antes das definições — eu classifiquei como órfãs sem confirmar.
  - Ponto legítimo remanescente (performance/manutenção, **não bug**): o markdown pesa **252 KB**
    por causa do base64 inline — imagens não são cacheáveis nem lazy-loaded. Migrar para arquivos
    em `static/` é uma otimização, opcional.

### O que FUNCIONA (confirmado)

- Home `HTTP 200`, **0,56 s**, sem redirect chain, SSL válido.
- Build limpo: **0 warnings** de link/ref interno. Hugo local 0.151.0 = produção.
- Busca FuseJS OK (`index.json` 17 KB gerado, página `/search/` existe).
- Sitemap (22 URLs), `robots.txt`, RSS gerados corretamente.
- GA4 `gtag` presente em **todas** as páginas (home + posts) → pageview funciona.
- Links externos dos posts OK (towardsdatascience 403 e LinkedIn 999 são anti-bot, não links mortos; YouTube e GitHub = 200).
- Headers de segurança (X-Frame-Options, nosniff, Referrer-Policy) + cache imutável de assets.

### Ajuste ao diagnóstico anterior

- **`claudiomelo.dev` NÃO resolve mais** (`Could not resolve host`). Logo o redirect 301
  `.dev`→`.com` que eu havia sugerido é **desnecessário** — não há domínio antigo no ar.
- O redirect `/pt/* → 404` no `netlify.toml` é inofensivo hoje (site é só EN), mas é uma regra
  estranha; baixa prioridade.

### Decisões técnicas que preciso de você (bloqueiam o fix "bem feito")

1. **Imagens do post JVM (7):** você tem os diagramas originais (stack/heap/GC)? Opções:
   recrio os diagramas · você me manda os arquivos · removo os placeholders por ora.
2. **Formulário de contato:** criar um funcional (via **Netlify Forms**, casa com o deploy) ou
   manter só os links?
3. **Favicon + OG image:** eu gero assets básicos (ex.: monograma "CM") ou você fornece a arte?

---

## 0. Retrato honesto (leia antes de tudo)

O blog **não é antigo em conteúdo** — só o **domínio** pode ter história. O conteúdo atual
tem **2 posts** (out/2025) e foi migrado de `claudiomelo.dev` → `claudiomelo.com` em 22/out/2025.

Números externos (Ubersuggest, jul/2026):

| Métrica | Valor | Leitura |
|---|---|---|
| Domain Authority | **2** | Praticamente zero autoridade |
| Tráfego orgânico | **0** | Nenhuma visita de busca |
| Keywords rankeando | **0** | Não aparece para nada |
| Backlinks | **6** (5 ref. domains, todos nofollow) | Sem link equity |
| Conectado ao Search Console | **Não** | Voando às cegas |
| Conectado ao GA (via Ubersuggest) | **Não** | (GA4 existe no site, mas não plugado ao painel SEO) |

**Conclusão:** não existe "potencial adormecido de domínio antigo" a ser explorado. O ativo real
é o **nome/portfólio pessoal**. A estratégia de carreira certa aqui é **autoridade + prova de
competência técnica**, não caça a tráfego de volume. Ver seção 8.

---

## 1. CRÍTICO — quebra a experiência e a credibilidade

### 1.1 — 8 imagens quebradas nos 2 posts (o pior problema do blog)
- **`content/posts/jvm-deep-dive-stack-heap/index.md`** (o melhor post, 2145 palavras):
  linhas 30, 44, 59, 65, 69, 104, 134 → `![][image1]` … `![][image7]`.
  São **referências de imagem Markdown órfãs** (sintaxe `![][ref]` sem a definição
  `[ref]: url`), tipicamente resultado de colar do Google Docs. Renderizam como imagem sem `src`.
- **`content/posts/statistics-foundation/index.md`** linha 31 →
  `![...](/images/statistics-foundation//trends.png)`: barra dupla no path **e** o arquivo
  `trends.png` **não existe** no repo (só existem `human-brain.png` e `ml-lifecile.jpg`).
- Efeito: o post-âncora do blog está com 7 imagens quebradas. Para quem chega por um link
  (recrutador, engenheiro), a primeira impressão é "abandonado/quebrado".

### 1.2 — Google Search Console não conectado
- GA4 está instalado (`extend_head.html`, `G-NHFJSXSGGR`), mas o Search Console não.
- Sem GSC não há dados de impressão/posição/query reais — impossível medir SEO com fato.

---

## 2. ALTO — trava crescimento

### 2.1 — Conteúdo raso e escasso
- **2 posts**. `statistics-foundation` tem **519 palavras** (thin content).
- Site audit: **15 páginas** flag `content_count_words` (impacto alto). A maioria são páginas de
  taxonomia (tags/categorias/series) do PaperMod, quase vazias, geradas a partir de só 2 posts.

### 2.2 — Mobile lento (Core Web Vitals)
- **Mobile: LCP 4.4s** (ideal < 2.5s), FCP 3.5s, TTI 4.4s. Desktop OK (LCP 1.1s, CLS 0).
- Oportunidades PageSpeed: **Redirects −630ms** e **Unused JavaScript −600ms (65 KB)**.
- Causa provável do render-block: Google Fonts (Inter + JetBrains Mono) carregadas via CDN
  no `<head>` (`extend_head.html`) + cadeia de redirect de domínio.

### 2.3 — Ruído de indexação (17 meta desc duplicadas + títulos)
- Site audit: **17 páginas** com `duplicate_meta_descriptions`, **2** `have_title_duplicates`,
  **2** `title_long` (> 60 chars — os títulos dos posts são muito longos e cortam no SERP).
- As páginas de listagem herdam a mesma description global → Google vê conteúdo repetido.

### 2.4 — Inglês não-nativo sem revisão
- O blog é em inglês (`languageCode = 'en'`) mas tem construções não-idiomáticas
  ("this blog purpose is to share", "I've never evolved with a language", "GC Minor running slowly").
- Num blog técnico em inglês competindo globalmente, isso reduz a qualidade percebida.

---

## 3. MÉDIO — higiene e estratégia

- **3.1 Sem redirect 301 `claudiomelo.dev` → `.com`.** O `netlify.toml` nunca recebeu o redirect
  (era "opcional" na revisão de out/2025). Se o `.dev` ainda resolve, é conteúdo duplicado e
  perda de qualquer equity antigo.
- **3.2 Redirect `/pt/* → 404`** (`netlify.toml`): qualquer URL em português antiga é mandada
  para 404 em vez de redirecionada. Mata conteúdo PT que porventura esteja indexado.
- **3.3 GA4 hardcoded** no `extend_head.html` enquanto `googleAnalytics = ""` no `hugo.toml`.
  Funciona, mas é inconsistente e ignora o mecanismo nativo do PaperMod.
- **3.4 `human-brain.png`** existe no repo mas não é referenciada em nenhum post (imagem morta).
- **3.5 Data inconsistente:** `statistics-foundation` tem `date: 2025-01-22` mas foi commitado
  depois; publicar com data retroativa pode confundir ordenação/percepção de frescor.

---

## 4. Potencial de keywords (realidade do nicho)

- `jvm stack and heap` → **volume 10/mês**, SEO difficulty 5 (fácil, mas irrelevante em volume).
- Os temas atuais (JVM interno, transição p/ data eng) são **baixo volume / alta qualificação**.
- Implicação: o blog **não vai virar máquina de tráfego** com esses temas. Ele pode virar
  **prova de senioridade** para um público pequeno e valioso (pares, recrutadores, entrevistas).

---

## 5. O que está BOM (não mexer)

- Hugo + Netlify com `--minify`, headers de segurança (X-Frame-Options, nosniff, Referrer-Policy).
- Cache imutável de assets (`max-age=31536000`).
- Sitemap e RSS gerados corretamente. SSL válido. Desktop rápido.
- Estrutura de front matter completa (ToC, reading time, tags/categorias/series).

---

## 6. Priorização (esforço × impacto)

| # | Item | Impacto | Esforço | Faixa |
|---|---|---|---|---|
| 1 | Corrigir 8 imagens quebradas | Alto | Baixo | **Fazer já** |
| 2 | Conectar Search Console + sitemap | Alto | Baixo | **Fazer já** |
| 3 | Redirect 301 `.dev`→`.com` + revisar `/pt/*` | Médio | Baixo | **Fazer já** |
| 4 | Meta descriptions únicas + encurtar títulos | Alto | Médio | Semana 1 |
| 5 | Fonts self-hosted / `font-display` (mobile LCP) | Médio | Médio | Semana 1 |
| 6 | Revisão de inglês dos 2 posts | Alto | Médio | Semana 1 |
| 7 | Cadência de conteúdo (ver seção 8) | Alto | Alto | Contínuo |

---

## 7. Correções rápidas propostas (escopo mínimo)

1. **Imagens JVM:** substituir cada `![][imageN]` por imagens reais (recriar diagramas de
   stack/heap/GC) OU remover os placeholders. Diagramas próprios também viram conteúdo linkável.
2. **`trends.png`:** corrigir o path (barra dupla) e adicionar o arquivo, ou remover a linha.
3. **Redirect de domínio** em `netlify.toml`:
   ```toml
   [[redirects]]
     from = "https://claudiomelo.dev/*"
     to   = "https://claudiomelo.com/:splat"
     status = 301
     force = true
   ```
4. **Search Console:** verificar propriedade `claudiomelo.com`, submeter `sitemap.xml`.

---

## 8. Estratégia de carreira (o "para quê")

O blog não compete por tráfego — compete por **reputação técnica**. Plano sugerido:

1. **Posicionamento:** escolher 1 eixo forte (ex.: "performance de JVM/sistemas em produção" OU
   "transição eng. software → eng. dados") e ser consistente. Hoje está dividido.
2. **Conteúdo de senioridade:** posts que só quem viveu produção escreve (o caso real do
   restart por GC Minor no post JVM é ouro — aprofundar com métricas do Datadog, before/after).
3. **Distribuição > SEO:** com DA 2, o tráfego virá de LinkedIn, X, dev.to (canonical), Hacker
   News, Reddit (r/java, r/dataengineering). SEO é o jogo longo; distribuição é o curto.
4. **Cadência:** 1 post sólido a cada 2–3 semanas > 10 posts rasos. Consistência gera autoridade.
5. **Prova social:** links do blog na bio do LinkedIn/GitHub/X; cada post vira também um
   thread/artigo. Isso alimenta o backlink profile (hoje 6 nofollow).
6. **Métrica de sucesso realista:** não "tráfego", mas "peças citáveis em entrevista/networking"
   e crescimento de referral + posição para 5–10 keywords de nicho em 90 dias.

---

## 9. Próximos passos oferecidos

- **(A)** Abrir um `bugfix/*` só para as imagens quebradas + redirect (fix real, PR para `develop`).
- **(B)** Minerar keywords de nicho com volume real (o `keyword_suggestions` retornou 6k linhas —
  dá para extrair um mapa de temas com um subagente) e montar calendário editorial.
- **(C)** Transformar esta auditoria em relatório visual (Artifact) para acompanhamento.
