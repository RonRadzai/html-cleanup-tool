# HTML Cleanup Tool

A lightweight, self-contained browser tool for stripping formatting noise from HTML without affecting content. Built for support and content teams who copy HTML between platforms and end up with a mess of inline styles, Office artifacts, and junk attributes.

No installation. No server. No dependencies.

**[Open the tool](https://ronradzai.github.io/html-cleanup-tool/)**

---

## What it does

Paste messy HTML into the Input box, choose a preset or configure individual rules, hit **Run Cleanup**, and copy the cleaned result. A changelog at the bottom shows exactly which rules fired on each run.

---

## What it never touches

Regardless of which preset or rules are enabled, the following are always preserved:

- All text content
- Links — `<a>` tags and their `href` values
- Images — `<img>` tags and their `src` attributes
- Document structure — headings, paragraphs, lists, tables and their data
- Semantic formatting — `<strong>`, `<em>`, `<u>`, etc.
- Anchor IDs — `id` on `<a>` tags is preserved even when id removal is enabled

> **This is not scorched earth.** Unlike pasting into Notepad (which strips everything down to raw text), this tool keeps your document structure completely intact. It removes formatting noise, not content.

---

## Presets

| Preset | Description |
|---|---|
| **Safe** | Recommended default. Removes inline styles, class attributes, MS Office markup, empty tags, and invisible characters. Very low risk. |
| **Aggressive** | All rules enabled including `aria-*` attributes. Best for heavily polluted HTML. Review output before using. |
| **Clear All** | Unchecks all rules so you can hand-pick exactly what to run. |

---

## Rule categories

### Attributes
- **Inline styles** — Strip all `style="..."` attributes
- **Class attributes** — Remove all `class="..."` attributes
- **data-* attributes** — Strip tracking and editor data attributes
- **id attributes** — Remove `id="..."` except on `<a>` anchors
- **lang= on inline elements** — Remove `lang="en-US"` injected by editors on spans and p tags
- **Presentational attributes** — Remove `align=`, `valign=`, `bgcolor=`, `cellpadding=`, `cellspacing=`, `border=` on tables
- **aria-* attributes** — Strip aria attributes injected by WYSIWYG editors
- **tabindex attributes** — Remove tabindex on non-interactive elements

### Tags
- **Empty `<p>` tags** — Remove `<p>` tags containing only whitespace or `&nbsp;`
- **Empty / bare `<span>` tags** — Remove spans with no attributes or content
- **`<font>` tags** — Unwrap legacy `<font>` elements, keep inner content
- **`<center>` tags** — Unwrap deprecated `<center>` elements, keep inner content
- **Duplicate `<br>` tags** — Collapse consecutive `<br>` into one
- **Redundant nested tags** — Collapse doubled `<strong><strong>`, `<em><em>` etc.
- **Normalize `<b>` / `<i>` tags** — Convert legacy `<b>` to `<strong>` and `<i>` to `<em>`
- **Bare wrapper `<div>` tags** — Unwrap `<div>` tags with no attributes

### Encoding & Invisible Characters
- **Zero-width spaces** — Remove invisible `&#8203;` and `\u200B` characters
- **Soft & non-breaking hyphens** — Remove `&shy;` and convert non-breaking hyphens from Word autocorrect
- **Smart quotes** — Normalize curly quotes to straight ASCII quotes
- **Extra `&nbsp;` chains** — Collapse runs of 3+ `&nbsp;` down to one

### MS Office & CMS Artifacts
- **MS Office markup** — Remove `<o:p>`, `mso-*` styles, `if/endif` comment blocks, `xmlns` attributes
- **HTML comments** — Remove all `<!-- ... -->` comments
- **Stray whitespace in tags** — Fix `<p >` with trailing space before `>`

### Whitespace
- **Normalize blank lines** — Collapse 3+ consecutive blank lines to two
- **Trailing whitespace** — Trim trailing spaces and tabs from each line

---

## Usage tips

- The **Changes Applied** bar shows exactly which rules fired so you always know what was modified.
- If your destination platform uses specific class names to style elements (callout boxes, code blocks, etc.), be careful with the **Class attributes** rule — those classes will be removed along with the junk ones.
- The **Smart quotes** rule converts curly quotes to straight ASCII. Leave it off if your content intentionally uses typographic quotes.
- The **aria-*** rule is only in Aggressive because some aria attributes are intentionally added for accessibility. Only enable it if you know the attributes were injected by an editor.
- Presets are just a starting point — you can enable or disable individual rules after applying one.
- Use the **Light / Dark** toggle in the top-right corner of the header to switch themes.

---

## Files

```
index.html   — the entire tool, self-contained
README.md
```
