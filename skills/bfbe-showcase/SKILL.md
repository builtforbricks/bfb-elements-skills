---
name: bfbe-showcase
description: "Use when placing, wiring or styling BFB Sticky Showcase (`bfbe-showcase`): steps of content beside media that stays put and changes as the visitor scrolls, walking through features one step at a time. Read before writing its settings."
---

# BFB Sticky Showcase (`bfbe-showcase`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-showcase.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/showcase/

## What it is
Steps of content beside media that stays put and changes as the visitor scrolls, walking through features one step at a time. Each step carries its own image or video, and on narrow screens every step shows its own media in place. Five layouts pin either the media or the words, or lay the steps over a full-width pinned background.

**Not for:** Not for a parent that clips its overflow: the pinned half uses CSS position: sticky, which a clipping parent can stop from sticking. Below the Stack below width the media no longer stays put, because each step shows its own media in place.

**Costs a page:** CSS 2.41 KB, JS 2.34 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable. Its own children: `bfbe-showcase-step`, `bfbe-showcase-card`.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-showcase",
    "settings": {},
    "children": [
        {
            "name": "bfbe-showcase-step",
            "settings": {},
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
                        "text": "What it does, and why that matters."
                    }
                }
            ]
        },
        {
            "name": "bfbe-showcase-step",
            "settings": {},
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
                        "text": "What it does, and why that matters."
                    }
                }
            ]
        },
        {
            "name": "bfbe-showcase-step",
            "settings": {},
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
                        "text": "What it does, and why that matters."
                    }
                }
            ]
        }
    ]
}
```

`bfbe-showcase-step` (BFB Showcase Step), 36 controls, schema `../bfbe-schemas/references/elements/bfbe-showcase-step.json`, nestable itself.

`bfbe-showcase-card` (BFB Showcase Card), 38 controls, schema `../bfbe-schemas/references/elements/bfbe-showcase-card.json`, nestable itself.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Layout (`bfbeLayout`)
- `snap` (select) **Scrolling**: options: `free` Free (default), `snap` Snaps when close, `always` Snaps to every step. Free is the default. Snaps when close settles on a step when the visitor is near it, and Snaps to every step makes each scroll land on a step while the showcase is in view.
- `stackBelow` (select) **Stack below**: options: `480` 480 px, `640` 640 px, `768` 768 px (default), `992` 992 px, `0` Never. Below 768 px by default, each step stacks and shows its own media in place. Pick 480, 640 or 992 px instead, or Never to keep the layout at every width.
- `dimInactive` (checkbox) **Dim the others**. Tick it to dim the steps that are not current, to the opacity set by How dim, 0.4 by default.
- `side` (select) **Layout**: options: `right` Media right, media stays (default), `left` Media left, media stays, `right-words` Media right, words stay, `left-words` Media left, words stay, `behind` Steps over the media. Choose which half holds still: Media right, media stays (the default), Media left, media stays, Media right, words stay, Media left, words stay, or Steps over the media, which pins a full-width background.
Styling, in the schema file: `stepHeight`, `stepsAlign`, `stepsPlace`, `stepsWidth`, `stepsInset`, `stepsColor`, `stepGap`, `dimAmount`, `mediaHeight`, `split`, `gap`, `stickyTop`.

### Info panel (`bfbePanel`)
The whole group shows only when `side` is `right-words` or `left-words`.
- `wordsFx` (select) **Text transition**: options: `fade` Crossfade (default), `rise` Rise, `none` At once; only when `side` is `right-words` or `left-words`. Choose how the words change in the pinned panel: Crossfade (the default), Rise or At once. This group shows just for the layouts where the words stay.
- `wordsPlace` (select) **Words sit**: options: `stretch` Filling the panel (default), `start` At the top, `center` In the middle, `end` At the bottom; writes CSS; only when `side` is `right-words` or `left-words`. Filling the panel is the default. Pick At the top, In the middle or At the bottom to place the words.
- `marks` (select) **Show them as**: options: `dots` Dots (default), `lines` Lines, `numbers` Numbers, `none` None; only when `side` is `right-words` or `left-words`. Show the step marks as Dots (the default), Lines, Numbers or None, drawn as buttons that jump to a step.
Styling, in the schema file: `panelBackground`, `panelColor`, `panelBorder`, `panelShadow`, `panelPadding`, `panelHeight`, `markColor`, `markOnColor`, `panelGap`, `marksAlign`, `markGap`, `markSize`.

### Media (`bfbeMedia`)
- `mediaFit` (select) **Image fit**: options: `cover` Fill the frame (default), `contain` Fit inside it; writes CSS. Fill the frame is the default. Pick Fit inside it so nothing is cropped.
- `pauseButton` (select) **Show pause button**: options: `never` Never. The pause button shows by default on steps that have a video, and Never removes it. It pauses every step video, and its name swaps between Pause and Play.
- `pausePosition` (select) **Position**: options: `bottom-right` Bottom right (default), `bottom-left` Bottom left, `top-right` Top right, `top-left` Top left; only when `pauseButton` is not `never`. Where the pause button sits: Bottom right (the default), Bottom left, Top right or Top left.
Styling, in the schema file: `mediaBorder`, `mediaRatio`, `mediaShadow`, `mediaBackground`, `overlayColor`, `overlayGradient`, `pauseSize`, `pauseOffset`, `pauseColor`, `pauseBackground`, `pauseHoverBackground`, `pauseBorder`, `pauseShadow`.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Snappy by default. Pick another curve from the list, or Custom to type your own in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Every step lit, so you can style them, `live` Working, as on the site (default). Working, as on the site, is the default, so the canvas moves through the steps as you scroll. Every step lit, so you can style them shows all the words at once.

## What it guarantees for accessibility (do not undo)
- Where the words stay, the step marks are real buttons named Step 1, Step 2 and so on, and a press scrolls to that step.
- The current step mark carries aria-current="step", so a screen reader can tell which step is showing.
- A step's video is muted and plays while its step is current, and the pause button swaps its name between Pause and Play.
- Under reduced motion the media change is a cut instead of a crossfade, and scrolling to a step jumps instead of gliding.
- Under reduced motion step videos are not played, and the pause button is hidden because nothing plays.
- Snaps when close uses proximity snapping, never mandatory, so a visitor is not held on a section they are trying to leave.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
