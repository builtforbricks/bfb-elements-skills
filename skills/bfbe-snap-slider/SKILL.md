---
name: bfbe-snap-slider
description: "Use when placing, wiring or styling BFB Advanced Snap Slider (`bfbe-snap-slider`): a row of Snap Slide children in a native scroll container with scroll snapping, so the browser scrolls and the stylesheet snaps, with no slider library. Read before writing its settings."
---

# BFB Advanced Snap Slider (`bfbe-snap-slider`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
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
- `dots` (checkbox) **Show them**. Under the Dots heading, tick it to add a row of dots, one per slide. A press on a dot moves the row to its slide.
- `dotsPosition` (select) **Position**: options: `below` Below the slides (default), `above` Above the slides; only when `dots` is set. Below the slides, the default, or Above the slides. On the same side as the buttons, the dots join the button row.
- `progress` (checkbox) **Show it**: only when `dots` is not set. Under the Progress bar heading, offered while the dots are off, tick it to add a bar that fills as the row scrolls.
- `barPosition` (select) **Position**: options: `below` Below the slides (default), `above` Above the slides; only when `progress` is set and `dots` is not set. Below the slides, the default, or Above the slides. On the same side as the buttons, the dots join the button row.
Styling, in the schema file: `dotsSpacing`, `dotsAlign`, `dotSize`, `dotActiveWidth`, `dotGap`, `dotColor`, `dotActiveColor`, `dotBorder`, `dotDim`, `dotHover`, `barSpacing`, `barHeight`, `barTrack`, `barFill`.

### Scrolling (`bfbeMotion`)
- `drag` (checkbox) **Mouse drag**. Tick it to let a mouse drag the row. It is off by default. Touch and keyboard scrolling work either way.
- `autoplay` (checkbox) **Autoplay**. Tick it to move the row on by one slide at a time. At the end the row rewinds to the start.
- `interval` (number) **Seconds per slide**: only when `autoplay` is set. How long autoplay waits on each slide, 4 by default and never under 1.
- `scrollEasing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. The curve those timed moves follow, Snappy unless set.
Styling, in the schema file: `scrollDuration`, `scrollEasingCustom`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Still, so you can style it (default), `live` Working, as on the site. Still, the default, holds the row so you can style it. Working lets it drag and play in the canvas.

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

## Rendered DOM

On the page, with arrows, a counter and dots below:

```html
<div class="bfbe-ss bfbe-ss--arrows bfbe-ss--pattern is-start" data-bfbe-ss="bfbe-<uid>" data-bfbe-bleed="both"
     data-bfbe-nav="above" data-bfbe-fade="0" data-bfbe-drag="1" data-bfbe-move="1" data-bfbe-dot="Slide">
  <style>/* the Width pattern: one rule per row and breakpoint */</style>
  <a class="bfbe-ss__skip" href="#bfbe-<uid>-end">Skip the slides</a>
  <div class="bfbe-ss__bar">
    <button type="button" class="bfbe-ss__btn bfbe-ss__btn--prev bfbe-chip bfbe-ss__btn--icon" data-bfbe-dir="-1">
      <svg class="bfbe-ss__icon bfbe-ss__arrow">…</svg><span class="bfbe-sr">Previous</span></button>
    <span class="bfbe-ss__count" aria-hidden="true">2 / 6</span>
    <button type="button" class="bfbe-ss__btn bfbe-ss__btn--next bfbe-chip bfbe-ss__btn--icon" data-bfbe-dir="1">…</button>
  </div>
  <div class="bfbe-ss__stage">
    <ul class="bfbe-ss__list" aria-label="Slides" tabindex="0">
      <li id="brxe-<slide id>" class="brxe-bfbe-snap-slide bfbe-ss__slide">…</li>
    </ul>
  </div>
  <div class="bfbe-ss__dots" role="group" aria-label="Choose a slide">
    <button type="button" class="bfbe-ss__dot is-active" aria-label="Slide 1" aria-current="true"></button>…
  </div>
  <span class="bfbe-ss__end" id="bfbe-<uid>-end" tabindex="-1"></span>
</div>
```

- `.bfbe-ss__bar` comes before the stage for `navPosition: "above"`, after it for `"below"`, and inside `.bfbe-ss__stage` after the list for `"sides"`. The dots, or the progress bar `.bfbe-ss__progress > .bfbe-ss__fill`, join the bar when they sit on the buttons' side; otherwise they are a row of their own.
- A typed `prevLabel` or `nextLabel` becomes `<span class="bfbe-ss__label">` and the button loses `bfbe-ss__btn--icon`. A chosen `prevIcon` or `nextIcon` replaces the drawn arrow and keeps the class `bfbe-ss__icon`.
- Variants are attributes: `data-bfbe-bleed` (none, both, end), `data-bfbe-nav` (above, below, sides) and `data-bfbe-fade` (0, 1) are always present; `data-bfbe-nav-hover="1"`, `data-bfbe-drag="1"` and `data-bfbe-autoplay` (milliseconds) only when on. `bfbe-ss--arrows` and `bfbe-ss--pattern` mark arrows and a pattern.
- The script builds the dots and the count, toggles `is-start`, `is-end`, `is-fits` (nothing to scroll, page only) and `is-dragging` on the root, sets `aria-disabled` on the buttons at the ends, and keeps `--bfbe-ss-p` (0 to 1, the bar's fill) on the root.
- Where controls write: most styling controls are custom properties on the root (`--bfbe-ss-gap`, `--bfbe-ss-btn-bg`, `--bfbe-ss-dot-on`). `btnPadding` and `btnBorder` write `.bfbe-ss__btn`, `dotBorder` `.bfbe-ss__dot`, `counterTypography` `.bfbe-ss__count`, `barAlign` `.bfbe-ss__bar`, `patternUse` the slides. A Snap Slide's own `width` and `align` are `--bfbe-ss-w` and `--bfbe-ss-align` on its `li`.
- In the builder canvas the list and the slides are `div`s with the same classes; the still view adds `bfbe-ss--canvas`, the working view `data-bfbe-live="1"`.

## Wiring to other elements

Stands alone among other elements: nothing in the pack targets it and it targets nothing. Its wiring is its own children.

- The tree is `bfbe-snap-slider` > `bfbe-snap-slide` > any elements. Schema: `../bfbe-schemas/references/elements/bfbe-snap-slide.json`.
- **Snap Slide** settings that decide a build: **Width** `width` wins over every width on the slider; **Snap to** `align` takes `start`, `center` or `end`; **Place** `place` (`order`, `after`, `every`) with **After item** `after`, **Repeat every** `every` and **Max repeats** `limit`; `hasLoop` with `query` repeats the slide once per item. Its Style tab carries Bricks' Direction, Wrap and gaps once `_display` is `flex`.
- **Slider Controls does not drive this slider.** `bfbe-slider-controls` finds Bricks' Slider (Nestable), `.splide`, by its **Slider element ID** `target` or the nearest ancestor holding one, and never matches `.bfbe-ss`. Use this element's own `arrows`, `counter`, `dots` or `progress`.
- For custom CSS or a script, add a class in `_cssClasses` and select it with `.bfbe-ss`, never `_cssId`: component instances share ids, and inside a query loop Bricks moves the id into a class.
- `window.bfbeSnapSlider()` initialises every slider on the page again. It already runs on load and after Bricks' AJAX pagination, page loads, query results and popups; call it after your own script inserts a slider.

## Verified patterns

Cards in a narrow, narrow, wide rhythm, from the fixture page `fixture-snap-slider` (four of its six slides, card wrappers and numbering left out). Each `pattern` row carries its own `width:tablet_portrait`; `patternUse:mobile_portrait: "initial"` turns the pattern off on phones so `slideWidth:mobile_portrait` applies, and `className` adds `is-wide` to every third slide on the page.

```json
{"name": "bfbe-snap-slider", "settings": {
  "label": "Meet the new standard", "bleed": "both", "gap": "16px", "arrows": true, "counter": true, "drag": true,
  "pattern": [
    {"width": "520px", "width:tablet_portrait": "400px"},
    {"width": "520px", "width:tablet_portrait": "400px"},
    {"width": "860px", "width:tablet_portrait": "640px", "className": "is-wide"}
  ],
  "patternUse:mobile_portrait": "initial", "slideWidth:mobile_portrait": "85%"
}, "children": [
  {"name": "bfbe-snap-slide", "settings": {}, "children": [{"name": "heading", "settings": {"text": "A platform that keeps up", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Everything updates live."}}]},
  {"name": "bfbe-snap-slide", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Made for you", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Rearrange panels, save studios."}}]},
  {"name": "bfbe-snap-slide", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Photo editing", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Wide card from the pattern."}}]},
  {"name": "bfbe-snap-slide", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Vector design", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Back to a narrow one."}}]}
]}
```

A query loop with a static intro and promo slides placed among its items, from `fixture-snap-slider` (slide contents shortened). The intro stays first because positions count loop items; `after: 2` lands after the second item, and `every: 3` with `limit: 2` repeats after items 3 and 6. Swap `post_type` for the feed you want.

```json
{"name": "bfbe-snap-slider", "settings": {
  "label": "Pages", "bleed": "end", "slideWidth": "280px",
  "arrows": true, "prevLabel": "Previous", "nextLabel": "Next", "navPosition": "below", "barAlign": "flex-end", "counter": true
}, "children": [
  {"name": "bfbe-snap-slide", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Intro, stays first", "tag": "h3"}}]},
  {"name": "bfbe-snap-slide", "settings": {"hasLoop": true, "query": {"post_type": ["page"], "posts_per_page": 7, "orderby": "title", "order": "ASC"}}, "children": [
    {"name": "heading", "settings": {"text": "{post_title}", "tag": "h4"}}
  ]},
  {"name": "bfbe-snap-slide", "settings": {"place": "after", "after": 2, "width": "360px"}, "children": [{"name": "heading", "settings": {"text": "After item 2", "tag": "h3"}}]},
  {"name": "bfbe-snap-slide", "settings": {"place": "every", "every": 3, "limit": 2}, "children": [{"name": "heading", "settings": {"text": "Every 3, twice", "tag": "h3"}}]}
]}
```

A centred row with a peek of its neighbours, autoplaying, with arrows over the slides that appear on hover, from `fixture-snap-slider` (slide contents shortened). `perView: 1.15` sizes every slide, `align: "center"` snaps their centres, and `fade` softens an edge while there is more to see past it.

```json
{"name": "bfbe-snap-slider", "settings": {
  "perView": 1.15, "align": "center", "fade": true,
  "arrows": true, "navPosition": "sides", "navHover": true, "autoplay": true, "interval": 3
}, "children": [
  {"name": "bfbe-snap-slide", "settings": {}, "children": [{"name": "heading", "settings": {"text": "One", "tag": "h3"}}]},
  {"name": "bfbe-snap-slide", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Two", "tag": "h3"}}]},
  {"name": "bfbe-snap-slide", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Three", "tag": "h3"}}]},
  {"name": "bfbe-snap-slide", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Four", "tag": "h3"}}]}
]}
```

## Gotchas

- **Switches are off until set, and one value for every breakpoint.** `arrows`, `counter`, `dots`, `progress`, `drag` and `autoplay` carry no default, so a slider made through MCP moves by touch, wheel and keys alone. These, `bleed`, `fade`, `navPosition` and `navHover` ignore breakpoint suffixes; only controls that write CSS take one. <!-- src: plugins/bfb-elements-pro/elements/snap-slider.php:262-273, plugins/bfb-elements-pro/elements/snap-slider.php:833-889, docs/API-PROBE.md "12. Control defaults exist only in the builder", docs/REMAINING-WORK.md "Advanced Snap Slider + Snap Slide" -->
- **Only Snap Slides go directly in the slider.** Anything else lands in the `<ul>` as a non-list item, takes a slide's width and a dot, and the width pattern skips it. A Snap Slide anywhere else renders a stray `<li>`; the canvas marks it. <!-- src: src/elements/snap-slider/snap-slider.css:68-76, src/elements/snap-slider/snap-slider.js:77-86, plugins/bfb-elements-pro/elements/snap-slider.php:1035-1036, plugins/bfb-elements-pro/elements/snap-slide.php:125-129 -->
- **Widths resolve in one order.** A slide's own `width` wins, then the pattern row while `patternUse` is Yes, then **Slides in view** `perView`, then **Slide width** `slideWidth`. So `slideWidth:mobile_landscape` does nothing while a pattern applies until `patternUse:mobile_landscape` is `"initial"`. <!-- src: src/elements/snap-slider/snap-slider.css:67-76; measured on demo-bfb-snap-slider at 700px: --bfbe-ss-fixed reads 78%, slides read 360 and 660 from the pattern -->
- **A pattern row's breakpoint widths live inside the row.** Write `"width:tablet_portrait": "400px"` in the row object. The element writes its own `:nth-child(… of .bfbe-ss__slide)` rules from the rows, so the pattern counts Snap Slides alone. <!-- src: plugins/bfb-elements-pro/elements/snap-slider.php:1032-1091, docs/elements/snap-slider.md "Round 402" -->
- **No slide height control.** The list is a flex row, so every slide stretches to the tallest one and one tall image sets the height for all. Give images a fixed height or aspect ratio, or a height on each slide. <!-- src: src/elements/snap-slider/snap-slider.css:47-49, docs/REMAINING-WORK.md "Snap Slider: a slide-height control. PARKED" -->
- **The canvas is not the page.** It shows Snap Slides in structure order without the pattern's `className`, and in the default still view of **Show it** `builderView` the row never snaps and keys, drag and autoplay are off. Placed slides and pattern classes appear on the page and in the preview; `builderView: "live"` brings snapping, keys, drag and autoplay to the canvas. <!-- src: plugins/bfb-elements-pro/elements/snap-slider.php:11-13, plugins/bfb-elements-pro/elements/snap-slider.php:1101-1104, src/elements/snap-slider/snap-slider.css:174-182, src/elements/snap-slider/snap-slider.js:55-57, docs/elements/snap-slider.md "In the builder canvas" -->
- **Positions count loop items.** When an in-order slide has `hasLoop`, only its items count, so a static intro never shifts `after`; with no loop every in-order slide counts. `after: 0` puts a slide first, a number past the end puts it after the last item, `limit: 0` repeats without limit, and `place: "every"` on a slide that loops hands out one item per stop. <!-- src: plugins/bfb-elements-pro/elements/snap-slider.php:1137-1187, plugins/bfb-elements-pro/elements/snap-slide.php:59-92 -->
- **A repeated slide repeats its ids.** Each copy made by `place: "every"` keeps the slide's `brxe-` ids so its Bricks styling reaches every copy. An HTML validator flags the duplicates, and a link or script by id finds the first copy. <!-- src: docs/elements/snap-slider.md "Round 453", plugins/bfb-elements-pro/elements/snap-slider.php:1189-1200 -->
- **Dots replace the progress bar.** `progress` and its five controls are offered while `dots` is off; with both saved, the dots are drawn and the bar is not. <!-- src: plugins/bfb-elements-pro/elements/snap-slider.php:539-540, plugins/bfb-elements-pro/elements/snap-slider.php:842-843, docs/elements/snap-slider.md "round 350" -->
- **The controls hide when nothing scrolls.** On the page a row whose slides all fit gets `is-fits`, which hides the bar, the dots, the progress bar and the fades; the canvas always shows them. <!-- src: src/elements/snap-slider/snap-slider.js:145-147, src/elements/snap-slider/snap-slider.css:96, src/elements/snap-slider/snap-slider.css:111, src/elements/snap-slider/snap-slider.css:158 -->
- **Full bleed runs to the window's edges, inside any clipping parent.** `bleed: "both"` or `"end"` extends the row to the viewport while the first slide stays in line with the content; a parent that clips its overflow clips the run-off. **Start inset** `inset` pads both ends of the row, not the start alone. <!-- src: src/elements/snap-slider/snap-slider.css:24-30, src/elements/snap-slider/snap-slider.css:43-60, src/elements/snap-slider/snap-slider.js:68-75, docs/elements/snap-slider.md "In the builder canvas" -->
- **Easing needs a duration.** **Easing** `scrollEasing` is read only while **Scroll duration (ms)** `scrollDuration` is above 0; at the default 0, buttons, keys and autoplay use the browser's smooth scroll. A drag, wheel or swipe is always the browser's. <!-- src: src/elements/snap-slider/snap-slider.js:9-23, docs/elements/snap-slider.md "Under Scrolling" -->

## Never do

- Do not put anything but a `bfbe-snap-slide` directly in a `bfbe-snap-slider`, or a `bfbe-snap-slide` anywhere else.
- Do not place a `bfbe-slider-controls` to drive this slider; set `arrows`, `counter`, `dots` or `progress` on it.
- Do not write a breakpoint suffix on `arrows`, `counter`, `dots`, `progress`, `drag`, `autoplay`, `bleed`, `fade`, `navPosition` or `navHover`.
- Do not set `slideWidth` or `perView` at a breakpoint where a pattern applies without `patternUse` set to `"initial"` there.
- Do not set a dot control without `dots: true`, or a progress-bar control while `dots` is on.
- Do not set `scrollEasing` without a `scrollDuration` above 0.
- Do not target the slider or a slide by `_cssId`; use a class in `_cssClasses`.
- Do not name or focus the list any way but **Name** `label`: no `tabindex`, `role` or `aria-label` on `.bfbe-ss__list` or the slides.
