# DocHub — Confluence-Style Docs on GitHub Pages

> **Write documentation as code. Review it like code. Ship it automatically.**

DocHub is an open-source, enterprise-ready documentation platform that turns plain Markdown files into a fully navigable, cross-linked knowledge base — hosted for **free** on GitHub Pages using **Jekyll**.

Think of it as a self-hosted Confluence replacement where every page is a version-controlled text file, every change goes through a pull request, and the entire site deploys automatically on merge.

---

## Table of Contents

1. [Why Jekyll + Markdown?](#why-jekyll--markdown)
2. [Project Structure](#project-structure)
3. [How to Create a New Documentation Page](#how-to-create-a-new-documentation-page)
4. [How to Edit an Existing Page](#how-to-edit-an-existing-page)
5. [How to Upload Images and Files](#how-to-upload-images-and-files)
6. [How to Deploy and Host on GitHub Pages](#how-to-deploy-and-host-on-github-pages)
7. [Local Development](#local-development)
8. [Doc Groups (Navigation Structure)](#doc-groups-navigation-structure)
9. [Jekyll Front Matter Quick Reference](#jekyll-front-matter-quick-reference)
10. [Contributing](#contributing)

---

## Why Jekyll + Markdown?

### The Problem with Traditional Wiki Tools

Tools like Confluence, Notion, and SharePoint solve the immediate problem of shared documentation, but they come with significant long-term costs:

| Pain Point | Traditional Wiki | DocHub |
|---|---|---|
| Licensing cost | Per-seat, per-month | **Free** (GitHub Pages) |
| Version history | Opaque, hard to diff | **Full Git history** — diff any two versions |
| Review workflow | Comments after the fact | **Pull requests** — review before publishing |
| Offline access | Requires internet + VPN | **Clone the repo**, works anywhere |
| Search | Vendor-dependent | **Full-text search** built into the theme |
| Custom branding | Paid plan | **Full CSS control** |
| Backup / export | Manual export, vendor lock-in | **It's just files** — always portable |
| Editor freedom | Must use the browser UI | **Any editor** — VS Code, Vim, Notepad |

### Why Jekyll Specifically?

Jekyll is the static-site generator built into GitHub Pages. When you push to `main`, GitHub automatically runs Jekyll and deploys the result — no CI/CD pipeline to maintain (though this repo also includes one for advanced control).

**Key benefits of Jekyll over vanilla Markdown:**

- **Front matter** — add metadata (title, navigation order, description) to any page with a simple YAML header
- **Layouts** — wrap all pages in a consistent header/sidebar/footer without repeating HTML
- **Liquid templates** — generate navigation menus, breadcrumbs, and cross-links automatically
- **Kramdown extensions** — richer Markdown: definition lists, footnotes, attribute injection, callout boxes
- **Rouge syntax highlighting** — beautiful, language-aware code blocks out of the box
- **Themes** — drop in a professional theme (this repo uses `just-the-docs`) in one config line
- **Collections** — group related pages into logical sections (Getting Started, Guides, Reference, etc.)
- **Plugins** — add SEO tags, sitemaps, feeds, and more with a single line in `Gemfile`

### The Result

A documentation site that looks and navigates like Confluence, costs nothing to host, and is maintained entirely through Git workflows your engineering team already knows.

---

## Project Structure

```
repo-root/
│
├── .github/
│   ├── workflows/
│   │   └── pages.yml          ← GitHub Actions: auto-build & deploy on push to main
│   └── PULL_REQUEST_TEMPLATE.md
│
├── _config.yml                ← Site-wide configuration (title, theme, plugins, nav)
├── Gemfile                    ← Ruby gem dependencies (Jekyll + plugins)
├── .gitignore
│
├── _layouts/                  ← HTML wrapper templates
│   ├── default.html           ← Standard page: header + sidebar + content + footer
│   └── home.html              ← Homepage with doc-group card grid
│
├── _includes/                 ← Reusable HTML snippets (Liquid partials)
│   ├── header.html            ← Top navigation bar
│   ├── sidebar.html           ← Left-panel doc navigation tree
│   └── footer.html            ← Footer with "Edit on GitHub" link
│
├── assets/
│   ├── css/style.css          ← All custom styles (CSS variables, layout, components)
│   ├── images/                ← Screenshots, diagrams, and other image assets
│   └── js/                    ← Optional JavaScript
│
├── docs/                      ← All documentation content
│   ├── getting-started/       ← "Getting Started" doc group
│   │   ├── index.md           ← Group landing page
│   │   ├── installation.md
│   │   ├── quick-start.md
│   │   └── project-structure.md
│   ├── guides/                ← "Guides" doc group
│   │   ├── index.md
│   │   ├── creating-pages.md
│   │   ├── linking-pages.md
│   │   └── jekyll-front-matter.md
│   ├── reference/             ← "Reference" doc group
│   │   ├── index.md
│   │   ├── jekyll-syntax.md
│   │   └── front-matter-fields.md
│   └── contributing/          ← Contribution guidelines
│       ├── index.md
│       └── style-guide.md
│
└── index.md                   ← Site homepage (renders at /)
```

---

## How to Create a New Documentation Page

> **Estimated time:** 2–5 minutes

### Step 1 — Decide Where It Belongs

Choose the doc group folder that best fits your content:

```
docs/getting-started/   ← Setup, prerequisites, first steps
docs/guides/            ← How-to articles, tutorials
docs/reference/         ← API, config keys, syntax lookups
docs/contributing/      ← Contributor workflows and style
```

To create a **brand-new doc group**, create a new folder and add an `index.md` inside it (copy the structure from an existing group index).

---

### Step 2 — Create the Markdown File

Name your file using lowercase letters and hyphens only:

```
✅  docs/guides/configure-sso.md
✅  docs/reference/api-endpoints.md
❌  docs/guides/Configure SSO.md    (spaces not allowed)
❌  docs/guides/ConfigureSSO.md     (uppercase causes routing issues)
```

---

### Step 3 — Add Front Matter

Paste this block at the very top of your file and fill in the values:

```yaml
---
layout: default
title: "Your Page Title"
parent: "Guides"          # must exactly match the parent group's title
nav_order: 10             # position in sidebar (lower = higher up)
description: "One-sentence summary of what this page covers."
last_modified_date: 2026-06-23
---
```

---

### Step 4 — Write Your Content

After the closing `---`, write standard Markdown:

```markdown
---
layout: default
title: Configure SSO
parent: Guides
nav_order: 4
description: "Step-by-step guide to setting up SAML 2.0 SSO."
last_modified_date: 2026-06-23
---

# Configure SSO

This guide walks you through configuring Single Sign-On.

## Prerequisites

- Admin access to your Identity Provider (IdP)
- Admin rights in the DocHub settings panel

## Steps

1. Navigate to **Settings > Authentication > SSO**.
2. Enter your **IdP Metadata URL**.
3. Click **Save and Test**.
4. Verify the login flow with a test account.
```

---

### Step 5 — Preview Locally

```bash
bundle exec jekyll serve --livereload
# Open http://localhost:4000
# Your new page appears in the sidebar under its parent group
```

---

### Step 6 — Submit a Pull Request

```bash
git checkout -b docs/add-sso-guide
git add docs/guides/configure-sso.md
git commit -m "docs: add SSO configuration guide"
git push -u origin docs/add-sso-guide
```

Open a pull request on GitHub. The page deploys automatically when the PR is merged to `main`.

---

### New Page Flow Diagram

```
┌─────────────────────────────────────────────────────────────────┐
│                     CREATE A NEW PAGE                           │
└─────────────────────────────────────────────────────────────────┘

  1. Choose group        2. Create file         3. Add front matter
  ┌─────────────┐        ┌──────────────┐       ┌──────────────────┐
  │ docs/       │        │ my-topic.md  │       │ ---              │
  │ ├ guides/   │  ───►  │ (lowercase,  │  ───► │ layout: default  │
  │ ├ reference/│        │  hyphens)    │       │ title: "…"       │
  │ └ getting-  │        └──────────────┘       │ parent: "…"      │
  │   started/  │                               │ nav_order: N     │
  └─────────────┘                               └──────────────────┘
         │
         ▼
  4. Write content       5. Preview locally     6. Open PR
  ┌─────────────┐        ┌──────────────┐       ┌──────────────────┐
  │ # Heading   │        │ bundle exec  │       │ git checkout -b  │
  │             │  ───►  │ jekyll serve │  ───► │ git add .        │
  │ Markdown    │        │              │       │ git commit -m    │
  │ content     │        │ localhost:   │       │ git push         │
  │ here        │        │ 4000         │       │ → open PR on GH  │
  └─────────────┘        └──────────────┘       └──────────────────┘
```

---

## How to Edit an Existing Page

> **Estimated time:** 1–3 minutes

### Option A — Edit in GitHub's Web UI (No Local Setup Required)

This is the fastest path for small changes like fixing typos or updating a step.

1. Navigate to the file on GitHub (e.g., `docs/guides/creating-pages.md`)
2. Click the **pencil icon** (✏️) in the top-right of the file view
3. Make your changes in the built-in editor
4. Scroll down to **Commit changes**
5. Select **"Create a new branch for this commit and start a pull request"**
6. Click **Propose changes**
7. Fill in the PR form and submit

```
GitHub file view
┌──────────────────────────────────────────────────────┐
│  docs / guides / creating-pages.md          [✏️] [🗑️] │
│  ─────────────────────────────────────────────────── │
│  Raw  |  Blame  |  History                           │
│                                                      │
│  ---                                                 │
│  layout: default                                     │
│  title: Creating Pages                               │
│  ...                                                 │
└──────────────────────────────────────────────────────┘
         ↑ Click ✏️ to open the web editor
```

### Option B — Edit Locally with Your Preferred Editor

```bash
# 1. Pull the latest changes
git checkout main
git pull origin main

# 2. Create a branch for your edits
git checkout -b docs/update-installation-guide

# 3. Open the file in your editor
code docs/getting-started/installation.md    # VS Code
# or: vim, nano, Sublime Text, etc.

# 4. Make your changes and update last_modified_date in front matter

# 5. Preview
bundle exec jekyll serve --livereload

# 6. Commit and push
git add docs/getting-started/installation.md
git commit -m "docs: update Ruby version requirement to 3.2"
git push -u origin docs/update-installation-guide

# 7. Open a pull request on GitHub
```

---

## How to Upload Images and Files

### Images

1. **Place the image file** in `assets/images/`:

```bash
cp ~/Downloads/architecture-diagram.png assets/images/
git add assets/images/architecture-diagram.png
```

2. **Reference it in your Markdown page:**

```markdown
![Architecture diagram](/assets/images/architecture-diagram.png)
```

3. **For diagrams that need to scale**, use relative_url:

```liquid
![Architecture diagram]({{ '/assets/images/architecture-diagram.png' | relative_url }})
```

### Image Best Practices

| Guideline | Why |
|---|---|
| Use descriptive file names (`sso-flow.png` not `img1.png`) | Easier to reference and maintain |
| Prefer SVG for diagrams | Scales to any screen size without blurring |
| Keep files under 500 KB | Keeps the repository lean and Pages loads fast |
| Always add `alt` text | Accessibility and SEO |
| Store images in `assets/images/` | Consistent, predictable paths |

### Uploading via GitHub Web UI

You can also upload files without a local Git setup:

```
1. Navigate to assets/images/ on GitHub
2. Click "Add file" → "Upload files"
3. Drag and drop your image(s)
4. Commit directly to main (for assets) or via a PR
```

```
GitHub folder view: assets/images/
┌──────────────────────────────────────────────────────┐
│  assets / images /                                   │
│                                               ┌────┐ │
│  Name              Last commit    Date        │Add │ │
│  ──────────────    ──────────     ──────      │file│ │
│  .gitkeep          Initial        Jun 23      └────┘ │
│                                                      │
│         ↑ Click "Add file" → "Upload files"          │
└──────────────────────────────────────────────────────┘
```

---

## How to Deploy and Host on GitHub Pages

### One-Time Setup (5 steps)

#### Step 1 — Enable GitHub Pages in Repository Settings

1. Go to your repository on GitHub
2. Click **Settings** (top navigation)
3. In the left sidebar, click **Pages**
4. Under **Source**, select **GitHub Actions**
5. Click **Save**

```
Repository Settings → Pages
┌──────────────────────────────────────────────────────┐
│  GitHub Pages                                        │
│  ─────────────────────────────────────────────────── │
│  Build and deployment                                │
│                                                      │
│  Source                                              │
│  ┌──────────────────────────────┐                   │
│  │  GitHub Actions          ▼   │  ← Select this    │
│  └──────────────────────────────┘                   │
│                                                      │
│  Your site is published at:                          │
│  https://<org>.github.io/<repo>/                     │
└──────────────────────────────────────────────────────┘
```

#### Step 2 — Update `_config.yml` with Your URLs

Open `_config.yml` and set your site's URL:

```yaml
# _config.yml

url: "https://<your-org>.github.io"        # your GitHub Pages root URL
baseurl: "/<your-repo-name>"               # leave empty "" if using <org>.github.io
```

**Examples:**

| Scenario | `url` | `baseurl` |
|---|---|---|
| Organization site (`acme.github.io`) | `https://acme.github.io` | `""` |
| Project site (`acme.github.io/docs`) | `https://acme.github.io` | `"/docs"` |
| Custom domain (`docs.acme.com`) | `https://docs.acme.com` | `""` |

#### Step 3 — Push to `main`

The GitHub Actions workflow (`.github/workflows/pages.yml`) automatically runs on every push to `main`:

```bash
git add .
git commit -m "chore: configure site URL for GitHub Pages"
git push origin main
```

#### Step 4 — Watch the Deployment

1. Go to the **Actions** tab of your repository
2. You'll see a workflow run named **"Deploy to GitHub Pages"**
3. Click it to see the build and deploy steps in real time

```
Actions tab
┌──────────────────────────────────────────────────────┐
│  All workflows                                       │
│  ─────────────────────────────────────────────────── │
│  ✅ Deploy to GitHub Pages    main   2 minutes ago   │
│     ├── build    ✅  45s                             │
│     └── deploy   ✅  15s                             │
│                                                      │
│  Site URL: https://acme.github.io/docs/              │
└──────────────────────────────────────────────────────┘
```

#### Step 5 — (Optional) Set a Custom Domain

1. In **Settings → Pages**, enter your custom domain (e.g., `docs.acme.com`)
2. Add a `CNAME` file to the repo root:

```bash
echo "docs.acme.com" > CNAME
git add CNAME && git commit -m "chore: add custom domain CNAME" && git push
```

3. In your DNS provider, add a `CNAME` record:

```
Type    Name    Value
CNAME   docs    <your-org>.github.io
```

4. Back in GitHub Pages settings, check **"Enforce HTTPS"** once DNS propagates (usually < 1 hour)

---

### Full Deployment Flow Diagram

```
Developer Workstation                GitHub                   GitHub Pages CDN
─────────────────────                ──────                   ────────────────

  Edit .md files
        │
        ▼
  git commit -m "…"
        │
        ▼
  git push origin main  ──────────►  main branch
                                          │
                                          ▼
                                    GitHub Actions triggers
                                    "Deploy to GitHub Pages"
                                          │
                                    ┌─────┴──────┐
                                    │   build    │
                                    │            │
                                    │ ruby/setup │
                                    │ -ruby@v1   │
                                    │            │
                                    │ jekyll     │
                                    │ build      │
                                    │            │
                                    │ → _site/   │
                                    └─────┬──────┘
                                          │
                                    ┌─────┴──────┐
                                    │   deploy   │
                                    │            │
                                    │ upload to  │──────────► https://org.github.io/repo/
                                    │ Pages CDN  │
                                    └────────────┘

  Total time from push to live: ~60–90 seconds
```

---

### Deployment Checklist

Before your first deploy, verify:

- [ ] `_config.yml` has correct `url` and `baseurl`
- [ ] **Settings → Pages → Source** is set to **GitHub Actions**
- [ ] The workflow file exists at `.github/workflows/pages.yml`
- [ ] Repository is public, **or** you have a GitHub Pro / Teams / Enterprise plan (private repos require a paid plan for Pages)
- [ ] `Gemfile` includes `github-pages` or `jekyll` gem

---

## Local Development

### Prerequisites

| Tool | Version | Install |
|---|---|---|
| Ruby | ≥ 3.1 | [ruby-lang.org](https://www.ruby-lang.org/en/downloads/) |
| Bundler | latest | `gem install bundler` |
| Git | ≥ 2.30 | [git-scm.com](https://git-scm.com) |

### Setup

```bash
# Clone the repository
git clone https://github.com/<org>/<repo>.git
cd <repo>

# Install gems
bundle install

# Start the local server with live reload
bundle exec jekyll serve --livereload

# Open in browser
open http://localhost:4000
```

### Useful Commands

```bash
# Build without serving (output goes to _site/)
bundle exec jekyll build

# Build for production
JEKYLL_ENV=production bundle exec jekyll build

# Include draft pages
bundle exec jekyll serve --drafts

# Faster incremental builds (only rebuild changed files)
bundle exec jekyll serve --incremental

# Check for broken links (requires html-proofer gem)
bundle exec htmlproofer ./_site --disable-external
```

---

## Doc Groups (Navigation Structure)

The sidebar is organized into **doc groups** — top-level sections that contain related pages. Each group is a folder inside `docs/` with an `index.md` that has `has_children: true` in its front matter.

### Existing Groups

| Group | Folder | Purpose |
|---|---|---|
| Getting Started | `docs/getting-started/` | Setup, installation, first steps |
| Guides | `docs/guides/` | How-to articles and tutorials |
| Reference | `docs/reference/` | Technical reference, syntax, config |
| Contributing | `docs/contributing/` | How to contribute docs, style guide |

### Adding a New Group

1. Create the folder: `docs/my-new-group/`
2. Create `docs/my-new-group/index.md`:

```yaml
---
layout: default
title: "My New Group"
nav_order: 6               # position in top-level nav
has_children: true
group_index: true          # shows as card on homepage
icon: "⚙️"
description: "What this group covers."
permalink: /docs/my-new-group/
---

# My New Group

Short introduction to this section.
```

3. Add child pages with `parent: "My New Group"` in their front matter.

### Navigation Hierarchy Diagram

```
Sidebar Navigation Tree
═══════════════════════

Home                          (index.md, nav_order: 1)
│
├── Getting Started           (docs/getting-started/index.md, nav_order: 2)
│   ├── Installation          (nav_order: 1, parent: "Getting Started")
│   ├── Quick Start           (nav_order: 2, parent: "Getting Started")
│   └── Project Structure     (nav_order: 3, parent: "Getting Started")
│
├── Guides                    (docs/guides/index.md, nav_order: 3)
│   ├── Creating Pages        (nav_order: 1, parent: "Guides")
│   ├── Linking Pages         (nav_order: 2, parent: "Guides")
│   └── Jekyll Front Matter   (nav_order: 3, parent: "Guides")
│
├── Reference                 (docs/reference/index.md, nav_order: 4)
│   ├── Jekyll Syntax         (nav_order: 1, parent: "Reference")
│   └── Front Matter Fields   (nav_order: 2, parent: "Reference")
│
└── Contributing              (docs/contributing/index.md, nav_order: 5)
    └── Style Guide           (nav_order: 1, parent: "Contributing")
```

---

## Jekyll Front Matter Quick Reference

```yaml
---
# ── Required ─────────────────────────────────────────
layout: default              # HTML wrapper template
title: "Page Title"          # Shown in nav, browser tab, and content header

# ── Navigation ───────────────────────────────────────
nav_order: 3                 # Sidebar position (lower = higher up)
parent: "Guides"             # Exact title of parent group page
has_children: true           # true = this page has child pages in sidebar
nav_exclude: false           # true = hide from sidebar (still accessible by URL)
permalink: /custom/url/      # Override default URL

# ── Metadata ─────────────────────────────────────────
description: "One-line summary."
last_modified_date: 2026-06-23

# ── Homepage Cards (group index pages only) ──────────
group_index: true            # Show as card on homepage
icon: "📖"                   # Card icon (emoji)
---
```

---

## Contributing

We welcome documentation contributions from everyone on the team.

### Quick Start

```bash
git checkout -b docs/<your-topic>
# create or edit files in docs/
git add .
git commit -m "docs: describe what you added or changed"
git push -u origin docs/<your-topic>
# open a pull request on GitHub
```

### Before You Open a PR

- [ ] Front matter is complete and correct
- [ ] File name is `lowercase-with-hyphens.md`
- [ ] Code blocks have language tags (` ```bash `, ` ```yaml `, etc.)
- [ ] Internal links use relative paths
- [ ] `last_modified_date` is updated to today
- [ ] Preview runs locally without errors

### Review and Merge

PRs are reviewed by any team member with write access. Merging to `main` automatically triggers a deploy. The live site updates within ~60 seconds.

---

## License

This project is released under the [MIT License](LICENSE).

---

*Powered by [Jekyll](https://jekyllrb.com) · Hosted on [GitHub Pages](https://pages.github.com) · Theme: [Just the Docs](https://just-the-docs.github.io/just-the-docs/)*
