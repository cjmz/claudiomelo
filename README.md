# Blog Técnico - Claudio Melo

Blog pessoal focado em Engenharia de Dados, construído com Hugo e o tema PaperMod.

## 📋 Sobre

Este blog foi criado com o objetivo de compartilhar conhecimento técnico sobre Engenharia de Dados, incluindo tópicos como:

- Apache Spark
- Data Lakes e Data Warehouses
- Pipelines de Dados
- Cloud Computing (AWS, Azure, GCP)
- Arquitetura de Dados
- Boas práticas e padrões de desenvolvimento

## 🎯 Filosofia de Design e Conteúdo

A principal inspiração para o design e a estrutura do blog vem de referências técnicas como **Martin Fowler** e **Elton Minetto**. A filosofia se baseia nos seguintes pilares:

- **Minimalismo Funcional:** O design deve ser limpo, rápido e sem distrações.
- **Conteúdo é Rei:** O foco principal é a qualidade, profundidade e legibilidade do conteúdo técnico.
- **Performance:** O site deve carregar de forma quase instantânea.
- **Legibilidade Máxima:** Tipografia clara, alto contraste e blocos de código bem formatados são essenciais.

## 🎯 Objetivos Estratégicos

1. Publicar artigos e tutoriais sobre temas relevantes em Engenharia de Dados (Spark, Data Lakes, Data Warehouses, Pipelines, Cloud, etc.).
2. Criar um portfólio de conhecimento que demonstre minha expertise para o mercado.
3. Fortalecer minha marca como especialista para oportunidades de carreira, com foco no Brasil e no exterior.

## 🚀 Como Rodar o Projeto Localmente

### Pré-requisitos

- **Hugo v0.146.0 ou superior** (recomendado: v0.151.0)
- Git

### Instalação do Hugo

#### Linux

```bash
# Baixar e instalar o Hugo v0.151.0
mkdir -p ~/bin
cd ~/bin
wget https://github.com/gohugoio/hugo/releases/download/v0.151.0/hugo_extended_0.151.0_linux-amd64.tar.gz
tar -xzf hugo_extended_0.151.0_linux-amd64.tar.gz hugo
chmod +x hugo

# Adicionar ao PATH (opcional, adicione ao ~/.bashrc ou ~/.zshrc)
export PATH="$HOME/bin:$PATH"
```

#### macOS

```bash
brew install hugo
```

#### Windows

```powershell
choco install hugo-extended
```

### Clonar o Repositório

```bash
git clone <url-do-repositorio>
cd claudiomelo

# Inicializar e atualizar os submódulos (tema PaperMod)
git submodule update --init --recursive
```

### Rodar Localmente

```bash
# Usando o Hugo instalado globalmente
hugo server -D

# Ou usando o Hugo local (se instalado em ~/bin)
~/bin/hugo server -D
```

O site estará disponível em: **http://localhost:1313/**

### Comandos Úteis

```bash
# Criar um novo post
hugo new posts/nome-do-post.md

# Build para produção
hugo --minify

# Limpar cache e builds anteriores
hugo --gc
```

## 📁 Estrutura do Projeto

```
claudiomelo/
├── archetypes/          # Templates para novos conteúdos
├── assets/              # Assets personalizados (CSS, JS)
├── content/             # Conteúdo do blog (posts, páginas)
│   └── posts/           # Artigos do blog
├── data/                # Arquivos de dados
├── i18n/                # Traduções
├── layouts/             # Templates personalizados
├── static/              # Arquivos estáticos (imagens, etc)
├── themes/              # Temas (PaperMod)
│   └── PaperMod/        # Tema PaperMod (submódulo Git)
├── hugo.toml            # Configuração do Hugo
└── README.md            # Este arquivo
```

## 🎨 Tema

Este blog utiliza o tema [PaperMod](https://github.com/adityatelange/hugo-PaperMod), conhecido por:

- Design limpo e minimalista
- Suporte a modo escuro/claro
- Performance otimizada
- SEO friendly
- Totalmente responsivo

## ⚙️ Configuração

As principais configurações do site estão no arquivo `hugo.toml`. Para personalizar:

1. Edite `baseURL` com o domínio final
2. Ajuste `title` e outras configurações básicas
3. Personalize os parâmetros em `[params]`
4. Configure ícones sociais em `[[params.socialIcons]]`

## 📝 Criando Conteúdo

### Novo Post

```bash
hugo new posts/meu-novo-post.md
```

### Front Matter Recomendado

```yaml
---
title: "Título do Post"
date: 2025-10-13T10:00:00-03:00
draft: false
tags: ["spark", "data-engineering", "python"]
categories: ["tutorial"]
author: "Claudio Melo"
description: "Descrição breve do conteúdo"
ShowToc: true
TocOpen: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
---
```

## 🚢 Deploy

O site pode ser deployado em diversas plataformas:

- **GitHub Pages**
- **Netlify**
- **Vercel**
- **Cloudflare Pages**
- **AWS Amplify**

## 📄 Licença

Este projeto é de uso pessoal. O conteúdo dos artigos é protegido por direitos autorais.

## 👤 Autor

**Claudio Melo**
- Especialista em Engenharia de Dados
- [GitHub](https://github.com/)

---

**Nota:** Este é um blog técnico focado em compartilhar conhecimento sobre Engenharia de Dados e tecnologias relacionadas.
