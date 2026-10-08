---
name: bfbe-before-after
description: "Use when placing, wiring or styling BFB Before / After Image (`bfbe-before-after`): two images sit under a draggable divider that runs left and right or top and bottom. Read before writing its settings."
---

# BFB Before / After Image (`bfbe-before-after`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-before-after.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/before-after/

## What it is
Two images sit under a draggable divider that runs left and right or top and bottom. The divider is a native range input, so arrow keys, touch and screen readers all work on it. The frame reserves the images' aspect ratio, taken from the media library, unless you type one.

**Not for:** The divider compares exactly two images, so a sequence of three or more stages needs one comparison per pair. Video and live content cannot go on either side, because both sides are image controls.

**Costs a page:** CSS 1.34 KB, JS 0.79 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Images (`bfbeImages`)
- `before` (image) **Before**. The image to the left of the divider, or above it when Direction is Top and bottom. It accepts a dynamic data tag.
- `after` (image) **After**. The image on the other side of the divider. Choose both images, or the page shows nothing outside the builder.
- `fit` (select) **Image fit**: options: `cover` Fill the frame, cropping (default), `contain` Fit inside the frame; writes CSS. Fill the frame, cropping is the default. Choose Fit inside the frame when no part of either image may be cut off.
- `ratio` (text) **Aspect ratio**: placeholder From the images. Leave it empty to use your images' own ratio, with 16 / 9 as the fallback. Type 4 / 3 to override it.

### Slider (`bfbeSlider`)
- `orientation` (select) **Direction**: options: `horizontal` Left and right (default), `vertical` Top and bottom. Left and right is the default. Pick Top and bottom to stack the images, so the divider moves up and down.
- `start` (number) **Start position (%)**. Where the divider sits when the page loads, 50 by default. Set a value from 0 to 100 when the subject sits off center.
- `hoverMove` (checkbox) **Follow the pointer**. Off by default, so visitors drag the divider. Tick it and a mouse moves the divider without a click. Touch still drags.

### Labels (`bfbeLabels`)
- `showLabels` (checkbox) **Show labels**. Off by default. Tick it to print Before and After on the images.
- `labelBefore` (text) **Label**: placeholder Before; dynamic data accepted; only when `showLabels` is set. Under Before and under After, the word printed on that image, Before or After when left empty. It accepts dynamic data.
- `labelBeforePosition` (select) **Position**: options: `top` Top (default), `middle` Middle, `bottom` Bottom, `custom` Custom; only when `showLabels` is set. Choose Top, Middle, Bottom or Custom for each label. Custom brings up From the left or From the right, plus From the top.
- `labelAfter` (text) **Label**: placeholder After; dynamic data accepted; only when `showLabels` is set. Under Before and under After, the word printed on that image, Before or After when left empty. It accepts dynamic data.
- `labelAfterPosition` (select) **Position**: options: `top` Top, `middle` Middle, `bottom` Bottom, `custom` Custom; only when `showLabels` is set. Choose Top, Middle, Bottom or Custom for each label. Custom brings up From the left or From the right, plus From the top.
Styling, in the schema file: `labelBeforeX`, `labelBeforeY`, `labelAfterX`, `labelAfterY`, `labelTypography`, `labelBackground`, `labelPadding`, `labelBorder`, `labelOffset`.

### Divider (`bfbeDivider`)
Styling only, every key in the schema file: `dividerWidth`, `dividerColor`.

### Handle (`bfbeHandle`)
- `handleText` (text) **Text**: placeholder Drag; dynamic data accepted. A word such as Drag, shown instead of the arrows. It accepts dynamic data, and the arrow controls hide while it is filled in.
- `handleIconLeft` (icon) **Left arrow**: only when `handleText` is not set. Your own icon for the left side of the handle, in place of the drawn arrows.
- `handleIconRight` (icon) **Right arrow**: only when `handleText` is not set. Your own icon for the right side. Leave it empty and it mirrors the left arrow, or set both to use them as they are.
Styling, in the schema file: `handleSize`, `handleBackground`, `handleBorder`, `handleShadow`, `handleIconSize`, `handleIconGap`, `handleIconColor`.

## What it guarantees for accessibility (do not undo)
- The divider is a native range input named Compare plus the two label words, such as Compare Before and After.
- Tab reaches it, and the arrow keys, Home and End move it. In a vertical comparison the Up and Down arrows move the divider the way they point.
- Its value is announced as a percentage through aria-valuetext, updated as the divider moves.
- The labels, the line and the handle are hidden from assistive technology, so the range input is the one control a screen reader finds.
- A visible focus outline is drawn around the handle when the range input has keyboard focus.
- With reduced motion requested, the handle's small hover scale runs with no transition.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
