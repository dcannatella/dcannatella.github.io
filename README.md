# Daniele Cannatella — Personal Website

Built with [Quarto](https://quarto.org). Design: Electric Lime + Deep Forest, v4.

---

## Setup

### Prerequisites
- [Quarto](https://quarto.org/docs/get-started/) ≥ 1.4
- R with packages: `yaml`, `glue`

```r
install.packages(c("yaml", "glue"))
```

### Run locally
```bash
quarto preview
```

### Build for deployment
```bash
quarto render
# Output goes to /docs
```

---

## File structure

```
/
├── _quarto.yml          # Site config, navbar, fonts
├── styles.scss          # Design system (DO NOT edit lightly)
├── index.qmd            # Home page
├── about.qmd            # About / full bio
├── research.qmd         # Research — reads from _data/projects.yml
├── teaching.qmd         # Teaching
├── publications.qmd     # Publications — reads from _data/publications.yml
├── speaking.qmd         # Speaking — reads from _data/speaking.yml
├── contact.qmd          # Contact
│
├── _data/
│   ├── publications.yml  ← EDIT THIS for publications
│   ├── speaking.yml      ← EDIT THIS for talks
│   └── projects.yml      ← EDIT THIS for research projects
│
├── images/
│   ├── headshot.jpg      ← Add your photo here
│   └── project-*.jpg     ← Add project images
│
└── docs/
    ├── CV_Cannatella.pdf ← Add your CV here
    └── papers/           ← Add paper PDFs here
```

---

## How to update content

### Publications
Edit `_data/publications.yml`. Add entries under `journal:`, `book-chapters:`,
`conference:`, or `reports:`. Bold your name with `**Cannatella, D.**`.
Run `quarto render` — the page rebuilds automatically.

### Speaking
Edit `_data/speaking.yml`. Set `upcoming: true` for forthcoming talks.
Entries sort by date automatically.

### Research projects
Edit `_data/projects.yml`. Add under `current:` or `past:`.

### Photos
Replace placeholder `<div class="dc-img-ph">` blocks in `.qmd` files with:
```html
<img src="images/your-photo.jpg" alt="Description">
```

---

## Personalise

Replace all placeholders in `.qmd` files:
- `https://github.com/your-github` → your GitHub URL
- `https://linkedin.com/in/your-linkedin` → your LinkedIn URL
- `https://scholar.google.com/your-profile` → your Scholar URL
- `https://your-blog-url.com` → your blog URL
- `https://your-sdgis-platform.com` → SD&GIS platform URL
- `d.cannatella@tudelft.nl` → already correct, update if needed

---

## Deploy (GitHub Pages)

1. Push to GitHub
2. In repo Settings → Pages → Source: Deploy from `/docs`
3. Done. Site lives at `https://your-username.github.io/your-repo`

Or use [Quarto Pub](https://quartopub.com): `quarto publish quarto-pub`
