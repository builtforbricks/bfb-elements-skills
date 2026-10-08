---
name: bfbe-scroll-indicator
description: "Use when placing, wiring or styling BFB Scroll Indicator (`bfbe-scroll-indicator`): shows how far a visitor has scrolled, as a bar or a ring, fixed to the top or bottom or placed in the flow. Read before writing its settings."
---

# BFB Scroll Indicator (`bfbe-scroll-indicator`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-scroll-indicator.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/scroll-indicator/

## What it is
Shows how far a visitor has scrolled, as a bar or a ring, fixed to the top or bottom or placed in the flow. A bar can also mark sections: each dot is a link to its section, named after the section's heading, and the current one is flagged. The progress value is exposed as a progressbar role that updates with the scroll.

**Not for:** It reports progress of the page's own scroll, so a scrolling panel inside the page does not drive it. A reading bar for one article therefore counts the header, footer and everything else on the page too.

**Costs a page:** CSS 1.60 KB, JS 1.73 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Indicator (`bfbeShape`)
- `shape` (select) **Shape**: options: `bar` Bar (default), `ring` Ring. Bar is the default. Ring draws a circular indicator with an optional percentage or a scroll-to-top icon in the middle.
- `position` (select) **Position**: options: `top` Fixed to the top (default), `bottom` Fixed to the bottom, `inline` Where it is placed. Fixed to the top is the default. Choose Fixed to the bottom, or Where it is placed to sit in the page flow.
- `percent` (checkbox) **Show the percentage**: only when `shape` is `ring` and `centerIcon` is not set. For the Ring, tick it to print how far the page has scrolled in the middle of the ring.
- `centerIcon` (checkbox) **Show an icon instead**: only when `shape` is `ring`. For the Ring, tick it to swap the percentage for a button with a caret that scrolls the page to the top.
- `appearAfter` (number) **Show after scrolling (px)**: only when `shape` is `ring` and `position` is not `inline`. For a fixed Ring, how far the page scrolls before the ring appears, 0 by default.
- `offBelow` (select) **Hide below**: options: `never` Never (default), `480` 480px, `640` 640px, `768` 768px, `992` 992px. Never by default. Choose 480, 640, 768 or 992px to drop the indicator on narrow screens.

### Sections (`bfbeSections`)
The whole group shows only when `shape` is not `ring`.
- `sections` (checkbox) **Mark the sections**: only when `shape` is not `ring`. For the Bar, adds a dot for each section found by Which elements. Each dot links to its section.
- `sectionSelector` (text) **Which elements**: placeholder main > .brxe-section; only when `shape` is not `ring` and `sections` is set. A CSS selector for the sections, main > .brxe-section by default. Sections without an id are given one.
- `labels` (checkbox) **Show labels**: only when `shape` is not `ring` and `sections` is set. Shows each dot's name as text. It comes from the section's heading, or from a data-bfbe-label attribute, which takes priority.
- `labelPlace` (select) **Labels**: options: `auto` Below, or above a bottom bar (default), `below` Below, `above` Above, `hover` On hover, over each dot; only when `shape` is not `ring` and `sections` is set and `labels` is set. Below, or above a bottom bar, is the default. The other choices are Below, Above and On hover, over each dot.
Styling, in the schema file: `labelPadding`, `labelShadow`.

### Dots (`bfbeDots`)
The whole group shows only when `shape` is not `ring` and `sections` is set.
Styling only, every key in the schema file: `markerSize`, `markerColor`, `markerCurrent`, `markerDone`, `markerHover`, `markerGrow`, `markerBorder`, `markerShadow`.

### Look (`bfbeLook`)
- `ringTrack` (select) **Line**: options: `solid` Solid (default), `dashed` Dashed, `dotted` Dotted; only when `shape` is `ring`
- `ringCaps` (select) **Fill ends**: options: `round` Round (default), `butt` Flat; writes CSS; only when `shape` is `ring`
- `align` (justify-content) **Alignment**: only when `shape` is not `ring` and `width` is set
- `icon` (icon) **Icon**: only when `shape` is `ring` and `centerIcon` is set. With Show an icon instead, pick your own icon in place of the caret.
Styling, in the schema file: `offset`, `percentBackground`, `percentPadding`, `percentBorder`, `percentTypography`, `thickness`, `color`, `track`, `ringSize`, `barBorder`, `fillBorder`, `width`, `iconSize`, `iconColor`, `labelBackground`, `labelBorder`, `labelGap`, `labelTypography`.

### Motion (`bfbeMotion`)
Styling only, every key in the schema file: `smoothing`.

## What it guarantees for accessibility (do not undo)
- The bar or ring has role progressbar with the name Page progress, and aria-valuenow updates from 0 to 100 as the page scrolls.
- Section dots are links in an ordered list named Sections, each named by its heading, and the current one carries aria-current location.
- The ring's icon is a real button named Scroll to top, and the percentage text is hidden from assistive technology.
- With reduced motion requested, Scroll to top jumps straight up and Smoothing is set to zero.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
