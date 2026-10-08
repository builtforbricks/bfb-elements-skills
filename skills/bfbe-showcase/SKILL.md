---
name: bfbe-showcase
description: "Use when building a sticky scroll feature section with BFB Sticky Showcase (`bfbe-showcase`) and its Showcase Step and Showcase Card children: a pinned image or video that changes as the steps scroll past, pinned words beside scrolling pictures, or steps over a pinned full-width background, with snapping, step marks and cards on the pictures. Read before writing its settings."
---

# BFB Sticky Showcase (`bfbe-showcase`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-showcase.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/showcase/

## What it is
Steps of content beside media that stays put and changes as the visitor scrolls, walking through features one step at a time. Each step carries its own image or video, and on narrow screens every step shows its own media in place. Five layouts pin either the media or the words, or lay the steps over a full-width pinned background.

**Not for:** Not for a parent that clips its overflow: the pinned half uses CSS position: sticky, which a clipping parent can stop from sticking. Below the Stack below width the media no longer stays put, because each step shows its own media in place.

**Costs a page:** CSS 2.41 KB, JS 2.34 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable. Its own children: `bfbe-showcase-step`.
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

## Rendered DOM

Where the media stays (`side` `right`, `left` or `behind`), once the script has run:

```html
<div class="bfbe-show bfbe-show--right bfbe-show--snap bfbe-show--dim" data-bfbe-stack="768">
  <div class="bfbe-show__steps">
    <div class="bfbe-show__step is-active" data-bfbe-step="a1b2c3">
      <div class="bfbe-show__inline"><img class="bfbe-show__img" …></div>  <!-- shown only when stacked -->
      <div class="bfbe-show__body">…the step's own elements…</div>
    </div>
  </div>
  <div class="bfbe-show__sticky">
    <div class="bfbe-show__media">                                        <!-- position: sticky -->
      <div class="bfbe-show__slide is-active" data-bfbe-slide="0" data-bfbe-step="a1b2c3">
        <img class="bfbe-show__img" …>
        <div class="bfbe-show__card" data-bfbe-place="bottom-left" data-bfbe-wide="0">…</div>
      </div>
      <div class="bfbe-show__overlay"></div>
      <button type="button" class="bfbe-show__pause bfbe-show__pause--bottom-right">…</button>
    </div>
  </div>
</div>
```

- Root modifiers: `bfbe-show--right|left|behind`; a words layout gives `--right` or `--left` plus `bfbe-show--pin-words` and `bfbe-show--words-fade|rise|none`. `bfbe-show--snap` marks either snapping value, and `snap: "always"` adds `bfbe-show--snap-always` as well. Also `bfbe-show--dim` and `bfbe-show--no-pause`. `data-bfbe-stack` holds `stackBelow` (`0` for Never).
- Words stay: there is no `.bfbe-show__media`. Each step's `.bfbe-show__inline` shows at every width, and `.bfbe-show__sticky` holds `.bfbe-show__panel` (sticky) with `.bfbe-show__slot`, then `.bfbe-show__marks.bfbe-show__marks--dots` (`role="group"`, `aria-label="Steps"`) of `button.bfbe-show__mark[data-bfbe-mark]` named Step 1, Step 2. The script moves each step's `.bfbe-show__body` into the slot, stamped `data-bfbe-of`, and back once stacked. The root carries `data-bfbe-marks`.
- A card renders inside its step, and the script moves it onto that step's `.bfbe-show__slide` (media stays, wide) or its `.bfbe-show__inline` (words stay, or stacked). Its place is the attribute `data-bfbe-place`, never a class.
- States the script sets: `is-active` on the current step, slide, body and mark, with `aria-current="step"` on the mark; `is-paused` on the root; `is-holding` on a `snap-always` root while it holds the page, with `bfbe-snap-on` on `<html>`; `--bfbe-show-pad` inline on the root, the page's `scroll-padding-top`.
- Media is `<img class="bfbe-show__img">` (first slide eager, the rest lazy) or `<video class="bfbe-show__vid" muted loop playsinline>` with the step's image as `poster`. Only the current step's video plays, and only the copy the layout shows. `.bfbe-show__overlay` is drawn only when an overlay key has a value, and the pause button only when a step has a video.
- Where controls write: `mediaBorder` to `.bfbe-show__media` and to every `.bfbe-show__inline img, video`; `mediaShadow` and `mediaBackground` to `.bfbe-show__media`; the overlay keys to `.bfbe-show__overlay`; the panel keys to `.bfbe-show__panel`; the pause keys to `.bfbe-show__pause`; `stepsColor` and `stepsAlign` to the steps, behind only. `gap` is the root's `column-gap`; the rest are custom properties on the root (`--bfbe-sc-split`, `--bfbe-show-gap`, `--bfbe-show-top`, `--bfbe-show-step`, `--bfbe-show-ratio`, `--bfbe-show-fit`, `--bfbe-show-dim`, `--bfbe-show-mark*`).
- In the builder only, `builderView: "open"` adds `bfbe-show--canvas` (media static, every set of words shown) and Working adds `data-bfbe-live="1"`.

## Wiring to other elements

Stands alone among other elements: nothing targets it and it targets nothing. Its wiring is its own children.

- The tree is `bfbe-showcase` > `bfbe-showcase-step` > any elements, with an optional `bfbe-showcase-card` inside a step > any elements. Schemas: `../bfbe-schemas/references/elements/bfbe-showcase-step.json` and `../bfbe-schemas/references/elements/bfbe-showcase-card.json`.
- **Showcase Step** carries the media: **Image** `image` (`{"id": 123, "size": "full"}`), **Video** `videoFile` from the media library, or **Or a video URL** `video`, which takes a dynamic tag. The same values feed the step's slide in the pinned column and its own in-place copy. **Up and down** `place` positions it behind the steps only. For the pause button on its own video it reads the showcase's `pauseButton` and `pausePosition`.
- **Showcase Card**: **Where it sits** `place` (`bottom-left` by default, `bottom`, `bottom-right`, `top-left`, `top`, `top-right`, `centre`), **Inset** `inset` (20px), **Nudge across** `nudgeX` and **Nudge down** `nudgeY` (negatives allowed), **Fill the width** `stretch`. Its own **Show it** `builderView` acts in the builder only, apart from the showcase's.
- `window.bfbeShowcase()` starts every `.bfbe-show` again. It already runs on load and after Bricks' AJAX pagination, page loads, query results and popups; call it after your own script inserts a showcase.
- To target one showcase in custom CSS, give it a class in `_cssClasses`, never `_cssId`: component instances share ids.

## Verified patterns

**1. Words pinned, snapping to every step, cards on the pictures.** From the demo page `demo-bfb-showcase`, trimmed to two of its four steps with shorter words. `side: "right-words"` pins the words in a dark panel with dot marks, `snap: "always"` with `stepHeight: "50vh"` makes each step half a window, and each card spans the foot of its picture. The image ids are the demo site's media: use the target site's own. The video was a demo-site file, replaced here with an example.com address.

```json
{"name": "bfbe-showcase", "settings": {
  "side": "right-words", "snap": "always", "stepHeight": "50vh", "stickyTop": "23vh", "split": 50,
  "gap": "clamp(32px, 4.5vh, 56px)", "stepGap": "clamp(32px, 4.5vh, 56px)", "mediaRatio": "1 / 1",
  "mediaBorder": {"radius": {"top": "22px", "right": "22px", "bottom": "22px", "left": "22px"}},
  "panelBackground": {"color": {"hex": "#101828"}}, "panelColor": {"hex": "#ffffff"},
  "panelPadding": {"top": "24", "right": "40", "bottom": "24", "left": "40"},
  "panelBorder": {"radius": {"top": 24, "right": 24, "bottom": 24, "left": 24}},
  "wordsFx": "rise", "wordsPlace": "start", "marks": "dots", "markSize": "9px",
  "markColor": {"rgb": "rgba(255, 255, 255, 0.3)"}, "markOnColor": {"hex": "#6e44ff"}, "dimInactive": true, "dimAmount": 0.45
}, "children": [
  {"name": "bfbe-showcase-step", "settings": {"image": {"id": 3957, "size": "full"}}, "children": [
    {"name": "heading", "settings": {"text": "Cut from one sheet of acetate", "tag": "h3"}},
    {"name": "text-basic", "settings": {"text": "Seven weeks in an Italian mill, then a day on our own bench."}},
    {"name": "bfbe-showcase-card", "settings": {"place": "bottom", "inset": "18px", "stretch": true,
      "_display": "flex", "_direction": "row", "_justifyContent": "space-between", "_columnGap": "14px",
      "_background": {"color": {"hex": "#ffffff"}}, "_padding": {"top": "14", "right": "18", "bottom": "14", "left": "18"}}, "children": [
      {"name": "text-basic", "settings": {"text": "Marlowe, in tortoise"}},
      {"name": "text-basic", "settings": {"text": "£185"}}
    ]}
  ]},
  {"name": "bfbe-showcase-step", "settings": {"image": {"id": 4158, "size": "full"}, "video": "https://example.com/wp-content/uploads/eye-test.mp4"}, "children": [
    {"name": "heading", "settings": {"text": "Forty minutes, and a photograph of the back of your eye", "tag": "h3"}},
    {"name": "text-basic", "settings": {"text": "You leave with the prescription and the images."}}
  ]}
]}
```

**2. The default layout: media pinned on the right.** From the fixture page `fixture-showcase`, trimmed to two of its three steps with shorter words. No `side`, so the media stays on the right; `stackBelow: "992"` stacks it on tablets, `dimInactive` fades the steps not in view, and `duration` with the Overshoot `easing` shapes the crossfade. Image ids 22 and 23 are the development site's: use the target site's own.

```json
{"name": "bfbe-showcase", "settings": {"dimInactive": true, "stackBelow": "992", "duration": 700, "easing": "cubic-bezier(0.34, 1.56, 0.64, 1)"}, "children": [
  {"name": "bfbe-showcase-step", "settings": {"image": {"id": 22, "size": "large"}}, "children": [
    {"name": "heading", "settings": {"text": "Design it", "tag": "h3"}},
    {"name": "text-basic", "settings": {"text": "What it does, and why that matters."}}
  ]},
  {"name": "bfbe-showcase-step", "settings": {"image": {"id": 23, "size": "large"}}, "children": [
    {"name": "heading", "settings": {"text": "Build it", "tag": "h3"}},
    {"name": "text-basic", "settings": {"text": "What it does, and why that matters."}}
  ]}
]}
```

**3. Steps over a pinned background.** From the same fixture page, trimmed to two of its three steps with shorter words. `side: "behind"` pins the media full width, the overlay colour and gradient darken it under white `stepsColor` words, and `stepsAlign` with `stepsPlace` put the steps bottom right; the last step's own `place: "flex-start"` lifts it to the top of its slot. Same image ids, same note.

```json
{"name": "bfbe-showcase", "settings": {
  "side": "behind", "stepsAlign": "flex-end", "stepsPlace": "flex-end", "stepsWidth": "520px",
  "stepsColor": {"hex": "#ffffff"}, "dimInactive": true, "stackBelow": "640",
  "overlayColor": {"hex": "#0b1020", "rgb": "rgba(11, 16, 32, 0.45)"},
  "overlayGradient": {"angle": "180", "colors": [{"color": {"hex": "#000000", "rgb": "rgba(0, 0, 0, 0)"}, "stop": "40"},
    {"color": {"hex": "#000000", "rgb": "rgba(0, 0, 0, 0.7)"}, "stop": "100"}]}
}, "children": [
  {"name": "bfbe-showcase-step", "settings": {"image": {"id": 22, "size": "large"}}, "children": [
    {"name": "heading", "settings": {"text": "Design it", "tag": "h3"}},
    {"name": "text-basic", "settings": {"text": "What it does, and why that matters."}}
  ]},
  {"name": "bfbe-showcase-step", "settings": {"image": {"id": 23, "size": "large"}, "place": "flex-start"}, "children": [
    {"name": "heading", "settings": {"text": "Ship it", "tag": "h3"}},
    {"name": "text-basic", "settings": {"text": "What it does, and why that matters."}}
  ]}
]}
```

## Gotchas

- **Media goes on each step, not on the showcase.** Each step's `image`, `videoFile` or `video` fills its slide, `videoFile` winning over `video` with the image as the video's poster. Where the media stays, a step with none shows an empty frame while it is current. <!-- src: plugins/bfb-elements-pro/elements/showcase.php:780-782, 917-922; plugins/bfb-elements-pro/elements/showcase-step.php:38-61, 90-92 -->
- **Only Showcase Steps count.** Any other element placed directly in the showcase renders in the steps column with no slide, no mark and no lit state. <!-- src: plugins/bfb-elements-pro/elements/showcase.php:894-908; src/elements/showcase/showcase.js:30 -->
- **A clipping ancestor stops the pin.** The pinned half, `.bfbe-show__media` or `.bfbe-show__panel`, is `position: sticky`, so `overflow: hidden` on the showcase or any parent keeps it from staying put. <!-- src: src/elements/showcase/showcase.css:53, 112-116 -->
- **Stack below follows the window, one value for every width.** `stackBelow` is a media query on the viewport, not on the showcase's own width; like `side` and `snap`, it takes no breakpoint suffix. Below it the pinned column hides, each step shows its own media above its words, words and cards go back into their steps, and snapping and dimming stop. <!-- src: src/elements/showcase/showcase.css:4-8, 325-334; src/elements/showcase/showcase.js:180-192; plugins/bfb-elements-pro/elements/showcase.php:106-149 -->
- **The space between steps is the scroll.** Where the media stays, `stepGap` defaults to 40vh, a screenful of scroll per step. With the words pinned it is 24px; behind it is 0 and each step is a slot as tall as `mediaHeight` (100vh). Stacked it falls back to 24px unless `stepGap` is set, which then carries to both. <!-- src: src/elements/showcase/showcase.css:11-13, 36-39, 100; plugins/bfb-elements-pro/elements/showcase.php:229-239 -->
- **Snapping is set on the page.** Either snapping value puts `scroll-snap-type` on `<html>`. `snap: "always"` turns it mandatory only while the showcase holds the page, from its first step reaching the sticky line to its last. A stacked showcase withdraws its snap points; `stackBelow: "0"` keeps them at every width. <!-- src: src/elements/showcase/showcase.css:168-197, 210, 255-259; src/elements/showcase/showcase.js:232-242; docs/elements/showcase.md "Round 422" -->
- **Snaps to every step sizes the words layouts.** With `snap: "always"` and the words pinned, each step's picture and the panel are both **Step height** `stepHeight` tall, by default `100dvh` less `stickyTop` and `stepGap`, and the picture crops to fit. **Smallest height** `panelHeight` is hidden and dropped in that mode. <!-- src: src/elements/showcase/showcase.css:232-235; plugins/bfb-elements-pro/elements/showcase.php:121-138, 406-418 -->
- **With the words pinned, the words leave their step.** The script moves each step's `.bfbe-show__body` into the panel while wide, so styles set on the Showcase Step, or selectors through it, do not reach them there. A colour that reads on the panel may not read on the page once stacked; let the words inherit. <!-- src: src/elements/showcase/showcase.js:141-191; docs/elements/showcase.md "each step's words render in two places" -->
- **The media frame belongs to the layouts where the media stays.** With the words pinned, `mediaShadow`, `mediaBackground`, `overlayColor` and `overlayGradient` are hidden and dropped. `mediaBorder` (corners included), `mediaRatio` and `mediaFit` still reach each step's own picture. <!-- src: plugins/bfb-elements-pro/elements/showcase.php:543-615; src/elements/showcase/showcase.css:61-62; docs/elements/showcase.md "round 390" -->
- **Behind, the steps place themselves on the background.** With `side: "behind"`, `stepsAlign`, `stepsPlace`, `stepsWidth` (480px), `stepsInset` (40px) and `stepsColor` act and `split` and `gap` are hidden. A step's `place` overrides the vertical placement there only; Bricks' **Align self** `_alignSelf` moves one step across. <!-- src: src/elements/showcase/showcase.css:36-39; plugins/bfb-elements-pro/elements/showcase.php:159-218, 303-328; plugins/bfb-elements-pro/elements/showcase-step.php:63-73; docs/elements/showcase.md "round 269" -->
- **A card needs a step, and a step with media.** Outside a step the script never moves a card onto a picture, and the builder says it belongs in a Showcase Step. Give its step an image or video, or the card has no picture to sit on. <!-- src: plugins/bfb-elements-pro/elements/showcase-card.php:128; src/elements/showcase/showcase.js:164-178; plugins/bfb-elements-pro/elements/showcase-step.php:93-108 -->
- **A card's flex controls wait on Display.** The card carries Bricks' **Direction** `_direction`, **Row gap** `_rowGap` and **Column gap** `_columnGap`, which Bricks offers on its own layout elements alone, and they act only with **Display** `_display: "flex"`. <!-- src: plugins/bfb-elements/includes/abstract-element.php:798-843; docs/elements/showcase.md "The card also carries" -->

## Never do

- Do not place anything but a `bfbe-showcase-step` directly in a `bfbe-showcase`, or a `bfbe-showcase-card` anywhere but inside a step.
- Do not leave a step without `image`, `videoFile` or `video` in a layout where the media stays.
- Do not set `_overflow: "hidden"` on the showcase or on any element around it.
- Do not write `stackBelow`, `side` or `snap` with a breakpoint suffix.
- Do not set Info panel keys without `side: "right-words"` or `"left-words"`, `panelHeight` with `snap: "always"`, or `mediaShadow`, `mediaBackground` and the overlay keys with the words pinned.
- Do not style a words layout's words through the Showcase Step's own settings; style the elements inside it, or the panel.
- Do not set a card's `_direction`, `_rowGap` or `_columnGap` without `_display: "flex"`.
- Do not add `role`, `tabindex` or `aria-current` to the marks or the pause button; the element and its script manage their names and state.
