---
name: bfbe-cart-quantity
description: "Use when placing, wiring or styling BFB Cart Quantity (`bfbe-cart-quantity`). Read before writing its settings."
---

# BFB Cart Quantity (`bfbe-cart-quantity`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-cart-quantity.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/cart-quantity/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.75 KB, JS 2.33 KB (gzipped), plus shop-live, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Quantity (`bfbeCartQty`)
- `shows` (select) **Shows**: options: `both` Quantity and Remove (default), `qty` Quantity only, `remove` Remove only
- `removeWord` (text) **Remove word**: placeholder Remove; only when `shows` is not `qty`
- `removeIcon` (icon) **Remove icon**: only when `shows` is not `qty`. None unless set.
- `removeWordHidden` (checkbox) **Icon only**: only when `shows` is not `qty` and `removeIcon` is set. Hides the word when an icon is set.
- `minusIcon` (icon) **Minus icon**: only when `shows` is not `remove`. A plain minus unless set.
- `plusIcon` (icon) **Plus icon**: only when `shows` is not `remove`. A plain plus unless set.

### Look (`bfbeCartQtyLook`)
Styling only, every key in the schema file: `size`, `inputWidth`, `stepperBorder`, `stepperBackground`, `dividerColor`, `numberTypography`, `buttonIconSize`, `buttonColor`, `buttonBackground`, `buttonHoverColor`, `buttonHoverBackground`, `removeTypography`, `removeIconSize`, `removeColor`, `removeBackground`, `removeBorder`, `removePadding`, `removeHoverColor`, `removeHoverBackground`, `gap`.
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
