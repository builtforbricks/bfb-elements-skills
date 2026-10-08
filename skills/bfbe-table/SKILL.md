---
name: bfbe-table
description: "Use when building a static HTML table with BFB Table (`bfbe-table`) and its Table Row and Table Cell children: comparison and spec tables, header rows and row headers, spanning cells, rows from a query loop, a sticky header, or rows that scroll sideways or stack on narrow screens. Read before writing its settings."
---

# BFB Table (`bfbe-table`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-table.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/table/

## What it is
A real HTML table, built from Table Row and Table Cell elements, where each cell can hold any Bricks element. Header cells carry scope col or row, and the caption names the scroll region, so headings stay tied to their cells. On narrow screens the table scrolls sideways or stacks each row, decided by the table's own width through a container query, not by a script.

**Not for:** This is a static layout table: rows and cells are placed by hand or by a query loop, with no sorting, searching or paging. Visitors cannot reorder or filter it, so a data table people explore needs a different element.

**Costs a page:** CSS 1.38 KB, JS 1.15 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Nestable. Its own children: `bfbe-table-row`.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-table",
    "settings": {},
    "children": [
        {
            "name": "bfbe-table-row",
            "settings": {
                "isHeader": true
            },
            "children": [
                {
                    "name": "bfbe-table-cell",
                    "settings": {},
                    "children": [
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "Heading 1"
                            }
                        }
                    ]
                },
                {
                    "name": "bfbe-table-cell",
                    "settings": {},
                    "children": [
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "Heading 2"
                            }
                        }
                    ]
                },
                {
                    "name": "bfbe-table-cell",
                    "settings": {},
                    "children": [
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "Heading 3"
                            }
                        }
                    ]
                }
            ]
        },
        {
            "name": "bfbe-table-row",
            "settings": {},
            "children": [
                {
                    "name": "bfbe-table-cell",
                    "settings": {},
                    "children": [
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "Cell"
                            }
                        }
                    ]
                },
                {
                    "name": "bfbe-table-cell",
                    "settings": {},
                    "children": [
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "Cell"
                            }
                        }
                    ]
                },
                {
                    "name": "bfbe-table-cell",
                    "settings": {},
                    "children": [
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "Cell"
                            }
                        }
                    ]
                }
            ]
        },
        {
            "name": "bfbe-table-row",
            "settings": {},
            "children": [
                {
                    "name": "bfbe-table-cell",
                    "settings": {},
                    "children": [
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "Cell"
                            }
                        }
                    ]
                },
                {
                    "name": "bfbe-table-cell",
                    "settings": {},
                    "children": [
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "Cell"
                            }
                        }
                    ]
                },
                {
                    "name": "bfbe-table-cell",
                    "settings": {},
                    "children": [
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "Cell"
                            }
                        }
                    ]
                }
            ]
        }
    ]
}
```

`bfbe-table-row` (BFB Table Row), 37 controls, schema `../bfbe-schemas/references/elements/bfbe-table-row.json`, nestable itself.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Table (`bfbeTable`)
- `caption` (text) **Caption**: dynamic data accepted. A title that names the table for screen readers. It accepts dynamic data. Show it is Visible by default and can hide the caption from sight.
- `captionMode` (select) **Show it**: options: `visible` Visible (default), `hidden` Hidden; only when `caption` is set
- `responsive` (select) **On narrow screens**: options: `scroll` Scroll sideways (default), `stack` Stack each row. Scroll sideways is the default. Stack each row repeats the column heading beside each value. Stack below sets where: 480, 640, 768 or 992px, 640px by default.
- `stackBelow` (select) **Stack below**: options: `480` 480px, `640` 640px (default), `768` 768px, `992` 992px; only when `responsive` is `stack`
- `stickyHeader` (checkbox) **Sticky header**. Tick it to keep the header row in view while the table scrolls inside the Height you set, 420px by default.
- `bar` (select) **Look**: options: `browser` Browser default (default), `styled` Styled, `hidden` Hidden. Under Scroll bar, pick Browser default, Styled or Hidden. Styled adds Thickness, 8px by default, Thumb, Thumb on hover and Track. Hidden hides the bar, and the table still scrolls.
Styling, in the schema file: `captionTypography`, `minWidth`, `barSize`, `barThumb`, `barThumbHover`, `barTrack`, `barSpace`, `maxHeight`, `columnGap`, `rowGap`, `tableBorder`, `tableBackground`.

### Header row (`bfbeHeader`)
Styling only, every key in the schema file: `headerBackground`, `headerTypography`.

### Cells (`bfbeCells`)
- `cellVerticalAlign` (select) **Vertical align**: options: `top` Top, `middle` Middle (default), `bottom` Bottom; writes CSS. Place cell contents at the Top, Middle or Bottom, with Middle as the default. Change it when cells hold different amounts of text.
Styling, in the schema file: `cellPadding`, `cellBorder`, `cellTypography`, `labelTypography`.

### Rows (`bfbeRows`)
Styling only, every key in the schema file: `stripe`, `rowHover`, `rowLineWidth`, `rowLineColor`.

## What it guarantees for accessibility (do not undo)
- On the published page the table uses real table, tr, th, td and caption elements, not divs.
- Header cells get scope col in a header row, and scope row when Row header is ticked on a Table Cell.
- The scrolling region takes keyboard focus and is named by the caption, or Table when there is no caption.
- The script removes the tab stop and region role when the table fits and nothing overflows.
- When rows stack, the header row is clipped out of sight rather than removed, and each cell gets an aria-hidden copy of its column heading.
<!-- bfbe:generated:end -->

## Rendered DOM

On the page the three elements write real table markup, one part per element:

```html
<div class="bfbe-table bfbe-table--stack bfbe-table--stack-640">
  <div class="bfbe-table__scroll" tabindex="0" role="region" aria-labelledby="bfbe-<id>-caption">
    <table class="bfbe-table__table">
      <caption id="bfbe-<id>-caption" class="bfbe-table__caption">Plans compared</caption>
      <tr class="bfbe-table__row bfbe-table__row--header">
        <th class="bfbe-table__cell bfbe-table__cell--th" scope="col">…</th>
      </tr>
      <tr class="bfbe-table__row">
        <th class="bfbe-table__cell bfbe-table__cell--th" scope="row"><span class="bfbe-table__label" aria-hidden="true">Plan</span>…</th>
        <td class="bfbe-table__cell bfbe-table__cell--span" colspan="2" style="--bfbe-span:2">…</td>
      </tr>
    </table>
  </div>
</div>
```

- Root modifiers: `bfbe-table--scroll` or `bfbe-table--stack` with `bfbe-table--stack-480|640|768|992`; `bfbe-table--spaced` when `columnGap` or `rowGap` has a value; `bfbe-table--sticky`; `bfbe-table--bar-styled` or `bfbe-table--bar-hidden` (none for Browser default). The root is a size container named `bfbe-table`.
- No `<thead>` or `<tbody>` is written. The browser wraps every row in one implied `<tbody>`, so select rows by `.bfbe-table__row`, never `table > tr`.
- `captionMode: "hidden"` adds `bfbe-sr` to the caption, off screen and still announced. With no caption the wrapper carries `aria-label="Table"` instead, and `captionMode` does nothing: it is offered only with a `caption`.
- A looped row prints Bricks' own `div.brx-query-trail` after its last `<tr>`, inside the `<table>` in the served HTML; the browser moves it out above the table. It is Bricks' marker, not the element's.
- The script reads no `data-bfbe-*` attribute and changes two things: it removes `tabindex` and `role` from the wrapper while nothing overflows, and on a stacking table it puts a `.bfbe-table__label` span first in each body cell, shown below the breakpoint.
- Where controls write: `tableBorder` and `tableBackground` to `.bfbe-table__scroll`; the Header row group to `.bfbe-table__row--header .bfbe-table__cell`; the Cells group to `.bfbe-table__cell`, and `labelTypography` to `.bfbe-table__label`. `stripe`, `minWidth`, `maxHeight`, the gaps, the bar values and the row line are custom properties on the root (`--bfbe-table-stripe`, `--bfbe-table-min`, `--bfbe-table-height`, and so on).
- A Table Row's and a Table Cell's own controls write to the cell; **Column width** `colWidth` is `--bfbe-col-w` on it.
- In the builder canvas every part is a `div` with the same classes, and a table holding a spanning cell is drawn as a CSS grid (`bfbe-table--grid`). Check tags, scopes, spans and stacking on the page.

## Wiring to other elements

Stands alone among other elements: nothing targets it and it targets nothing. Its wiring is its own children.

- The tree is `bfbe-table` > `bfbe-table-row` > `bfbe-table-cell` > any elements, each a direct child. Schemas: `../bfbe-schemas/references/elements/bfbe-table-row.json` and `../bfbe-schemas/references/elements/bfbe-table-cell.json`.
- **Table Row**: **Header row** `isHeader: true` makes every cell in it `<th scope="col">`. **Background** `rowBackground` and **Typography** `rowTypography` paint that row's cells. The row is the part that loops: `hasLoop: true` with `query` (for example `{"post_type": ["post"], "posts_per_page": 10}`) repeats its `<tr>` per item, and the elements in its cells take dynamic tags such as `{post_title}`.
- **Table Cell**: **Row header** `rowHeader: true` gives `<th scope="row">`; **Span columns** `colspan`; **Column width** `colWidth`; **Align** `cellAlign`; **Background**, **Typography** and **Padding** (`cellBackground`, `cellTypography`, `cellPadding`) for that cell alone. It has no loop controls.
- `window.bfbeTable()` reruns the labels and the tab-stop check. It already runs on load and after Bricks' AJAX pagination, page loads, query results and popups; call it after your own script inserts rows.
- To target one table in custom CSS, give it a class in `_cssClasses`, never `_cssId`: component instances share ids, and inside a query loop Bricks moves the id into a class.

## Verified patterns

A comparison table with row headers, from the demo page `demo-bfb-table` (trimmed to three columns and two rows). `rowHeader` on each row's first cell makes it `<th scope="row">`; `stripe` is a colour and `headerBackground` a background object. `cellVerticalAlign:mobile_portrait` shows a breakpoint suffix on a control that writes CSS.

```json
{"name": "bfbe-table", "settings": {
  "stripe": {"hex": "#f7f8fa"}, "headerBackground": {"color": {"hex": "#f0ecff"}},
  "cellPadding": {"top": "14", "right": "14", "bottom": "14", "left": "14"}, "cellVerticalAlign:mobile_portrait": "top"
}, "children": [
  {"name": "bfbe-table-row", "settings": {"isHeader": true}, "children": [
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "Method"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "Water"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "Time"}}]}
  ]},
  {"name": "bfbe-table-row", "settings": {}, "children": [
    {"name": "bfbe-table-cell", "settings": {"rowHeader": true}, "children": [{"name": "text-basic", "settings": {"text": "V60"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "250 g at 94°C"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "2:45"}}]}
  ]},
  {"name": "bfbe-table-row", "settings": {}, "children": [
    {"name": "bfbe-table-cell", "settings": {"rowHeader": true}, "children": [{"name": "text-basic", "settings": {"text": "Aeropress"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "220 g at 88°C"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "1:30"}}]}
  ]}
]}
```

Rows that stack on narrow screens, with a closing line across the table, from the fixture page `fixture-table` (trimmed to three columns). `responsive: "stack"` with `stackBelow: "768"` stacks below a 768px table width; `colspan` must equal the column count.

```json
{"name": "bfbe-table", "settings": {"caption": "Plans compared", "responsive": "stack", "stackBelow": "768", "stripe": {"hex": "#f4f4f5"}}, "children": [
  {"name": "bfbe-table-row", "settings": {"isHeader": true}, "children": [
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "Plan"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "Sites"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "Price"}}]}
  ]},
  {"name": "bfbe-table-row", "settings": {}, "children": [
    {"name": "bfbe-table-cell", "settings": {"rowHeader": true}, "children": [{"name": "text-basic", "settings": {"text": "Starter"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "1"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "Free"}}]}
  ]},
  {"name": "bfbe-table-row", "settings": {}, "children": [
    {"name": "bfbe-table-cell", "settings": {"colspan": 3, "cellAlign": "center"}, "children": [{"name": "text-basic", "settings": {"text": "All plans include updates for the term"}}]}
  ]}
]}
```

A sticky header with set column widths and a caption for screen readers, from `fixture-table` (three columns, caption shortened, the header cells' alignment left out). `stickyHeader` scrolls the table inside the default 420px **Height**; `colWidth` sits on the header cells.

```json
{"name": "bfbe-table", "settings": {"caption": "Plans compared", "captionMode": "hidden", "stickyHeader": true}, "children": [
  {"name": "bfbe-table-row", "settings": {"isHeader": true}, "children": [
    {"name": "bfbe-table-cell", "settings": {"colWidth": "30%"}, "children": [{"name": "text-basic", "settings": {"text": "Plan"}}]},
    {"name": "bfbe-table-cell", "settings": {"colWidth": "120px"}, "children": [{"name": "text-basic", "settings": {"text": "Sites"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "Support"}}]}
  ]},
  {"name": "bfbe-table-row", "settings": {}, "children": [
    {"name": "bfbe-table-cell", "settings": {"rowHeader": true}, "children": [{"name": "text-basic", "settings": {"text": "Starter"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "1"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "Email"}}]}
  ]},
  {"name": "bfbe-table-row", "settings": {}, "children": [
    {"name": "bfbe-table-cell", "settings": {"rowHeader": true}, "children": [{"name": "text-basic", "settings": {"text": "Studio"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "10"}}]},
    {"name": "bfbe-table-cell", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "Priority email"}}]}
  ]}
]}
```

## Gotchas

- **Rows sit directly in the Table, cells directly in a row.** Bricks cannot restrict what a nestable holds, and anything else renders inside `<table>` or `<tr>`, where the browser moves it out above the table. A cell becomes `<th scope="col">` when its direct parent row has `isHeader: true`. <!-- src: plugins/bfb-elements/includes/abstract-element.php:512-517, plugins/bfb-elements/elements/table-cell.php:136-140, docs/API-PROBE.md "5. Nestable elements and real table semantics" -->
- **Loop the row, not the table.** `hasLoop` on the Table repeats the whole table, caption and header included, once per item. Put `hasLoop` and `query` on the body Table Row after the header row, and it renders one `<tr>` per item. <!-- src: plugins/bfb-elements/elements/table.php:483-486, plugins/bfb-elements/elements/table-row.php:91-93 -->
- **Stacking follows the table's own width, set once.** **Stack below** is a container query on the table, so a table in a 600px column stacks under the default 640px even on a wide screen. `responsive` and `stackBelow` are read without breakpoint suffixes, so `responsive:mobile_portrait` does nothing. <!-- src: src/elements/table/table.css:162-165, plugins/bfb-elements/elements/table.php:488-492 -->
- **Stacked labels come from the header row's text.** With no header row, or a heading cell holding only an image or icon, the stacked cells have no label. A cell with `colspan` above 1 never gets one and fills the stacked row's width. <!-- src: src/elements/table/table.js:9-28, src/elements/table/table.css:206 -->
- **Every row needs the header's column count.** Labels go by column position, counting `colspan`, so an extra cell in a row goes unlabelled and a short row ends early. Add a column by adding a cell to the header row and to every row. <!-- src: src/elements/table/table.js:12-25, docs/elements/table.md "A column is a cell in every row" -->
- **Column width follows the column; alignment does not.** `colWidth` on the header cell lays out the whole column, and the canvas reads its grid tracks from the header row. `cellAlign` aligns its own cell, so repeat it on every cell of the column. <!-- src: plugins/bfb-elements/elements/table-cell.php:91-120, src/elements/table/table.js:72-80, docs/elements/table.md "each cell aligns its own text" -->
- **Sticky header sticks inside the table, not to the page.** `stickyHeader` caps the wrapper at **Height** `maxHeight`, 420px by default, and scrolls it; the header row sticks to that box. A table shorter than the height has nothing to stick to. <!-- src: src/elements/table/table.css:66-72, plugins/bfb-elements/elements/table.php:147-151 -->
- **Scroll sideways makes the table as wide as its text on one line.** Cells holding sentences stretch it wide; set **Smallest width** `minWidth` (for example `"900px"`) so they wrap and the table still scrolls. On macOS a floating scroll bar draws over the last row; **Space above it** `barSpace`, or `bar: "styled"` in Chrome and Safari, keeps it off. <!-- src: src/elements/table/table.css:31-40, docs/elements/table.md "Round 402" -->
- **Any space between cells separates their borders.** A value in `columnGap` or `rowGap` switches the table to `border-collapse: separate`, so each cell draws its own border. Stacked, the row space becomes the space between stacked rows. <!-- src: plugins/bfb-elements/elements/table.php:497-500, src/elements/table/table.css:82-85 -->
- **The line between rows is two Rows controls.** **Line thickness** `rowLineWidth` and **Line colour** `rowLineColor` draw the bottom edge of every cell but the last row's, and outrank the bottom of the Cells **Border** `cellBorder`. Stacked rows show no line until `rowLineWidth` is set. <!-- src: plugins/bfb-elements/elements/table.php:406-441, src/elements/table/table.css:185-187 -->
- **Style each part with its own controls.** Bricks' Style-tab border and background on the Table land outside the drawn frame, `.bfbe-table__scroll`, which has its own 1px border and 12px radius; use `tableBorder` and `tableBackground`. On a row a Style-tab background paints the `<tr>`, which the stripe covers on every other row, and on a cell Style-tab values lose to the Table's Cells group; use `rowBackground` and the cell's Look controls. <!-- src: plugins/bfb-elements/elements/table.php:270-274, plugins/bfb-elements/elements/table-row.php:46-50, plugins/bfb-elements/elements/table-cell.php:60-66 -->
- **A background control takes an object, a colour control a colour.** `headerBackground`, `tableBackground`, `rowBackground` and `cellBackground` want `{"color": {"hex": "#f0ecff"}}`, and a bare colour writes nothing. `stripe`, `rowHover`, `rowLineColor` and the bar colours take `{"hex": "#f7f8fa"}`. <!-- src: docs/elements/table.md "round 279" -->

## Never do

- Do not place anything but a `bfbe-table-row` directly in a `bfbe-table`, or anything but a `bfbe-table-cell` directly in a row.
- Do not set `hasLoop` on the `bfbe-table` to list posts; loop a `bfbe-table-row`.
- Do not write `responsive` or `stackBelow` with a breakpoint suffix.
- Do not give a row more or fewer columns than the header row, counting `colspan`.
- Do not leave heading cells without text on a table set to `responsive: "stack"`.
- Do not style the table frame, a row or a cell through Bricks' `_border`, `_background`, `_padding` or `_typography`; use the element's own controls.
- Do not hand a background control a bare colour.
- Do not add or remove `tabindex` or `role` on `.bfbe-table__scroll`; the element and its script manage both.
