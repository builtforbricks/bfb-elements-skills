---
name: bfbe-tooltips
description: "Use when placing, wiring or styling BFB Tooltips (`tooltips`): a feature on every element, Bricks' own included, not an element of its own: the Tooltip group on the Style tab, after Hover effect, gives any element a short text shown beside it on hover, after a short delay, and at once on keyboard focus. Read before writing its settings."
---

# BFB Tooltips (`tooltips`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.1.1 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/tooltips.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/tooltips/

## What it is
A feature on every element, Bricks' own included, not an element of its own: the Tooltip group on the Style tab, after Hover effect, gives any element a short text shown beside it on hover, after a short delay, and at once on keyboard focus. It stays while the pointer moves onto it and closes with Escape, and a touch opens it. It sits above, below, left or right, flips when there is no room, and is never cut by a parent's overflow or transform. Its two files load on a page where some element has a tooltip.

**Not for:** Not for links, buttons or anything to click: a tooltip holds plain text. Use Popover for content inside a panel. An Image printed as a bare picture, with no link or caption, cannot hold the bubble: its tooltip sits beside it with the colours and the width, not the Typography or the Border.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Where it lives
A feature, not an element: its controls are added to every element, Bricks' own included.

## Settings that decide the build

### Tooltip (`bfbeTooltip`)
- `bfbeTooltip` (textarea) **Text**: dynamic data accepted. Type the words the tooltip shows. It accepts dynamic data, and a line break starts a new line. It holds plain text: any HTML is taken out.
- `bfbeTooltipPlace` (select) **Place**: options: `top` Above (default), `right` Right, `bottom` Below, `left` Left; only when `bfbeTooltip` is set. Above is the default. Choose Right, Below or Left instead. When there is no room on that side, it flips to the other.
- `bfbeTooltipDelay` (number) **Delay**: placeholder 150; only when `bfbeTooltip` is set. How long the pointer rests before it shows, in milliseconds, 150 by default. Keyboard focus shows it at once.
- `bfbeTooltipNoArrow` (checkbox) **Hide the arrow**: only when `bfbeTooltip` is set. Tick it to take the small arrow away.
Styling, in the schema file: `bfbeTooltipWidth`, `bfbeTooltipBackground`, `bfbeTooltipColor`, `bfbeTooltipTypography`, `bfbeTooltipBorder`.

## What it guarantees for accessibility (do not undo)
- It shows on keyboard focus at once and on hover after the Delay, and it stays while the pointer moves from the element onto the bubble, so it can be read and its words selected.
- Escape closes it. It also closes when the pointer leaves, unless the focus is inside, or when the focus leaves.
- A touch on the element opens it, and a touch anywhere else closes it.
- For screen readers the bubble is the element's description, read once after its name, and is kept out of the name itself.
- Under reduced motion it appears without fading.
<!-- bfbe:generated:end -->

## Rendered DOM

The server adds no wrapper, class or child: it writes data attributes on the host's own root. The script builds the bubble when the page is ready, so the page a visitor tabs through looks like this before anything is hovered:

```html
<h3 id="brxe-a1b2c3" class="brxe-heading" data-bfbe-tip="Named for the room above the shop where it is knitted." tabindex="0" aria-describedby="bfbe-tip-1">The Studio crew<span class="bfbe-tip" id="bfbe-tip-1" role="tooltip" aria-hidden="true" popover="manual" style="--bfbe-tip-font: Inter, sans-serif;">Named for the room above the shop where it is knitted.<span class="bfbe-tip__arrow"></span></span></h3>
<a id="brxe-d4e5f6" class="brxe-button bricks-button" href="#trial" data-bfbe-tip="No card needed.&#10;Cancel in two clicks." data-bfbe-tip-place="bottom" data-bfbe-tip-delay="0" data-bfbe-tip-arrow="0" aria-describedby="bfbe-tip-2">Start your 30 days<span class="bfbe-tip" id="bfbe-tip-2" role="tooltip" aria-hidden="true" popover="manual" style="--bfbe-tip-font: Inter, sans-serif;">No card needed.
Cancel in two clicks.</span></a>
<img id="brxe-g7h8i9" class="brxe-image" src="..." data-bfbe-tip="Photographed in the shop, in daylight." tabindex="0" aria-describedby="bfbe-tip-3">
<span class="bfbe-tip" id="bfbe-tip-3" role="tooltip" aria-hidden="true" popover="manual" style="--bfbe-tip-font: Inter, sans-serif; --bfbe-tip-w: 260px;">Photographed in the shop, in daylight.<span class="bfbe-tip__arrow"></span></span>
```

- `data-bfbe-tip` carries the **Text** (`bfbeTooltip`) after dynamic data, with every tag stripped and the ends trimmed. A Text that is empty after that writes nothing at all: no attribute, no files.
- `data-bfbe-tip-place` is written for `right`, `bottom` and `left`; Above (`top`, the default) writes nothing. `data-bfbe-tip-delay` is written when **Delay** is set, held between 0 and 3000. `data-bfbe-tip-arrow="0"` is **Hide the arrow**.
- **Max width**, **Background** and **Text colour** are custom properties Bricks writes at the element's id: `--bfbe-tip-w` (240px when unset, never wider than the window less 16px), `--bfbe-tip-bg` (`#101828`) and `--bfbe-tip-fg` (`#ffffff`). **Typography** and **Border** are written to `.bfbe-tip` under the element's id.
- The bubble is a `span.bfbe-tip` with an id `bfbe-tip-N`, `role="tooltip"`, `aria-hidden="true"` and, where the browser has the Popover API, `popover="manual"`, which puts it in the top layer when shown. It holds the words and a `span.bfbe-tip__arrow` unless the arrow is hidden. It is appended as the element's last child; after a root that cannot hold children (`img`, `input`, `textarea`, `select`, `video`, `audio`, `iframe`, `canvas`, `embed`, `object`, `svg`, `hr`, `br`) it is inserted as the next sibling, with any of the three custom properties set on the element copied onto it inline.
- The host gains `aria-describedby` naming the bubble (other ids already there are kept), and `tabindex="0"` when it cannot take focus and holds nothing that can. Since BFB Elements Pro 1.1.2, a host inside a link or a button (an Icon given a `link`) gains no tab stop: the link or button gets the `aria-describedby`, and its focus opens the host's tooltip.
- Shown, the bubble gains `is-open`, `data-side` (the side it ended on after a flip), an inline `left` and `top` (it is `position: fixed`) and `--bfbe-tip-ax`, which keeps the arrow on the element's middle. Its own look: 14px, weight 400, line height 1.4, padding 6px 10px, `white-space: pre-line`, the pack's small radius and shadow, and an opacity fade over `--bfbe-duration` (0ms under reduced motion).
- Both files use the handle `bfbe-tooltip`. `window.bfbeTooltip` exists for the builder and does nothing.

## Wiring to other elements

- **On its own.** A tooltip belongs to the element that carries it. No `_cssId` or `_cssClasses` is involved and nothing targets it, so it works on Bricks' own elements, on BFB elements and on component instances alike.
- **In a query loop.** Each item renders its own text: `bfbeTooltip: "About {post_title}"` on a Heading inside a looping Block gave three items three texts (rendered 2026-10-13). Items that arrive later, through pagination, a filter or any script, get their bubble, tab stop and description as they land; nothing needs calling.
- **On a container.** A tooltip on a Block opens when the pointer is over any of its children, and when focus lands on a link or button inside it. The description is the Block's, so a screen reader on that link does not hear it. Put the tooltip on the control itself.
- **Nested tooltips.** Under the pointer or focus, the innermost element with a tooltip wins and the outer one closes. One tooltip is open at a time on the page.
- **BFB Popover** (`bfbe-popover`) is the other choice. Its tooltip mode is an element of its own with a trigger; its popover mode holds links, buttons and nested elements. This feature describes an element that is already on the page, in plain text.
- **BFB Hover Effects** on the same element works beside it. Zoom and Shine set `overflow: hidden` on the host, which does not cut the bubble in the top layer.

## Verified patterns

The image carries the demo site's media id and `https://example.com/...` addresses in place of its own. Use the target site's own media id, `filename`, `url` and `full`.

**An info icon after each line of a plan.** From the Tooltips demo (`demo-bfb-tooltips`), "Works offline in the van". Bricks' own Icon carries the tooltip to its right, 320px wide. Trimmed: the paragraph's type and margin, the icon's classes, and the other three lines.

```json
{
  "name": "block",
  "settings": { "_direction": "row", "_flexWrap": "nowrap", "_alignItems": "center", "_columnGap": "10px" },
  "children": [
    { "name": "icon", "settings": { "icon": { "library": "themify", "icon": "ti-check" }, "iconColor": { "hex": "#6e44ff" }, "iconSize": "15px" } },
    { "name": "text-basic", "settings": { "text": "Works offline in the van", "tag": "p" } },
    { "name": "icon", "settings": { "icon": { "library": "themify", "icon": "ti-info-alt" }, "iconColor": { "hex": "#475467" }, "iconSize": "15px", "bfbeTooltip": "Jobs, photos and signatures save on the phone and send when there is signal.", "bfbeTooltipPlace": "right", "bfbeTooltipWidth": "320px" } }
  ]
}
```

**A button's small print, on two lines, below it.** From the same demo, "Start your 30 days". The line break in the Text starts a new line in the bubble. Trimmed: the demo's own fill, padding and pill corners, for which `style: "primary"` stands in.

```json
{ "name": "button", "settings": { "text": "Start your 30 days", "link": { "type": "external", "url": "#trial" }, "style": "primary", "bfbeTooltip": "No card needed.\nCancel in two clicks.", "bfbeTooltipPlace": "bottom" } }
```

**A product photo, its name and its buttons, each explaining itself.** From the Tooltips feature page (`feature-bfb-tooltips-on-any-element`). Bricks' Image, Heading and Button each carry a 260px bubble at 15px. The Image prints as a bare `img`, so its bubble sits beside it and its Typography does not reach it. Trimmed: the page's two-column grid, colours, padding and corners, three icon lines, and `bfbeTooltipDelay: "0"`, set there for filming.

```json
{
  "name": "block",
  "settings": { "_rowGap": "14px", "_alignItems": "flex-start" },
  "children": [
    { "name": "image", "settings": { "image": { "id": 3151, "filename": "bfbe-demo-hollis-knits.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/bfbe-demo-hollis-knits-682x1024.jpg", "full": "https://example.com/wp-content/uploads/bfbe-demo-hollis-knits.jpg" }, "_objectFit": "cover", "_aspectRatio": "4/5", "_width": "100%", "bfbeTooltip": "Photographed in the shop, by the window, in daylight.", "bfbeTooltipWidth": "260px", "bfbeTooltipTypography": { "font-size": "15px", "line-height": "1.45" } } },
    { "name": "heading", "settings": { "text": "The Studio crew", "tag": "h3", "bfbeTooltip": "Named for the room above the shop where it is knitted.", "bfbeTooltipWidth": "260px", "bfbeTooltipTypography": { "font-size": "15px", "line-height": "1.45" } } },
    { "name": "button", "settings": { "text": "Add to bag", "link": { "type": "external", "url": "#bag" }, "style": "primary", "bfbeTooltip": "Your bag keeps it for a week.", "bfbeTooltipPlace": "bottom", "bfbeTooltipWidth": "260px", "bfbeTooltipTypography": { "font-size": "15px", "line-height": "1.45" } } },
    { "name": "button", "settings": { "text": "Size guide", "link": { "type": "external", "url": "#sizes" }, "style": "outline", "bfbeTooltip": "Chest, length and sleeve, in centimetres.", "bfbeTooltipPlace": "bottom", "bfbeTooltipWidth": "260px", "bfbeTooltipTypography": { "font-size": "15px", "line-height": "1.45" } } }
  ]
}
```

**A styled bubble, and one from dynamic data.** From the Tooltips probe's scratch page (`dev/tooltip-probe.mjs`), which reads them in a browser: the Button's bubble opens below in red, at 20px, with a 3px border; the Text's bubble shows the page's title, with no arrow.

```json
[
  { "name": "button", "settings": { "text": "A button", "link": { "type": "external", "url": "https://example.com" }, "bfbeTooltip": "Opens in a new tab", "bfbeTooltipPlace": "bottom", "bfbeTooltipBackground": { "hex": "#b91c1c" }, "bfbeTooltipTypography": { "font-size": "20px" }, "bfbeTooltipBorder": { "width": { "top": "3", "right": "3", "bottom": "3", "left": "3" }, "style": "solid", "color": { "hex": "#111827" } } } },
  { "name": "text-basic", "settings": { "text": "A text", "bfbeTooltip": "{post_title}", "bfbeTooltipNoArrow": true } }
]
```

## Gotchas

- **A bare Image or an SVG Icon cannot hold the bubble.** A Bricks `image` with no link, caption or HTML tag renders its `img` as the root, and an Icon from an SVG library renders an `svg`; the bubble goes beside either. There it takes Max width, Background and Text colour, copied once when it is built, but not Typography or Border, which are written for `.bfbe-tip` inside the element. The sibling also sits between the element and the next one, so a `+` selector aimed at the next element misses. <!-- src: src/elements/tooltip/tooltip.js:12, 46-56 --> <!-- src: plugins/bfb-elements-pro/includes/class-tooltips.php:151-166 --> <!-- src: Bricks 2.3.10 includes/elements/image.php:822, 967-986 ; includes/elements/base.php:4379-4419 -->
- **The Text is plain.** Tags are stripped after dynamic data resolves, so `Plain <b>bold</b> & <a href="#">link</a>` shows as "Plain bold & link". A line break is kept and starts a new line. A Text that resolves to nothing, such as an empty custom field, gives the element no tooltip, no tab stop and no files. <!-- src: plugins/bfb-elements-pro/includes/class-tooltips.php:183-192 --> <!-- src: src/elements/tooltip/tooltip.css:28 --> <!-- src: rendered 2026-10-13 on a scratch page -->
- **Delay is for the pointer.** It is held between 0 and 3000 ms (5000 renders as 3000) and waits before a hover opens the bubble. Keyboard focus and a touch open it at once. <!-- src: plugins/bfb-elements-pro/includes/class-tooltips.php:199-201 --> <!-- src: src/elements/tooltip/tooltip.js:120-133, 145-161 -->
- **The bubble lives inside the element.** The element's `textContent` includes the tooltip's words (its `innerText` does not while closed). On a link, such as a Bricks Button with a link or a linked Image, a click on the bubble follows the link, and a touch on the link opens the tooltip and follows the link in the same tap. <!-- src: src/elements/tooltip/tooltip.js:55, 156-161 --> <!-- src: read 2026-10-13 on demo-bfb-tooltips: a click on the Start your 30 days bubble moved the page to #trial -->
- **It adds a tab stop.** A Heading, Text, Icon, bare Image or Block with nothing focusable inside, and not inside a link or button, becomes a tab stop with a focus ring (`[data-bfbe-tip]:focus-visible`). A `tabindex="-1"` set through Bricks' attributes is replaced with `0`. <!-- src: src/elements/tooltip/tooltip.js:12, 81 --> <!-- src: src/elements/tooltip/tooltip.css:50 -->
- **A linked Icon is reached through its link.** Bricks wraps a linked Icon's `i` in `a.bricks-link-wrapper` and keeps the tooltip's attributes on the `i`. Since BFB Elements Pro 1.1.2 the icon takes no tab stop of its own: the link is described by the tooltip and opens it on focus (before, the icon was a second tab stop and the link's focus opened nothing). The same holds for any element with a tooltip inside a link or a button; the nearest one inside wins. <!-- src: Bricks 2.3.10 includes/elements/icon.php:158-170, 214-218 --> <!-- src: src/elements/tooltip/tooltip.js:24, 70 --> <!-- src: measured 2026-10-13 by dev/fixes-1.1.2-probe.mjs: one tab stop, the link described, its focus opened the bubble -->
- **A click keeps it open.** A click that focuses the element (a link, a button, or an element given a tab stop) leaves the bubble open after the pointer leaves, until the focus leaves or Escape is pressed. The other way round, focus leaving closes it even with the pointer still on the element. <!-- src: src/elements/tooltip/tooltip.js:164-172 -->
- **An outer tooltip's style reaches inner bubbles.** The three custom properties inherit, and the outer element's Typography and Border rule matches every `.bfbe-tip` inside it, so a tooltip on a Button inside a Block with a styled tooltip takes the Block's look unless it sets its own. <!-- src: plugins/bfb-elements-pro/includes/class-tooltips.php:132-164 --> <!-- src: src/elements/tooltip/tooltip.css:11, 15-16 -->
- **The bubble keeps none of the element's type.** It takes the body's font family (an Icon's icon font never reaches it), 14px, weight 400 and line height 1.4, so a tooltip on a heading is not set as a heading. The Tooltip group's Typography overrides all of these. <!-- src: src/elements/tooltip/tooltip.js:37-39 --> <!-- src: src/elements/tooltip/tooltip.css:19-27 -->
- **The arrow takes the Background, not the Border.** It is a square filled with the bubble's background, with no border of its own. Corners come from the Border's radius. <!-- src: src/elements/tooltip/tooltip.css:14, 38-48 -->
- **It is placed when it opens.** The side flips when there is no room and the bubble is held 8px inside the window, then placed again on scroll and resize. An element that moves any other way while it is open, such as one sliding in, leaves the bubble where it opened. <!-- src: src/elements/tooltip/tooltip.js:69-95, 167-176 -->
- **Without the Popover API it is a fixed span.** The bubble then shows by class, outside the top layer, so an ancestor with a transform can trap it. <!-- src: src/elements/tooltip/tooltip.js:16, 34, 102 --> <!-- src: src/elements/tooltip/tooltip.css:35-36 -->
- **The canvas builds it on use.** In the builder the script skips the page-ready pass, so a tooltip there is built the moment it is hovered or focused, with no tab stop before that. The two files always load in the canvas. <!-- src: src/elements/tooltip/tooltip.js:207-217 --> <!-- src: plugins/bfb-elements-pro/includes/class-tooltips.php:211-215 -->
- **The files follow the render.** They are enqueued when an element with a tooltip renders, so a page whose tooltips all resolve to nothing loads neither. Switched off on the BFB Elements admin screen, the feature adds no control, attribute or file; saved settings stay and work again when it is back on. <!-- src: plugins/bfb-elements-pro/includes/class-tooltips.php:206, 217-237 --> <!-- src: plugins/bfb-elements-pro/includes/class-plugin.php:152-155, 178-180 -->

## Never do

- Do not put links, buttons or HTML in `bfbeTooltip`; use BFB Popover (`bfbe-popover`) in popover mode.
- Do not count on `bfbeTooltipTypography` or `bfbeTooltipBorder` for a bare Image or an SVG Icon; put the tooltip on a Block around it.
- Do not put a tooltip on a Block to describe a link or button inside it; put it on the link or button.
- Do not put words a phone visitor needs on a link's tooltip; a touch follows the link.
- Do not set `tabindex="-1"` on an element with a tooltip to keep it out of the tab order; the script replaces it.
- Do not set `bfbeTooltipDelay` above 3000.
- Do not call `window.bfbeTooltip()` to bind new markup; it does nothing, and new tooltips are prepared as they arrive.
