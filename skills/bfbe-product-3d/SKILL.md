---
name: bfbe-product-3d
description: "Use when placing, wiring or styling BFB 3D View (`bfbe-product-3d`). Read before writing its settings."
---

# BFB 3D View (`bfbe-product-3d`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-product-3d.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/product-3d/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 1.05 KB, JS 2.37 KB (gzipped), plus model-viewer 4.4.0 (Apache-2.0, the 3D model, on a press), loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### View (`bfbeView`)
- `product` (select) **Product**: placeholder The product of the page
- `image` (image) **Still image**. The product image unless chosen.
- `frames` (select) **Frames from**: options: `product` The product field (default), `here` Images chosen here
- `framesHere` (image-gallery) **Frames**: only when `frames` is `here`
- `load` (select) **Load the frames**: options: `turn` On the first turn (default), `view` Once it comes into view
- `auto` (checkbox) **Turn once in view**. Never under reduced motion.
- `time` (number) **One turn takes (s)**: placeholder 4
- `model` (select) **3D model**: options: `press` On a press (default), `view` Once in view, `off` Off. From the product's GLB file.

### Words (`bfbeWords`)
- `spoken` (text) **Spoken name**: placeholder {product}, 360 degree view
- `spinText` (text) **Spin button**: placeholder Spin
- `modelText` (text) **3D button**: placeholder View in 3D
- `arText` (text) **AR link**: placeholder View in your room

### Look (`bfbeLook`)
- `fit` (select) **Fit**: options: `contain` Contain (default), `cover` Cover; writes CSS
Styling, in the schema file: `ratio`, `stageBackground`, `stageBorder`, `stageShadow`, `stagePadding`, `barAlign`, `barGap`, `buttonGap`, `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonShadow`, `buttonPadding`, `buttonHoverBackground`, `buttonHoverColor`, `spinPressedBackground`, `spinPressedColor`, `spinPressedBorder`.
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
