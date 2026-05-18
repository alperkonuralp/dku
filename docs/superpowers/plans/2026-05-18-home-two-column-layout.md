# Home Two-Column Layout Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the single "Recent Posts" list on the home page with a two-column layout — left column shows the 5 latest Episodes (`/posts`), right column shows the 5 latest Blog posts (`/blog`) — working in both TR and EN.

**Architecture:** Override `layouts/_default/home.html` (already a project-level override) to render two independent `posts-list` columns inside a CSS grid wrapper. Hugo `where` filters on `Type` field (derived from content directory name) separate episodes from blog posts. New i18n keys are added to `i18n/tr.toml` and a new `i18n/en.toml` file. CSS for the two-column grid lives in a new `assets/css/custom.css` file that the existing `layouts/partials/head/css.html` override already bundles.

**Tech Stack:** Hugo templates, Hugo i18n, CSS Grid, existing `post-card.html` partial

---

## File Map

| File | Action | Responsibility |
|---|---|---|
| `layouts/_default/home.html` | Modify | Replace single posts section with two-column HTML |
| `i18n/tr.toml` | Modify | Add `latestEpisodes`, `recentBlogPosts`, `viewAll` keys |
| `i18n/en.toml` | Create | Full EN override with same three keys |
| `assets/css/custom.css` | Create | Two-column grid + responsive + column header styles |
| `layouts/partials/head/css.html` | Modify | Add `custom.css` to bundle |

---

### Task 1: Add i18n keys to TR

**Files:**
- Modify: `i18n/tr.toml`

- [ ] **Step 1: Open file and append three new keys**

Add at the end of `i18n/tr.toml`:

```toml
# Ana sayfa iki sütun
latestEpisodes = "Son Bölümler"
recentBlogPosts = "Son Yazılar"
viewAll = "Tümünü gör"
```

- [ ] **Step 2: Verify the file is valid TOML**

Run:
```bash
hugo config --printI18nWarnings 2>&1 | head -20
```
Expected: no errors about `tr.toml`

- [ ] **Step 3: Commit**

```bash
git add i18n/tr.toml
git commit -m "i18n: add two-column home section keys (TR)"
```

---

### Task 2: Create EN i18n override

**Files:**
- Create: `i18n/en.toml`

Hugo merges project-level i18n files on top of theme-level ones. We only need to add keys that differ from or extend the theme's `themes/mana/i18n/en.toml`. The theme already has all other EN keys, so this file only needs the three new ones.

- [ ] **Step 1: Create `i18n/en.toml`**

```toml
# Home two-column section
latestEpisodes = "Latest Episodes"
recentBlogPosts = "Recent Blog Posts"
viewAll = "View all"
```

- [ ] **Step 2: Verify**

Run:
```bash
hugo config --printI18nWarnings 2>&1 | head -20
```
Expected: no errors about `en.toml`

- [ ] **Step 3: Commit**

```bash
git add i18n/en.toml
git commit -m "i18n: add two-column home section keys (EN)"
```

---

### Task 3: Create custom.css with two-column styles

**Files:**
- Create: `assets/css/custom.css`

- [ ] **Step 1: Create the file**

```css
/* Home page two-column layout */

.home-container {
  max-width: 1200px;
}

.home-columns {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 2.5rem;
  margin-top: var(--spacing-2xl);
}

.home-column {
  min-width: 0;
}

.column-header {
  display: flex;
  align-items: baseline;
  justify-content: space-between;
  gap: var(--spacing-md);
  margin-bottom: var(--spacing-lg);
}

.column-title {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--text-primary);
  margin: 0;
}

.column-view-all {
  font-size: 0.875rem;
  color: var(--accent-primary);
  text-decoration: none;
  white-space: nowrap;
  flex-shrink: 0;
  transition: opacity var(--transition-fast);
}

.column-view-all:hover {
  opacity: 0.75;
}

/* Mobile: stack columns, episodes first */
@media (max-width: 768px) {
  .home-columns {
    grid-template-columns: 1fr;
    gap: var(--spacing-2xl);
  }
}
```

- [ ] **Step 2: Commit**

```bash
git add assets/css/custom.css
git commit -m "css: add two-column home layout styles"
```

---

### Task 4: Wire custom.css into the CSS bundle

**Files:**
- Modify: `layouts/partials/head/css.html`

The existing override at `layouts/partials/head/css.html` already bundles all theme CSS. It currently ends with `(resources.Get "css/responsive.css")` and then a `custom.css` that doesn't exist yet. Check if it's already referenced:

- [ ] **Step 1: Verify current state of `layouts/partials/head/css.html`**

Open and read the file. The current content ends with:
```
  (resources.Get "css/animations.css")
  (resources.Get "css/responsive.css")
  (resources.Get "css/custom.css")
```

The `custom.css` line is **already there** — it just didn't exist as a file before. No edit needed if it's already referenced.

- [ ] **Step 2: If `custom.css` is NOT already in the bundle slice, add it**

Only do this step if Step 1 showed `custom.css` is missing. Add it after `responsive.css`:

```html
  (resources.Get "css/responsive.css")
  (resources.Get "css/custom.css")
```

- [ ] **Step 3: Test the build**

Run:
```bash
hugo --minify 2>&1 | tail -5
```
Expected: build completes without errors, no "file not found" for `custom.css`

- [ ] **Step 4: Commit (only if file was changed)**

```bash
git add layouts/partials/head/css.html
git commit -m "css: wire custom.css into bundle"
```

---

### Task 5: Update home layout to two-column structure

**Files:**
- Modify: `layouts/_default/home.html`

This is the main change. Replace the single `posts-section` block entirely.

- [ ] **Step 1: Replace the `home-container` div in `layouts/_default/home.html`**

Find this block (lines 70–81):
```html
  <div class="home-container">
    <!-- Posts List -->
    <section class="posts-section">
      <h2 class="posts-title">{{ i18n "recentPosts" }}</h2>

      <div class="posts-list">
        {{ range where site.RegularPages "Type" "posts" | first 10 }}
          {{ partial "post-card.html" (dict "page" . "limit" 3) }}
        {{ end }}
      </div>
    </section>
  </div>
```

Replace with:
```html
  <div class="home-container">
    <div class="home-columns">
      <!-- Episodes column -->
      <section class="home-column home-column--episodes">
        <div class="column-header">
          <h2 class="column-title">{{ i18n "latestEpisodes" }}</h2>
          <a href="{{ "/posts" | relLangURL }}" class="column-view-all">{{ i18n "viewAll" }} →</a>
        </div>
        <div class="posts-list">
          {{ range where site.RegularPages "Type" "posts" | first 5 }}
            {{ partial "post-card.html" (dict "page" . "limit" 3) }}
          {{ end }}
        </div>
      </section>

      <!-- Blog column -->
      <section class="home-column home-column--blog">
        <div class="column-header">
          <h2 class="column-title">{{ i18n "recentBlogPosts" }}</h2>
          <a href="{{ "/blog" | relLangURL }}" class="column-view-all">{{ i18n "viewAll" }} →</a>
        </div>
        <div class="posts-list">
          {{ range where site.RegularPages "Type" "blog" | first 5 }}
            {{ partial "post-card.html" (dict "page" . "limit" 3) }}
          {{ end }}
        </div>
      </section>
    </div>
  </div>
```

- [ ] **Step 2: Build and verify**

Run:
```bash
hugo server --port 1313 2>&1 &
```
Then open http://localhost:1313 (TR) and http://localhost:1313/en/ (EN) in a browser.

Check:
- Two columns visible on desktop
- Left column shows "Son Bölümler" (TR) / "Latest Episodes" (EN) with 5 episode cards
- Right column shows "Son Yazılar" (TR) / "Recent Blog Posts" (EN) with blog cards
- "Tümünü gör →" / "View all →" links appear in column headers
- Episodes link goes to `/posts` (TR) or `/en/posts` (EN)
- Blog link goes to `/blog` (TR) or `/en/blog` (EN)
- On mobile (resize browser to <768px): columns stack, episodes on top

- [ ] **Step 3: Stop the dev server and commit**

```bash
git add layouts/_default/home.html
git commit -m "feat: two-column home layout — Episodes + Blog"
```

---

### Task 6: Final build check and push

- [ ] **Step 1: Full production build**

```bash
hugo --minify 2>&1 | tail -10
```
Expected: 0 errors, site builds cleanly.

- [ ] **Step 2: Push**

```bash
git push
```

---

## Self-Review Notes

- **Spec coverage:**
  - ✅ Desktop two-column layout → Task 5 CSS grid
  - ✅ Mobile stacking, episodes first → Task 3 responsive breakpoint
  - ✅ 5 cards per column → `first 5` in Task 5
  - ✅ TR/EN labels → Tasks 1 & 2
  - ✅ "View all" links in column headers → Task 5 template
  - ✅ Episodes link → `/posts`, Blog link → `/blog` via `relLangURL`
  - ✅ Existing `post-card.html` partial reused → Task 5
  - ✅ "Recent Posts" heading removed → Task 5 (not carried over)

- **Type consistency:** `Type "posts"` and `Type "blog"` match Hugo's content type derived from `content/tr/posts/` and `content/tr/blog/` directory names — confirmed from `hugo.toml` `contentDir` config.

- **`relLangURL`:** Ensures `/posts` → `/posts` for TR default and `/en/posts` for EN, handling multilingual routing correctly.
