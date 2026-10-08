---
name: bfbe-read-more
description: "Use when a page needs a read more or show more toggle, a truncated excerpt, or long content collapsed to a few lines or a set height. BFB Read More (`bfbe-read-more`) clamps whatever is nested inside it behind a real button; read this before writing its settings."
---

# BFB Read More (`bfbe-read-more`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-read-more.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/read-more/

## What it is
Clamps any content you nest inside it to a number of lines or a height, with a real button that expands the rest. The button carries aria-expanded and aria-controls, and the clamped content stays in the page rather than being removed. If the content already fits, the button hides itself, and tabbing into clamped content expands it.

**Not for:** Each Read More clamps one block with its own button, so panels where opening one closes another need a different structure. The clamped part is still in the page, so content that must stay out of the page until requested does not belong here.

**Costs a page:** CSS 0.65 KB, JS 0.96 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-read-more",
    "settings": {},
    "children": [
        {
            "name": "text",
            "settings": {
                "text": "<p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.</p>"
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Clamp (`bfbeClamp`)
- `mode` (select) **Clamp by**: options: `lines` Lines (default), `height` Height. Lines is the default. Height clamps to a set height instead, which suits content that mixes images and text.
Styling, in the schema file: `lines`, `maxHeight`.

### Button (`bfbeButton`)
- `labelMore` (text) **Collapsed label**: placeholder Read more; dynamic data accepted. The words on the button while it is closed, Read more by default. It accepts dynamic data.
- `labelLess` (text) **Expanded label**: placeholder Show less; dynamic data accepted. The words once the content is open, Show less by default. It also accepts dynamic data.
- `icon` (icon) **Icon**. An optional icon that turns 180 degrees when the content opens.
- `iconPosition` (select) **Icon position**: options: `right` After the words (default), `left` Before the words; only when `icon` is set. After the words is the default, or pick Before the words.
Styling, in the schema file: `iconSize`, `buttonAlign`, `buttonGap`, `buttonTypography`, `buttonBackground`, `buttonBorder`, `buttonPadding`, `buttonHoverColor`, `buttonHoverBackground`.

### Fade (`bfbeFade`)
- `fade` (checkbox) **Fade the last lines**. Off by default. Tick it and the clamped edge fades out instead of cutting off hard.
Styling, in the schema file: `fadeSize`.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. How they speed up and slow down, Snappy by default. Pick Custom and type your own curve in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Open, so you can style it (default), `closed` Closed, as the site leaves it, `live` Working, as on the site. The content is shown open by default, so you can style it. Closed shows the clamped state, and Working lets the button expand the content in the builder.

## What it guarantees for accessibility (do not undo)
- The toggle is a real button with aria-expanded and aria-controls pointing at the content, so Enter and Space both work.
- Tabbing into clamped content, such as a link in the hidden lines, expands the element, so the focused link comes into view.
- Clamped content stays in the DOM, and a short block that already fits hides its button.
- Without script the content is not clamped, because the clamp applies after a one-line inline script marks the element ready.
- With reduced motion requested, the content opens and closes with no transition.
<!-- bfbe:generated:end -->

## Rendered DOM

On the front end, clamped by lines with the fade, before a click:

```html
<div class="brxe-bfbe-read-more bfbe-read-more bfbe-read-more--lines bfbe-read-more--fade is-ready">
  <script>document.currentScript.parentNode.classList.add("is-ready")</script>
  <div class="bfbe-read-more__content" id="bfbe-{uid}-content"><!-- the nested children --></div>
  <button type="button" class="bfbe-read-more__toggle bfbe-chip bfbe-read-more__toggle--icon-right"
          aria-expanded="false" aria-controls="bfbe-{uid}-content">
    <!-- with an icon: Bricks' icon markup, class bfbe-read-more__icon, aria-hidden="true" -->
    <span class="bfbe-read-more__labels">
      <span class="bfbe-read-more__more">Read more</span>
      <span class="bfbe-read-more__less">Show less</span>
    </span>
  </button>
</div>
```

- Root modifiers: `bfbe-read-more--lines` or `bfbe-read-more--height` from **Clamp by** (`mode`), and `bfbe-read-more--fade` from **Fade the last lines** (`fade`). The inline `<script>` is the root's first child, front end only.
- States the script sets on the root: `is-ready` (every clamp rule requires it), `is-open` (`aria-expanded="true"`, icon turned 180 degrees, labels swapped), `is-closing` (during the collapse, beside `is-open`) and `is-short` (content fits: no clamp, no fade, button `display: none`). An inline `max-height` on `__content` lasts only for the animation.
- The clamp sits on `__content`: by lines `display: -webkit-box` with `-webkit-line-clamp: var(--bfbe-rm-lines)`, by height `max-height: var(--bfbe-rm-max)`. It is `overflow: hidden` in every state. The fade is a `mask-image` there, so it suits any background.
- The root is a flex column with `align-items: flex-start`; the children sit in `__content`, a plain block box, so space between them comes from their own margins or one Block wrapping them.
- Root variables: **Lines** (`lines`) writes `--bfbe-rm-lines` (3), **Height** (`maxHeight`) `--bfbe-rm-max` (200px), **Fade size** (`fadeSize`) `--bfbe-rm-fade` (3em), **Space above** (`buttonGap`) `--bfbe-rm-gap` (8px, the button's top margin), **Duration (ms)** and **Easing** `--bfbe-duration` and `--bfbe-ease`.
- The button carries `bfbe-chip`, the pack's pill: 1px border, surface fill, `.5em .9em` padding, inherited font and colour. **Typography**, **Background**, **Border**, **Padding** and **Align** (as `align-self`) write to `.bfbe-read-more__toggle`; the two **On hover** controls write to its `:hover` and `:focus-visible`; **Icon size** to `.bfbe-read-more__icon`.
- In the canvas there is no inline script. **Show it** Open adds `bfbe-read-more--canvas` (never clamped, button always shown); Working adds `data-bfbe-live="1"`.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing. Its button controls only its own `__content`, and no attribute lets another element open or close it.

- **By class, never by id.** Put a class in `_cssClasses` for any CSS or script that reaches it, not `_cssId`: component instances share ids, and in a query loop Bricks moves the id into a class.
- **Query loops and AJAX.** With `hasLoop` each iteration gets its own content id, so every `aria-controls` stays unique. The script re-runs on `bricks/ajax/pagination/completed`, `bricks/ajax/load_page/completed`, `bricks/ajax/query_result/displayed` and `bricks/ajax/popup/loaded`; a Read More it has seen keeps its open state. For content inserted any other way, call `window.bfbeReadMore()`.
- **Nesting.** The script and the stylesheet read only direct children, so a Read More inside another Read More works on its own.

## Verified patterns

**1. A text excerpt by lines, with a styled button.** From the feature page `feature-bfb-read-more-collapse-to-a-few-lines` (the website's "Collapse to a few lines" clip). Three lines, 600 ms with Medium easing, the pill in ink with the accent on hover; the colour objects show the shapes these controls store. Font size and the story's last clause trimmed.

```json
{
  "name": "bfbe-read-more",
  "settings": {
    "mode": "lines",
    "lines": 3,
    "labelMore": "Read more",
    "labelLess": "Show less",
    "duration": 600,
    "easing": "cubic-bezier(0.65, 0, 0.35, 1)",
    "buttonBackground": { "color": { "hex": "#101828" } },
    "buttonHoverBackground": { "color": { "hex": "#6e44ff" } },
    "buttonTypography": { "color": { "hex": "#ffffff" }, "font-weight": "600" },
    "buttonHoverColor": { "hex": "#ffffff" },
    "buttonPadding": { "top": "12", "right": "24", "bottom": "12", "left": "24" },
    "buttonBorder": { "radius": { "top": 999, "right": 999, "bottom": 999, "left": 999 } },
    "buttonGap": "20px"
  },
  "children": [
    { "name": "text", "settings": { "text": "<p>Ridgeline began in a heating firm in Otley with nine engineers, a whiteboard that never matched the diary, and a notebook in every van that came back damp on a Friday. The office rang the engineers to ask where they were. The engineers rang the office to ask what the job was.</p><p>We built the first version over a winter, for that one firm. It did three things: it put the day on a board, it put the job on a phone, and it turned a signature into an invoice. The owner stopped coming in on Saturdays to do the paperwork.</p>" } }
  ]
}
```

**2. Mixed content by height.** From the fixture `fixture-read-more-mixed`: a heading, text, a button and more text held to 160px, because lines would clamp only the last text. `builderView: "live"` makes the button work in the canvas too. The fixture's image child is left out here; an image from the site's media library clamps with the rest.

```json
{
  "name": "bfbe-read-more",
  "settings": { "mode": "height", "maxHeight": "160px", "builderView": "live" },
  "children": [
    { "name": "heading", "settings": { "text": "A heading inside the clamp", "tag": "h3" } },
    { "name": "text-basic", "settings": { "text": "Text before the button, long enough to wrap onto several lines at any sensible width. Text before the button, long enough to wrap onto several lines at any sensible width. Text before the button, long enough to wrap onto several lines at any sensible width." } },
    { "name": "button", "settings": { "text": "A button inside", "link": { "type": "external", "url": "#" } } },
    { "name": "text-basic", "settings": { "text": "Text after the button, also long enough to wrap. Text after the button, also long enough to wrap. Text after the button, also long enough to wrap. Text after the button, also long enough to wrap." } }
  ]
}
```

## Gotchas

- **Lines counts text, not elements.** With several child elements (a heading, an image, a button), the browser applied **Lines** to the trailing text only: 569 of 620px stayed visible with four lines set. Use `mode: "height"` for a mix. <!-- src: docs/elements/read-more.md "Anything can go inside" (measured 2026-09-13) -->
- **Each clamp value acts in its own mode only.** **Height** (`maxHeight`) does nothing unless `mode: "height"`, and **Lines** (`lines`) does nothing under it; the panel hides the other mode's control. <!-- src: plugins/bfb-elements/elements/read-more.php:64-86; src/elements/read-more/read-more.css:37-45 -->
- **Fade size needs the fade.** **Fade size** (`fadeSize`) acts only with `fade: true`, which adds the `--fade` class the mask rule matches. <!-- src: plugins/bfb-elements/elements/read-more.php:246-256, 299-301; src/elements/read-more/read-more.css:51-57 -->
- **Content that fits gets no button.** When the content is no taller than the clamp, the script adds `is-short`, which drops the clamp, the fade and the button. Test with content that runs well past the clamp. <!-- src: src/elements/read-more/read-more.js:41-46; src/elements/read-more/read-more.css:76 -->
- **The canvas shows it open by default.** **Show it** (`builderView`) starts at Open: nothing is clamped and the button does nothing. `closed` shows the clamp, `live` makes the button work, and the front end ignores the setting. <!-- src: plugins/bfb-elements/elements/read-more.php:303-313; src/elements/read-more/read-more.js:88-94 -->
- **Server HTML is not clamped.** The clamp rules need `is-ready`, which the inline script adds as the page parses, so a fetch without scripts shows every line. Judge the clamp in a browser. <!-- src: plugins/bfb-elements/elements/read-more.php:329-332; src/elements/read-more/read-more.css:37-45 -->
- **The button holds both labels.** They stack in one cell and crossfade, so its `textContent` reads both and it is as wide as the longer one. Read `aria-expanded` or `is-open` for the state. <!-- src: plugins/bfb-elements/elements/read-more.php:343-348; src/elements/read-more/read-more.css:65-73 -->
- **Labels are plain text.** **Collapsed label** (`labelMore`) and **Expanded label** (`labelLess`) resolve dynamic data and are then escaped, so HTML in them prints as text. <!-- src: plugins/bfb-elements/elements/read-more.php:292-293; plugins/bfb-elements/includes/abstract-element.php:1265-1273 -->
- **The icon turns 180 degrees when open.** Pick one that points down at rest, such as `{"library": "themify", "icon": "ti-angle-down"}`. **Icon position** (`iconPosition`) and **Icon size** (`iconSize`) act only with `icon` set. <!-- src: src/elements/read-more/read-more.css:62-63; plugins/bfb-elements/elements/read-more.php:122-146 -->
- **The content box always clips.** `__content` keeps `overflow: hidden` open or closed, so a child's shadow, focus ring or dropdown past its edge is cut off. <!-- src: src/elements/read-more/read-more.css:22-26 -->
- **The button sits at the start edge.** The root aligns its items to the start; centre or stretch the button with **Align** (`buttonAlign`), which writes `align-self` on the toggle. <!-- src: src/elements/read-more/read-more.css:11-20; plugins/bfb-elements/elements/read-more.php:155-162 -->
- **A background colour goes under `color`.** **Background** (`buttonBackground`) and its hover twin store `{"color": {"hex": "#101828"}}`; a bare `{"hex": "#101828"}` saves but writes no CSS. **Text colour** (`buttonHoverColor`) is a colour control and takes the bare form. <!-- src: measured 2026-10-08: demo-bfb-read-more stores a bare {"hex"} and prints no toggle rule; feature-bfb-read-more-collapse-to-a-few-lines stores {"color": {"hex"}} and prints background-color -->

## Never do

- Do not use `mode: "lines"` for a mix of headings, images and buttons; use `mode: "height"`.
- Do not set `maxHeight` without `mode: "height"`, or `fadeSize` without `fade: true`.
- Do not set `iconPosition` or `iconSize` without `icon`.
- Do not toggle `is-open`, `is-short` or `aria-expanded` from an interaction or another script; only the element's own button keeps the state, the attribute and the motion together.
- Do not put HTML in `labelMore` or `labelLess`.
- Do not judge the clamp from server HTML, or from the canvas in its default Open view.
- Do not target it by `_cssId`; use a class in `_cssClasses`.
- Do not store a `buttonBackground` or `buttonHoverBackground` colour as a bare `{"hex"}`; nest it under `color`.
