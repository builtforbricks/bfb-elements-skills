---
name: bfbe-image-accordion
description: "Use when placing, wiring or styling BFB Image Accordion (`bfbe-image-accordion`): picture panels side by side, or stacked, that widen on hover, on click or on focus to reveal a caption, and stack on phones. Read before writing its settings."
---

# BFB Image Accordion (`bfbe-image-accordion`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
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

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-image-accordion bfbe-ia bfbe-ia--row bfbe-ia--hover bfbe-ia--reveal bfbe-ia--stack-640"
     data-bfbe-active="1" data-bfbe-from="below" data-bfbe-rest="hidden">
  <div class="brxe-block is-open" tabindex="0">   <!-- a panel: every direct child of the root -->
    <div class="brxe-block">heading, text</div>   <!-- the panel's direct children: what fades and travels -->
  </div>
  <div class="brxe-block" tabindex="0">...</div>
</div>
```

- Root `.bfbe-ia`, a flex `div` whose `block-size` is `--bfbe-ia-h`. Classes: `bfbe-ia--row` or `--column` from `direction`, `--hover` or `--click` from `trigger`, `--reveal` when `contentShows` is `none` at any breakpoint, and `--stack-{480|640|768|992}` with Side by side and `stackBelow` not `never`.
- Attributes, always written: `data-bfbe-active` (**Open at first** `active`, counted from 1, `0` for none), `data-bfbe-from` (**Content comes in** `contentFrom`), `data-bfbe-rest` (`hidden` when the base `contentShows` is `none`, else `shown`).
- Panels are the root's direct children: `flex: 1 1 0`, `overflow: hidden`, corners `var(--bfbe-radius, 12px)`. Each panel's `::after` is the closed tint. A panel's own direct children get `position: relative; z-index: 1` above the tint.
- State: the script puts `is-open` on the panel `data-bfbe-active` names and, in click mode alone, moves it on click. Hover and focus grow a panel in CSS (`:hover`, `:focus-within`) without `is-open`.
- Keyboard parts, from the script: in hover mode a panel holding nothing focusable gets `tabindex="0"`. In click mode such a panel's first heading gets its text moved into `<button type="button" class="bfbe-ia__toggle" aria-expanded>`; a panel with no heading takes `tabindex="0"`, `role="button"` and `aria-expanded` itself.
- Where controls write, as custom properties on the root: `height` `--bfbe-ia-h`, `grow` `--bfbe-ia-grow`, `overlay` `--bfbe-ia-overlay`, `duration` `--bfbe-ia-duration`, `easing` `--bfbe-ease`, `revealDelay` `--bfbe-ia-delay`, `contentShift` `--bfbe-ia-shift`, `contentShows` `--bfbe-ia-rest` and `--bfbe-ia-rest-pe` per breakpoint. `gap` is the root's `gap`; `panelBorder` writes `border` on every panel (`&.bfbe-ia > *`).
- In the builder only: `bfbe-ia--still` (Show it Open or Closed, where hover and focus do nothing), `bfbe-ia--canvas` (Open: equal panels, all content shown), `data-bfbe-live="1"` (Working).

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing.
- Select one accordion in custom CSS by a class in `_cssClasses`, never `_cssId`: component instances share ids, so an id is not unique where the accordion repeats.
- The script runs on load and again on Bricks' AJAX events (`bricks/ajax/popup/loaded`, `bricks/ajax/pagination/completed`, `bricks/ajax/load_page/completed`, `bricks/ajax/query_result/displayed`), so an accordion inside a Bricks popup needs nothing added. Markup inserted any other way is set up by calling `window.bfbeImageAccordion()`.

## Verified patterns

**Picture panels that reveal a caption on hover** (demo page `demo-bfb-image-accordion`, cut from four panels to three). Hover is the default **Expands on**, and `contentShows: "none"` keeps each caption for its open panel. Each caption is one Block, so it arrives as one card. The pictures are the panel Blocks' own `_background`, kept here with the caption's fill. The `id` values 1934, 1937 and 1938 are the demo site's media: use the target site's own attachment ids and URLs. The `https://example.com/...` addresses replace the demo site's.

```json
{
  "name": "bfbe-image-accordion",
  "settings": { "contentShows": "none", "height": "460px", "gap": "12px", "panelBorder": { "radius": { "top": 16, "right": 16, "bottom": 16, "left": 16 } } },
  "children": [
    { "name": "block", "settings": { "_justifyContent": "flex-end", "_padding": { "top": 16, "right": 16, "bottom": 16, "left": 16 },
      "_background": { "image": { "id": 1934, "filename": "bfbe-demo-rye-living-room.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/2026/09/bfbe-demo-rye-living-room-1024x658.jpg", "full": "https://example.com/wp-content/uploads/2026/09/bfbe-demo-rye-living-room.jpg" }, "size": "cover", "position": "center center", "repeat": "no-repeat" } }, "children": [
      { "name": "block", "settings": { "_padding": { "top": "14", "right": "16", "bottom": "14", "left": "16" }, "_background": { "color": { "rgb": "rgba(16, 24, 40, 0.55)" } }, "_border": { "radius": { "top": 10, "right": 10, "bottom": 10, "left": 10 } } }, "children": [
        { "name": "heading", "settings": { "text": "Beckett Road", "tag": "h3", "_typography": { "color": { "hex": "#ffffff" } } } },
        { "name": "text-basic", "settings": { "text": "A rear extension and a kitchen that finally sees the garden.", "tag": "p", "_typography": { "color": { "hex": "#ffffff" } } } }
      ] }
    ] },
    { "name": "block", "settings": { "_justifyContent": "flex-end", "_padding": { "top": 16, "right": 16, "bottom": 16, "left": 16 },
      "_background": { "image": { "id": 1937, "filename": "bfbe-demo-rye-facade.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/2026/09/bfbe-demo-rye-facade-682x1024.jpg", "full": "https://example.com/wp-content/uploads/2026/09/bfbe-demo-rye-facade.jpg" }, "size": "cover", "position": "center center", "repeat": "no-repeat" } }, "children": [
      { "name": "block", "settings": { "_padding": { "top": "14", "right": "16", "bottom": "14", "left": "16" }, "_background": { "color": { "rgb": "rgba(16, 24, 40, 0.55)" } }, "_border": { "radius": { "top": 10, "right": 10, "bottom": 10, "left": 10 } } }, "children": [
        { "name": "heading", "settings": { "text": "The Old Dairy", "tag": "h3", "_typography": { "color": { "hex": "#ffffff" } } } },
        { "name": "text-basic", "settings": { "text": "A barn with one good wall, kept, and a house built behind it.", "tag": "p", "_typography": { "color": { "hex": "#ffffff" } } } }
      ] }
    ] },
    { "name": "block", "settings": { "_justifyContent": "flex-end", "_padding": { "top": 16, "right": 16, "bottom": 16, "left": 16 },
      "_background": { "image": { "id": 1938, "filename": "bfbe-demo-rye-stair.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/2026/09/bfbe-demo-rye-stair-683x1024.jpg", "full": "https://example.com/wp-content/uploads/2026/09/bfbe-demo-rye-stair.jpg" }, "size": "cover", "position": "center center", "repeat": "no-repeat" } }, "children": [
      { "name": "block", "settings": { "_padding": { "top": "14", "right": "16", "bottom": "14", "left": "16" }, "_background": { "color": { "rgb": "rgba(16, 24, 40, 0.55)" } }, "_border": { "radius": { "top": 10, "right": 10, "bottom": 10, "left": 10 } } }, "children": [
        { "name": "heading", "settings": { "text": "Flat 6, Park Hill", "tag": "h3", "_typography": { "color": { "hex": "#ffffff" } } } },
        { "name": "text-basic", "settings": { "text": "Two rooms opened into one, and a stair that stopped being an apology.", "tag": "p", "_typography": { "color": { "hex": "#ffffff" } } } }
      ] }
    ] }
  ]
}
```

**Hidden until open on a desktop, always shown on a phone** (fixture page `fixture-image-accordion`, its first accordion). `contentShows: "none"` at the base and `"auto"` at `mobile_landscape`, Bricks' default phone breakpoint key; a site with its own breakpoints uses its own key. `stackBelow: "768"` stacks the panels at about the same width, so a phone shows every panel's words without a hover. The fixture's probe class is left out.

```json
{
  "name": "bfbe-image-accordion",
  "settings": { "contentShows": "none", "contentShows:mobile_landscape": "auto", "stackBelow": "768" },
  "children": [
    { "name": "block", "settings": { "_background": { "color": { "hex": "#334155" } }, "_padding": { "top": "32", "right": "24", "bottom": "32", "left": "24" } }, "children": [
      { "name": "heading", "settings": { "text": "Desk", "tag": "h3" } },
      { "name": "text-basic", "settings": { "text": "Hidden until open on a desktop." } }
    ] },
    { "name": "block", "settings": { "_background": { "color": { "hex": "#0f766e" } }, "_padding": { "top": "32", "right": "24", "bottom": "32", "left": "24" } }, "children": [
      { "name": "heading", "settings": { "text": "Phone", "tag": "h3" } },
      { "name": "text-basic", "settings": { "text": "Always there on a phone." } }
    ] },
    { "name": "block", "settings": { "_background": { "color": { "hex": "#7c3aed" } }, "_padding": { "top": "32", "right": "24", "bottom": "32", "left": "24" } }, "children": [
      { "name": "heading", "settings": { "text": "Both", "tag": "h3" } },
      { "name": "text-basic", "settings": { "text": "A line." } }
    ] }
  ]
}
```

**Stacked click accordion, all closed at first** (fixture page `fixture-image-accordion`, the stacked click case). `direction: "column"` stacks at every width, `trigger: "click"` opens one panel per click and a second click closes it, and `active: 0` opens none on load. Each heading becomes its panel's button.

```json
{
  "name": "bfbe-image-accordion",
  "settings": { "trigger": "click", "direction": "column", "active": 0, "height": "300px", "contentShows": "none" },
  "children": [
    { "name": "block", "settings": { "_background": { "color": { "hex": "#1e3a8a" } }, "_padding": { "top": "32", "right": "24", "bottom": "32", "left": "24" } }, "children": [
      { "name": "heading", "settings": { "text": "Alpha", "tag": "h3" } },
      { "name": "text-basic", "settings": { "text": "Click me." } }
    ] },
    { "name": "block", "settings": { "_background": { "color": { "hex": "#065f46" } }, "_padding": { "top": "32", "right": "24", "bottom": "32", "left": "24" } }, "children": [
      { "name": "heading", "settings": { "text": "Beta", "tag": "h3" } },
      { "name": "text-basic", "settings": { "text": "Click me." } }
    ] },
    { "name": "block", "settings": { "_background": { "color": { "hex": "#7f1d1d" } }, "_padding": { "top": "32", "right": "24", "bottom": "32", "left": "24" } }, "children": [
      { "name": "heading", "settings": { "text": "Gamma", "tag": "h3" } },
      { "name": "text-basic", "settings": { "text": "Click me." } }
    ] }
  ]
}
```

## Gotchas

- **Every direct child is a panel, and its direct children are what reveals.** Each child of a panel fades and travels on its own, so wrap a caption in one Block to have it arrive as one card, as the demo does. <!-- src: src/elements/image-accordion/image-accordion.css:42 ; src/elements/image-accordion/image-accordion.css:71 -->
- **Content shows defaults to Always.** Until `contentShows` is `none` somewhere, closed panels show their content, and **Content comes in**, **Travel distance** and **Content delay** have nothing to animate: content shown at rest has no travel left. <!-- src: src/elements/image-accordion/image-accordion.css:29 ; src/elements/image-accordion/image-accordion.css:32 ; plugins/bfb-elements-pro/elements/image-accordion.php:338 -->
- **In hover mode the panel open at first stays open.** `is-open` is set once from `active`, and only click mode moves it, so hovering another panel opens a second one beside it. Set `active: 0` when only the hovered panel should grow. <!-- src: src/elements/image-accordion/image-accordion.js:38 ; src/elements/image-accordion/image-accordion.css:51 ; src/elements/image-accordion/image-accordion.css:97 ; measured 2026-10-08 on fixture-image-accordion, four hover panels at 1280: 380/159/380/159 with the third hovered -->
- **Open panel size multiplies the free space, not the panel.** Panels start from a flex basis of zero but never shrink below their own padding, so `grow` shares out only what is left after padding. With 32px padding in a 300px stacked accordion, the open panel measured 119px against 82px. <!-- src: src/elements/image-accordion/image-accordion.css:44 ; src/elements/image-accordion/image-accordion.css:51 ; measured 2026-10-08 on fixture-image-accordion, the stacked click case -->
- **Stack below reads the window, not the element.** It is a media query on the viewport, so an accordion in a narrow column stays side by side on a wide screen. At or below the width each panel is half the Height and none grows; opening changes only the content and the tint. <!-- src: src/elements/image-accordion/image-accordion.css:4 ; src/elements/image-accordion/image-accordion.css:106 ; measured 2026-10-08 at 600px: 210/210/210 before and during a hover -->
- **Stack below acts on Side by side alone.** `direction: "column"` stacks at every width and keeps growing the open panel; the builder hides `stackBelow` there. <!-- src: plugins/bfb-elements-pro/elements/image-accordion.php:132 ; plugins/bfb-elements-pro/elements/image-accordion.php:349 -->
- **Panels have a fixed height and clip.** The root is **Height** tall (420px unless set) and every panel has `overflow: hidden`, so content taller than a panel, or wider than a closed one, is cut. <!-- src: src/elements/image-accordion/image-accordion.css:37 ; src/elements/image-accordion/image-accordion.css:47 -->
- **The picture is the panel's, the tint is the accordion's.** Put each image in its panel Block's `_background`. **Closed overlay** `overlay` tints closed panels and lifts as one opens; it is transparent until set. <!-- src: plugins/bfb-elements-pro/elements/image-accordion.php:186 ; src/elements/image-accordion/image-accordion.css:56 ; src/elements/image-accordion/image-accordion.css:58 -->
- **Round the panels with Panel border.** `panelBorder` writes to every panel. The accordion's own `_border` lands on the root, which clips nothing, so it draws one frame round the set and leaves the pictures' corners alone. <!-- src: plugins/bfb-elements-pro/elements/image-accordion.php:183 ; src/elements/image-accordion/image-accordion.css:48 -->
- **Duration does not time the content.** `duration` times the panels' growth and the tint; the content's fade and travel run at the pack's `--bfbe-duration` (200ms) after the Content delay. That delay, unset, is two fifths of `duration` and follows it. <!-- src: src/elements/image-accordion/image-accordion.css:19 ; src/elements/image-accordion/image-accordion.css:71 ; plugins/bfb-elements/includes/class-assets.php:81 -->
- **A panel holding its own link or button is not made a toggle.** In click mode such a panel gets no button and no role: a click on that link follows it, a click elsewhere in the panel toggles, and the keyboard opens it by focus. <!-- src: src/elements/image-accordion/image-accordion.js:51 ; src/elements/image-accordion/image-accordion.js:86 ; docs/elements/image-accordion.md "Show it did nothing, and a click never opened a panel" -->
- **Show it changes the canvas only.** `builderView` never reaches the page. Open, the default, shows equal panels with all content and nothing answering the pointer, so check hover and click on the published page, or set `builderView: "live"`. <!-- src: plugins/bfb-elements-pro/elements/image-accordion.php:352 ; src/elements/image-accordion/image-accordion.js:38 ; src/elements/image-accordion/image-accordion.css:113 -->

## Never do

- Do not put anything directly inside the accordion that is not a panel; every direct child becomes one.
- Do not leave `active` at its default on a hover accordion where only the hovered panel should open; set `active: 0`.
- Do not set `stackBelow` with `direction: "column"`, or expect it to follow the element's own width.
- Do not put the panel pictures on the accordion root; give each panel Block its own `_background`.
- Do not round the panels with the accordion's `_border`; use `panelBorder`.
- Do not judge hover or click in the canvas under Show it Open or Closed; check the published page.
- Do not target an accordion by `_cssId`; use a class in `_cssClasses`.
