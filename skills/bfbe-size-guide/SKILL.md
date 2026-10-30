---
name: bfbe-size-guide
description: "Use when placing, wiring or styling BFB Size Guide (`bfbe-size-guide`). Read before writing its settings."
---

# BFB Size Guide (`bfbe-size-guide`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-size-guide.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/size-guide/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.82 KB, JS 1.42 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Guide (`bfbeGuide`)
- `shows` (select) **Shows**: options: `button` A button that opens the guide (default), `page` The guide on the page
- `guide` (select) **Guide**: options: `auto` The guide that applies to this product (default), `g0` Shirts
- `title` (text) **Dialog title**: placeholder The guide name; dynamic data accepted; only when `shows` is not `page`
- `units` (select) **Units shown first**: options: `guide` As the guide is typed (default), `cm` Centimetres, `in` Inches
- `unitsLabel` (text) **Units label**: placeholder Units; dynamic data accepted

### Button (`bfbeButton`)
The whole group shows only when `shows` is not `page`.
- `text` (text) **Text**: placeholder Size guide; dynamic data accepted
- `style` (select) **Style**: options: `primary` Primary, `secondary` Secondary, `light` Light, `dark` Dark, `muted` Muted, `info` Info, `success` Success, `warning` Warning, `danger` Danger
- `size` (select) **Size**: options: `sm` Small, `md` Medium (default), `lg` Large, `xl` Extra large
- `outline` (checkbox) **Outline**
Styling, in the schema file: `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonPadding`, `buttonHoverBackground`, `buttonHoverColor`.

### Size finder (`bfbeFinder`)
- `finder` (select) **Size finder**: options: `show` Shown (default), `hide` Hidden
- `finderTitle` (text) **Title**: placeholder Find my size; only when `finder` is not `hide`
- `finderButton` (text) **Button**: placeholder Find my size; only when `finder` is not `hide`
- `finderResult` (text) **Answer**: placeholder Your size is {size}; only when `finder` is not `hide`
- `finderNone` (text) **No fit**: placeholder No size in this guide fits those measurements.; only when `finder` is not `hide`
Styling, in the schema file: `finderSpacing`, `finderTitleTypography`, `fieldLabelTypography`, `fieldsGap`, `inputTypography`, `inputBackground`, `inputBorder`, `inputPadding`, `inputFocusBorder`, `findTypography`, `findBackground`, `findBorder`, `findPadding`, `findHoverBackground`, `findHoverColor`, `resultTypography`.

### Dialog (`bfbeDialog`)
The whole group shows only when `shows` is not `page`.
Styling only, every key in the schema file: `dialogWidth`, `dialogBackground`, `dialogColor`, `dialogPadding`, `dialogBorder`, `dialogShadow`, `backdrop`, `titleTypography`, `headSpacing`, `closeSize`, `closeIconSize`, `closeColor`, `closeBackground`, `closeBorder`, `closeHoverBackground`, `closeHoverColor`.

### Table (`bfbeTable`)
Styling only, every key in the schema file: `headTypography`, `cellTypography`, `headBackground`, `cellPadding`, `lineColor`, `rowStripe`, `rowHoverBackground`, `unitsTypography`, `unitBackground`, `unitBorder`, `unitPadding`, `unitChosenBackground`, `unitChosenColor`, `unitChosenBorder`, `unitsSpacing`.

### Size finder: arrows (`bfbeFinderArrows`)
The whole group shows only when `finder` is not `hide`.
- `finderSpinArrows` (select) **Arrows**: options: `browser` The browser's, `inside` Ours, inside the box, `stepper` A − and a + beside it, `none` None; only when `finder` is not `hide`
Styling, in the schema file: `finderSpinArrowSize`, `finderSpinArrowWidth`, `finderSpinArrowGap`, `finderSpinArrowColor`, `finderSpinArrowBg`, `finderSpinArrowHover`, `finderSpinArrowHoverBg`, `finderSpinArrowLine`, `finderSpinArrowBorder`.

### In the builder (`bfbeBuilder`)
The whole group shows only when `shows` is not `page`.
- `builderView` (select) **Show it**: options: `open` Open, so you can style it (default), `closed` Closed, as the site leaves it. Closed shows the button alone, as the site does.
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
