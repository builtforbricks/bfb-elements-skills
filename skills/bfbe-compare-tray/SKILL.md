---
name: bfbe-compare-tray
description: "Use when placing, wiring or styling BFB Compare Tray (`bfbe-compare-tray`). Read before writing its settings."
---

# BFB Compare Tray (`bfbe-compare-tray`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-compare-tray.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/compare-tray/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

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
- `trayName` (text) **Tray name**: placeholder Compare. Read out as the name of the tray.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` In the flow, so you can style it (default), `live` Working, as on the site. Working means it shows and hides as outside.
<!-- bfbe:generated:end -->

## Rendered DOM

_Not written yet._

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
