---
layout: default
title: Linking Between Pages
parent: Guides
nav_order: 2
description: "How to cross-link documentation pages using relative and absolute URLs."
last_modified_date: 2026-06-23
---

# Linking Between Pages

DocHub pages can be linked to each other using standard Markdown links.

## Relative Links (Recommended)

Relative links stay valid even if the site moves to a different base URL.

```markdown
<!-- From docs/guides/my-page.md -->

See [Installation](../getting-started/installation/) for setup instructions.
See [API Reference](../reference/jekyll-syntax/) for syntax details.
See [another page in this group](./other-guide/) for more.
```

### Rules for Relative Paths

| You are in | Target | Link |
|---|---|---|
| `docs/guides/` | Same group | `./target-page/` |
| `docs/guides/` | Different group | `../reference/target-page/` |
| `docs/guides/` | Homepage | `../../` |
| `docs/guides/` | Group index | `../getting-started/` |

---

## Linking to Headings (Anchors)

Add `#heading-slug` to link directly to a section on a page. Jekyll auto-generates anchor IDs from headings by lowercasing and replacing spaces with hyphens.

```markdown
[Jump to Step 2](#step-2--create-the-markdown-file)
[See Prerequisites](./installation/#prerequisites)
```

**How slugs are generated:**

| Heading | Anchor |
|---|---|
| `## Prerequisites` | `#prerequisites` |
| `## Step 1 — Install Ruby` | `#step-1--install-ruby` |
| `## My Section (Advanced)` | `#my-section-advanced` |

---

## Linking to External Resources

```markdown
Visit the [Jekyll documentation](https://jekyllrb.com/docs/) for more.
```

Use `{:target="_blank"}` to open in a new tab (requires kramdown):

```markdown
[Jekyll docs](https://jekyllrb.com/docs/){:target="_blank"}
```

---

## Linking to Images

Place images in `assets/images/` and reference them with a relative path from the site root:

```markdown
![Architecture diagram](/assets/images/architecture.png)
```

Or use the `relative_url` Liquid filter to ensure the path is always correct:

```liquid
![Diagram]({{ '/assets/images/diagram.png' | relative_url }})
```
