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

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
