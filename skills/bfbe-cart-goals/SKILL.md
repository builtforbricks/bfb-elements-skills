---
name: bfbe-cart-goals
description: "Use when placing, wiring or styling BFB Cart Goals (`bfbe-cart-goals`). Read before writing its settings."
---

# BFB Cart Goals (`bfbe-cart-goals`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-cart-goals.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/cart-goals/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 0.99 KB, JS 1.77 KB (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Goals (`bfbeGoals`)
- `shows` (select) **Shows**: options: `all` Sentence, track and gift choice (default), `sentence` Sentence only, `track` Track only, `gifts` Gift choice only. Place a second one to put a part elsewhere.
- `nextOnly` (checkbox) **Next goal only**
- `steps` (select) **Steps**: options: `show` Show (default), `hide` Hide
- `toGo` (text) **Before a goal**: placeholder {amount} to go for {label}
- `reachedText` (text) **Goal reached**: placeholder Reached: {label}
- `allText` (text) **All reached**: placeholder You have every reward.

### Gift choice (`bfbeGift`)
The whole group shows only when `shows` is not `sentence` or `track`.
- `gifts` (text) **Gift choices**: placeholder Ids or SKUs, comma-separated
- `giftWord` (text) **Chooser heading**: placeholder Choose your free gift; only when `gifts` is set
- `chooseWord` (text) **Button**: placeholder Choose; only when `gifts` is set
- `choicesAs` (select) **Choices as**: options: `radios` Radios (default), `pills` Pills; only when `gifts` is set
- `radioLook` (select) **Radios**: options: `native` As the browser draws it (default), `custom` Styled with the controls below; only when `gifts` is set and `choicesAs` is not `pills`
Styling, in the schema file: `legendTypography`, `choiceTypography`, `legendSpace`, `choiceGap`, `radioGap`, `boxBackground`, `boxBorder`, `boxPadding`, `radioColor`, `radioTickSize`, `radioTickBg`, `radioTickBorder`, `radioTickHover`, `radioTickOnLine`, `radioTickMarkColor`, `pillBackground`, `pillColor`, `pillBorder`, `pillPadding`, `pillHoverBackground`, `pillHoverBorder`, `pillOnBackground`, `pillOnColor`, `pillOnBorder`.

### Track (`bfbeTrack`)
The whole group shows only when `shows` is not `gifts`.
- `labelDisplay` (select) **Goal names**: options: `block` Show (default), `none` Hide; writes CSS; only when `steps` is not `hide`
Styling, in the schema file: `gap`, `textTypography`, `trackHeight`, `trackColor`, `fillColor`, `trackBorder`, `stepTypography`, `thresholdTypography`, `reachedTypography`, `markColor`, `markBorder`.
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
