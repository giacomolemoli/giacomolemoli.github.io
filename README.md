# giacomolemoli.github.io

Academic website of [Giacomo Lemoli](https://giacomolemoli.github.io), built with [Quarto](https://quarto.org) and deployed via GitHub Actions to GitHub Pages.

---

## Local development

### Prerequisites

Install [Quarto](https://quarto.org/docs/get-started/) (v1.4 or later).

### Preview locally

```bash
quarto preview
```

This starts a live-reloading server at `http://localhost:4567`.

### Render to static HTML

```bash
quarto render
```

Output is written to `_site/`. Do not commit the `_site/` folder — deployment is handled automatically by GitHub Actions on push to `main`.

---


## Adding a new publication

1. Open `publications.qmd` and add a new `::: {.pub-entry}` block in the correct section. Include title, authors, journal/status, abstract (inside `<details>`), and any relevant links.
2. Commit and push — GitHub Actions will rebuild and redeploy the site automatically.

---

## Creating a new course sub-site

Each course gets its own repository deployed as `giacomolemoli.github.io/<course-name>`.

1. **Create a new repo** on GitHub (e.g., `giacomolemoli/comp-pols`). Enable GitHub Pages (source: GitHub Actions).

2. **Copy the template** from `_templates/course-site/` into the new repo:

   ```bash
   cp -r _templates/course-site/. /path/to/new-course-repo/
   ```

3. **Edit `_quarto.yml`** in the new repo:
   - Replace `COURSE-NAME` with your course slug (e.g., `comp-pols`)
   - Update `title` and `site-url`

4. **Fill in content** in `index.qmd`, `syllabus.qmd`, and `slides/week01.qmd`.

5. **Push to `main`** — the included GitHub Actions workflow will render and deploy the site to `https://giacomolemoli.github.io/<course-name>`.

---

## Deployment

Deployment is fully automated. On every push to `main`, the workflow at `.github/workflows/publish.yml`:

1. Installs the latest stable Quarto
2. Runs `quarto render`
3. Publishes the `_site/` folder to GitHub Pages

The live site is at **<https://giacomolemoli.github.io>**.
