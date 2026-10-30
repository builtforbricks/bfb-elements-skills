---
name: bfbe-linked-products
description: "Use when placing, wiring or styling BFB Linked Products (`bfbe-linked-products`). Read before writing its settings."
---

# BFB Linked Products (`bfbe-linked-products`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-linked-products.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/linked-products/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Linked products (`bfbeLinked`)
- `linkedBy` (select) **Linked by**: options: `field` The Linked products field (default), `attribute` A shared attribute
- `attribute` (select) **Attribute**: options: `pa_colour` Colour, `pa_material` Material, `pa_size` Size, `pa_warmth` Warmth. Its swatch colours the links.
- `label` (text) **Label**: placeholder The attribute name; dynamic data accepted
Styling, in the schema file: `labelTypography`, `currentTypography`, `swatchSize`, `gap`, `swatchBorder`, `currentColor`.
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
