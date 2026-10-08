---
name: bfbe-price-list
description: "Use when building a café or restaurant menu, a salon or studio service list, or any list of prices with BFB Price List (`bfbe-price-list`): rows of title, description and price joined by a dotted leader, with an optional image, link, struck-through original price and highlighted rows. Read before writing its settings."
---

# BFB Price List (`bfbe-price-list`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-price-list.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/price-list/

## What it is
A list of menu or service items, each with a title, description, price, optional image, optional struck-through original price and an optional link. A leader line, dotted by default, runs from the title to the price, and any row can be highlighted with its own styling group. Every text field takes dynamic data, and the list can run a query loop.

**Not for:** Each row holds one title, one price and an optional original price, so plans compared across several features need a table with column headings.

**Costs a page:** CSS 0.64 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** no · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Items (`bfbeItems`)
- `items` (repeater) **Items**. One row per item, with Title, Description, Price, Original price, Image, Link and Highlight this item. The text fields accept dynamic data. A row with nothing filled in is skipped.
- `leader` (select) **Leader line**: options: `dots` Dotted (default), `line` Solid, `none` None. The line from title to price. Dotted is the default, with Solid or None as the alternatives. Line colour, Line thickness and Leader offset, 25% by default, adjust it.
Styling, in the schema file: `leaderColor`, `leaderWidth`, `leaderOffset`.

### Item layout (`bfbeLayout`)
- `divided` (checkbox) **Line between items**. Off by default. Tick it to draw a divider between rows, with its own Divider colour and Divider thickness, 1px by default.
Styling, in the schema file: `itemGap`, `dividerColor`, `dividerWidth`, `itemPadding`, `itemBackground`, `itemBorder`.

### Title (`bfbeTitle`)
Styling only, every key in the schema file: `titleTypography`, `titleHoverColor`.

### Description (`bfbeDesc`)
Styling only, every key in the schema file: `descTypography`, `descGap`.

### Price (`bfbePrice`)
Styling only, every key in the schema file: `priceTypography`, `originalTypography`, `priceBackground`, `pricePadding`, `priceBorder`.

### Image (`bfbeImage`)
Styling only, every key in the schema file: `imageSize`, `imageBorder`, `imageGap`.

### Highlighted items (`bfbeHighlight`)
Styling only, every key in the schema file: `highlightBackground`, `highlightBorder`, `highlightPadding`, `highlightShadow`, `highlightTitleTypography`, `highlightDescTypography`, `highlightPriceTypography`, `highlightOriginalColor`, `highlightLeaderColor`, `highlightImageSize`, `highlightImageBorder`.

## What it guarantees for accessibility (do not undo)
- The list is a ul with role list and each row is an li, so screen readers can announce it as a list.
- The leader line is aria-hidden, so a screen reader reads each title and then its price without the dots.
- A title with a Link becomes a real anchor that shows an underline on hover and on keyboard focus.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<ul class="bfbe-price-list bfbe-price-list--leader-dots bfbe-price-list--divided" role="list">
  <li class="bfbe-price-list__item bfbe-price-list__item--highlight">
    <img class="bfbe-price-list__img" src="beans.jpg" alt="" loading="lazy" decoding="async">
    <div class="bfbe-price-list__body">
      <div class="bfbe-price-list__head">
        <a class="bfbe-price-list__title" href="/shop/beans/">Beans, 250 g</a>
        <span class="bfbe-price-list__price">
          <span class="bfbe-price-list__leader" aria-hidden="true"></span>
          <s class="bfbe-price-list__original">£11.00</s>
          <span class="bfbe-price-list__amount">£9.50</span>
        </span>
      </div>
      <p class="bfbe-price-list__desc">Ground for your machine, free.</p>
    </div>
  </li>
</ul>
```

- The root carries one mode class, `bfbe-price-list--leader-dots`, `--leader-line` or `--leader-none`, and `bfbe-price-list--divided` while **Line between items** (`divided`) is on.
- Each repeater row is an `li.bfbe-price-list__item`, a flex row of image then body. **Highlight this item** (`highlight`) adds `bfbe-price-list__item--highlight`.
- Parts appear when filled: the `<img>` with an image, an `<a>` title when the row has both Link and Title (a `<span>` otherwise), the price box with a price or an original price, the `<p>` with a description (its newlines become `<br>`).
- A row with no title, description, price, original price or image is skipped, and so is a row that is not an object.
- `.bfbe-price-list__price` grows to fill the head and holds the leader, the struck `<s>` original and `.bfbe-price-list__amount`, which keeps its full width.
- The leader is an empty span whose bottom border is the line, as tall as the price and lifted by `--bfbe-pl-leader-y`. With `leader: "none"` it stays as a borderless spacer, so the price still sits at the end.
- Where styling lands: `priceTypography` on `.bfbe-price-list__price` (the leader inherits it); `priceBackground`, `pricePadding` and `priceBorder` on `.bfbe-price-list__amount`; `itemPadding`, `itemBackground`, `itemBorder` and `imageGap` on `.bfbe-price-list__item`; `imageBorder` on `.bfbe-price-list__img`; `titleHoverColor` on `a.bfbe-price-list__title` at `:hover` and `:focus-visible`.
- Custom properties on the root: `--bfbe-pl-gap` (`itemGap`), `--bfbe-pl-img` (`imageSize`, 72px square, `object-fit: cover`), `--bfbe-pl-leader`, `--bfbe-pl-leader-width`, `--bfbe-pl-leader-y` (25%), `--bfbe-pl-divider`, `--bfbe-pl-divider-width` (1px).
- `highlightImageSize` and `highlightLeaderColor` set those same properties on the highlighted `li`, which shadows the root's value for that row.
- The divider is a `border-block-start` on every row after the first, with `padding-block-start` equal to the gap.
- No script, no `data-bfbe-*` attributes, no state classes: the server's markup is final. With no rows the page gets nothing and the canvas shows an "Add an item." notice.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing.

## Verified patterns

### Café menu with a highlighted row and a sale price

From the demo page `demo-bfb-price-list` (its second list, trimmed to three rows). A pale dotted leader; one row highlighted on the accent with white title, description and price; one row with an original price struck through. The demo's `dividerColor` is left out, because without `divided` it draws nothing.

```json
{
  "name": "bfbe-price-list",
  "settings": {
    "leader": "dots",
    "leaderColor": { "hex": "#e9ecf1" },
    "highlightBackground": { "hex": "#6e44ff" },
    "highlightTitleTypography": { "color": { "hex": "#ffffff" } },
    "highlightDescTypography": { "color": { "hex": "#ffffff" } },
    "highlightPriceTypography": { "color": { "hex": "#ffffff" } },
    "items": [
      { "title": "Batch brew", "description": "Whatever is on that morning.", "price": "£2.80" },
      { "title": "V60, single origin", "description": "Ethiopia Guji, washed. Changes weekly.", "price": "£4.20", "highlight": true },
      { "title": "Beans, 250 g", "description": "Ground for your machine, free.", "price": "£9.50", "originalPrice": "£11.00" }
    ]
  }
}
```

### Service list with photos, a link and dividers

From the fixture page `fixture-price-list` (FREE: Price List). A solid leader, dividers between rows, a thumbnail per row, a linked first title and a two-line description. The image `id` is the development site's: use an attachment from the target site's media library.

```json
{
  "name": "bfbe-price-list",
  "settings": {
    "leader": "line",
    "divided": true,
    "items": [
      {
        "title": "Cut and finish",
        "description": "Consultation included.\nAllow 45 minutes.",
        "price": "£45",
        "image": { "id": 22, "size": "thumbnail" },
        "link": { "type": "external", "url": "https://example.com/cut" }
      },
      {
        "title": "Colour",
        "description": "Full head.",
        "price": "£80",
        "originalPrice": "£95",
        "image": { "id": 22, "size": "thumbnail" }
      }
    ]
  }
}
```

### Menu fed by a query loop

Built from the schema, since no demo or fixture page loops a Price List; rendered on the development site, one list per post. Swap `post` for the menu's post type and `{cf_price}` for the custom field that holds the price.

```json
{
  "name": "bfbe-price-list",
  "settings": {
    "hasLoop": true,
    "query": { "objectType": "post", "post_type": ["post"], "posts_per_page": 12 },
    "items": [
      {
        "title": "{post_title}",
        "description": "{post_excerpt}",
        "price": "{cf_price}",
        "link": { "type": "meta", "useDynamicData": "{post_url}" }
      }
    ]
  }
}
```

## Gotchas

- **Divider settings need their switch.** **Divider colour** (`dividerColor`) and **Divider thickness** (`dividerWidth`) are offered while **Line between items** (`divided`) is on; without it they draw nothing. <!-- src: plugins/bfb-elements/elements/price-list.php:163-191 -->
- **None hides the leader's styling.** With **Leader line** (`leader`) at `none`, **Line colour** (`leaderColor`), **Line thickness** (`leaderWidth`), **Leader offset** (`leaderOffset`) and the highlighted rows' **Line colour** (`highlightLeaderColor`) are hidden, and their CSS skips a list in that mode. <!-- src: plugins/bfb-elements/elements/price-list.php:113-148,409-416; docs/elements/price-list.md "A hidden control has no say" -->
- **Leader offset is a share of the price's height.** The line sits inside the price box and is lifted from its bottom, so `50%` runs through the middle of the price whatever size the title is. The default is `25%`; a px value lifts it a fixed distance. <!-- src: src/elements/price-list/price-list.css:55-65; docs/elements/price-list.md intro -->
- **Key order decides a highlighted row's background, padding and border.** **Item background** (`itemBackground`), **Item padding** (`itemPadding`) and **Item border** (`itemBorder`) write at the same specificity as the Highlighted items group's `highlightBackground`, `highlightPadding` and `highlightBorder`. Bricks emits the rules in the order the settings keys appear, so a `highlight*` key written before its `item*` partner loses to it. <!-- src: plugins/bfb-elements/elements/price-list.php:201-215,339-361; Bricks includes/assets.php:3273 iterates settings in stored order; measured 2026-10-08 with Assets::generate_inline_css_from_element, both orders -->
- **The highlight switch restyles the row on its own.** With nothing set in Highlighted items, a highlighted row gets a 5% tint of the text colour, 12px corners and 16px padding. Its words then sit 16px in from the other rows until **Padding** (`highlightPadding`) says otherwise. <!-- src: src/elements/price-list/price-list.css:24-29; plugins/bfb-elements/includes/class-assets.php:73-76 -->
- **The divider curls at its ends.** Rows keep a 12px corner radius and the divider is each row's top border, so its ends bend round the corners. Corners of 0 in **Item border** (`itemBorder`, `{"radius": {"top": "0", "right": "0", "bottom": "0", "left": "0"}}`) straighten it, and square a highlighted row too unless **Border** (`highlightBorder`) gives it corners. <!-- src: src/elements/price-list/price-list.css:17-34; docs/SESSION-HANDOFF.md:1159; radius-only itemBorder measured to emit border-radius alone, 2026-10-08 -->
- **A Link needs a Title, and the hover colour needs a Link.** The row's **Link** (`link`) wraps the title, so a row with a link and no title renders no anchor. **Link hover colour** (`titleHoverColor`) targets `a.bfbe-price-list__title`, so unlinked rows ignore it. <!-- src: plugins/bfb-elements/elements/price-list.php:227-236,516-523 -->
- **A price pill belongs on the amount.** `.bfbe-price-list__price` holds the leader too and stretches from the title to the number, so a background there paints the whole run. The Price group's **Background** (`priceBackground`), **Padding** (`pricePadding`) and **Price border** (`priceBorder`) write to `.bfbe-price-list__amount`, the number alone. <!-- src: plugins/bfb-elements/elements/price-list.php:277-299,526-537; docs/SESSION-HANDOFF.md "Round 225" -->
- **A query loop repeats the whole list.** With `hasLoop` on, every post renders its own `<ul>` holding every repeater row, so give **Items** one row of dynamic tags. Space between items and the divider act inside each list; the parent's gap spaces the repeated lists. <!-- src: plugins/bfb-elements/includes/abstract-element.php:1201-1243; docs/API-PROBE.md section 6; measured 2026-10-08, three posts gave three ul elements -->
- **A tag's HTML prints as text.** Each text field is escaped after its dynamic data resolves, so a tag that returns markup (`{post_title:link}`) shows its tags on the page. Use a plain-text tag and the row's `link`, which takes `{"type": "meta", "useDynamicData": "{post_url}"}`. <!-- src: plugins/bfb-elements/elements/price-list.php:440-448; measured 2026-10-08, {post_title:link} rendered as escaped markup and the meta link as a real href -->
- **The canvas draws divs.** In the builder the root and rows are `<div>`s; the `ul` and `li` tags are the page's. CSS written against the tags misses in the canvas, so target the `bfbe-price-list__*` classes. <!-- src: plugins/bfb-elements/elements/price-list.php:473-474; plugins/bfb-elements/includes/abstract-element.php:411-421 -->
- **Images load at the thumbnail size, and a URL image has an empty alt.** A row's image uses its own `size`, or `thumbnail` when it names none, so a large **Size** (`imageSize`) wants `"size": "medium"` or larger. A media-library image carries its alt text; one given by URL, or by a tag that returns a URL, renders with `alt=""`. <!-- src: plugins/bfb-elements/elements/price-list.php:495,507-511 -->

## Never do

- Do not set `dividerColor` or `dividerWidth` without `divided: true`.
- Do not set `leaderColor`, `leaderWidth`, `leaderOffset` or `highlightLeaderColor` with `leader: "none"`.
- Do not write `highlightBackground`, `highlightPadding` or `highlightBorder` before `itemBackground`, `itemPadding` or `itemBorder` in the settings object.
- Do not put a dynamic tag that returns HTML in a text field; use a plain-text tag and the row's `link`.
- Do not give a row a `link` without a `title`.
- Do not fill a looped Price List with several rows unless every post should repeat them all.
- Do not style the list through `ul` or `li` selectors; target the `bfbe-price-list__*` classes.
- Do not paint a price background on `.bfbe-price-list__price`; use `priceBackground`, which writes to `.bfbe-price-list__amount`.
