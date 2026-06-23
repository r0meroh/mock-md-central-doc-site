---
layout: default
title: Jekyll Front Matter
parent: Guides
nav_order: 3
description: "Everything you need to know about the YAML block at the top of every page."
last_modified_date: 2026-06-23
---

# Jekyll Front Matter

Front matter is a YAML block at the very top of every Markdown file, enclosed between triple-dash (`---`) delimiters. Jekyll reads this block to control the page's layout, navigation, metadata, and more.

## Minimal Front Matter

```yaml
---
layout: default
title: My Page Title
---
```

## Full Front Matter Reference

```yaml
---
layout: default          # REQUIRED — which HTML template wraps this page
title: "Page Title"      # REQUIRED — shown in nav, browser tab, and <h1>
nav_order: 3             # Controls position in sidebar (lower number = higher up)
parent: "Guides"         # Makes this page a child of the named page
has_children: true       # Set to true if this page has child pages
nav_exclude: false       # Set to true to hide from sidebar navigation
description: "…"         # Short summary — used in SEO meta tags
last_modified_date: 2026-06-23   # Displayed as "Last updated" on the page
permalink: /custom/url/  # Override the default URL (optional)
---
```

## Navigation Hierarchy

The sidebar navigation is built from two front matter keys:

```
parent: "Getting Started"    ← name of the PARENT page's title
nav_order: 2                 ← position among siblings
```

**Example hierarchy:**

```
Getting Started   (nav_order: 2, no parent)
├── Installation  (nav_order: 1, parent: "Getting Started")
├── Quick Start   (nav_order: 2, parent: "Getting Started")
└── Structure     (nav_order: 3, parent: "Getting Started")
```

## Tips and Gotchas

- The `title` in front matter **must exactly match** what you use in `parent:` on child pages.
- `nav_order` accepts integers or floats (`nav_order: 2.5` inserts between 2 and 3).
- Omitting `nav_order` causes pages to sort alphabetically by title as a fallback.
- Setting `nav_exclude: true` hides a page from the sidebar but it is still accessible via its URL.
