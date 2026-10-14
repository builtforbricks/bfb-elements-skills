---
name: bfbe-background-masks-and-patterns
description: "Use for a decorative shape or a repeating pattern behind a section's content with BFB Background masks and patterns (`background-masks-and-patterns`): a circle rising off a hero's edge, a wave along a card's foot, faint dots fading out, copies placed exactly. A feature on Bricks' Section, Container, Block and Div, not an element."
---

# BFB Background masks and patterns (`background-masks-and-patterns`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.2.0 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/background-masks-and-patterns.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/background-masks-and-patterns/

## What it is
A feature for Bricks' Section, Container, Block and Div, not an element of its own: the Mask and pattern group on their Style tab lays a shape and a repeating pattern over the element's background, each in a colour, behind its content. 17 shapes fill the element, 6 single shapes are drawn to their own size, and 12 patterns tile it. The layers are decoration, hidden from screen readers and never in the way of a click. There is no script on the page, and one stylesheet loads only where it is used.

**Not for:** Not for a shape outside its element, at an angle or on the move: a shape stays inside the element, turns only with Flip, and holds still. One mask and one pattern per element, and no uploaded SVG. Bricks' own Shape dividers and Image masks keep doing their own jobs.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** no · **Keyboard:** no · **Reduced motion:** no

## Where it lives
A feature, not an element: its controls are added to the Style tab of Bricks' Section, Container, Block and Div (`section`, `container`, `block`, `div`).

## Settings that decide the build

### Mask and pattern (`bfbeBackdrop`)
- `bfbeMask` (select) **Shape**: options: `arch` Arch, `blob` Corner blob, `diagonal` Diagonal, `wave` Wave, `circle` Circle, `ellipse` Ellipse, `half` Curved half, `corner` Corner triangle, `pill` Pill, `steps` Steps, `hills` Hills, `zigzag` Zigzag edge, `bars` Bars, `sun` Rising sun, `rings` Rings, `frame` Frame, `dots` Scattered dots, `one-circle` Single circle, `one-ring` Single ring, `one-square` Single soft square, `one-triangle` Single triangle, `one-blob` Single blob, `one-half` Single half circle. Pick one of 17 shapes that fill the element (Arch, Corner blob, Diagonal, Wave, Circle, Ellipse, Curved half, Corner triangle, Pill, Steps, Hills, Zigzag edge, Bars, Rising sun, Rings, Frame and Scattered dots), or one of 6 single shapes drawn to their own size (Single circle, Single ring, Single soft square, Single triangle, Single blob and Single half circle). The rest of the mask's settings appear.
- `bfbeMaskFit` (select) **Size**: options: `cover` Keep its shape, fill, `contain` Keep its shape, inside, `custom` Width and height; writes CSS; only when `bfbeMask` is set. A single shape keeps its shape unless set.
- `bfbeMaskRepeat` (select) **Repeat**: options: `x` Across, `y` Down, `xy` Across and down; only when `bfbeMask` is set. Lay copies Across, Down, or Across and down. With no Copies set, as many whole copies as fit, spread evenly.
- `bfbeMaskAcross` (select) **Position across**: options: `left` Left, `right` Right; writes CSS; only when `bfbeMask` is set
- `bfbeMaskDown` (select) **Position down**: options: `top` Top, `bottom` Bottom; writes CSS; only when `bfbeMask` is set
- `bfbeMaskFlip` (select) **Flip**: options: `x` Across, `y` Upside down, `xy` Both; only when `bfbeMask` is set. Turn the shape Across, Upside down or Both.
- `bfbeMaskInvert` (checkbox) **Invert**: only when `bfbeMask` is set. Tick it to paint the colour everywhere but the shape.
- `bfbeMaskBlend` (select) **Blend**: options: `multiply` Multiply, `screen` Screen, `overlay` Overlay, `soft-light` Soft light; writes CSS; only when `bfbeMask` is set
- `bfbePattern` (select) **Pattern**: options: `dots` Dots, `grid` Grid, `stripes` Stripes, `checks` Checks, `waves` Waves, `zigzag` Zigzag, `triangles` Triangles, `plus` Plus signs, `diamonds` Diamonds, `rings` Rings, `crosshatch` Crosshatch, `scales` Scales. Pick one of 12: Dots, Grid, Stripes, Checks, Waves, Zigzag, Triangles, Plus signs, Diamonds, Rings, Crosshatch and Scales. The rest of the pattern's settings appear. The pattern lies over the shape.
- `bfbePatternFade` (select) **Fade**: options: `top` Out at the top, `bottom` Out at the bottom, `left` Out to the left, `right` Out to the right, `edges` Out at the edges, `centre` Clear in the middle; only when `bfbePattern` is set. Let the pattern fade Out at the top, Out at the bottom, Out to the left, Out to the right or Out at the edges, or keep it Clear in the middle.
- `bfbePatternBlend` (select) **Blend**: options: `multiply` Multiply, `screen` Screen, `overlay` Overlay, `soft-light` Soft light; writes CSS; only when `bfbePattern` is set
Styling, in the schema file: `bfbeMaskColor`, `bfbeMaskOpacity`, `bfbeMaskWidth`, `bfbeMaskHeight`, `bfbeMaskCopies`, `bfbeMaskSpacing`, `bfbeMaskMoveX`, `bfbeMaskMoveY`, `bfbePatternColor`, `bfbePatternOpacity`, `bfbePatternSize`, `bfbePatternMoveX`, `bfbePatternMoveY`.

## What it guarantees for accessibility (do not undo)
- The shape and the pattern are decoration: hidden from screen readers and never in the Tab order.
- They sit behind the content, so the words stay on top and a button over a shape still takes the click.
- The content does not move, and a position set in Bricks on the element still wins.
<!-- bfbe:generated:end -->

## Rendered DOM

The server writes the choices on the element's own root and puts one empty span per layer first inside it. Nothing else is added, and no script runs on the page. The demo's hero, a Single circle and Dots on a Section:

```html
<section id="brxe-730a42" class="brxe-section" data-bfbe-mask="one-circle" data-bfbe-pattern="dots" data-bfbe-pattern-fade="left"><span class="bfbe-bgl bfbe-bgl--mask" aria-hidden="true"></span><span class="bfbe-bgl bfbe-bgl--pattern" aria-hidden="true"></span><div id="brxe-f68241" class="brxe-container">...</div></section>
```

- **On the root**: `data-bfbe-mask` (the shape's key), `data-bfbe-mask-flip` (`x`, `y`, `xy`), `data-bfbe-mask-invert` (empty), `data-bfbe-mask-repeat` (`x`, `y`, `xy`), `data-bfbe-pattern`, `data-bfbe-pattern-fade`. A value outside the panel's list writes nothing.
- **The layers**: `span.bfbe-bgl.bfbe-bgl--mask` then `span.bfbe-bgl.bfbe-bgl--pattern`, each `aria-hidden="true"` and empty, so the pattern paints over the shape. Each is `position: absolute; inset: 0; z-index: -1; pointer-events: none` and inherits the root's `border-radius`. The root gets `position: relative; isolation: isolate` inside `:where()`, at no specificity.
- **Every other setting is a custom property** Bricks writes at the element's id, so breakpoints, hover states and global classes work as on any control. The demo's: `#brxe-730a42 {--bfbe-mask-c: #6e44ff; --bfbe-mask-fit: var(--bfbe-mask-w, auto) var(--bfbe-mask-h, auto); --bfbe-mask-o2: auto; --bfbe-mask-w: 640px; --bfbe-mask-ax: 100%; --bfbe-mask-mx: 220px; --bfbe-pat-c: rgba(255, 255, 255, 0.11); --bfbe-pat-s: 20px}`, then at the phone breakpoint `--bfbe-mask-w: 240px; --bfbe-mask-ay: 0%; --bfbe-mask-mx: 110px; --bfbe-mask-my: -120px`.
- **The map**: Colour `--bfbe-mask-c`, Opacity `--bfbe-mask-op`, Size `--bfbe-mask-fit` (with `--bfbe-mask-o2: auto` for any Size), Width `--bfbe-mask-w`, Height `--bfbe-mask-h`, Copies `--bfbe-mask-n` and `--bfbe-mask-rep: repeat`, Spacing `--bfbe-mask-gap`, `--bfbe-mask-sp: space` and `--bfbe-mask-slack: 1px`, Position across `--bfbe-mask-ax` (`0%` left, `100%` right), Move across `--bfbe-mask-mx`, Position down `--bfbe-mask-ay`, Move down `--bfbe-mask-my`, Blend `--bfbe-mask-blend`; the pattern's `--bfbe-pat-c`, `--bfbe-pat-op`, `--bfbe-pat-s`, `--bfbe-pat-mx`, `--bfbe-pat-my`, `--bfbe-pat-blend`.
- **The drawing**: each layer is its own `background-color` seen through a CSS mask (an SVG data URI per shape and pattern, all in one stylesheet). Unset, the colour is `currentColor` at 10% for the shape and 14% for the pattern. Flip is a `transform` on the mask layer; Invert adds a full-size second mask composited with `exclude`; Fade adds a gradient composited with `intersect`.
- **Files**: `bfbe-backdrop` (one stylesheet, 2.05 KB gzipped) on pages that use it, nothing on others. In the builder, `bfbe-backdrop-canvas` (0.95 KB) puts the layers into the canvas and follows the panel; `window.bfbeBackdrop` is its hook, and a visitor's page never loads it.

## Wiring to other elements

- **Where it goes.** Only Bricks' `section`, `container`, `block` and `div`, through `bricks/add-element` or `bricks/update-element` like any of their settings. No BFB element and no other Bricks element takes the group.
- **The content.** Whatever is inside the element renders as before, above the layers. Nothing points at anything: no `_cssId` or class is needed.
- **Nested and looped.** A Block inside a masked Section can carry its own mask and pattern; each element gets its own layers, once. In a query loop every item gets its own (`hasLoop` on the masked Block itself works).
- **Colours.** Any Bricks colour object: `{"hex": ...}`, `{"raw": "rgba(...)"}` or a global colour or variable. BFB Dark Mode moves a shape's or pattern's colour with the rest of the page, as it moves any Bricks colour; a see-through colour is left as it is.
- **Bricks' own Shape dividers and Image masks** stay separate and can sit on the same element: a divider draws along an edge, an Image mask clips a picture, this draws behind the content.
- **Custom CSS**: reach a layer with `#brxe-<id> > .bfbe-bgl--mask` (or `--pattern`), or set the custom properties above on a class in `_cssClasses`.

## Verified patterns

**A large circle rising off a hero's edge, faint dots fading out towards the words.** The demo's Section (`demo-bfb-background-masks-and-patterns`), its settings as saved. The circle is 640px, pushed 220px past the right edge; on phones it shrinks to 240px and moves to the top corner. Trimmed: the section's padding and colours, and its children.

```json
{
  "name": "section",
  "settings": {
    "_background": { "color": { "hex": "#101828" } },
    "_typography": { "color": { "hex": "#ffffff" } },
    "bfbeMask": "one-circle",
    "bfbeMaskColor": { "hex": "#6e44ff" },
    "bfbeMaskFit": "custom",
    "bfbeMaskWidth": "640px",
    "bfbeMaskAcross": "right",
    "bfbeMaskMoveX": "220px",
    "bfbeMaskWidth:mobile_landscape": "240px",
    "bfbeMaskDown:mobile_landscape": "top",
    "bfbeMaskMoveX:mobile_landscape": "110px",
    "bfbeMaskMoveY:mobile_landscape": "-120px",
    "bfbePattern": "dots",
    "bfbePatternColor": { "raw": "rgba(255, 255, 255, 0.11)" },
    "bfbePatternSize": "20px",
    "bfbePatternFade": "left"
  },
  "children": [ { "name": "container", "children": [ { "name": "heading", "settings": { "text": "Roasted on Tuesdays, poured all week", "tag": "h1" } } ] } ]
}
```

**A wave in four copies along a panel's foot, and a small circle set into its corner.** The feature visual "Copies placed exactly". The four waves join into one band; the inner Block holds a 72px circle 32px in from its top right corner. Trimmed: the panel's padding, border and text.

```json
{
  "name": "block",
  "settings": {
    "_width": "100%",
    "_height": "560px",
    "_background": { "color": { "hex": "#ffffff" } },
    "bfbeMask": "wave",
    "bfbeMaskColor": { "hex": "#f0ecff" },
    "bfbeMaskRepeat": "x",
    "bfbeMaskCopies": 4
  },
  "children": [
    {
      "name": "block",
      "settings": {
        "_position": "absolute", "_top": "0", "_right": "0", "_width": "160px", "_height": "160px",
        "bfbeMask": "one-circle",
        "bfbeMaskColor": { "hex": "#6e44ff" },
        "bfbeMaskFit": "custom",
        "bfbeMaskWidth": "72px",
        "bfbeMaskAcross": "right",
        "bfbeMaskDown": "top",
        "bfbeMaskMoveX": "-32px",
        "bfbeMaskMoveY": "32px"
      }
    }
  ]
}
```

**A pattern card.** The feature visual "Twelve patterns", one of its six cards: Grid in a faint grey, 22px tiles, fading out towards the name at the foot.

```json
{
  "name": "block",
  "settings": {
    "_height": "240px",
    "_justifyContent": "flex-end",
    "_padding": { "top": "20", "right": "20", "bottom": "20", "left": "20" },
    "_background": { "color": { "hex": "#ffffff" } },
    "bfbePattern": "grid",
    "bfbePatternColor": { "raw": "rgba(16, 24, 40, 0.18)" },
    "bfbePatternSize": "22px",
    "bfbePatternFade": "bottom"
  },
  "children": [ { "name": "text-basic", "settings": { "text": "Grid", "tag": "p" } } ]
}
```

## Gotchas

- **Six choices are one value for every breakpoint.** Shape, Pattern, Repeat, Flip, Invert and Fade are written on the root from the base key alone, so `bfbeMaskRepeat:mobile_portrait` or `bfbeMask:hover` does nothing. Everything else is CSS and takes breakpoints: to show fewer copies on a phone, change `bfbeMaskCopies:mobile_portrait`, not Repeat. <!-- src: plugins/bfb-elements-pro/includes/class-backdrop.php:442-479 -->
- **With Repeat, the copies start at the element's edge along the repeat.** Repeat across puts the first copy at the left whatever Position across and Move across say; they still place the band down the element. Down and Across and down work the same way on their axes. <!-- src: src/elements/backdrop/backdrop.css:62-64 -->
- **Edges join only with Copies.** Without a count, Repeat spreads as many whole copies as fit with even gaps (`space`), so Wave, Hills and Zigzag edge show breaks. With `bfbeMaskCopies` and no Spacing the copies tile edge to edge (`repeat`), each the element's size over the count, and join. Spacing goes back to spreading them. <!-- src: src/elements/backdrop/backdrop.css:17-33; plugins/bfb-elements-pro/includes/class-backdrop.php:246-276 -->
- **Opacity, Copies and Spacing are plain numbers.** Opacity is 0 to 100 (`50`, not `0.5`, which draws at half a percent), Copies 1 to 24, Spacing 0 to 100. The length controls take units, and Bricks adds `px` to a bare number. <!-- src: plugins/bfb-elements-pro/includes/class-backdrop.php:182-192,246-276; src/elements/backdrop/backdrop.css:51 -->
- **A single shape keeps its proportions unless both sides are set.** The `one-*` shapes default to Keep its shape, inside, and a Width alone keeps the proportions. To stretch one, set `bfbeMaskFit: "custom"` with both `bfbeMaskWidth` and `bfbeMaskHeight`. The 17 that fill the element stretch to it by default. <!-- src: src/elements/backdrop/backdrop.css:14-15,47; plugins/bfb-elements-pro/includes/class-backdrop.php:193-232 -->
- **Size and Position on a filling shape are the drawing's board.** The 17 are drawn on one 16:9 board with room round them, so their size and position move the board, not the shape inside it. To place a shape exactly, use a single shape. <!-- src: build/backdrop-shapes.mjs:5-8,38-39 (plugin repository) -->
- **The layers come first inside the element.** Custom CSS such as `#brxe-abc123 > :first-child` or `:nth-child()` now counts the spans. They are absolutely positioned, so flex and grid gaps and the element's own layout ignore them. <!-- src: plugins/bfb-elements-pro/includes/class-backdrop.php:490-507; src/elements/backdrop/backdrop.css:35-41 -->
- **The element becomes its own stacking layer.** `isolation: isolate` keeps the layers behind the content, and means a `z-index` inside the element ranks only among its own content. A position set in Bricks on the element wins over the `relative`. <!-- src: src/elements/backdrop/backdrop.css:10-12 -->
- **Nothing shows outside the element.** A Move past the edge, as in the demo's circle, cuts the shape at the element's box; there is no setting to let it spill or turn it to an angle. <!-- src: src/elements/backdrop/backdrop.css:35-41; bfb-elements docs/MASK-CONTROLS-PROPOSAL-2026-10-13.md "Not offered" -->

## Never do

- Do not put `bfbeMask*` or `bfbePattern*` settings on any element but `section`, `container`, `block` and `div`.
- Do not write a breakpoint or hover key for `bfbeMask`, `bfbePattern`, `bfbeMaskRepeat`, `bfbeMaskFlip`, `bfbeMaskInvert` or `bfbePatternFade`.
- Do not set `bfbeMaskCopies` without `bfbeMaskRepeat`, `bfbeMaskSpacing` without `bfbeMaskCopies`, or `bfbeMaskWidth` and `bfbeMaskHeight` without `bfbeMaskFit: "custom"`: the panel hides them and they are dropped.
- Do not write Opacity as a fraction (`0.5`); it is a percentage.
- Do not add an image, a span or an extra Block to fake a shape behind the content; that is what this group draws.
- Do not give the layers content, focus or a role: they are decoration and stay `aria-hidden`.
