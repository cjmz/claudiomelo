# 📘 Guia de Uso - Personalizações do Blog

Este documento explica como usar as personalizações implementadas no blog.

## 🎨 Shortcodes Disponíveis

### 1. Alert Box

Use para destacar informações importantes:

```markdown
{{< alert type="info" >}}
**Apache Spark** usa lazy evaluation por padrão. Isso significa que transformações não são executadas imediatamente.
{{< /alert >}}

{{< alert type="warning" >}}
⚠️ **Atenção:** Usar `collect()` em DataFrames grandes pode causar **OutOfMemory**.
{{< /alert >}}

{{< alert type="tip" >}}
💡 **Dica:** Use `cache()` apenas quando for reutilizar o DataFrame múltiplas vezes.
{{< /alert >}}

{{< alert type="spark" >}}
🔥 Configuração recomendada para jobs Spark em produção...
{{< /alert >}}
```

#### Tipos de Alert
- `info` - Informações gerais (cyan)
- `warning` - Avisos e cuidados (laranja)
- `tip` - Dicas e boas práticas (verde)
- `danger` - Perigos e erros críticos (vermelho)
- `spark` - Específico para Apache Spark (laranja Spark)

### 2. Code Snippet com Título

Use para blocos de código com contexto:

```markdown
{{< code lang="python" title="spark_optimization.py" >}}
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("OptimizedJob") \
    .config("spark.sql.adaptive.enabled", "true") \
    .config("spark.sql.adaptive.coalescePartitions.enabled", "true") \
    .getOrCreate()

df = spark.read.parquet("s3://bucket/data/")
result = df.filter(df.status == "active").groupBy("category").count()
{{< /code >}}
```

#### Linguagens Suportadas
- `python`
- `sql`
- `bash`
- `scala`
- `java`
- `yaml`
- `json`
- `toml`

## 🎯 Templates de Post

### Criar Novo Post

```bash
~/bin/hugo new posts/otimizacao-spark-shuffle.md
```

O template já vem com a estrutura completa:

```markdown
---
title: "Otimização Spark Shuffle"
date: 2025-10-13T10:00:00-03:00
draft: true
tags: ["spark", "performance", "data-engineering"]
categories: ["tutorial", "performance"]
author: "Claudio Melo"
description: "Como otimizar operações de shuffle no Apache Spark para melhorar performance em até 10x"
ShowToc: true
---

## Introdução
## Conceitos Fundamentais
## Solução
## Exemplos Práticos
## Considerações
## Conclusão
## Referências
```

### Categorias Recomendadas

- `tutorial` - Guias passo a passo
- `conceitos` - Explicações teóricas
- `arquitetura` - Design patterns
- `performance` - Otimizações
- `boas-praticas` - Recomendações
- `case-study` - Estudos de caso

### Tags Sugeridas

**Apache Spark:**
- `spark`, `pyspark`, `spark-sql`, `spark-streaming`
- `performance`, `optimization`, `shuffle`, `caching`

**Data Lakes:**
- `data-lake`, `delta-lake`, `iceberg`, `hudi`
- `parquet`, `orc`, `avro`

**Cloud:**
- `aws`, `s3`, `emr`, `glue`
- `azure`, `databricks`
- `gcp`, `bigquery`

**Arquitetura:**
- `data-mesh`, `data-fabric`, `lakehouse`
- `etl`, `elt`, `pipeline`

**Python:**
- `python`, `pandas`, `polars`
- `airflow`, `prefect`

## 🎨 Customizações CSS

### Cores Principais

```css
--accent-color: #00d9ff;      /* Cyan - cor principal */
--spark-orange: #e25a1c;      /* Apache Spark */
--data-green: #00c853;        /* Sucesso/dados */
--warning-amber: #ffa726;     /* Avisos */
```

### Aplicar Destaque Especial

Para destacar tecnologias específicas, use **negrito**:

```markdown
Neste tutorial vamos usar **Apache Spark**, **PySpark** e **Delta Lake**.
```

No CSS customizado, palavras em negrito ficam com a cor accent automaticamente.

## 📝 Exemplos de Posts

### Exemplo 1: Tutorial Técnico

```markdown
---
title: "Como Otimizar Joins no Apache Spark"
date: 2025-10-13T14:00:00-03:00
draft: false
tags: ["spark", "performance", "joins", "data-engineering"]
categories: ["tutorial", "performance"]
description: "Guia completo de otimização de joins no Spark com broadcast, bucketing e estatísticas"
ShowToc: true
---

## Introdução

Joins são operações custosas no Spark. Vamos explorar técnicas para otimizá-los.

{{< alert type="spark" >}}
🔥 **Performance Tip:** Joins podem causar shuffle massivo de dados se não otimizados.
{{< /alert >}}

## Conceitos Fundamentais

### Tipos de Join no Spark

- **Broadcast Join** - Para datasets pequenos (<10MB)
- **Sort-Merge Join** - Join padrão para grandes datasets
- **Shuffle Hash Join** - Quando uma tabela é pequena mas não cabe em broadcast

## Solução

### 1. Broadcast Join

{{< code lang="python" title="broadcast_join.py" >}}
from pyspark.sql.functions import broadcast

# Força broadcast da tabela menor
result = large_df.join(
    broadcast(small_df),
    "key",
    "inner"
)
{{< /code >}}

{{< alert type="tip" >}}
💡 Use broadcast apenas para DataFrames < 10MB em ambiente de produção.
{{< /alert >}}

## Exemplos Práticos

### Comparação de Performance

| Técnica | Tempo | Shuffle |
|---------|-------|---------|
| Join Normal | 45s | 2.5GB |
| Broadcast Join | 8s | 0GB |
| Bucketed Join | 12s | 500MB |

## Considerações

### Quando Usar Cada Técnica

- ✅ **Broadcast:** Tabela < 10MB, join frequente
- ✅ **Bucketing:** Tabelas grandes, joins repetidos
- ⚠️ **Sort-Merge:** Padrão, mas pode ser lento

## Conclusão

Escolher a estratégia certa de join pode reduzir o tempo em até 80%.

## Referências

- [Spark SQL Guide - Joins](https://spark.apache.org/docs/latest/sql-performance-tuning.html)
- [Databricks - Join Optimization](https://docs.databricks.com)
```

### Exemplo 2: Conceito Explicado

```markdown
---
title: "Entendendo Particionamento no Apache Spark"
date: 2025-10-13T16:00:00-03:00
draft: false
tags: ["spark", "conceitos", "partitioning"]
categories: ["conceitos"]
description: "Explicação detalhada sobre particionamento no Spark e como ele afeta performance"
ShowToc: true
---

## Introdução

Particionamento é fundamental para paralelizar processamento no Spark.

{{< alert type="info" >}}
ℹ️ **Definição:** Partição é uma divisão lógica dos dados distribuída pelos nós do cluster.
{{< /alert >}}

## Conceitos Fundamentais

### O que é Particionamento?

Spark divide dados em **partições** que são processadas em paralelo...

[Continue com a explicação...]
```

## 🚀 Comandos Úteis

### Desenvolvimento

```bash
# Servidor com drafts e live reload
~/bin/hugo server -D

# Servidor sem drafts (produção)
~/bin/hugo server

# Build para produção
~/bin/hugo --minify
```

### Git

```bash
# Atualizar tema PaperMod
git submodule update --remote --merge

# Commit das mudanças
git add .
git commit -m "feat: novo post sobre Spark"
git push
```

## 📊 Checklist de Publicação

Antes de publicar um post (`draft: false`):

- [ ] Título claro e descritivo
- [ ] Description entre 150-160 caracteres
- [ ] Tags relevantes (3-5 tags)
- [ ] Categoria apropriada
- [ ] Data correta
- [ ] TOC habilitado se necessário
- [ ] Código com syntax highlighting
- [ ] Exemplos práticos incluídos
- [ ] Ortografia revisada
- [ ] Links funcionando
- [ ] Imagens otimizadas (se houver)
- [ ] Referências citadas

## 🎯 SEO Best Practices

### Title
- Máximo 60 caracteres
- Inclua palavra-chave principal
- Seja descritivo

### Description
- Entre 150-160 caracteres
- Inclua call-to-action
- Descreva o valor do conteúdo

### URLs
- Use slugs amigáveis
- Evite caracteres especiais
- Mantenha curto e descritivo

Exemplo bom: `/posts/otimizar-spark-joins/`
Exemplo ruim: `/posts/como-otimizar-operacoes-de-join-no-apache-spark-para-melhorar-performance/`

## 📱 Testes de Responsividade

Antes de publicar, teste em:

- Desktop (1920x1080)
- Tablet (768x1024)
- Mobile (375x667)

Use as DevTools do navegador para testar.

---

**Dúvidas?** Consulte a documentação oficial do [Hugo](https://gohugo.io/documentation/) e [PaperMod](https://github.com/adityatelange/hugo-PaperMod/wiki).
