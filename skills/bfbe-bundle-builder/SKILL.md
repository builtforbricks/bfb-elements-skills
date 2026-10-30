---
name: bfbe-bundle-builder
description: "Use when placing, wiring or styling BFB Bundle Builder (`bfbe-bundle-builder`). Read before writing its settings."
---

# BFB Bundle Builder (`bfbe-bundle-builder`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-bundle-builder.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/bundle-builder/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.87 KB, JS 1.37 KB (gzipped), plus shop-live, loaded only on pages that use it.

## Structure
Nestable. Its own children: `bfbe-bundle-title`, `bfbe-bundle-progress`, `bfbe-bundle-products`.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-bundle-builder",
    "settings": {},
    "children": [
        {
            "name": "bfbe-bundle-title",
            "settings": {}
        },
        {
            "name": "bfbe-bundle-progress",
            "settings": {}
        },
        {
            "name": "bfbe-bundle-products",
            "settings": {}
        },
        {
            "name": "button",
            "settings": {
                "text": "Add the bundle",
                "tag": "button",
                "style": "primary",
                "_cssClasses": "bfbe-bundle__add",
                "_attributes": [
                    {
                        "id": "bfbebb",
                        "name": "type",
                        "value": "submit"
                    }
                ]
            }
        }
    ]
}
```

`bfbe-bundle-title` (BFB Bundle Title), 43 controls, schema `../bfbe-schemas/references/elements/bfbe-bundle-title.json`.

`bfbe-bundle-progress` (BFB Bundle Progress), 51 controls, schema `../bfbe-schemas/references/elements/bfbe-bundle-progress.json`.

`bfbe-bundle-products` (BFB Bundle Products), 71 controls, schema `../bfbe-schemas/references/elements/bfbe-bundle-products.json`.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Bundle (`bfbeBundle`)
- `source` (select) **Products from**: options: `category` A category (default), `tag` A tag, `ids` Products chosen here
- `category` (text) **Category slug**: placeholder kitchen; only when `source` is not `tag` or `ids`
- `tag` (text) **Tag slug**: placeholder gift; only when `source` is `tag`
- `products` (select) **Products**: placeholder Pick the products; only when `source` is `ids`
- `most` (number) **Products shown**: placeholder 12
- `count` (number) **Products to choose**: placeholder 3
- `kind` (select) **Bundle price**: options: `price` A set price (default), `percent` A percentage off each
- `price` (number) **Set price**: placeholder 30; only when `kind` is not `percent`
- `percent` (number) **Percentage off**: placeholder 20; only when `kind` is `percent`

### Button (`bfbeButton`)
Styling only, every key in the schema file: `disabledOpacity`.
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
