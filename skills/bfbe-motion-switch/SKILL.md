---
name: bfbe-motion-switch
description: "Use when adding a switch or button that pauses the page's animations, autoplay and videos for visitors, remembered across pages, with BFB Motion Switch (`bfbe-motion-switch`). Read before writing its settings."
---

# BFB Motion Switch (`bfbe-motion-switch`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 2.0.0 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-motion-switch.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/motion-switch/

## What it is
A switch the visitor presses to pause the page's motion: the pack's own animations, Bricks' animations and videos that play by themselves, on this page and every page after, until they press it again. It starts pressed for a visitor whose device asks for reduced motion, and the choice is applied before the page is drawn. Free, on any site, shop or not.

**Not for:** It does not stop a YouTube or Vimeo embed, Bricks' sliders' autoplay, other plugins' CSS animations or scrolling effects. Behind a page cache, add the bfbe_motion_switch_everywhere filter so every page applies the choice.

**Costs a page:** CSS 0.56 KB, JS 0.91 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Switch (`bfbeMotion`)
- `text` (text) **Text**: placeholder Pause animations; dynamic data accepted. "Pause animations" unless you set it; dynamic data works. The words say what pressing does, and the pressed state is said with them.
- `look` (select) **Look**: options: `switch` Switch (default), `button` Button. Switch by default, a track with a knob before the words, filled with the accent when pressed; or Button, the words in a pill, ringed when pressed.

### Look (`bfbeMotionLook`)
Styling only, every key in the schema file: `trackOn`, `trackOff`, `knob`, `trackWidth`, `trackBorder`, `pressedBackground`, `pressedColor`, `pressedBorder`, `gap`.

## What it guarantees for accessibility (do not undo)
- A real button with aria-pressed: a screen reader hears "Pause animations, toggle button, pressed".
- It starts from the device's reduced-motion setting, and a device set to reduce motion keeps the pack's own elements still whatever the switch says.
- Without JavaScript nothing can be paused, so the switch is sent hidden and shown by its own script.
- Pressing it in the builder does nothing, so the canvas keeps its motion while you design.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<button id="brxe-{id}" class="brxe-bfbe-motion-switch bfbe-motion bfbe-motion--switch" aria-pressed="false" data-bfbe-motion type="button" hidden>
  <script>/* reads the stored choice, sets aria-pressed, removes hidden */</script>
  <span class="bfbe-motion__track" aria-hidden="true"><span class="bfbe-motion__knob"></span></span> <!-- switch look only -->
  <span class="bfbe-motion__text">Pause animations</span>
</button>
```

- The root is a real `button` with `aria-pressed`, sent `hidden`; its own inline script sets the state and shows it before it is drawn. In the canvas the root is a `div`, never hidden and never pressed.
- **Look** `look: "switch"` (default) draws the track and knob before the words; `button` drops them and adds `bfbe-motion--button`: a pill with a line, ringed (`border-color: currentColor` and an inset shadow) when pressed.
- Paused, `html` carries `bfbe-motion-off`, every `[data-bfbe-motion]` on the page reads `aria-pressed="true"`, and `document` gets `bfbe:motion` with `detail.paused`. The pack's duration tokens go to zero under that class as under reduced motion.
- The head snippet, at `wp_head` priority 1 before any stylesheet: `<script id="bfbe-motion">` (applies the choice, holds videos that start by themselves) and `<style id="bfbe-motion-css">` (ends `.brx-animated` in 1ms, as Bricks' own reduced-motion rule does).
- Where the Look controls write: `trackOn`, `trackOff`, `knob`, `trackWidth` to `--bfbe-motion-on`, `--bfbe-motion-track`, `--bfbe-motion-knob`, `--bfbe-motion-w` on the root (the track's height is the width divided by 1.8); `trackBorder` to `.bfbe-motion__track`, replacing its drawn line; `pressedBackground`, `pressedColor`, `pressedBorder` to the root's `[aria-pressed="true"]`; `gap` to the root.
- Bricks' Style tab styles the root at rest: type, spacing, the button look's background and border.
- The choice is kept as `localStorage` `bfbe_motion` (`off` or `on`, kind "needed", no consent asked) and a cookie `bfbe_motion=1` for a year, which tells the server to print the head snippet.

## Wiring to other elements

- Nothing targets it and it names nothing: it acts on the whole page through `html.bfbe-motion-off`. Every switch on a page agrees, other tabs follow through the `storage` event, and a switch in a popup or a page loaded by Bricks' AJAX is set up on Bricks' `bricks/ajax/popup/loaded` and `bricks/ajax/load_page/completed`.
- **What it pauses**: the pack's own durations; BFB Marquee (a still row), Text Rotator (holds its word), Lottie that plays by itself, Snap Slider and Content Timeline autoplay, the 3D View's own turn; Bricks' entrance animations and interaction animations; Bricks' Video, video backgrounds and BFB Video Player autoplay. Pressed again, they move again.
- **A script of your own** stops while `document.documentElement.classList.contains('bfbe-motion-off')` or `matchMedia('(prefers-reduced-motion: reduce)').matches`, and checks again on `bfbe:motion`. CSS reads `html.bfbe-motion-off` beside its reduced-motion rules.
- **Where to place it**: the header or footer template, so every page has it and the head snippet sees it.
- For your own CSS give it a class in `_cssClasses`, never `_cssId`: component instances share ids.

## Verified patterns

**A small switch in the header's utility row.** From the demo shop's header template (`dev/demo/shop/10-templates.php`, "Motion switch", the 2.4 site). The accent fills the track when pressed; a narrower track and gap suit a row of small text. Trimmed: the demo's type.

```json
{
  "name": "bfbe-motion-switch",
  "settings": { "text": "Pause animations", "trackOn": { "hex": "#6e44ff" }, "trackOff": { "hex": "#e9ecf1" }, "knob": { "hex": "#ffffff" }, "trackWidth": "34", "gap": "8" }
}
```

**The button look with its pressed state.** From the fixture `fixture-shop-motion` (the P10 probe reads its pressed colours). Pressed, it takes a dark fill, white words and a border in place of the drawn ring.

```json
{
  "name": "bfbe-motion-switch",
  "settings": {
    "look": "button", "text": "Pause the motion",
    "pressedBackground": { "hex": "#101828" }, "pressedColor": { "hex": "#ffffff" },
    "pressedBorder": { "width": { "top": "3", "right": "3", "bottom": "3", "left": "3" }, "style": "solid", "color": { "hex": "#c80000" } },
    "_cssClasses": "p10-motion-b"
  }
}
```

**A switch with its own track line.** From the same fixture. **Track border** replaces the thin drawn line, corners included.

```json
{
  "name": "bfbe-motion-switch",
  "settings": { "trackBorder": { "width": { "top": "2", "right": "2", "bottom": "2", "left": "2" }, "style": "solid", "color": { "hex": "#0a7a3d" } }, "_cssClasses": "p10-motion" }
}
```

## Gotchas

- **No JavaScript, no switch.** It is sent `hidden` and shown by its own script, since nothing can be paused without one; the device's reduced-motion setting still acts through CSS. <!-- src: plugins/bfb-elements/elements/motion-switch.php:211-220 --> <!-- src: docs/elements/motion-switch.md "What works without JavaScript" -->
- **The canvas never pauses.** The canvas switch is drawn unpressed and a press there does nothing, so the pressed look (`trackOn`, the `pressed*` keys) shows only on the page. <!-- src: src/elements/motion-switch/motion-switch.js:56 --> <!-- src: plugins/bfb-elements/elements/motion-switch.php:200-214 -->
- **It starts from the device.** With no choice yet it is pressed for a device that asks for reduced motion. On such a device the pack's own elements stay still whatever the switch says; pressing it only lets Bricks' animations and the videos move. <!-- src: plugins/bfb-elements/elements/motion-switch.php:51 --> <!-- src: docs/elements/motion-switch.md "What a press pauses" -->
- **The head snippet looks in three places.** It prints on a page whose Bricks header, content or footer holds a switch at the top level, and on every page of a browser with the cookie. A switch only inside a popup, a component or a nested template applies the choice just before it is drawn. <!-- src: plugins/bfb-elements/elements/motion-switch.php:241-262 -->
- **Behind a page cache the cookie is not seen.** A cached page without a switch keeps its motion until the visitor reaches one; add `add_filter( 'bfbe_motion_switch_everywhere', '__return_true' );` to print the snippet on every page. <!-- src: plugins/bfb-elements/elements/motion-switch.php:235-243 --> <!-- src: docs/elements/motion-switch.md "Behind a page cache" -->
- **The Look keys split by look.** `trackOn`, `trackOff`, `knob`, `trackWidth` and `trackBorder` are offered only when `look` is not `button`; `pressedBackground`, `pressedColor` and `pressedBorder` only with `look: "button"`. `gap` serves both. <!-- src: plugins/bfb-elements/elements/motion-switch.php:101-194 -->
- **Some motion is beyond it.** It does not stop YouTube or Vimeo embeds that play by themselves, Bricks' sliders' autoplay, other plugins' CSS animations or scrolling effects. <!-- src: docs/elements/motion-switch.md "What it does not do" -->
- **Some of the pack follows the device only.** Charts' drawing, Business Hours' pulse, the Cursor, Hover effects, Flip Box, the Toast's timing bar, the Page Loader and the scroll-linked elements ignore the switch. <!-- src: docs/elements/motion-switch.md "What it does not do" -->
- **A press is site-wide and lasting.** The choice holds on every later page for a year, in this browser only; a video the visitor starts with a press still plays. <!-- src: src/elements/motion-switch/motion-switch.js:23-26 --> <!-- src: src/elements/motion-switch/motion-switch.js:70-73 -->

## Never do

- Do not set `trackOn`, `trackOff`, `knob`, `trackWidth` or `trackBorder` with `look: "button"`, or the `pressed*` keys without it.
- Do not judge the pressed look in the canvas; check it on the page.
- Do not place the only switch in a popup, a component or a nested template; put it in the header or footer template.
- Do not serve a cached site with the switch on some pages only without the `bfbe_motion_switch_everywhere` filter.
- Do not promise it stops YouTube or Vimeo embeds or Bricks' slider autoplay.
- Do not target it by `_cssId`; give it a class.
