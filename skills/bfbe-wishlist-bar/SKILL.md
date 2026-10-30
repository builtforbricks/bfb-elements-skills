---
name: bfbe-wishlist-bar
description: "Use when placing, wiring or styling BFB Wishlist Bar (`bfbe-wishlist-bar`). Read before writing its settings."
---

# BFB Wishlist Bar (`bfbe-wishlist-bar`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-wishlist-bar.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/wishlist-bar/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-wishlist-bar",
    "settings": {},
    "children": [
        {
            "name": "block",
            "settings": {
                "_direction": "row",
                "_flexWrap": "wrap",
                "_alignItems": "baseline",
                "_columnGap": "16px",
                "_rowGap": "8px"
            },
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "{bfbe_wishlist_name}",
                        "tag": "h2"
                    }
                },
                {
                    "name": "text-basic",
                    "settings": {
                        "text": "{bfbe_wishlist_saved} saved"
                    }
                },
                {
                    "name": "text-basic",
                    "settings": {
                        "text": "{bfbe_wishlist_registry}",
                        "tag": "span",
                        "_padding": {
                            "top": "4",
                            "right": "10",
                            "bottom": "4",
                            "left": "10"
                        },
                        "_border": {
                            "radius": {
                                "top": "999",
                                "right": "999",
                                "bottom": "999",
                                "left": "999"
                            }
                        },
                        "_background": {
                            "color": {
                                "raw": "var(--bfbe-surface-hover, #f4f4f5)"
                            }
                        },
                        "_typography": {
                            "font-size": "0.8em",
                            "font-weight": "600"
                        },
                        "_conditions": [
                            [
                                {
                                    "id": "bfbewr",
                                    "key": "dynamic_data",
                                    "dynamic_data": "{bfbe_wishlist_registry}",
                                    "compare": "empty_not"
                                }
                            ]
                        ]
                    }
                }
            ]
        },
        {
            "name": "block",
            "settings": {
                "_direction": "row",
                "_flexWrap": "wrap",
                "_alignItems": "flex-end",
                "_columnGap": "16px",
                "_rowGap": "8px"
            },
            "children": [
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "pick"
                    }
                },
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "new"
                    }
                },
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "rename"
                    }
                },
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "delete"
                    }
                }
            ]
        },
        {
            "name": "block",
            "settings": {
                "_direction": "row",
                "_flexWrap": "wrap",
                "_alignItems": "flex-end",
                "_columnGap": "16px",
                "_rowGap": "8px"
            },
            "children": [
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "share"
                    }
                },
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "registry"
                    }
                },
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "surprise"
                    }
                }
            ]
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Lists bar (`bfbeBar`)
- `barGuest` (text) **Words for guests**: placeholder Sign in to keep several lists and share them.; dynamic data accepted
- `barShared` (text) **Words on a shared list**: placeholder A list shared with you.; dynamic data accepted
Styling, in the schema file: `barNoteTypography`, `barLinkColor`.

### Notice (`bfbeNotice`)
Styling only, every key in the schema file: `noticeTypography`, `noticeBackground`, `noticeBorder`, `noticePadding`.
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
