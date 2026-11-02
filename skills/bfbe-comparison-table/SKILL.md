---
name: bfbe-comparison-table
description: "Use when placing, wiring or styling BFB Comparison Table (`bfbe-comparison-table`): a plan or pricing comparison with plans across the top and features down the side, ticks, crosses or text in each cell, a highlighted plan, notes and group headings; in a shop, the products a visitor compares side by side, with their attributes, size, weight and SKU as rows and the differences marked. Read before writing its settings."
---

# BFB Comparison Table (`bfbe-comparison-table`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-comparison-table.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/comparison-table/

## What it is
Plans across the top and features down the side, with ticks, crosses or text in each cell. It is a real table with scoped headers, an optional caption, an optional sticky features column and notes behind small buttons. On narrow screens it scrolls sideways, or stacks into one card per feature below a width measured on the table itself.

**Not for:** Plans and features are rows you enter in two repeaters, so it suits a short, hand-written comparison; with WooCommerce, Products being compared reads the visitor's compare list instead, up to four products. Records from posts or a file fit a table that reads its rows from a source; this one does not sort or filter.

**Costs a page:** CSS 2.00 KB, JS 0.47 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Ungrouped
- `source` (select) **Rows and columns from**: options: `typed` Typed in (default), `compare` Products being compared. At the top of the panel, Typed in, the default, for your plans and features, or, with WooCommerce, Products being compared: the products a visitor puts side by side with BFB Compare Button, up to four, as the columns, and the facts you choose as the rows. The Plans, Features and Ticks and crosses groups leave the panel with it, and Table, Look and Plan header style both. In the builder the table shows three of your shop's products, so you can design it before anything is compared.

### Products being compared (`bfbeProducts`)
The whole group shows only when `source` is `compare`.
- `cmpShow` (select) **Each column shows**: options: `image` Image, `name` Name, `price` Price, `rating` Rating, `stock` Stock, `cart` Add to cart, `remove` Remove. Image, Name, Price, Rating, Stock, Add to cart and Remove, all of them unless you pick some. The price is WooCommerce's own, and Add to cart is WooCommerce's add for a simple product that can be bought, a link to the product for any other.
- `cmpRows` (select) **Rows**: options: `attrs` Every attribute, `attr:pa_colour` Colour, `attr:pa_material` Material, `attr:pa_q5-finish` Q5 Finish, `attr:pa_q5-pattern` Q5 Pattern, `attr:pa_size` Size, `attr:pa_warmth` Warmth, `dimensions` Dimensions, `weight` Weight, `sku` SKU. Every attribute any compared product has, or the ones you pick, and Dimensions, Weight and SKU. **Custom field rows** adds a row for each field key you type, commas between, such as care, origin.
- `cmpMeta` (text) **Custom field rows**: placeholder care, origin. Field keys, commas between.
- `cmpHighlight` (checkbox) **Highlight**
- `cmpOnlyDiff` (checkbox) **Only differences**
- `cmpDiffMark` (select) **Mark with**: options: `fill` A fill on the row (default), `dot` A dot by the feature; only when `cmpHighlight` is set
- `cmpDiffKey` (checkbox) **Dot on the first heading**: only when `cmpHighlight` is set and `cmpDiffMark` is `dot`. Its words then say what a dot means.
- `cmpCartText` (text) **Add to cart words**: placeholder Add to cart
- `cmpRemoveText` (text) **Remove words**: placeholder Remove
- `cmpEmpty` (text) **While there is nothing**: placeholder Nothing to compare yet.; dynamic data accepted
Styling, in the schema file: `cmpDiffBackground`, `cmpDiffDot`, `cmpEmptyTypography`, `cmpEmptyBorder`, `cmpEmptyPadding`.

### Plans (`bfbePlans`)
The whole group shows only when `source` is not `compare`.
- `plans` (repeater) **Plans**: only when `source` is not `compare`. Add one row per plan. Each row sets its Name, Price, Badge, Highlight, Button label and Link. Name, Price, Badge and Button label take dynamic data. A Badge, Price or Note from a dynamic tag with nothing in it is not drawn.

### Features (`bfbeFeatures`)
The whole group shows only when `source` is not `compare`.
- `features` (repeater) **Features**: only when `source` is not `compare`. Add one row per feature. Each row has a Feature name, Per plan values, a Note and Use as a group heading. Feature, Per plan and Note take dynamic data.
Styling, in the schema file: `hintSize`.

### Table (`bfbeTable`)
- `caption` (text) **Caption**: dynamic data accepted. A title shown above the table, which screen readers hear as the table's caption. It takes dynamic data.
- `firstColumn` (text) **Features column heading**: placeholder Features; dynamic data accepted. The words at the top of the features column, Features unless set. It takes dynamic data.
- `sticky` (checkbox) **Sticky features column**. Off by default. Tick it to keep the features column in view while the plan columns scroll sideways beneath it.
- `narrow` (select) **On narrow screens**: options: `scroll` Scroll sideways (default), `cards` One card per feature. Scroll sideways, or Cards. **Below** sets the width at which the plans turn into cards: 480px, 640px, 768px (the default) or 992px, or **Custom** to set your own in **Custom width**, in px, rem or em (a number on its own is px). The width is the table's own, not the screen's, so a table in a narrow column turns into cards on a wide screen too. A rem follows your site's root font size, an em the table's own font size.
- `stackBelow` (select) **Below**: options: `480` 480px, `640` 640px, `768` 768px (default), `992` 992px, `custom` Custom; only when `narrow` is `cards`
- `stackWidth` (number) **Custom width**: placeholder 700px; with a unit; only when `narrow` is `cards` and `stackBelow` is `custom`. Stacks at this width or narrower.
Styling, in the schema file: `planMinWidth`, `tableMinWidth`.

### Look (`bfbeLook`)
- `featureHeadAlign` (select) **First heading alignment**: options: `top` Top, `middle` Middle (default), `bottom` Bottom; writes CSS
- `columnLines` (checkbox) **Lines between columns**
Styling, in the schema file: `highlightBackground`, `highlightColor`, `featureTypography`, `valueTypography`, `groupTypography`, `firstColumnWidth`, `cellPadding`, `tableBackground`, `valueAlign`, `lineColor`, `headBackground`, `featureBackground`, `stripeBackground`, `groupBackground`, `tableBorder`, `hintBackground`, `hintColor`, `captionTypography`, `captionPadding`, `noteTypography`, `labelTypography`.

### Ticks and crosses (`bfbeMarks`)
The whole group shows only when `source` is not `compare`.
- `tickIcon` (icon) **Tick icon**: only when `source` is not `compare`. Pick any icon from the picker to replace the drawn tick. Cross icon does the same for the cross.
- `crossIcon` (icon) **Cross icon**: only when `source` is not `compare`
Styling, in the schema file: `tickColor`, `crossColor`, `iconSize`, `tickBackground`, `crossBackground`, `markPadding`, `markBorder`.

### Plan header (`bfbePlanLook`)
Styling only, every key in the schema file: `cmpImgWidth`, `cmpImgBorder`, `cmpPartGap`, `headTypography`, `priceTypography`, `cmpStarColor`, `cmpStarSize`, `cmpRatingTypography`, `cmpStockTypography`, `cmpOutColor`, `badgeTypography`, `badgeBackground`, `badgePadding`, `badgeBorder`, `buttonBackground`, `buttonColor`, `buttonTypography`, `buttonPadding`, `buttonBorder`, `buttonBackgroundHover`, `buttonColorHover`, `cmpRemoveTypography`, `cmpRemoveColor`, `cmpRemoveHover`.

## What it guarantees for accessibility (do not undo)
- In the table layout, plan and feature headings are header cells with scope col, row or colgroup.
- A Caption becomes the table's own caption element, and ticks and crosses carry visually hidden text, Yes or No.
- Each note button is a native button with aria-expanded and aria-controls and a hidden name, Details; Enter or Space shows and hides its note.
- Plan buttons are real links in the Tab order, and the plan names repeated for the card layout are hidden from assistive technology.
- With Products being compared, each product's header cell is th scope col and each fact th scope row.
<!-- bfbe:generated:end -->

## Rendered DOM

On the frontend, a real table inside a scroll wrapper. Square brackets mark what appears when its setting is filled:

```html
<div id="brxe-..." class="brxe-bfbe-comparison-table bfbe-cmp [bfbe-cmp--cards]"
     data-bfbe-cards="" data-bfbe-sticky="0" style="--bfbe-cmp-cols:3">
  <div class="bfbe-cmp__scroll">
    <table class="bfbe-cmp__table">
      [<caption class="bfbe-cmp__caption">Caption</caption>]
      <thead class="bfbe-cmp__head"><tr class="bfbe-cmp__row">
        <th scope="col" class="bfbe-cmp__cell bfbe-cmp__feature-head">Features</th>
        <th scope="col" class="bfbe-cmp__cell bfbe-cmp__plan [bfbe-cmp__plan--hl]">
          [<span class="bfbe-cmp__badge">] <span class="bfbe-cmp__name"> [<span class="bfbe-cmp__price">]
          [<a class="bfbe-cmp__btn" href="..."><span>Button label</span></a>]</th></tr></thead>
      <tbody class="bfbe-cmp__body">
        <tr class="bfbe-cmp__row bfbe-cmp__row--group"><th scope="colgroup" colspan="4" class="bfbe-cmp__cell bfbe-cmp__group">Group</th></tr>
        <tr class="bfbe-cmp__row">
          <th scope="row" class="bfbe-cmp__cell bfbe-cmp__feature">Feature
            [<button type="button" class="bfbe-cmp__hint" aria-expanded="false" aria-controls="bfbe-UID-n2">?</button>
             <span class="bfbe-cmp__note" id="bfbe-UID-n2" hidden>Note</span>]</th>
          <td class="bfbe-cmp__cell bfbe-cmp__value [bfbe-cmp__value--hl]">
            <span class="bfbe-cmp__label" aria-hidden="true">Plan name</span>
            <span class="bfbe-cmp__yes"><svg class="bfbe-cmp__mark bfbe-cmp__mark--own"></svg><span class="bfbe-sr">Yes</span></span></td>
```

- Root: `data-bfbe-cards` holds the **Below** width in cards mode and is empty otherwise; `data-bfbe-sticky` is `1` or `0`; `--bfbe-cmp-cols` is the plan count. The root is a size container (`container-type: inline-size`).
- A cell value is plain text, or `.bfbe-cmp__yes` / `.bfbe-cmp__no` around the pack's stroked SVG (or the chosen icon as `<i class="... bfbe-cmp__mark">`) with hidden Yes or No.
- `.bfbe-cmp__label` repeats the plan name in every value cell; it is `display: none` outside the cards layout.
- The script handles the note buttons and nothing else: a click flips the note's `hidden` and the button's `aria-expanded`. It binds on load and again after Bricks' AJAX events (pagination, query results, popup loaded). Cards and the sticky column are CSS.
- In the builder canvas every table tag is a `div` carrying the same classes, laid out with `display: table-*`.
- Most colour and size controls write custom properties on the root: `--bfbe-cmp-hl`, `-bg`, `-head-bg`, `-feature-bg`, `-stripe`, `-line`, `-yes`, `-no`, `-yes-bg`, `-no-bg`, `-btn`, `-btn-hover`, `-hint`, `-icon`, `-mark-pad`, `-plan-min`, `-min`, `-col1`.
- The caption sits in by the cells' own side padding, `padding: 12px 16px` (since 2026-10-30), so a rounded
  `tableBorder` no longer clips it; **Caption padding** (`captionPadding`, per breakpoint) writes to `.bfbe-cmp__caption`.
- The root always carries `data-bfbe-cmp-diff` (`fill` or `dot`), `data-bfbe-cmp-cols` (`lines` with **Lines between
  columns**, `columnLines`) and `data-bfbe-cmp-key`.
- **Products being compared** (`source: "compare"`, Pro 2.0) adds `bfbe-cmp--products`, `data-bfbe-list-row="compare:<page>:<element id>"`
  and `data-bfbe-list-have` (the ids drawn) to the root. Each product's header is `th.bfbe-cmp__plan.bfbe-cmp__product`
  holding, as **Each column shows** (`cmpShow`) picks, `span.bfbe-cmp__img`, `a.bfbe-cmp__name` (kept, `hidden`, when not
  picked), `span.bfbe-cmp__price`, `span.bfbe-cmp__rating` with `.bfbe-cmp__rating-words`, `span.bfbe-cmp__stock`
  (`--out` when sold out), `form.bfbe-cmp__cart` with `button.bfbe-cmp__btn[name=add-to-cart]` or an `a.bfbe-cmp__btn`,
  and `form.bfbe-cmp__remove-form` with `button.bfbe-cmp__remove`. Each fact row is
  `tr.bfbe-cmp__row[data-bfbe-cmp-fact="attr:pa_material|dimensions|weight|sku|meta:care"]`, plus
  `bfbe-cmp__row--differs` with **Highlight**; an empty cell is `span.bfbe-cmp__none` and a hidden "Not given". With
  nothing to compare the root holds only `p.bfbe-cmp__empty`.
- Controls that write to parts: `cellPadding` to `.bfbe-cmp__cell`, `tableBorder` to `.bfbe-cmp__scroll`, `markBorder` to `.bfbe-cmp__yes` and `.bfbe-cmp__no`, `buttonColor` to `.bfbe-cmp__btn span`, `valueAlign` to `.bfbe-cmp__value` and `.bfbe-cmp__plan`, `groupBackground` to `.bfbe-cmp__group`, `hintColor` to `.bfbe-cmp__hint`. Each typography control writes to the part it names.

## Wiring to other elements

With the typed source it stands alone: plan buttons are plain links from each plan row's **Link** (`link`).

- **Products being compared** draws the visitor's compare list, four products at most, filled by **BFB Compare Button**
  (`bfbe-compare-button`) on product pages and cards and shown in **BFB Compare Tray** (`bfbe-compare-tray`). Put the
  table on the page chosen as the compare page (Shop, Customers) and link to it with `{bfbe_compare_url}`. Needs the
  shop's **Lists** switch (hub: `bfbe-shop`).
- A Remove redraws every such table on the page; on a cached page the lists' script
  draws it again from the visitor's own list after load. A query loop of `bfbeShopCompare` (`bfbe-shop-loops`) is the
  card-by-card alternative.

- On a site with the Dark Mode Toggle, its dark state turns the plan button's words black or white from the fill behind them. A **Label colour** (`buttonColor`) you set wins in both states.
- To style it from a stylesheet, add a class in `_cssClasses` and scope part selectors under it (`.plans-compare .bfbe-cmp__btn`), never under `_cssId`: component instances share ids.

## Verified patterns

Three-plan comparison that scrolls sideways with a sticky features column, group headings, text values and one highlighted plan with a badge. From the demo page `demo-bfb-comparison-table`, the plan rows' stray `note` keys removed (plans have no Note field). The button pairs **Background** (`buttonBackground`) with **Label colour** (`buttonColor`).

```json
{"name": "bfbe-comparison-table", "settings": {
  "caption": "Plans compared", "sticky": true, "narrow": "scroll", "valueAlign": "center",
  "cellPadding": {"top": "11", "right": "16", "bottom": "11", "left": "16"},
  "tableBackground": {"hex": "#ffffff"}, "headBackground": {"hex": "#ffffff"}, "stripeBackground": {"hex": "#f7f8fa"},
  "lineColor": {"hex": "#e9ecf1"}, "groupBackground": {"hex": "#f7f8fa"}, "highlightBackground": {"hex": "#f0ecff"},
  "tickColor": {"hex": "#6e44ff"}, "crossColor": {"hex": "#475467"},
  "badgeBackground": {"hex": "#6e44ff"}, "badgeTypography": {"color": {"hex": "#ffffff"}},
  "buttonBackground": {"hex": "#101828"}, "buttonColor": {"hex": "#ffffff"}, "buttonBackgroundHover": {"hex": "#6e44ff"},
  "plans": [
    {"name": "Crew", "price": "£19 per engineer", "button": "Start a trial", "link": {"type": "external", "url": "#crew"}},
    {"name": "Company", "price": "£29 per engineer", "badge": "Most picked", "highlight": true, "button": "Start a trial", "link": {"type": "external", "url": "#company"}},
    {"name": "Fleet", "price": "£42 per engineer", "button": "Talk to sales", "link": {"type": "external", "url": "#fleet"}}
  ],
  "features": [
    {"label": "Out on the job", "heading": true},
    {"label": "Jobs board and scheduling", "values": "yes | yes | yes"},
    {"label": "Route planning", "values": "no | yes | yes"},
    {"label": "Live fleet tracking", "values": "no | no | yes"},
    {"label": "Money and support", "heading": true},
    {"label": "Accounts export", "values": "CSV | Xero, Sage | Xero, Sage, API"},
    {"label": "Answer within", "values": "Two days | Four hours | One hour"}
  ]
}}
```

Stacks into one card per feature below 768px of its own width, with a note behind a button and ticks and crosses on tinted chips. From the fixture `fixture-comparison-table`, trimmed to the settings that make it; digits stay text. The Agency plan sets no button.

```json
{"name": "bfbe-comparison-table", "settings": {
  "caption": "Plans", "sticky": true, "narrow": "cards", "stackBelow": "768",
  "tickBackground": {"hex": "#dcfce7"}, "crossBackground": {"hex": "#fee2e2"}, "markPadding": "5px",
  "plans": [
    {"name": "Starter", "price": "£9 / month", "button": "Choose", "link": {"type": "external", "url": "#starter"}},
    {"name": "Pro", "price": "£29 / month", "badge": "Popular", "highlight": true, "button": "Choose", "link": {"type": "external", "url": "#pro"}},
    {"name": "Agency", "price": "£79 / month"}
  ],
  "features": [
    {"label": "Basics", "heading": true},
    {"label": "Sites", "values": "1 | 5 | Unlimited"},
    {"label": "Support", "values": "Email | Priority | Priority", "note": "Priority means a reply within a working day."},
    {"label": "Extras", "heading": true},
    {"label": "Updates", "values": "yes | yes | yes"},
    {"label": "White label", "values": "no | no | yes"}
  ]
}}
```

Chosen icons in place of the drawn tick and cross, two plans, no buttons. From the fixture `fixture-comparison-table-icons`. An icon setting is `{library, icon}`, as Bricks' icon picker stores it.

```json
{"name": "bfbe-comparison-table", "settings": {
  "tickIcon": {"library": "fontawesomeSolid", "icon": "fas fa-circle-check"},
  "crossIcon": {"library": "fontawesomeSolid", "icon": "fas fa-circle-xmark"},
  "iconSize": "18px", "tickColor": {"hex": "#c9a227"},
  "plans": [{"name": "Free", "price": "£0"}, {"name": "Pro", "price": "£29 / month", "highlight": true}],
  "features": [
    {"label": "Updates", "values": "yes | yes"},
    {"label": "Priority support", "values": "no | yes"},
    {"label": "White label", "values": "no | no"}
  ]
}}
```

Products being compared, with the material, size, weight, SKU and two custom fields as rows and the rows that differ
filled. From the fixture `fixture-shop-p9-compare` (its `tbl-hl` table). Its twin there sets `cmpOnlyDiff: true` and
`cmpShow: ["name", "price", "remove"]` instead of `cmpHighlight`.

```json
{"name": "bfbe-comparison-table", "settings": {
  "source": "compare", "caption": "Your products side by side", "cmpHighlight": true, "_cssClasses": "tbl-hl",
  "cmpRows": ["attr:pa_material", "dimensions", "weight", "sku"], "cmpMeta": "p9_origin, p9_care"
}}
```

## Gotchas

- **Both repeaters need a row.** With the typed source and no plan or no feature the page gets no markup at all; the canvas shows "Add a plan and a feature." <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:630 -->
- **A fixed set of words draws marks.** `yes`, `true`, `y`, `✓` and `✔` draw a tick; `no`, `false`, `n`, `✗`, `✕` and a lone hyphen draw a cross, case and spaces ignored. `1` and `0` stay text. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:606-617 -->
- **Per plan is matched by position.** **Per plan** (`values`) splits on `|` after dynamic data resolves: values past the plan count are dropped, a missing one leaves its cell empty, and a tag whose value holds a bar adds cells. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:709,718-721 -->
- **A plan button needs both Button label and Link.** A **Button label** (`button`) without a **Link** (`link`) draws nothing, on the page and in the canvas. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:690-697 -->
- **An empty dynamic value draws nothing.** A **Badge**, **Price** or **Note** whose tag resolves to nothing draws no badge pill, price line or note button (since BFB Elements 1.0.0; before it, empty ones). <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php render(); measured 2026-10-12 with dev/comparison-table-probe.mjs on fixture-comparison-table-empty -->
- **The button fill is the text colour until Background is set.** Its fill defaults to `currentColor` on the link, which inherits the plan cell's colour, so the highlighted plan's **Text** (`highlightColor`) or a colour in the button's **Typography** recolours the fill, not the words. <!-- src: src/elements/comparison-table/comparison-table.css:12,46-51; plugins/bfb-elements/includes/class-assets.php:66-69,78 -->
- **The sticky column needs something to scroll.** **Sticky features column** (`sticky`) holds the first column while the table is wider than the element; the header row never sticks, and below the cards width the column is static. <!-- src: src/elements/comparison-table/comparison-table.css:72-86 -->
- **A sticky column must be opaque.** The features column paints **Features background** (`featureBackground`), else its row's colour, else **Background** (`tableBackground`); a translucent value lets plan cells show through as they scroll under it. <!-- src: src/elements/comparison-table/comparison-table.css:36-39; docs/elements/comparison-table.md "Features column background" -->
- **Sideways scroll starts at a computed width.** The table will not shrink below 190px plus **Narrowest plan column** (`planMinWidth`, 132px) per plan. **Smallest table width** (`tableMinWidth`) replaces that sum, after which `planMinWidth` changes nothing. Button labels never wrap, so a long one widens its column. <!-- src: src/elements/comparison-table/comparison-table.css:20-21,29,46; docs/elements/comparison-table.md "round 355" -->
- **Cards follow the element's width, not the screen.** **Below** (`stackBelow`) is measured on the table's own container, so a table in a narrow column stacks on a desktop; above that width a cards table is still a table and scrolls. <!-- src: src/elements/comparison-table/comparison-table.css:23,83-86; docs/elements/comparison-table.md "round 355" -->
- **A width of your own (BFB Elements Pro 1.3.2).** `stackBelow: "custom"` with `stackWidth` (`"700px"`, `"70rem"`, `"40em"`; a bare number is px; up to 3000px or 200 rem/em) stacks at that width or narrower. A rem follows the site's root font size (10px on both sites measured, set to 62.5%: never assume 16px), an em the table's own font size. A `stackWidth` in another unit (vw, %), or none, stacks at the default 768px, and the builder says "Custom width takes px, rem or em." A table on a preset is unchanged and carries no extra markup; a custom one carries one small style block. <!-- src: plugins/bfb-elements-pro/includes/class-stack-width.php; plugins/bfb-elements-pro/elements/comparison-table.php:647-654,692-697; docs/elements/*table.md "Custom stacking width (1.3.2)"; bfb-elements dev/stack-width-probe.cjs, 34 readings -->
- **The canvas draws divs.** In the builder every table, row, cell and caption tag is a `div` with the same classes; `scope`, the caption and the table semantics exist on the frontend. <!-- src: plugins/bfb-elements/includes/abstract-element.php:411-421; plugins/bfb-elements-pro/elements/comparison-table.php:656-661 -->
- **A group heading row drops its values and counts in the stripe.** **Use as a group heading** (`heading`) spans every column, ignores **Per plan** and **Note**, and takes a place in the alternate-row count. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:705-708; src/elements/comparison-table/comparison-table.css:38 -->

- **The compare source needs WooCommerce and Lists.** It is offered only while WooCommerce is active; without the
  Lists switch the builder says "Needs WooCommerce and the Lists feature on." and the page draws nothing. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:59-61, :886-893 -->
- **The builder shows three products, the page the visitor's.** Before anything is compared the canvas draws three of
  the shop's products to design with; the page shows **While there is nothing** (`cmpEmpty`) in place of the table. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:899-916, :926-930 -->
- **The typed parts leave with the typed source.** With `source: "compare"`, Plans, Features, Ticks and crosses, the
  badge, the plan highlight, group headings and notes are hidden and do nothing; product cells are words, never marks. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:41-51, :716-726 -->
- **Highlight marks rows, not a plan.** `cmpHighlight` marks every row whose values differ (case ignored), with
  `cmpDiffMark` `fill` or `dot`; **Only differences** (`cmpOnlyDiff`) acts from two products, and a row no product has a
  value for is always left out. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:980-988 -->
- **Rows unset means every attribute, then size, weight and SKU.** Attributes come in the order they first appear; a
  custom field key that starts with `_` is skipped and its row is named from the key (`p9_care` reads "P9 care"). <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:849-877 -->
- **Add to cart is a post only for a simple product.** A simple, purchasable product in stock gets WooCommerce's add to
  cart post with **Add to cart words** (`cmpCartText`); any other is a link to its page in WooCommerce's own words. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:964-971 -->
- **The caption moved in (2026-10-30).** A caption saved before now sits in 16px at the sides with 12px above and below;
  set `captionPadding` to place it otherwise. <!-- src: src/elements/comparison-table/comparison-table.css:31-33; docs/SHOP-LABELS-2.0.0.md "BFB Comparison Table: the caption" -->

## Never do

- Do not add a typed table without a row in both `plans` and `features`.
- Do not write a hyphen for "not applicable" or `1` and `0` for yes and no: a hyphen draws a cross and digits stay text.
- Do not set a plan's `button` without its `link`.
- Do not colour the plan button through `highlightColor` or `buttonTypography`; set `buttonBackground` and `buttonColor`.
- Do not set `stackBelow` or `labelTypography` without `narrow: "cards"`.
- Do not give a `sticky: true` table a translucent `tableBackground` or `featureBackground`.
- Do not set `tableMinWidth` and expect `planMinWidth` to widen the table.
- Do not judge the table's semantics from the builder canvas; check the frontend.
- Do not set `plans`, `features`, `tickIcon` or the badge and highlight colours with `source: "compare"`; they are hidden there.
- Do not read `cmpHighlight` as a plan highlight; it marks the rows that differ.
- Do not judge a compare table in the builder by its three sample products; check a page with a compare list.
