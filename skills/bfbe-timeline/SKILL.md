---
name: bfbe-timeline
description: "Use when placing, wiring or styling BFB Content Timeline (`bfbe-timeline`): one set of moments in five layouts: Story and Ledger draw a line that fills as the page scrolls. Read before writing its settings."
---

# BFB Content Timeline (`bfbe-timeline`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
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

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
