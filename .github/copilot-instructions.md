# GitHub Copilot Instructions - Blog Técnico Claudio Melo

## Contexto do Projeto

Este é um blog técnico pessoal construído com **Hugo** e o tema **PaperMod**, focado em **Engenharia de Dados**. O objetivo é compartilhar conhecimento de alta qualidade sobre tecnologias e práticas de engenharia de dados.

## Filosofia e Princípios

### Design e Estrutura
- **Inspiração:** Martin Fowler, Elton Minetto e outros blogs técnicos minimalistas
- **Minimalismo Funcional:** Priorize código limpo, rápido e sem distrações
- **Conteúdo é Rei:** O foco principal é a qualidade, profundidade e legibilidade do conteúdo técnico
- **Performance:** Otimize para carregamento instantâneo
- **Legibilidade Máxima:** Tipografia clara, alto contraste e blocos de código bem formatados

### Objetivos Estratégicos
1. Publicar artigos técnicos de alta qualidade sobre Engenharia de Dados
2. Demonstrar expertise profissional através de conteúdo técnico aprofundado
3. Construir marca pessoal para oportunidades no Brasil e exterior
4. Manter um portfólio de conhecimento atualizado

## Diretrizes de Desenvolvimento

### Tecnologias Principais
- **Hugo v0.151.0+** (static site generator)
- **Tema PaperMod** (submódulo Git)
- **Markdown** para conteúdo
- **TOML** para configuração

### Estrutura de Arquivos
```
content/posts/       # Artigos do blog
layouts/             # Templates personalizados do Hugo
static/              # Imagens, CSS customizado
themes/PaperMod/     # Tema (não modificar diretamente)
hugo.toml            # Configuração principal
```

### Padrões de Código

#### Hugo/Templates
- Use shortcodes do Hugo quando apropriado
- Mantenha templates limpos e bem documentados
- Evite lógica complexa em templates
- Prefira partials reutilizáveis

#### Markdown/Conteúdo
- Use heading hierarchy corretamente (H1 para título, H2 para seções principais)
- Inclua front matter completo em todos os posts
- Use code blocks com syntax highlighting apropriado
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
3. **Criar exemplos de código** relacionados a Engenharia de Dados
4. **Otimizar configurações** do Hugo e PaperMod
5. **Sugerir estruturas de artigos** técnicos bem organizados
6. **Gerar shortcodes** úteis para o Hugo
7. **Criar snippets** de código Python/Spark bem documentados
8. **Sugerir melhorias de SEO** e performance

## Referências

- [Hugo Documentation](https://gohugo.io/documentation/)
- [PaperMod Wiki](https://github.com/adityatelange/hugo-PaperMod/wiki)
- [Martin Fowler's Blog](https://martinfowler.com/)
- [Elton Minetto's Blog](https://eltonminetto.dev/)

---

**Nota:** Este arquivo guia o comportamento do GitHub Copilot para manter consistência e qualidade no desenvolvimento do blog.
