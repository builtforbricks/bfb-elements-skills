---
name: bfbe-marquee
description: "Use when placing, wiring or styling BFB Marquee (`bfbe-marquee`): a strip of any elements scrolled continuously, sideways or upward, at a speed you set in pixels per second. Read before writing its settings."
---

# BFB Marquee (`bfbe-marquee`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-marquee.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/marquee/

## What it is
A strip of any elements scrolled continuously, sideways or upward, at a speed you set in pixels per second. It pauses while keyboard focus is inside it, pauses under the pointer unless you change that, and offers an optional pause button. With reduced motion requested it becomes a still strip that visitors scroll by hand.

**Not for:** Everything in the strip moves continuously, so text people must read in full, or links they need to reach quickly, belongs in a static layout. The strip is a single line of items, repeated to fill the width, so it cannot wrap into rows or a grid.

**Costs a page:** CSS 0.97 KB, JS 1.10 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-marquee",
    "settings": {},
    "children": [
        {
            "name": "text-basic",
            "settings": {
                "text": "One"
            }
        },
        {
            "name": "text-basic",
            "settings": {
                "text": "Two"
            }
        },
        {
            "name": "text-basic",
            "settings": {
                "text": "Three"
            }
        },
        {
            "name": "text-basic",
            "settings": {
                "text": "Four"
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Motion (`bfbeMotion`)
- `orientation` (select) **Direction**: options: `horizontal` Horizontal (default), `vertical` Vertical. Horizontal is the default. Vertical scrolls the items upward inside a fixed height, which you set under Strip.
- `reverse` (checkbox) **Reverse**. Off by default. Tick it to run the strip rightward, or downward when Direction is Vertical.
- `speed` (number) **Speed (px/s)**. How fast the strip travels, 60 pixels per second by default. A longer strip takes longer to loop.
- `pauseOnHover` (select) **Under the pointer**: options: `pause` Pauses (default), `keep` Keeps moving. Pauses is the default. Choose Keeps moving for a strip that should run whatever the pointer does.

### Pause button (`bfbePause`)
- `pauseButton` (checkbox) **Show pause button**. Off by default. Tick it to add a real button that switches the whole strip between Pause and Play.
- `pausePosition` (select) **Position**: options: `top-right` Top right (default), `top-left` Top left, `bottom-right` Bottom right, `bottom-left` Bottom left; only when `pauseButton` is set. Choose Top right, Top left, Bottom right or Bottom left for the button. Top right is the default.
Styling, in the schema file: `pauseSize`, `pauseOffset`, `pauseColor`, `pauseBackground`, `pauseHoverBackground`, `pauseBorder`, `pauseShadow`.

### Strip (`bfbeStrip`)
- `fade` (checkbox) **Fade the edges**. Off by default. Tick it to fade both ends of the strip to transparent. Fade size is 48px by default.
Styling, in the schema file: `gap`, `height`, `stripBorder`, `fadeSize`, `itemAlign`.

## What it guarantees for accessibility (do not undo)
- Scrolling pauses whenever keyboard focus is inside the strip, with nothing to configure.
- The pause button is a real button whose hidden text switches between Pause and Play as the state changes.
- The repeated copies that fill the strip are aria-hidden and kept out of the tab order, so each item is met once.
- With reduced motion requested, the strip stops animating, drops the copies and the pause button, and becomes a strip visitors can scroll.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
