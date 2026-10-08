---
name: bfbe-table
description: "Use when placing, wiring or styling BFB Table (`bfbe-table`): a real HTML table, built from Table Row and Table Cell elements, where each cell can hold any Bricks element. Read before writing its settings."
---

# BFB Table (`bfbe-table`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
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

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
