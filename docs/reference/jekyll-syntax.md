---
layout: default
title: Jekyll Syntax
parent: Reference
nav_order: 1
description: "Markdown extensions and Jekyll-specific syntax supported by this site."
last_modified_date: 2026-06-23
---

# Jekyll Syntax

This site uses **kramdown** (GitHub-Flavored Markdown superset) with **Rouge** syntax highlighting. Below is a reference for all supported syntax.

---

## Headings

```markdown
# H1 — Page Title (use once per page, via front matter `title`)
## H2 — Major Section (gets a divider line)
### H3 — Subsection
#### H4 — Minor heading
```

---

## Text Formatting

```markdown
**Bold text**
*Italic text*
~~Strikethrough~~
`inline code`
[Link text](./target-page/)
![Alt text](/assets/images/filename.png)
```

---

## Blockquotes

```markdown
> This is a blockquote. Use it for important notes or quotes.
```

> This is a blockquote. Use it for important notes or quotes.

---

## Callout Boxes (Custom Classes)

Apply CSS classes using kramdown's block attribute syntax `{: .class-name}`:

```markdown
> **Note:** This is an informational callout.
{: .callout .callout-note}

> **Tip:** This is a helpful tip.
{: .callout .callout-tip}

> **Warning:** Pay attention to this.
{: .callout .callout-warn}

> **Danger:** This action is destructive.
{: .callout .callout-danger}
```

---

## Code Blocks

Fenced code blocks with optional language for syntax highlighting:

````markdown
```bash
git commit -m "feat: add new doc page"
```

```yaml
layout: default
title: My Page
```

```python
def hello():
    print("Hello, DocHub!")
```
````

Supported language tags: `bash`, `sh`, `yaml`, `json`, `python`, `javascript`, `typescript`, `ruby`, `html`, `css`, `markdown`, `diff`, `sql`, and [many more](https://rouge-ruby.github.io/docs/file.Languages.html).

---

## Tables

```markdown
| Column A | Column B | Column C |
|---|---|---|
| Cell 1 | Cell 2 | Cell 3 |
| Cell 4 | Cell 5 | Cell 6 |
```

| Column A | Column B | Column C |
|---|---|---|
| Cell 1 | Cell 2 | Cell 3 |
| Cell 4 | Cell 5 | Cell 6 |

Alignment:

```markdown
| Left | Center | Right |
|:---|:---:|---:|
| text | text | text |
```

---

## Lists

```markdown
- Unordered item
- Another item
  - Nested item (indent 2 spaces)

1. Ordered item
2. Second item
   1. Nested ordered (indent 3 spaces)
```

**Task lists:**

```markdown
- [x] Completed task
- [ ] Pending task
- [ ] Another pending task
```

---

## Liquid Template Tags

Jekyll supports [Liquid](https://shopify.github.io/liquid/) templating inside Markdown:

{% raw %}
```liquid
{{ site.title }}                          ← outputs site title from _config.yml
{{ page.title }}                          ← current page title
{{ '/path/to/file' | relative_url }}      ← safe relative URL
{{ page.date | date: "%B %d, %Y" }}       ← formatted date

{% if page.has_children %}…{% endif %}    ← conditional block
{% for item in site.pages %}…{% endfor %} ← loop
{% include filename.html %}               ← embed a partial
```
{% endraw %}

---

## Definition Lists (kramdown extension)

```markdown
Term
: Definition of the term.

Another term
: Another definition.
```

---

## Footnotes (kramdown extension)

```markdown
This sentence has a footnote.[^1]

[^1]: This is the footnote text.
```
