---
name: bfbe-view-switch
description: "Use when placing, wiring or styling BFB View Switch (`bfbe-view-switch`): grid and list buttons, column choices and products per page for a product grid or a looping element, together or as separate switches. Read before writing its settings."
---

# BFB View Switch (`bfbe-view-switch`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-view-switch.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/view-switch/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.68 KB, JS 1.42 KB (gzipped), plus shop-live, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Switch (`bfbeSwitch`)
- `target` (text) **Loop element id**: placeholder The next product loop
- `layouts` (checkbox) **Grid and list buttons**
- `columns` (text) **Column choices**: placeholder 2, 3, 4. Numbers, comma separated; empty for none.
- `perPage` (text) **Per page choices**: placeholder 12, 24, 48. Numbers, comma separated; empty for none.

### Words (`bfbeWords`)
- `gridText` (text) **Grid**: placeholder Grid; only when `layouts` is set
- `listText` (text) **List**: placeholder List; only when `layouts` is set
- `columnsText` (text) **Columns**: placeholder Columns
- `perPageText` (text) **Per page**: placeholder Per page

### Look (`bfbeLook`)
Styling only, every key in the schema file: `gap`, `justify`, `groupBackground`, `groupBorder`, `groupPadding`, `groupGap`, `wordTypography`, `wordPadding`, `buttonTypography`, `buttonPadding`, `buttonBorder`, `buttonBackground`, `hoverBackground`, `hoverColor`, `onBackground`, `onColor`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-view-switch bfbe-view" data-bfbe-view data-bfbe-view-target="{loop id}">
  <div class="bfbe-view__group" role="group" aria-label="Layout">
    <button type="button" class="bfbe-view__btn" data-bfbe-view-layout="grid" aria-pressed="true">Grid</button>
    <button type="button" class="bfbe-view__btn" data-bfbe-view-layout="list" aria-pressed="false">List</button>
  </div>
  <div class="bfbe-view__group" role="group" aria-label="Columns">
    <span class="bfbe-view__word">Columns</span>
    <button type="button" class="bfbe-view__btn" data-bfbe-view-cols="3" aria-pressed="false">3</button>
  </div>
  <div class="bfbe-view__group" role="group" aria-label="Per page">
    <span class="bfbe-view__word">Per page</span>
    <a class="bfbe-view__btn" href="?bfbe_pp=24&bfbe_pv={proof}&bfbe_pt={loop id}" data-bfbe-view-pp="24" rel="nofollow" aria-current="page">24</a>
  </div>
</div>
```

- `data-bfbe-view-target` is printed only with **Loop element id** (`target`); `data-bfbe-view-canvas` marks the builder's instance. A group is printed only when its part is on; with none on, the root is empty and the builder says "Nothing to switch".
- States: `aria-pressed` on the grid, list and column buttons; `aria-current="page"` on the per-page link the page was built with (the server marks it, never the remembered value).
- On the target: `bfbe-view--grid` or `bfbe-view--list`, `--bfbe-view-cols` and an inline `grid-template-columns` (one column in list). On Bricks' Products element the class goes on its root and the columns on its `ul.products`; on a looping element both go on the loop items' parent.
- Bricks' Products element has two presets: the list lays each `li.product` as a two-column grid, the picture beside the words; the grid is Bricks' own. A looping element only gets `.bfbe-view--list > * { grid-column: 1 / -1 }`.
- Where controls write: `gap` as `--bfbe-view-gap` and `justify` on the root; `group*` on `.bfbe-view__group`; `word*` on `.bfbe-view__word`; `button*` and `hover*` on `.bfbe-view__btn` (`buttonBackground` on buttons not pressed and links not current); `onBackground` and `onColor` as `--bfbe-view-on-bg` and `--bfbe-view-on-fg`, drawn with `:not(#_)` so Bricks' id-weighted button typography never paints over the pressed look.

## Wiring to other elements

- **Hub.** Start at `bfbe-shop`. Product loops are `bfbe-shop-loops`; the catalogue settings on the same grid (promo tiles, sorting, filters) are `bfbe-shop-catalogue`.
- **The target is an element id, by Bricks' design.** `target` takes the six-character id of Bricks' Products element or of the looping element itself (not its wrapper), as the structure panel shows it. Empty, the switch drives the first product loop after it on the page. Per page goes only to that loop, never to a loop placed before the switch.
- **Several switches over one loop share one choice.** Each reads the stored choice when pressed and writes it back whole, keyed by the loop's id whether named or found as the nearest, so a layout switch in the toolbar and a columns switch beside the result count stay in step.
- **The per-page link reaches the query on the server** through Bricks' `bricks/posts/query_vars` (a Products element or a Posts loop over products) and through the shop archive's main query.
- **Bricks' live filters and pagination** redraw the loop; the switch applies the choice again after Bricks' `query_result/displayed`, `pagination/completed` and `load_page/completed` events.
- The choice lives in the visitor's browser (`localStorage`, `bfbe_shop_view:{loop id}`), as necessary storage. Give the switch a class in `_cssClasses` for your own CSS.

## Verified patterns

**A toolbar switch for an archive grid.** From the 2.4 site's demo shop, template "Fernhouse: product archive" (`bfb-demo-archive`): layout, columns and per page in rounded tracks, aimed at the archive loop by id. Use the target loop's own id. Trimmed: the words' and buttons' typography and the demo's colour variables.

```json
{
  "name": "bfbe-view-switch",
  "settings": {
    "target": "2c8e19",
    "layouts": true,
    "columns": "2, 3, 4",
    "perPage": "12, 24",
    "gap": "10",
    "groupBackground": { "hex": "#ffffff" },
    "groupBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
    "groupPadding": { "top": "4", "right": "4", "bottom": "4", "left": "4" },
    "groupGap": "2",
    "buttonPadding": { "top": "7", "right": "13", "bottom": "7", "left": "13" },
    "buttonBorder": { "width": { "top": "0", "right": "0", "bottom": "0", "left": "0" }, "style": "solid", "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } },
    "hoverBackground": { "hex": "#f7f8fa" },
    "onBackground": { "hex": "#101828" },
    "onColor": { "hex": "#ffffff" }
  }
}
```

**No id: the nearest product loop after it.** From the fixture "PRO: Shop view switch" (`fixture-shop-view`), the switch `.view-b` with its own words and the loop under it. The fixture's grid sits on the looping element; here it is on a wrapper, since the classes and columns go on the loop items' parent.

```json
[
  {
    "name": "bfbe-view-switch",
    "settings": { "layouts": true, "columns": "2, 4", "perPage": "6, 12", "gridText": "Tiles", "listText": "Rows", "_cssClasses": "view-b" }
  },
  {
    "name": "block",
    "settings": { "_display": "grid", "_gridTemplateColumns": "repeat(3, minmax(0, 1fr))", "_gridGap": "16px" },
    "children": [
      {
        "name": "block",
        "settings": { "hasLoop": true, "query": { "objectType": "post", "post_type": ["product"], "posts_per_page": 6 }, "_cssClasses": "view-loop" },
        "children": [ { "name": "product-title", "settings": { "tag": "h3", "linkToProduct": true } } ]
      }
    ]
  }
]
```

**The layout and the columns placed apart.** From the same fixture, `.view-c` and `.view-d`: two switches over one Products element, far from it, sharing its choice. The empty strings turn the other parts off.

```json
[
  { "name": "bfbe-view-switch", "settings": { "target": "a65a83", "layouts": true, "columns": "", "perPage": "", "_cssClasses": "view-c" } },
  { "name": "bfbe-view-switch", "settings": { "target": "a65a83", "columns": "2, 3, 4", "perPage": "", "_cssClasses": "view-d" } }
]
```

## Gotchas

- **Unset is not empty.** `columns` and `perPage` left out print the placeholders' choices, "2, 3, 4" and "12, 24, 48"; only an empty string means none. Numbers run 1 to 200, eight at most. <!-- src: plugins/bfb-elements-pro/elements/view-switch.php:287-311 -->
- **A looping element needs a grid parent.** The layout class and the inline columns go on the loop items' parent, so put the looping element in a wrapper with `_display: "grid"`; on the parent itself nothing changes. <!-- src: src/elements/view-switch/view-switch.js:24-31 ; src/elements/view-switch/view-switch.js:60-68 -->
- **List looks like a list on the Products element only.** A looping element in list view gets one card per row and nothing more: style `.bfbe-view--list` on the wrapper yourself. <!-- src: src/elements/view-switch/view-switch.css:17-26 ; docs/elements/view-switch.md "What the visitor gets" -->
- **A choice holds only while a switch of its loop is on screen.** The chosen layout and columns are inline values that beat Bricks' own Columns; where every switch of the loop is hidden with Bricks' Display (a phone, say), the loop drops them and shows the layout and columns set in Bricks, and takes the choice back when a switch shows again. A switch in a closed off-canvas still counts (Bricks hides it with visibility, not display). Hide the switch at the widths where the visitor should not choose. <!-- src: src/elements/view-switch/view-switch.js:53-75 ; src/elements/view-switch/view-switch.js:150-159 -->
- **Per page reloads the page.** It is a real link to page 1 with a proven count; a number typed into the address is ignored, and the count reaches only a Products element, a Posts loop over products or the shop archive's main query. <!-- src: plugins/bfb-elements-pro/includes/shop/class-views.php:50-68 ; plugins/bfb-elements-pro/includes/shop/class-views.php:184-202 -->
- **The nearest is the next product loop, by the saved order.** Without `target`, a loop above the switch, or a second loop after the first, is never resized; name the loop when the page has several. <!-- src: plugins/bfb-elements-pro/includes/shop/class-views.php:92-111 ; plugins/bfb-elements-pro/includes/shop/class-views.php:159-173 -->
- **A remembered per-page count is followed once.** On a later visit the page redirects to that count once per path in the session, only when this switch offers it and never on a `/page/N/` address; after that the page keeps its default. <!-- src: src/elements/view-switch/view-switch.js:103-115 -->
- **The canvas only presses buttons.** In the builder the grid never changes, so the canvas stays as you build it; check the layout on the page. <!-- src: src/elements/view-switch/view-switch.js:96 ; src/elements/view-switch/view-switch.js:127 -->
- **Without the script only per page works.** Grid, list and columns need JavaScript; the grid then stays as the designer set it. <!-- src: docs/elements/view-switch.md "What works without JavaScript" -->

## Never do

- Do not leave `columns` or `perPage` out to mean none; set `""`.
- Do not set `target` to a class or to a wrapper's id; it takes the Products element's or the looping element's id.
- Do not put a looping element's grid on the looping element itself when a switch drives it; put it on a wrapper.
- Do not expect a list layout on a looping element without your own `.bfbe-view--list` CSS.
- Do not leave a switch shown at a width whose grid cannot take its column counts; hide it there with Display and the loop keeps its Bricks columns.
- Do not rely on the nearest loop on a page with several product loops; set `target`.
