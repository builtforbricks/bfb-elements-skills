---
name: bfbe-dark-mode
description: "Use when placing, wiring or styling BFB Dark Mode Toggle (`bfbe-dark-mode`): a button that sets data-bfbe-theme on the html element, remembered in the visitor's browser and following the device setting until a choice is made. Read before writing its settings."
---

# BFB Dark Mode Toggle (`bfbe-dark-mode`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-dark-mode.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/dark-mode/

## What it is
A button that sets data-bfbe-theme on the html element, remembered in the visitor's browser and following the device setting until a choice is made. A script in the head applies the stored choice before the page paints, and it prints on every page once a toggle has rendered anywhere. The Colour the page option can recolor the page for dark, and the bfbe-dark-only and bfbe-light-only classes swap content per scheme.

**Not for:** Everything on the page recolors the stylesheet Bricks wrote for the page and can move color variables other stylesheets set on the root. Their other rules, inline styles, images and translucent colors stay as they are. A design that needs exact dark values in every part fits CSS custom properties or light-dark() better, with Colour the page left off.

**Costs a page:** CSS 1.04 KB, JS 1.56 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Toggle (`bfbeToggle`)
- `mode` (select) **Choices**: options: `two` Light and dark (default), `three` Light, dark and system. Choose Light and dark, the default, or Light, dark and system. The second adds a third press that hands the choice back to the device setting.
- `shape` (select) **Shape**: options: `round` Round (default), `pill` Pill with label, `switch` Switch. Choose Round, the default, Pill with label to show the current choice in words, or Switch for a sliding knob.
- `labelLight` (text) **Light label**: placeholder Light; dynamic data accepted. The word for the light state, Light unless set. It takes dynamic data, as the other two labels do.
- `labelDark` (text) **Dark label**: placeholder Dark; dynamic data accepted. The word for the dark state, Dark unless set.
- `labelSystem` (text) **System label**: placeholder System; dynamic data accepted; only when `mode` is `three`. With three choices, the word for following the device setting, System unless set.

### Icons (`bfbeIcons`)
- `iconLight` (icon) **Light**. Pick any icon from the picker to replace the drawn sun.
- `iconDark` (icon) **Dark**. An icon of your own in place of the drawn moon.
- `iconSystem` (icon) **System**: only when `mode` is `three`. With three choices, an icon of your own in place of the drawn half circle.

### Button (`bfbeLook`)
Styling only, every key in the schema file: `size`, `iconSize`, `backgroundHover`, `colorHover`, `knobColor`, `knobInk`, `labelTypography`, `knobShadow`.

### Dark page (`bfbePage`)
- `pageColors` (checkbox) **Colour the page**. Off by default. Tick it and the dark state recolors every page of the site, once a page with the toggle has loaded. The recolor leaves images, inline styles and see-through colors as they are.
- `pageDepth` (select) **How much**: options: `all` Everything on the page (default), `page` The page background and text; only when `pageColors` is set. Everything on the page, the default, recolors the CSS Bricks writes for the page: light surfaces darken, dark text lightens and brand colors stay. The page background and text sets just the colors below.
- `pageSkip` (textarea) **Leave these alone**: placeholder .logo-bar #brxe-abc123; only when `pageDepth` is not `page`. Type one selector per line, such as .logo-bar. With Everything on the page, rules written for those selectors keep their colors. A block filled with a light brand color keeps its light look anyway.
- `pageBackground` (color) **Background**: only when `pageColors` is set. The page background in the dark state, #121212 unless set.
- `pageText` (color) **Text colour**: only when `pageColors` is set. The page's text color in the dark state, #e6e6e6 unless set.
- `pageHeadings` (color) **Headings colour**: only when `pageColors` is set. The color of headings in the dark state, the Text colour unless set.
- `pageLinks` (color) **Links colour**: only when `pageColors` is set. One color for links in the dark state, Bricks buttons aside. Leave it empty to set none.
- `pageOutline` (color) **Outline buttons colour**: only when `pageColors` is set. The text and border of outline Bricks buttons in the dark state, the Text colour unless set.
- `pageButtonText` (color) **Button text colour**: only when `pageColors` is set. One text color for filled Bricks buttons in the dark state, such as white on a dark brand button. Leave it empty to set none.
- `keepInk` (color) **Kept blocks text colour**: only when `pageColors` is set. The color of text, headings and links in blocks with the class bfbe-keep, #1f1f1f unless set. A block with that class keeps its own background in dark mode, so give it to a block with a light background.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. The curve those changes follow, Snappy unless set.
- `pageFx` (select) **Page transition**: options: `crossfade` Crossfade (default), `reveal` Reveal from the button, `fade` Colours fade, `none` None. Crossfade, the default, dissolves the page between themes. Reveal from the button grows the new theme in a circle from the button. Colours fade eases every color. None cuts at once. Without view transitions, a browser gets Colours fade.
Styling, in the schema file: `duration`, `easingCustom`, `pageFxDuration`.

## What it guarantees for accessibility (do not undo)
- With Light and dark the button is a native button whose aria-pressed is true while the page is dark.
- A visually hidden name reads Theme: Dark with two choices, and Theme followed by the current choice with three.
- Enter and Space press it like any button, and the drawn icons are hidden from assistive technology.
- Under forced colors, such as Windows high contrast, the button takes the system button colors; drawn icons use button text, reversed on the Switch knob.
- Under reduced motion every switch is an immediate cut, with no crossfade, reveal or color fade.
<!-- bfbe:generated:end -->

## Rendered DOM

On the frontend the root is a native `<button type="button">`; the builder canvas draws it as a `<div>`.

```html
<button type="button" class="bfbe-theme bfbe-theme--switch bfbe-theme--two" data-bfbe-mode="two"
  data-bfbe-fx="crossfade" data-bfbe-light="Light" data-bfbe-dark="Dark" data-bfbe-system="System"
  data-bfbe-name="Theme: %s" aria-pressed="false" data-bfbe-state="light">
  <span class="bfbe-theme__knob" aria-hidden="true">
    <svg class="bfbe-theme__icon bfbe-theme__icon--drawn bfbe-theme__icon--light">...</svg>
    <svg class="bfbe-theme__icon bfbe-theme__icon--drawn bfbe-theme__icon--dark">...</svg>
    <!-- a bfbe-theme__icon--system as well with mode "three" -->
  </span>
  <span class="bfbe-theme__label" aria-hidden="true">Light</span>
  <span class="bfbe-sr bfbe-theme__sr">Theme: Dark</span>
</button>
```

- Classes name the shape (`bfbe-theme--round`, `--pill`, `--switch`) and the mode (`bfbe-theme--two`, `--three`). The label is in the markup in every shape; Round and Switch hide it.
- The script sets `data-bfbe-state` (`light`, `dark`, and `system` with three choices) on every `.bfbe-theme` on the page, and the icon for that state shows. With three choices there is no `aria-pressed`; the hidden name reads the current choice.
- A picked icon (`iconLight`, `iconDark`, `iconSystem`) replaces the drawn SVG without the `--drawn` class, so it keeps its own fill and stroke.
- On `<html>`: `data-bfbe-theme="dark"` or `"light"`, absent while the device decides, stored in `localStorage` as `bfbe-theme`. During a switch, `data-bfbe-vt` (Crossfade, Reveal) or `data-bfbe-fading` (Colours fade) sits there briefly.
- In `<head>` on every page once a toggle has rendered on the frontend: `script#bfbe-theme`, `style#bfbe-theme-css` (`color-scheme`, `--bfbe-in-dark`, the per-scheme classes), `style#bfbe-page-css` (the owner's Dark page rules), and `style#bfbe-dark-paint` with **Everything on the page**.
- `size` sets `--bfbe-theme-size` on the root: Round is that square, Switch is 1.85 times as wide. `iconSize` sets `--bfbe-theme-icon`.
- `knobColor` and `knobInk` set `--bfbe-theme-knob` and `--bfbe-theme-knob-ink` (Canvas and CanvasText unless set). `knobShadow` writes the Switch's `.bfbe-theme__knob`, `labelTypography` the Pill's `.bfbe-theme__label`.
- `backgroundHover` and `colorHover` write the root on `:hover` and `:focus-visible`. `duration` and `easing` set `--bfbe-duration` and `--bfbe-ease`; `pageFxDuration` sets `--bfbe-theme-page-dur`, which the script reads.
- The resting colour, background and border have no controls here: set Bricks' Style tab (`_typography`, `_background`, `_border`) on the root.

## Wiring to other elements

- **The owner.** A toggle with **Colour the page** (`pageColors`) rendered on a published page stores its Dark page rules, depth and skip list in site options. It names itself in `bfbe_pro_dark_owner` as `"post id:element id"`, the template's id when it sits in a header or footer template.
- **Every page follows the owner.** The stored rules print in the head of every page, toggle or not. Other toggles leave `pageColors` off: they switch the theme and the owner's palette paints it.
- **Toggles stay in step.** Every `.bfbe-theme` on a page repaints on a change, and the stored choice carries to the next page.
- **Per-scheme content.** Put `bfbe-dark-only` or `bfbe-light-only` in any element's `_cssClasses` (a string, `"bfbe-dark-only"`). The head hides the other scheme's with `display: none`; the Dark Mode fixture pairs two Bricks `image` elements this way.
- **Dark image source.** An `<img>` carrying `data-bfbe-dark-src`, and optionally `data-bfbe-dark-srcset`, swaps its source in the dark. The toggle's script does the swap.
- **Kept blocks.** `bfbe-keep` in a light block's `_cssClasses` keeps the block and everything inside it out of the recolour. Its text takes **Kept blocks text colour** (`keepInk`).
- **By class, never `_cssId`.** These classes are matched on the page itself, so they hold inside component instances, which share ids. **Leave these alone** (`pageSkip`) differs: it matches selector text in Bricks' CSS (Gotchas).
- **Listening.** Each change dispatches `bfbe/theme` on `document` with `detail.preference` (`light`, `dark`, `system`) and `detail.theme` (`light`, `dark`). BFB Dynamic Charts redraws on it and BFB Interactive Cursor reads its ring again.
- **Late markup.** The script scans again after Bricks' AJAX pagination, page load, query result and popup events, so a toggle in a Bricks popup works. `window.bfbeDarkMode()` runs the scan by hand.

## Verified patterns

None of these trees ticks **Colour the page**, so adding one never takes the palette from the site's owner. Add `"pageColors": true` to the one toggle meant to own it. The fixture's navy owner adds `pageBackground` `#0b1220`, `pageText` `#e7dfd0`, and `pageHeadings` and `pageLinks` `#c9a227`.

**A three-choice switch in the brand colour.** From the Dark Mode Toggle demo (`demo-bfb-dark-mode`), where it also carries `pageColors` and owns the palette. Trimmed: its labels, which equal the defaults, and its **Leave these alone** ids, which name blocks on that page.

```json
{
  "name": "bfbe-dark-mode",
  "settings": {
    "shape": "switch",
    "mode": "three",
    "size": "32px",
    "knobColor": { "hex": "#6e44ff" },
    "knobInk": { "hex": "#ffffff" }
  }
}
```

**A round icon button that reveals the new theme.** From the Dark Mode fixture (`fixture-dark-mode`), "Round, reveal from the button", `pageColors` dropped. Round is the default shape; the new theme grows as a circle from the button over 900 ms.

```json
{
  "name": "bfbe-dark-mode",
  "settings": {
    "pageFx": "reveal",
    "pageFxDuration": 900
  }
}
```

**A toggle with its choice in words.** From the Dark Mode fixture's "Pill, no page transition", `pageColors` dropped. Three choices name Light, Dark and System; `pageFx: "none"` cuts at once.

```json
{
  "name": "bfbe-dark-mode",
  "settings": {
    "mode": "three",
    "shape": "pill",
    "pageFx": "none"
  }
}
```

## Gotchas

- **One toggle owns the site's dark palette.** On a page, the `pageColors` toggle that renders ahead of the others writes it and the rest are ignored. Across pages owners take turns, the one rendered last winning. <!-- src: plugins/bfb-elements-pro/elements/dark-mode.php:424-445 --> <!-- src: plugins/bfb-elements-pro/includes/class-dark-mode-head.php:57-64 -->
- **A toggle that colours nothing never clears the palette.** The owner clears it when rendered again unticked, when its page or template is saved without it, or when that post is trashed. <!-- src: plugins/bfb-elements-pro/includes/class-dark-mode-head.php:70-127 -->
- **Drafts, private pages and previews write nothing site-wide.** A toggle there neither sets nor clears the palette, so its Dark page settings show nowhere until the post holding it is published. <!-- src: plugins/bfb-elements-pro/elements/dark-mode.php:434-437 -->
- **A change shows from the next page load.** The head prints the stored palette before the owner renders and stores its new settings, so load a page twice after saving. <!-- src: plugins/bfb-elements-pro/includes/class-dark-mode-head.php:11-15 -->
- **The canvas is a shallower preview.** The recolour does not run in the builder; the toggle prints its own page rules inline, so **Everything on the page** looks like **The page background and text** there. <!-- src: plugins/bfb-elements-pro/includes/class-dark-mode-paint.php:158-162 --> <!-- src: plugins/bfb-elements-pro/elements/dark-mode.php:449 -->
- **No owner, no dark colours.** Without a toggle that colours the page, a switch sets `data-bfbe-theme` and `color-scheme` alone; the site's own variables or `light-dark()` must do the rest. <!-- src: plugins/bfb-elements-pro/includes/class-dark-mode-head.php:149-181 --> <!-- src: docs/elements/dark-mode.md (intro, "The page background and text") -->
- **Leave these alone matches selector text.** Each line is tested as a substring of Bricks' rule selectors, and an element's own colours sit under its id (`#brxe-abc123`). Children with rules of their own still darken, and with **Colour the page** off the field does nothing though the panel shows it. <!-- src: plugins/bfb-elements-pro/includes/class-dark-mode-paint.php:648-652 --> <!-- src: plugins/bfb-elements-pro/elements/dark-mode.php:249, 427-428 -->
- **The recolour leaves some colours as set.** Stylesheets other than Bricks' generated CSS, inline `style` attributes, images, colours under 90% opacity, and declarations using `var()` or `currentColor` keep their light values. <!-- src: plugins/bfb-elements-pro/includes/class-dark-mode-paint.php:16-18, 673, 711-713 -->
- **A light brand fill becomes a light island.** A block filled with a saturated light colour (a yellow, lime or teal card) keeps its fill, and everything inside keeps its light look. White and grey surfaces still go dark; a large light brand section stays bright by design. <!-- src: plugins/bfb-elements-pro/includes/class-dark-mode-paint.php:565-610 --> <!-- src: docs/elements/dark-mode.md "Round 394" -->
- **The page background and text leaves blocks light.** With `pageDepth: "page"` the body, text, headings, links and Bricks buttons change, while a block's own background stays light under text that turns light. Give such a block `bfbe-keep`. <!-- src: plugins/bfb-elements-pro/elements/dark-mode.php:377-409 --> <!-- src: docs/elements/dark-mode.md (intro, "The page background and text") -->
- **A dark image source needs a toggle on the page.** The toggle's script swaps `data-bfbe-dark-src` after the page loads, so a page without a toggle keeps the light image. The `bfbe-dark-only` and `bfbe-light-only` classes work on every page, before it paints. <!-- src: src/elements/dark-mode/dark-mode.js:19-36 --> <!-- src: docs/REVIEW-2026-10-04.md item 21 -->
- **Easing and Duration time the button, not the page.** They drive the icon crossfade and the knob slide. The page transition runs a curve of its own over **Transition duration** (`pageFxDuration`, 500 ms unless set). <!-- src: src/elements/dark-mode/dark-mode.js:79-88 --> <!-- src: docs/elements/dark-mode.md (Motion paragraph) -->

## Never do

- Do not tick **Colour the page** (`pageColors`) on more than one toggle on the site; give the palette to one and leave every other toggle's Dark page keys empty.
- Do not judge the dark design in the builder canvas, a preview or a draft; read the published frontend, loaded twice after a save.
- Do not set `pageSkip` on a toggle without `pageColors`, or on one that is not the owner.
- Do not put `bfbe-keep` on a dark block: its text takes **Kept blocks text colour**, #1f1f1f unless set.
- Do not rely on `data-bfbe-dark-src` on a page without a toggle; pair two images with `bfbe-light-only` and `bfbe-dark-only`.
- Do not add `aria-pressed`, `role` or `tabindex` through `_attributes`; the script owns `aria-pressed`, and three choices leave it off by design.
- Do not use **Easing** or **Duration** to time the page change; set `pageFxDuration`.
