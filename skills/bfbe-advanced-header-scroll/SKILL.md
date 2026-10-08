---
name: bfbe-advanced-header-scroll
description: "Use when placing, wiring or styling BFB Advanced Header Scroll (`advanced-header-scroll`): a feature for the header template, not an element of its own. Read before writing its settings."
---

# BFB Advanced Header Scroll (`advanced-header-scroll`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/advanced-header-scroll.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/advanced-header-scroll/

## What it is
A feature for the header template, not an element of its own. Its Advanced Header Scroll group in the header template's settings, which a page or a content template can override with the page winning, makes the header sticky, or sticky over the first section, and sets when the scrolled state begins, when it hides on the way down and how it moves. Every element inside the header gets a When the page scrolls group on its Style tab, to hide, fade or appear and to restyle itself once the page has scrolled. Nothing in either group acts until Position is Sticky or Sticky, over the first section.

**Not for:** Not for a header placed at the side of the page, which it leaves to Bricks, nor for footers, popups or anything outside the header, which have no scroll states here.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Where it lives
A feature, not an element: its controls are added to the header template's settings, and every element in the header.

## Settings that decide the build

### When the page scrolls (`bfbeOnScroll`)
- `bfbeHsWhen` (select) **When scrolled**: options: `hide` Hides, `fade` Fades out, keeps its space, `show` Appears only then. Choose what the element does once the page scrolls. Hides closes it up. Fades out, keeps its space leaves a gap. Appears only then keeps it hidden until the page scrolls.
- `bfbeHsCollapse` (select) **Collapses**: options: `across` Sideways; only when `bfbeHsWhen` is `hide` or `show`. For Hides and Appears only then. The element shrinks downward by default. Choose Sideways to shrink its width instead, which suits an element in a row.
- `bfbeHsOver` (select) **Over the first section**: options: `hide` Hides, `show` Appears only then. Hides hides the element while the header sits over the first section. Appears only then hides it the rest of the time. It needs Position set to Sticky, over the first section.
- `bfbeHsIconOnly` (checkbox) **Keep only the icon**. Tick it on a Button that has an icon. Once the page scrolls the words go and the icon stays. The button keeps its name.
- `bfbeHsElEasing` (select) **Easing**: options: `cubic-bezier(0.16, 1, 0.3, 1)` Snappy; writes CSS. Choose how the motion feels: Soft, Medium, Snappy, Ease in, Ease out, Ease in and out, Linear, Overshoot or Soft spring. Snappy is the default.
Styling, in the schema file: `bfbeHsPadding`, `bfbeHsMargin`, `bfbeHsWidth`, `bfbeHsHeight`, `bfbeHsBackground`, `bfbeHsBlur`, `bfbeHsBorder`, `bfbeHsShadow`, `bfbeHsTypography`, `bfbeHsOpacity`, `bfbeHsScale`, `bfbeHsGap`, `bfbeHsOverBackground`, `bfbeHsOverTypography`, `bfbeHsOverBorder`, `bfbeHsOverShadow`, `bfbeHsOverOpacity`, `bfbeHsIconSize`, `bfbeHsElDuration`, `bfbeHsDelay`.

### bfbeHeaderScroll (`bfbeHeaderScroll`)
- `bfbeHsPosition` (select) **Position**: options: `sticky` Sticky, `over` Sticky, over the first section, `off` Off. Pick Sticky, or Sticky, over the first section, to replace the Bricks sticky header. Off turns this feature off, even on a page whose header template has it on.
- `bfbeHsFrom` (select) **From this width**: options: `992` 992px and wider (above Tablet portrait), `768` 768px and wider (above Mobile landscape), `479` 479px and wider (above Mobile portrait); only when `bfbeHsPosition` is `sticky` or `over`. Pick one of your site's breakpoints. Below it the header neither sticks nor sits over the first section, nothing in it changes on scroll, and an element set to Appears only then stays hidden. Always is the default.
- `bfbeHsBegin` (select) **The scrolled state begins**: options: `px` After a distance, `first` When the first section has left; only when `bfbeHsPosition` is `sticky` or `over`. Choose when the header counts as scrolled. By default that is once the page passes the header's own height. Pick After a distance, or When the first section has left, to change it.
- `bfbeHsAt` (number) **Distance (px)**: placeholder 300; only when `bfbeHsPosition` is `sticky` or `over` and `bfbeHsBegin` is `px`. For After a distance. The header counts as scrolled once the page has moved this many pixels. Before that, once the page passes its own height, the header waits out of view. 300 is the default.
- `bfbeHsHide` (number) **After (px)**: placeholder Never hides; only when `bfbeHsPosition` is `sticky` or `over`. Enter a number to hide the header when visitors scroll down. It hides that many pixels after the scrolled state begins and returns when they scroll up. Empty means never.
- `bfbeHsTolerance` (number) **Tolerance (px)**: placeholder 8; only when `bfbeHsPosition` is `sticky` or `over` and `bfbeHsHide` is set. How far visitors must scroll one way before the header hides or returns. 8 is the default, so a small wobble does nothing.
- `bfbeHsHideFx` (select) **Effect**: options: `fade` Fade; only when `bfbeHsPosition` is `sticky` or `over` and `bfbeHsHide` is set. Choose how the header hides. It slides up by default. Pick Fade to fade it out instead.
- `bfbeHsDuration` (number) **Duration**: placeholder 250; only when `bfbeHsPosition` is `sticky` or `over`. How long the changes take, in milliseconds. 250 is the default. The header and every element you style under When the page scrolls use it, unless an element sets its own.
- `bfbeHsEasing` (select) **Easing**: options: `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default); only when `bfbeHsPosition` is `sticky` or `over`. Choose how the motion feels: Soft, Medium, Snappy, Ease in, Ease out, Ease in and out, Linear, Overshoot or Soft spring. Snappy is the default.
- `bfbeHsAnchors` (select) **In-page links land**: options: `under` Under the header, as Bricks does; only when `bfbeHsPosition` is `sticky` or `over`. By default a link to a section stops below the header. Choose Under the header, as Bricks does, to let it land behind the header.
- `bfbeHsZ` (number) **z-index**: placeholder 998; only when `bfbeHsPosition` is `sticky` or `over`. Raise it if something else on the page covers the header. 998 is the default.
- `bfbeHsPreview` (select) **Preview in the builder**: options: `top` At rest, `scrolled` Scrolled, `hidden` Hidden, `over` Over the first section; writes CSS; only when `bfbeHsPosition` is `sticky` or `over`. Pick At rest, Scrolled, Hidden or Over the first section to see that state on the canvas. By default it shows everything, for editing. The page never sees it.

## What it guarantees for accessibility (do not undo)
- The header does not hide on the way down while keyboard focus is inside it, while a menu inside it is open, while the body carries the no-scroll class, or while the pointer is within 12 px of the top of the window.
- Tabbing into a header that has slid away brings it back, because focus inside the header ends the hidden state. A header hidden with Fade has visibility hidden, so it is out of the tab order until it returns.
- An element that has hidden or faded out gets visibility hidden and no pointer events, so it leaves the tab order and cannot be clicked; Hides and Appears only then also use display none where the browser supports it.
- In-page links land below the header unless In-page links land is set to Under the header, as Bricks does.
- With reduced motion requested, the header and every element carrying a setting here change state at once, with no transition and no delay.
- Keep only the icon sizes the button's words to zero instead of removing them, so the button keeps its name.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
