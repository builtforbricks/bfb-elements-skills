---
name: bfbe-product-badges
description: "Use when placing, wiring or styling BFB Product Badges (`bfbe-product-badges`). Read before writing its settings."
---

# BFB Product Badges (`bfbe-product-badges`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-product-badges.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/product-badges/

## What it is
Badges a product earns from rules, decided on the server when the page renders: Sale, Save 24%, New, Best seller, Only a few left, Sold out, Back-order, a pre-order with its date, Featured, a category, a tag or a field of your own. The rules live in one list for the whole shop on the Shop page; you place the element where the badges go, in a product card or on the product page.

**Not for:** It does not change Bricks' own Sale and New badges on its product elements, which stay as they are, and it does not read a sale scheduled for later as a sale. A pre-order badge shows a date; taking payment later is a pre-order extension's job.

**Costs a page:** CSS 0.38 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** no · **Keyboard:** no · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Badges (`bfbeBadges`)
- `max` (number) **Badges at most**: placeholder 2. How many show, highest priority first. 2 by default, up to 10.
- `rules` (select) **Rules shown**: options: `0` Sold out, `1` Back-order, `2` Pre-order: ships {date}, `3` Only a few left, `4` Save {percent}%, `5` Sale, `6` Best seller, `7` New, `8` Featured, `9` Kitchen, `10` A gift, `11` Sold per litre. All of them by default, or the rows you choose, for a card that shows only Sale and New, say.
- `layout` (select) **Layout**: options: `stacked` Stacked (default), `inline` Inline. Stacked by default (a column), or Inline (a row that wraps).
Styling, in the schema file: `alignStacked`, `alignInline`.

### Look (`bfbeLook`)
Styling only, every key in the schema file: `gap`, `badgeBackground`, `badgeColor`, `badgeTypography`, `badgePadding`, `badgeBorder`, `badgeShadow`.

## What it guarantees for accessibility (do not undo)
- A badge is always words; its colours sit behind the text and never carry the meaning alone.
- The badges are a list in the markup, one item per badge.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<ul class="brxe-bfbe-product-badges bfbe-badge bfbe-badge--stacked" data-bfbe-badges="2">
  <li class="bfbe-badge__item bfbe-badge__item--discount" data-bfbe-badge="discount" style="--bfbe-badge-bg:#c2410c;--bfbe-badge-fg:#ffffff">Save 24%</li>
  <li class="bfbe-badge__item bfbe-badge__item--new" data-bfbe-badge="new">New</li>
</ul>
```

- A real list, decided on the server when the page renders; no script. `bfbe-badge--stacked` is a column, `bfbe-badge--inline` a row that wraps. `data-bfbe-badges` is the count shown.
- Each item carries its rule's key as a modifier and in `data-bfbe-badge`: `sale`, `discount`, `new`, `best`, `low`, `soldout`, `backorder`, `preorder`, `featured`, `category`, `tag`, `meta`. A rule's own colours ride inline as `--bfbe-badge-bg` and `--bfbe-badge-fg`.
- Every badge stays on one line and ends in an ellipsis when its place is too narrow. The list has `pointer-events: none`.
- Where controls write: `gap`, `badgeBackground` and `badgeColor` set `--bfbe-badge-gap`, `--bfbe-badge-bg` and `--bfbe-badge-fg` on the root; `badgeTypography`, `badgePadding`, `badgeBorder` and `badgeShadow` write to `.bfbe-badge__item`; `alignStacked` to `&.bfbe-badge--stacked` (align-items), `alignInline` to `&.bfbe-badge--inline` (justify-content).
- No product, or no badge that applies: nothing on the page, not even the list.

## Wiring to other elements

- **The product.** It reads the product of the page on a single product template, or the loop item's in a product query loop (Bricks' Query with post type `product`, or a BFB Shop products loop, skill `bfbe-shop-loops`). It has no product setting of its own.
- **The rule list.** The rules live once for the whole shop, on BFB Elements, Shop, **Product badges**: badge text, **Show when**, value, priority, colours, forty rows at most. **Rules shown** `rules` names rows of that list by their saved ids; empty shows every row that applies.
- **The product's fields.** A pre-order badge reads **Release date** on the product's General tab (`_bfbe_release_date`; a variation takes its parent's), and `{date}` in its text prints it. `{percent}` in a discount badge prints the saving.
- **Over a picture.** Place it inside the card's picture box and give it Bricks' own **Position** (`_position: "absolute"`, `_top`, `_left`, `_zIndex`) with the box at `_position: "relative"`. Clicks pass through the badges to the picture's link.
- Nothing targets it by class or id. The hub is skill `bfbe-shop`.

## Verified patterns

**Two badges over a product card's picture** (the demo shop's product card, `dev/demo/shop/lib.php` `fh_card()`, "Badges"). Inside a product query loop, the card's picture box is relative and square; the badges sit 12px from its top left corner as pills, stacked, two at most. On a phone they move to the picture's foot. The card's other parts and the demo's typography are left out; the loop is a plain Bricks product query here.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "post", "post_type": [ "product" ], "posts_per_page": 4 } },
  "children": [
    { "name": "block", "settings": { "_position": "relative", "_aspectRatio": "1 / 1", "_overflow": "hidden" }, "children": [
      { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "woocommerce_single" }, "link": { "type": "external", "url": "{post_url}" }, "_width": "100%", "_height": "100%", "_objectFit": "cover" } },
      { "name": "bfbe-product-badges", "settings": { "max": 2, "layout": "stacked", "gap": "6px", "badgePadding": { "top": "6", "right": "10", "bottom": "6", "left": "10" }, "badgeBorder": { "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } }, "_cssClasses": "fh-card__badges", "_position": "absolute", "_top": "12px", "_left": "12px", "_zIndex": "2", "_top:mobile_portrait": "auto", "_bottom:mobile_portrait": "10px", "_left:mobile_portrait": "10px" } }
    ] },
    { "name": "product-title", "settings": { "tag": "h3", "linkToProduct": true } },
    { "name": "product-price", "settings": {} }
  ]
}
```

**A row of badges above the price on the product page** (the demo shop's product template, `dev/demo/shop/10-templates.php`, and the P2 fixture templates `bfbe-shop-product-p2`, `.p2-badges`). `layout: "inline"` with up to three badges, on a single product template, where the page's product is read.

```json
{
  "name": "block",
  "settings": { "_rowGap": "12px" },
  "children": [
    { "name": "product-title", "settings": { "tag": "h1" } },
    { "name": "bfbe-product-badges", "settings": { "max": 3, "layout": "inline", "gap": "6px", "_cssClasses": "p2-badges" } },
    { "name": "product-price", "settings": {} }
  ]
}
```

**Only some of the rules** (fixture page `fixture-shop-badges`, "Badges, chosen"). `rules` lists two rows of the fixture site's list, its Sold out (`"0"`) and its Pre-order (`"2"`), so a card can say availability alone. The ids are that site's: read the target site's from the element's schema options, which list its own rows.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "post", "post_type": [ "product" ], "posts_per_page": 6 } },
  "children": [
    { "name": "product-title", "settings": { "tag": "h3", "linkToProduct": true } },
    { "name": "bfbe-product-badges", "settings": { "max": 2, "rules": [ "0", "2" ], "layout": "stacked" } }
  ]
}
```

## Gotchas

- **Outside a product it is nothing.** On a page that is neither a product template nor inside a product loop the element prints nothing, and the canvas says "No product here". <!-- src: plugins/bfb-elements-pro/elements/product-badges.php:179-183 -->
- **No badge, no box.** When no rule applies, the page gets no `ul` at all; the canvas shows "No badge applies to this product." A layout that counts on the badges' height shifts between products. <!-- src: plugins/bfb-elements-pro/elements/product-badges.php:188-194 -->
- **Rules shown holds ids of one site's list.** `rules` stores the rows' saved ids, so the values in the schema's options are the source site's; on another site read its own list. Rows saved before ids existed answer to their place in the list. Empty means every row. <!-- src: plugins/bfb-elements-pro/includes/shop/class-badges.php:81-105 ; plugins/bfb-elements-pro/elements/product-badges.php:61-70 -->
- **An empty list shows nothing anywhere.** The badges come from the Shop page's list; until a row is added there, every element is empty. <!-- src: plugins/bfb-elements-pro/includes/shop/class-badges.php:322-331 -->
- **Priority, then the cap.** Rows are tested highest priority first (equal priorities in list order), and **Badges at most** `max` stops at 1 to 10, 2 when empty. <!-- src: plugins/bfb-elements-pro/includes/shop/class-badges.php:93 ; plugins/bfb-elements-pro/elements/product-badges.php:185 -->
- **A rule's colours beat the element's.** A row with its own background or text colour paints it inline on its badge; `badgeBackground` and `badgeColor` colour only badges whose rows have none. <!-- src: plugins/bfb-elements-pro/elements/product-badges.php:120-136 ; plugins/bfb-elements-pro/elements/product-badges.php:202-208 -->
- **Badges sit follows the layout.** `alignStacked` acts only with `layout` stacked and `alignInline` only with `inline`; a value kept from the other layout paints nothing. <!-- src: plugins/bfb-elements-pro/elements/product-badges.php:86-107 -->
- **Bricks' own sale badges stay.** Bricks' product elements keep their own Sale and New badges; with both, a card can say Sale twice. <!-- src: docs/elements/product-badges.md "What it does not do" -->
- **Rules read WooCommerce's own states.** A sale scheduled for later is not a sale yet; Best seller ranks WooCommerce's total sales, on-hold orders included, refreshed hourly; Low stock needs managed stock at or under the low-stock amount. <!-- src: docs/elements/product-badges.md ; plugins/bfb-elements-pro/includes/shop/class-badges.php:304 -->
- **One line, never a link.** A long badge ends in an ellipsis rather than wrapping, and the list takes no clicks, so a badge cannot act as a link or button. <!-- src: src/elements/product-badges/product-badges.css:6-9 -->

## Never do

- Do not place it outside a single product template or a product query loop.
- Do not copy `rules` values from another site; use the target site's row ids, or leave `rules` empty.
- Do not reserve layout space for the badges; position them over the picture or let the row collapse.
- Do not set `alignInline` with `layout: "stacked"`, or `alignStacked` with `layout: "inline"`.
- Do not count on `badgeBackground` or `badgeColor` for rows that carry their own colours.
- Do not make a badge the way to a product; link the picture or the title under it.
- Do not show Bricks' own Sale badge beside a Sale rule on the same card.
