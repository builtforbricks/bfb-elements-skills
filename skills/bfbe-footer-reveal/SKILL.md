---
name: bfbe-footer-reveal
description: "Use for a footer that waits behind the page, uncovered as the page lifts away at the end, with BFB Footer reveal (`footer-reveal`): turn it on in the footer template, keep it to wider screens, set the shadow and the page's colour, or turn it off on one page. A feature on the footer template, not an element."
---

# BFB Footer reveal (`footer-reveal`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.2.0 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/footer-reveal.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/footer-reveal/

## What it is
A feature for the footer template, not an element of its own: the Footer reveal group in the footer template's settings makes the footer wait behind the page, and the page lifts away at the end to uncover it. A page or a content template can turn it off for itself. Keyboard focus and links into the footer bring it into view, and a footer taller than the window, a visitor who asks for reduced motion and a page without its script all get an ordinary footer.

**Not for:** Needs a Bricks footer template: it does nothing to a theme's own footer. A footer taller than the window, and a visitor who asks for reduced motion, get an ordinary footer by design. It moves the page, not the footer: the footer itself does not animate.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Where it lives
A feature, not an element: its controls are added to the footer template's settings (`bfbeFr*`), with `bfbeFrOff` in the settings of a page or a content template.

## Settings that decide the build

### Footer reveal (`bfbeFooterReveal`)
- `bfbeFrOn` (checkbox) **Reveal the footer**. Tick it and the footer waits behind the page, which lifts away at the end to uncover it.
- `bfbeFrFrom` (select) **From this width**: options: `992` 992px and wider (above Tablet portrait), `768` 768px and wider (above Mobile landscape), `479` 479px and wider (above Mobile portrait); only when `bfbeFrOn` is set. Pick one of your site's breakpoints to keep the reveal to that width and wider. Below it the footer is an ordinary footer. Always is the default.
- `bfbeFrShadow` (select) **Shadow on the page's edge**: options: `strong` Strong, `none` None; only when `bfbeFrOn` is set. The shadow the lifting page casts on the footer. Soft is the default; pick Strong or None.
- `bfbeFrPage` (color) **Page colour**: only when `bfbeFrOn` is set. The colour of the page as it lifts away. Unset, it is the page's own background. Keep it opaque, or the footer shows through.
- `bfbeFrOff` (checkbox) **Off on this page**. In a page's or a content template's settings, tick it to give that page an ordinary footer, whatever the footer template says.

## What it guarantees for accessibility (do not undo)
- Moving keyboard focus into the footer brings the page to its end, so the focused link is in view.
- Following a link to something in the footer uncovers it the same way.
- A footer taller than the window stays an ordinary footer, since its top could not be reached.
- A visitor who asks for reduced motion gets an ordinary footer.
- Without its script, blocked or not yet run, the footer is ordinary: CSS alone never hides it.
<!-- bfbe:generated:end -->

## Rendered DOM

The feature draws nothing of its own. The server marks Bricks' footer and loads two files; the script then decides, on the visitor's screen, whether the reveal runs, and says so with classes on `<html>`. The demo's footer, with Reveal the footer ticked and nothing else set:

```html
<main id="brx-content">...</main>
<footer id="brx-footer" data-bfbe-fr="">...</footer>
```

- **On the footer**: `data-bfbe-fr` (empty) when it is on for this page, `data-bfbe-fr-from` (a width in px, from **From this width**), `data-bfbe-fr-shadow` (`strong` or `none`; Soft writes nothing), `data-bfbe-fr-page` (the **Page colour** as CSS). Nothing is written in the builder, nor on a page with **Off on this page**.
- **Files**: `bfbe-footer-reveal` (0.23 KB CSS, 0.84 KB JS, gzipped) on pages whose footer has it on, nothing on others.
- **On `<html>`, set by the script**: `bfbe-fr` while the reveal runs; `bfbe-fr--strong` or `bfbe-fr--flat` for the shadow; `bfbe-fr--paint` with an inline `--bfbe-fr-page` when the page is given a colour (the setting's, else the body's, else the root's, else white). With no `bfbe-fr` nothing in the stylesheet applies.
- **The reveal is CSS**, on screen only: `body { isolation: isolate }`, `#brx-footer { position: sticky; bottom: 0; z-index: -1 }`, and `#brx-content` given a background colour and a `box-shadow` on its lower edge. The footer stays in the page's flow, so the page's height and every scroll position are as without it.
- **The script listens** for focus entering the footer and for a `hashchange` to an id inside it (each scrolls to the end of the page), for resizes of the window and the footer, for a change of the reduced-motion and dark preferences, and for `data-bfbe-theme` or `class` changes on `<html>` (BFB Dark Mode), which repaint the page's colour.

## Wiring to other elements

- **The footer template carries the group.** Write it with `bricks/set-template-settings` on a template whose type is `footer`. The keys go into the template's settings, not into an element tree.
- **One page off.** `bfbeFrOff: true` in a page's settings (`bricks/set-page-settings`), or in a content template's (`bricks/set-template-settings`), gives every page it applies to an ordinary footer. The page's own switch is read first, then its content template's.
- **What lifts is `#brx-content`**, Bricks' `<main>`. Its sections keep their own backgrounds; the colour the feature gives `#brx-content` shows only where a section is see-through.
- **Elements inside the footer** need nothing. A fixed element inside the footer (a back-to-top button) sits with the footer, behind the page until it is uncovered.
- **BFB Dark Mode**: unset, the page's colour is read again whenever the theme changes, so the lifting page follows the dark body. Leave Page colour unset on a site that switches themes.
- **Advanced Header Scroll** is the header's feature and does not touch the footer.

## Verified patterns

**The demo's footer: the reveal on, everything else at its default.** The footer template settings of "Footer reveal: a roastery's footer" (`bfb-footer-reveal`), written with `bricks/set-template-settings` on the footer template; with `templateConditions` it applies to the pages they name. The check parses this block and renders nothing.

```json
{ "bfbeFrOn": true }
```

**A light footer with a strong shadow.** The footer template of the feature visual "A shadow on the page's edge": a light footer, so the strong shadow gives the page's edge depth.

```json
{ "bfbeFrOn": true, "bfbeFrShadow": "strong" }
```

**One page with an ordinary footer.** That page's settings, through `bricks/set-page-settings`.

```json
{ "bfbeFrOff": true }
```

## Gotchas

- **It needs a Bricks footer template.** The marks go on Bricks' `#brx-footer` and the page that lifts is `#brx-content`; with no footer template, or a theme's own footer, nothing happens. <!-- src: plugins/bfb-elements-pro/includes/class-footer-reveal.php:155-171; src/elements/footer-reveal/footer-reveal.js:15-17 -->
- **The builder never shows it.** Nothing is marked in the builder; scroll the page itself to see the reveal. <!-- src: plugins/bfb-elements-pro/includes/class-footer-reveal.php:165; src/elements/footer-reveal/footer-reveal.js:17 -->
- **A footer taller than the window is never revealed.** The script checks the footer's height against the window's on every resize, so a tall footer, or a short window, gets an ordinary footer. Keep a footer that should reveal shorter than the smallest window it is meant for, or set **From this width**. <!-- src: src/elements/footer-reveal/footer-reveal.js:39-45,64-66 -->
- **The page is painted a colour, never an image.** Unset, `#brx-content` takes the body's background colour, else the root's, else white. A background image or gradient on the body is covered on the page area; give the sections their own backgrounds, or set **Page colour**. A see-through Page colour lets the footer show through the page. <!-- src: src/elements/footer-reveal/footer-reveal.js:28-37; src/elements/footer-reveal/footer-reveal.css:12-17 -->
- **From this width is a number of pixels, the breakpoint's width plus one.** The panel offers the site's own breakpoints that way (`992`, `768`, `479` on the demo site); the script compares it with the window's width. Below it, an ordinary footer. <!-- src: plugins/bfb-elements-pro/includes/class-footer-reveal.php:77-89,168-171; src/elements/footer-reveal/footer-reveal.js:19,41 -->
- **The shadow is fixed.** Soft, Strong or None: its colour and size are not settings, and it is drawn on `#brx-content`, so a `box-shadow` given to `#brx-content` elsewhere is replaced while the reveal runs. <!-- src: src/elements/footer-reveal/footer-reveal.css:12-19 -->
- **Reduced motion is an ordinary footer**, for the visitor who asked, without a setting to change it. <!-- src: src/elements/footer-reveal/footer-reveal.js:22,41 -->

## Never do

- Do not write `bfbeFrOn`, `bfbeFrFrom`, `bfbeFrShadow` or `bfbeFrPage` into an element or a page; they belong to the footer template's settings.
- Do not set `bfbeFrOff` on the footer template; it belongs to a page or a content template.
- Do not set a see-through Page colour.
- Do not fake the effect with a fixed footer and a bottom margin on the page: the keyboard, height and reduced-motion guards come with this feature only.
