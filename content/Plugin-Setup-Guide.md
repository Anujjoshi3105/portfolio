# Quartz Plugin Setup Guide

This site runs **Quartz v5** with the community plugin system (`@quartz-community/*` npm packages and `github:` sources). All plugins are registered in `quartz.config.yaml`. Below is every plugin that was added/enabled, why it helps, and how it's set up.

---

## Recently Enabled Plugins

### 1. `@quartz-community/explicit-publish`

**Why:** Only pages with `publish: true` in their frontmatter are published. New pages stay hidden until you intentionally mark them, so you can draft privately and push everything without exposing unfinished work.

**Setup:**
```yaml
- source: "@quartz-community/explicit-publish"
  enabled: true
```
- `publish: true` was added to all 32 existing content pages so nothing disappears.
- For a new note, add `publish: true` to the frontmatter to make it live.

### 2. `@quartz-community/recent-notes`

**Why:** Shows your latest 5 notes on every page footer, surfacing fresh projects/blog posts to visitors instead of leaving them buried in the explorer.

**Setup:**
```yaml
- source: "@quartz-community/recent-notes"
  enabled: true
  options:
    title: Recent Notes
    limit: 5
    showTags: true
    hideFolderPages: true
    hideTagPages: true
  layout:
    position: afterBody
    priority: 50
```

### 3. `@quartz-community/tag-list`

**Why:** Renders the current page's tags as clickable links under the title, giving visitors a quick way to browse related content.

**Setup:**
```yaml
- source: "@quartz-community/tag-list"
  enabled: true
  layout:
    position: beforeBody
    priority: 30
```
No options.

### 4. `@quartz-community/comments` (Giscus)

**Why:** Adds GitHub-Discussions-powered comments to every page — zero database, free, and tied to your GitHub identity.

**Setup:**
```yaml
- source: "@quartz-community/comments"
  enabled: true
  options:
    provider: giscus
    options:
      repo: Anujjoshi3105/portfolio
      mapping: url
      strict: true
      reactionsEnabled: true
      inputPosition: bottom
      lang: en
  layout:
    position: afterBody
    priority: 10
```
> **Action needed:** Giscus needs a public GitHub repo with Discussions enabled. Get your exact `repo`, `repoId`, `category`, and `categoryId` from [giscus.app](https://giscus.app) and paste them into `options.options`.

### 5. `@quartz-community/citations`

**Why:** Adds academic citation support (BibTeX + CSL styles like APA). Only useful if you publish research/thesis content.

**Setup:**
```yaml
- source: "@quartz-community/citations"
  enabled: true
  options:
    bibliographyFile: ./content/bibliography.bib
    csl: apa
  order: 85
```
- The bibliography file `content/bibliography.bib` must stay **empty or contain only valid BibTeX** — the plugin parses it on every page build and any stray comment breaks the build.
- Add entries, then cite in notes with `@citationkey`. Set `csl: chicago|harvard1|mla|vancouver` to switch styles.

### 6. `@quartz-community/stacked-pages`

**Why:** Turns a multi-part page into a slide-style stack reader — nice for presenting a long project or tutorial.

**Setup:**
```yaml
- source: "@quartz-community/stacked-pages"
  enabled: true
  layout:
    position: afterBody
    priority: 50
    display: all
```
No options. Use it on a page by enabling the stacked-page display (see Quartz docs).

---

## Newly Installed Plugins

### 7. `@quartz-community/obsidian-plugin-excalidraw`

**Why:** Renders Obsidian Excalidraw drawings (`.excalidraw` / `.excalidraw.md`) as interactive full-page SVGs with pan/zoom — great for diagrams in project write-ups.

**Install:**
```bash
npm install @quartz-community/obsidian-plugin-excalidraw
```

**Setup:**
```yaml
- source: "@quartz-community/obsidian-plugin-excalidraw"
  enabled: true
  options:
    enableInteraction: true
    darkMode: auto
    exportPadding: 20
```

### 8. `@quartz-community/obsidian-plugin-leaflet`

**Why:** Interactive maps from Obsidian Leaflet. **Note:** the npm package `obsidian-plugin-leaflet` currently ships the plugin-template placeholder (not a real map renderer), so it was **not registered** — wait for a working release or use the GitHub repo directly.

### 9. `github:vazome/quartz-image-zoom` (Clickable Images / Lightbox)

**Why:** Click any image to open it full-size in a lightbox — a polished, high-impact touch for a portfolio.

**Install:**
```bash
npx quartz plugin add github:vazome/quartz-image-zoom
```

**Setup:** (auto-added by the CLI)
```yaml
- source: github:vazome/quartz-image-zoom
  enabled: true
  options: {}
  order: 50
```
Verified: images render with `class="lightbox-image"`.

### 10. `github:vazome/quartz-jupyter-embed`

**Why:** Links a `.ipynb` file and Quartz renders the whole notebook inline (markdown, code, outputs). Perfect if you showcase ML/data analysis.

**Install:**
```bash
npx quartz plugin add github:vazome/quartz-jupyter-embed
```

**Setup:** (auto-added by the CLI)
```yaml
- source: github:vazome/quartz-jupyter-embed
  enabled: true
  options:
    cacheDir: .quartz-cache/notebooks
    downloadFromGitHub: true
    downloadTimeout: 15000
  order: 15
```
> `order: 15` keeps it below `syntax-highlighting` (order 20) so code blocks still get highlighted.
> Usage: a standalone link to any public `.ipynb` URL gets replaced by the embedded notebook.

---

## Useful Commands

```bash
npx quartz build                 # build to public/
npx quartz build --serve -d content   # live preview
npx quartz plugin add github:<owner>/<repo>   # install a plugin
npx quartz plugin update --latest # update installed plugins
npx quartz plugin prune --dry-run # see orphaned plugins
```

## Notes & Gotchas

- **ExplicitPublish is now active**: any new note without `publish: true` won't appear on the site.
- **`bibliography.bib`** must stay valid/empty or the whole build fails — do not add `%`-style comments.
- **Giscus** requires completing the config at giscus.app before comments load.
- The remaining disabled plugins (`hard-line-breaks`, `ox-hugo`, `roam`, `@quartz-themes/core`, `citations`-adjacent, `tag-list` replaced by `note-properties`) are intentionally off for this portfolio.
