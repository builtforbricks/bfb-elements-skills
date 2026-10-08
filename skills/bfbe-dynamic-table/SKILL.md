---
name: bfbe-dynamic-table
description: "Use when a page needs a sortable, searchable or filterable data table with paging, built from typed rows, a CSV file, an ACF repeater or a query loop of posts: BFB Dynamic Table (`bfbe-dynamic-table`), with seven cell formats and stacked or card rows on narrow screens. Read before writing its settings."
---

# BFB Dynamic Table (`bfbe-dynamic-table`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-dynamic-table.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/dynamic-table/

## What it is
A real table built on the server from typed rows, a CSV file, an ACF repeater or a query loop, with seven cell formats. Sorting, search, filters and paging work on the rows already in the page, which are all there before any script runs. Those four sources are the bounds of what it reads, and nothing in it edits the data.

**Not for:** Sorting, search, filters and paging run in the browser over rows already in the page, and nothing in it edits data. A large data set that needs paging on the server, or rows that visitors edit, needs a different approach.

**Costs a page:** CSS 2.79 KB, JS 2.60 KB (gzipped), no dependencies, loaded only on pages that use it. Only where used, the dropdowns (the sort field and the filters' selects): JS 1.05 KB.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Source (`bfbeSource`)
- `source` (select) **Rows come from**: options: `manual` Text typed here (default), `csv` A CSV file, `acf` An ACF repeater, `loop` A query loop. Choose Text typed here (the default), A CSV file, An ACF repeater or A query loop. A query loop brings Bricks' Query loop switch and Query, and takes a dynamic tag in each column.
- `rows` (textarea) **Rows**: dynamic data accepted; only when `source` is not `csv` or `acf` or `loop`. Type one row per line, with commas between the cells. It is read as CSV, so a quoted cell can hold commas, and it takes dynamic data.
- `file` (file) **CSV file**: only when `source` is `csv`. Choose the CSV file to read. It is offered when Rows come from is A CSV file.
- `headerRow` (checkbox) **Header row**: only when `source` is not `acf` or `loop`. Tick it to use the top row as headings for any column whose Heading is empty. With no columns set, it makes one column per cell.
- `acfField` (text) **Repeater field name**: placeholder price_list; only when `source` is `acf`. Type the name of the ACF repeater to read. Each column's Value then names a sub field.

### Columns (`bfbeColumns`)
- `columns` (repeater) **Columns**. Add one row per column, in order. Each has Heading, Value, Format, Sortable, Width, and Align, which places the text at the Start (the default), Centre or End.

### Search and pages (`bfbeFeatures`)
- `search` (checkbox) **Search box**. Tick it to add a search field above or below the table, as Position sets. Typing hides rows that have no matching text in any cell.
- `searchLabel` (text) **Label**: placeholder Search; dynamic data accepted; only when `search` is set. Under Search, set the hidden name and the placeholder of the search field. It reads Search unless you change it.
- `searchPlace` (select) **Position**: options: `above` Above the table (default), `below` Below the table; only when `search` is set. Under Search, put the search box Above the table (the default) or Below the table.
- `searchAlign` (align-items) **Aligned**: only when `search` is set
- `sortLabel` (text) **Label**: placeholder Sort by; dynamic data accepted; only when `responsive` is not `` or `scroll`. Under Search, set the hidden name and the placeholder of the search field. It reads Search unless you change it.
- `emptyText` (text) **Text**: placeholder No matching rows.; dynamic data accepted. Under Nothing found, type what shows when no row matches. It reads No matching rows unless you change it, and it takes dynamic data.
- `pageSize` (number) **Rows per page**: placeholder All. Set a number to page the table, with Previous page and Next page buttons and a count such as 1 to 10 of 42. All rows show unless set.
- `pagerLayout` (select) **Position**: options: `range-start` Count left, arrows right (default), `range-end` Arrows left, count right, `start` Both left, `center` Both centred, `end` Both right; only when `pageSize` is set. Under Search, put the search box Above the table (the default) or Below the table.
Styling, in the schema file: `searchBackground`, `searchBorder`, `searchTypography`, `searchPadding`, `searchWidth`, `toolsGap`, `ddBackground`, `ddBorder`, `ddTypography`, `ddPadding`, `ddWidth`, `ddListBackground`, `ddListBorder`, `ddListShadow`, `ddListTypography`, `ddOptionPadding`, `ddOptionHover`, `ddChosenBackground`, `ddChosenColor`, `emptyTypography`, `pagerGap`.

### Filters (`bfbeFilter`)
- `filters` (repeater) **Filters**. Add one row per filter. Each has a Column number, Shown as (Chips, A select, A number range or A date range), a Label, the column heading unless set, an Everything label, and Lowest label and Highest label for a range.
- `filterUrl` (checkbox) **Filters in the URL**: only when `filters` is set. Tick it to write a choice into the address, so a reload keeps it and a link shares it.
- `filterRow` (checkbox) **On their own row**: only when `filters` is set. Off by default, so filters share the search row. Tick it to give them a row of their own, with Row sits (Above the table, the default, or Below the table), They run (Across or Down) and Line up.
- `filterPlace` (select) **Row sits**: options: `above` Above the table (default), `below` Below the table; only when `filterRow` is set and `filters` is set
- `filterDirection` (select) **They run**: options: `row` Across (default), `column` Down; only when `filterRow` is set and `filters` is set
- `filterAlign` (justify-content) **Line up**: only when `filterRow` is set and `filters` is set
- `filterStretch` (checkbox) **Fill the row**: only when `filters` is set. Tick it to stretch the filters across their row.
- `filterLabels` (checkbox) **Show each label**: only when `filters` is set. Tick it to show each filter's label on the page. Screen readers hear the label either way.
Styling, in the schema file: `filterGap`, `chipTypography`, `chipBackground`, `chipHoverBackground`, `chipOnBackground`, `chipOnColor`, `chipBorder`, `chipPadding`, `filterSpace`, `filterWidth`, `filterLabelTypography`, `rangeWidth`, `rangeBackground`, `rangeBorder`, `rangeTypography`.

### Table (`bfbeTable`)
- `caption` (text) **Caption**: dynamic data accepted. Type a caption that names the table. It takes dynamic data, and screen readers hear it as the table's caption.
- `stickyHeader` (checkbox) **Sticky header**. Tick it to keep the header in view while rows scroll inside the Table height, which is 70vh unless set.
- `responsive` (select) **On narrow screens**: options: `scroll` Scroll sideways (default), `stack` Stack each row, `cards` Cards. Scroll sideways is the default. Stack each row and Cards drop the header row below a width and move sorting to a Sort by field.
- `stackBelow` (select) **Below**: options: `480` 480px, `640` 640px (default), `768` 768px, `992` 992px; only when `responsive` is not `` or `scroll`. Choose the width where stacking or cards take over: 480, 640, 768 or 992px, 640px unless set. It is measured on the table's own container.
Styling, in the schema file: `captionTypography`, `captionPadding`, `captionMargin`, `tableBorder`, `maxHeight`, `colMin`.

### Header (`bfbeHeader`)
- `headerSit` (select) **Text and icon sit**: options: `start` At the start, `center` In the centre, `end` At the end, `apart` Apart; writes CSS. Place each heading's text and sort icon At the start, In the centre, At the end or Apart, with the text at the start and the icon at the end. Unset, the typography's alignment stands.
- `sortIcon` (icon) **Icon**. Choose your own sort icon. Headings show two arrows until you choose one, and your icon turns for ascending.
Styling, in the schema file: `headerTypography`, `headerBackground`, `headerPadding`, `headerBorder`, `sortIconSize`, `arrowColor`.

### Cells (`bfbeCells`)
- `cellAlign` (select) **Vertical align**: options: `middle` Middle (default), `top` Top, `bottom` Bottom; writes CSS. Place cell contents at the Middle (the default), Top or Bottom.
Styling, in the schema file: `cellTypography`, `cellPadding`, `cellBorder`, `labelTypography`, `imageSize`, `imageBorder`.

### Rows (`bfbeRows`)
- `zebra` (checkbox) **Striped rows**. Tick it to tint every other row with the Stripe background.
Styling, in the schema file: `rowBackground`, `rowBorder`, `rowGap`, `zebraBackground`.

### Highlights (`bfbeHigh`)
- `noRowHover` (checkbox) **No hover highlight**. Tick it to stop rows lighting up under the pointer or while focus is inside them.
Styling, in the schema file: `rowHoverBackground`, `rowHoverColor`, `sortedBackground`, `sortedHeadBackground`, `sortedHeadColor`.

### Badges (`bfbeBadges`)
Styling only, every key in the schema file: `badgeBackground`, `badgeColor`, `badgeTypography`, `badgePadding`, `badgeBorder`.

### Page buttons (`bfbePager`)
The whole group shows only when `pageSize` is set.
Styling only, every key in the schema file: `pageBackground`, `pageColor`, `pagerTypography`, `pageGap`, `pageButtonSize`, `pagePadding`, `pageIconSize`, `pageBorder`, `pageShadow`, `pageDim`, `pageHoverBackground`, `pageHoverColor`, `rangeColor`.

## What it guarantees for accessibility (do not undo)
- Each sortable heading holds a real button, and its header cell carries aria-sort, which reads none, ascending or descending as the sort changes.
- In the scrolling layout the table keeps its native semantics: header cells carry scope col and a Caption is the caption element.
- Changes from search, filters and paging are announced in a polite live region as a row count, a range or the Nothing found text.
- Filter chips are buttons with aria-pressed; a select filter is a combobox with a listbox that answers arrow keys, Home, End, Enter, Space and Escape.
- With Stack each row or Cards, the header row is hidden and sorting moves to a Sort by combobox, so no unseen button stays reachable.
<!-- bfbe:generated:end -->

## Rendered DOM

On the frontend, one real table inside a scroll box, with tool rows around it. Square brackets mark what a setting adds:

```html
<div id="brxe-..." class="brxe-bfbe-dynamic-table bfbe-dt bfbe-dt--scroll|stack|cards [bfbe-dt--narrow-640] [bfbe-dt--sticky]
     [bfbe-dt--zebra] [bfbe-dt--no-hover]" data-bfbe-empty="No matching rows." data-bfbe-tools="above" data-bfbe-search="flex-start"
     data-bfbe-pager="range-start" [data-bfbe-page-size="6"] [data-bfbe-filter-url="1"] [data-bfbe-filters="above" data-bfbe-fdir="row" data-bfbe-falign="flex-start"] [data-bfbe-hsit="apart"]>
  [<div class="bfbe-dt__tools bfbe-dt__tools--filters">the filters, on their own row</div>]
  [<div class="bfbe-dt__tools" [data-bfbe-filters-in]>the filters, <label class="bfbe-dt__tool"><input type="search" class="bfbe-dt__search" data-bfbe-search></label>,
     <div class="bfbe-dt__tool bfbe-dt__dd bfbe-dt__tool--sort"><select class="bfbe-dt__dd-select" data-bfbe-sort-select>...</select>
       <button class="bfbe-dt__dd-btn" role="combobox" hidden>...</button><ul class="bfbe-dt__dd-list" role="listbox" hidden>...</ul></div></div>]
  <div class="bfbe-dt__scroll"><table class="bfbe-dt__table" id="bfbe-UID-table">
    [<caption class="bfbe-dt__caption">Caption</caption>]
    <thead class="bfbe-dt__head"><tr class="bfbe-dt__row"><th scope="col" class="bfbe-dt__cell" aria-sort="none">
      <button type="button" class="bfbe-dt__sort" data-bfbe-sort="0">Heading<svg class="bfbe-dt__arrows"></svg></button></th></tr></thead>
    <tbody class="bfbe-dt__body"><tr class="bfbe-dt__row"><td class="bfbe-dt__cell" data-bfbe-sort="4808">
      [<span class="bfbe-dt__label">Heading</span>]<span class="bfbe-dt__value">4,808</span></td></tr></tbody></table></div>
  <p class="bfbe-dt__empty" hidden></p><span class="bfbe-sr" aria-live="polite" data-bfbe-dt-live></span>
  [<div class="bfbe-dt__pager"><span class="bfbe-dt__range"></span><button class="bfbe-dt__page" data-bfbe-page="-1">...</button><button class="bfbe-dt__page" data-bfbe-page="1">...</button></div>]
</div>
```

- A filter carries `data-bfbe-filter="n"`, n its column's zero-based place in **Columns**. Chips: `.bfbe-dt__filter` of `button.bfbe-dt__chip[aria-pressed][data-bfbe-value]`, the Everything chip first with an empty value. A range: `.bfbe-dt__filter.bfbe-dt__pair[data-bfbe-range="range|dates"]` with `input.bfbe-dt__input[data-bfbe-from]` and `[data-bfbe-to]`. A select: a `.bfbe-dt__dd` whose `select` carries the attribute. **Show each label** adds `span.bfbe-dt__legend` before each.
- Formats, inside `.bfbe-dt__value`: Number the localised number; Date a `<time datetime="Y-m-d">` in the site's date format; Badge `span.bfbe-dt__badge`; Image `img.bfbe-dt__img` (an attachment ID at thumbnail size, or a URL with an empty `alt`); Link an `<a>` whose words are the address without its scheme; HTML the markup through `wp_kses_post()`. `data-bfbe-sort` holds the number, the Unix time, or the text.
- `.bfbe-dt__label` is rendered only with **Stack each row** or **Cards**, and shows only below the width.
- The script hides every row, then appends the matching rows in sort order and unhides the current page. It sets `aria-sort` on the headings, `aria-pressed` on chips, `disabled` on a pager button at either end, `is-col-on` on the cells of the column under the pointer, and each heading's `inline-size` as a percentage at start.
- A dropdown gains `.bfbe-dt__dd--on` once its script runs (the select then hidden behind the button), `.is-open` while open and `.bfbe-dt__dd--up` when it opens upwards.
- The root is a size container; Stack and Cards are `@container` rules keyed on `bfbe-dt--narrow-<width>`. In the builder canvas every table tag is a `div` with the same classes.
- Most colours and sizes are custom properties on the root (`--bfbe-dt-head-bg`, `-row-bg`, `-row-on`, `-row-on-color`, `-zebra`, `-row-gap`, `-max`, `-col-min`, `-icon`, `-chip-*`, `-page-*`, `-dd-*`). `sortedBackground` writes `--bfbe-dt-col-on`, the tint of the column under the pointer, not the sorted one.
- `headerBorder` writes to `.bfbe-dt__head .bfbe-dt__row` and `rowBorder` to `.bfbe-dt__body .bfbe-dt__row`, both drawn by the cells (the first and last take the sides and corners); `cellBorder` to the body cells, replacing the row's on the sides it sets; `tableBorder` to `.bfbe-dt__scroll`. The search box's styling controls write to `.bfbe-dt__search`, the `dd*` controls style every dropdown's button and list, and a column's **Width** and **Align** to `--bfbe-dt-col-w` and `--bfbe-dt-col-align` on `.bfbe-dt__cell:nth-child(n)`.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing. Its search box, filters, sort field and pager are parts of it, not elements.

- **A query loop source** is Bricks' own `hasLoop` and `query` on the table itself, offered with `source: "loop"`. The table runs the query once and draws one row per result; a looping parent container would repeat the whole table instead.
- **Filters in the URL** (`filterUrl`) names each parameter after the root's HTML id, `brxe-<id>-f<n>`, n the zero-based column. A `_cssId` renames it, and two tables that share an id (two instances of one component) read the same parameter. Target the table by a class in `_cssClasses`, never `_cssId`.
- The script runs again after Bricks' AJAX pagination, page load, query result and popup events, so a table in a Bricks popup or in AJAX-loaded content starts. For markup added another way, call `window.bfbeDynamicTable()`.
- To style it from a stylesheet, scope part selectors under that class (`.price-table .bfbe-dt__cell`).

## Verified patterns

Typed rows whose first line heads the columns, with no **Columns** list, a search box, 6 rows per page and cards below 640px of its own width. From the demo page `demo-bfb-dynamic-table`, the two chip colours dropped (the demo has no filters, so the panel hides them). Every column here is Text and sortable.

```json
{"name": "bfbe-dynamic-table", "settings": {
  "headerRow": true, "search": true, "pageSize": 6, "responsive": "cards",
  "caption": "Every integration, what it moves and which way",
  "headerBackground": {"hex": "#f7f8fa"}, "headerBorder": {"color": {"hex": "#e9ecf1"}}, "rowBorder": {"color": {"hex": "#e9ecf1"}},
  "sortedBackground": {"hex": "#f0ecff"}, "rowHoverBackground": {"hex": "#f7f8fa"},
  "rows": "Service, What moves, Direction, Plan\nXero, Invoices and payments, Both ways, Company\nSage 50, Invoices and nominal codes, To Sage, Company\nQuickBooks, Invoices and customers, Both ways, Company\nStripe, Card payments on invoices, From Stripe, All plans\nGoCardless, Direct debits, From GoCardless, Company\nGoogle Calendar, Jobs and holidays, Both ways, All plans\nOutlook 365, Jobs and holidays, Both ways, All plans\nwhat3words, Job locations, To Ridgeline, All plans\nTwilio, Job texts to customers, From Ridgeline, Company\nMailchimp, Customers and service dates, To Mailchimp, Fleet\nZapier, Anything else, Both ways, Fleet"
}}
```

A number range, a date range and chips on a row of their own, kept in the URL. From the fixture `fixture-dynamic-table`. The Number and Date formats give the ranges their sort values; the columns have no `key`, so each reads the cell at its own position, and only the two with `sortable: true` sort.

```json
{"name": "bfbe-dynamic-table", "settings": {
  "headerRow": true, "filterUrl": true, "filterRow": true, "filterLabels": true, "filterSpace": "14px", "filterAlign": "space-between",
  "rangeWidth": "10em", "chipOnBackground": {"hex": "#0f766e"}, "chipOnColor": {"hex": "#ffffff"},
  "rows": "Launch, Height (m), Opened, Country\nAlpine Ridge, 4808, 2019-04-12, France\nMont Blanc Way, 4810, 2021-07-01, Italy\nMatterhorn Line, 4478, 2018-11-23, Switzerland\nEiger Trail, 3967, 2022-02-08, Switzerland\nOlympus Path, 2918, 2020-09-30, Greece\nAneto Climb, 3404, 2023-05-19, Spain\nRysy Route, 2501, 2017-06-14, Poland\nGrossglockner, 3798, 2024-01-05, Austria",
  "columns": [
    {"label": "Launch"},
    {"label": "Height (m)", "format": "number", "sortable": true},
    {"label": "Opened", "format": "date", "sortable": true},
    {"label": "Country"}
  ],
  "filters": [
    {"column": 2, "kind": "range", "label": "Height (m)"},
    {"column": 3, "kind": "dates", "label": "Opened"},
    {"column": 4, "kind": "chips", "label": "Country"}
  ]
}}
```

Six pages, the last published at the top, one row each, from a query loop. From the fixture `fixture-dynamic-table`. Each column's `key` is a dynamic tag resolved per result; the Link column shows each address as its words. On a site whose date format is day first, write `{post_date:Y-m-d}`.

```json
{"name": "bfbe-dynamic-table", "settings": {
  "source": "loop", "hasLoop": true,
  "query": {"post_type": ["page"], "posts_per_page": 6, "orderby": "date", "order": "DESC"},
  "columns": [
    {"label": "Title", "key": "{post_title}", "sortable": true},
    {"label": "Published", "key": "{post_date}", "format": "date", "sortable": true},
    {"label": "Link", "key": "{post_url}", "format": "link"}
  ]
}}
```

## Gotchas

- **A column sorts only with `sortable: true`.** The panel ticks **Sortable** when a column is added in the builder; a column written as data without it gets a plain heading and no sort button. <!-- src: plugins/bfb-elements-pro/elements/dynamic-table.php:288-292,1939-1947; docs/API-PROBE.md "12. Control defaults exist only in the builder" -->
- **Header row takes the first line out of the body.** With **Header row** (`headerRow`), that line heads every column whose **Heading** is empty and is never a data row; with no **Columns**, it makes one Text, sortable column per cell. With neither, the page draws nothing. <!-- src: plugins/bfb-elements-pro/elements/dynamic-table.php:1569-1571,1604-1606,1712-1723 -->
- **A column's Value means something different per source.** Typed rows and CSV take a column number from 1 (empty reads the column's own position); ACF takes a sub field name; a query loop takes a dynamic tag, and plain text there prints itself in every row. <!-- src: plugins/bfb-elements-pro/elements/dynamic-table.php:1615-1640 -->
- **A source missing its input draws nothing on the page.** A CSV source with no `file`, an ACF source with no `acfField` or no ACF, and a loop with `hasLoop` off show a notice in the builder only. <!-- src: plugins/bfb-elements-pro/elements/dynamic-table.php:1694-1706; plugins/bfb-elements/includes/abstract-element.php:538-546 -->
- **A query loop table holds one page of its query.** Without `posts_per_page` in `query`, Bricks uses the site's posts per page (10 unless changed), and search, filters and paging act only on the rows rendered; set it, `-1` for all. <!-- src: plugins/bfb-elements-pro/elements/dynamic-table.php:1581-1597; themes/bricks/includes/query.php:568 (Bricks 2.4-beta3) -->
- **Sorting reads each cell's sort value, and a Text cell's is its text.** When every value starts with a number the column sorts by that leading number, so `4,808` sorts as 4 and `2024-03-01` as 2024; use the Number and Date formats. <!-- src: src/elements/dynamic-table/dynamic-table.js:48-51,72-79; plugins/bfb-elements-pro/elements/dynamic-table.php:1674 -->
- **Number and Date read their text strictly.** Number takes a comma as a thousands separator (`1,5` is 15) and an unquoted comma in typed rows or CSV starts a new cell; Date reads slashes month first (`05/04/2024` is 4 May) and leaves `31/12/2024` as text with no sort value. <!-- src: plugins/bfb-elements-pro/elements/dynamic-table.php:1527,1649-1659; docs/elements/dynamic-table.md (first ⚑) -->
- **A filter's Column counts the Columns list, from 1.** Its choices are the values in the rendered rows, and a number past the list draws nothing. A range compares sort values, so give **A number range** a Number column and **A date range** a Date column; a column with no numeric sort values draws no range. <!-- src: plugins/bfb-elements-pro/elements/dynamic-table.php:1793-1832; src/elements/dynamic-table/dynamic-table.js:59-71 -->
- **Search matches what the cells show.** It reads each `.bfbe-dt__value`, case ignored, so `4808` does not find a Number cell that reads `4,808`; the stacked labels are never searched. <!-- src: src/elements/dynamic-table/dynamic-table.js:29-38,55-58 -->
- **Stack and Cards switch at the element's own width.** **Below** (`stackBelow`, 640px unless set) is measured on the table's container, while **Minimum column width** (`colMin`) follows Bricks' screen breakpoints. Below it the header row is hidden, a column's **Width** and **Align** and `colMin` stop applying, and sorting moves to a Sort by field that exists only when some column is sortable. <!-- src: src/elements/dynamic-table/dynamic-table.css:10,147-194; plugins/bfb-elements-pro/elements/dynamic-table.php:1892-1909; docs/elements/dynamic-table.md "Round 405" -->
- **With Cards, the rows' Border is the card's.** Below the width `rowBorder` outlines each card, and above it the same setting outlines each row of the wide table; unset, the cards keep their own line, corners, fill and shadow. <!-- src: src/elements/dynamic-table/dynamic-table.css:92,160; docs/elements/dynamic-table.md "Round 404" -->
- **The sticky header sticks inside the table, not the page.** **Sticky header** (`stickyHeader`) caps the table's box at **Table height** (`maxHeight`, 70vh unless set) and the header sticks while rows scroll in it; a shorter table never scrolls. <!-- src: src/elements/dynamic-table/dynamic-table.css:112-116; plugins/bfb-elements-pro/elements/dynamic-table.php:840-854 -->

## Never do

- Do not leave `sortable` out of a column that should sort; write `"sortable": true`.
- Do not keep numbers or dates that visitors sort or filter by range in the Text format; set `format: "number"` or `"date"`.
- Do not write day-first dates or decimal commas; write `2024-12-31` and `1.5`, and quote a cell that holds a comma.
- Do not set `source: "loop"` without `hasLoop: true` and a `query` that sets `posts_per_page`.
- Do not put a column number or plain text in the `key` of a loop or ACF column; use a dynamic tag or a sub field name.
- Do not count CSV columns in a filter's `column`; count the **Columns** list from 1.
- Do not shape the stacked or card rows with `colMin` or a column's `width` and `align`.
- Do not use `stickyHeader` to pin a header to the page; it sticks only inside the table's own box.
