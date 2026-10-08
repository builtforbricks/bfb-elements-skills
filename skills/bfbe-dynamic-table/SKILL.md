---
name: bfbe-dynamic-table
description: "Use when placing, wiring or styling BFB Dynamic Table (`bfbe-dynamic-table`): a real table built on the server from typed rows, a CSV file, an ACF repeater or a query loop, with seven cell formats. Read before writing its settings."
---

# BFB Dynamic Table (`bfbe-dynamic-table`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-dynamic-table.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/dynamic-table/

## What it is
A real table built on the server from typed rows, a CSV file, an ACF repeater or a query loop, with seven cell formats. Sorting, search, filters and paging work on the rows already in the page, which are all there before any script runs. Those four sources are the bounds of what it reads, and nothing in it edits the data.

**Not for:** Sorting, search, filters and paging run in the browser over rows already in the page, and nothing in it edits data. A large data set that needs paging on the server, or rows that visitors edit, needs a different approach.

**Costs a page:** CSS 2.79 KB, JS 2.60 KB (gzipped), no dependencies, loaded only on pages that use it.

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

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
