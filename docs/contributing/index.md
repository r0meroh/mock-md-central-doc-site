---
layout: default
title: Contributing
nav_order: 5
has_children: true
group_index: true
icon: "🤝"
description: "Guidelines for contributing documentation, reviewing PRs, and maintaining quality."
permalink: /docs/contributing/
---

# Contributing

Documentation is a team effort. This section explains how to contribute new pages, edit existing ones, and get your changes reviewed and published.

## The Contribution Workflow

```
Fork / branch → Edit / create files → Commit → Push → Open PR → Review → Merge → Auto-deploy
```

## In This Section

- [Style Guide](./style-guide/) — Voice, tone, formatting conventions

## Quick Contribution Checklist

- [ ] Page has correct front matter (`layout`, `title`, `parent`, `nav_order`)
- [ ] File name is lowercase with hyphens only (`my-topic.md`)
- [ ] Headings are hierarchical (H2 under H1, H3 under H2)
- [ ] Code blocks have language tags for syntax highlighting
- [ ] All internal links use relative paths
- [ ] `last_modified_date` is updated to today's date
- [ ] Preview runs locally without errors (`bundle exec jekyll serve`)
