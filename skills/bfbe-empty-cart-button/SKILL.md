---
name: bfbe-empty-cart-button
description: "Use when placing, wiring or styling BFB Empty Cart Button (`bfbe-empty-cart-button`). Read before writing its settings."
---

# BFB Empty Cart Button (`bfbe-empty-cart-button`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-empty-cart-button.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/empty-cart-button/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.59 KB, JS 0.74 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Button (`bfbeButton`)
- `text` (text) **Text**: placeholder Empty the cart; dynamic data accepted
- `style` (select) **Style**: options: `primary` Primary, `secondary` Secondary, `light` Light, `dark` Dark, `muted` Muted, `info` Info, `success` Success, `warning` Warning, `danger` Danger
- `size` (select) **Size**: options: `sm` Small, `md` Medium (default), `lg` Large, `xl` Extra large
- `outline` (checkbox) **Outline**
- `icon` (icon) **Icon**. Before the text. None unless set.
- `hideEmpty` (checkbox) **Hide when empty**
Styling, in the schema file: `iconSize`, `iconGap`.

### Confirm (`bfbeConfirm`)
- `question` (text) **Question**: placeholder Empty your cart?; dynamic data accepted
- `confirmText` (text) **Yes button**: placeholder Yes, empty it
- `cancelText` (text) **Cancel button**: placeholder Keep my cart

### Question box (`bfbeDialog`)
- `builderPreview` (checkbox) **Preview in the builder**
Styling, in the schema file: `boxTypography`, `boxBackground`, `boxBorder`, `boxPadding`, `boxWidth`, `boxShadow`, `backdrop`, `questionTypography`, `btnTypography`, `btnPadding`, `btnBorder`, `btnGap`, `btnJustify`, `okBackground`, `okColor`, `okHoverBackground`, `okHoverColor`, `okHoverBorder`, `cancelBackground`, `cancelColor`, `cancelHoverBackground`, `cancelHoverColor`, `cancelHoverBorder`.
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
