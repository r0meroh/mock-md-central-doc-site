---
layout: default
title: Guides
nav_order: 3
has_children: true
group_index: true
icon: "📖"
description: "Step-by-step guides for writing, linking, and organizing documentation pages."
permalink: /docs/guides/
---

# Guides

Practical walkthroughs for the most common documentation tasks.

## In This Section

- [Creating Pages](./creating-pages/) — Add new Markdown pages to any doc group
- [Linking Between Pages](./linking-pages/) — Cross-link pages using relative URLs
- [Jekyll Front Matter](./jekyll-front-matter/) — Master the YAML front matter block

## The Golden Rule

Every documentation file is a plain Markdown (`.md`) file with a YAML front matter block at the top. You don't need to know HTML or Ruby — just Markdown and a handful of front matter keys.

```markdown
---
layout: default
title: My New Page
parent: Guides
nav_order: 5
---

# My New Page

Your content goes here.
```
