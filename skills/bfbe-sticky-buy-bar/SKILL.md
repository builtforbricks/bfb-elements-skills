---
name: bfbe-sticky-buy-bar
description: "Use when placing, wiring or styling BFB Sticky Buy Bar (`bfbe-sticky-buy-bar`). Read before writing its settings."
---

# BFB Sticky Buy Bar (`bfbe-sticky-buy-bar`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-sticky-buy-bar.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/sticky-buy-bar/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.60 KB, JS 2.34 KB (gzipped), plus shop-live, loaded only on pages that use it.

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-sticky-buy-bar",
    "settings": {},
    "children": [
        {
            "name": "image",
            "settings": {
                "image": {
                    "useDynamicData": "{featured_image}",
                    "size": "thumbnail"
                },
                "_width": "56px"
            }
        },
        {
            "name": "product-title",
            "settings": {
                "tag": "p"
            }
        },
        {
            "name": "text-basic",
            "settings": {
                "text": "{bfbe_variation_price}"
            }
        },
        {
            "name": "button",
            "settings": {
                "text": "Add to cart",
                "tag": "button",
                "style": "primary",
                "_cssClasses": "bfbe-buybar-go"
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Bar (`bfbeBar`)
- `edge` (select) **Edge**: options: `bottom` Bottom (default), `top` Top
- `buttonClass` (text) **Buy button class**: placeholder bfbe-buybar-go. The child that presses the real add to cart button.
- `missingText` (text) **Missing choice words**: placeholder Choose a %s first; dynamic data accepted. %s is the attribute.
- `clear` (text) **Keep clear of**: placeholder #bfbcc. A fixed element at the same edge, by selector.
- `wrap` (select) **Wrap**: options: `nowrap` No wrap (default), `wrap` Wrap, `wrap-reverse` Wrap reverse; writes CSS
Styling, in the schema file: `width`, `direction`, `align`, `alignItems`, `gap`, `padding`, `pictureMax`, `choiceTypography`.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS
Styling, in the schema file: `duration`, `easingCustom`.

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
