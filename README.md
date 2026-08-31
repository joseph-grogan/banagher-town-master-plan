# Banagher Town Masterplan

Community project site built with Jekyll and hosted on GitHub Pages.

**Live site:** https://joseph-grogan.github.io/banagher-town-master-plan/

---

## Running Locally

You need Docker installed. No Ruby or Jekyll required on your machine.

### Start the local site

```bash
cd banagher-town-master-plan
docker run --rm -d --name jekyll-serve -p 4000:4000 -v "$(pwd):/srv/jekyll:Z" jekyll/jekyll:4.2.2 jekyll serve --host 0.0.0.0 --config _config.yml,_config_dev.yml --force_polling
```

First run takes ~90 seconds (installing gems). After that, visit **http://localhost:4000/**

The site auto-regenerates when you edit files — just refresh the browser.

### Stop the local site

```bash
docker stop jekyll-serve
```

---

## Project Structure

```
_config.yml              — Site settings, collections, defaults
_config_dev.yml          — Local overrides (not committed to git)
Gemfile                  — Ruby dependencies (github-pages gem)
index.md                 — Homepage
_layouts/
  default.html           — Base template (head, header, footer)
  project.html           — Project page template
_includes/
  header.html            — Navigation bar
  footer.html            — Footer
  map.html               — Leaflet map (reads project coordinates)
_projects/               — One .md file per project (published to site)
  meitheal.md
  fort-falkland.md
  ...
assets/
  css/style.css          — All styling
  images/                — Site images
docs/                    — Internal records (NOT published to site)
.github/workflows/       — Auto-deploys to GitHub Pages on push
```

## Adding a New Project

Create a file in `_projects/`, e.g. `_projects/my-project.md`:

```markdown
---
title: My Project
tagline: A short description
status: Concept
order: 10
lat: 53.1890
lng: -7.9870
---

Your content here in plain markdown.
```

- **status** — `Concept` (orange), `In Progress` (blue), or `Launched` (green)
- **order** — controls sort order on the homepage
- **lat/lng** — optional, places a pin on the map. Omit if the project has no fixed location.

The project page, homepage card, and map pin are all generated automatically.

## Deploying

Push to `main` and GitHub Actions builds and deploys automatically. Takes about a minute.

```bash
git add .
git commit -m "describe your change"
git push
```
