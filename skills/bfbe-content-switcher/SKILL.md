---
name: bfbe-content-switcher
description: "Use when placing, wiring or styling BFB Content Switcher (`bfbe-content-switcher`): two or more nested panels behind a pill toggle, the monthly and yearly pricing pattern. Read before writing its settings."
---

# BFB Content Switcher (`bfbe-content-switcher`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-content-switcher.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/content-switcher/

## What it is
Two or more nested panels behind a pill toggle, the monthly and yearly pricing pattern. The toggle follows the tabs pattern with one Tab stop and arrow keys between options, and each option can carry a badge. A choice can be written into the address as a hash and remembered in the visitor's browser.

**Not for:** Every panel is in the page, matched to its option by position, so all of their markup is delivered and one is visible. It suits a few short options such as monthly and yearly, not content that should load on demand.

**Costs a page:** CSS 1.00 KB, JS 1.39 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-content-switcher",
    "settings": {},
    "children": [
        {
            "name": "block",
            "settings": {},
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "Monthly",
                        "tag": "h3"
                    }
                }
            ]
        },
        {
            "name": "block",
            "settings": {},
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "Yearly",
                        "tag": "h3"
                    }
                }
            ]
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Options (`bfbeOptions`)
- `options` (repeater) **Options**. Add one row per option with a Label and a Badge, both taking dynamic data. Each row controls the nested block in the same position.
- `active` (number) **Selected at first**. Choose the option shown on load, 1 unless set. A number past the last option selects the last one.
- `hash` (checkbox) **Link with a hash**. Tick it to write a chosen option's label into the address, such as #yearly, so visiting that address selects it.
- `remember` (checkbox) **Remember the choice**. Tick it to keep the choice in the visitor's browser. With Link with a hash ticked, a hash in the address overrides it.
Styling, in the schema file: `align`.

### Toggle (`bfbeToggle`)
- `tabsOverflow` (select) **Overflow**: options: `wrap` Wrap (default), `scroll` Scroll sideways. Wrap, the default, puts options that do not fit on new lines. Scroll sideways keeps one row that scrolls.
Styling, in the schema file: `toggleBackground`, `toggleBorder`, `togglePadding`, `panelsGap`, `tabGap`.

### Option (`bfbeOption`)
Styling only, every key in the schema file: `tabTypography`, `tabPadding`, `tabRadius`, `tabBackgroundHover`, `activeBackground`, `activeColor`.

### Badge (`bfbeBadge`)
Styling only, every key in the schema file: `badgeTypography`, `badgeBackground`, `badgeColor`, `badgePadding`, `badgeBorder`, `badgeSelectedBackground`, `badgeSelectedColor`.

### Motion (`bfbeMotion`)
- `pillMotion` (select) **Pill**: options: `slide` Slides to the chosen option (default), `none` Switches at once. The pill Slides to the chosen option by default. Pick Switches at once for no movement.
- `panelEffect` (select) **Panel effect**: options: `none` None (default), `fade` Fade, `rise` Rise. None is the default. Fade or Rise animates the arriving panel while the one leaving disappears at once.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Choose from the list or set a custom curve, Snappy by default. The pill and the panel share it.
Styling, in the schema file: `duration`, `easingCustom`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Stacked, so you can style them (default), `closed` Closed, as the site leaves it, `live` Working, as on the site. Stacked, the default, lays every panel out for styling, Closed matches the site at rest, and Working lets the tabs switch panels in the canvas.

## What it guarantees for accessibility (do not undo)
- The toggle is a tablist; each option is a tab with aria-selected and aria-controls, and each panel is a tabpanel labeled by its tab.
- Arrow keys move between options and wrap round, Home and End jump to the ends, and the selected tab is the one Tab stop.
- Panels that are not selected carry the hidden attribute and display none, so assistive technology reads the chosen panel alone.
- Under reduced motion the sliding pill and the panel effect run with no duration, so the change is immediate.
<!-- bfbe:generated:end -->

## Rendered DOM

The fixture's monthly and yearly switcher, after the script has run (`is-ready`, the panel roles and the hiding are the script's):

```html
<div id="brxe-eb64f9" class="brxe-bfbe-content-switcher bfbe-switch bfbe-switch--fx-none is-ready"
     data-bfbe-active="1" data-bfbe-overflow="scroll" data-bfbe-pill="1" data-bfbe-hash="1" data-bfbe-remember="1">
  <div class="bfbe-switch__bar">
    <div class="bfbe-switch__tabs" role="tablist">
      <button type="button" role="tab" class="bfbe-switch__tab is-selected" id="bfbe-eb64f9-t0" aria-selected="true"
              tabindex="0" aria-controls="brxe-0970c1" data-bfbe-slug="monthly"><span>Monthly</span></button>
      <button type="button" role="tab" class="bfbe-switch__tab" id="bfbe-eb64f9-t1" aria-selected="false" tabindex="-1"
              aria-controls="brxe-1400ca" data-bfbe-slug="yearly"><span>Yearly</span><span class="bfbe-switch__badge">Save 20%</span></button>
    </div>
  </div>
  <div class="bfbe-switch__panels">
    <div id="brxe-0970c1" class="brxe-block" role="tabpanel" aria-labelledby="bfbe-eb64f9-t0">...</div>
    <div id="brxe-1400ca" class="brxe-block" role="tabpanel" aria-labelledby="bfbe-eb64f9-t1" hidden style="display: none;">...</div>
  </div>
</div>
```

- Root data: `data-bfbe-active` (from 1, clamped to the options), `data-bfbe-pill` (`1` slides, `0` at once), `data-bfbe-overflow` (`wrap` or `scroll`); `data-bfbe-hash` and `data-bfbe-remember` only when ticked; `data-bfbe-live` in the builder's Working view.
- Root classes: `bfbe-switch--fx-none`, `--fx-fade` or `--fx-rise` from **Panel effect**; `bfbe-switch--canvas` in the builder's Stacked view; `is-ready` once the script has run.
- The tabs are `<button>`s the element draws, not nested elements. A tab's id is `bfbe-<id>-t<n>`, counted from 0; `data-bfbe-slug` is its hash word. Selected: `.is-selected`, `aria-selected="true"`, `tabindex="0"`.
- The panels are the direct children of `.bfbe-switch__panels`, matched to tabs by position. Before the script runs, the stylesheet shows the one panel **Selected at first** names, up to the fourth; past that, panel one.
- The sliding pill is `.bfbe-switch__tabs::before`, sized and moved by `--bfbe-switch-pill-x`, `-y`, `-w`, `-h` on the tab list.
- Where controls write: `align` to `.bfbe-switch__bar`; `toggleBackground`, `toggleBorder`, `togglePadding`, `tabGap` to `.bfbe-switch__tabs`; `panelsGap` to the root's `gap`; `tabTypography`, `tabPadding` to `.bfbe-switch__tab`; `tabRadius` to the tab and `--bfbe-switch-pill-radius`; `activeBackground`, `activeColor`, `tabBackgroundHover` to root variables `--bfbe-switch-on-bg`, `--bfbe-switch-on-color`, `--bfbe-switch-hover-bg`; the badge controls to `.bfbe-switch__badge`, its two Selected ones to `.bfbe-switch__tab.is-selected .bfbe-switch__badge`.

## Wiring to other elements

- Its panels are its own direct children, by position. No other BFB element targets it, and it targets none.
- **In, by hash.** With **Link with a hash** `hash: true`, an address ending `#<slug>` selects that option on load. The slug is the label lower-cased with hyphens (`In the van` becomes `#in-the-van`), or `option-<n>` from 1 when two labels share one. Link from another page, as a Bricks `button` with link `/pricing/#yearly`.
- **Out, by event.** Each selection dispatches `bfbe/switch` on the root, bubbling, with `detail.index` counted from 0. It also fires once at start-up, so a listener added later reads `.bfbe-switch__tab[aria-selected="true"]` for the current option.
- Find the switcher by class: set `_cssClasses: "pricing-switch"` and listen on `.pricing-switch`. Never `_cssId`: component instances share ids, and Bricks drops the `id` inside a query loop.
- **Re-running.** `window.bfbeContentSwitcher()` initialises every `.bfbe-switch`; the script calls it after `bricks/ajax/pagination/completed`, `bricks/ajax/load_page/completed`, `bricks/ajax/query_result/displayed` and `bricks/ajax/popup/loaded`, so a switcher in an AJAX popup works.
- **BFB Dark Mode Toggle.** In its dark state the selected option's words turn black or white from the fill, unless **Selected text** `activeColor` is set.

## Verified patterns

**Three audiences, styled.** From the demo page `demo-bfb-content-switcher`: dark pill, white words, a violet "New" badge on the third option, 40px under the toggle. The demo's panels hold an image, a video and buttons; here each is trimmed to a heading and a line. `toggleBackground` and `badgeSelectedBackground` are given as `{"color": {...}}`, the shape a Background control writes CSS from.

```json
{
  "name": "bfbe-content-switcher",
  "settings": {
    "options": [{"label": "In the office"}, {"label": "In the van"}, {"label": "For the customer", "badge": "New"}],
    "align": "center",
    "panelsGap": "40px",
    "toggleBackground": {"color": {"hex": "#f7f8fa"}},
    "activeBackground": {"hex": "#101828"},
    "activeColor": {"hex": "#ffffff"},
    "badgeBackground": {"hex": "#6e44ff"},
    "badgeColor": {"hex": "#ffffff"},
    "badgeSelectedBackground": {"color": {"hex": "#6e44ff"}},
    "badgeSelectedColor": {"hex": "#ffffff"}
  },
  "children": [
    {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Book it once", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Drag a job onto an engineer and the board settles the rest.", "tag": "p"}}]},
    {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "The job in a pocket", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "Address, history, parts and notes, with or without signal.", "tag": "p"}}]},
    {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "They know when", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "A text the morning of, and a map that shows the van getting closer.", "tag": "p"}}]}
  ]
}
```

**Monthly and yearly prices, linkable and remembered.** From the fixture page `fixture-content-switcher`. `hash` makes `#yearly` open the yearly panel, `remember` keeps the visitor's pick, and Scroll sideways holds one row on a phone. The class `pricing-switch` is added for the event in Wiring.

```json
{
  "name": "bfbe-content-switcher",
  "settings": {
    "options": [{"label": "Monthly"}, {"label": "Yearly", "badge": "Save 20%"}],
    "hash": true,
    "remember": true,
    "tabsOverflow": "scroll",
    "_cssClasses": "pricing-switch"
  },
  "children": [
    {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Monthly plan", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "£9 a month."}}]},
    {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Yearly plan", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "£86 a year."}}]}
  ]
}
```

**Three plans, the middle one first, no slide.** From the fixture page `fixture-content-switcher`. `active: 2` opens on Pro, and `pillMotion: "none"` paints the selected tab itself instead of sliding the pill.

```json
{
  "name": "bfbe-content-switcher",
  "settings": {
    "options": [{"label": "Starter"}, {"label": "Pro", "badge": "Popular"}, {"label": "Agency"}],
    "active": 2,
    "pillMotion": "none"
  },
  "children": [
    {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Starter", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "For one site."}}]},
    {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Pro", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "For a few."}}]},
    {"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Agency", "tag": "h3"}}, {"name": "text-basic", "settings": {"text": "For all of them."}}]}
  ]
}
```

## Gotchas

- **No options, no output.** The insert tree has `settings: {}`, and with `options` empty the page renders nothing; the canvas shows "Add an option." Add one row per nested block. <!-- src: plugins/bfb-elements-pro/elements/content-switcher.php:350 -->
- **Every direct child is a panel.** Panels are matched to options by position among the switcher's direct children, whatever element they are, so a heading placed inside the switcher becomes panel one. <!-- src: src/elements/content-switcher/content-switcher.js:29 -->
- **Counts must match, and only the canvas says so.** A block past the last option stays hidden and unreachable; an option with no block shows nothing. The "One nested block per option." notice is builder-only. <!-- src: plugins/bfb-elements-pro/elements/content-switcher.php:406; src/elements/content-switcher/content-switcher.js:72 -->
- **Two Background controls need a colour object.** `toggleBackground` and `badgeSelectedBackground` take `{"color": {"hex": "..."}}`; a bare `{"hex": "..."}` is stored and writes no CSS. The Color controls (`activeBackground`, `badgeBackground`) take `{"hex": "..."}`. <!-- src: plugins/bfb-elements-pro/elements/content-switcher.php:108, :279; bricks/includes/assets.php:2038, measured 2026-10-08 with Assets::generate_inline_css_from_element -->
- **The pill is the selected background.** With **Pill** `pillMotion` on its default slide, the fill is `.bfbe-switch__tabs::before` and the selected tab goes transparent. **Selected background** `activeBackground` feeds both. <!-- src: src/elements/content-switcher/content-switcher.css:32 -->
- **Option corners come from Radius, the toggle's from Border.** `tabRadius` rounds the tabs and the pill together; the toggle has no radius control, its corners are in **Border** `toggleBorder`. <!-- src: docs/elements/content-switcher.md "No radius-only control (round 390)"; plugins/bfb-elements-pro/elements/content-switcher.php:161 -->
- **Typography's colour misses the selected option.** The selected option's words take **Selected text** `activeColor`, set on its children, so the colour in `tabTypography` shows on the others only. <!-- src: src/elements/content-switcher/content-switcher.css:66 -->
- **Badge colours hold when selected.** `badgeBackground` and `badgeColor` are written under the element's id and outrank the stylesheet's selected tint. Set `badgeSelectedBackground` and `badgeSelectedColor` for a different selected badge. <!-- src: src/elements/content-switcher/content-switcher.css:77; docs/API-PROBE.md section 8 -->
- **The hash is read once.** The script reads the address on load and has no hash-change listener, so an in-page link to `#yearly` does nothing after load. It writes the hash only when a visitor picks, with no history entry. <!-- src: src/elements/content-switcher/content-switcher.js:75, :102 -->
- **Two counts.** `active` counts from 1; the tab ids and `detail.index` of `bfbe/switch` count from 0. <!-- src: src/elements/content-switcher/content-switcher.js:78, :98 -->
- **Hidden panels are hidden inline.** The script sets `hidden` and inline `display: none`, so a Display set on a panel block survives for the shown panel. A `display` with `!important` beats it and shows every panel. <!-- src: docs/elements/content-switcher.md "Hiding (2026-09-12)"; src/elements/content-switcher/content-switcher.js:68 -->
- **The canvas is not the page.** **Show it** `builderView` defaults to Stacked: every panel shown, no panel effect. Closed shows one panel with dead tabs; Working switches. A new **Panel effect** shows in the canvas only after save and reload. <!-- src: docs/elements/content-switcher.md "Closed showed every panel" and "A structural control and the builder canvas"; docs/API-PROBE.md section 24 -->

## Never do

- Do not leave `options` empty or out of step with the nested blocks: one row per block, in the same order.
- Do not put a heading, intro or button as a direct child of the switcher; place it outside, because every direct child is a panel.
- Do not write `toggleBackground` or `badgeSelectedBackground` as a bare `{"hex": ...}`; wrap it in `{"color": ...}`.
- Do not paint or round `.bfbe-switch__tab` with custom CSS; use `activeBackground`, `activeColor` and `tabRadius`, which the pill follows.
- Do not give a panel block `display` with `!important`.
- Do not find the switcher or a panel by `_cssId`; use a class in `_cssClasses`.
- Do not count on an in-page `#slug` link to switch it after the page has loaded.
- Do not set `role`, `tabindex` or `aria-*` attributes on the panel blocks; the script sets them.
