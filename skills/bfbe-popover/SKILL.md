---
name: bfbe-popover
description: "Use when adding a tooltip to a word or button, or a panel of nested content (text, links, buttons, images) that opens beside a button on click or hover, with BFB Popover (`bfbe-popover`). Read before writing its settings."
---

# BFB Popover (`bfbe-popover`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-popover.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/popover/

## What it is
One element with two modes: Tooltip shows short plain text on hover and keyboard focus, and Popover holds nested Bricks content behind a button. The panel is placed on the side with room, shifted to stay on screen, and can carry an arrow that follows the trigger. It uses the browser's Popover API where there is one, with a fallback that handles dismissal itself.

**Not for:** Not for content that must be reachable without a click or a hover, or for a full-screen dialog: use Modal for that. Tooltip mode holds short plain text, so links and buttons belong in Popover mode.

**Costs a page:** CSS 0.94 KB, JS 1.91 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-popover",
    "settings": {},
    "children": [
        {
            "name": "text-basic",
            "settings": {
                "text": "Popover content. Put anything here."
            }
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Mode (`bfbeMode`)
- `mode` (select) **Mode**: options: `popover` Popover (nested content) (default), `tooltip` Tooltip (short text). Popover (nested content) is the default. Tooltip (short text) holds plain text and drops anything nested inside the element.
- `text` (textarea) **Tooltip text**: placeholder Tooltip text; dynamic data accepted; only when `mode` is `tooltip`. Type the words a tooltip shows. They accept dynamic data, and line breaks are kept. Links or buttons belong in Popover mode instead.
- `openOn` (select) **Opens on**: options: `click` Click (default), `hover` Hover and click; only when `mode` is not `tooltip`. Click is the default. Choose Hover and click to open on hover too. A tooltip always opens on hover and on keyboard focus.
- `delay` (number) **Hover delay (ms)**. Set how long the pointer rests before a tooltip or a hover popover opens, 100 by default. Raise it if the panel flickers as the mouse crosses the page.

### Trigger (`bfbeTrigger`)
- `label` (text) **Text**: placeholder More; dynamic data accepted. Type the label on the trigger button, More by default. It accepts dynamic data, so each query loop item can name its own popover.
- `icon` (icon) **Icon**. Choose an icon from the library to sit beside the label. Icon size, 1em, and Icon gap, .45em by default, come with it.
- `triggerStyle` (select) **Looks like**: options: `chip` Button (default), `link` Link, `plain` Plain text. Button is the default. Choose Link or Plain text instead. The trigger stays a real button in all three, so just the style changes.
Styling, in the schema file: `iconSize`, `triggerGap`, `triggerTypography`, `triggerBackground`, `triggerBackgroundHover`, `triggerBorder`, `triggerPadding`.

### Placement (`bfbePlace`)
- `placement` (select) **Side**: options: `auto` Wherever there is room (default), `top` Top, `bottom` Bottom, `left` Left, `right` Right. Wherever there is room, the default, tries bottom, top, right and left in turn. A fixed side flips to the opposite one when it does not fit and that side has more room.
- `offset` (number) **Distance (px)**. Set the gap between the trigger and the panel, 8 by default. The panel is kept inside the viewport whichever side it takes.
Styling, in the schema file: `inset`.

### Panel (`bfbePanel`)
- `arrow` (checkbox) **Arrow**. Tick it to draw an arrow that points at the trigger, sized by Arrow size, 10px by default.
Styling, in the schema file: `maxWidth`, `panelBackground`, `panelColor`, `panelTypography`, `panelPadding`, `panelGap`, `panelBorder`, `lineColor`, `panelShadow`, `arrowSize`.

### Motion (`bfbeMotion`)
- `effect` (select) **Effect**: options: `fade` Fade (default), `rise` Rise, `scale` Scale, `none` None. Choose how the panel arrives and leaves: Fade (the default), Rise, Scale or None.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Snappy by default. Pick another curve from the list of ten, or Custom to type your own in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Open, so you can style it (default), `closed` Closed, as the site leaves it, `live` Working, as on the site. Open, the default, shows the panel so you can style it. Closed matches the site at rest, and Working lets a click open it in the canvas.

## What it guarantees for accessibility (do not undo)
- Tooltip mode ties the plain-text panel to a focusable trigger with aria-describedby and role tooltip.
- A tooltip shows on hover and focus, and it hides again on blur or Escape.
- Popover mode puts aria-expanded and aria-controls on a real button, and opening it by click or key moves focus into the panel. Tab then wraps within the panel's controls, and in a panel with no controls Tab closes it.
- Escape closes a popover and returns focus to the trigger, and a click outside closes it through the browser's light dismiss or the fallback.
- The popover panel is named by its trigger through aria-labelledby.
- Fade, rise and scale run on the shared motion duration, which reduced motion sets to zero, so the panel appears without animation.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-popover bfbe-popover bfbe-popover--popover bfbe-popover--fx-fade bfbe-popover--arrow"
     data-bfbe-placement="auto" data-bfbe-open-on="click" data-bfbe-offset="8" data-bfbe-delay="100">
  <button type="button" class="bfbe-popover__trigger bfbe-popover__trigger--chip bfbe-chip" id="bfbe-{id}-t"
          aria-expanded="false" aria-controls="bfbe-{id}-p"><span>More</span></button>
  <span class="bfbe-popover__inset" aria-hidden="true"></span>
  <div class="bfbe-popover__panel" id="bfbe-{id}-p" tabindex="-1" aria-labelledby="bfbe-{id}-t" hidden>
    <span class="bfbe-popover__arrow" aria-hidden="true"></span>
    <div class="bfbe-popover__body">… the nested elements …</div>
  </div>
</div>
```

- Root `.bfbe-popover`, an inline-flex `div`: `bfbe-popover--{mode}`, `bfbe-popover--fx-{effect}`, `bfbe-popover--arrow` when **Arrow** `arrow` is on, `bfbe-popover--canvas` in the builder's Open view.
- The script reads `data-bfbe-placement`, `data-bfbe-open-on` (always `hover` in tooltip mode), `data-bfbe-offset` and `data-bfbe-delay`. The canvas's Working view adds `data-bfbe-live="1"`.
- The trigger is always a `<button type="button">`, classed `bfbe-popover__trigger--chip`, `--link` or `--plain` by **Looks like** `triggerStyle`; `chip` adds `bfbe-chip`. **Icon** renders `.bfbe-popover__icon` before the label's `<span>`.
- Tooltip mode swaps `aria-expanded` and `aria-controls` for `aria-describedby`, gives the panel `role="tooltip"` and no `tabindex`, and puts the escaped **Tooltip text** in `.bfbe-popover__body`.
- Ids are `bfbe-{id}-t` and `bfbe-{id}-p`; inside a query loop Bricks' loop identifier is added, so each item's references stay unique.
- States: where the browser has the Popover API, the script sets `popover="auto"` (popover) or `popover="manual"` (tooltip) and removes `hidden`, and an open panel matches `:popover-open`. Otherwise it toggles `hidden` and `.is-shown`. The trigger's `aria-expanded` follows.
- On every open, scroll, resize and panel resize, the panel gets inline `left` and `top`, `data-side` (`top`, `bottom`, `left`, `right`), and the root gets `--bfbe-pop-ax` and `--bfbe-pop-ay`, the arrow's anchor.
- The panel is `position: fixed`, `z-index: 9999`, as wide as its content up to `min(var(--bfbe-pop-w), 100vw - 16px)`. `.bfbe-popover__body` is a flex column with `gap: var(--bfbe-pop-gap, 12px)`.
- Where controls write: `maxWidth`, `panelBackground`, `lineColor` and `panelGap` set `--bfbe-pop-w`, `--bfbe-pop-bg`, `--bfbe-pop-line` and `--bfbe-pop-gap` on the root. `panelColor`, `panelTypography`, `panelPadding`, `panelBorder` and `panelShadow` write to `.bfbe-popover__panel`. `arrowSize` sets `--bfbe-pop-arrow` on `.bfbe-popover--arrow`. The `trigger*` controls write to `.bfbe-popover__trigger` (the hover background on `:focus-visible` too), `inset` writes margins on `.bfbe-popover__inset`, `duration` and `easing` set `--bfbe-duration` and `--bfbe-ease`.

## Wiring to other elements

Stands alone: the trigger is always its own button, and no attribute on another element opens, closes or points at it.
- Popover-mode panels share the browser's auto popover stack: opening one closes any other open one. Tooltips are `manual` and stay out of it.
- The script runs on load and again on Bricks' `bricks/ajax/popup/loaded`, `bricks/ajax/pagination/completed`, `bricks/ajax/load_page/completed` and `bricks/ajax/query_result/displayed`, so popovers inside a Bricks popup or AJAX-loaded query results need nothing added. `window.bfbePopover()` initialises every `.bfbe-popover` again for markup added another way.
- Style a set of popovers by a class in **CSS classes** (`_cssClasses`), such as `.faq-pop .bfbe-popover__panel`, never by `_cssId`: component instances share ids and query loop items repeat them. The panel stays inside the root in the DOM while it shows in the top layer, so descendant selectors reach it.
- In a query loop, **Text** `label` takes dynamic data, so each item's trigger can carry `{post_title}`.

## Verified patterns

**Click panel with text and a link button** (demo page `demo-bfb-popover`, "Can we change plan mid-year?"). The default `mode` and `openOn` give a click popover; `placement: "right"` opens it beside its question, and the panel's colours come through `panelBackground` and `panelColor` so the arrow matches. The demo's translucent trigger fills are left out. For hover, add `openOn: "hover"` (fixture `fixture-popover`, "Hover me").

```json
{
  "name": "bfbe-popover",
  "settings": { "label": "Can we change plan mid-year?", "arrow": true, "placement": "right", "maxWidth": "320px", "panelBackground": { "hex": "#ffffff" }, "panelColor": { "hex": "#101828" }, "panelPadding": { "top": "16", "right": "16", "bottom": "16", "left": "16" } },
  "children": [
    { "name": "text-basic", "settings": { "text": "Up whenever you like, and we charge the difference from that day. Down at the end of the year, and nothing is lost in between.", "tag": "p" } },
    { "name": "button", "settings": { "text": "See the plans", "link": { "type": "external", "url": "#plans" } } }
  ]
}
```

**Definition on a term** (fixture page `fixture-popover`). `mode: "tooltip"` with `text`, and `triggerStyle: "plain"` draws the trigger as words with a dotted underline. No children: tooltip mode renders none.

```json
{ "name": "bfbe-popover", "settings": { "mode": "tooltip", "label": "a term", "triggerStyle": "plain", "text": "A short definition of the term.", "arrow": true } }
```

**Placement nudged per breakpoint** (fixture page `fixture-popover`, "Moved"). `placement: "bottom"` sets the side; `inset` moves the panel 20px down and 30px right, and `inset:mobile_portrait` lifts it 12px instead on phones.

```json
{
  "name": "bfbe-popover",
  "settings": { "label": "Moved", "placement": "bottom", "arrow": true, "inset": { "top": "20", "left": "30" }, "inset:mobile_portrait": { "top": "0", "bottom": "12", "left": "0" } },
  "children": [ { "name": "text-basic", "settings": { "text": "Placed, then moved by the Inset." } } ]
}
```

## Gotchas

- **Tooltip mode drops nested content.** The page renders no children in tooltip mode. The canvas keeps them below the trigger with the notice "Nested content shows in popover mode.", and switching back to `popover` restores them. <!-- src: plugins/bfb-elements-pro/elements/popover.php:448 -->
- **Tooltip text and Text are plain text.** Both are escaped after dynamic data resolves, so typed HTML shows as characters. Line breaks in **Tooltip text** `text` become `<br>`; links and buttons need popover mode. <!-- src: plugins/bfb-elements-pro/elements/popover.php:451 ; plugins/bfb-elements/includes/abstract-element.php:1272 -->
- **An empty Text renders "More".** The trigger always carries its label in a `<span>`, so clearing **Text** `label` never leaves an icon-only button. <!-- src: plugins/bfb-elements-pro/elements/popover.php:409 ; plugins/bfb-elements/includes/abstract-element.php:1268 -->
- **Side and Distance hold one value for every width.** `placement` and `offset` are read from their base keys alone, so `placement:mobile_portrait` does nothing. **Inset** `inset` is written per breakpoint: a top pushes the panel down, a left pushes it right, a bottom up, a right left. <!-- src: plugins/bfb-elements-pro/elements/popover.php:416 ; src/elements/popover/popover.js:35 ; docs/elements/popover.md "Round 413" -->
- **A fixed Side still moves.** `top` or `bottom` flips to the opposite side when it does not fit and that side has more room, and likewise `left` and `right`. The panel, Inset included, is then held 8px inside the viewport. <!-- src: src/elements/popover/popover.js:21 ; src/elements/popover/popover.js:41 -->
- **The arrow takes Background and Outline colour.** It fills with `--bfbe-pop-bg` and outlines with `--bfbe-pop-line`. A colour set in **Panel border** `panelBorder`, or a panel background set any other way, leaves the arrow in the old colours. <!-- src: src/elements/popover/popover.css:25 ; src/elements/popover/popover.css:57 -->
- **A Bricks Button with no link is skipped by the keyboard.** Opening by click or key focuses the first link, button, field or `[tabindex]` in the panel, and Tab cycles among those. A Button without `link` renders a `<span>`, so give it a link or **HTML tag** `tag: "button"`. <!-- src: src/elements/popover/popover.js:10 ; src/elements/popover/popover.js:179 ; wp-content/themes/bricks/includes/elements/button.php:170 -->
- **Hover delay acts on the pointer alone.** **Hover delay** `delay` waits before a tooltip or a hover popover opens and before it closes, a tooltip at least 150ms; a click opens at once. A hover-opened popover never takes focus, and the pointer leaving never closes a panel holding focus. <!-- src: src/elements/popover/popover.js:139 ; src/elements/popover/popover.js:157 ; src/elements/popover/popover.js:161 -->
- **The canvas's Open view shows no placement.** With **Show it** `builderView` at its default, the panel sits static under the trigger with a dashed outline and no arrow, so Side, Distance, Inset and Arrow show nothing. Set `builderView: "live"` to click it open in the canvas. <!-- src: src/elements/popover/popover.css:66 ; plugins/bfb-elements-pro/elements/popover.php:425 ; src/elements/popover/popover.js:65 -->
- **Children stretch across the panel.** The body is a flex column with **Space between items** `panelGap` (12px) between children, and their own margins add to it, so a Button spans the panel's width. <!-- src: src/elements/popover/popover.css:63 ; docs/elements/popover.md "Space between items" -->
- **The Style tab paints the wrapper.** Universal `_background`, `_padding` and `_border` write to the root, the inline-flex wrapper around the trigger. Style the trigger in the Trigger group and the panel in the Panel group. <!-- src: plugins/bfb-elements-pro/elements/popover.php:413 ; src/elements/popover/popover.css:2 -->

## Never do

- Do not nest elements in a popover with `mode: "tooltip"`; use `mode: "popover"` for anything but plain text.
- Do not put HTML in `text` or `label`.
- Do not clear `label` to get an icon-only trigger.
- Do not set `placement` or `offset` per breakpoint; use `inset:{breakpoint}`.
- Do not colour a panel with an arrow through `panelBorder` alone; set `panelBackground` and `lineColor`.
- Do not rely on a Bricks Button without `link` or `tag: "button"` as a control inside the panel.
- Do not style the panel or trigger with the element's own `_background`, `_padding` or `_border`.
- Do not judge Side, Distance, Inset or Arrow from the canvas's default Open view, or target a popover by `_cssId`.
