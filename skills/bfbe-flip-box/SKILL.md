---
name: bfbe-flip-box
description: "Use when placing, wiring or styling BFB Flip Box (`bfbe-flip-box`): two faces, front and back, built as ordinary Bricks blocks, swap on hover, on click, or from a button you place and style yourself. Read before writing its settings."
---

# BFB Flip Box (`bfbe-flip-box`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-flip-box.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/flip-box/

## What it is
Two faces, front and back, built as ordinary Bricks blocks, swap on hover, on click, or from a button you place and style yourself. Both faces share one grid cell, so the card takes the height of its taller face and you set no height. The face out of view is made inert and hidden from assistive technology until the card turns.

**Not for:** The two faces share one grid cell, so one of them is always hidden from view. Content visitors must compare side by side, or read in full before deciding, belongs in a plain layout.

**Costs a page:** CSS 1.33 KB, JS 2.05 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-flip-box",
    "settings": {},
    "children": [
        {
            "name": "block",
            "settings": {
                "_background": {
                    "color": {
                        "hex": "#1f2937"
                    }
                },
                "_alignItems": "center",
                "_justifyContent": "center",
                "_rowGap": "16px",
                "_padding": {
                    "top": "40",
                    "right": "30",
                    "bottom": "40",
                    "left": "30"
                },
                "_hidden": {
                    "_cssClasses": "bfbe-flip-box__front"
                }
            },
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "Front",
                        "tag": "h3",
                        "_typography": {
                            "color": {
                                "hex": "#ffffff"
                            },
                            "font-size": "18px",
                            "text-align": "center"
                        }
                    }
                },
                {
                    "name": "button",
                    "settings": {
                        "text": "Show more",
                        "_cssClasses": "bfbe-flip-trigger",
                        "_background": {
                            "color": {
                                "hex": "#ffffff"
                            }
                        },
                        "_typography": {
                            "color": {
                                "hex": "#1f2937"
                            }
                        },
                        "_border": {
                            "radius": {
                                "top": "999",
                                "right": "999",
                                "bottom": "999",
                                "left": "999"
                            }
                        }
                    }
                }
            ]
        },
        {
            "name": "block",
            "settings": {
                "_background": {
                    "color": {
                        "hex": "#0d9488"
                    }
                },
                "_alignItems": "center",
                "_justifyContent": "center",
                "_rowGap": "16px",
                "_padding": {
                    "top": "40",
                    "right": "30",
                    "bottom": "40",
                    "left": "30"
                },
                "_hidden": {
                    "_cssClasses": "bfbe-flip-box__back"
                }
            },
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "Back",
                        "tag": "h3",
                        "_typography": {
                            "color": {
                                "hex": "#ffffff"
                            },
                            "font-size": "18px",
                            "text-align": "center"
                        }
                    }
                },
                {
                    "name": "button",
                    "settings": {
                        "text": "Show less",
                        "_cssClasses": "bfbe-flip-trigger",
                        "_background": {
                            "color": {
                                "hex": "#ffffff"
                            }
                        },
                        "_typography": {
                            "color": {
                                "hex": "#1f2937"
                            }
                        },
                        "_border": {
                            "radius": {
                                "top": "999",
                                "right": "999",
                                "bottom": "999",
                                "left": "999"
                            }
                        }
                    }
                }
            ]
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Flip (`bfbeFlip`)
- `trigger` (select) **Flip on**: options: `hover` Hover (default), `click` Click, `none` None. Choose Hover, Click or None, and set it per breakpoint. Hover is the default. Pick None when just your own button should turn the card.
- `effect` (select) **Effect**: options: `flip` Flip (default), `slide` Slide over, `push` Push across, `zoom-in` Zoom in, `zoom-out` Zoom out, `cube` Cube turn, `circle` Circle reveal, `fade` Crossfade. Pick Flip, Slide over, Push across, Zoom in, Zoom out, Cube turn, Circle reveal or Crossfade. Flip is the default.
- `direction` (select) **Direction**: options: `left` Left (default), `right` Right, `up` Up, `down` Down; only when `effect` is not `zoom-in` or `zoom-out` or `circle` or `fade`. Left, Right, Up or Down, with Left as the default. It shows for Flip, Slide over, Push across and Cube turn.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium (default), `cubic-bezier(0.16, 1, 0.3, 1)` Snappy, `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. How the turn speeds up and slows down, Medium by default. Pick Custom and type your own curve in Custom curve.
- `reducedMotion` (select) **Reduced motion**: options: `fade` Crossfade (default), `instant` Instant. What visitors who ask their device for less motion see. Crossfade, the default, fades the faces at the set duration. Instant swaps them at once.
- `equalHeights` (checkbox) **Match face heights**. Tick it when the faces have backgrounds and the shorter one should fill the card. It is off by default, so each face keeps its own height.
Styling, in the schema file: `duration`, `easingCustom`, `perspective`.

### Faces (`bfbeFaces`)
Styling only, every key in the schema file: `minHeight`, `faceBorder`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Held still, so you can style it (default), `live` Working, as on the site. The card is held still by default, so you can style it. Pick Working, as on the site, to see it turn in the builder.

## What it guarantees for accessibility (do not undo)
- Any element carrying the class bfbe-flip-trigger becomes a button for assistive technology, answers Enter and Space, and reports aria-expanded for the card's state.
- When nothing on the card carries that class, the published page adds a Show more button that stays invisible until keyboard focus reaches it.
- The face out of view is set inert and aria-hidden, so its links and buttons leave the tab order until the card turns.
- Escape turns a flipped card back to the front and moves focus to a flip control there.
- On a touch screen a tap turns a Hover card, because hover does not exist there.
- With reduced motion requested, every effect becomes a crossfade at the set duration, and the Reduced motion control can make it Instant.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
