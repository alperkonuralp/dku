# Quantum Guide — Multi-Page Book-Style Design Spec

## Goal

Publish a 25-chapter technical guide ("Kuantum Bilgisayarlar: Yalın, Derinlemesine ve Güncel Bir Rehber") as a Hugo book-style multi-page guide under the blog section. Each chapter is a separate page. A landing page shows the summary/preface and an auto-generated table of contents. Chapter pages have a two-block right sidebar (in-page ToC + all-chapters list) and prev/next navigation.

---

## Content Architecture

### Directory Structure

```
content/tr/blog/kuantum-bilgisayar/        ← branch bundle
  _index.md                                ← landing page
  01-giris/
    index.md                               ← Chapter 1
  02-klasik-bilgisayardan-kuantuma/
    index.md
  03-kuantum-mekanigine-yalin-giris/
    index.md
  04-qubit-kavrami/
    index.md
  05-superpozisyon/
    index.md
  06-olcum-problemi/
    index.md
  07-dolasiklik-entanglement/
    index.md
  08-girisim-interference/
    index.md
  09-kuantum-kapilari-ve-devreleri/
    index.md
  10-kuantum-algoritmalarinin-temel-mantigi/
    index.md
  11-onemli-kuantum-algoritmalari/
    index.md
  12-kuantum-bilgisayar-donanimlari/
    index.md
  13-gurultu-decoherence-ve-hata-problemi/
    index.md
  14-kuantum-hata-duzeltme/
    index.md
  15-guncel-durum/
    index.md
  16-kullanim-alanlari/
    index.md
  17-[slug]/
    index.md
  ... (chapters 18–25 follow same pattern)

content/en/blog/kuantum-bilgisayar/
  _index.md                                ← EN stub, draft = true
```

### URL Convention

- Landing: `/blog/kuantum-bilgisayar/`
- Chapters: `/blog/kuantum-bilgisayar/01-giris/`, `/blog/kuantum-bilgisayar/02-klasik-bilgisayardan-kuantuma/`, …

**Slug policy:** All directory names are fully ASCII-transliterated (ı→i, ş→s, ğ→g, ü→u, ö→o, ç→c). No Turkish characters in URLs.

### Front Matter Schemas

**Landing `_index.md`:**
```toml
+++
title = "Kuantum Bilgisayarlar: Yalın, Derinlemesine ve Güncel Bir Rehber"
description = "Kuantum bilgisayarları yalın ama derinlemesine anlatan, yazılım geliştiricilere yönelik kapsamlı bir rehber."
date = "2026-05-18T00:00:00+03:00"
type = "blog"
layout = "guide-landing"
image = "/images/kuantum-bilgisayar.webp"
draft = false
+++
[content from summary.md — H1 removed since title field covers it]
```

**Chapter `index.md`:**
```toml
+++
title = "1. Giriş"
description = "[one-sentence chapter description]"
date = "2026-05-18T00:00:00+03:00"
weight = 1
type = "guide"
draft = false
+++
[chapter content — leading H1 removed, weight-ordered H2+ retained]
```

**EN stub `_index.md`:**
```toml
+++
title = "Quantum Computers: A Plain but In-Depth Guide"
description = "Coming soon in English."
date = "2026-05-18T00:00:00+03:00"
type = "blog"
layout = "guide-landing"
draft = true
+++
```

### Visibility Rules

- `type = "blog"` → appears in blog index and home "Recent Blog Posts" column
- `type = "guide"` → excluded from blog index and home column (Hugo's `where ... "Type" "blog"` filters only match "blog")
- Landing is `type = "blog"` → single card in blog index ✅
- 25 chapters are `type = "guide"` → invisible to blog index ✅
- EN stub is `draft = true` → never rendered in production ✅

---

## Layout & Partial Architecture

### New Files

```
layouts/
  blog/
    guide-landing.html          ← landing page layout
  guide/
    single.html                 ← chapter page layout (auto-selected for type=guide)
  partials/
    guide-chapter-nav.html      ← right sidebar: THIS CHAPTER + ALL CHAPTERS
    guide-prev-next.html        ← bottom prev/next navigation
```

### Landing Page (`layouts/blog/guide-landing.html`)

Extends `baseof.html` via `{{ define "main" }}`. Structure:

```html
{{ define "main" }}
<div class="guide-landing-wrapper">
  <header class="guide-landing-header">
    <h1>{{ .Title }}</h1>
    <p class="guide-landing-description">{{ .Description }}</p>
  </header>

  <div class="guide-landing-content">
    {{ .Content }}
  </div>

  <nav class="guide-chapter-list" aria-label="{{ i18n "allChapters" }}">
    <h2>{{ i18n "allChapters" }}</h2>
    <ol>
      {{ range .Pages }}
        <li>
          <a href="{{ .RelPermalink }}">{{ .Title }}</a>
          {{ if .Description }}<span class="chapter-desc">{{ .Description }}</span>{{ end }}
        </li>
      {{ end }}
    </ol>
  </nav>
</div>
{{ end }}
```

`.Pages` is automatically ordered by `weight` front matter. No manual list maintenance needed.

### Chapter Page (`layouts/guide/single.html`)

Mirrors the structure of `themes/mana/layouts/_default/single.html` with two changes:
1. Right sidebar uses `guide-chapter-nav.html` instead of `toc.html`
2. `guide-prev-next.html` is rendered after post content, before footer

```html
{{ define "main" }}
<div class="single-post-wrapper">
  <article class="single-post">
    <header class="post-header">
      {{ partial "breadcrumb.html" . }}
      <h1 class="post-title-main">{{ .Title }}</h1>
      {{ if .Description }}<p class="post-description-main">{{ .Description }}</p>{{ end }}
      {{ partial "post-meta.html" . }}
    </header>

    <div class="post-content-main">
      {{ .Content }}
    </div>

    {{ partial "guide-prev-next.html" . }}
  </article>

  {{ partial "guide-chapter-nav.html" . }}
</div>
{{ end }}
```

No post tags footer, no related posts — guide chapters don't need those.

### `guide-chapter-nav.html` (Right Sidebar)

Two blocks: THIS CHAPTER (in-page H2/H3 ToC) and ALL CHAPTERS (sibling list with active highlight).

`ALL CHAPTERS` is wrapped in `<details>` for mobile accordion behavior — open on desktop via CSS, closed by default on mobile.

```html
{{ $currentPage := . }}
<aside class="guide-sidebar post-toc" aria-label="{{ i18n "allChapters" }}">

  {{/* THIS CHAPTER block */}}
  {{ if .TableOfContents }}
  <div class="guide-toc-block">
    <h3 class="guide-sidebar-heading">{{ i18n "thisChapter" }}</h3>
    <nav class="guide-toc-content">
      {{ .TableOfContents }}
    </nav>
  </div>
  {{ end }}

  {{/* ALL CHAPTERS block */}}
  <details class="guide-chapters-details" open>
    <summary class="guide-sidebar-heading guide-chapters-summary">
      {{ i18n "allChapters" }}
    </summary>
    <nav class="guide-chapters-nav">
      <ol class="guide-chapters-list">
        {{ range .Parent.Pages }}
        <li class="guide-chapter-item{{ if eq . $currentPage }} active{{ end }}">
          <a href="{{ .RelPermalink }}" class="guide-chapter-link{{ if eq . $currentPage }} active{{ end }}">
            {{ .Title }}
          </a>
        </li>
        {{ end }}
      </ol>
    </nav>
  </details>

</aside>
```

**Desktop:** `<details open>` is kept open via the `open` HTML attribute; CSS hides the `<summary>` toggle arrow on wide screens.  
**Mobile (≤1024px):** `<details>` loses the `open` attribute via CSS `content` trick — not possible in pure CSS. Instead: JavaScript removes `open` on mobile, or we use a different approach.

**Revised approach for mobile accordion:** Use `<details>` without the `open` attribute by default, and add it via a `<script>` tag based on viewport width, OR simply omit `open` and let desktop CSS force it open with `details[open]` override. The cleanest pure-CSS solution:

```css
/* Desktop: always open */
@media (min-width: 1025px) {
  .guide-chapters-details {
    /* Force open state visually — can't set 'open' attr via CSS,
       but we can hide the summary and show content always */
  }
}
```

**Final decision:** Use a small inline script (already acceptable in Hugo templates) to add `open` attribute on desktop load, leave it absent by default so mobile starts collapsed.

Actually, the cleanest Hugo-native approach: render `<details>` **without** `open` by default. On desktop, CSS makes the content always visible regardless of open state:

```css
@media (min-width: 1025px) {
  .guide-chapters-details > nav {
    display: block !important;
  }
  .guide-chapters-details > summary::marker,
  .guide-chapters-details > summary::-webkit-details-marker {
    display: none;
  }
}
```

This way: mobile = native `<details>` accordion (closed by default), desktop = always-open list with hidden toggle. No JavaScript needed.

### `guide-prev-next.html` (Bottom Navigation)

Uses Hugo's built-in `.PrevInSection` / `.NextInSection`. Since chapters are `type = "guide"` in the same section, these automatically traverse only guide pages.

```html
{{ if or .PrevInSection .NextInSection }}
<nav class="guide-prev-next" aria-label="{{ i18n "chapterNavigation" }}">
  {{ with .PrevInSection }}
  <a href="{{ .RelPermalink }}" class="guide-nav-link guide-nav-prev">
    <span class="guide-nav-label">← {{ i18n "guidePrev" }}</span>
    <span class="guide-nav-title">{{ .Title }}</span>
  </a>
  {{ end }}
  {{ with .NextInSection }}
  <a href="{{ .RelPermalink }}" class="guide-nav-link guide-nav-next">
    <span class="guide-nav-label">{{ i18n "guideNext" }} →</span>
    <span class="guide-nav-title">{{ .Title }}</span>
  </a>
  {{ end }}
</nav>
{{ end }}
```

First chapter: only `.NextInSection` renders. Last chapter: only `.PrevInSection` renders.

---

## i18n Keys

Add to `i18n/tr.toml` and `i18n/en.toml`:

```toml
# Guide / multi-chapter navigation
thisChapter = "Bu Bölümde"          # EN: "In This Chapter"
allChapters = "Tüm Bölümler"        # EN: "All Chapters"
guidePrev = "Önceki"                # EN: "Previous"
guideNext = "Sonraki"               # EN: "Next"
chapterNavigation = "Bölüm navigasyonu"  # EN: "Chapter navigation"
```

---

## CSS

Added to `assets/css/custom.css`:

### Guide Sidebar

```css
.guide-sidebar {
  /* Inherits .post-toc positioning from theme — sidebar on right, sticky */
}

.guide-sidebar-heading {
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--text-muted);
  margin: 0 0 var(--spacing-sm) 0;
  padding-bottom: var(--spacing-xs);
  border-bottom: 1px solid var(--border-color);
}

.guide-toc-block {
  margin-bottom: var(--spacing-xl);
}

.guide-toc-content nav ul {
  /* Mirrors theme's .toc-content styles */
  list-style: none;
  padding: 0;
  margin: 0;
}

.guide-chapters-details {
  /* No border/box — plain list */
}

.guide-chapters-summary {
  cursor: pointer;
  list-style: none;
  /* Styled same as .guide-sidebar-heading */
}

.guide-chapters-summary::-webkit-details-marker,
.guide-chapters-summary::marker {
  display: none;
}

/* Desktop: always show chapters content */
@media (min-width: 1025px) {
  .guide-chapters-details > nav {
    display: block !important;
  }
  .guide-chapters-summary {
    cursor: default;
    pointer-events: none;
  }
}

.guide-chapters-list {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
}

.guide-chapter-link {
  font-size: 0.875rem;
  color: var(--text-secondary);
  text-decoration: none;
  display: block;
  padding: 0.2rem 0.5rem;
  border-radius: 0.25rem;
  transition: color var(--transition-fast), background-color var(--transition-fast);
}

.guide-chapter-link:hover {
  color: var(--text-primary);
  background-color: var(--bg-tertiary, var(--bg-secondary));
}

.guide-chapter-link.active {
  color: var(--accent-primary);
  font-weight: 600;
  background-color: var(--accent-light-purple-rgba-01);
}
```

### Guide Prev/Next Navigation

```css
.guide-prev-next {
  display: flex;
  justify-content: space-between;
  gap: var(--spacing-md);
  margin-top: var(--spacing-2xl);
  padding-top: var(--spacing-xl);
  border-top: 1px solid var(--border-color);
}

.guide-nav-link {
  display: flex;
  flex-direction: column;
  gap: 0.25rem;
  text-decoration: none;
  padding: var(--spacing-md);
  border-radius: 0.5rem;
  border: 1px solid var(--border-color);
  transition: border-color var(--transition-base), box-shadow var(--transition-base);
  max-width: 45%;
}

.guide-nav-link:hover {
  border-color: var(--accent-primary);
  box-shadow: var(--shadow-md);
}

.guide-nav-next {
  margin-left: auto;
  text-align: right;
}

.guide-nav-label {
  font-size: 0.75rem;
  color: var(--text-muted);
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.guide-nav-title {
  font-size: 0.9375rem;
  color: var(--text-primary);
  font-weight: 500;
}

@media (max-width: 640px) {
  .guide-prev-next {
    flex-direction: column;
  }
  .guide-nav-link {
    max-width: 100%;
  }
  .guide-nav-next {
    margin-left: 0;
    text-align: left;
  }
}
```

### Landing Page

```css
.guide-landing-wrapper {
  max-width: 800px;
  margin: 0 auto;
}

.guide-landing-header {
  margin-bottom: var(--spacing-2xl);
}

.guide-landing-description {
  color: var(--text-secondary);
  font-size: 1.125rem;
  margin-top: var(--spacing-sm);
}

.guide-chapter-list {
  margin-top: var(--spacing-2xl);
  padding-top: var(--spacing-xl);
  border-top: 1px solid var(--border-color);
}

.guide-chapter-list h2 {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: var(--spacing-lg);
}

.guide-chapter-list ol {
  list-style: decimal;
  padding-left: 1.5rem;
  display: flex;
  flex-direction: column;
  gap: var(--spacing-md);
}

.guide-chapter-list li a {
  font-weight: 600;
  color: var(--text-primary);
  text-decoration: none;
}

.guide-chapter-list li a:hover {
  color: var(--accent-primary);
}

.chapter-desc {
  display: block;
  font-size: 0.875rem;
  color: var(--text-secondary);
  margin-top: 0.2rem;
}
```

---

## Content Processing Rules

### Chapter Title Cleanup

Each source file (`kuantum_bilgisayarlar_NN_*.md`) has a leading H1 line that duplicates the front matter `title`. This H1 must be removed from the markdown content before placing it in `index.md`.

- Source: `# 1. Giriş` → remove this line; `title = "1. Giriş"` in front matter is sufficient
- Source: `# Kuantum Bilgisayarlar: Yalın, Derinlemesine ve Güncel Bir Rehber` (in file 01, it's the guide title, not chapter title) → also remove; chapter H2 becomes the first heading in rendered content

### Chapter Titles (from `icindekiler.md`)

| Weight | Dir slug | Title |
|--------|----------|-------|
| 1 | 01-giris | 1. Giriş |
| 2 | 02-klasik-bilgisayardan-kuantuma | 2. Klasik Bilgisayardan Kuantum Bilgisayara |
| 3 | 03-kuantum-mekanigine-yalin-giris | 3. Kuantum Mekaniğine Yalın Giriş |
| 4 | 04-qubit-kavrami | 4. Qubit Kavramı |
| 5 | 05-superpozisyon | 5. Süperpozisyon |
| 6 | 06-olcum-problemi | 6. Ölçüm Problemi |
| 7 | 07-dolasiklik-entanglement | 7. Dolaşıklık: Entanglement |
| 8 | 08-girisim-interference | 8. Girişim: Interference |
| 9 | 09-kuantum-kapilari-ve-devreleri | 9. Kuantum Kapıları ve Kuantum Devreleri |
| 10 | 10-kuantum-algoritmalarinin-temel-mantigi | 10. Kuantum Algoritmalarının Temel Mantığı |
| 11 | 11-onemli-kuantum-algoritmalari | 11. Önemli Kuantum Algoritmaları |
| 12 | 12-kuantum-bilgisayar-donanimlari | 12. Kuantum Bilgisayar Donanımları |
| 13 | 13-gurultu-decoherence-ve-hata-problemi | 13. Gürültü, Decoherence ve Hata Problemi |
| 14 | 14-kuantum-hata-duzeltme | 14. Kuantum Hata Düzeltme |
| 15 | 15-guncel-durum | 15. Kuantum Bilgisayarların Güncel Durumu |
| 16 | 16-kullanim-alanlari | 16. Kullanım Alanları |
| 17 | 17-kriptografi-ve-post-quantum | 17. Kriptografi ve Post-Quantum Cryptography |
| 18 | 18-kuantum-programlama | 18. Kuantum Programlama |
| 19 | 19-kuantum-ve-yazilim-mimarisi | 19. Kuantum Bilgisayarlar ve Yazılım Mimarisi |
| 20 | 20-yaygin-yanlislar | 20. Kuantum Bilgisayarlar Hakkında Yaygın Yanlışlar |
| 21 | 21-is-dunyasi-ve-stratejik-perspektif | 21. İş Dünyası ve Stratejik Perspektif |
| 22 | 22-turkiye-ve-bolgesel-perspektif | 22. Türkiye ve Bölgesel Perspektif |
| 23 | 23-ogrenme-yol-haritasi | 23. Öğrenme Yol Haritası |
| 24 | 24-ozet-ve-sonuc | 24. Özet ve Sonuç |
| 25 | 25-ekler | 25. Ekler |

---

## What Is NOT Changed

- `themes/mana/` — read-only, never modified
- `layouts/partials/toc.html` — unchanged; guide chapters use `guide-chapter-nav.html` instead
- `layouts/_default/` templates — unchanged
- `content/tr/blog/makine-duruyor/` and other blog posts — unchanged
- Home page two-column layout — unchanged; guide landing appears as one card in "Son Yazılar" column
