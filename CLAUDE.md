# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal academic website for Felipe R. Monteiro, built with the [al-folio](https://github.com/alshedivat/al-folio) Jekyll theme. Hosted at feliperodri.github.io via GitHub Pages.

## Architecture

- **_config.yml** — Main site configuration (name, URL, plugins, scholar settings)
- **_pages/** — Site pages (about, publications, projects, cv, blog)
- **_bibliography/papers.bib** — BibTeX file; publications are auto-rendered by jekyll-scholar
- **_news/** — News/announcements (one markdown file per item, shown on homepage)
- **_projects/** — Open source contribution pages (CBMC, ESBMC, etc.)
- **_data/socials.yml** — Social links (GitHub, Scholar, LinkedIn)
- **_data/repositories.yml** — GitHub repos to display
- **assets/img/** — Images including profile picture and project logos
- **assets/pdf/** — Paper PDFs and CV
- **cv/** — LaTeX CV source (resume.tex)

## Development

Run locally with Docker (recommended):
```
docker compose up
```
Site will be at http://localhost:8080. Changes auto-reload.

Slim image alternative (<100MB):
```
docker compose -f docker-compose-slim.yml up
```

To rebuild the CV PDF: `pdflatex cv/resume.tex`

## Adding Content

- **New publication**: Add BibTeX entry to `_bibliography/papers.bib`. Use `selected = {true}` for homepage display. Put PDFs in `assets/pdf/`.
- **New news item**: Create `_news/YYYY-MM-DD-slug.md` with frontmatter `layout: post`, `date:`, `inline: true`.
- **New project**: Create `_projects/name.md` with frontmatter including `layout: page`, `title`, `description`, `img`, `importance`, `category`.

## Deployment

Push to `master` triggers the GitHub Actions "Deploy site" workflow which builds to `gh-pages` branch. GitHub Pages serves from `gh-pages`.

Settings required:
- Actions > General > Workflow permissions: Read and write
- Pages > Source: Deploy from branch `gh-pages`
