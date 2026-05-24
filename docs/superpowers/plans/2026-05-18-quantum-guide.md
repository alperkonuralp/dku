# Quantum Guide — Multi-Page Book-Style Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Publish a 25-chapter quantum computing guide as a Hugo book-style multi-page guide under `content/tr/blog/kuantum-bilgisayar/`, with a landing page showing the summary + auto-generated chapter list, and chapter pages featuring a two-block right sidebar (in-page ToC + all-chapters list) and prev/next navigation.

**Architecture:** Landing page uses `type = "blog"` so it appears as one card in blog/home listings; chapter pages use `type = "guide"` to be invisible to those listings. Hugo's `_default/single.html` is overridden at `layouts/guide/single.html` for chapter rendering. New partials handle the two-block sidebar and prev/next nav. The existing `assets/css/custom.css` is extended with guide styles.

**Tech Stack:** Hugo (multilingual, page bundles, `weight` ordering, `.PrevInSection`/`.NextInSection`), Go templates, CSS Grid/Flexbox, HTML `<details>` accordion (no JS)

---

## File Map

| File | Action | Responsibility |
|---|---|---|
| `layouts/blog/guide-landing.html` | Create | Landing page layout |
| `layouts/guide/single.html` | Create | Chapter page layout |
| `layouts/partials/guide-chapter-nav.html` | Create | Right sidebar: THIS CHAPTER + ALL CHAPTERS |
| `layouts/partials/guide-prev-next.html` | Create | Bottom prev/next navigation |
| `assets/css/custom.css` | Modify | Append guide-specific CSS |
| `i18n/tr.toml` | Modify | Add 5 guide i18n keys |
| `i18n/en.toml` | Modify | Add 5 guide i18n keys (EN) |
| `content/tr/blog/kuantum-bilgisayar/_index.md` | Create | Landing page content (from summary.md) |
| `content/tr/blog/kuantum-bilgisayar/01-giris/index.md` | Create | Chapter 1 |
| `content/tr/blog/kuantum-bilgisayar/02-klasik-bilgisayardan-kuantuma/index.md` | Create | Chapter 2 |
| `content/tr/blog/kuantum-bilgisayar/03-kuantum-mekanigine-yalin-giris/index.md` | Create | Chapter 3 |
| `content/tr/blog/kuantum-bilgisayar/04-qubit-kavrami/index.md` | Create | Chapter 4 |
| `content/tr/blog/kuantum-bilgisayar/05-superpozisyon/index.md` | Create | Chapter 5 |
| `content/tr/blog/kuantum-bilgisayar/06-olcum-problemi/index.md` | Create | Chapter 6 |
| `content/tr/blog/kuantum-bilgisayar/07-dolasiklik-entanglement/index.md` | Create | Chapter 7 |
| `content/tr/blog/kuantum-bilgisayar/08-girisim-interference/index.md` | Create | Chapter 8 |
| `content/tr/blog/kuantum-bilgisayar/09-kuantum-kapilari-ve-devreleri/index.md` | Create | Chapter 9 |
| `content/tr/blog/kuantum-bilgisayar/10-kuantum-algoritmalarinin-temel-mantigi/index.md` | Create | Chapter 10 |
| `content/tr/blog/kuantum-bilgisayar/11-onemli-kuantum-algoritmalari/index.md` | Create | Chapter 11 |
| `content/tr/blog/kuantum-bilgisayar/12-kuantum-bilgisayar-donanimlari/index.md` | Create | Chapter 12 |
| `content/tr/blog/kuantum-bilgisayar/13-gurultu-decoherence-ve-hata-problemi/index.md` | Create | Chapter 13 |
| `content/tr/blog/kuantum-bilgisayar/14-kuantum-hata-duzeltme/index.md` | Create | Chapter 14 |
| `content/tr/blog/kuantum-bilgisayar/15-guncel-durum/index.md` | Create | Chapter 15 |
| `content/tr/blog/kuantum-bilgisayar/16-kullanim-alanlari/index.md` | Create | Chapter 16 |
| `content/en/blog/kuantum-bilgisayar/_index.md` | Create | EN stub (draft=true) |

---

### Task 1: i18n keys

**Files:**
- Modify: `i18n/tr.toml`
- Modify: `i18n/en.toml`

- [ ] **Step 1: Append to `i18n/tr.toml`**

Add at the end of `C:\Projects\DKU\dku\i18n\tr.toml`:

```toml
# Rehber / çok bölümlü navigasyon
thisChapter = "Bu Bölümde"
allChapters = "Tüm Bölümler"
guidePrev = "Önceki"
guideNext = "Sonraki"
chapterNavigation = "Bölüm navigasyonu"
```

- [ ] **Step 2: Append to `i18n/en.toml`**

Add at the end of `C:\Projects\DKU\dku\i18n\en.toml`:

```toml
# Guide / multi-chapter navigation
thisChapter = "In This Chapter"
allChapters = "All Chapters"
guidePrev = "Previous"
guideNext = "Next"
chapterNavigation = "Chapter navigation"
```

- [ ] **Step 3: Verify build**

Run from `C:\Projects\DKU\dku`:
```
hugo --minify 2>&1 | tail -5
```
Expected: 0 errors, builds cleanly.

---

### Task 2: Guide CSS

**Files:**
- Modify: `assets/css/custom.css`

- [ ] **Step 1: Read current `assets/css/custom.css` to get current content, then append the following**

Append to `C:\Projects\DKU\dku\assets\css\custom.css`:

```css

/* ============================================================
   Guide: multi-page book layout
   ============================================================ */

/* Landing page */

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
  line-height: 1.6;
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
  color: var(--text-primary);
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
  line-height: 1.5;
}

/* Guide sidebar */

.guide-sidebar {
  /* Reuse .post-toc positioning from theme (sticky right sidebar) */
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
  list-style: none;
  padding: 0;
  margin: 0;
}

/* ALL CHAPTERS accordion */

.guide-chapters-details {
  /* No extra styling needed — plain container */
}

.guide-chapters-summary {
  cursor: pointer;
  list-style: none;
  padding: var(--spacing-xs) 0;
  display: flex;
  align-items: center;
  justify-content: space-between;
  /* Inherits .guide-sidebar-heading styles */
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  color: var(--text-muted);
  margin: 0 0 var(--spacing-sm) 0;
  border-bottom: 1px solid var(--border-color);
}

.guide-chapters-summary::-webkit-details-marker,
.guide-chapters-summary::marker {
  display: none;
}

/* Desktop: always show chapters list, hide toggle affordance */
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
  margin: var(--spacing-sm) 0 0 0;
  display: flex;
  flex-direction: column;
  gap: 0.125rem;
}

.guide-chapter-link {
  font-size: 0.8125rem;
  color: var(--text-secondary);
  text-decoration: none;
  display: block;
  padding: 0.2rem 0.5rem;
  border-radius: 0.25rem;
  line-height: 1.4;
  transition: color var(--transition-fast), background-color var(--transition-fast);
}

.guide-chapter-link:hover {
  color: var(--text-primary);
  background-color: var(--bg-secondary);
}

.guide-chapter-link.active {
  color: var(--accent-primary);
  font-weight: 600;
  background-color: var(--accent-light-purple-rgba-01);
}

/* Prev/Next navigation */

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
  line-height: 1.4;
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

- [ ] **Step 2: Verify build**

Run from `C:\Projects\DKU\dku`:
```
hugo --minify 2>&1 | tail -5
```
Expected: 0 errors.

---

### Task 3: Layout files

**Files:**
- Create: `layouts/blog/guide-landing.html`
- Create: `layouts/guide/single.html`
- Create: `layouts/partials/guide-chapter-nav.html`
- Create: `layouts/partials/guide-prev-next.html`

- [ ] **Step 1: Create directory `layouts/blog/` if it doesn't exist, then create `layouts/blog/guide-landing.html`**

```html
{{ define "main" }}
<div class="guide-landing-wrapper">
  <header class="guide-landing-header">
    <h1 class="post-title-main">{{ .Title }}</h1>
    {{ if .Description }}
      <p class="guide-landing-description">{{ .Description }}</p>
    {{ end }}
  </header>

  <div class="post-content-main">
    {{ .Content }}
  </div>

  <nav class="guide-chapter-list" aria-label="{{ i18n "allChapters" }}">
    <h2>{{ i18n "allChapters" }}</h2>
    <ol>
      {{ range .Pages }}
        <li>
          <a href="{{ .RelPermalink }}">{{ .Title }}</a>
          {{ if .Description }}
            <span class="chapter-desc">{{ .Description }}</span>
          {{ end }}
        </li>
      {{ end }}
    </ol>
  </nav>
</div>
{{ end }}
```

- [ ] **Step 2: Create directory `layouts/guide/` if it doesn't exist, then create `layouts/guide/single.html`**

```html
{{ define "main" }}
<div class="single-post-wrapper">
  <article class="single-post">
    {{ partial "post-image-single.html" . }}

    <header class="post-header">
      {{ partial "breadcrumb.html" . }}
      <h1 class="post-title-main">{{ .Title }}</h1>

      {{ if .Description }}
        <p class="post-description-main">{{ .Description }}</p>
      {{ end }}

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

- [ ] **Step 3: Create `layouts/partials/guide-chapter-nav.html`**

```html
{{ $currentPage := . }}
<aside class="post-toc guide-sidebar" aria-label="{{ i18n "allChapters" }}">

  {{/* THIS CHAPTER: in-page heading ToC */}}
  {{ if .TableOfContents }}
  <div class="guide-toc-block">
    <h3 class="guide-sidebar-heading">{{ i18n "thisChapter" }}</h3>
    <div class="guide-toc-content">
      {{ .TableOfContents }}
    </div>
  </div>
  {{ end }}

  {{/* ALL CHAPTERS: sibling chapter list */}}
  <details class="guide-chapters-details">
    <summary class="guide-chapters-summary">{{ i18n "allChapters" }}</summary>
    <nav>
      <ol class="guide-chapters-list">
        {{ range .Parent.Pages }}
        <li class="guide-chapter-item">
          <a href="{{ .RelPermalink }}"
             class="guide-chapter-link{{ if eq . $currentPage }} active{{ end }}">
            {{ .Title }}
          </a>
        </li>
        {{ end }}
      </ol>
    </nav>
  </details>

</aside>
```

- [ ] **Step 4: Create `layouts/partials/guide-prev-next.html`**

```html
{{ if or .PrevInSection .NextInSection }}
<nav class="guide-prev-next" aria-label="{{ i18n "chapterNavigation" }}">
  {{ with .PrevInSection }}
  <a href="{{ .RelPermalink }}" class="guide-nav-link guide-nav-prev"
     aria-label="{{ i18n "guidePrev" }}: {{ .Title }}">
    <span class="guide-nav-label">← {{ i18n "guidePrev" }}</span>
    <span class="guide-nav-title">{{ .Title }}</span>
  </a>
  {{ end }}
  {{ with .NextInSection }}
  <a href="{{ .RelPermalink }}" class="guide-nav-link guide-nav-next"
     aria-label="{{ i18n "guideNext" }}: {{ .Title }}">
    <span class="guide-nav-label">{{ i18n "guideNext" }} →</span>
    <span class="guide-nav-title">{{ .Title }}</span>
  </a>
  {{ end }}
</nav>
{{ end }}
```

- [ ] **Step 5: Verify build**

Run from `C:\Projects\DKU\dku`:
```
hugo --minify 2>&1 | tail -5
```
Expected: 0 errors.

---

### Task 4: Landing page and EN stub

**Files:**
- Create: `content/tr/blog/kuantum-bilgisayar/_index.md`
- Create: `content/en/blog/kuantum-bilgisayar/_index.md`

**Context:** `summary.md` at `content/tr/blog/kuantum-bilgisayar/summary.md` starts with a prose preamble (author's note about sources), then `---`, then `# Kuantum Bilgisayarlar: Yalın ama Derinlemesine Bir Rehber`, then content. The landing `_index.md` content should be the material AFTER the H1 (the H1 becomes the `title` field). The preamble (sources note + `---`) before the H1 can be kept as intro content.

- [ ] **Step 1: Read `content/tr/blog/kuantum-bilgisayar/summary.md` in full**

This gives you the exact content to place in `_index.md`. The structure is:
- Lines 1–3: preamble + `---`
- Line 5: `# Kuantum Bilgisayarlar: Yalın ama Derinlemesine Bir Rehber` ← becomes `title` in front matter, remove from body
- Lines 7+: actual content (H2 sections) ← goes in body

- [ ] **Step 2: Create `content/tr/blog/kuantum-bilgisayar/_index.md`**

Front matter + body:

```toml
+++
title = "Kuantum Bilgisayarlar: Yalın, Derinlemesine ve Güncel Bir Rehber"
description = "Kuantum bilgisayarları yalın ama derinlemesine anlatan, yazılım geliştiricilere yönelik kapsamlı bir rehber. Süperpozisyondan hata düzeltmeye, algoritmalardan donanım yarışına kadar 25 bölümde."
date = "2026-05-18T00:00:00+03:00"
type = "blog"
layout = "guide-landing"
draft = false
+++
```

Then append the full body of `summary.md` **excluding** the H1 line (`# Kuantum Bilgisayarlar: Yalın ama Derinlemesine Bir Rehber`). Keep everything else including the preamble and all H2 sections.

- [ ] **Step 3: Create `content/en/blog/kuantum-bilgisayar/_index.md`**

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

- [ ] **Step 4: Verify build**

Run from `C:\Projects\DKU\dku`:
```
hugo --minify 2>&1 | tail -5
```
Expected: 0 errors. TR landing page exists at `/blog/kuantum-bilgisayar/`. EN stub not rendered (draft=true).

---

### Task 5: Chapter pages (1–8)

**Files:**
- Create 8 chapter directories + `index.md` files under `content/tr/blog/kuantum-bilgisayar/`

**Content processing rule for ALL chapters:**
1. Read the source file (e.g. `kuantum_bilgisayarlar_01_giris.md`)
2. Find and REMOVE the very first line if it starts with `# ` (the H1 — it becomes `title` in front matter)
3. For chapter 1: the first H1 is `# Kuantum Bilgisayarlar: Yalın, Derinlemesine ve Güncel Bir Rehber` (the guide title, not a chapter title). Remove it. The first H2 `## 1. Giriş` stays.
4. For chapters 2–8: the H1 is the chapter title (e.g. `# 2. Klasik Bilgisayardan Kuantum Bilgisayara`). Remove it. Keep everything after.
5. All remaining content (H2 and below) goes into the body of `index.md`.

**Chapter title → front matter `title` mapping:**

| Chapter | Source file | title in front matter |
|---------|------------|----------------------|
| 1 | `kuantum_bilgisayarlar_01_giris.md` | `1. Giriş` |
| 2 | `kuantum_bilgisayarlar_02_klasik_bilgisayardan_kuantuma.md` | `2. Klasik Bilgisayardan Kuantum Bilgisayara` |
| 3 | `kuantum_bilgisayarlar_03_kuantum_mekanigine_yalin_giris.md` | `3. Kuantum Mekaniğine Yalın Giriş` |
| 4 | `kuantum_bilgisayarlar_04_qubit_kavrami.md` | `4. Qubit Kavramı` |
| 5 | `kuantum_bilgisayarlar_05_superpozisyon.md` | `5. Süperpozisyon` |
| 6 | `kuantum_bilgisayarlar_06_olcum_problemi.md` | `6. Ölçüm Problemi` |
| 7 | `kuantum_bilgisayarlar_07_dolasiklik_entanglement.md` | `7. Dolaşıklık: Entanglement` |
| 8 | `kuantum_bilgisayarlar_08_girisim_interference.md` | `8. Girişim: Interference` |

- [ ] **Step 1: Create `content/tr/blog/kuantum-bilgisayar/01-giris/index.md`**

Front matter:
```toml
+++
title = "1. Giriş"
description = "Bu rehberin amacı, kapsamı ve farklı okuyucu kitleleri için okuma kılavuzu."
date = "2026-05-18T00:00:00+03:00"
weight = 1
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_01_giris.md` with the first line (`# Kuantum Bilgisayarlar: Yalın, Derinlemesine ve Güncel Bir Rehber`) removed.

- [ ] **Step 2: Create `content/tr/blog/kuantum-bilgisayar/02-klasik-bilgisayardan-kuantuma/index.md`**

Front matter:
```toml
+++
title = "2. Klasik Bilgisayardan Kuantum Bilgisayara"
description = "Klasik bilgisayarın nasıl çalıştığı, sınırları ve kuantum hesaplamanın neden farklı bir model sunduğu."
date = "2026-05-18T00:00:00+03:00"
weight = 2
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_02_klasik_bilgisayardan_kuantuma.md` with first line (`# 2. Klasik Bilgisayardan Kuantum Bilgisayara`) removed.

- [ ] **Step 3: Create `content/tr/blog/kuantum-bilgisayar/03-kuantum-mekanigine-yalin-giris/index.md`**

Front matter:
```toml
+++
title = "3. Kuantum Mekaniğine Yalın Giriş"
description = "Kuantum, dalga-parçacık dualitesi, belirsizlik ilkesi — kuantum bilgisayarları anlamak için gereken fizik temeli."
date = "2026-05-18T00:00:00+03:00"
weight = 3
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_03_kuantum_mekanigine_yalin_giris.md` with first line removed.

- [ ] **Step 4: Create `content/tr/blog/kuantum-bilgisayar/04-qubit-kavrami/index.md`**

Front matter:
```toml
+++
title = "4. Qubit Kavramı"
description = "Qubit'i olasılık genlikleri, Bloch küresi ve fiziksel/mantıksal qubit ayrımıyla derinlemesine anlamak."
date = "2026-05-18T00:00:00+03:00"
weight = 4
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_04_qubit_kavrami.md` with first line removed.

- [ ] **Step 5: Create `content/tr/blog/kuantum-bilgisayar/05-superpozisyon/index.md`**

Front matter:
```toml
+++
title = "5. Süperpozisyon"
description = "'Qubit aynı anda hem 0 hem 1'dir' klişesinin ötesinde: süperpozisyonun gerçek matematiksel ve fiziksel anlamı."
date = "2026-05-18T00:00:00+03:00"
weight = 5
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_05_superpozisyon.md` with first line removed.

- [ ] **Step 6: Create `content/tr/blog/kuantum-bilgisayar/06-olcum-problemi/index.md`**

Front matter:
```toml
+++
title = "6. Ölçüm Problemi"
description = "Kuantum ölçümü neden klasik okumadan farklıdır ve algoritmayı nasıl etkiler?"
date = "2026-05-18T00:00:00+03:00"
weight = 6
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_06_olcum_problemi.md` with first line removed.

- [ ] **Step 7: Create `content/tr/blog/kuantum-bilgisayar/07-dolasiklik-entanglement/index.md`**

Front matter:
```toml
+++
title = "7. Dolaşıklık: Entanglement"
description = "Dolaşıklık gizemli bir bağlantı değil, ortak kuantum durumunun zorunlu sonucudur."
date = "2026-05-18T00:00:00+03:00"
weight = 7
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_07_dolasiklik_entanglement.md` with first line removed.

- [ ] **Step 8: Create `content/tr/blog/kuantum-bilgisayar/08-girisim-interference/index.md`**

Front matter:
```toml
+++
title = "8. Girişim: Interference"
description = "Kuantum algoritmalarının gerçek gücü: olasılık genliklerini doğru cevaba yönlendiren girişim mekanizması."
date = "2026-05-18T00:00:00+03:00"
weight = 8
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_08_girisim_interference.md` with first line removed.

- [ ] **Step 9: Verify build**

Run from `C:\Projects\DKU\dku`:
```
hugo --minify 2>&1 | tail -5
```
Expected: 0 errors.

---

### Task 6: Chapter pages (9–16)

**Files:**
- Create 8 more chapter directories + `index.md` files

**Same content processing rule as Task 5:** Remove the first `# ` line from each source file; everything else becomes the body.

**Chapter title mapping:**

| Chapter | Source file | title in front matter |
|---------|------------|----------------------|
| 9 | `kuantum_bilgisayarlar_09_kuantum_kapilari_ve_devreleri.md` | `9. Kuantum Kapıları ve Kuantum Devreleri` |
| 10 | `kuantum_bilgisayarlar_10_kuantum_algoritmalarin_temel_mantigi.md` | `10. Kuantum Algoritmalarının Temel Mantığı` |
| 11 | `kuantum_bilgisayarlar_11_onemli_kuantum_algoritmalari.md` | `11. Önemli Kuantum Algoritmaları` |
| 12 | `kuantum_bilgisayarlar_12_kuantum_bilgisayar_donanimlari.md` | `12. Kuantum Bilgisayar Donanımları` |
| 13 | `kuantum_bilgisayarlar_13_gurultu_decoherence_ve_hata_problemi.md` | `13. Gürültü, Decoherence ve Hata Problemi` |
| 14 | `kuantum_bilgisayarlar_14_kuantum_hata_duzeltme.md` | `14. Kuantum Hata Düzeltme` |
| 15 | `kuantum_bilgisayarlar_15_guncel_durum.md` | `15. Kuantum Bilgisayarların Güncel Durumu` |
| 16 | `kuantum_bilgisayarlar_16_kullanim_alanlari.md` | `16. Kullanım Alanları` |

- [ ] **Step 1: Create `content/tr/blog/kuantum-bilgisayar/09-kuantum-kapilari-ve-devreleri/index.md`**

Front matter:
```toml
+++
title = "9. Kuantum Kapıları ve Kuantum Devreleri"
description = "Kuantum kapılarının qubit durumlarını nasıl dönüştürdüğü ve kuantum devrelerinin nasıl oluşturulduğu."
date = "2026-05-18T00:00:00+03:00"
weight = 9
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_09_kuantum_kapilari_ve_devreleri.md` with first line (`# 9. Kuantum Kapıları ve Kuantum Devreleri`) removed.

- [ ] **Step 2: Create `content/tr/blog/kuantum-bilgisayar/10-kuantum-algoritmalarinin-temel-mantigi/index.md`**

Front matter:
```toml
+++
title = "10. Kuantum Algoritmalarının Temel Mantığı"
description = "Qubit, süperpozisyon, dolaşıklık ve girişimin bir araya gelerek nasıl algoritma oluşturduğu."
date = "2026-05-18T00:00:00+03:00"
weight = 10
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_10_kuantum_algoritmalarin_temel_mantigi.md` with first line removed.

- [ ] **Step 3: Create `content/tr/blog/kuantum-bilgisayar/11-onemli-kuantum-algoritmalari/index.md`**

Front matter:
```toml
+++
title = "11. Önemli Kuantum Algoritmaları"
description = "Deutsch-Jozsa'dan Shor'a, Grover'dan QAOA'ya: tarihsel ve kavramsal açıdan öne çıkan kuantum algoritmaları."
date = "2026-05-18T00:00:00+03:00"
weight = 11
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_11_onemli_kuantum_algoritmalari.md` with first line removed.

- [ ] **Step 4: Create `content/tr/blog/kuantum-bilgisayar/12-kuantum-bilgisayar-donanimlari/index.md`**

Front matter:
```toml
+++
title = "12. Kuantum Bilgisayar Donanımları"
description = "Süperiletken, iyon tuzağı, nötr atom, foton, spin ve topolojik qubit yaklaşımları karşılaştırmalı olarak."
date = "2026-05-18T00:00:00+03:00"
weight = 12
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_12_kuantum_bilgisayar_donanimlari.md` with first line removed.

- [ ] **Step 5: Create `content/tr/blog/kuantum-bilgisayar/13-gurultu-decoherence-ve-hata-problemi/index.md`**

Front matter:
```toml
+++
title = "13. Gürültü, Decoherence ve Hata Problemi"
description = "Kuantum bilgisayarların neden hâlâ sınırlı olduğunun temel nedeni: gürültü, decoherence ve hata birikmesi."
date = "2026-05-18T00:00:00+03:00"
weight = 13
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_13_gurultu_decoherence_ve_hata_problemi.md` with first line removed.

- [ ] **Step 6: Create `content/tr/blog/kuantum-bilgisayar/14-kuantum-hata-duzeltme/index.md`**

Front matter:
```toml
+++
title = "14. Kuantum Hata Düzeltme"
description = "Kırılgan fiziksel qubitlerden güvenilir mantıksal qubitler üretmek: surface code, threshold ve hata düzeltme maliyeti."
date = "2026-05-18T00:00:00+03:00"
weight = 14
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_14_kuantum_hata_duzeltme.md` with first line removed.

- [ ] **Step 7: Create `content/tr/blog/kuantum-bilgisayar/15-guncel-durum/index.md`**

Front matter:
```toml
+++
title = "15. Kuantum Bilgisayarların Güncel Durumu"
description = "2026 itibarıyla kuantum bilgisayarlar nerede? Hype ile gerçek ilerlemeyi ayırt etmek."
date = "2026-05-18T00:00:00+03:00"
weight = 15
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_15_guncel_durum.md` with first line removed.

- [ ] **Step 8: Create `content/tr/blog/kuantum-bilgisayar/16-kullanim-alanlari/index.md`**

Front matter:
```toml
+++
title = "16. Kullanım Alanları"
description = "Kuantum bilgisayarların gerçek potansiyeli: hangi problem sınıflarında, ne zaman ve nasıl anlamlı olabilir?"
date = "2026-05-18T00:00:00+03:00"
weight = 16
type = "guide"
draft = false
+++
```
Body: full content of `kuantum_bilgisayarlar_16_kullanim_alanlari.md` with first line removed.

- [ ] **Step 9: Verify build and smoke test**

Run from `C:\Projects\DKU\dku`:
```
hugo --minify 2>&1 | tail -5
```
Expected: 0 errors.

Then run dev server:
```
hugo server --port 1313
```
Manually verify at `http://localhost:1313/blog/kuantum-bilgisayar/`:
- Landing page shows title, description, summary content, and numbered chapter list (chapters 1–16)
- Click Chapter 1 → right sidebar shows THIS CHAPTER (H2/H3 list) and ALL CHAPTERS (accordion, chapter 1 highlighted)
- Click Chapter 2 → chapter 2 highlighted in ALL CHAPTERS
- Bottom nav shows ← Önceki on chapter 2+, Sonraki → on chapter 1–15
- Chapter 1 shows only Sonraki →, Chapter 16 shows only ← Önceki
- Blog index at `/blog/` shows ONE card for the guide (not 16 cards)
- Home page "Son Yazılar" column shows ONE guide card

Stop dev server.

---

## Self-Review

**Spec coverage:**
- ✅ Page bundle: `_index.md` + chapter dirs with `index.md`
- ✅ URL slug ASCII policy: 01-giris, 02-klasik-bilgisayardan-kuantuma, etc.
- ✅ Landing `type = "blog"`, chapters `type = "guide"` — visibility rules correct
- ✅ EN stub `draft = true`
- ✅ Layout files: guide-landing.html, guide/single.html, guide-chapter-nav.html, guide-prev-next.html
- ✅ Two-block sidebar: THIS CHAPTER (`.TableOfContents`) + ALL CHAPTERS (`.Parent.Pages` range)
- ✅ Active chapter detection: `{{ $currentPage := . }}` before range, `{{ if eq . $currentPage }}`
- ✅ ALL CHAPTERS as `<details>` — closed by default on mobile, always-open on desktop via CSS
- ✅ Prev/next: `.PrevInSection` / `.NextInSection`, first/last chapter edge cases handled
- ✅ H1 removal from chapter bodies: first line stripped, becomes `title` in front matter
- ✅ i18n keys: thisChapter, allChapters, guidePrev, guideNext, chapterNavigation
- ✅ CSS: guide-sidebar, guide-toc-block, guide-chapters-details, guide-prev-next, landing styles
- ✅ No commit/push — changes stay in working tree per user instruction

**Placeholder scan:** No TBDs. All front matter descriptions are concrete. All file paths are exact.

**Type consistency:** `guide-chapter-nav.html` uses `$currentPage` (set before range). CSS class `.guide-chapter-link.active` matches what the template emits. `guide-prev-next.html` uses `.PrevInSection`/`.NextInSection` — these work correctly because all chapter pages share the same section (`kuantum-bilgisayar`) and same `type = "guide"`.

**Scope note:** Chapters 17–25 are NOT in this plan — source files don't exist yet. When they're ready, the implementer creates `17-kriptografi-ve-post-quantum/index.md` through `25-ekler/index.md` following the exact same pattern as Task 6. They automatically appear in `.Parent.Pages` and `.PrevInSection`/`.NextInSection` due to `weight` ordering — no layout changes needed.
