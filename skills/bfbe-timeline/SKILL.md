---
name: bfbe-timeline
description: "Use when building a company history, milestones, a roadmap or a year-by-year story with BFB Content Timeline (`bfbe-timeline`) and its Timeline Moments: a line that fills as the page scrolls, year tabs that switch one moment, or a sticky chapter list. Read before writing its settings."
---

# BFB Content Timeline (`bfbe-timeline`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-timeline.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/timeline/

## What it is
One set of moments in five layouts: Story and Ledger draw a line that fills as the page scrolls. Years and Journey show the moment chosen from a list of labels, and Chapters keeps a sticky list of labels beside every moment. Each Timeline Moment is a container you fill with any elements, and moments can share a label or repeat from a query loop.

**Not for:** Moments sit in the order you place them, so it does not space them by date or zoom along a time axis. Story and Ledger follow the window's scroll, so inside a box that scrolls on its own the line will not advance.

**Costs a page:** CSS 2.97 KB, JS 2.91 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable. Its own children: `bfbe-timeline-item`.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-timeline",
    "settings": {},
    "children": [
        {
            "name": "bfbe-timeline-item",
            "settings": {
                "label": "2022"
            },
            "children": [
                {
                    "name": "block",
                    "settings": {},
                    "children": [
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "2022"
                            }
                        },
                        {
                            "name": "heading",
                            "settings": {
                                "text": "A moment",
                                "tag": "h3"
                            }
                        },
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "What happened, and why it mattered."
                            }
                        }
                    ]
                },
                {
                    "name": "image",
                    "settings": {}
                }
            ]
        },
        {
            "name": "bfbe-timeline-item",
            "settings": {
                "label": "2023"
            },
            "children": [
                {
                    "name": "block",
                    "settings": {},
                    "children": [
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "2023"
                            }
                        },
                        {
                            "name": "heading",
                            "settings": {
                                "text": "A moment",
                                "tag": "h3"
                            }
                        },
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "What happened, and why it mattered."
                            }
                        }
                    ]
                },
                {
                    "name": "image",
                    "settings": {}
                }
            ]
        },
        {
            "name": "bfbe-timeline-item",
            "settings": {
                "label": "2024"
            },
            "children": [
                {
                    "name": "block",
                    "settings": {},
                    "children": [
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "2024"
                            }
                        },
                        {
                            "name": "heading",
                            "settings": {
                                "text": "A moment",
                                "tag": "h3"
                            }
                        },
                        {
                            "name": "text-basic",
                            "settings": {
                                "text": "What happened, and why it mattered."
                            }
                        }
                    ]
                },
                {
                    "name": "image",
                    "settings": {}
                }
            ]
        }
    ]
}
```

`bfbe-timeline-item` (BFB Timeline Moment), 46 controls, schema `../bfbe-schemas/references/elements/bfbe-timeline-item.json`, nestable itself.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Layout (`bfbeLayout`)
- `style` (select) **Style**: options: `story` Story: alternating across a line (default), `ledger` Ledger: one after another beside a line, `years` Years: a list beside one moment, `journey` Journey: a strip above one moment, `chapters` Chapters: a sticky list beside every moment. Story, the default, alternates moments across a line, and Ledger lists them beside a line. Years shows one moment beside a list, Journey one under a strip, and Chapters every moment beside a sticky list.
- `active` (number) **Moment shown first**: only when `style` is `years` or `journey`. Choose which moment opens in Years and Journey, 1 unless set. Remember choice and Link with a hash take precedence when they are ticked.
- `narrowBelow` (select) **Narrow layout below**: options: `480` 480 px, `640` 640 px, `768` 768 px (default), `992` 992 px. Set the container width under which every layout becomes one column: 480, 640, 768 (the default) or 992 px. Any list of labels then sits above or below the moments.
- `listPosition` (select) **Position**: options: `start` Before the moments (default), `end` After the moments, `top` Above the moments, `bottom` Below the moments; only when `style` is `years` or `chapters`. Choose where the label list sits in Years and Chapters: Before the moments (the default), or After, Above or Below them. Alignment sets how the list and the moments line up.
- `stageDirection` (select) **Moments flow**: options: `column` Down (default), `row` Across; writes CSS; only when `style` is `years` or `journey`. In Years and Journey, lay out the moments on show Down, the default, or Across. Moments packed, Moments aligned and Space between moments, 48px by default, place them.
Styling, in the schema file: `gap`, `rowAlign`, `stickTop`, `stageJustify`, `stageAlign`, `stageGap`.

### Moments (`bfbeMoments`)
- `itemFill` (checkbox) **Fill height**: only when `style` is `years` or `journey`. In Years and Journey, tick it so the moment on show stretches to fill its area, with its content centered unless Packed says otherwise.
- `itemDirection` (select) **Flows**: options: `row` Across (default), `column` Down; writes CSS. Lay out each moment's content Across, the default, or Down. It turns Down on a narrow container.
- `itemWrap` (select) **Wraps**: options: `nowrap` No (default), `wrap` Yes; writes CSS; only when `itemDirection` is `` or `row`. With Across, pick No, the default, or Yes to let the content wrap onto new lines.
Styling, in the schema file: `itemJustify`, `itemAlign`, `itemGap`, `itemMinHeight`, `itemBackground`, `cellPadding`, `itemBorder`, `itemShadow`.

### Line and dot (`bfbeLine`)
- `noDot` (checkbox) **Hide the dot**: only when `style` is `` or `story` or `ledger`. In Story and Ledger, tick it to leave the dot out, so the travelled line alone shows progress.
Styling, in the schema file: `lineColor`, `fillColor`, `lineWidth`, `dotSize`, `dotColor`, `dotRing`, `markSize`, `fillColor2`.

### Labels (`bfbeYears`)
The whole group shows only when `style` is `years` or `journey` or `chapters`.
- `listDirection` (select) **They flow**: options: `column` Down, `row` Across; writes CSS; only when `style` is `years` or `chapters`. In Years and Chapters, run the labels Down or Across. Unset, each layout uses its own.
- `listWrap` (select) **They wrap**: options: `nowrap` One line (default), `wrap` Wrap; writes CSS. Keep the labels on One line, the default, or let them Wrap.
- `listFill` (checkbox) **Stretch labels**: only when `style` is `years` or `chapters`. In Years and Chapters, tick it so the labels fill the list and the list fills its row.
- `group` (checkbox) **Group by label**. Tick it so neighboring moments that share a label, such as a year, get one button and show together.
- `thumbs` (checkbox) **On the labels**: only when `style` is `journey`. In Journey, tick it to show each moment's opening image on its label, with the label over it. Height, 96px by default, and Colour over image style it.
- `hash` (checkbox) **Link with a hash**. Tick it to write a chosen label into the address, such as #2013, so visiting that address opens the moment.
- `remember` (checkbox) **Remember choice**. Tick it to keep the chosen moment in the browser for the next visit. With Link with a hash ticked, a hash in the address overrides it.
Styling, in the schema file: `yearTypography`, `labelDim`, `yearActiveColor`, `pillBackground`, `pillActiveBackground`, `pillHoverBackground`, `labelPadding`, `pillBorder`, `pillActiveBorder`, `labelGap`, `listJustify`, `listAlign`, `yearsHeight`, `yearWidth`, `listBackground`, `listPadding`, `thumbHeight`, `thumbInk`.

### Autoplay (`bfbePlay`)
The whole group shows only when `style` is `years` or `journey`.
- `autoplay` (checkbox) **Play through**. Tick it to make Years and Journey move to the next moment on their own.
- `interval` (number) **Seconds per moment**: only when `autoplay` is set. Set how long each moment stays, 5 seconds unless set. Playback pauses while a pointer or keyboard focus is inside the timeline.
Styling, in the schema file: `ringColor`, `ringWidth`, `ringGap`.

### Motion (`bfbeMotion`)
- `reveal` (select) **Upcoming moments**: options: `none` As they are (default), `fade` Dimmed until the dot passes, `rise` Dimmed and lower until the dot passes; only when `style` is `` or `story` or `ledger` or `chapters`. In Story, Ledger and Chapters, choose As they are (the default), Dimmed until the dot passes, or Dimmed and lower until the dot passes.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Choose a curve for the same reveals, switches and travel as Duration. Snappy is the default, and you can pick from the list or set a custom curve.
Styling, in the schema file: `duration`, `easingCustom`.

## What it guarantees for accessibility (do not undo)
- In Years and Journey the labels form a tablist of tabs with aria-selected, and the chosen tab is the one Tab stop.
- Arrow keys, Home and End move between labels in Years, Journey and Chapters, and each press goes to that moment.
- Years and Journey display the chosen label's moments and hide the rest with display none, so assistive technology reads the moments shown and no others.
- In Chapters the list is a group, and the label for the moment in view carries aria-current.
- The line, dot and markers are hidden from assistive technology, so Story and Ledger read as ordinary content in order.
- Play through never starts under reduced motion, pauses while a pointer or focus is inside, and stops for good once the visitor picks a moment.
- Under reduced motion, scrolling to a chosen moment jumps rather than glides, and the line, reveal and switch durations are zero.
<!-- bfbe:generated:end -->

## Rendered DOM

The root is a `div.bfbe-tl` (Bricks adds `brxe-bfbe-timeline` and the `brxe-` id), a size container (`container-type: inline-size`). What sits before the stage depends on **Style** (`style`):

```html
<div class="brxe-bfbe-timeline bfbe-tl" data-bfbe-style="story" data-bfbe-wide="768" data-bfbe-active="1"
     data-bfbe-reveal="none" data-bfbe-play="0" data-bfbe-group="0" data-bfbe-list="start"
     data-bfbe-item-dir="row" data-bfbe-fill="0" data-bfbe-list-fill="0">
  <!-- story, ledger: -->
  <div class="bfbe-tl__track" aria-hidden="true"><span class="bfbe-tl__fill"></span><span class="bfbe-tl__dot"></span></div>
  <!-- years:    div.bfbe-tl__row > div.bfbe-tl__side > div.bfbe-tl__years[role=tablist], then the stage inside the row -->
  <!-- chapters: the same row; the side holds a track (fill, dot) before div.bfbe-tl__years[role=group] -->
  <!-- journey:  div.bfbe-tl__strip > div.bfbe-tl__track + div.bfbe-tl__scroll > fill, dot, div.bfbe-tl__years[role=tablist] -->
  <div class="bfbe-tl__stage">
    <div class="brxe-bfbe-timeline-item bfbe-tl__item" data-bfbe-label="2024">
      <span class="bfbe-tl__mark" aria-hidden="true"></span>
      <!-- the elements placed in the moment -->
    </div>
  </div>
</div>
```

- `data-bfbe-wide` is **Narrow layout below** and `data-bfbe-play` the seconds per moment or `0`. The root also carries `data-bfbe-thumbs="1"` (Journey only), `data-bfbe-hash="1"` and `data-bfbe-remember="1"` when those boxes are ticked.
- `.bfbe-tl__years` is empty in the server HTML. The script fills it with one `button.bfbe-tl__year > span` per moment or group, `role="tab"` in Years and Journey and `role="link"` in Chapters. With Journey thumbnails, an `img.bfbe-tl__thumb` comes first in each button.
- States: the chosen button has `.is-on`, `aria-selected` or `aria-current`, and `tabindex="0"`. A moment gets `.is-past` once the dot passes (Story, Ledger, Chapters) and `.is-on` while shown (Years, Journey).
- The root gets `.is-ready` after the script runs, `.is-timing` while the autoplay ring counts and `.is-held` while paused. The script writes `--bfbe-tl-p` (progress, 0 to 1) on the root and `--bfbe-tl-stage-h` on the stage; `--bfbe-tl-x` and `--bfbe-tl-y` place the Journey and Chapters dot.
- A moment's own marker is `span.bfbe-tl__mark.bfbe-tl__mark--own` holding the icon, `span.bfbe-tl__mark-text` and `img.bfbe-tl__mark-img`; `--solo` marks an icon or image alone (a circle), `--pic` an image alone.
- Where styling lands: Line and dot, the gaps and the label colours are custom properties on the root. `itemBackground`, `cellPadding`, `itemBorder`, `itemShadow` and `itemMinHeight` write to `.bfbe-tl__item`.
- `yearTypography`, `labelPadding` and `pillBorder` write to `.bfbe-tl__year`, `listBackground` to `.bfbe-tl__side`, `listPadding` to `.bfbe-tl__years`. On the Moment, `markPadding`, `markBorder` and `markBackground` write to `.bfbe-tl__mark`, `markColor` to its children, `markTypography` to `.bfbe-tl__mark-text`.

## Wiring to other elements

- **Its moments.** It reads only `bfbe-timeline-item` (BFB Timeline Moment, schema `../bfbe-schemas/references/elements/bfbe-timeline-item.json`) placed directly in it. Each moment's **Button label** (`label`, dynamic data) becomes `data-bfbe-label`, and the script builds the buttons from those after render.
- **A query loop on a moment.** Set `hasLoop` and `query` on one `bfbe-timeline-item` and each post renders as a moment with its own button. With `label: "{post_date:Y}"` and **Group by label** (`group: true`) on the timeline, a year's posts share one button.
- **The Moment's marker.** Its **Marker** group (`markIcon`, `markText`, `markImage`, then the Look controls) replaces the plain dot on the Story and Ledger line for that moment alone.
- **Links to a moment.** With **Link with a hash** (`hash: true`), any link on the page to `#` plus the label's slug, such as `#2013`, opens that moment. A Bricks Button or text link with that `href` is enough.
- Nothing else targets it. To style several timelines alike, give them a class in `_cssClasses`, never a `_cssId`: component instances share ids.
- Content inserted later: it re-initialises on Bricks' AJAX pagination, load-page, query-result and popup events. After inserting one with your own script, call `window.bfbeTimeline()`.

## Verified patterns

**Journey, a strip of years above one moment.** From the demo page `demo-bfb-timeline`, trimmed to three moments with shorter words. `style: "journey"` sets the years along a line above one moment; `labelDim` dims the unchosen years and `yearActiveColor` marks the chosen one. Set each `image` to an attachment on the site.

```json
{"name": "bfbe-timeline", "settings": {"style": "journey", "lineColor": {"hex": "#e9ecf1"}, "fillColor": {"hex": "#6e44ff"}, "dotColor": {"hex": "#6e44ff"}, "yearTypography": {"font-weight": "600", "font-size": "14"}, "yearActiveColor": {"hex": "#101828"}, "labelDim": "0.4", "labelGap": "32px", "gap": "24px"}, "children": [
  {"name": "bfbe-timeline-item", "settings": {"label": "2019"}, "children": [
    {"name": "block", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "2019"}}, {"name": "heading", "settings": {"text": "The first commercial build", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "A five-storey office let within a season."}}]},
    {"name": "image", "settings": {}}]},
  {"name": "bfbe-timeline-item", "settings": {"label": "2020"}, "children": [
    {"name": "block", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "2020"}}, {"name": "heading", "settings": {"text": "A resident architect on every job", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Every scheme starts with the client in the room."}}]},
    {"name": "image", "settings": {}}]},
  {"name": "bfbe-timeline-item", "settings": {"label": "2021"}, "children": [
    {"name": "block", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "2021"}}, {"name": "heading", "settings": {"text": "Our first residential tower", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Forty-two apartments, every one facing the water."}}]},
    {"name": "image", "settings": {}}]}
]}
```

**Chapters grouped by year.** From the fixture page `fixture-timeline`, trimmed to four moments. `style: "chapters"` keeps a sticky list of labels beside every moment; `group: true` gives the two 2021 moments one button, so four moments make three labels. `reveal: "fade"` dims each moment until the scroll reaches it.

```json
{"name": "bfbe-timeline", "settings": {"style": "chapters", "group": true, "reveal": "fade", "fillColor": {"hex": "#c9a227"}, "dotColor": {"hex": "#c9a227"}}, "children": [
  {"name": "bfbe-timeline-item", "settings": {"label": "2019"}, "children": [
    {"name": "block", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "2019"}}, {"name": "heading", "settings": {"text": "The idea", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "A sketch on a napkin."}}]},
    {"name": "image", "settings": {}}]},
  {"name": "bfbe-timeline-item", "settings": {"label": "2020"}, "children": [
    {"name": "block", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "2020"}}, {"name": "heading", "settings": {"text": "The build", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "A year of quiet work."}}]},
    {"name": "image", "settings": {}}]},
  {"name": "bfbe-timeline-item", "settings": {"label": "2021"}, "children": [
    {"name": "block", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "2021"}}, {"name": "heading", "settings": {"text": "The launch", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "The first customers."}}]},
    {"name": "image", "settings": {}}]},
  {"name": "bfbe-timeline-item", "settings": {"label": "2021"}, "children": [
    {"name": "block", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "2021"}}, {"name": "heading", "settings": {"text": "The hire", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Same year, second moment, one chapter."}}]},
    {"name": "image", "settings": {}}]}
]}
```

**Story with markers of their own.** From the fixture page `fixture-timeline`, without its picture marker (that attachment is the dev site's) and its probe class. Story is the default `style`. The first marker is a number pill, the second an icon and a word with a border, the third the plain dot; `fillColor2` fades the travelled line into a second colour.

```json
{"name": "bfbe-timeline", "settings": {"reveal": "rise", "lineWidth": "2px", "fillColor": {"hex": "#0f766e"}, "fillColor2": {"hex": "#c9a227"}, "dotColor": {"hex": "#c9a227"}}, "children": [
  {"name": "bfbe-timeline-item", "settings": {"label": "2022", "markText": "1", "markTypography": {"font-size": "15px", "font-weight": "700"}, "markPadding": {"top": "4", "right": "12", "bottom": "4", "left": "12"}, "markBackground": {"hex": "#0f766e"}, "markColor": {"hex": "#ffffff"}}, "children": [
    {"name": "block", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "2022"}}, {"name": "heading", "settings": {"text": "A number in the marker", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "The marker takes a word or a number and grows into a pill."}}]},
    {"name": "image", "settings": {}}]},
  {"name": "bfbe-timeline-item", "settings": {"label": "2023", "markIcon": {"library": "themify", "icon": "ti-star"}, "markText": "Star", "markIconSize": "20px", "markIconGap": "12px", "markBorder": {"width": {"top": "2", "right": "2", "bottom": "2", "left": "2"}, "style": "solid", "color": {"hex": "#111111"}}, "markBackground": {"hex": "#c9a227"}, "markColor": {"hex": "#111111"}}, "children": [
    {"name": "block", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "2023"}}, {"name": "heading", "settings": {"text": "An icon and a word in the marker", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "The icon and the word each at their own size, with a border."}}]},
    {"name": "image", "settings": {}}]},
  {"name": "bfbe-timeline-item", "settings": {"label": "2025"}, "children": [
    {"name": "block", "settings": {}, "children": [{"name": "text-basic", "settings": {"text": "2025"}}, {"name": "heading", "settings": {"text": "The plain dot", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "A moment with nothing set keeps the line's own marker."}}]},
    {"name": "image", "settings": {}}]}
]}
```

## Gotchas

- **Only Timeline Moments make buttons, and their label prints nothing.** The script builds each button from a moment's `label`, and an empty label gets its position number. The year shown inside a moment is an element you place. Any other element dropped straight into the timeline gets no button and is never hidden in Years or Journey. <!-- src: src/elements/timeline/timeline.js:25 and :83, src/elements/timeline/timeline.css:128, plugins/bfb-elements-pro/elements/timeline-item.php:215 -->
- **Moment shown first counts moments, not buttons.** With `group` on, `active: 3` opens the group holding the third moment. A remembered choice overrides it, and a matching hash overrides both. <!-- src: src/elements/timeline/timeline.js:277 -->
- **Group by label joins neighbours only.** Moments share a button when they are consecutive and their labels are equal; the same label further on gets a second button, and empty labels never group. Order a looped query by date. <!-- src: src/elements/timeline/timeline.js:79 -->
- **The hash is the label's slug, and only Chapters scrolls to it.** "( 2022 )" becomes `#2022` and "Step 1" `#step-1`. Years and Journey switch the moment without moving the page; Chapters scrolls to it, on load too when a hash or a remembered choice picks one. <!-- src: src/elements/timeline/timeline.js:72 and :293 -->
- **Remember choice is stored per element id.** The key is `bfbe-tl-` plus the root's id, so instances of one component, which share ids, share the stored choice. In Chapters only a click or an arrow key stores it, never the scroll. <!-- src: src/elements/timeline/timeline.js:71 and :194 -->
- **Narrow layout below reads the timeline's own width.** It is a container query on the root, so a timeline in a narrow column stacks on a wide screen. Setting `itemDirection: "row"` keeps moments across below it too (measured); left unset, they stack. <!-- src: src/elements/timeline/timeline.css:41 and :179 -->
- **A Moment's own Display defeats Years and Journey.** They hide unchosen moments with `display: none`, and Bricks writes a moment's **Display** (`_display`) on its id, which outranks that rule, so the moment always shows (measured). <!-- src: src/elements/timeline/timeline.css:128 -->
- **Story mirrors its moments when wide.** Moments on the left align their text, and the contents of their direct `block` children, to the end; moments on the right run reversed, picture first. Build each moment as a words `block` then an `image`; a block's own **Align items** wins. <!-- src: src/elements/timeline/timeline.css:155, docs/elements/timeline.md "Round 402" -->
- **Hide the dot leaves a stale mode.** `noDot` acts on Story and Ledger only, but while it is stored the panel hides **Dot size** and **Dot colour** in every style. Delete `noDot` before switching `style` and styling the dot. <!-- src: docs/elements/timeline.md "Round 402", plugins/bfb-elements-pro/elements/timeline.php:373 -->
- **Markers show on Story and Ledger only.** Elsewhere `.bfbe-tl__mark` is never displayed. Its fill is the line colour, then the travelled colour once passed; `markColor` and `markTypography` reach only its icon and word. **Icon size**, **Icon spacing**, **Image size** and **Typography** are offered only with what they size. <!-- src: src/elements/timeline/timeline.css:50, plugins/bfb-elements-pro/elements/timeline-item.php:92 and :138 -->
- **The rings default to the page colour.** The dot's ring, the markers' ring and the words on a passed marker without its own Background use `Canvas`, and so does the Chapters list's sticky box unless it sits beside the moments. On a dark or coloured section set **Dot ring colour** (`dotRing`) and the list's **Background** (`listBackground`). <!-- src: src/elements/timeline/timeline.css:23 and :102, src/elements/timeline-marker/timeline-marker.css:22 -->
- **Autoplay never runs in the builder.** **Play through** stays off in the canvas and under reduced motion, so check it on the page; a click or an arrow key stops it for good. <!-- src: src/elements/timeline/timeline.js:216 and :247 -->

## Never do

- Do not put anything but `bfbe-timeline-item` directly inside `bfbe-timeline`.
- Do not count on `label` to show the year inside a moment; place a `text-basic` or `heading` for it.
- Do not set `itemDirection: "row"` to get the default; leave it unset so moments stack below `narrowBelow`.
- Do not set Bricks' **Display** (`_display`) on a Timeline Moment in Years or Journey.
- Do not leave `noDot` stored when `style` is not `story` or `ledger`.
- Do not set `markIconSize`, `markIconGap`, `markImageSize` or `markTypography` without the `markIcon`, `markText` or `markImage` they size.
