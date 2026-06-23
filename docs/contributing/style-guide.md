---
layout: default
title: Style Guide
parent: Contributing
nav_order: 1
description: "Voice, tone, formatting, and structural conventions for all documentation."
last_modified_date: 2026-06-23
---

# Style Guide

Consistent documentation is easier to read, easier to maintain, and builds trust with readers. Follow these conventions in all documentation pages.

---

## Voice and Tone

- **Second-person, active voice.** Address the reader as "you": "Click **Save**", not "The user should click Save."
- **Present tense.** "Jekyll builds the site", not "Jekyll will build the site."
- **Concise.** One idea per sentence. Aim for sentences under 25 words.
- **Scannable.** Readers skim. Use headings, bullets, and tables over long prose paragraphs.

---

## Page Structure

Every page should follow this order:

1. **Front matter block** (`---` YAML block)
2. **Optional lead paragraph** — a single sentence describing the page (if the `description` front matter isn't enough)
3. **Body** — H2 sections, each covering one concept
4. **Next Step or See Also** section at the bottom — link to related pages

---

## Headings

- Use title case for H1 (`# My Page Title`) and sentence case for H2+ (`## My section heading`).
- Do not skip heading levels (H2 → H4). Keep the hierarchy clean.
- Each page has exactly one H1 (provided via `title` in front matter — do not add a redundant `# Title` in the body).

---

## Code

- Always specify the language on fenced code blocks.
- Use real, runnable examples. Avoid pseudocode.
- When showing commands, use `bash` or `sh` as the language tag.
- Inline code (backticks) for: file names, paths, command names, flag names, config keys, UI labels.

---

## UI Elements

Bold UI labels and button names: "Click **Save**", "Navigate to **Settings > Security**."

---

## Formatting Specifics

| Element | Convention |
|---|---|
| File names | `backtick code` |
| Folder names | `backtick code` with trailing `/` — e.g. `_layouts/` |
| Configuration keys | `backtick code` |
| Button / UI label | **Bold** |
| First use of a term | *Italic* |
| External link | Full URL, opens in same tab unless explicitly new-tab |

---

## Images and Diagrams

- Store images in `assets/images/`.
- Use descriptive `alt` text for accessibility.
- Keep screenshots up to date with the current UI.
- Prefer vector diagrams (SVG) over raster (PNG/JPG) for anything that might be zoomed.

---

## Callout Boxes

Use sparingly — a page full of warnings loses impact.

| Class | When to Use |
|---|---|
| `.callout-note` | Additional context that is helpful but not essential |
| `.callout-tip` | A shortcut or best practice |
| `.callout-warn` | Something the reader should be careful about |
| `.callout-danger` | An action that could cause data loss or breakage |
