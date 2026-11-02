---
name: bfbe-compare-tray
description: "Use when placing the bar of products being compared at the foot of the window, with its count, its Remove buttons and a link to the compare page, with BFB Compare Tray (`bfbe-compare-tray`). Read before writing its settings."
---

# BFB Compare Tray (`bfbe-compare-tray`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-compare-tray.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/compare-tray/

## What it is
The products being compared in a bar fixed to the foot of the window, built from Bricks' own elements and placed once, in the footer template. It comes with a live count, a Block looping Products being compared with a picture, a name and a Remove on each row, and a Compare now button to your compare page. It hides while nothing is compared and shows the moment something is, with no reload.

**Not for:** Not the comparison itself: the table is a Comparison Table set to Products being compared, on your compare page. One tray per page is enough, and the footer template gives every page one.

**Costs a page:** CSS 0.50 KB, JS 0.90 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-compare-tray",
    "settings": {},
    "children": [
        {
            "name": "text-basic",
            "settings": {
                "text": "Compare ({bfbe_compare_count})",
                "tag": "p",
                "_typography": {
                    "font-weight": "600"
                }
            }
        },
        {
            "name": "block",
            "settings": {
                "hasLoop": true,
                "query": {
                    "objectType": "bfbeShopCompare"
                },
                "_direction": "row",
                "_alignItems": "center",
                "_columnGap": "8px",
                "_width": "auto",
                "_padding": {
                    "top": "4",
                    "right": "4",
                    "bottom": "4",
                    "left": "4"
                },
                "_border": {
                    "width": {
                        "top": "1",
                        "right": "1",
                        "bottom": "1",
                        "left": "1"
                    },
                    "style": "solid",
                    "color": {
                        "raw": "var(--bfbe-line, #e4e4e7)"
                    },
                    "radius": {
                        "top": "8",
                        "right": "8",
                        "bottom": "8",
                        "left": "8"
                    }
                }
            },
            "children": [
                {
                    "name": "image",
                    "settings": {
                        "image": {
                            "useDynamicData": "{featured_image}",
                            "size": "thumbnail"
                        },
                        "_width": "44px",
                        "_height": "44px",
                        "_objectFit": "cover"
                    }
                },
                {
                    "name": "product-title",
                    "settings": {
                        "tag": "span",
                        "linkToProduct": true,
                        "_typography": {
                            "font-size": "14px"
                        }
                    }
                }
            ]
        },
        {
            "name": "button",
            "settings": {
                "text": "Compare now",
                "style": "primary",
                "link": {
                    "type": "external",
                    "url": "{bfbe_compare_url}"
                },
                "_conditions": [
                    [
                        {
                            "id": "bfbect",
                            "key": "dynamic_data",
                            "dynamic_data": "{bfbe_compare_url}",
                            "compare": "empty_not"
                        }
                    ]
                ]
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Tray (`bfbeTray`)
- `trayName` (text) **Tray name**: placeholder Compare. "Compare" unless set; what a screen reader announces as the tray's name.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` In the flow, so you can style it (default), `live` Working, as on the site. In the flow, so you can style it (the default), or Working, which shows and hides it as on the site.

## What it guarantees for accessibility (do not undo)
- The tray is a section named with its Tray name.
- One polite region says each change once: the sentence of a change made on the page, the count for a change made in another tab, and nothing for an answer that changes nothing.
- Removing from the tray with the keyboard keeps the focus in the tray, on the Remove of the row now in its place.
- It slides in with the pack's duration and appears at once under reduced motion.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div class="bfbe-ctray__space" aria-hidden="true" hidden></div> <!-- moved to the end of body by the script -->
<section id="brxe-{id}" class="brxe-bfbe-compare-tray bfbe-ctray" data-bfbe-ctray="0" data-bfbe-shop-need="compare"
         aria-label="Compare" data-one="%d product to compare" data-many="%d products to compare" hidden style="display:none">
  <span class="bfbe-sr bfbe-ctray__said" aria-live="polite"></span>
  <p class="brxe-text-basic">Compare (<span class="bfbe-shop-live" data-bfbe-shop-live="compare_count">0</span>)</p>
  <div class="brxe-block" data-bfbe-list-row="compare:412:a1b2c3" data-bfbe-list-have="57:0,61:0" data-bfbe-list-item="57:0">
    <img class="brxe-image …"> <span class="brxe-product-title">Oak Serving Board</span>
    <div class="bfbe-lrow__actions"><form class="bfbe-lrow__form" method="post" data-bfbe-list-act="list_remove">…
      <button type="submit" class="bfbe-lrow__btn bfbe-lrow__remove" aria-label="Remove: Oak Serving Board">Remove</button></form></div>
  </div> <!-- one per product being compared -->
  <a class="brxe-button bricks-button bricks-background-primary" href="https://…/compare/">Compare now</a>
</section>
```

- The root is a `section` named by **Tray name** `trayName` ("Compare" unless set), holding its children directly. With nothing compared it carries `hidden` and an inline `display:none`, so a Display set on its Style tab cannot show it empty.
- The stylesheet fixes it to the window's foot (`position: fixed`, `inset-block-end: 0`, `z-index: 90`), a wrapping flex row, its padding keeping the content to 1240px and clear of the safe area. It slides in with `--bfbe-duration`, at once under reduced motion.
- The script listens for `bfbe:shop:list` with `detail.kind` `"compare"`: it toggles `hidden` and the inline display, sizes `.bfbe-ctray__space` to the tray's height (a ResizeObserver follows wraps), and writes each change once into `.bfbe-ctray__said`.
- The rows are the seeded Block's query loop: each row's root carries `data-bfbe-list-row` and `data-bfbe-list-item`, its Remove form appended before the closing tag. An empty loop prints Bricks' no-results content and `div.bfbe-lrow__wait`.
- In the canvas, **Show it** `builderView: "open"` (default) adds `bfbe-ctray--canvas`: in the flow, `position: relative`, a dashed frame. `live` adds `data-bfbe-live` instead.
- The tray's own look (background, border, shadow, padding, layout) is Bricks' Style tab on the element, an id rule that outranks the stylesheet; each child is styled on its own Style tab.

## Wiring to other elements

- **Placed once, in the footer template**, so every page with compare buttons has it. It holds Bricks' own elements; move, restyle or remove the seeded three, or add any other.
- **BFB Compare Button** (`bfbe-compare-button`) changes the list; the tray follows it through the shop's state, with no class or id between them. Without a tray on the page, the buttons have no tray.
- **The products** are a query loop of type **Products being compared** (`query.objectType: "bfbeShopCompare"`, `hasLoop: true`) on a Block, Container or Div. Its group **BFB Products being compared**: **Remove on each row** `bfbeShopCompareActions` (`on` or `off`) and **Remove word** `bfbeShopCompareRemoveText`. Inside a row, Bricks' Image with `{featured_image}`, Product title and every product tag read that product (`bfbe-shop-loops`).
- **The count**: `{bfbe_compare_count}` in a Text, live. **The link**: `{bfbe_compare_url}` in a Button's link, the page chosen as **Compare page** (BFB Elements, Shop, Customers, the wishlist and compare pages card). The seeded Button carries a condition, `dynamic_data` `{bfbe_compare_url}` `empty_not`, so it hides while no page is chosen.
- **The compare page** itself is a Comparison Table with `source: "compare"` (`bfbe-comparison-table`).
- **Drawn again after each change** by the lists' render action (`?wc-ajax=bfbe_shop_list`), which reads the loop from the page's own Bricks content and the header, footer and popup templates Bricks resolves for that post (since 30 October).
- **One voice**: a change made on the page with the tray showing is said by the tray's region, the last removal by the shop's shared status, a count changed in another tab by the tray as "3 products to compare".
- For your own CSS give it a class in `_cssClasses`, never `_cssId`: component instances share ids.

## Verified patterns

**The demo shop's tray, in its footer template.** From `dev/demo/shop/10-templates.php` ("Compare tray", the 2.4 site's demo shop). A white bar with rounded top corners; the products as pills, each with its Remove; Compare now pushed right with an auto margin. `_display: "flex"` is added here, as the panel offers Direction and the gaps only with it. Trimmed: the demo's type and shadow.

```json
{
  "name": "bfbe-compare-tray",
  "settings": {
    "trayName": "Comparing", "_cssClasses": "fh-ctray",
    "_display": "flex", "_direction": "row", "_alignItems": "center", "_columnGap": "14px", "_rowGap": "10px",
    "_background": { "color": { "hex": "#ffffff" } },
    "_border": { "width": { "top": "1", "right": "0", "bottom": "0", "left": "0" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "20", "right": "20", "bottom": "0", "left": "0" } }
  },
  "children": [
    { "name": "text-basic", "settings": { "text": "Comparing ({bfbe_compare_count})", "tag": "p", "_typography": { "font-weight": "800" } } },
    { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopCompare" }, "bfbeShopCompareRemoveText": "Remove", "_direction": "row", "_alignItems": "center", "_flexWrap": "nowrap", "_columnGap": "10px", "_width": "auto", "_padding": { "top": "5", "right": "8", "bottom": "5", "left": "5" }, "_background": { "color": { "hex": "#f6f6f8" } }, "_border": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } } }, "children": [
      { "name": "image", "settings": { "image": { "useDynamicData": "{featured_image}", "size": "thumbnail" }, "_width": "40px", "_height": "40px", "_objectFit": "cover" } },
      { "name": "product-title", "settings": { "tag": "span", "linkToProduct": true } }
    ] },
    { "name": "button", "settings": { "text": "Compare now", "style": "primary", "link": { "type": "external", "url": "{bfbe_compare_url}" }, "_margin": { "left": "auto" }, "_conditions": [ [ { "id": "fhctgo", "key": "dynamic_data", "dynamic_data": "{bfbe_compare_url}", "compare": "empty_not" } ] ] } }
  ]
}
```

**Names only, styled by class.** From the fixture `fixture-shop-p9` (the P9 probe reads it). Each part has a class for the site's CSS; the rows are names with their Remove, no pictures. The condition on the Button is added here, as the seeded one has it.

```json
{
  "name": "bfbe-compare-tray",
  "settings": { "_cssClasses": "ctray" },
  "children": [
    { "name": "text-basic", "settings": { "text": "Compare ({bfbe_compare_count})", "_cssClasses": "ctray-count" } },
    { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopCompare" }, "_direction": "row", "_alignItems": "center", "_columnGap": "8px", "_width": "auto", "_cssClasses": "ctray-rows" }, "children": [
      { "name": "product-title", "settings": { "tag": "span", "linkToProduct": true, "_cssClasses": "ctray-name" } }
    ] },
    { "name": "button", "settings": { "text": "Compare now", "style": "primary", "link": { "type": "external", "url": "{bfbe_compare_url}" }, "_cssClasses": "ctray-go", "_conditions": [ [ { "id": "ctgo01", "key": "dynamic_data", "dynamic_data": "{bfbe_compare_url}", "compare": "empty_not" } ] ] } }
  ]
}
```

## Gotchas

- **Compare buttons print no tray.** Since 29 October the tray is this element alone: a page with compare buttons and no BFB Compare Tray has none. This may be revisited. <!-- src: docs/elements/compare-tray.md "Limits" --> <!-- src: plugins/bfb-elements-pro/elements/compare-tray.php:14 -->
- **The tray's layout keys need `_display: "flex"`.** **Direction** `_direction`, **Wrap** `_flexWrap`, **Column gap** `_columnGap` and **Row gap** `_rowGap` are offered only with it. Unset, the stylesheet already lays the tray out as a wrapping, centred row. <!-- src: plugins/bfb-elements/includes/abstract-element.php:884-929 --> <!-- src: src/elements/compare-tray/compare-tray.css:14-17 -->
- **A sticky header that slides up carries it away.** Bricks moves `#brx-header.brx-sticky.slide-up` with a transform, and a fixed element inside a transformed ancestor is fixed to that ancestor; the header's `z-index: 998` also tops the tray's 90. The footer template avoids both. <!-- src: themes/bricks/assets/css/frontend-light.min.css "#brx-header.brx-sticky.slide-up" --> <!-- src: src/elements/compare-tray/compare-tray.css:9-12 -->
- **On a term archive the rows are not drawn again.** On a product category or tag page the view's mark carries the term's id, and the render action answers "no page": after a press there the tray shows, but its rows stay as the page was drawn until the next load. Product pages and pages redraw. <!-- src: plugins/bfb-elements-pro/includes/shop/class-list-set.php:215-217 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:1345-1353 -->
- **One tray per page.** The lists' script hands the change's sentence to the first `[data-bfbe-ctray]` only, and each tray adds a space at the end of the page. <!-- src: src/elements/shop-lists/shop-lists.js:153-155 --> <!-- src: src/elements/compare-tray/compare-tray.js:20-31 -->
- **The canvas compares nothing.** **Show it** `open` draws the tray in the flow to style it; `live` renders it hidden in the canvas, since the canvas counts no products, and its children cannot be picked there. <!-- src: plugins/bfb-elements-pro/elements/compare-tray.php:143-168 -->
- **Remove lives in the row.** Each row's Remove is a form appended before the row root's closing tag, so a looping Block with `tag: "a"` puts forms inside a link. Link the name with Product title's `linkToProduct`. <!-- src: plugins/bfb-elements-pro/includes/shop/class-list-set.php:166-180 --> <!-- src: plugins/bfb-elements-pro/includes/shop/class-compare-set.php:49-56 -->
- **No compare page, no link.** `{bfbe_compare_url}` is empty until a published page is chosen as **Compare page**; keep the seeded condition so Compare now does not link nowhere. <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:1293-1296 --> <!-- src: plugins/bfb-elements-pro/elements/compare-tray.php:115-116 -->
- **An empty tray asks for its parts.** With no children it prints a canvas notice, "Add a Block looping Products being compared, the count and a button.", and nothing on the page but the hidden section. <!-- src: plugins/bfb-elements-pro/elements/compare-tray.php:178-181 -->
- **The tray stays right on a cached page.** The server draws it shown or hidden from the visitor's list and marks a guest's page `DONOTCACHEPAGE`; a cached copy is put right by the live answer after load. <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:208-212 --> <!-- src: docs/elements/compare-tray.md "Without the script" -->

## Never do

- Do not place more than one BFB Compare Tray on a page; place one in the footer template.
- Do not put it in a sticky header that slides up, or in any element with a transform, filter or backdrop-filter.
- Do not set `_direction`, `_flexWrap`, `_columnGap` or `_rowGap` on the tray without `_display: "flex"`.
- Do not make the looping Block a link; link the name with `linkToProduct`.
- Do not force the tray visible with your own `display` rule; it hides itself while nothing is compared.
- Do not remove the condition on the Compare now Button unless a Compare page is chosen.
- Do not leave the tray empty of children; it needs at least the loop of products being compared.
