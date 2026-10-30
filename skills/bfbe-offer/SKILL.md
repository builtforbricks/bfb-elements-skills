---
name: bfbe-offer
description: "Use when placing, wiring or styling BFB Offer (`bfbe-offer`). Read before writing its settings."
---

# BFB Offer (`bfbe-offer`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-offer.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/offer/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.44 KB, JS 1.08 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Nestable. Its own children: `bfbe-offer-checkbox`.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-offer",
    "settings": {},
    "children": [
        {
            "name": "image",
            "settings": {
                "image": {
                    "useDynamicData": "{bfbe_offer_image}",
                    "size": "woocommerce_thumbnail"
                },
                "_width": "96px"
            }
        },
        {
            "name": "block",
            "settings": {
                "_rowGap": "8px",
                "_flexGrow": "1"
            },
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "One-time offer",
                        "tag": "h4"
                    }
                },
                {
                    "name": "bfbe-offer-checkbox",
                    "settings": {}
                }
            ]
        }
    ]
}
```

`bfbe-offer-checkbox` (BFB Offer Checkbox), 57 controls, schema `../bfbe-schemas/references/elements/bfbe-offer-checkbox.json`.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Offer (`bfbeOffer`)
- `product` (select) **Product**: placeholder Pick a product
- `priceMode` (select) **Price**: options: `price` A price (default), `percent` Percent off
- `price` (number) **Offer price**: placeholder 9.90; only when `priceMode` is not `percent`
- `percent` (number) **Percent off**: placeholder 15; only when `priceMode` is `percent`. Off the current price, 1 to 99.
- `updateWord` (text) **Button**: placeholder Update

### Show when (`bfbeWhen`)
- `minTotal` (number) **Cart total at least**: placeholder 0
- `withProduct` (text) **A product in the cart**: placeholder Id or SKU
- `withCategory` (text) **A category in the cart**: placeholder Category slug

### Card (`bfbeCard`)
Styling only, every key in the schema file: `chosenBorder`, `chosenBackground`, `chosenShadow`.
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
