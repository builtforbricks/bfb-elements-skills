---
name: bfbe-advanced-header-scroll
description: "Use for a sticky header that changes as the page scrolls, with BFB Advanced Header Scroll (`advanced-header-scroll`): shrink the header and logo, turn a button to its icon, sit see-through over the hero, hide on the way down and return on the way up. A feature on the header template and the elements inside it, not an element."
---

# BFB Advanced Header Scroll (`advanced-header-scroll`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/advanced-header-scroll.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/advanced-header-scroll/

## What it is
A feature for the header template, not an element of its own. Its Advanced Header Scroll group in the header template's settings, which a page or a content template can override with the page winning, makes the header sticky, or sticky over the first section, and sets when the scrolled state begins, when it hides on the way down and how it moves. Every element inside the header gets a When the page scrolls group on its Style tab, to hide, fade or appear and to restyle itself once the page has scrolled. Nothing in either group acts until Position is Sticky or Sticky, over the first section.

**Not for:** Not for a header placed at the side of the page, which it leaves to Bricks, nor for footers, popups or anything outside the header, which have no scroll states here.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Where it lives
A feature, not an element: its controls are added to the header template's settings, and every element in the header.

## Settings that decide the build

### When the page scrolls (`bfbeOnScroll`)
- `bfbeHsWhen` (select) **When scrolled**: options: `hide` Hides, `fade` Fades out, keeps its space, `show` Appears only then. Choose what the element does once the page scrolls. Hides closes it up. Fades out, keeps its space leaves a gap. Appears only then keeps it hidden until the page scrolls.
- `bfbeHsCollapse` (select) **Collapses**: options: `across` Sideways; only when `bfbeHsWhen` is `hide` or `show`. For Hides and Appears only then. The element shrinks downward by default. Choose Sideways to shrink its width instead, which suits an element in a row.
- `bfbeHsOver` (select) **Over the first section**: options: `hide` Hides, `show` Appears only then. Hides hides the element while the header sits over the first section. Appears only then hides it the rest of the time. It needs Position set to Sticky, over the first section.
- `bfbeHsIconOnly` (checkbox) **Keep only the icon**. Tick it on a Button that has an icon. Once the page scrolls the words go and the icon stays. The button keeps its name.
- `bfbeHsElEasing` (select) **Easing**: options: `cubic-bezier(0.16, 1, 0.3, 1)` Snappy; writes CSS
Styling, in the schema file: `bfbeHsPadding`, `bfbeHsMargin`, `bfbeHsWidth`, `bfbeHsHeight`, `bfbeHsBackground`, `bfbeHsBlur`, `bfbeHsBorder`, `bfbeHsShadow`, `bfbeHsTypography`, `bfbeHsOpacity`, `bfbeHsScale`, `bfbeHsGap`, `bfbeHsOverBackground`, `bfbeHsOverTypography`, `bfbeHsOverBorder`, `bfbeHsOverShadow`, `bfbeHsOverOpacity`, `bfbeHsIconSize`, `bfbeHsElDuration`, `bfbeHsDelay`.

### bfbeHeaderScroll (`bfbeHeaderScroll`)
- `bfbeHsPosition` (select) **Position**: options: `sticky` Sticky, `over` Sticky, over the first section, `off` Off. Pick Sticky, or Sticky, over the first section, to replace the Bricks sticky header. Off turns this feature off, even on a page whose header template has it on.
- `bfbeHsFrom` (select) **From this width**: options: `992` 992px and wider (above Tablet portrait), `768` 768px and wider (above Mobile landscape), `479` 479px and wider (above Mobile portrait); only when `bfbeHsPosition` is `sticky` or `over`. Pick one of your site's breakpoints. Below it the header neither sticks nor sits over the first section, nothing in it changes on scroll, and an element set to Appears only then stays hidden. Always is the default.
- `bfbeHsBegin` (select) **The scrolled state begins**: options: `px` After a distance, `first` When the first section has left; only when `bfbeHsPosition` is `sticky` or `over`. Choose when the header counts as scrolled. By default that is once the page passes the header's own height. Pick After a distance, or When the first section has left, to change it.
- `bfbeHsAt` (number) **Distance (px)**: placeholder 300; only when `bfbeHsPosition` is `sticky` or `over` and `bfbeHsBegin` is `px`. For After a distance. The header counts as scrolled once the page has moved this many pixels. Before that, once the page passes its own height, the header waits out of view. 300 is the default.
- `bfbeHsHide` (number) **After (px)**: placeholder Never hides; only when `bfbeHsPosition` is `sticky` or `over`. Enter a number to hide the header when visitors scroll down. It hides that many pixels after the scrolled state begins and returns when they scroll up. Empty means never.
- `bfbeHsTolerance` (number) **Tolerance (px)**: placeholder 8; only when `bfbeHsPosition` is `sticky` or `over` and `bfbeHsHide` is set. How far visitors must scroll one way before the header hides or returns. 8 is the default, so a small wobble does nothing.
- `bfbeHsHideFx` (select) **Effect**: options: `fade` Fade; only when `bfbeHsPosition` is `sticky` or `over` and `bfbeHsHide` is set. Choose how the header hides. It slides up by default. Pick Fade to fade it out instead.
- `bfbeHsDuration` (number) **Duration**: placeholder 250; only when `bfbeHsPosition` is `sticky` or `over`. Milliseconds; every element inherits it.
- `bfbeHsEasing` (select) **Easing**: options: `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default); only when `bfbeHsPosition` is `sticky` or `over`
- `bfbeHsAnchors` (select) **In-page links land**: options: `under` Under the header, as Bricks does; only when `bfbeHsPosition` is `sticky` or `over`. By default a link to a section stops below the header. Choose Under the header, as Bricks does, to let it land behind the header.
- `bfbeHsZ` (number) **z-index**: placeholder 998; only when `bfbeHsPosition` is `sticky` or `over`. Raise it if something else on the page covers the header. 998 is the default.
- `bfbeHsPreview` (select) **Preview in the builder**: options: `top` At rest, `scrolled` Scrolled, `hidden` Hidden, `over` Over the first section; writes CSS; only when `bfbeHsPosition` is `sticky` or `over`. Pick At rest, Scrolled, Hidden or Over the first section to see that state on the canvas. By default it shows everything, for editing. The page never sees it.

## What it guarantees for accessibility (do not undo)
- The header does not hide on the way down while keyboard focus is inside it, while a menu inside it is open, while the body carries the no-scroll class, or while the pointer is within 12 px of the top of the window.
- Tabbing into a header that has slid away brings it back, because focus inside the header ends the hidden state. A header hidden with Fade has visibility hidden, so it is out of the tab order until it returns.
- An element that has hidden or faded out gets visibility hidden and no pointer events, so it leaves the tab order and cannot be clicked; Hides and Appears only then also use display none where the browser supports it.
- In-page links land below the header unless In-page links land is set to Under the header, as Bricks does.
- With reduced motion requested, the header and every element carrying a setting here change state at once, with no transition and no delay.
- Keep only the icon sizes the button's words to zero instead of removing them, so the button keeps its name.
<!-- bfbe:generated:end -->

## Rendered DOM

The feature draws nothing of its own. It adds classes, data attributes and custom properties to Bricks' `<header id="brx-header">` and to each element inside it that carries a `bfbeHs*` setting (a marked element).

```html
<header id="brx-header" class="bfbe-hs bfbe-hs--anchors bfbe-hs--scrolled" data-bfbe-hs-begin="own"
        data-bfbe-hs-hide="480" data-bfbe-hs-tolerance="8" style="--bfbe-hs-dur:300;--bfbe-hs-ease:...;--bfbe-hs-rest:...">
  <section class="brxe-section bfbe-hs--scrolled" data-bfbe-hs="blur">...
    <a class="brxe-logo bfbe-hs--scrolled" data-bfbe-hs="styled lh" data-bfbe-hs-inverse="https://example.com/logo-inverse.png"><img class="bricks-site-logo" ...></a>
    <a class="brxe-button bfbe-hs--scrolled" data-bfbe-hs="icon"><i class="ti-calendar"></i>Book an eye test</a>
```

- **On the header**: `bfbe-hs` while **Position** is on, `bfbe-hs--over-on` with `"over"`, `bfbe-hs--anchors` unless **In-page links land** is `"under"`. Bricks' `brx-sticky`, `on-scroll` and `data-slide-up-after` are taken off.
- **Its configuration**: `data-bfbe-hs-begin` (`own`, `px`, `first`), `data-bfbe-hs-at` (with `px`), `data-bfbe-hs-from`, `data-bfbe-hs-hide` with `data-bfbe-hs-tolerance` and `data-bfbe-hs-fx="fade"`, and `data-bfbe-hs-preview` in the canvas alone. Duration, Easing and z-index ride an inline style as `--bfbe-hs-dur` (bare milliseconds), `--bfbe-hs-ease`, `--bfbe-hs-z`.
- **States**, set by the script on the header and every marked element: `bfbe-hs--top`, `--scrolled`, `--hidden`, `--over` (at rest over the first section), `--away` (between the header's height and **Distance (px)**, out of view with no motion), `--edit` (the canvas with no preview). Below **From this width** none is set and the header gets `bfbe-hs--off`.
- **The marker** `data-bfbe-hs` lists tokens: `hide`, `fade`, `show`, `across`, `over-hide`, `over-show`, `blur`, `icon`, else `styled`; a Logo adds `lh` or `lw`. A Logo with **Logo inverse** carries `data-bfbe-hs-inverse`, and its `<img>` takes that `src` while scrolled.
- **Measured by the script**: `--bfbe-hs-rest`, the rest height the header box keeps as its `min-block-size`, and `--bfbe-header-h` on the header; the compact height as `--bfbe-header-h` on `<html>`, which `scroll-padding-block-start` reads; `--bfbe-hs-h`, `--bfbe-hs-w`, `--bfbe-hs-gs`, `--bfbe-hs-ge` on each collapsing element.
- **The header's CSS**: `position: sticky`, never fixed, its `top` 0 or the admin bar's height (0 again below 600px). Hidden is `translate: 0 -100%`, or `opacity: 0; visibility: hidden` with Fade. Over is a negative `margin-block-end` of the rest height. Scrolled, the header box lets clicks through and its children take them.
- **Where the controls write**: each styling control under `#brxe-<id>.bfbe-hs--scrolled`, the five Over ones under `.bfbe-hs--over`, a Logo's Width and Height on its `.bricks-site-logo`. Blur behind, Icon size then and the element's Duration, Easing and Delay set `--bfbe-hs-blur`, `--bfbe-hs-icon`, `--bfbe-hs-dur`, `--bfbe-hs-ease`, `--bfbe-hs-delay` on the element. **Preview in the builder** writes `--bfbe-hs-preview` on `#brx-header`.

## Wiring to other elements

- **The header template carries the header group.** Write it with `bricks/set-template-settings` on the header template. A page overrides any key with `bricks/set-page-settings`, a content template with `bricks/set-template-settings`; the page wins, then the content template. `bfbeHsPosition: "off"` on a page turns the feature off there.
- **Elements carry the When the page scrolls group.** Any element in the header template, Bricks' own or the pack's, takes `bfbeHsWhen` and the rest through `bricks/add-element` or `bricks/update-element` with the template's id as `postId`. Nothing points at anything: the script finds `#brx-header` and the `[data-bfbe-hs]` elements inside it.
- **Custom CSS by state**: reach an element through a class in `_cssClasses` under the header's state, `#brx-header.bfbe-hs--scrolled .my-cta`, never through `_cssId`, because component instances share ids.
- **Logo**: its own **Logo inverse** (`logoInverse`) is shown while scrolled, as Bricks does for its sticky header.
- **Button**: **Keep only the icon** (`bfbeHsIconOnly`) leaves the button's own `icon` showing; its words stay in the markup.
- **Menus and off-canvas in the header**: Bricks' `.brx-open`, any `aria-expanded="true"` inside the header and `no-scroll` on `<body>` keep the header from hiding. A custom toggle must set `aria-expanded` to count.
- **In-page links** land below the compact header through `scroll-padding-block-start` on `<html>`; `bfbeHsAnchors: "under"` removes it.
- **Scripts**: `window.bfbeHeaderScroll()` sets the feature up again, for a header a script has replaced. The builder re-runs it after every element render.

## Verified patterns

**Sticky, steps aside on the way down.** The header template settings of the demo "ZZ demo: Advanced Header Scroll". They go on the header template through `bricks/set-template-settings`, not into an element tree, so the check parses this block and renders nothing.

```json
{ "bfbeHsPosition": "sticky", "bfbeHsHide": 480, "bfbeHsTolerance": 8, "bfbeHsDuration": 300, "bfbeHsEasing": "cubic-bezier(0.16, 1, 0.3, 1)" }
```

The demo "Kestrel Optical: Advanced Header Scroll" sits over its hero and turns solid once the hero has gone: `{"bfbeHsPosition": "over", "bfbeHsBegin": "first", "bfbeHsHide": 1200}`. One page alone overrides through `bricks/set-page-settings`, as the feature page "Transparent over the top section" does with `{"bfbeHsPosition": "over"}`.

**A header that tightens into glass.** The same demo's header, its top-level section added with `bricks/add-element` and the header template's id as `postId`. Scrolled, the padding halves, the section turns translucent with blur and a shadow, the logo shrinks a beat late, the nav's gap tightens and takes the accent, and the button keeps its calendar icon. Trimmed to two links. The ids 50108 and 50109 are the demo site's attachments and the `example.com` URLs stand in for its files: use the target site's own logo attachments.

```json
{
  "name": "section",
  "settings": {
    "_background": { "color": { "hex": "#ffffff", "rgb": "rgba(255, 255, 255, 1)" } },
    "_padding": { "top": "18", "right": "20", "bottom": "18", "left": "20" },
    "_border": { "width": { "bottom": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" } },
    "bfbeHsPadding": { "top": "9", "right": "20", "bottom": "9", "left": "20" },
    "bfbeHsBackground": { "color": { "hex": "#ffffff", "rgb": "rgba(255, 255, 255, 0.86)" } },
    "bfbeHsBlur": "12px",
    "bfbeHsShadow": { "values": { "offsetX": 0, "offsetY": 10, "blur": 30, "spread": -18 }, "color": { "hex": "#101828", "rgb": "rgba(16, 24, 40, 0.3)" } }
  },
  "children": [ { "name": "container", "settings": { "_width": "1140px", "_rowGap": "0px", "_alignItems": "stretch" }, "children": [
    { "name": "block", "settings": { "_direction": "row", "_justifyContent": "space-between", "_alignItems": "center", "_flexWrap": "nowrap", "_columnGap": "32px" }, "children": [
      { "name": "logo", "settings": {
        "logo": { "id": 50108, "size": "full", "url": "https://example.com/wp-content/uploads/kestrel-logo.png" },
        "logoInverse": { "id": 50109, "size": "full", "url": "https://example.com/wp-content/uploads/kestrel-logo-inverse.png" },
        "logoHeight": "40px", "logoWidth": "180px", "_flexShrink": "0", "bfbeHsHeight": "28px", "bfbeHsDelay": 60 } },
      { "name": "block", "settings": { "_direction": "row", "_alignItems": "center", "_columnGap": "36px", "_typography": { "color": { "hex": "#101828" } },
        "bfbeHsGap": "24px", "bfbeHsTypography": { "color": { "hex": "#6e44ff" } } }, "children": [
        { "name": "text-link", "settings": { "text": "Frames", "link": { "type": "external", "url": "#frames" } } },
        { "name": "text-link", "settings": { "text": "Lenses", "link": { "type": "external", "url": "#lenses" } } } ] },
      { "name": "button", "settings": { "text": "Book an eye test", "link": { "type": "external", "url": "#visits" },
        "icon": { "library": "themify", "icon": "ti-calendar" }, "iconPosition": "left", "_flexShrink": "0",
        "_padding": { "top": "11", "right": "20", "bottom": "11", "left": "20" }, "_border": { "radius": { "top": 999, "right": 999, "bottom": 999, "left": 999 } },
        "bfbeHsIconOnly": true, "bfbeHsIconSize": "20px", "bfbeHsPadding": { "top": "10", "right": "11", "bottom": "10", "left": "11" } } }
    ] } ] } ]
}
```

**A top row that folds away and an offer that comes in.** The fixture "PRO: Advanced Header Scroll (probe)", the header the feature's browser probe measures, trimmed of its logo and nav and of the top row's dark fill: put yours before the Actions block. The top row collapses downward in the container's column; the offer appears sideways in its row, and the button after it keeps its icon. Its template settings are `{"bfbeHsPosition": "sticky", "bfbeHsFrom": "768", "bfbeHsHide": 400}`, so below 768px the offer stays hidden.

```json
{
  "name": "section",
  "settings": { "_padding": { "top": "14", "bottom": "18" }, "bfbeHsPadding": { "top": "8", "bottom": "8" } },
  "children": [ { "name": "container", "settings": { "_rowGap": "0px", "_alignItems": "stretch" }, "children": [
    { "name": "block", "settings": { "_direction": "row", "_justifyContent": "space-between", "_alignItems": "center", "_margin": { "bottom": "14" }, "bfbeHsWhen": "hide" }, "children": [
      { "name": "text-basic", "settings": { "text": "Free fitting on every frame, in store and at home" } },
      { "name": "text-basic", "settings": { "text": "Call 020 7946 0000, Monday to Saturday" } } ] },
    { "name": "block", "settings": { "_direction": "row", "_justifyContent": "space-between", "_alignItems": "center", "_flexWrap": "nowrap", "_columnGap": "32px" }, "children": [
      { "name": "block", "settings": { "_direction": "row", "_alignItems": "center", "_columnGap": "12px" }, "children": [
        { "name": "button", "settings": { "text": "Get 10% off", "size": "sm", "bfbeHsWhen": "show", "bfbeHsCollapse": "across" } },
        { "name": "button", "settings": { "text": "Book a call", "icon": { "library": "themify", "icon": "ti-calendar" }, "iconPosition": "left",
          "bfbeHsIconOnly": true, "bfbeHsIconSize": "20px", "bfbeHsPadding": { "top": "10", "right": "12", "bottom": "10", "left": "12" } } } ] }
    ] } ] } ]
}
```

## Gotchas

- **Nothing acts until Position is set.** With `bfbeHsPosition` empty or `"off"`, or the template's **Header location** (`headerPosition`) at a side, no element is marked and every element setting here does nothing on the page. <!-- src: plugins/bfb-elements-pro/includes/class-header-scroll.php:500-511,654-659 -->
- **The header's keys and an element's keys differ.** `bfbeHsDuration` and `bfbeHsEasing` belong to the template; an element's own are `bfbeHsElDuration` and `bfbeHsElEasing`. A template key written on an element only marks it. <!-- src: plugins/bfb-elements-pro/includes/class-header-scroll.php:233-252,403-422,616-623 -->
- **Bricks' own sticky header stops applying.** While Position is on, the header loses `brx-sticky`, so **Sticky header**, **Slide up after** and Bricks' scrolling colour, background and shadow (`headerStickyScrolling*`) do nothing. <!-- src: plugins/bfb-elements-pro/includes/class-header-scroll.php:523-525; themes/bricks/includes/frontend.php:1119-1137 and includes/settings/settings-template.php:158-170 (Bricks 2.3.10) -->
- **States reach marked elements inside the header only.** An element with no `bfbeHs*` setting, or with only Duration, Easing or Delay, or outside the header template, never gets `bfbe-hs--scrolled`. Style it from `#brx-header.bfbe-hs--scrolled`. <!-- src: src/elements/header-scroll/header-scroll.js:55,161-168; plugins/bfb-elements-pro/includes/class-header-scroll.php:616-623 -->
- **Over the first section needs `"over"` and pulls the page up.** `bfbeHsOver` and the five `bfbeHsOver*` styles act only with that Position. The header's rest height becomes a negative bottom margin, so the first section needs at least that much top padding; at rest the header's top-level elements are transparent. With `bfbeHsBegin: "first"` the threshold is the foot of the first child of `#brx-content`. <!-- src: src/elements/header-scroll/header-scroll.css:47-51,101; src/elements/header-scroll/header-scroll.js:48,51,140,156; dev/demo/header-shop.php:84 -->
- **A Logo needs attachment ids and one scrolled size.** Bricks' Logo draws from `logo.id` and the swap reads `logoInverse.id`; a URL alone draws the site name. `bfbeHsHeight` and `bfbeHsWidth` go to the image and set the other side to `auto`; with both set Height wins, and a rest `logoHeight` keeps the proportions while it animates. <!-- src: themes/bricks/includes/elements/logo.php:111-185 (Bricks 2.3.10); plugins/bfb-elements-pro/includes/class-header-scroll.php:185-192,624-645; src/elements/header-scroll/header-scroll.css:79-89 -->
- **`auto` never animates, so shrink a button by padding.** A scrolled Width on a button sized by its words jumped 62px in one frame. Use `bfbeHsPadding` with `bfbeHsIconOnly`, which is offered on Bricks' Button alone and needs its `icon`; without one the words go and an empty box is left. <!-- src: docs/elements/header-scroll.md "Traps" (`auto` never animates); plugins/bfb-elements-pro/includes/class-header-scroll.php:216-231; src/elements/header-scroll/header-scroll.css:163-165 -->
- **Delay is for the way in, and a delayed element moves its neighbours twice.** `bfbeHsDelay` applies when scrolling down only. A delayed button in a row whose padding also changed slid its neighbours 93px one way, then 160px back. <!-- src: docs/elements/header-scroll.md "Traps" (rounds 381, 382); src/elements/header-scroll/header-scroll.css:70-76 -->
- **Collapse along the parent's direction.** The parent's gap closes with the element when the collapse matches a flex parent: Downward (the default) in a column, `bfbeHsCollapse: "across"` in a row. A Sideways element stays on one line and is clipped. A browser without `transition-behavior: allow-discrete` keeps the collapsed box and its gap. <!-- src: src/elements/header-scroll/header-scroll.js:57-75; src/elements/header-scroll/header-scroll.css:91-95,131-155 -->
- **Durations and delays are bare milliseconds.** Bricks writes `bfbeHsElDuration` and `bfbeHsDelay` as given and the stylesheet multiplies them by `1ms`, so `"300ms"` drops the duration or delay to zero. A template `bfbeHsDuration` with a unit is ignored and 250 applies. <!-- src: src/elements/header-scroll/header-scroll.css:26-29,62-76; plugins/bfb-elements-pro/includes/class-header-scroll.php:234-264,563-566; themes/bricks/includes/assets.php:2988-3000 (Bricks 2.3.10, a number control with no units is written as given) -->
- **The canvas shows everything by default.** With no `bfbeHsPreview` every element stays expanded in the builder, an Appears only then element included; check the page itself. `bfbeHsFrom` offers the site's own breakpoints plus 1px (992, 768 and 479 on the demo site). <!-- src: src/elements/header-scroll/header-scroll.js:130-134; src/elements/header-scroll/header-scroll.css:96-101; plugins/bfb-elements-pro/includes/class-header-scroll.php:321-334 -->

## Never do

- Do not write `bfbeHsPosition` or any other header key into an element; set it with `bricks/set-template-settings`, or `bricks/set-page-settings` for one page.
- Do not give elements `bfbeHs*` settings while `bfbeHsPosition` is empty or `"off"`, or the template has a `headerPosition`.
- Do not set Bricks' `headerSticky`, `headerStickySlideUpAfter` or `headerStickyScrolling*` on a header this feature runs.
- Do not set `bfbeHsOver` or a `bfbeHsOver*` style unless the page's Position is `"over"`.
- Do not set both `bfbeHsWidth` and `bfbeHsHeight` on a Logo.
- Do not give a button a scrolled `bfbeHsWidth`; use `bfbeHsPadding` with `bfbeHsIconOnly`.
- Do not empty a Button's `text` to make it an icon; `bfbeHsIconOnly` keeps its accessible name.
- Do not write units into `bfbeHsElDuration`, `bfbeHsDelay` or `bfbeHsDuration`.
