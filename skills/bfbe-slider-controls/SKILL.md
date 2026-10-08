---
name: bfbe-slider-controls
description: "Use when placing, wiring or styling BFB Slider Controls (`bfbe-slider-controls`): one control for Bricks' Slider (Nestable) element, placed anywhere on the page: arrows, a fraction like 3 / 7, a progress bar or thumbnails. Read before writing its settings."
---

# BFB Slider Controls (`bfbe-slider-controls`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-slider-controls.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/slider-controls/

## What it is
One control for Bricks' Slider (Nestable) element, placed anywhere on the page: arrows, a fraction like 3 / 7, a progress bar or thumbnails. Each element is exactly one of those, so you lay a row of them out with Bricks' own containers. It binds to a slider by element ID, or to the nearest slider when the ID is empty.

**Not for:** Not a slider of its own: it drives Bricks' Slider (Nestable) element, not the Slider or the Carousel, and hides itself if it cannot find one. It cannot drive an Advanced Snap Slider, which carries its own buttons and dots.

**Costs a page:** CSS 0.71 KB, JS 1.44 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Slider (`bfbeTarget`)
- `target` (text) **Slider element ID**: placeholder The nearest slider. The ID of the Bricks Slider (Nestable) to control: it drives that element, not the Slider or the Carousel. Empty, the default, takes the nearest slider, found by walking out from this element. With no slider found, it hides itself on the page.
- `part` (select) **Control**: options: `arrows` Both arrows (default), `prev` Previous arrow, `next` Next arrow, `fraction` Fraction (3 / 7), `progress` Progress bar, `thumbs` Thumbnails. Choose Both arrows, the default, Previous arrow, Next arrow, Fraction (3 / 7), Progress bar or Thumbnails. Each element is one control, and the groups below follow your choice.

### Arrows (`bfbeArrows`)
The whole group shows only when `part` is not `fraction` or `progress` or `thumbs`.
- `prevLabel` (text) **Previous label**: placeholder Previous slide; dynamic data accepted; only when `part` is not `next` or `fraction` or `progress` or `thumbs`. The name screen readers read for the previous button, Previous slide by default. It takes dynamic data.
- `nextLabel` (text) **Next label**: placeholder Next slide; dynamic data accepted; only when `part` is not `prev` or `fraction` or `progress` or `thumbs`. The same for the next button, Next slide by default. It takes dynamic data too.
- `prevIcon` (icon) **Previous icon**: only when `part` is not `next` or `fraction` or `progress` or `thumbs`. Pick an icon of your own in place of the drawn chevron.
- `nextIcon` (icon) **Next icon**: only when `part` is not `prev` or `fraction` or `progress` or `thumbs`. The same for the next button. An arrow with no icon of its own draws a simple chevron.
Styling, in the schema file: `gap`, `arrowSize`, `arrowColor`, `arrowBackground`, `arrowBackgroundHover`, `arrowColorHover`, `arrowBorder`.

### Progress bar (`bfbeBar`)
The whole group shows only when `part` is `progress`.
Styling only, every key in the schema file: `barHeight`, `barColor`, `barTrack`, `barBorder`.

### Fraction (`bfbeFraction`)
The whole group shows only when `part` is `fraction`.
Styling only, every key in the schema file: `fractionTypography`.

### Thumbnails (`bfbeThumbs`)
The whole group shows only when `part` is `thumbs`.
Styling only, every key in the schema file: `thumbsAlign`, `thumbSize`, `thumbBorder`, `thumbGap`, `thumbDim`, `thumbActive`.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. The curve those changes follow, Snappy unless set.
Styling, in the schema file: `duration`, `easingCustom`.

## What it guarantees for accessibility (do not undo)
- Every arrow and thumbnail is a real button that names the slider it controls through aria-controls, and the arrow names are editable.
- At the start and end of a slider that neither loops nor rewinds, the matching arrow gets aria-disabled and ignores clicks.
- The progress bar is a progressbar with aria-valuenow and a Slide progress label, and the fraction is hidden from assistive technology.
- Each thumbnail is named Go to slide with its number, and the current one carries aria-current.
- The bar's fill and the thumbnails' fades run on the shared motion duration, which reduced motion sets to zero.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
