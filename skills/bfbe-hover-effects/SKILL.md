---
name: bfbe-hover-effects
description: "Use when placing, wiring or styling BFB Hover Effects (`hover-effects`): a feature on every element, Bricks' own included, not an element of its own: the Hover effect group on the Style tab, after Bricks' own style groups, offers nine effects with Strength, Speed and Delay. Read before writing its settings."
---

# BFB Hover Effects (`hover-effects`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/hover-effects.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/hover-effects/

## What it is
A feature on every element, Bricks' own included, not an element of its own: the Hover effect group on the Style tab, after Bricks' own style groups, offers nine effects with Strength, Speed and Delay. A card can tick Children respond to hover, so parts inside it set to A hovered parent play when the card is hovered, and a Delay on each part, except Tilt and Follow the pointer, staggers them. The stylesheet loads on a page where an element has an Effect or Children respond to hover ticked, the script where an element uses Tilt or Follow the pointer, and the builder canvas loads both.

**Not for:** Not for changing one property on hover, such as a colour or a shadow, which is a hover state on Bricks' own style controls; an effect here answers its own element or a parent with Children respond to hover ticked.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Where it lives
A feature, not an element: its controls are added to every element, Bricks' own included.

## Settings that decide the build

### Hover effect (`bfbeHover`)
- `bfbeHoverEffect` (select) **Effect**: options: `lift` Lift, `zoom` Zoom the picture, `shine` Shine, `border` Gradient border, `tilt` Tilt, `follow` Follow the pointer, `fade` Fade in, `slide` Slide in, `grow` Grow. Pick one of nine: Lift, Zoom the picture, Shine, Gradient border, Tilt, Follow the pointer, Fade in, Slide in or Grow. The last three start faded, offset or smaller and settle on hover.
- `bfbeHoverOn` (select) **Responds to**: options: `parent` A hovered parent; only when `bfbeHoverEffect` is set. Leave it on This element to play the effect when the element is hovered. Choose A hovered parent to play it when the card it sits in is hovered. The card needs Children respond to hover ticked.
- `bfbeHoverFrom` (select) **Comes from**: options: `up` Above, `left` The left, `right` The right; only when `bfbeHoverEffect` is `slide`. For Slide in. Choose where the element starts: Above, The left or The right. Below is the default.
- `bfbeHoverOff` (select) **Off below**: options: `480` 480 px, `640` 640 px, `768` 768 px, `992` 992 px; only when `bfbeHoverEffect` is set. Choose 480, 640, 768 or 992 px and the effect switches off on screens that wide or narrower, where the element shows as normal. Never is the default.
- `bfbeHoverScope` (checkbox) **Children respond to hover**. Tick it on a card. Parts inside it set to A hovered parent then play when the card is hovered. The card needs no effect of its own.
Styling, in the schema file: `bfbeHoverStrength`, `bfbeHoverSpeed`, `bfbeHoverDelay`, `bfbeHoverColor`.

## What it guarantees for accessibility (do not undo)
- Lift, Zoom the picture, Shine and Gradient border play when the element is hovered or has keyboard focus. Fade in, Slide in and Grow also play when keyboard focus is anywhere inside the element.
- With A hovered parent, the effect plays when the parent is hovered or when focus is anywhere inside it, except Tilt and Follow the pointer, which follow the mouse over the parent and do not react to focus.
- Tilt and Follow the pointer react to a mouse, not to touch or a pen. An element set to Tilt or Follow the pointer lifts 4 px times Strength when it has keyboard focus, unless it responds to a hovered parent, and Off below turns that off too.
- On a screen with no hover, such as a touch screen, Fade in, Slide in and Grow show in their finished state, so nothing waits behind a hover. The other effects need a screen that can hover.
- Fade in changes opacity alone, so an element waiting to fade in can still be reached by keyboard and assistive technology, and it shows itself when it receives focus.
- With reduced motion requested, transitions and animations stop: Lift, Zoom the picture, Fade in, Slide in and Grow change at once, the Shine sweep is removed, the Gradient border stops spinning, and Tilt and Follow the pointer ignore the pointer.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
