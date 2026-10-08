---
name: bfbe-marquee
description: "Use when building a scrolling logo strip, ticker or endless row of words or images with BFB Marquee (`bfbe-marquee`): any elements scrolled continuously, sideways or upward, at a speed in pixels per second, with an optional pause button. Read before writing its settings."
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

## Rendered DOM

The root is `div.bfbe-marquee` (Bricks adds `brxe-bfbe-marquee` and `#brxe-<id>`) with `data-bfbe-speed`, which the script reads. The motion is one CSS animation on `.bfbe-marquee__track`; the groups inside it never animate.

```html
<div class="bfbe-marquee bfbe-marquee--horizontal bfbe-marquee--pause-hover is-ready" data-bfbe-speed="60"
     style="--bfbe-mq-shift: 255px; --bfbe-mq-duration: 4.25s">
  <!-- only with pauseButton -->
  <button type="button" class="bfbe-marquee__pause bfbe-marquee__pause--top-right" data-bfbe-pause="Pause" data-bfbe-play="Play">
    <svg class="bfbe-marquee__ico bfbe-marquee__ico--pause"></svg><svg class="bfbe-marquee__ico bfbe-marquee__ico--play"></svg>
    <span class="bfbe-sr">Pause</span>
  </button>
  <div class="bfbe-marquee__viewport">
    <div class="bfbe-marquee__track">
      <div class="bfbe-marquee__group"><!-- the children, each one item --></div>
      <div class="bfbe-marquee__group" aria-hidden="true" inert><!-- a copy, made by the script --></div>
    </div>
  </div>
</div>
```

- Root modifiers: `--horizontal` or `--vertical` always; `--reverse` with `reverse`; `--pause-hover` unless `pauseOnHover` is `"keep"`; `--fade` with `fade`.
- `is-ready` is added by the script after it measures the group and makes the copies (no copies under reduced motion). Without it the animation is off and the viewport scrolls by hand.
- `is-paused` is toggled by the pause button, which swaps its `.bfbe-sr` text between `data-bfbe-pause` and `data-bfbe-play`. There is no `aria-pressed`.
- The script writes `--bfbe-mq-shift` (one group plus the gap, in px) and `--bfbe-mq-duration` (shift divided by speed) inline on the root, and measures again on resize.
- Pausing is `animation-play-state: paused` on the track, from `.bfbe-marquee--pause-hover:hover`, `.bfbe-marquee__viewport:focus-within` and `.is-paused`.
- Where controls write: `gap`, `height`, `fadeSize`, `pauseSize` and `pauseOffset` set `--bfbe-mq-gap`, `--bfbe-mq-height`, `--bfbe-mq-fade`, `--bfbe-mq-btn` and `--bfbe-mq-btn-offset` on the root. `stripBorder` writes to `.bfbe-marquee__viewport`, `itemAlign` writes `align-items` to `.bfbe-marquee__group`.
- The pause colour, background, border and shadow write to `.bfbe-marquee__pause`; `pauseHoverBackground` writes to its `:hover` and `:focus-visible`.
- The fade is a `mask-image` on the viewport: left and right, or top and bottom when vertical.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing. What matters is what goes inside it:

- The copies keep every class and id of the items. A script that selects by class matches the copies as well; `document.getElementById()` returns the original, which comes first.
- To style or target an item, give it a class in `_cssClasses`, never an `_cssId`: an id is repeated in every copy on the page, and component instances share ids too.
- The copies are removed and made again whenever the strip or its first group changes size, so anything another script attaches to a copy does not last.
- The script starts every `.bfbe-marquee` on load and again after Bricks' AJAX pagination, AJAX page loads, query results and popup loads, so a strip inside a Bricks popup starts on its own. A strip your own script adds needs `window.bfbeMarquee()` called once it is in the DOM.

## Verified patterns

**A row of words, edges faded.** From the demo page "ZZ demo: Marquee" (`demo-bfb-marquee`), trimmed to three items and without the bean icons between them. Each item is a Block laid out as a row with `_width: "auto"`, which keeps it to its content. `speed: 40` reads as slow; the fade hides where items enter and leave.

```json
{
  "name": "bfbe-marquee",
  "settings": { "gap": "40px", "speed": 40, "pauseOnHover": "pause", "fade": true },
  "children": [
    { "name": "block", "settings": { "_direction": "row", "_alignItems": "center", "_columnGap": "14px", "_width": "auto" }, "children": [
      { "name": "text-basic", "settings": { "text": "Ethiopia Guji", "tag": "p" } },
      { "name": "text-basic", "settings": { "text": "peach and jasmine", "tag": "p" } }
    ] },
    { "name": "block", "settings": { "_direction": "row", "_alignItems": "center", "_columnGap": "14px", "_width": "auto" }, "children": [
      { "name": "text-basic", "settings": { "text": "Colombia Huila", "tag": "p" } },
      { "name": "text-basic", "settings": { "text": "red apple", "tag": "p" } }
    ] },
    { "name": "block", "settings": { "_direction": "row", "_alignItems": "center", "_columnGap": "14px", "_width": "auto" }, "children": [
      { "name": "text-basic", "settings": { "text": "Kenya Nyeri", "tag": "p" } },
      { "name": "text-basic", "settings": { "text": "blackcurrant", "tag": "p" } }
    ] }
  ]
}
```

**Photographs running the other way.** From the same demo page, trimmed to three images. `reverse: true` runs it rightward, and every image is sized with `_width: "320px"` and a 4:3 crop. The `image` ids are the demo site's media; use the target site's own.

```json
{
  "name": "bfbe-marquee",
  "settings": { "gap": "20px", "speed": 28, "reverse": true, "pauseOnHover": "pause", "fade": true },
  "children": [
    { "name": "image", "settings": { "image": { "id": 7497, "size": "large" }, "_width": "320px", "_aspectRatio": "4/3", "_objectFit": "cover" } },
    { "name": "image", "settings": { "image": { "id": 3409, "size": "large" }, "_width": "320px", "_aspectRatio": "4/3", "_objectFit": "cover" } },
    { "name": "image", "settings": { "image": { "id": 3379, "size": "large" }, "_width": "320px", "_aspectRatio": "4/3", "_objectFit": "cover" } }
  ]
}
```

**A vertical strip with a pause button.** From the fixture page "FREE: Marquee" (`fixture-marquee`). `orientation: "vertical"` with `height` gives a 200px window scrolling upward; `pauseButton` adds the button and `pausePosition` puts it bottom left. The fixture's link is there to prove that keyboard focus pauses the strip.

```json
{
  "name": "bfbe-marquee",
  "settings": { "orientation": "vertical", "height": "200px", "pauseOnHover": "pause", "pauseButton": true, "pausePosition": "bottom-left" },
  "children": [
    { "name": "text-basic", "settings": { "text": "Line one" } },
    { "name": "text-basic", "settings": { "text": "<a href=\"#x\">A link</a>" } },
    { "name": "text-basic", "settings": { "text": "Line three" } }
  ]
}
```

## Gotchas

- **The pause button is off until ticked.** **Show pause button** (`pauseButton`) is a checkbox and arrives unticked; `pausePosition` and the seven pause styling controls are hidden and do nothing without it. <!-- src: plugins/bfb-elements/elements/marquee.php:112-133, 202-277; docs/elements/marquee.md "Corrected, then fixed" -->
- **Only `"keep"` stops the pointer pause.** **Under the pointer** (`pauseOnHover`) is a select; any other value, `true` and `false` included, falls back to Pauses. Keyboard focus inside the viewport pauses the strip in every case. <!-- src: plugins/bfb-elements/elements/marquee.php:96-97, 310; plugins/bfb-elements/includes/abstract-element.php:1369; src/elements/marquee/marquee.css:60-64 -->
- **Links in the copies do not respond.** The copies are `inert` and `aria-hidden`, so their links and buttons take no click and no focus; only the first group's items act. Measured on the fixture: a click on a copy's link lands on the track. <!-- src: src/elements/marquee/marquee.js:57-72; measured headless on fixture-marquee 2026-10-08 -->
- **Items keep their natural width.** Every item is `flex: none`. A Bricks Block keeps its `width: 100%`, takes the whole group's width and overlaps the next, and an image with no width shows at its file's width (1024px at size large). Set `_width` on each item. <!-- src: src/elements/marquee/marquee.css:41; Bricks frontend CSS .brxe-block width:100%; measured headless on fixture-marquee 2026-10-08 -->
- **Height and Fade size need their switches.** **Height** (`height`, 300px when empty) is offered only with `orientation: "vertical"`; a horizontal strip is as tall as its tallest item. **Fade size** (`fadeSize`) is offered only with `fade`. <!-- src: plugins/bfb-elements/elements/marquee.php:148-158, 179-189; src/elements/marquee/marquee.css:52 -->
- **Rounded corners come from Strip border.** The viewport clips the items, so a radius from Bricks' own Border on the element leaves the items square at the corners. Set the radius in `stripBorder`. <!-- src: plugins/bfb-elements/elements/marquee.php:160-170; src/elements/marquee/marquee.css:18-24 -->
- **A pause background freezes the hover.** `pauseBackground` outranks the stylesheet's hover rule, so the button shows no hover or focus change unless `pauseHoverBackground` is set too. <!-- src: plugins/bfb-elements/elements/marquee.php:244-259 -->
- **The canvas shows a still strip.** In the builder the script makes no copies and never adds `is-ready`, so the strip sits still and scrolls by hand. Judge the motion on the page. <!-- src: src/elements/marquee/marquee.js:47-49; src/elements/marquee/marquee.css:101-103 -->
- **Reduced motion gives a still, scrollable row.** With reduced motion requested the track stops, the copies, the pause button and the fade are gone, and the viewport scrolls. Without the script the strip is the same still row. <!-- src: src/elements/marquee/marquee.css:101-109; src/elements/marquee/marquee.js:51 -->
- **Speed is pixels per second, not a duration.** The duration is worked out from the measured group, so the pace holds whatever the strip holds. Zero, a negative number or no value falls back to 60. <!-- src: plugins/bfb-elements/elements/marquee.php:299-300; src/elements/marquee/marquee.js:40-45 -->
- **A right-to-left page runs it rightward.** A horizontal strip on a `dir="rtl"` page travels the other way so it never scrolls off its own start; `reverse` still flips it. <!-- src: src/elements/marquee/marquee.css:47-49, 57 -->

## Never do

- Do not write `pauseOnHover` as `true` or `false`; write `"pause"` or `"keep"`.
- Do not set `pausePosition` or any pause styling key without `pauseButton: true`.
- Do not set `height` without `orientation: "vertical"`, or `fadeSize` without `fade: true`.
- Do not leave a Block or an image in the strip without a `_width`.
- Do not fill the strip with links or buttons visitors must reach; only the first copy of each responds.
- Do not round the strip with Bricks' own Border on the element; use `stripBorder`.
- Do not set `pauseBackground` without `pauseHoverBackground`.
- Do not target an item by `_cssId`; use `_cssClasses`.
