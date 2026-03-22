# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Hugo static site using the **Mana theme** (installed as a Git submodule at `themes/mana`). Hugo Extended version 0.100.0+ is required.

## Commands

```bash
# Serve locally with live reload
hugo server

# Build the site
hugo

# Create a new post
hugo new posts/my-post-title.md

# Regenerate syntax highlighting CSS (only needed when changing Chroma styles)
hugo gen chromastyles --style=catppuccin-macchiato > themes/mana/assets/css/syntax-dark.css
hugo gen chromastyles --style=catppuccin-frappe > themes/mana/assets/css/syntax-light.css
```

## Architecture

### Configuration (`hugo.toml`)

The site is configured entirely via `hugo.toml`. Key sections:
- `[params]` — site description, favicon, hero title, avatar, social links, admonitions style
- `[params.codeHighlight]` — dark/light syntax highlighting themes
- `[params.umami]` — analytics
- `[params.buyMeACoffee]` — floating widget
- `[outputs]` — must include `home = ["HTML", "JSON"]` to enable search
- `[pagination]` — posts per page
- `[markup]` — table of contents levels, Goldmark parser (needed for blockquote alerts), and Chroma highlight settings
- `[[menus.main]]` — navigation (use root-level for single-language; use `[[languages.<lang>.menus.main]]` for multilingual)

### Theme (`themes/mana/`)

The theme is a **read-only Git submodule** — do not edit files inside it. Override theme behavior by mirroring the path in the project root (e.g., `layouts/partials/footer.html` overrides the theme's footer).

Theme layout structure:
- `layouts/_default/` — base template, home, list, single post
- `layouts/about/single.html` — about page
- `layouts/archive/` and `layouts/archives/` — archive views
- `layouts/taxonomy/` — tag cloud and per-tag listing
- `layouts/partials/` — reusable components (header, footer, post-card, TOC, search modal, etc.)
- `assets/css/` — modular CSS files bundled by `main.css`
- `assets/js/` — feature scripts (search, theme toggle, filters, navigation, blockquotes)
- `i18n/` — translation strings (`en.toml`, `he.toml`, `fr.toml`, `ja.toml`)

### Content

Posts go in `content/posts/` with frontmatter:
```markdown
---
title: "Post Title"
date: 2024-01-01
tags: ["tag1", "tag2"]
image: "/images/your-image.png"
draft: false
---
```

For an **about page**, create `content/about/index.md` (uses `layouts/about/single.html`).

### Multilingual

Two supported approaches:
- **Translation by filename**: all languages share `content/`, files named `post.md` + `post.es.md`
- **Translation by directory**: each language has its own `contentDir` (e.g., `content/en/`, `content/he/`)

RTL languages (Hebrew, Arabic) use `languageDirection = "rtl"` in the language block — the theme handles layout mirroring automatically.

### Static Assets

Place images and other static files in `static/` (e.g., `static/images/`, `static/favicon/`). They are served from the site root.
