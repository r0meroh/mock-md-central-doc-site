---
layout: default
title: Quick Start
parent: Getting Started
nav_order: 2
description: "Run the site locally and preview your changes before publishing."
last_modified_date: 2026-06-23
---

# Quick Start

Once you have Ruby and Bundler installed, you can run the site locally in under two minutes.

## Run Locally

```bash
bundle exec jekyll serve --livereload
```

Open your browser and navigate to:

```
http://localhost:4000
```

Jekyll will watch for file changes and automatically reload the browser when you save a file.

### Useful flags

| Flag | Effect |
|---|---|
| `--livereload` | Auto-refreshes browser on save |
| `--drafts` | Includes pages in `_drafts/` folder |
| `--incremental` | Faster rebuilds (only regenerates changed pages) |
| `--open-url` | Opens browser automatically |
| `--port 5000` | Use a custom port |

---

## Build for Production

```bash
bundle exec jekyll build
```

The compiled site is written to the `_site/` directory. This is what GitHub Pages serves — you never need to commit the `_site/` folder (it's in `.gitignore`).

---

## Project Structure at a Glance

```
.
├── _config.yml            ← Site-wide configuration
├── _layouts/              ← HTML wrapper templates
├── _includes/             ← Reusable HTML partials (header, footer, nav)
├── assets/
│   └── css/style.css      ← Custom styles
├── docs/                  ← All documentation pages
│   ├── getting-started/
│   ├── guides/
│   └── reference/
├── index.md               ← Site homepage
├── Gemfile                ← Ruby gem dependencies
└── .github/
    └── workflows/
        └── pages.yml      ← Auto-deploy to GitHub Pages
```

---

## Next Step

Continue to [Project Structure](../project-structure/) for a detailed breakdown of each file.
