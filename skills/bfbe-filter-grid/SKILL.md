---
name: bfbe-filter-grid
description: "Use when placing, wiring or styling BFB Filter Grid (`bfbe-filter-grid`): items behind filter chips, each Filter Item carrying its tags, typed in or taken from a query loop's dynamic tags. Read before writing its settings."
---

# BFB Filter Grid (`bfbe-filter-grid`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-filter-grid.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/filter-grid/

## What it is
Items behind filter chips, each Filter Item carrying its tags, typed in or taken from a query loop's dynamic tags. The chips are built from the tags actually present, and items hide and reveal in the page with an animated reflow where the browser allows. A filter can live in the URL, and several tags can be chosen at once.

**Not for:** It filters the items already in the page, so every item's markup is delivered up front. A large archive that needs paging or a server search fits a paginated query loop better, because this grid cannot fetch more items.

**Costs a page:** CSS 0.79 KB, JS 1.43 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable. Its own children: `bfbe-filter-item`.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-filter-grid",
    "settings": {},
    "children": [
        {
            "name": "bfbe-filter-item",
            "settings": {
                "tags": "Design"
            },
            "children": [
                {
                    "name": "block",
                    "settings": {
                        "_background": {
                            "color": {
                                "hex": "#e2e8f0"
                            }
                        },
                        "_padding": {
                            "top": "32",
                            "right": "24",
                            "bottom": "32",
                            "left": "24"
                        }
                    },
                    "children": [
                        {
                            "name": "heading",
                            "settings": {
                                "text": "Brand site",
                                "tag": "h3"
                            }
                        }
                    ]
                }
            ]
        },
        {
            "name": "bfbe-filter-item",
            "settings": {
                "tags": "Development"
            },
            "children": [
                {
                    "name": "block",
                    "settings": {
                        "_background": {
                            "color": {
                                "hex": "#e2e8f0"
                            }
                        },
                        "_padding": {
                            "top": "32",
                            "right": "24",
                            "bottom": "32",
                            "left": "24"
                        }
                    },
                    "children": [
                        {
                            "name": "heading",
                            "settings": {
                                "text": "Shop build",
                                "tag": "h3"
                            }
                        }
                    ]
                }
            ]
        },
        {
            "name": "bfbe-filter-item",
            "settings": {
                "tags": "Video"
            },
            "children": [
                {
                    "name": "block",
                    "settings": {
                        "_background": {
                            "color": {
                                "hex": "#e2e8f0"
                            }
                        },
                        "_padding": {
                            "top": "32",
                            "right": "24",
                            "bottom": "32",
                            "left": "24"
                        }
                    },
                    "children": [
                        {
                            "name": "heading",
                            "settings": {
                                "text": "Launch film",
                                "tag": "h3"
                            }
                        }
                    ]
                }
            ]
        },
        {
            "name": "bfbe-filter-item",
            "settings": {
                "tags": "Design, Print"
            },
            "children": [
                {
                    "name": "block",
                    "settings": {
                        "_background": {
                            "color": {
                                "hex": "#e2e8f0"
                            }
                        },
                        "_padding": {
                            "top": "32",
                            "right": "24",
                            "bottom": "32",
                            "left": "24"
                        }
                    },
                    "children": [
                        {
                            "name": "heading",
                            "settings": {
                                "text": "Identity",
                                "tag": "h3"
                            }
                        }
                    ]
                }
            ]
        }
    ]
}
```

`bfbe-filter-item` (BFB Filter Item), 35 controls, schema `../bfbe-schemas/references/elements/bfbe-filter-item.json`, nestable itself.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Filters (`bfbeFilters`)
- `allLabel` (text) **Show-everything chip**: placeholder All; dynamic data accepted. The words on the chip that shows every item, All by default. It takes dynamic data.
- `multi` (checkbox) **Several at once**. Off by default, so one tag shows at a time. Tick it to let visitors combine chips, and items matching any chosen tag show.
- `counts` (checkbox) **Show counts**. Tick it to show on each chip the number of items that have its tag. The show-everything chip counts every item.
- `hash` (checkbox) **Filter in the URL**. Tick it to write the choice into the address as #filter=Tag. The hash belongs to the whole page, so it suits one grid per page.
- `emptyText` (text) **Nothing found text**: placeholder Nothing matches.; dynamic data accepted. Type what shows when no item matches. It reads Nothing matches unless you change it, and it takes dynamic data.
Styling, in the schema file: `emptyTypography`.

### Grid (`bfbeGrid`)
Styling only, every key in the schema file: `columns`, `columnsNarrow`, `columnsPhone`, `gap`, `barGap`.

### Chips (`bfbeChips`)
Styling only, every key in the schema file: `barAlign`, `chipGap`, `chipTypography`, `chipBackground`, `chipBackgroundHover`, `chipBorder`, `chipPadding`, `chipOnBackground`, `chipOnColor`, `chipSelectedBorder`, `countBackground`, `countTypography`, `countPadding`, `countBorder`.

### Motion (`bfbeMotion`)
- `itemEffect` (select) **Item effect**: options: `fade` Fade, `rise` Rise (default), `scale` Scale, `none` None. Rise is the default. Fade, Scale or None change how items arrive after a filter.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Snappy by default. Pick another curve from the list, or Custom to type your own in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`, `stagger`.

## What it guarantees for accessibility (do not undo)
- Chips are native buttons with aria-pressed and an aria-controls naming the items container, so Tab, Enter and Space work and no arrow keys are bound.
- A visually hidden polite live region announces how many items are shown after each choice, or the Nothing found text when none is.
- Items that do not match carry the hidden attribute, so they leave the reading order as well as the screen.
- Under reduced motion the view transition is skipped and the new set appears at once, with no arrival animation or delay.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
