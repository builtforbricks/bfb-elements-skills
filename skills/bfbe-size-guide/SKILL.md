---
name: bfbe-size-guide
description: "Use when adding a size chart, a cm and inches switch or a find-my-size answer to a product page with `bfbe-size-guide`: a button that opens the guide, or the guide placed on the page in a Bricks container or Tabs pane."
---

# BFB Size Guide (`bfbe-size-guide`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-size-guide.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/size-guide/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.82 KB, JS 1.42 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Guide (`bfbeGuide`)
- `shows` (select) **Shows**: options: `button` A button that opens the guide (default), `page` The guide on the page
- `guide` (select) **Guide**: options: `auto` The guide that applies to this product (default), `g0` Shirts
- `title` (text) **Dialog title**: placeholder The guide name; dynamic data accepted; only when `shows` is not `page`
- `units` (select) **Units shown first**: options: `guide` As the guide is typed (default), `cm` Centimetres, `in` Inches
- `unitsLabel` (text) **Units label**: placeholder Units; dynamic data accepted

### Button (`bfbeButton`)
The whole group shows only when `shows` is not `page`.
- `text` (text) **Text**: placeholder Size guide; dynamic data accepted
- `style` (select) **Style**: options: `primary` Primary, `secondary` Secondary, `light` Light, `dark` Dark, `muted` Muted, `info` Info, `success` Success, `warning` Warning, `danger` Danger
- `size` (select) **Size**: options: `sm` Small, `md` Medium (default), `lg` Large, `xl` Extra large
- `outline` (checkbox) **Outline**
Styling, in the schema file: `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonPadding`, `buttonHoverBackground`, `buttonHoverColor`.

### Size finder (`bfbeFinder`)
- `finder` (select) **Size finder**: options: `show` Shown (default), `hide` Hidden
- `finderTitle` (text) **Title**: placeholder Find my size; only when `finder` is not `hide`
- `finderButton` (text) **Button**: placeholder Find my size; only when `finder` is not `hide`
- `finderResult` (text) **Answer**: placeholder Your size is {size}; only when `finder` is not `hide`
- `finderNone` (text) **No fit**: placeholder No size in this guide fits those measurements.; only when `finder` is not `hide`
Styling, in the schema file: `finderSpacing`, `finderTitleTypography`, `fieldLabelTypography`, `fieldsGap`, `inputTypography`, `inputBackground`, `inputBorder`, `inputPadding`, `inputFocusBorder`, `findTypography`, `findBackground`, `findBorder`, `findPadding`, `findHoverBackground`, `findHoverColor`, `resultTypography`.

### Dialog (`bfbeDialog`)
The whole group shows only when `shows` is not `page`.
Styling only, every key in the schema file: `dialogWidth`, `dialogBackground`, `dialogColor`, `dialogPadding`, `dialogBorder`, `dialogShadow`, `backdrop`, `titleTypography`, `headSpacing`, `closeSize`, `closeIconSize`, `closeColor`, `closeBackground`, `closeBorder`, `closeHoverBackground`, `closeHoverColor`.

### Table (`bfbeTable`)
Styling only, every key in the schema file: `headTypography`, `cellTypography`, `headBackground`, `cellPadding`, `lineColor`, `rowStripe`, `rowHoverBackground`, `unitsTypography`, `unitBackground`, `unitBorder`, `unitPadding`, `unitChosenBackground`, `unitChosenColor`, `unitChosenBorder`, `unitsSpacing`.

### Size finder: arrows (`bfbeFinderArrows`)
The whole group shows only when `finder` is not `hide`.
- `finderSpinArrows` (select) **Arrows**: options: `browser` The browser's, `inside` Ours, inside the box, `stepper` A − and a + beside it, `none` None; only when `finder` is not `hide`
Styling, in the schema file: `finderSpinArrowSize`, `finderSpinArrowWidth`, `finderSpinArrowGap`, `finderSpinArrowColor`, `finderSpinArrowBg`, `finderSpinArrowHover`, `finderSpinArrowHoverBg`, `finderSpinArrowLine`, `finderSpinArrowBorder`.

### In the builder (`bfbeBuilder`)
The whole group shows only when `shows` is not `page`.
- `builderView` (select) **Show it**: options: `open` Open, so you can style it (default), `closed` Closed, as the site leaves it. Closed shows the button alone, as the site does.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-size-guide bfbe-size" data-bfbe-size data-bfbe-size-key="g0">
  <form class="bfbe-size__opener" method="get" action="{product URL}#bfbe-{uid}-size-dialog">
    <input type="hidden" name="bfbe_size_open" value="g0">
    <button type="submit" class="bfbe-size__open bricks-button sm outline bricks-color-dark" aria-haspopup="dialog"
            aria-controls="bfbe-{uid}-size-dialog" data-bfbe-size-open>Size guide</button>
  </form>
  <dialog id="bfbe-{uid}-size-dialog" class="bfbe-size__dialog" aria-labelledby="bfbe-{uid}-size-dialog-title">
    <div class="bfbe-size__head"><h3 class="bfbe-size__title">Shirts</h3>
      <form class="bfbe-size__closer" method="dialog"><button class="bfbe-size__close" aria-label="Close" data-bfbe-size-close>…</button></form></div>
    <!-- the body: the same on the page with shows: "page", where it is the root's only content -->
    <form class="bfbe-size__units" method="get" data-bfbe-size-units>
      <span class="bfbe-size__units-label">Units</span>
      <span class="bfbe-size__units-btns" role="group"><button class="bfbe-size__unit bfbe-chip" name="bfbe_units" value="cm" aria-pressed="true" data-bfbe-unit="cm">cm</button>…</span>
    </form>
    <div class="bfbe-size__scroll"><table class="bfbe-size__table" data-bfbe-size-table data-bfbe-unit="cm" data-bfbe-guide-unit="cm" data-bfbe-rows="{json}">…</table></div>
    <form class="bfbe-size__finder" method="get" data-bfbe-size-finder data-bfbe-result-pattern="…" data-bfbe-result-none="…">
      <fieldset class="bfbe-size__set"><legend class="bfbe-size__finder-title">Find my size</legend>
        <div class="bfbe-size__fields"><label class="bfbe-size__field"><span class="bfbe-size__field-label">Chest <span class="bfbe-size__u">(cm)</span></span>
          <input type="number" name="bfbe_fit[0]" data-bfbe-size-measure="0"></label>…</div>
        <button type="submit" class="bfbe-size__find bfbe-chip">Find my size</button>
        <p class="bfbe-size__result" data-bfbe-size-result hidden></p></fieldset>
    </form>
  </dialog>
</div>
```

- Root `div.bfbe-size`, `inline-block` around the button. `bfbe-size--page` with **Shows** `shows: "page"` (a block, no opener, no dialog, no head); `bfbe-size--canvas` in the builder's Open view, which draws the dialog in the flow under the button.
- The button is Bricks' own `bricks-button`: **Size** adds `sm` to `xl`, **Style** adds `bricks-background-{style}`, or `bricks-color-{style}` with **Outline**. No Style, no colour class.
- The `<dialog>` is real, opened with `showModal()` in the top layer; `[open]` is its state. The table is a real `table`: a hidden caption naming guide and unit, `th scope="col"` headers, `th scope="row"` sizes. The unit buttons toggle `aria-pressed`; the script rewrites the cells, the `.bfbe-size__u` words and the hidden unit field in place.
- Where controls write: `dialogWidth` sets `--bfbe-size-width` on the root; `dialog*` write to `.bfbe-size__dialog`, `backdrop` to its `::backdrop`, `close*` to `.bfbe-size__close`, `button*` to `.bfbe-size__open`. Table controls write to `.bfbe-size__table th, td`, `rowStripe` to even rows; `unit*` to `.bfbe-size__unit` and `unitChosen*` to `[aria-pressed="true"]`; `find*` to `.bfbe-size__find`, `input*` to `.bfbe-size__field input`, `resultTypography` to `.bfbe-size__result`.

## Wiring to other elements

- **The guide comes from the Shop page**, not the element: BFB Elements, Shop, Products, card **Size guides**. `guide: "auto"` takes the first guide whose **Applies to** matches the product on the template, or the query loop's product.
- **Two instances, placed apart.** One Size Guide with the default `shows` sits under Bricks' `product-add-to-cart` as a button; a second with `shows: "page"` goes in any Bricks container: a Block beside a heading, a pane of Bricks' Tabs (Nestable), an Accordion, a popup. Each works on its own: the page instance's unit switch and finder never open the other's dialog.
- **Bricks' Product tabs** (`product-tabs`) gains a "Size guide" tab by itself when the guide's **Also a product tab** switch is on. That tab holds the units and the table, without the finder.
- The script re-binds after Bricks' AJAX events (query results shown, popup loaded, page loaded), so an instance inside a Bricks popup or a loop loaded later works. The finder's answer is said once by the shop's announcer.
- Give an instance a class in `_cssClasses` for your own CSS. Nothing targets it by attribute, and it targets nothing.

## Verified patterns

**A button under Add to cart, and the whole guide placed apart** (fixture template `bfbe-shop-product-p4`, `.p4-size` and `.p4-size-page`, trimmed to the parts that matter). The summary's instance is the button; the second, `shows: "page"`, prints units, table and finder in its own grid beside a Bricks heading, since the page instance has no title. Use this tree on a product template; outside one, `guide: "auto"` finds no product.

```json
{
  "name": "block",
  "settings": { "_rowGap": "32px" },
  "children": [
    { "name": "block", "settings": { "_rowGap": "12px" }, "children": [
      { "name": "product-title", "settings": {} },
      { "name": "product-price", "settings": {} },
      { "name": "product-add-to-cart", "settings": {} },
      { "name": "bfbe-size-guide", "settings": { "text": "Size guide", "style": "dark", "outline": true, "size": "sm", "_cssClasses": "p4-size" } }
    ] },
    { "name": "block", "settings": { "_display": "grid", "_gridTemplateColumns": "1fr 2fr", "_columnGap": "32px", "_cssClasses": "p4-apart-size" }, "children": [
      { "name": "heading", "settings": { "text": "Fit and sizing", "tag": "h2" } },
      { "name": "bfbe-size-guide", "settings": { "shows": "page", "unitsLabel": "Measure in", "_cssClasses": "p4-size-page" } }
    ] }
  ]
}
```

**One guide by name, on a page that is not a product** (built from the schema; the dev site's first guide is `g0`, Shirts). **Guide** `guide` names the Shop page's guide, so a sizing page shows it with no product; **Units shown first** `units: "in"` opens it in inches. Read the target site's `guide` options before choosing a key.

```json
{ "name": "bfbe-size-guide", "settings": { "shows": "page", "guide": "g0", "units": "in", "finderTitle": "Find your size", "_cssClasses": "size-page" } }
```

## Gotchas

- **No matching guide, no output.** With `guide: "auto"` and no guide whose **Applies to** covers the product (by category with its children, tag or ids; a variation reads its parent), the page gets nothing and the canvas a notice. <!-- src: plugins/bfb-elements-pro/elements/size-guide.php:736 ; plugins/bfb-elements-pro/includes/shop/class-size-guides.php:93 -->
- **Guide keys are positions.** `g0`, `g1` are the guides' places in the Shop page's list, renumbered on save when a nameless guide is dropped, so a pinned key follows the place, not the name. <!-- src: plugins/bfb-elements-pro/includes/shop/class-size-guides.php:65 -->
- **The page instance has no title and no button.** `shows: "page"` hides the Button, Dialog and In the builder groups and **Dialog title** `title`, and the render prints none of them: place a Bricks heading before it. <!-- src: plugins/bfb-elements-pro/elements/size-guide.php:56 ; plugins/bfb-elements-pro/elements/size-guide.php:99 ; plugins/bfb-elements-pro/elements/size-guide.php:775 -->
- **The product tab shows it a second time.** **Also a product tab** on the guide adds a "Size guide" tab to Bricks' Product tabs, so a page instance on the same template prints the table twice. <!-- src: plugins/bfb-elements-pro/includes/shop/class-size-guides.php:278 -->
- **The finder needs a measurement column and ordered rows.** It hides with fewer than two columns, and answers with the first row, top down, whose every typed measure fits up to the range's top; a column of words never fits. <!-- src: plugins/bfb-elements-pro/elements/size-guide.php:813 ; src/elements/size-guide/size-guide.js:43 ; docs/elements/size-guide.md "Size finder" -->
- **The dialog is a light card on any page.** It is white with dark text whatever the page's colours; on a dark site set `dialogBackground` and `dialogColor`. The page instance takes the page's own surface. <!-- src: src/elements/size-guide/size-guide.css:4 ; src/elements/size-guide/size-guide.css:33 -->
- **Style the parts, not the element.** Bricks' universal `_background`, `_padding` and `_border` land on the inline-block root around the button; the dialog sits in the top layer and takes only the `dialog*` controls. <!-- src: src/elements/size-guide/size-guide.css:2 ; plugins/bfb-elements-pro/elements/size-guide.php:762 -->
- **The canvas shows a layout and a sample answer.** **Show it** `builderView` unset (Open) draws the dialog in place under the button with the guide's middle size in the Answer sentence; the script is idle in the builder. Closed shows the button alone. <!-- src: plugins/bfb-elements-pro/elements/size-guide.php:765 ; plugins/bfb-elements-pro/elements/size-guide.php:858 ; src/elements/size-guide/size-guide.js:57 -->
- **Without a script, every part is a GET form.** The button, the units and the finder reload the product's address (`?bfbe_size_open=g0&bfbe_units=in`) with the dialog open and the answer in it; the page instance comes back to its units, with no dialog opened. <!-- src: plugins/bfb-elements-pro/elements/size-guide.php:760 ; plugins/bfb-elements-pro/elements/size-guide.php:785 -->

## Never do

- Do not set Button, Dialog or `builderView` keys, or `title`, with `shows: "page"`; the panel hides them.
- Do not pin `guide` to a `g` key without reading the target site's options; use `auto` on product templates.
- Do not place a page instance on products whose guide has **Also a product tab** on beside Bricks' Product tabs.
- Do not leave a `shows: "page"` instance without a heading of your own before it.
- Do not style the dialog with Bricks' universal `_background`, `_padding` or `_border`; use the `dialog*` controls.
- Do not put a `guide: "auto"` instance on a page that is not a product; pick a guide by key there.
