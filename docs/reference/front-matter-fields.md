---
layout: default
title: Front Matter Fields
parent: Reference
nav_order: 2
description: "Complete reference for every supported front matter key."
last_modified_date: 2026-06-23
---

# Front Matter Fields

Complete reference for every front matter key supported by this site.

## Required Fields

### `layout`

**Type:** string  
**Default:** none (must be set)

The HTML layout template to use. Almost always `default`.

```yaml
layout: default
```

---

### `title`

**Type:** string  
**Default:** none (must be set)

The page title. Appears in the browser tab, sidebar navigation, and as the visible `<h1>` in the content header area.

```yaml
title: "Getting Started"
```

---

## Navigation Fields

### `nav_order`

**Type:** integer or float  
Controls the position of this page in the sidebar. Lower numbers appear higher. Pages without `nav_order` sort alphabetically after ordered pages.

```yaml
nav_order: 3
```

---

### `parent`

**Type:** string  
The **exact** `title` value of this page's parent. Makes this page a child item in the sidebar under the named parent.

```yaml
parent: "Getting Started"
```

---

### `has_children`

**Type:** boolean (default: `false`)  
Set to `true` on group index pages that have child pages. Enables the expand/collapse arrow in the sidebar.

```yaml
has_children: true
```

---

### `nav_exclude`

**Type:** boolean (default: `false`)  
Set to `true` to hide this page from sidebar navigation. The page is still accessible directly by URL.

```yaml
nav_exclude: true
```

---

### `permalink`

**Type:** string  
Override the default URL for this page.

```yaml
permalink: /custom/path/
```

---

## Metadata Fields

### `description`

**Type:** string  
A short summary (1–2 sentences). Used in SEO `<meta name="description">` tags and displayed below the page title.

```yaml
description: "Step-by-step guide to configuring SAML 2.0 SSO."
```

---

### `last_modified_date`

**Type:** date (ISO 8601: `YYYY-MM-DD`)  
Displayed at the top of the page as "Last updated: Month Day, Year".

```yaml
last_modified_date: 2026-06-23
```

---

## Group Index Fields

These fields are only meaningful on group `index.md` pages.

### `group_index`

**Type:** boolean  
Marks a page as a group landing page. Used by the home layout to render it as a doc-group card.

```yaml
group_index: true
```

---

### `icon`

**Type:** string (emoji or Unicode)  
Icon displayed on the doc-group card on the homepage.

```yaml
icon: "🚀"
```
