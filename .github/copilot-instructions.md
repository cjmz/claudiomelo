# GitHub Copilot Instructions - Claudio Melo Technical Blog

## Project Context

This is a personal technical blog built with **Hugo** and the **PaperMod** theme, focused on **Software Engineering** and **Data Engineering**. The goal is to share high-quality knowledge about building robust systems, data engineering practices, and the mental models that help solve complex problems.

## Philosophy and Principles

### Design and Structure
- **Functional Minimalism:** Prioritize clean, fast code without distractions
- **Content is King:** The main focus is quality, depth, and readability of technical content
- **Performance:** Optimize for instant loading
- **Maximum Readability:** Clear typography, high contrast, and well-formatted code blocks
- **English Only:** All content is written in English for maximum reach

### Strategic Goals
1. Publish high-quality technical articles about Software and Data Engineering
2. Demonstrate professional expertise through in-depth technical content
3. Build personal brand for opportunities internationally
4. Maintain an updated knowledge portfolio
5. Share enduring principles that transcend specific technologies

## Development Guidelines

### Main Technologies
- **Hugo v0.151.0+** (static site generator)
- **PaperMod Theme** (Git submodule)
- **Markdown** for content
- **TOML** for configuration
- **English only** (no multilingual support)

### File Structure
```
content/
  posts/           # Blog articles (English)
  about.md         # About page
  search.md        # Search page
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
- Include SEO metadata (description, tags, categories)

#### Configuration
- Keep `hugo.toml` organized and commented
- Use clear sections for different configuration types
- Document custom configurations

### Standard Front Matter for Posts

```yaml
---
title: "Clear and Descriptive Title"
date: 2025-10-13T10:00:00-03:00
draft: false
tags: ["spark", "data-engineering", "python", "aws"]
categories: ["tutorial", "concepts", "architecture"]
author: "Claudio Melo"
description: "Concise description of 150-160 characters for SEO"
ShowToc: true
TocOpen: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
---
```

## Blog Topics and Categories

### Main Topics
- **Software Engineering** (design patterns, architecture, best practices)
- **Distributed Systems** (scalability, reliability, performance)
- **Apache Spark** (performance tuning, optimization, architecture)
- **Data Lakes** (design, governance, architecture)
- **Data Pipelines** (ETL/ELT, orchestration, Airflow)
- **Cloud Computing** (AWS, Azure, GCP - data services)
- **Data Architecture** (data mesh, lake house, modern data stack)
- **Python** (pandas, PySpark, data manipulation)
- **SQL** (optimization, best practices)
- **Streaming** (Kafka, Kinesis, real-time processing)
- **System Design** (trade-offs, scalability patterns, mental models)

### Post Categories
- `tutorial` - Step-by-step practical guides
- `concepts` - Theoretical explanations and fundamentals
- `architecture` - Design patterns and architectural decisions
- `performance` - Optimizations and benchmarks
- `best-practices` - Patterns and recommendations
- `case-study` - Real-world case studies
- `opinion` - Technical analyses and reflections

## Content Guidelines

### Article Structure
1. **Introduction** - Context and problem
2. **Concepts** - Necessary fundamentals
3. **Solution/Explanation** - Main content
4. **Practical Examples** - Code and demonstrations
5. **Considerations** - Trade-offs, limitations, when to use
6. **Conclusion** - Summary and next steps
7. **References** - Links and additional resources

### Writing Style
- Professional but accessible tone
- Explain complex concepts clearly
- Use analogies when appropriate
- Include functional code examples
- Document trade-offs and design decisions
- Cite sources and references
- Focus on enduring principles over specific technologies

### Code in Articles
- Always include syntax highlighting
- Use complete, executable examples when possible
- Comment complex code
- Show expected outputs
- Include repository links when relevant

```python
# Example of well-formatted code
from pyspark.sql import SparkSession

# Spark configuration
spark = SparkSession.builder \
    .appName("ClearExample") \
    .config("spark.sql.adaptive.enabled", "true") \
    .getOrCreate()

# Data processing
df = spark.read.parquet("s3://bucket/data/")
result = df.filter(df.status == "active").groupBy("category").count()
result.show()
```

## Useful Hugo Commands

### Development
```bash
# Local server with drafts
~/bin/hugo server -D

# Create new post
~/bin/hugo new posts/post-title.md

# Build for production
~/bin/hugo --minify
```

### Git and Submodules
```bash
# Update PaperMod theme
git submodule update --remote --merge

# Clone with submodules
git clone --recurse-submodules <repo-url>
```

## Checklist for New Posts

When creating or reviewing posts, verify:

- [ ] Complete and correct front matter
- [ ] Clear and SEO-friendly title
- [ ] Description between 150-160 characters
- [ ] Appropriate tags and categories
- [ ] Correct date in ISO format
- [ ] Draft: false when ready to publish
- [ ] Code with syntax highlighting
- [ ] Optimized images (if any)
- [ ] Working links
- [ ] Spelling and grammar reviewed
- [ ] TOC (table of contents) enabled if necessary
- [ ] Reading metadata (ShowReadingTime, etc.)

## Optimizations and Performance

### Images
- Use modern formats (WebP when possible)
- Compress images before adding
- Use lazy loading
- Size appropriately

### Build
- Enable minification in production
- Use build cache when possible
- Optimize CSS/JS bundles

### SEO
- Include unique meta descriptions
- Use friendly URLs
- Configure Open Graph tags
- Add schema.org markup when relevant

## Maintenance

### Updates
- Keep Hugo updated (minimum v0.151.0)
- Update PaperMod theme periodically
- Review old posts to maintain relevance

### Backup
- Frequent Git commits
- Keep submodules synchronized
- Document significant changes

## Copilot Assistance Suggestions

When working on this project, Copilot should:

1. **Suggest Hugo/GoTemplate code** following best practices
2. **Generate complete front matter** for new posts
3. **Create code examples** related to Software and Data Engineering
4. **Optimize Hugo and PaperMod** configurations
5. **Suggest well-organized technical article** structures
6. **Generate useful Hugo shortcodes**
7. **Create well-documented** code snippets (Python, Spark, SQL, etc.)
8. **Suggest SEO and performance improvements**
9. **Focus on enduring principles** over specific technologies
10. **Emphasize system design and trade-offs** in technical content

## References

- [Hugo Documentation](https://gohugo.io/documentation/)
- [PaperMod Wiki](https://github.com/adityatelange/hugo-PaperMod/wiki)

---

**Note:** This file guides GitHub Copilot behavior to maintain consistency and quality in blog development.
