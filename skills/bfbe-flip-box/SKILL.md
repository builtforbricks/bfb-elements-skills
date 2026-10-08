---
name: bfbe-flip-box
description: "Use when building a flip card, a hover reveal or a front-and-back card with BFB Flip Box (`bfbe-flip-box`): two ordinary Bricks blocks that swap on hover, on click, or from any element marked with the class bfbe-flip-trigger. Read before writing its settings, marking its triggers or rounding its corners."
---

# BFB Flip Box (`bfbe-flip-box`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
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

## Rendered DOM

```html
<div class="brxe-bfbe-flip-box bfbe-flip-box bfbe-flip-box--flip bfbe-flip-box--left bfbe-flip-box--equal is-flipped"
     data-bfbe-flip-trigger="click" data-bfbe-flip-trigger-at="478:none" data-bfbe-flip-ready="1">
  <div class="bfbe-flip-box__inner" id="bfbe-{id}-faces">
    <div class="brxe-block bfbe-flip-box__front" inert aria-hidden="true">
      <h3 class="brxe-heading">Front</h3>
      <span class="brxe-button bfbe-flip-trigger" role="button" tabindex="0"
            aria-controls="bfbe-{id}-faces" aria-expanded="true">Show more</span>
    </div>
    <div class="brxe-block bfbe-flip-box__back">… the same, with "Show less" …</div>
  </div>
</div>
```

- Root `.bfbe-flip-box`, a `div`: `bfbe-flip-box--{effect}` always; `bfbe-flip-box--{direction}` for `flip`, `slide`, `push` and `cube` alone; `--equal` from `equalHeights`; `--rm-instant` from `reducedMotion: "instant"`; `--canvas` in the builder's held-still view.
- `data-bfbe-flip-trigger` holds the base **Flip on** value. `data-bfbe-flip-trigger-at` lists breakpoint values as `width:value`, narrowest first; the script tests each as `max-width` and the first match wins.
- States: `is-flipped` on the root while the back shows, and `data-bfbe-flip-ready="1"` once the script has run. Until then, CSS alone shows the back on hover or when focus enters it.
- `.bfbe-flip-box__inner` (id `bfbe-{element id}-faces`, with the loop index added inside a query loop) stacks every face in one grid cell. CSS picks front and back by position; the script adds `bfbe-flip-box__front` to the first child and `bfbe-flip-box__back` to the rest.
- The face out of view gets `inert` and `aria-hidden="true"`. Every control gets `aria-controls` (the inner's id) and the card's `aria-expanded`. A marked element that is not a `<button>` also gets `role="button"`, and `tabindex="0"` unless it is a link with `href` or has its own. Bricks' **Button** with no link renders a `<span>`, so it gets both.
- With nothing marked, the published page puts `<button class="bfbe-flip-box__toggle">` before the inner, its words in `.bfbe-flip-box__label` (Show more, Show less: fixed, not a setting), clipped to 1px until `:focus-visible`.
- Where controls write: `duration`, `easing`, `easingCustom` and `perspective` set `--bfbe-flip-duration`, `--bfbe-flip-easing`, `--bfbe-ease-custom` and `--bfbe-flip-perspective` on the root. `minHeight` writes `min-height` on every face. `faceBorder` writes the border to `.bfbe-flip-box__inner`; the faces inherit its radius (12px when unset) and clip with `overflow: hidden`.

## Wiring to other elements

The card wires inward alone. Its controls are elements inside its own faces carrying `bfbe-flip-trigger` in **CSS classes** (`_cssClasses`): a Button, an Icon, a Heading, a Block.
- By class, never `_cssId`. Bricks moves the element id into a class inside a query loop, and component instances share ids, so an id is neither found nor unique where cards repeat.
- The script collects marked elements inside the card and keeps those whose nearest `.bfbe-flip-box` is this card. A nested flip box keeps its own triggers; a marked element outside every card does nothing, and nothing outside the card can turn it.
- Every control drives the same region and reports the same `aria-expanded`. The script never rewrites a control's own text, so each face carries its own words.
- It initialises on load and again on Bricks' AJAX events (`bricks/ajax/popup/loaded`, `bricks/ajax/pagination/completed`, `bricks/ajax/load_page/completed`, `bricks/ajax/query_result/displayed`), so cards in a Bricks popup or in AJAX-loaded query results need nothing added.
- Clicks on the card are never stopped, so Bricks' popups, offcanvas and mobile menus still close from them.

## Verified patterns

**Product card that slides on hover** (demo page `demo-bfb-flip-box`, The Fell hood). Hover is the default **Flip on**; **Effect** `slide` from the left brings the back over a front that stays put, so give the back its own `_background`. Nothing is marked: a mouse turns it by hovering, a finger by a tap, the keyboard through the fallback. The demo's images, fills and 20px face corners are universal settings left out here.

```json
{
  "name": "bfbe-flip-box",
  "settings": { "effect": "slide", "direction": "left", "minHeight": "440px", "equalHeights": true, "reducedMotion": "instant" },
  "children": [
    { "name": "block", "settings": {}, "children": [
      { "name": "block", "settings": {}, "children": [
        { "name": "text-basic", "settings": { "text": "£190", "tag": "p" } },
        { "name": "heading", "settings": { "text": "The Fell hood", "tag": "h3" } }
      ] }
    ] },
    { "name": "block", "settings": {}, "children": [
      { "name": "block", "settings": {}, "children": [
        { "name": "text-basic", "settings": { "text": "Merino and mohair", "tag": "p" } },
        { "name": "heading", "settings": { "text": "The Fell hood", "tag": "h3" } },
        { "name": "text-basic", "settings": { "text": "A hood that stays up in a wind, a hem that stays down in one.", "tag": "p" } }
      ] },
      { "name": "block", "settings": {}, "children": [
        { "name": "text-basic", "settings": { "text": "£190", "tag": "p" } },
        { "name": "button", "settings": { "text": "Add to bag", "link": { "type": "external", "url": "#bag" }, "size": "sm" } }
      ] }
    ] }
  ]
}
```

**Click card turned by icons** (fixture page `fixture-flip-box`, "Flip up, icon triggers"). `trigger: "click"` and `direction: "up"`, with an Icon marked on each face; the script makes each icon a keyboard button. The `aria-label` in each icon's `_attributes` is added here, because an icon has no text to name it.

```json
{
  "name": "bfbe-flip-box",
  "settings": { "trigger": "click", "effect": "flip", "direction": "up", "equalHeights": true },
  "children": [
    { "name": "block", "settings": {}, "children": [
      { "name": "heading", "settings": { "text": "Flip up, icon triggers", "tag": "h3" } },
      { "name": "icon", "settings": { "icon": { "library": "themify", "icon": "ti-arrow-right" }, "_cssClasses": "bfbe-flip-trigger", "_attributes": [ { "name": "aria-label", "value": "Show more" } ] } }
    ] },
    { "name": "block", "settings": {}, "children": [
      { "name": "heading", "settings": { "text": "Back of 2", "tag": "h3" } },
      { "name": "icon", "settings": { "icon": { "library": "themify", "icon": "ti-arrow-left" }, "_cssClasses": "bfbe-flip-trigger", "_attributes": [ { "name": "aria-label", "value": "Show less" } ] } }
    ] }
  ]
}
```

**One card per post** (fixture page `fixture-flip-box`, the query-loop card). `hasLoop` and `query` repeat the card per page with `{post_title}` on the front. The marked Buttons find their own card by class, and each card's inner id carries its loop index.

```json
{
  "name": "bfbe-flip-box",
  "settings": { "trigger": "click", "effect": "flip", "direction": "right", "equalHeights": true, "hasLoop": true, "query": { "objectType": "post", "post_type": [ "page" ], "posts_per_page": 3, "orderby": "title" } },
  "children": [
    { "name": "block", "settings": {}, "children": [
      { "name": "heading", "settings": { "text": "{post_title}", "tag": "h3" } },
      { "name": "button", "settings": { "text": "Show more", "_cssClasses": "bfbe-flip-trigger" } }
    ] },
    { "name": "block", "settings": {}, "children": [
      { "name": "heading", "settings": { "text": "Back of 16", "tag": "h3" } },
      { "name": "button", "settings": { "text": "Show less", "_cssClasses": "bfbe-flip-trigger" } }
    ] }
  ]
}
```

## Gotchas

- **Every direct child is a face.** The first child is the front and every later child joins the back in the same cell, so a third child sits over the second; the canvas flags more or fewer than two. Position decides, not the face classes, so reordering in the structure panel swaps the faces. <!-- src: plugins/bfb-elements/elements/flip-box.php:493 ; src/elements/flip-box/flip-box.css:34 ; src/elements/flip-box/flip-box.js:46 -->
- **Mark an element on each face, or on none.** One marked element anywhere stops the published page's fallback button. If the back has no control, turning the card from the front drops keyboard focus to the page, with no control on the back to turn it again. <!-- src: plugins/bfb-elements/elements/flip-box.php:411 ; src/elements/flip-box/flip-box.js:193 -->
- **Marked elements turn the card whatever Flip on says.** **Flip on** `trigger` governs hover, click and tap on the card itself, so `none` at a breakpoint stops those and leaves the marked elements working. With `none` and nothing marked, no mouse or finger can turn the card; the page keeps the hidden keyboard fallback alone. <!-- src: src/elements/flip-box/flip-box.js:226 ; src/elements/flip-box/flip-box.js:293 ; plugins/bfb-elements/elements/flip-box.php:418 -->
- **The builder notice reads the base value.** "Add the class bfbe-flip-trigger to an element on each face." shows in the canvas when the base `trigger` is `none`; a breakpoint key such as `trigger:mobile_portrait` set to `none` brings no notice. A breakpoint value applies at and below that breakpoint's width. <!-- src: plugins/bfb-elements/elements/flip-box.php:508 ; docs/elements/flip-box.md "Round 402" -->
- **A marked link stops navigating.** The script cancels a marked link's click so it turns the card instead. Mark a Button or an Icon, and leave links that must go somewhere unmarked. <!-- src: src/elements/flip-box/flip-box.js:229 -->
- **Unmarked interactive content never turns the card by click or tap.** A click on a link, button, input, label, `summary`, media or anything with `tabindex` keeps its own job, and the check climbs past the card to its ancestors. A face, or a Block around the card, with **HTML tag** `tag: "a"` therefore stops click and tap turning it. <!-- src: src/elements/flip-box/flip-box.js:26 ; src/elements/flip-box/flip-box.js:300 -->
- **A trigger without text has no name.** The script gives a marked non-button `role="button"` and no label, so an Icon is announced as an unnamed button. Give it `_attributes` with `aria-label`. <!-- src: src/elements/flip-box/flip-box.js:115 -->
- **The Style tab's border radius does not round the card.** The universal border writes to the root, while the corners a visitor sees are the faces', inherited from **Face border** `faceBorder` on `.bfbe-flip-box__inner`. A face's own `_border` radius overrides that for that face. <!-- src: plugins/bfb-elements/elements/flip-box.php:239 ; src/elements/flip-box/flip-box.css:280 -->
- **Faces clip their content.** Every face has `overflow: hidden`, and Slide over, Push across and Zoom out clip at the inner wrapper too, so a dropdown or tooltip that leaves a face is cut. For those three, the clip copies the front's corners when they are in pixels; a percentage or elliptical corner leaves the card's radius. <!-- src: src/elements/flip-box/flip-box.css:184 ; src/elements/flip-box/flip-box.css:284 ; src/elements/flip-box/flip-box.js:150 -->
- **The canvas holds the card still.** With **Show it** `builderView` at its default, hover does nothing, the turn is instant, both faces stay editable, the fallback never renders, and selecting anything on the back turns the card to it. Set `builderView: "live"` to watch it turn, and check focus and `inert` on the published page. <!-- src: src/elements/flip-box/flip-box.js:73 ; src/elements/flip-box/flip-box.js:313 ; src/elements/flip-box/flip-box.css:119 ; plugins/bfb-elements/elements/flip-box.php:425 -->
- **Minimum height sits on each face.** **Minimum height** `minHeight` writes `min-height` to every face, and the card takes the taller face's height. Without **Match face heights** `equalHeights`, a shorter face keeps its own height, so its background stops short. <!-- src: plugins/bfb-elements/elements/flip-box.php:224 ; src/elements/flip-box/flip-box.css:52 -->
- **A trigger outside the card does nothing.** The script searches inside the card alone and keeps elements whose nearest card is this one, so a marked element beside the card, or in a nested card, never turns it. <!-- src: src/elements/flip-box/flip-box.js:103 -->

## Never do

- Do not give the card more or fewer than two direct children; put extra content inside the back block.
- Do not mark an element on one face alone; mark one on each face, or none.
- Do not set the base `trigger` to `none` unless both faces carry a marked element.
- Do not mark a link that must navigate, and do not set a face's `tag` to `a`.
- Do not mark an Icon or other text-free element without an `aria-label` in its `_attributes`.
- Do not round the card with the flip box's own `_border`; use `faceBorder`.
- Do not target the card or a trigger by `_cssId`, or place a `bfbe-flip-trigger` element outside the card it should turn.
- Do not set `direction` with `effect` `zoom-in`, `zoom-out`, `circle` or `fade`, or `perspective` with any effect but `flip` and `cube`.
