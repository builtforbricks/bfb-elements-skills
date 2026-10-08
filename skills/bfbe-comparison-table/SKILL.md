---
name: bfbe-comparison-table
description: "Use when placing, wiring or styling BFB Comparison Table (`bfbe-comparison-table`): a plan or pricing comparison with plans across the top and features down the side, ticks, crosses or text in each cell, a highlighted plan, notes and group headings. Read before writing its settings."
---

# BFB Comparison Table (`bfbe-comparison-table`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-comparison-table.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/comparison-table/

## What it is
Plans across the top and features down the side, with ticks, crosses or text in each cell. It is a real table with scoped headers, an optional caption, an optional sticky features column and notes behind small buttons. On narrow screens it scrolls sideways, or stacks into one card per feature below a width measured on the table itself.

**Not for:** Plans and features are rows you enter in two repeaters, so it suits a short, hand-written comparison. Records from posts or a file fit a table that reads its rows from a source; this one does not sort or filter.

**Costs a page:** CSS 1.57 KB, JS 0.47 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Plans (`bfbePlans`)
- `plans` (repeater) **Plans**. Add one row per plan. Each row sets its Name, Price, Badge, Highlight, Button label and Link. Name, Price, Badge and Button label take dynamic data.

### Features (`bfbeFeatures`)
- `features` (repeater) **Features**. Add one row per feature. Each row has a Feature name, Per plan values, a Note and Use as a group heading. Feature, Per plan and Note take dynamic data.
Styling, in the schema file: `hintSize`.

### Table (`bfbeTable`)
- `caption` (text) **Caption**: dynamic data accepted. A title shown above the table, which screen readers hear as the table's caption. It takes dynamic data.
- `firstColumn` (text) **Features column heading**: placeholder Features; dynamic data accepted. The words at the top of the features column, Features unless set. It takes dynamic data.
- `sticky` (checkbox) **Sticky features column**. Off by default. Tick it to keep the features column in view while the plan columns scroll sideways beneath it.
- `narrow` (select) **On narrow screens**: options: `scroll` Scroll sideways (default), `cards` One card per feature. Scroll sideways is the default. One card per feature stacks the plans above a card for each feature.
- `stackBelow` (select) **Below**: options: `480` 480px, `640` 640px, `768` 768px (default), `992` 992px; only when `narrow` is `cards`. The width at which cards take over, 768px unless set. It is measured on the table's own container, not the screen.
Styling, in the schema file: `planMinWidth`, `tableMinWidth`.

### Look (`bfbeLook`)
Styling only, every key in the schema file: `highlightBackground`, `highlightColor`, `featureTypography`, `valueTypography`, `groupTypography`, `firstColumnWidth`, `cellPadding`, `tableBackground`, `valueAlign`, `lineColor`, `headBackground`, `featureBackground`, `stripeBackground`, `groupBackground`, `tableBorder`, `hintBackground`, `hintColor`, `captionTypography`, `noteTypography`, `labelTypography`.

### Ticks and crosses (`bfbeMarks`)
- `tickIcon` (icon) **Tick icon**. Pick any icon from the picker to replace the drawn tick. Cross icon does the same for the cross.
- `crossIcon` (icon) **Cross icon**
Styling, in the schema file: `tickColor`, `crossColor`, `iconSize`, `tickBackground`, `crossBackground`, `markPadding`, `markBorder`.

### Plan header (`bfbePlanLook`)
Styling only, every key in the schema file: `headTypography`, `priceTypography`, `badgeTypography`, `badgeBackground`, `badgePadding`, `badgeBorder`, `buttonBackground`, `buttonColor`, `buttonTypography`, `buttonPadding`, `buttonBorder`, `buttonBackgroundHover`, `buttonColorHover`.

## What it guarantees for accessibility (do not undo)
- In the table layout, plan and feature headings are header cells with scope col, row or colgroup.
- A Caption becomes the table's own caption element, and ticks and crosses carry visually hidden text, Yes or No.
- Each note button is a native button with aria-expanded and aria-controls and a hidden name, Details; Enter or Space shows and hides its note.
- Plan buttons are real links in the Tab order, and the plan names repeated for the card layout are hidden from assistive technology.
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
- Controls that write to parts: `cellPadding` to `.bfbe-cmp__cell`, `tableBorder` to `.bfbe-cmp__scroll`, `markBorder` to `.bfbe-cmp__yes` and `.bfbe-cmp__no`, `buttonColor` to `.bfbe-cmp__btn span`, `valueAlign` to `.bfbe-cmp__value` and `.bfbe-cmp__plan`, `groupBackground` to `.bfbe-cmp__group`, `hintColor` to `.bfbe-cmp__hint`. Each typography control writes to the part it names.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing. Plan buttons are plain links from each plan row's **Link** (`link`).

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

## Gotchas

- **Both repeaters need a row.** With no plan or no feature the page gets no markup at all; the canvas shows "Add a plan and a feature." <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:630 -->
- **A fixed set of words draws marks.** `yes`, `true`, `y`, `✓` and `✔` draw a tick; `no`, `false`, `n`, `✗`, `✕` and a lone hyphen draw a cross, case and spaces ignored. `1` and `0` stay text. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:606-617 -->
- **Per plan is matched by position.** **Per plan** (`values`) splits on `|` after dynamic data resolves: values past the plan count are dropped, a missing one leaves its cell empty, and a tag whose value holds a bar adds cells. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:709,718-721 -->
- **A plan button needs both Button label and Link.** A **Button label** (`button`) without a **Link** (`link`) draws nothing, on the page and in the canvas. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:690-697 -->
- **Emptiness is tested before dynamic data.** A **Badge**, **Price** or **Note** whose tag resolves to nothing still draws an empty badge pill, an empty price line or a note button with nothing behind it. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:683-689,710-715 -->
- **The button fill is the text colour until Background is set.** Its fill defaults to `currentColor` on the link, which inherits the plan cell's colour, so the highlighted plan's **Text** (`highlightColor`) or a colour in the button's **Typography** recolours the fill, not the words. <!-- src: src/elements/comparison-table/comparison-table.css:12,46-51; plugins/bfb-elements/includes/class-assets.php:66-69,78 -->
- **The sticky column needs something to scroll.** **Sticky features column** (`sticky`) holds the first column while the table is wider than the element; the header row never sticks, and below the cards width the column is static. <!-- src: src/elements/comparison-table/comparison-table.css:72-86 -->
- **A sticky column must be opaque.** The features column paints **Features background** (`featureBackground`), else its row's colour, else **Background** (`tableBackground`); a translucent value lets plan cells show through as they scroll under it. <!-- src: src/elements/comparison-table/comparison-table.css:36-39; docs/elements/comparison-table.md "Features column background" -->
- **Sideways scroll starts at a computed width.** The table will not shrink below 190px plus **Narrowest plan column** (`planMinWidth`, 132px) per plan. **Smallest table width** (`tableMinWidth`) replaces that sum, after which `planMinWidth` changes nothing. Button labels never wrap, so a long one widens its column. <!-- src: src/elements/comparison-table/comparison-table.css:20-21,29,46; docs/elements/comparison-table.md "round 355" -->
- **Cards follow the element's width, not the screen.** **Below** (`stackBelow`) is measured on the table's own container, so a table in a narrow column stacks on a desktop; above that width a cards table is still a table and scrolls. <!-- src: src/elements/comparison-table/comparison-table.css:23,83-86; docs/elements/comparison-table.md "round 355" -->
- **The canvas draws divs.** In the builder every table, row, cell and caption tag is a `div` with the same classes; `scope`, the caption and the table semantics exist on the frontend. <!-- src: plugins/bfb-elements/includes/abstract-element.php:411-421; plugins/bfb-elements-pro/elements/comparison-table.php:656-661 -->
- **A group heading row drops its values and counts in the stripe.** **Use as a group heading** (`heading`) spans every column, ignores **Per plan** and **Note**, and takes a place in the alternate-row count. <!-- src: plugins/bfb-elements-pro/elements/comparison-table.php:705-708; src/elements/comparison-table/comparison-table.css:38 -->

## Never do

- Do not add the element without a row in both `plans` and `features`.
- Do not write a hyphen for "not applicable" or `1` and `0` for yes and no: a hyphen draws a cross and digits stay text.
- Do not set a plan's `button` without its `link`.
- Do not colour the plan button through `highlightColor` or `buttonTypography`; set `buttonBackground` and `buttonColor`.
- Do not set `stackBelow` or `labelTypography` without `narrow: "cards"`.
- Do not give a `sticky: true` table a translucent `tableBackground` or `featureBackground`.
- Do not set `tableMinWidth` and expect `planMinWidth` to widen the table.
- Do not judge the table's semantics from the builder canvas; check the frontend.
