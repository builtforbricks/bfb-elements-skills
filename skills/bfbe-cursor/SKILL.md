---
name: bfbe-cursor
description: "Use when placing, wiring or styling BFB Interactive Cursor (`bfbe-cursor`): a ring that follows the mouse pointer, grows over links and buttons, and can show a word inside itself over anything you tag. Read before writing its settings."
---

# BFB Interactive Cursor (`bfbe-cursor`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-cursor.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/cursor/

## What it is
A ring that follows the mouse pointer, grows over links and buttons, and can show a word inside itself over anything you tag. The browser's own pointer stays unless you hide it, and steps aside only while the ring shows a word. The ring switches itself off for touch, reduced motion and forced colors. Block effects add a spotlight, a reveal, an image trail or a floating gallery image to any block you tag.

**Not for:** Not for guiding keyboard or touch visitors: the ring follows a mouse alone and is hidden from assistive technology, so it carries nothing a visitor must know. One Interactive Cursor runs per page, so place a single one, usually in the header template.

**Costs a page:** CSS 2.05 KB, JS 2.83 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** no · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Cursor (`bfbeCursor`)
- `mode` (select) **Native cursor**: options: `ring` Keep it, add the ring (default), `replace` Hide it, `none` Keep it, effects only. What happens to the browser's own pointer. Keep it, add the ring is the default. Hide it swaps the pointer for the ring and a dot. Keep it, effects only draws no ring.
- `lag` (number) **Follow delay**. How far the ring lags behind the pointer, from 0 for instant to 1 for lazy. The default is 0.15. Raise it for a looser trail.
- `offBelow` (select) **Off below**: options: `never` Never, `480` 480px, `640` 640px, `768` 768px, `992` 992px (default). The window width at or under which the ring and the Block effects are off, 992px by default. Choose Never to keep them on at every width where a mouse is used.
- `shape` (select) **Shape**: options: `ring` Ring (default), `cross` Crosshair. Choose Ring, the default, or Crosshair. A Crosshair turns into the ring over anything it grows over, and while it shows a word.

### Hover effect (`bfbeHover`)
- `hoverSelector` (text) **Grows over**: placeholder a, button, [role="button"]. The CSS selector for what the ring grows over, a, button, [role="button"] by default. Add your own classes when cards or custom buttons should count too.
- `labels` (repeater) **Labels**. Add rows that pair a CSS selector (Over) with a word (Say). The word shows inside the ring over matching elements. Say accepts dynamic data. Giving any element data-bfbe-cursor="View" does the same.
- `magnet` (checkbox) **Magnetic**. Tick it to pull the elements the ring grows over toward the pointer. Use it for call-to-action buttons and leave it off for body links.
- `magnetPull` (number) **Pull (px)**: only when `magnet` is set. How far a magnetic element can move toward the pointer, 12px unless set.
- `sticky` (checkbox) **Ring hugs the element**. Tick it so the ring takes the shape of the element it is over. Use it for a highlight box, not a growing circle.
- `stickyPad` (number) **Hug distance (px)**: only when `sticky` is set. The room between the element and the ring that hugs it, 6px unless set.
Styling, in the schema file: `hoverScale`.

### Look (`bfbeLook`)
- `blend` (select) **Blend**: options: `normal` Normal (default), `difference` Invert what is under it. Choose Normal, the default, or Invert what is under it. Inverting blends the ring by difference, so it stays visible on light and dark areas.
- `noFillBorder` (checkbox) **No border once filled**. Tick it to drop the ring's border while it is filled, over an element or behind a word. It is off by default.
Styling, in the schema file: `size`, `color`, `ringBorder`, `dotSize`, `fill`, `labelBackground`, `labelTypography`.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. The curve those changes follow, Snappy unless set.
- `stretch` (checkbox) **Stretches with speed**. Tick it to stretch the ring along its direction of travel as the pointer speeds up. It is off by default.
- `stretchAmount` (number) **Stretch**: only when `stretch` is set. How much the ring stretches, 0.35 unless set, from 0 to 1.
- `pulse` (checkbox) **Pulses on click**. Tick it to send a pulse out of the ring each time the pointer is pressed. It is off by default.
Styling, in the schema file: `duration`, `easingCustom`, `pulseColor`.

### Block effects (`bfbeFx`)
- `trailImages` (image-gallery) **Images**. Under Image trail, the pictures that appear along the pointer's path over a block whose data-bfbe-fx is trail. With none chosen, the trail uses the pictures inside the block.
- `trailEvery` (number) **Spacing (px)**. How far the pointer travels between two trail pictures, 80 by default.
- `followImages` (image-gallery) **Images**. Under Image trail, the pictures that appear along the pointer's path over a block whose data-bfbe-fx is trail. With none chosen, the trail uses the pictures inside the block.
Styling, in the schema file: `fxSize`, `fxColor`, `fxFade`, `fxEdge`, `trailSize`, `trailLife`, `followSize`, `followBorder`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Still, so you can style it (default), `live` Working, as on the site. Still, the default, shows the ring and the dot where the element sits, so you can style them. Working lets the ring follow the pointer over the canvas.

## What it guarantees for accessibility (do not undo)
- The ring, dot and label are aria-hidden and ignore pointer events, so they add nothing to the reading order and never block a click.
- It follows a mouse alone: touch, pen and keyboard input never move it. The browser's own pointer hides only under Hide it, or while the ring shows a word.
- For coarse pointers, reduced motion or forced colors, the script never tracks the pointer, and the stylesheet hides the ring and the Block effects.
- Where Hide it is chosen, the browser's own pointer is hidden just when motion is not reduced and forced colors are off.
- The browser's own pointer returns over text fields, text areas and selects, even where Hide it is chosen.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
