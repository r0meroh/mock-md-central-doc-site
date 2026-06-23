---
layout: default
title: Project Structure
parent: Getting Started
nav_order: 3
description: "A detailed breakdown of every file and folder in the repository."
last_modified_date: 2026-06-23
---

# Project Structure

Understanding the repository layout is key to contributing documentation effectively.

## Directory Tree

```
repo-root/
│
├── .github/
│   └── workflows/
│       └── pages.yml          ← GitHub Actions: build & deploy to Pages
│
├── _config.yml                ← Jekyll site configuration (title, theme, plugins)
├── Gemfile                    ← Ruby dependency manifest
├── .gitignore                 ← Files excluded from Git (e.g. _site/, vendor/)
│
├── _layouts/                  ← HTML templates that wrap Markdown content
│   ├── default.html           ← Base layout: header + sidebar + main + footer
│   └── home.html              ← Homepage layout with doc-group card grid
│
├── _includes/                 ← Reusable HTML snippets (Liquid partials)
│   ├── header.html            ← Top navigation bar
│   ├── sidebar.html           ← Left-side doc navigation
│   └── footer.html            ← Page footer with edit link
│
├── assets/
│   ├── css/
│   │   └── style.css          ← All custom CSS (variables, layout, components)
│   ├── images/                ← Site images and screenshots
│   └── js/                    ← Optional JavaScript enhancements
│
├── docs/                      ← All documentation content lives here
│   ├── getting-started/       ← "Getting Started" group
│   │   ├── index.md           ← Group landing page
│   │   ├── installation.md
│   │   ├── quick-start.md
│   │   └── project-structure.md
│   │
│   ├── guides/                ← "Guides" group
│   │   ├── index.md
│   │   ├── creating-pages.md
│   │   ├── linking-pages.md
│   │   └── jekyll-front-matter.md
│   │
│   ├── reference/             ← "Reference" group
│   │   ├── index.md
│   │   ├── jekyll-syntax.md
│   │   └── front-matter-fields.md
│   │
│   └── contributing/          ← Contribution guidelines
│       ├── index.md
│       └── style-guide.md
│
└── index.md                   ← Site homepage (maps to /)
```

## Key Files Explained

### `_config.yml`
Controls everything about how Jekyll builds the site: theme, plugins, navigation defaults, search, and more. Changes here require a server restart to take effect.

### `Gemfile`
Declares the Ruby gems the project uses. Run `bundle install` after changes. The `github-pages` gem pins every dependency to the exact version GitHub Pages uses — this prevents "works locally, breaks on Pages" surprises.

### Front Matter
Every Markdown page starts with a YAML block between `---` delimiters. This tells Jekyll which layout to use, the page title, navigation order, and more. See [Front Matter Fields](../../reference/front-matter-fields/) for a complete reference.

### `_layouts/` vs `_includes/`
- **Layouts** are full-page wrappers. A page picks exactly one layout via `layout: default` in front matter.
- **Includes** are reusable snippets you can embed anywhere with `{% include filename.html %}`.
