---
name: bfbe-hover-effects
description: "Use when adding a hover effect to any element, Bricks' own included, with BFB Hover Effects (`hover-effects`): lift, zoom the picture, shine, gradient border, tilt or follow the pointer, or a card whose parts fade, slide or grow in sequence when it is hovered. Read before writing its settings."
---

# BFB Hover Effects (`hover-effects`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/hover-effects.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/hover-effects/

## What it is
A feature on every element, Bricks' own included, not an element of its own: the Hover effect group on the Style tab, after Bricks' own style groups, offers nine effects with Strength, Speed and Delay. A card can tick Children respond to hover, so parts inside it set to A hovered parent play when the card is hovered, and a Delay on each part, except Tilt and Follow the pointer, staggers them. The stylesheet loads on a page where an element has an Effect or Children respond to hover ticked, the script where an element uses Tilt or Follow the pointer, and the builder canvas loads both.

**Not for:** Not for changing one property on hover, such as a colour or a shadow, which is a hover state on Bricks' own style controls; an effect here answers its own element or a parent with Children respond to hover ticked.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Where it lives
A feature, not an element: its controls are added to every element, Bricks' own included.

## Settings that decide the build

### Hover effect (`bfbeHover`)
- `bfbeHoverEffect` (select) **Effect**: options: `lift` Lift, `zoom` Zoom the picture, `shine` Shine, `border` Gradient border, `tilt` Tilt, `follow` Follow the pointer, `fade` Fade in, `slide` Slide in, `grow` Grow. Pick one of nine: Lift, Zoom the picture, Shine, Gradient border, Tilt, Follow the pointer, Fade in, Slide in or Grow. The last three start faded, offset or smaller and settle on hover.
- `bfbeHoverOn` (select) **Responds to**: options: `parent` A hovered parent; only when `bfbeHoverEffect` is set. Leave it on This element to play the effect when the element is hovered. Choose A hovered parent to play it when the card it sits in is hovered. The card needs Children respond to hover ticked.
- `bfbeHoverFrom` (select) **Comes from**: options: `up` Above, `left` The left, `right` The right; only when `bfbeHoverEffect` is `slide`. For Slide in. Choose where the element starts: Above, The left or The right. Below is the default.
- `bfbeHoverOff` (select) **Off below**: options: `480` 480 px, `640` 640 px, `768` 768 px, `992` 992 px; only when `bfbeHoverEffect` is set. Choose 480, 640, 768 or 992 px and the effect switches off on screens that wide or narrower, where the element shows as normal. Never is the default.
- `bfbeHoverScope` (checkbox) **Children respond to hover**. Tick it on a card. Parts inside it set to A hovered parent then play when the card is hovered. The card needs no effect of its own.
Styling, in the schema file: `bfbeHoverStrength`, `bfbeHoverSpeed`, `bfbeHoverDelay`, `bfbeHoverColor`.

## What it guarantees for accessibility (do not undo)
- Lift, Zoom the picture, Shine and Gradient border play when the element is hovered or has keyboard focus. Fade in, Slide in and Grow also play when keyboard focus is anywhere inside the element.
- With A hovered parent, the effect plays when the parent is hovered or when focus is anywhere inside it, except Tilt and Follow the pointer, which follow the mouse over the parent and do not react to focus.
- Tilt and Follow the pointer react to a mouse, not to touch or a pen. An element set to Tilt or Follow the pointer lifts 4 px times Strength when it has keyboard focus, unless it responds to a hovered parent, and Off below turns that off too.
- On a screen with no hover, such as a touch screen, Fade in, Slide in and Grow show in their finished state, so nothing waits behind a hover. The other effects need a screen that can hover.
- Fade in changes opacity alone, so an element waiting to fade in can still be reached by keyboard and assistive technology, and it shows itself when it receives focus.
- With reduced motion requested, transitions and animations stop: Lift, Zoom the picture, Fade in, Slide in and Grow change at once, the Shine sweep is removed, the Gradient border stops spinning, and Tilt and Follow the pointer ignore the pointer.
<!-- bfbe:generated:end -->

## Rendered DOM

The feature adds no wrapper, class or child: it writes data attributes on the host's own root, and its stylesheet does the rest.

```html
<div id="brxe-a1b2c3" class="brxe-block" data-bfbe-hover="lift" data-bfbe-hover-scope>
  <div id="brxe-d4e5f6" class="brxe-block" data-bfbe-hover="zoom" data-bfbe-hover-on="parent"><img class="brxe-image" ...></div>
  <p class="brxe-text-basic" data-bfbe-hover="fade" data-bfbe-hover-on="parent">...</p>
  <a class="brxe-button bricks-button" data-bfbe-hover="slide" data-bfbe-hover-on="parent" data-bfbe-hover-from="left" data-bfbe-hover-off="768" href="#bag">...</a>
</div>
```

- `data-bfbe-hover` carries the **Effect** (`bfbeHoverEffect`). `data-bfbe-hover-on="parent"`, `data-bfbe-hover-from` (Slide in) and `data-bfbe-hover-off` (the **Off below** width) are written with an Effect, never without one.
- `data-bfbe-hover-scope`, a bare attribute, marks **Children respond to hover** (`bfbeHoverScope`), with or without an Effect beside it.
- **Strength**, **Speed**, **Delay** and **Colour** are custom properties Bricks writes at the element's id: `--bfbe-hv-k`, `--bfbe-hv-t`, `--bfbe-hv-d`, `--bfbe-hv-c`. Strength takes breakpoint values (`bfbeHoverStrength:mobile_portrait`).
- At Strength 1: Lift rises 6 px with a `drop-shadow` filter, Slide in starts 24 px off (below unless **Comes from**, `bfbeHoverFrom`, says otherwise), Grow starts at scale 0.9, and Zoom scales each `img` and `video` inside to 1.08.
- Lift, Slide in and Follow the pointer move with `translate`, Grow and Zoom with `scale`, Fade in with `opacity` from 0, and Tilt with `transform`.
- Zoom and Shine set `overflow: hidden` on the root. Shine draws its band on `::after`, Gradient border its ring (2 px times Strength) on `::before`, and both set `position: relative`. Without Colour both paint `currentColor`.
- Tilt leans up to 5 degrees each way at Strength 1; Follow moves a fifth of the pointer's distance from centre. The script writes `--bfbe-hv-rx` and `--bfbe-hv-ry`, or `--bfbe-hv-mx` and `--bfbe-hv-my`, inline as the pointer moves and removes them on leave.
- Both files use the handle `bfbe-hover`. `window.bfbeHover()` binds every Tilt and Follow on the page again.

## Wiring to other elements

- **On its own.** An element with an Effect and **Responds to** (`bfbeHoverOn`) left empty plays on its own hover. Nothing targets it.
- **A card and its parts.** Tick `bfbeHoverScope` on the card and set `bfbeHoverOn: "parent"` on each part, at any depth inside it. Give each part its own **Delay** (`bfbeHoverDelay`) so they arrive in sequence.
- **By nesting, never by id or class.** A part finds its card through the `data-bfbe-hover-scope` attribute on an ancestor. No `_cssId` or `_cssClasses` is involved, so cards repeated by a query loop or as component instances, which share ids, each play their own parts.
- **The card's own Effect is optional.** The demo card also lifts (`bfbeHoverEffect: "lift"` beside the tick); the fixture's "Card with a tilting picture" carries the tick alone.
- **Tilt and Follow on a part** read the pointer over the nearest ticked ancestor, so a picture set to Tilt with A hovered parent leans as the pointer crosses its card.
- **BFB Interactive Cursor.** Follow on link tiles beside the cursor's **Magnetic** (`magnet`) makes tile and cursor reach for each other: the pull writes an inline `transform`, Follow writes `translate`, and the two add up. That inline `transform` also cancels Tilt on an element the cursor pulls.
- **BFB Text Rotator** keeps its own hover controls in this group. Its `hover` key is the rotating words' effect; `bfbeHoverEffect`, under **The whole element**, is this feature.

## Verified patterns

The images carry the demo site's media id and `https://example.com/...` addresses in place of its own. Use the target site's own media id, `filename`, `url` and `full`.

**A card whose parts arrive in sequence.** From the Hover Effects demo (`demo-bfb-hover-effects`), "The Undyed crew". The card lifts; its picture frame zooms, the sizes fade in after 80 ms and the button slides in after 160 ms. Trimmed: the demo's two-column grid and colours, an eyebrow and a description line.

```json
{
  "name": "block",
  "settings": { "bfbeHoverScope": true, "bfbeHoverEffect": "lift" },
  "children": [
    {
      "name": "block",
      "settings": { "bfbeHoverEffect": "zoom", "bfbeHoverOn": "parent" },
      "children": [
        { "name": "image", "settings": { "image": { "id": 3140, "filename": "bfbe-demo-hollis-white.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/bfbe-demo-hollis-white-768x1024.jpg", "full": "https://example.com/wp-content/uploads/bfbe-demo-hollis-white.jpg" } } }
      ]
    },
    {
      "name": "block",
      "settings": {},
      "children": [
        { "name": "text-basic", "settings": { "text": "The Undyed crew", "tag": "p" } },
        { "name": "text-basic", "settings": { "text": "XS to XL, every size in the shop today.", "tag": "p", "bfbeHoverEffect": "fade", "bfbeHoverOn": "parent", "bfbeHoverDelay": "80" } },
        { "name": "button", "settings": { "text": "Add to bag, £150", "link": { "type": "external", "url": "#bag" }, "bfbeHoverEffect": "slide", "bfbeHoverOn": "parent", "bfbeHoverDelay": "160" } }
      ]
    }
  ]
}
```

**A product card that shines in the brand colour.** From the same demo, "The Orange tee (Shine)". The effect sits on the card itself; `bfbeHoverColor` paints the band and `bfbeHoverSpeed` 400 makes the sweep last 1.2 s. Trimmed: the price row.

```json
{
  "name": "block",
  "settings": { "bfbeHoverEffect": "shine", "bfbeHoverColor": { "hex": "#6e44ff" }, "bfbeHoverSpeed": "400" },
  "children": [
    { "name": "image", "settings": { "image": { "id": 3142, "filename": "bfbe-demo-hollis-orange.jpg", "size": "large", "url": "https://example.com/wp-content/uploads/bfbe-demo-hollis-orange-682x1024.jpg", "full": "https://example.com/wp-content/uploads/bfbe-demo-hollis-orange.jpg" } } },
    {
      "name": "block",
      "settings": {},
      "children": [
        { "name": "text-basic", "settings": { "text": "The Orange tee", "tag": "p" } },
        { "name": "text-basic", "settings": { "text": "Heavy jersey, garment dyed.", "tag": "p" } }
      ]
    }
  ]
}
```

**Menu tiles that drift after the pointer.** From the Hover Effects fixture (`hover-effects`), "Three tiles that follow the pointer". Each Bricks `button` carries Follow the pointer and eases back over 100 ms (half of `bfbeHoverSpeed` 200). `_direction` and `_columnGap` are kept from the fixture's row.

```json
{
  "name": "block",
  "settings": { "_direction": "row", "_columnGap": "24px" },
  "children": [
    { "name": "button", "settings": { "text": "Docs", "link": { "type": "external", "url": "#docs" }, "bfbeHoverEffect": "follow", "bfbeHoverSpeed": "200" } },
    { "name": "button", "settings": { "text": "Roadmap", "link": { "type": "external", "url": "#roadmap" }, "bfbeHoverEffect": "follow", "bfbeHoverSpeed": "200" } },
    { "name": "button", "settings": { "text": "Pricing", "link": { "type": "external", "url": "#pricing" }, "bfbeHoverEffect": "follow", "bfbeHoverSpeed": "200" } }
  ]
}
```

## Gotchas

- **A part needs a ticked ancestor.** With `bfbeHoverOn: "parent"` and no ancestor carrying `bfbeHoverScope`, Lift, Zoom, Shine and Gradient border never play, and Fade in, Slide in and Grow stay faded, offset or small on a screen that can hover. Tilt and Follow fall back to the element's own hover. <!-- src: src/elements/hover/hover.css:31-36, 64-72 --> <!-- src: src/elements/hover/hover.js:19 -->
- **Every ticked ancestor plays the parts below it.** The rule matches a hovered ancestor at any depth, not the nearest, so a ticked section plays the parts of all its cards at once. Tilt and Follow listen to the nearest ticked ancestor. <!-- src: src/elements/hover/hover.css:64-72 --> <!-- src: src/elements/hover/hover.js:19 --> <!-- src: docs/HOVER-EFFECTS-PROPOSAL-2026-09-13.md §3 "Nested scopes just nest" -->
- **Off below belongs to one element.** It needs an Effect on the same element, and a card's Off below leaves its parts moving, because each part resets the switch for itself. Its four widths are fixed media queries, not the site's Bricks breakpoints. <!-- src: plugins/bfb-elements-pro/includes/class-hover-effects.php:242-255 --> <!-- src: src/elements/hover/hover.css:21-23, 82-98 -->
- **Zoom grows what is inside the host.** It scales each `img` and `video` inside and clips them at the host's edges, so the demos zoom a block holding the image. A Bricks `image` with no link, caption or HTML tag renders its `<img>` as the root, and Zoom there grows the picture past its own box. A background image has nothing to grow. <!-- src: src/elements/hover/hover.css:38-40, 65-67 --> <!-- src: dev/demo/feature-pages/bfb-hover-effects.php:34 --> <!-- src: docs/elements/hover-effects.md "In the builder" --> <!-- src: Bricks 2.3.10 includes/elements/image.php:822, 967-986; rendered 2026-10-08, the img is the root -->
- **Zoom and Shine clip; Shine and Gradient border hold positioned children.** Zoom and Shine set `overflow: hidden`, so a badge hanging over the host's edge is cut off. Shine and Gradient border set `position: relative`, so an absolutely placed child positions against the host. <!-- src: src/elements/hover/hover.css:39, 51-52 --> <!-- src: docs/elements/hover-effects.md "In the builder" -->
- **Gradient border and a Bricks gradient overlay collide.** Both draw on the host's `::before`: Bricks writes a **Gradient** applied to Overlay (`_gradient` with `applyTo: "overlay"`) there, at the element's id. <!-- src: src/elements/hover/hover.css:54 --> <!-- src: Bricks 2.3.10 includes/assets.php:2633-2652 -->
- **The element's own Bricks style wins on a shared property.** The defaults weigh nothing and nothing is `!important`, so a value at the element's id overrides the effect: **Transform** (`_transform`) cancels Tilt, **Opacity** (`_opacity`) holds Fade in, and **Transition** (`_cssTransition`) replaces the one carrying Speed and Delay. <!-- src: src/elements/hover/hover.css:12-13, 19-28, 45 --> <!-- src: Bricks 2.3.10 includes/elements/base.php:731-742, 1421-1428, 1618-1626 -->
- **A block's own Lift, Zoom, Shine or Gradient border ignores the keyboard.** Their self rules use `:focus-visible`, which a plain block never receives, so tabbing to a link inside a lifting card lifts nothing. Parts set to A hovered parent answer focus anywhere in the card. <!-- src: src/elements/hover/hover.css:64-72 -->
- **Fade in, Slide in and Grow wait for a hover.** On a screen that can hover they rest faded, offset or shrunk until played, so on This element a Fade in sits unseen until the pointer happens to cross it. <!-- src: src/elements/hover/hover.css:31-36, 70-72, 76-80 --> <!-- src: docs/elements/hover-effects.md (intro, "for parts of a card") -->
- **Speed times each effect differently.** Shine's sweep lasts three times Speed and plays once per hover; Gradient border fades in over Speed but turns once every 3 s regardless; Tilt and Follow ease back over half of Speed. The panel hides Delay for Tilt and Follow. <!-- src: src/elements/hover/hover.css:28, 46, 68-69 --> <!-- src: plugins/bfb-elements-pro/includes/class-hover-effects.php:189-190 -->
- **Tilt and Follow need their script.** It loads where an element with either renders, and binds again after Bricks' AJAX pagination, page load, query result and popup events. Markup added any other way needs `window.bfbeHover()`. <!-- src: plugins/bfb-elements-pro/includes/class-hover-effects.php:260, 294-297 --> <!-- src: src/elements/hover/hover.js:45-56 -->
- **Switched off, the feature leaves no trace.** With Hover Effects off on the BFB Elements admin screen, no control, attribute or file is added; saved settings stay and work again when it is back on. <!-- src: plugins/bfb-elements-pro/includes/class-plugin.php:148-151, 165-167 -->

## Never do

- Do not set `bfbeHoverOn: "parent"` on an element with no ancestor carrying `bfbeHoverScope: true`.
- Do not tick `bfbeHoverScope` on a section or grid that holds several cards; tick each card.
- Do not count on a card's `bfbeHoverOff` to still its parts; set it on each part too.
- Do not put Zoom on a Bricks `image` that must keep its edges; zoom a block that holds it.
- Do not put Gradient border on an element with a Bricks gradient overlay (`_gradient` with `applyTo: "overlay"`).
- Do not set `_transform` on a Tilt element, `_opacity` on a Fade in element, or `_cssTransition` on any element with an Effect.
- Do not use Fade in, Slide in or Grow without `bfbeHoverOn: "parent"`.
- Do not set `bfbeHoverDelay` on Tilt or Follow; the panel hides it there.
