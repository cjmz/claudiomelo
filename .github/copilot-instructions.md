# GitHub Copilot Instructions - Claudio Melo Technical Blog

## Project Context

This is a personal technical blog built with **Hugo** and the **PaperMod** theme, focused on **Data Engineering**. The goal is to share high-quality knowledge about data engineering technologies and practices.

## Philosophy and Principles

### Design and Structure
- **Functional Minimalism:** Prioritize clean, fast code without distractions
- **Content is King:** The main focus is quality, depth, and readability of technical content
- **Performance:** Optimize for instant loading
- **Maximum Readability:** Clear typography, high contrast, and well-formatted code blocks
- **Bilingual:** Primary language is English, with Portuguese support for Brazilian audience

### Strategic Goals
1. Publish high-quality technical articles about Data Engineering
2. Demonstrate professional expertise through in-depth technical content
3. Build personal brand for opportunities in Brazil and internationally
4. Maintain an updated knowledge portfolio

## Development Guidelines

### Main Technologies
- **Hugo v0.151.0+** (static site generator)
- **PaperMod Theme** (Git submodule)
- **Markdown** for content
- **TOML** for configuration
- **Multilingual support** (English/Portuguese)

### File Structure
```
content/
  posts/           # Blog articles (English by default)
  about.md         # About page (English)
  sobre.md         # About page (Portuguese)
layouts/           # Custom Hugo templates
static/            # Images, custom CSS
themes/PaperMod/   # Theme (don't modify directly)
hugo.toml          # Main configuration
```

### Code Standards

#### Hugo/Templates
- Use Hugo shortcodes when appropriate
- Keep templates clean and well-documented
- Avoid complex logic in templates
- Prefer reusable partials

#### Markdown/Content
- Use heading hierarchy correctly (H1 for title, H2 for main sections)
- Include complete front matter in all posts
- Use code blocks with appropriate syntax highlighting
- Inclua metadados SEO (description, tags, categories)

#### Configuração
- Mantenha `hugo.toml` organizado e comentado
- Use seções claras para diferentes tipos de configuração
- Documente configurações customizadas

### Front Matter Padrão para Posts

```yaml
---
title: "Título Claro e Descritivo"
date: 2025-10-13T10:00:00-03:00
draft: false
tags: ["spark", "data-engineering", "python", "aws"]
categories: ["tutorial", "conceitos", "arquitetura"]
author: "Claudio Melo"
description: "Descrição concisa de 150-160 caracteres para SEO"
ShowToc: true
TocOpen: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
---
```

## Temas e Categorias do Blog

### Tópicos Principais
- **Apache Spark** (performance, otimização, arquitetura)
- **Data Lakes** (design, governança, arquitetura)
- **Data Warehouses** (modelagem dimensional, modern data stack)
- **Pipelines de Dados** (ETL/ELT, orquestração, Airflow)
- **Cloud Computing** (AWS, Azure, GCP - serviços de dados)
- **Arquitetura de Dados** (data mesh, data fabric, lake house)
- **Python** (pandas, PySpark, data manipulation)
- **SQL** (otimização, boas práticas)
- **Streaming** (Kafka, Kinesis, real-time processing)
- **Data Quality** (validação, monitoramento, observability)

### Categorias de Posts
- `tutorial` - Guias passo a passo práticos
- `conceitos` - Explicações teóricas e fundamentos
- `arquitetura` - Design patterns e decisões arquiteturais
- `performance` - Otimizações e benchmarks
- `boas-praticas` - Padrões e recomendações
- `case-study` - Estudos de caso reais
- `opiniao` - Análises e reflexões técnicas

## Diretrizes de Conteúdo

### Estrutura de Artigos
1. **Introdução** - Contexto e problema
2. **Conceitos** - Fundamentos necessários
3. **Solução/Explicação** - Conteúdo principal
4. **Exemplos Práticos** - Código e demonstrações
5. **Considerações** - Trade-offs, limitações, quando usar
6. **Conclusão** - Resumo e próximos passos
7. **Referências** - Links e recursos adicionais

### Estilo de Escrita
- Tom profissional mas acessível
- Explique conceitos complexos de forma clara
- Use analogias quando apropriado
- Inclua exemplos de código funcionais
- Documente trade-offs e decisões de design
- Cite fontes e referências
- Use português brasileiro correto

### Código nos Artigos
- Sempre inclua syntax highlighting
- Use exemplos completos e executáveis quando possível
- Comente código complexo
- Mostre outputs esperados
- Inclua links para repositórios quando relevante

```python
# Exemplo de código bem formatado
from pyspark.sql import SparkSession

# Configuração do Spark
spark = SparkSession.builder \
    .appName("ExemploClaro") \
    .config("spark.sql.adaptive.enabled", "true") \
    .getOrCreate()

# Processamento de dados
df = spark.read.parquet("s3://bucket/data/")
result = df.filter(df.status == "active").groupBy("categoria").count()
result.show()
```

## Comandos Hugo Úteis

### Desenvolvimento
```bash
# Servidor local com drafts
~/bin/hugo server -D

# Criar novo post
~/bin/hugo new posts/titulo-do-post.md

# Build para produção
~/bin/hugo --minify
```

### Git e Submódulos
```bash
# Atualizar tema PaperMod
git submodule update --remote --merge

# Clonar com submódulos
git clone --recurse-submodules <repo-url>
```

## Checklist para Novos Posts

Ao criar ou revisar posts, verifique:

- [ ] Front matter completo e correto
- [ ] Título claro e SEO-friendly
- [ ] Description entre 150-160 caracteres
- [ ] Tags e categorias apropriadas
- [ ] Data correta no formato ISO
- [ ] Draft: false quando pronto para publicar
- [ ] Código com syntax highlighting
- [ ] Imagens otimizadas (se houver)
- [ ] Links funcionando
- [ ] Ortografia e gramática revisadas
- [ ] TOC (table of contents) habilitado se necessário
- [ ] Metadata de leitura (ShowReadingTime, etc.)

## Otimizações e Performance

### Imagens
- Use formatos modernos (WebP quando possível)
- Comprima imagens antes de adicionar
- Use lazy loading
- Dimensione adequadamente

### Build
- Habilite minificação em produção
- Use cache de build quando possível
- Otimize bundles CSS/JS

### SEO
- Inclua meta descriptions únicas
- Use URLs amigáveis
- Configure Open Graph tags
- Adicione schema.org markup quando relevante

## Manutenção

### Atualizações
- Mantenha Hugo atualizado (mínimo v0.146.0)
- Atualize tema PaperMod periodicamente
- Revise posts antigos para manter relevância

### Backup
- Commit frequente no Git
- Mantenha submódulos sincronizados
- Documente mudanças significativas

## Sugestões de Assistência do Copilot

Ao trabalhar neste projeto, o Copilot deve:

1. **Sugerir código Hugo/GoTemplate** seguindo boas práticas
2. **Gerar front matter** completo para novos posts
3. **Create code examples** related to Data Engineering
4. **Optimize Hugo and PaperMod** configurations
5. **Suggest well-organized technical article** structures
6. **Generate useful Hugo shortcodes**
7. **Create well-documented** Python/Spark code snippets
8. **Suggest SEO and performance improvements**

## References

- [Hugo Documentation](https://gohugo.io/documentation/)
- [PaperMod Wiki](https://github.com/adityatelange/hugo-PaperMod/wiki)

---

**Note:** This file guides GitHub Copilot behavior to maintain consistency and quality in blog development.

---

**Nota:** Este arquivo guia o comportamento do GitHub Copilot para manter consistência e qualidade no desenvolvimento do blog.
