---
name: bfbe-breakpoint-canvas
description: "Use when the owner asks about BFB Breakpoint Canvas (`breakpoint-canvas`, Pro), the Bricks builder tool that shows every breakpoint of the page side by side: how to open it (the toolbar button, Shift + B), the infinite canvas, row and grid, click to select, what the read-only frames show and leave out, its defaults (option `bfbe_breakpoint_canvas`), the Bricks lines it is verified on, and what it does not do. A builder tool, not an element: nothing to place."
---

# BFB Breakpoint Canvas (`breakpoint-canvas`)

Read `bfbe-start-here` first. Breakpoint Canvas is for the person editing in the Bricks builder: no ability opens it,
no element carries it, and it changes nothing on the site. An agent explains it, and can read or set its defaults;
it never builds with it.

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.3.0 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/breakpoint-canvas.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/breakpoint-canvas/

## What it is
A builder tool, not an element: every breakpoint of the page side by side in the Bricks builder, on an infinite canvas you pan and zoom, or as frames under Bricks' own canvas in a row or a grid. Click an element in any frame to select it in Bricks and switch to that breakpoint, in every layout. The frames are read-only copies of the canvas without scripts, and it adds nothing to a page.

**Not for:** The frames are read-only: you edit in Bricks' panels, and nothing is typed, dragged or dropped into a frame. Scripts do not run in a frame, so sliders, animations and anything a script draws are checked on the front end. Verified on Bricks 2.3.10 and 2.4.2, measured in Chrome.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** no

## Where it lives
A builder tool, not an element: a button in the Bricks builder's toolbar (and Shift + B) that shows every breakpoint of the page side by side. It adds no control to any element and nothing to a page; its defaults are the WordPress option `bfbe_breakpoint_canvas`, set on its own page in the menu (BFB Elements, Breakpoint Canvas).

## Settings that decide the build

## What it guarantees for accessibility (do not undo)
- Shift + B opens and closes it when the focus is not in a field.
- With the board focused, plus and minus zoom and the arrow keys pan; Shift + 1 fits every frame, Shift + 2 shows the selected element and Shift + 0 goes to 100%.
- Closing from the bar hands the keyboard focus back to the toolbar button.
- It never takes Ctrl or Cmd with plus, minus or 0, the browser's own zoom.
- Space is left to a button or toggle in Bricks' panels or toolbar that has the focus, even with the pointer over the board.
<!-- bfbe:generated:end -->

## Rendered DOM

**Nothing on a page.** Its two files (`bfbe-bc`, about 16 KB of script and 2 KB of CSS gzipped) load on the builder's main window only: never in Bricks' canvas iframe, never on the front end. <!-- src: plugins/bfb-elements-pro/includes/class-breakpoint-canvas.php (enqueue) -->

In the builder, opened:

- **The toolbar button** `[data-bfbe-bc-toggle]` sits between Bricks' refresh and desktop icons, tooltip "Infinite Canvas (Shift + B)". Shift + B toggles it when the focus is not in a field. <!-- src: src/builder/breakpoint-canvas/breakpoint-canvas.js (toolbar button, isTyping) -->
- **The stage** `.bfbe-bc-stage` takes Bricks' preview area: a bar (`.bfbe-bc-bar`) and, by layout:
  - **Infinite canvas** (stored as `overview`, the default): every breakpoint shown plus the base one as page-tall frames on a board (`.bfbe-bc-overview`), widest first, each labelled with its name (top left) and width (top right). Bricks' own canvas stays loaded and driven by Bricks behind the board.
  - **Row** and **Grid**: Bricks' canvas above (`.bfbe-bc-primary`), the other breakpoints as frames under it (`.bfbe-bc-mirrors--row`, one row that scrolls sideways; `--grid`, wrapping).
- **Each frame** is an `<iframe sandbox="allow-same-origin" srcdoc>`: a copy of Bricks' canvas document with no scripts and no builder CSS, at the breakpoint's frame width, scaled. A changed element is replaced in every frame as you edit; other changes trigger a short full refresh ("Refreshing the previews"). <!-- src: src/builder/breakpoint-canvas/breakpoint-canvas.js (mirror library, BUILDER_CHROME, REMOVE_SEL) -->
- **Frame widths.** Desktop-first: a breakpoint's own width, the base at least 1280 (1280, 991, 767, 478 with Bricks' defaults). Mobile-first: the width Bricks itself previews at (477, 768, 992, 1279 with the defaults), or a breakpoint's builder width when set. <!-- src: plugins/bfb-elements-pro/includes/class-breakpoint-canvas.php (breakpoints) -->

## Wiring to other elements

- **Bricks' breakpoints** decide the frames, custom ones included: in Row and Grid one per breakpoint other than the one Bricks' canvas shows (the base included when Bricks is on another, since Pro 1.3.1), on the infinite canvas every one with the base. There is nothing to wire on an element.
- **Click to select.** A click in a frame selects that element in Bricks (it highlights and scrolls to it, the panel opens it) and, in every layout (Pro 1.3.1; before, the infinite canvas only), switches Bricks to that frame's breakpoint by clicking Bricks' own breakpoint button, so the next change in the panel applies to that breakpoint. On the infinite canvas the frame's label shows **Editing**; in Row and Grid, Bricks' own canvas shows that breakpoint and the frames under it become every other one, the base included, so none shows twice. <!-- src: src/builder/breakpoint-canvas/breakpoint-canvas.js:401-430,1740-1750; dev/breakpoint-canvas/canvas.cjs section e -->
- **The only Bricks state it writes** is what selecting needs: `messageOrigin`, `activeId`, `scrollToElementId`, `activePanel`, through one allowlist. It never saves and never writes the active breakpoint. <!-- src: src/builder/breakpoint-canvas/breakpoint-canvas.js:92-146 -->
- **Bricks' preview mode**: the bar and the frames step aside and come back.
- **The defaults** (everyone's starting point) are the option `bfbe_breakpoint_canvas`; the bar's choices are kept per browser (`localStorage` key `bfbe_breakpoint_canvas_ui`) and win over the defaults in that browser.
- **In the builder's console**, `window.bfbeBreakpointCanvas`: `open()`, `close()`, `toggle()`, `isOpen()`, `state()` (layout, size, zoom, the breakpoints shown and each frame; on the infinite canvas also `view: { x, y, zoom }`), `set(partial)` (`layout`, `fit`, `scale`, `breakpoints`, `syncScroll`, `showLabels`, kept for the browser), `refresh()`, and on the infinite canvas `zoomTo(zoom, clientX?, clientY?)`, `fitAll()`, `focus(key)`.

## Verified patterns

The defaults, as the page **BFB Elements, Breakpoint Canvas** saves them (exactly these eight keys; an unknown key is dropped, values are clamped):

| Label | Key | Default and range |
|---|---|---|
| Breakpoints shown | `breakpoints` | `all`, or a list of non-base breakpoint keys (with every one off, all of them open) |
| Layout | `layout` | `overview` (Infinite canvas), `row`, `grid` |
| Size | `fit` | `width` (fit the stage width) or `scale` (Fixed zoom); Row and Grid |
| Fixed zoom | `scale` | 0.5, from 0.2 to 1 |
| Frame height | `frame_height` | 900 px, from 400 to 3000; the page scrolls inside it (Row and Grid) |
| Synced scroll | `sync_scroll` | on (Row and Grid) |
| Labels | `show_labels` | on |
| (none) | `editable` | always `false` |

A site whose editors work mostly on phones and tablets, opening on the row with two frames:

```json
{
  "breakpoints": ["tablet_portrait", "mobile_portrait"],
  "layout": "row",
  "fit": "width",
  "scale": 0.5,
  "frame_height": 900,
  "sync_scroll": true,
  "show_labels": true,
  "editable": false
}
```

Tell the owner where it is: the **Infinite Canvas** button in the builder's toolbar (three screens), or Shift + B; **Fit** or Shift + 1 to see every frame; click an element in a frame to edit it there in Bricks' panels.

## Gotchas

- **Read-only frames.** Nothing is typed, dragged or dropped into a frame; edits happen in Bricks' panels (Row and Grid keep Bricks' own canvas in view for typing and dragging). Editing inside the frames is not in this release.
- **Copies without scripts.** Sliders, interactions, animations and anything a script draws do not run in a frame; links and forms in it never navigate. Check those on the front end at each width.
- **Not the front end.** The frames show what Bricks' canvas renders. What only the front end adds is not there: BFB Dark Mode's colours, for one, since it paints the front end and not the builder.
- **The page's elements only.** A click on an element of the header or footer template in a frame selects nothing; edit a template in its own builder. <!-- src: docs/REVIEW-2026-10-15.md canvas-js-3 -->
- **Media set to play by itself is quiet in the frames (Pro 1.3.1).** A video plays muted in every frame and an audio does not start there; Bricks' own canvas plays them as the page does. Earlier versions played them again in each frame, sound included. <!-- src: src/builder/breakpoint-canvas/breakpoint-canvas.js:510-540,1880; dev/breakpoint-canvas/canvas.cjs section m -->
- **`vh` in a frame is measured against 900 px** on the infinite canvas, so a page-tall frame does not grow with its own height.
- **The Bricks line.** Verified on Bricks 2.3.10 and 2.4.2; at least 2.3.10 to start. A later release of a verified line (2.4.3, say) opens with no note, and the canvas page in the menu says "Newer than Bricks 2.4.2, checked". On another line the bar says "Bricks <version> is not verified yet. The mirrors are read-only and should work; check them against the canvas." When Bricks no longer offers what the frames rely on, the button says "Canvas mirrors need a Bricks version we have verified." and it does not open. <!-- src: plugins/bfb-elements-pro/includes/class-breakpoint-canvas.php:37-46,114-122; plugins/bfb-elements-pro/includes/class-breakpoint-canvas-screen.php:70-76 -->
- **Measured in Chrome only.** Safari, Firefox and touch pinch are not measured.
- **Turned off** (BFB Elements, Elements, Features), the builder has no button and loads no file; its page in the menu stays, says it is off, and keeps the defaults.
- **Pro only.** Without BFB Elements Pro there is no canvas.

## Never do

- Never tell the owner they can type into a frame, or drag between frames.
- Never call the frames a front-end preview.
- Never set `editable` to `true`: it is not read, and the page stores it `false`.
- Never change Bricks' breakpoints to change the frames: the frames follow Bricks' breakpoints, not the other way.
- Never look for an ability that opens the canvas: there is none, by design.
