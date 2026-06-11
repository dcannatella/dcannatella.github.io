# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
quarto preview        # local dev server with live reload
quarto render         # build site to /docs (for GitHub Pages)
```

R dependencies (required for pages that render from YAML data):
```r
install.packages(c("yaml", "glue"))
```

## Architecture

This is a [Quarto](https://quarto.org) static website. Pages are `.qmd` files mixing raw HTML (`{=html}` blocks) and R code chunks (`{r}` blocks). Output goes to `/docs` so GitHub Pages can serve from the `docs/` folder on the `main` branch.

**Content lives in `_data/` — edit these YAML files to update site content:**
- `_data/publications.yml` — journal articles, book chapters, conference papers, reports
- `_data/speaking.yml` — talks (set `upcoming: true` for forthcoming entries)
- `_data/projects.yml` — research projects under `current:` or `past:`
- `_data/theses.yml` — supervised theses

**Pages read and render the YAML data using R:**
- `publications.qmd`, `speaking.qmd`, `research.qmd` each use `yaml::read_yaml()` and `glue::glue()` to produce HTML at build time.
- Author name bold markup: use `**Cannatella, D.**` in YAML — the R renderer converts this to `<strong>`.

**Design system is entirely in `styles.scss` — treat it with care.** All custom classes use the `dc-` prefix:
- Layout: `.dc-page`, `.dc-hero`, `.dc-work-grid`, `.dc-dark`
- Typography: `.dc-heading`, `.dc-heading-em`, `.dc-eyebrow`, `.dc-body`, `.dc-pull`
- Components: `.dc-card`, `.dc-pub`, `.dc-talk`, `.dc-btn`, `.dc-tag`, `.dc-badge`, `.dc-photo-frame`
- Animation: `.dc-reveal` (scroll-triggered fade-up via IntersectionObserver)

**CSS variables (defined in `:root`):**
- Colors: `--lime` (#C8E34A), `--forest` (#1E3A2F), `--ink` (#16180F), `--paper` (#F8F7F2), `--muted` (#6B6B5A)
- Fonts: `--f-display` (Bricolage Grotesque), `--f-serif` (Lora), `--f-mono` (Space Mono)

**`_quarto.yml`** controls site metadata, navbar links, footer, and the base Quarto theme (`flatly` + `styles.scss`).

## Deployment

Push to GitHub → Settings → Pages → Source: deploy from `/docs`. Alternatively: `quarto publish quarto-pub`.

Static assets: place CV PDF at `docs/CV_Cannatella.pdf` and paper PDFs under `docs/papers/`.
