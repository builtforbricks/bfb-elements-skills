---
name: bfbe-image-accordion
description: "Use when placing, wiring or styling BFB Image Accordion (`bfbe-image-accordion`): panels side by side, or stacked, that grow under the pointer, on click, or when something inside them has focus. Read before writing its settings."
---

# BFB Image Accordion (`bfbe-image-accordion`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-image-accordion.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/image-accordion/

## What it is
Panels side by side, or stacked, that grow under the pointer, on click, or when something inside them has focus. Each panel is a nested block, so its background image and content are the block's own controls. Content shows can differ per breakpoint, so a phone can show every panel's content while a desktop reveals it on open.

**Not for:** Panels share one row or column of fixed height and trade space as they open, so it suits a few panels with short captions. A long set of images does not fit, because every panel shares one container and none of them scrolls.

**Costs a page:** CSS 0.96 KB, JS 0.94 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-image-accordion",
    "settings": {},
    "children": [
        {
            "name": "block",
            "settings": {
                "_justifyContent": "flex-end",
                "_padding": {
                    "top": "24",
                    "right": "24",
                    "bottom": "24",
                    "left": "24"
                },
                "_background": {
                    "color": {
                        "hex": "#334155"
                    }
                }
            },
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "One",
                        "tag": "h3"
                    }
                },
                {
                    "name": "text-basic",
                    "settings": {
                        "text": "A line about it."
                    }
                }
            ]
        },
        {
            "name": "block",
            "settings": {
                "_justifyContent": "flex-end",
                "_padding": {
                    "top": "24",
                    "right": "24",
                    "bottom": "24",
                    "left": "24"
                },
                "_background": {
                    "color": {
                        "hex": "#0f766e"
                    }
                }
            },
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "Two",
                        "tag": "h3"
                    }
                },
                {
                    "name": "text-basic",
                    "settings": {
                        "text": "A line about it."
                    }
                }
            ]
        },
        {
            "name": "block",
            "settings": {
                "_justifyContent": "flex-end",
                "_padding": {
                    "top": "24",
                    "right": "24",
                    "bottom": "24",
                    "left": "24"
                },
                "_background": {
                    "color": {
                        "hex": "#7c3aed"
                    }
                }
            },
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "Three",
                        "tag": "h3"
                    }
                },
                {
                    "name": "text-basic",
                    "settings": {
                        "text": "A line about it."
                    }
                }
            ]
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Panels (`bfbePanels`)
- `direction` (select) **Direction**: options: `row` Side by side (default), `column` Stacked. Choose Side by side, the default, or Stacked.
- `trigger` (select) **Expands on**: options: `hover` Hover (default), `click` Click. Choose Hover, the default, or Click. A panel also opens when focus moves inside it, whichever you pick. With Click, a second click closes the open panel.
- `active` (number) **Open at first**. The number of the panel that is open when the page loads, 1 unless set. Enter 0 to open none.
- `contentShows` (select) **Content shows**: options: `auto` Always (default), `none` Only when open; writes CSS. Choose Always, the default, or Only when open. Only when open hides a closed panel's content and blocks clicks on it until it opens. You can set it per breakpoint.
- `stackBelow` (select) **Stack below**: options: `never` Never, `480` 480px, `640` 640px (default), `768` 768px, `992` 992px; only when `direction` is not `column`. With Side by side panels, the width under which they stack, 640px unless set. The other choices are 480px, 768px, 992px and Never.

### Panel look (`bfbeLook`)
Styling only, every key in the schema file: `height`, `grow`, `gap`, `panelBorder`, `overlay`.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. The curve the movement follows, Snappy unless set. The others are Soft, Medium, Ease in, Ease out, Ease in and out, Linear, Overshoot, Soft spring and Custom.
- `contentFrom` (select) **Content comes in**: options: `below` From below (default), `above` From above, `start` From the start edge, `end` From the end edge, `fade` By fading alone, `scale` By growing, `none` Instantly. Pick how the content arrives. From below is the default. The others are From above, From the start edge, From the end edge, By fading alone, By growing and Instantly.
Styling, in the schema file: `duration`, `easingCustom`, `revealDelay`, `contentShift`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Open, so you can style them (default), `closed` Closed, as the site leaves it, `live` Working, as on the site. Choose how the canvas shows the panels. Open, the default, lays them out for styling, Closed matches the site at rest, and Working lets them answer the pointer in the canvas.

## What it guarantees for accessibility (do not undo)
- Focus anywhere inside a panel opens it, whatever Expands on is set to.
- With Hover, a panel holding no link or button of its own gets tabindex 0, so Tab can reach it.
- With Click, a panel with no link or button of its own gets a button in its heading, or acts as a button itself.
- Both forms carry aria-expanded, and Enter and Space toggle a panel that acts as the button.
- When scripting is off, content hidden until open is shown at all times.
- Under reduced motion the panel growth, the overlay fade and the content reveal run with no transition.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
