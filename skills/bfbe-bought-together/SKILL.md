---
name: bfbe-bought-together
description: "Use when placing, wiring or styling BFB Bought Together (`bfbe-bought-together`). Read before writing its settings."
---

# BFB Bought Together (`bfbe-bought-together`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-bought-together.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/bought-together/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 1.37 KB, JS 1.13 KB (gzipped), plus shop-live, loaded only on pages that use it.

## Structure
Nestable. Its own children: `bfbe-bought-together-products`, `bfbe-bought-together-total`.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-bought-together",
    "settings": {},
    "children": [
        {
            "name": "bfbe-bought-together-products",
            "settings": {}
        },
        {
            "name": "bfbe-bought-together-total",
            "settings": {}
        },
        {
            "name": "button",
            "settings": {
                "text": "Add the ticked products",
                "tag": "button",
                "style": "primary",
                "_cssClasses": "bfbe-bt__add",
                "_attributes": [
                    {
                        "id": "bfbebt",
                        "name": "type",
                        "value": "submit"
                    }
                ]
            }
        }
    ]
}
```

`bfbe-bought-together-products` (BFB Bought Together Products), 93 controls, schema `../bfbe-schemas/references/elements/bfbe-bought-together-products.json`.

`bfbe-bought-together-total` (BFB Bought Together Total), 49 controls, schema `../bfbe-schemas/references/elements/bfbe-bought-together-total.json`.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Set (`bfbeSet`)
- `product` (select) **Product**: placeholder The product of the page
- `source` (select) **Companions from**: options: `pick` Picked here (default), `upsells` Its upsells, `cross` Its cross-sells, `orders` Bought with it in your orders
- `products` (select) **Companions**: placeholder Pick up to three products; only when `source` is not `upsells` or `cross` or `orders`
- `most` (number) **Products in the set**: placeholder 3. This product included.
- `variable` (select) **Other variable products**: options: `choose` With a select of their options (default), `leave` Left out
- `unticked` (checkbox) **Start the others unticked**
- `discount` (number) **Set discount (%)**: placeholder 0. While the whole set is in the cart.
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
