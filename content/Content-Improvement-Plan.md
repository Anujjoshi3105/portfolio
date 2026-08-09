# Content Improvement Plan

> **Goal:** Make the portfolio content more **linked, informative, and polished** — a proper knowledge-graph driven portfolio that surfaces related work everywhere, keeps readers engaged, and fills in the thin/sparse pages.
>
> **Scope:** Everything under `content/` (index, 9 projects, 6 experience, 3 education, 2 testimonials, 8 blog posts, `.base` database views, `_assets`).
>
> **Note:** This is a plan. Nothing is implemented yet.

---

## 1. Current State Audit

### What's already good
- Strong folder structure (`Projects`, `Experience`, `Education`, `Testimonials`, `Blog`) with rich `.base` database views (table + cards) that render nicely.
- Project pages are the deepest — most have intro, problem statement, tech stack table, architecture, features, impact.
- Blog posts are genuinely useful (e.g. `sum-of-subarray-minimums.md` = 337 lines, 4 languages, complexity tables).
- Index page is a functional hub with links out to all sections.
- Frontmatter is rich enough to power the database views.

### Gaps found (priority-ordered)

**🔴 P1 — Correctness (broken things)**
| Issue | Location | Fix |
|---|---|---|
| Broken wikilinks with wrong case/spaces: `[[education/CBSE XII]]`, `[[testimonials/Rahul Agrawal]]`, `[[projects/Ekalavya]]` | `index.md:77,84,57` | Point to real filenames: `cbse-xii`, `rahul-agrawal`, `ekalavya` |
| Sarah Johnson testimonial links to **nothing** — "Website Redesign Project" has no page and no avatar/contact | `Testimonials/sarah-johnson.md` | Add link + optionally a `projects/website-redesign` placeholder or remove | 
| `LeetCode Weekly Contest 494` is a stub (17 lines, intro only) | `Blog/leetcode-weekly-contest-494.md` | Fill with real solutions or mark as draft/unpublish |
| LIMSTIR Live URL mismatch: intro says `limstir.netlify.app`, frontmatter says `limstir-dtu.vercel.app` | `Projects/limstir-dtu.md:33` | Make consistent |
| `sapplinn.png` is **2.5 MB** (huge, slow page) | `_assets/sapplinn.png` | Compress/resize |
| `blog/valid-sudoku` uses `###` headings (breaks TOC/outline) | `Blog/valid-sudoku.md` | Promote to `##` |

**🟠 P2 — Thin / uninformative pages**
| Page | Current depth | Fix |
|---|---|---|
| All **Education** pages (2–3 lines each) | 1–2 bullets | Add coursework, notable coursework→project links, activities, achievements |
| **Experience** pages (3 bullets, no numbers) | Sparse | Add concrete metrics, outcome, and links to the projects they produced |
| **Sarah Johnson** testimonial | 1 quote | Avatar, context, link |
| **index.md** | No stats | Add a "by the numbers" strip, profile links, featured graph |

**🟡 P3 — Missing links (knowledge-graph quality)**
- **No cross-links between projects sharing a stack** (e.g. `netrai`/`sapplinn` both ML+FastAPI; `fictora`/`bitlog` both Next.js).
- **Projects don't link to the experience that produced them** (`ird-dtu` ↔ `web-developer-intern-ird-dtu`, `srdtu` ↔ `general-secretary-sr-dtu`).
- **Experience pages don't link to their related projects** (only Quickintell, IRD, SR-DTU do).
- **Blog posts have almost no Related section** (only `sum-of-subarray-minimums` does).
- **No skill/tech hub** — nothing links "PyTorch" to the projects that use it.
- **Testimonials only link one-way** to experience; experience should link back.

**🟢 P4 — Missing sections/pages**
- No **Skills** page or tech index (tag pages exist but nothing curated).
- No **Certifications** page (certificates exist as Google-Drive links in frontmatter but are only visible in database views).
- No **Contact** page (only footer + index section).
- No **resume/CV** download link.
- Tag taxonomy is inconsistent (`Minstack`, `Sparse-Tree`, `computer-vision`, `full-stack`, `GFG`, `POTD`).

---

## 2. Implementation Plan (by phase)

### Phase A — Fix correctness (P1)
1. Repair broken wikilinks in `index.md` (3 links).
2. Fix LIMSTIR URL inconsistency.
3. Compress `sapplinn.png`.
4. Fix `valid-sudoku` heading levels.
5. Decide on contest-494: either flesh out (needs real content from user) or unpublish (remove `publish: true`).

### Phase B — Build the link graph (P3)
Add a `## Related` section to **every** page with 2-way links:
- **Projects:** related projects (shared stack/theme), the experience entry that produced it, blog posts about it.
- **Experience:** projects built there, testimonial, education (e.g. KKR → skills used in projects).
- **Education:** prerequisite education, projects built using that coursework (e.g. B.Tech ML minor → netrai/sapplinn), clubs/societies.
- **Testimonials:** experience + project the quote references.
- **Blog:** sibling problems, related project, related contest.

Example pattern:
```markdown
## Related
- [[projects/netrai]] — built with the same FastAPI + PyTorch stack
- [[experience/fullstack-intern-quickintell]] — where I shipped production AI
- [[Blog/subarrays-with-first-element-minimum]] — a follow-up monotonic stack problem
```

### Phase C — Deepen thin pages (P2)
- **Education:** add coursework bullet lists, notable projects tied to the degree, achievements, societies. Keep frontmatter; expand body.
- **Experience:** convert 3-bullet lists into outcome-focused write-ups with metrics where known, plus "Related" links.
- **index.md:** add a "By the Numbers" stats strip (projects, posts, stars, contest ratings), link each competitive-programming platform to its profile, and strengthen the featured sections.

### Phase D — New pages (P4)
1. **`Skills.md`** — curated skill index grouped by domain, each linking to the projects/experience that use it (this becomes the hub that powers graph/backlinks).
2. **`Certifications.md`** — list of certificates with links (source: frontmatter `certificate` fields).
3. **`Contact.md`** — expand "Get in Touch" into a page.
4. **(Optional)** `resume.pdf` in static + link from index/footer.

### Phase E — Standardization
- Define a consistent **tag taxonomy** and normalize frontmatter tags across all pages (e.g. `machine-learning`, `computer-vision`, `full-stack`, `nextjs`, `competition`).
- Ensure every page has `description` (needed by og-image + search snippets).
- Add missing `created`/`updated`/`slug` fields for consistency with the `.base` views.

---

## 3. Files Touched (summary)

| File(s) | Change |
|---|---|
| `index.md` | Fix links, add stats, tighten copy, more curated linkouts |
| `Projects/*.md` (9) | Add `## Related` (projects + experience + blog), fix URLs/tags |
| `Experience/*.md` (6) | Deepen bullets into outcomes, add `## Related` |
| `Education/*.md` (3) | Add coursework/achievements, `## Related` |
| `Testimonials/*.md` (2) | Fix Sarah (avatar/contact/link), back-links |
| `Blog/*.md` (8) | Add `## Related`, fix contest-494, heading fixes |
| `Skills.md`, `Certifications.md`, `Contact.md` (new) | New hub pages |
| `.base` files (5) | Minor: add `Related` isn't needed (body-only), add new pages where relevant |
| `_assets/sapplinn.png` | Compress |
| `bibliography.bib` | Unchanged (must stay empty/valid) |

---

## 4. Verification

After changes:
1. `npx quartz build` — must pass, no broken-link warnings for wikilinks.
2. Check emitted HTML: backlinks sidebar populates on project/blog pages; graph view shows a dense connected network.
3. Manually spot-check: index → project → experience → testimonial cycle all link both ways.
4. Confirm `Skills.md`, `Certifications.md`, `Contact.md` render and link correctly.

---

## 5. Decisions (confirmed)

1. **LeetCode Weekly Contest 494** → **Unpublish** (remove `publish: true`), keep file for later.
2. **Skills.md, Certifications.md, Contact.md** → create all three.
3. **Sarah Johnson testimonial** → **Remove** the file and its reference in `index.md`.
4. **Resume PDF** → user will provide; add `resume.pdf` to `static/` + link when available (placeholder noted).

---

*Status: decisions locked — implementation in progress.*
