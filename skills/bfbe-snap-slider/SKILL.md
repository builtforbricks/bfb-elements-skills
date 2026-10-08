---
name: bfbe-snap-slider
description: "Use when placing, wiring or styling BFB Advanced Snap Slider (`bfbe-snap-slider`): a row of Snap Slide children in a native scroll container with scroll snapping, so the browser scrolls and the stylesheet snaps, with no slider library. Read before writing its settings."
---

# BFB Advanced Snap Slider (`bfbe-snap-slider`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-snap-slider.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/snap-slider/

## What it is
A row of Snap Slide children in a native scroll container with scroll snapping, so the browser scrolls and the stylesheet snaps, with no slider library. Slides can run off the page's edges while the row stays aligned with your content, and a Width pattern repeats along them. Each Snap Slide can take its own width or sit after a chosen loop item, and a small script adds buttons, dots, dragging and autoplay.

**Not for:** Not for a continuous loop or a crossfade: it is a scroll container that snaps, so it has a start and an end. A looping carousel belongs in Bricks' own Slider element.

**Costs a page:** CSS 2.00 KB, JS 2.30 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable. Its own children: `bfbe-snap-slide`.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-snap-slider",
    "settings": {},
    "children": [
        {
            "name": "bfbe-snap-slide",
            "settings": {},
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "A slide",
                        "tag": "h3"
                    }
                },
                {
                    "name": "text-basic",
                    "settings": {
                        "text": "Anything can go in here."
                    }
                }
            ]
        },
        {
            "name": "bfbe-snap-slide",
            "settings": {},
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "A slide",
                        "tag": "h3"
                    }
                },
                {
                    "name": "text-basic",
                    "settings": {
                        "text": "Anything can go in here."
                    }
                }
            ]
        },
        {
            "name": "bfbe-snap-slide",
            "settings": {},
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "A slide",
                        "tag": "h3"
                    }
                },
                {
                    "name": "text-basic",
                    "settings": {
                        "text": "Anything can go in here."
                    }
                }
            ]
        },
        {
            "name": "bfbe-snap-slide",
            "settings": {},
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "A slide",
                        "tag": "h3"
                    }
                },
                {
                    "name": "text-basic",
                    "settings": {
                        "text": "Anything can go in here."
                    }
                }
            ]
        }
    ]
}
```

`bfbe-snap-slide` (BFB Snap Slide), 40 controls, schema `../bfbe-schemas/references/elements/bfbe-snap-slide.json`, nestable itself.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Slides (`bfbeSlides`)
- `label` (text) **Name**: placeholder Slides; dynamic data accepted. The label screen readers read for the scrolling list, Slides by default. It accepts dynamic data.
- `align` (select) **Snap slides to**: options: `start` Their start edge (default), `center` Their centre; writes CSS. Where a slide lines up when the row snaps, Their start edge by default, or Their centre.
- `snap` (select) **Snapping**: options: `x mandatory` Always land on a slide (default), `x proximity` Only when close to one, `none` Off, free scrolling; writes CSS. Choose Always land on a slide, the default, Only when close to one, or Off, free scrolling for a looser feel.
- `stop` (select) **Fast swipe**: options: `normal` Can pass several slides (default), `always` Stops at the next slide; writes CSS. Can pass several slides, the default, lets a quick swipe run past slides. Stops at the next slide halts it at the next one.
Styling, in the schema file: `slideWidth`, `perView`, `gap`.

### Edges (`bfbeEdges`)
- `bleed` (select) **Full bleed**: options: `none` No, stay inside the container (default), `both` Both edges, `end` The end edge only. No, stay inside the container is the default. Choose Both edges or The end edge only to let slides run off the page, while the row still starts in line with your content.
- `fade` (checkbox) **Fade the edges**. Tick it to fade the row out at its edges. It is off by default, and an edge the row has reached stays sharp.
Styling, in the schema file: `inset`, `fadeSize`.

### Width pattern (`bfbePattern`)
- `pattern` (repeater) **Pattern**: placeholder Width. Rows of widths that repeat along the slides, such as wide, narrow, narrow. Each row has a Width, per breakpoint if you like, and an optional Class to add. A slide's own width wins.
- `patternUse` (select) **Use the pattern**: options: `var(--bfbe-ss-pw)` Yes (default), `initial` No, use the slide width; writes CSS; only when `pattern` is set. Yes by default once you have rows. Choose No, use the slide width to switch the pattern off at the breakpoint you are editing.

### Buttons (`bfbeButtons`)
- `arrows` (checkbox) **Show them**. Tick it to add previous and next buttons. A new slider has none until you tick it.
- `navPosition` (select) **Position**: options: `above` Above the slides (default), `below` Below the slides, `sides` On the sides, over the slides; only when `arrows` is set. Above the slides, the default, Below the slides, or On the sides, over the slides.
- `navHover` (checkbox) **Show on hover**: only when `navPosition` is `sides` and `arrows` is set. With the buttons on the sides, keep them hidden until the pointer is over the slider or focus is inside it. Screens with no hover always show them.
- `perMove` (number) **Slides per click**: only when `arrows` is set. How many slides each press moves, 1 by default. Raise it for rows of small cards.
- `prevLabel` (text) **Previous label**: dynamic data accepted; only when `arrows` is set. Text beside the arrow, empty by default. With no text, the button is an icon that still has the screen reader name Previous.
- `nextLabel` (text) **Next label**: dynamic data accepted; only when `arrows` is set. The same for the next button, whose screen reader name without text is Next.
- `prevIcon` (icon) **Previous icon**: only when `arrows` is set. An icon of your own in place of the drawn arrow.
- `nextIcon` (icon) **Next icon**: only when `arrows` is set. An icon of your own for the next button.
- `counter` (checkbox) **Show it**. Under the Counter heading, tick it to add a count such as 2 / 6 to the button row.
- `counterPlace` (select) **Position**: options: `between` Between the arrows (default), `before` Before the arrows, `after` After the arrows; only when `counter` is set and `arrows` is set and `navPosition` is not `sides`. Above the slides, the default, Below the slides, or On the sides, over the slides.
Styling, in the schema file: `barAlign`, `sideY`, `sideX`, `btnSize`, `btnIcon`, `btnPadding`, `btnBackground`, `btnColor`, `btnBackgroundHover`, `btnBorder`, `btnDim`, `counterTypography`.

### Dots and Progress (`bfbeDots`)
- `dots` (checkbox) **Show them**. Tick it to add previous and next buttons. A new slider has none until you tick it.
- `dotsPosition` (select) **Position**: options: `below` Below the slides (default), `above` Above the slides; only when `dots` is set. Above the slides, the default, Below the slides, or On the sides, over the slides.
- `progress` (checkbox) **Show it**: only when `dots` is not set. Under the Counter heading, tick it to add a count such as 2 / 6 to the button row.
- `barPosition` (select) **Position**: options: `below` Below the slides (default), `above` Above the slides; only when `progress` is set and `dots` is not set. Above the slides, the default, Below the slides, or On the sides, over the slides.
Styling, in the schema file: `dotsSpacing`, `dotsAlign`, `dotSize`, `dotActiveWidth`, `dotGap`, `dotColor`, `dotActiveColor`, `dotBorder`, `dotDim`, `dotHover`, `barSpacing`, `barHeight`, `barTrack`, `barFill`.

### Scrolling (`bfbeMotion`)
- `drag` (checkbox) **Mouse drag**. Tick it to let a mouse drag the row. It is off by default. Touch and keyboard scrolling work either way.
- `autoplay` (checkbox) **Autoplay**. Tick it to move the row on by one slide at a time. At the end the row rewinds to the start.
- `interval` (number) **Seconds per slide**: only when `autoplay` is set. How long autoplay waits on each slide, 4 by default and never under 1.
- `scrollEasing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. The curve those timed moves follow, Snappy unless set.
Styling, in the schema file: `scrollDuration`, `scrollEasingCustom`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Still, so you can style it (default), `live` Working, as on the site. Under the Counter heading, tick it to add a count such as 2 / 6 to the button row.

## What it guarantees for accessibility (do not undo)
- The scrolling row is a list named by Name that takes focus, and ArrowLeft and ArrowRight move it one slide.
- Home and End jump the focused row to its start and its end.
- A Skip the slides link, visible while it has focus, lets a keyboard user jump past a long row.
- Buttons and dots are real buttons, and the dots form a group named Choose a slide, each dot named Slide with its number.
- The current dot carries aria-current, so a screen reader can tell which slide the row is on.
- Previous and next set aria-disabled at the ends of the row, and the counter is hidden from assistive technology because the buttons already show where you are.
- Autoplay never starts under reduced motion, pauses on hover and focus, and stops for good after any click, key or pointer press inside it.
- Under reduced motion smooth scrolling is switched off, so button and key moves jump straight to the slide.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
