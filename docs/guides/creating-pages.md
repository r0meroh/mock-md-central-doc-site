---
layout: default
title: Creating Pages
parent: Guides
nav_order: 1
description: "How to add new Markdown documentation pages to the site."
last_modified_date: 2026-06-23
---

# Creating Pages

Adding a new documentation page is a three-step process.

## Step 1 — Choose a Group

Pages live inside `docs/<group-name>/`. Pick the group that best fits your content, or create a new group folder:

```
docs/
├── getting-started/    ← installation, setup
├── guides/             ← how-to articles
├── reference/          ← API / config reference
└── contributing/       ← contributor guidelines
```

To create a new group, add a new folder and an `index.md` inside it (see the existing groups for examples).

---

## Step 2 — Create the Markdown File

Create a `.md` file in the appropriate folder. File names become part of the URL:

| File path | URL |
|---|---|
| `docs/guides/my-topic.md` | `/docs/guides/my-topic/` |
| `docs/reference/api.md` | `/docs/reference/api/` |

**Naming conventions:**
- Use lowercase letters and hyphens only: `my-topic.md` ✅
- No spaces or uppercase: `My Topic.md` ❌

---

## Step 3 — Add Front Matter

Every page must start with a YAML front matter block:

```yaml
---
layout: default
title: "My Topic"        # displayed in browser tab and as page heading in nav
parent: Guides           # must match the `title` of the parent index page
nav_order: 6             # controls position in the sidebar (lower = higher up)
description: "One-line summary of this page."
last_modified_date: 2026-06-23
---
```

After the closing `---`, write your Markdown content normally.

---

## Complete Example

```markdown
---
layout: default
title: Configure SSO
parent: Guides
nav_order: 4
description: "Step-by-step guide to setting up Single Sign-On."
last_modified_date: 2026-06-23
---

# Configure SSO

This guide walks you through configuring SAML 2.0 SSO.

## Prerequisites
- Admin access to your Identity Provider
- Admin access to DocHub settings

## Steps

1. Log in as an administrator.
2. Navigate to **Settings > Authentication > SSO**.
3. Enter your IdP metadata URL.
4. Click **Save and Test**.
```

---

## Verify Your Page

Run the site locally and confirm your page appears in the sidebar and is accessible at the expected URL:

```bash
bundle exec jekyll serve --livereload
# Open http://localhost:4000/docs/guides/configure-sso/
```
