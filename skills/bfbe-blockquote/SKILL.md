---
name: bfbe-blockquote
description: "Use when placing, wiring or styling BFB Blockquote (`bfbe-blockquote`): a quotation with its source, in the markup HTML gives one: a figure, the words in a blockquote, the source in a figcaption and the title of a work in cite, with the source's address on the blockquote's cite attribute. Read before writing its settings."
---

# BFB Blockquote (`bfbe-blockquote`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.1.0 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-blockquote.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/blockquote/

## What it is
A quotation with its source, in the markup HTML gives one: a figure, the words in a blockquote, the source in a figcaption and the title of a work in cite, with the source's address on the blockquote's cite attribute. Four looks, an optional quote mark or icon and a photo beside the name; every text accepts dynamic data, and the element runs in a query loop. A pull quote, words that already appear on the page, is hidden from screen readers. No script.

**Not for:** Pull quote is not for words that appear nowhere else on the page, since a pull quote is hidden from screen readers. Each Blockquote holds one quotation, with no star rating, and writes no review markup for search engines.

**Costs a page:** CSS 0.59 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** no · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Quote (`bfbeQuote`)
- `quote` (textarea) **Quote**: placeholder Good design is as little design as possible.; dynamic data accepted. Type the words. They accept dynamic data, and a blank line starts a new paragraph. Left empty, nothing shows on the page.
- `kind` (select) **Kind**: options: `quote` Quote (default), `pull` Pull quote. Quote is the default. Choose Pull quote for words that already appear on the page: they are set larger and screen readers skip them, having read them in the text.

### Source (`bfbeSource`)
- `author` (text) **Name**: dynamic data accepted. Type who said it. It accepts dynamic data.
- `role` (text) **Role**: dynamic data accepted. Type a job title or a company. It shows under the name in smaller text and accepts dynamic data.
- `work` (text) **Title of the source**: dynamic data accepted. Type the name of the book, article, talk or review. It shows in italics beside the role.
- `url` (text) **Source address**: placeholder https://; dynamic data accepted. Paste the source's address. With a Title of the source, the title links to it.
- `photo` (image) **Photo**. Choose a picture to show round, beside the name. Photo size sets it, 48px by default.
Styling, in the schema file: `photoSize`.

### Look (`bfbeLook`)
- `layout` (select) **Layout**: options: `bar` Bar at the side (default), `rules` Rules above and below, `centered` Centred, `plain` Plain. Bar at the side is the default. Choose Rules above and below, Centred or Plain instead.
Styling, in the schema file: `lineColor`, `lineWidth`, `gap`.

### Quote mark (`bfbeMark`)
- `mark` (select) **Show**: options: `none` None (default), `glyph` Quotation mark, `icon` Icon. None is the default. Choose Quotation mark for the typographic one, or Icon and pick any icon from the library.
- `markIcon` (icon) **Icon**: only when `mark` is `icon`
Styling, in the schema file: `markSize`, `markColor`.

### Text (`bfbeText`)
Styling only, every key in the schema file: `quoteTypography`, `authorTypography`, `roleTypography`.

## What it guarantees for accessibility (do not undo)
- The element is a figure holding a blockquote with the words and a figcaption with the source; the title of a work sits in a cite element, and Source address goes on the blockquote's cite attribute.
- A blank line in the quote makes a new paragraph element, so a long quote is read as paragraphs.
- The quotation mark and the icon are aria-hidden, so a screen reader reads the words and not the mark.
- The photo has an empty alt, since the name beside it already says who it is.
- Kind set to Pull quote puts aria-hidden on the whole figure on the page, not in the builder, because a screen reader has already read those words in the text.
- With a Source address, the Title of the source is a real link.
<!-- bfbe:generated:end -->

## Rendered DOM

On the front end, the Rules look with the quotation mark, a photo, a role and a linked source in two paragraphs (fixture `fixture-blockquote`):

```html
<figure id="brxe-{id}" class="brxe-bfbe-blockquote bfbe-quote bfbe-quote--rules">
  <span class="bfbe-quote__mark bfbe-quote__mark--glyph" aria-hidden="true">&#8220;</span>
  <blockquote class="bfbe-quote__text" cite="https://example.com/roasting">
    <p>Eight minutes, a slow ramp, and the day we threw out a whole batch.</p>
    <p>That is roasting dark.</p>
  </blockquote>
  <figcaption class="bfbe-quote__source">
    <img class="bfbe-quote__photo" src="…-150x150.png" alt="" loading="lazy" decoding="async" width="150" height="150">
    <span class="bfbe-quote__who">
      <span class="bfbe-quote__author">Tomas Reyes</span>
      <span class="bfbe-quote__meta">
        <span class="bfbe-quote__role">Head roaster</span>
        <cite class="bfbe-quote__work"><a href="https://example.com/roasting">Why we stopped roasting dark</a></cite>
      </span>
    </span>
  </figcaption>
</figure>
```

- Root `.bfbe-quote`, a `<figure>` on the page and a `<div>` in the builder's canvas. **Layout** (`layout`) adds `bfbe-quote--bar`, `--rules`, `--centered` or `--plain`; `kind: "pull"` adds `bfbe-quote--pull` and, on the front end only, `aria-hidden="true"` on the figure.
- **Show** (`mark`): `glyph` renders `span.bfbe-quote__mark.bfbe-quote__mark--glyph` holding the curly opening mark; `icon` renders `span.bfbe-quote__mark` around Bricks' icon markup (an `<i>` for a font icon, an `<svg>` for an SVG). Both are `aria-hidden="true"` and come before the blockquote.
- **Quote** (`quote`) is escaped, then run through `wpautop()`: a blank line starts a new `<p>`, a single line break becomes `<br>`. **Source address** (`url`) goes on the blockquote's `cite` attribute whenever it is set.
- The `<figcaption>` renders only when Name, Role, Title of the source or Photo is set. The photo leads, with `alt=""`; `__who` holds `__author`, then `__meta` with `__role` and `cite.bfbe-quote__work`, a link only when `url` is set too. With Bricks' lazy load on, the photo's `src` is a placeholder and the address sits in `data-src`.
- The root is a flex column, `gap` 16px (the pack's `--bfbe-gap`), margin 0. The blockquote loses the browser's and Bricks' margin, padding, border and quotes, and is set at 1.25em with line-height 1.5 (1.6em and 1.35 on a pull quote). Bricks gives every `<figcaption>` its image-caption look (light colour, .9em, a 1em margin, centred); `.bfbe-quote__source` resets it to `color: inherit`, 1em, margin 0, `text-align: start`, a flex row with an 8px gap.
- Looks: `--bar` draws `border-inline-start` with `padding-inline-start: 1.25em`; `--rules` draws `border-block` with `padding-block: 1.25em`; both use `var(--bfbe-quote-line-width) solid var(--bfbe-quote-line)` (3px, the pack's accent). `--centered` sets `align-items: center` and `text-align: center` on the root and centres the source.
- Where controls write: **Photo size** (`photoSize`) sets `--bfbe-quote-photo` (48px), **Line colour** (`lineColor`) `--bfbe-quote-line`, **Line width** (`lineWidth`) `--bfbe-quote-line-width` and **Gap** (`gap`) the root's `gap`, all on the root. **Size** (`markSize`) and **Colour** (`markColor`) write `font-size` and `color` on `.bfbe-quote__mark`. `quoteTypography` writes to `.bfbe-quote__text`, `authorTypography` to `.bfbe-quote__author`, `roleTypography` to `.bfbe-quote__meta` (role and title together).
- Empty **Quote**: nothing at all on the page; in the canvas a `div.bfbe-empty` with the notice "Enter the quote."

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing. No script, so nothing needs starting after AJAX.

- **A pull quote and its source text.** Nothing links the two: `kind: "pull"` only hides the figure from screen readers. The words must already be in the page's own text, in a text element nearby, or a screen reader user never hears them.
- **Testimonials from posts.** Set `hasLoop: true` and a `query` (for example `{"objectType": "post", "post_type": ["testimonial"]}`) on the Blockquote itself, and it repeats once per post. Give the texts dynamic tags: `quote` a plain-text field or `{post_excerpt}`, `author` `{post_title}`, `role` and `work` fields, `url` a link field. **Photo** (`photo`) takes Bricks' image picker, such as `{"useDynamicData": "{featured_image}", "size": "thumbnail"}`. To wrap each quote in a card, loop a Block around it instead.
- **By class, never by id.** Put a class in `_cssClasses` for CSS that reaches several quotes, such as `.reviews .bfbe-quote__author`; component instances share ids and loop items repeat them.

## Verified patterns

**A testimonial with the mark, a photo and the linked write-up** (demo page `demo-bfb-blockquote`, Margaret Hale's quote). Rules above and below in a hairline, the quotation mark in the accent, a 56px photo, and the title of the project's write-up linked to it. `photo.id` 3957 is the demo site's image and its addresses are made generic: use an attachment id and URLs from the target site's media library.

```json
{
  "name": "bfbe-blockquote",
  "settings": {
    "quote": "We stayed in the flat the whole nine weeks. They moved one room at a time and swept up every evening.\n\nA year on, it is the same flat, and we cannot believe how much light it has.",
    "author": "Margaret Hale",
    "role": "Hartley House, fourth floor",
    "work": "One room, and not a wall moved",
    "url": "https://example.com/projects/hartley-house",
    "photo": { "id": 3957, "filename": "bfbe-demo-kestrel-camel.jpg", "size": "thumbnail", "url": "https://example.com/wp-content/uploads/2026/09/bfbe-demo-kestrel-camel-150x150.jpg", "full": "https://example.com/wp-content/uploads/2026/09/bfbe-demo-kestrel-camel.jpg" },
    "photoSize": "56px",
    "layout": "rules",
    "mark": "glyph",
    "markColor": { "hex": "#6e44ff" },
    "lineColor": { "hex": "#e9ecf1" },
    "lineWidth": "1px",
    "quoteTypography": { "font-size": "24px", "line-height": "1.45", "color": { "hex": "#101828" } },
    "roleTypography": { "color": { "hex": "#475467" } }
  }
}
```

**A pull quote beside the article it repeats** (feature page `feature-bfb-blockquote-pull-quotes`, the website's "Pull quotes" still). The sentence is the article's own, so `kind: "pull"` hides the copy from screen readers. A 4px bar in the accent, 24px between its parts, the words large and bold. Place it next to the Text element that holds the sentence.

```json
{
  "name": "bfbe-blockquote",
  "settings": {
    "quote": "The budget went on plaster, oak and light.",
    "kind": "pull",
    "layout": "bar",
    "lineColor": { "hex": "#6e44ff" },
    "lineWidth": "4px",
    "gap": "24px",
    "quoteTypography": { "font-size": "38px", "line-height": "1.2", "font-weight": "700", "letter-spacing": "-0.02em", "color": { "hex": "#6e44ff" } }
  }
}
```

**Centred, with an icon for the mark** (fixture page `fixture-blockquote`, "Centred, icon mark, coloured"). `mark: "icon"` needs `markIcon`; **Colour** (`markColor`) tints it.

```json
{ "name": "bfbe-blockquote", "settings": { "quote": "One room, and not a wall moved.", "author": "Hartly House", "layout": "centered", "mark": "icon", "markIcon": { "library": "themify", "icon": "ti-quote-left" }, "markColor": { "hex": "#6e44ff" } } }
```

**A short quote with the bar** (demo page `demo-bfb-blockquote`, Daniel Okafor's quote). The bar is the default look, so `layout` is left out; `lineColor` sets the bar's colour. For words from dynamic data, the fixture page `fixture-blockquote` renders `"quote": "{post_title}"` with `"author": "{site_title}"` on a page.

```json
{ "name": "bfbe-blockquote", "settings": { "quote": "They told us what not to change, which was most of it.", "author": "Daniel Okafor", "role": "Beckett Road", "lineColor": { "hex": "#6e44ff" }, "quoteTypography": { "font-size": "19px", "color": { "hex": "#101828" } }, "roleTypography": { "color": { "hex": "#475467" } } } }
```

## Gotchas

- **The quote is plain text.** Typed HTML is escaped, so `<em>` prints as characters; a blank line makes a paragraph and one line break gives `<br>`, nothing more. A dynamic tag that returns HTML shows its tags too: `{post_content}` printed `<p class="wp-block-paragraph">` as text. Feed it `{post_excerpt}` or a plain-text field. <!-- src: plugins/bfb-elements/elements/blockquote.php:269 ; plugins/bfb-elements/elements/blockquote.php:310 ; plugins/bfb-elements/includes/abstract-element.php:1276 -->
- **The quote comes out in Georgia.** Bricks' own stylesheet sets `font-family: georgia, "Times New Roman", times, serif` on every `blockquote`, and the element resets the size, margin, padding and border but not the font: the fixture and the demo both computed Georgia. Set `font-family` in `quoteTypography` for the site's typeface. <!-- src: src/elements/blockquote/blockquote.css:13 ; wp-content/themes/bricks/assets/css/frontend-layer.min.css (the blockquote rule) -->
- **No quote, no element.** With `quote` empty the page gets nothing, not even the name or the photo; the canvas shows "Enter the quote." <!-- src: plugins/bfb-elements/elements/blockquote.php:274 ; plugins/bfb-elements/includes/abstract-element.php:549 -->
- **Source address alone shows nothing.** `url` always goes on the blockquote's `cite` attribute, which browsers do not display; it becomes a visible link only on **Title of the source** (`work`). It passes through `esc_url()`, so `example.com/x` comes out as `http://example.com/x`: type the full `https://` address. <!-- src: plugins/bfb-elements/elements/blockquote.php:294 ; plugins/bfb-elements/elements/blockquote.php:332 -->
- **A pull quote hides its link from screen readers, not from the keyboard.** `aria-hidden` covers the whole figure, so a linked title inside it is still reached by Tab yet announced by nothing. Give a pull quote no `url`. <!-- src: plugins/bfb-elements/elements/blockquote.php:284 ; plugins/bfb-elements/elements/blockquote.php:332 -->
- **The canvas is not the page.** In the builder the root is a `<div>` and a pull quote carries no `aria-hidden`, so the canvas stays selectable. Check the figure and the hidden state on the front end. <!-- src: plugins/bfb-elements/elements/blockquote.php:286 ; plugins/bfb-elements/elements/blockquote.php:297 ; plugins/bfb-elements/includes/abstract-element.php:430 -->
- **An icon mark needs its icon.** `mark: "icon"` without `markIcon` draws no mark at all. <!-- src: plugins/bfb-elements/elements/blockquote.php:304 -->
- **Size has two defaults.** **Size** (`markSize`) left empty means 5em for the quotation mark and 3em for an icon, both of the element's font size. The glyph's box is cut to .45em tall, the part of the mark that shows, so **Gap** (`gap`) measures from there to the quote. <!-- src: src/elements/blockquote/blockquote.css:17 ; src/elements/blockquote/blockquote.css:19 ; plugins/bfb-elements/elements/blockquote.php:209 -->
- **Line colour and Line width act on two looks.** They draw the bar and the rules only; the panel hides them for `centered` and `plain`. Unset, the line is 3px in the pack's accent colour. <!-- src: plugins/bfb-elements/elements/blockquote.php:153 ; src/elements/blockquote/blockquote.css:4 ; src/elements/blockquote/blockquote.css:33 -->
- **Role and source are always dimmed.** `.bfbe-quote__meta` has `opacity: .75` and `font-size: .9em`, so a colour set in `roleTypography` shows at 75% opacity over the background. <!-- src: src/elements/blockquote/blockquote.css:27 -->
- **The photo is a 150px file.** Without a `size` in `photo`, it uses WordPress's thumbnail size, so a **Photo size** (`photoSize`) above 150px stretches it. Set `"size": "medium"` in `photo` for a larger photo. <!-- src: plugins/bfb-elements/elements/blockquote.php:295 ; plugins/bfb-elements/includes/abstract-element.php:1397 -->
- **The layout key is `centered`.** The panel says Centred, the stored value is `centered`; any value outside `bar`, `rules`, `centered` and `plain` renders the bar. <!-- src: plugins/bfb-elements/elements/blockquote.php:31 ; plugins/bfb-elements/elements/blockquote.php:266 -->

## Never do

- Do not set `kind: "pull"` on words that appear nowhere else on the page; use the default `quote`.
- Do not give a pull quote a `url`.
- Do not put HTML in `quote`, `author`, `role` or `work`, or feed `quote` a tag that returns HTML such as `{post_content}`.
- Do not rely on `url` alone to show the source; set `work` for a visible link.
- Do not set `mark: "icon"` without `markIcon`, or `markSize` and `markColor` with `mark` at `none`.
- Do not set `lineColor` or `lineWidth` on `centered` or `plain`.
- Do not judge the figure or a pull quote's hidden state from the canvas, or target a quote by `_cssId`.
- Do not write `layout: "centred"`; the key is `centered`.
