---
name: bfbe-social-share
description: "Use when adding share buttons to a post, page or loop card with BFB Social Share (`bfbe-social-share`): Facebook, X, LinkedIn, Pinterest, WhatsApp, Telegram, Reddit, Email, a copy-link button and the browser's own share sheet, with optional UTM campaign tags. Read before writing its settings."
---

# BFB Social Share (`bfbe-social-share`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-social-share.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/social-share/

## What it is
Share buttons for ten destinations: Facebook, X, LinkedIn, Pinterest, WhatsApp, Telegram, Reddit, Email, Copy link and the browser's own share sheet. Destinations are real links, while Copy link and Share are buttons, and every item is named by its label. Copy link confirms through a polite live region, and the Share button hides itself in browsers without a share sheet.

**Not for:** The element builds share links and a copy action and reads no counts from any network. Each destination opens a network's share dialog, so links to your own profiles need ordinary link elements.

**Costs a page:** CSS 0.95 KB, JS 0.91 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Destinations (`bfbeNetworks`)
- `networks` (repeater) **Destinations**. One row per button. Its Destination is Facebook, X, LinkedIn, Pinterest, WhatsApp, Telegram, Reddit, Email, Copy link or Share. Optional Label, with dynamic data, and Icon replace its own name and icon.
- `show` (select) **Show**: options: `both` Icon and label (default), `icon` Icon only, `label` Label only. Icon and label is the default. Icon only and Label only draw one or the other, and a label hidden from view stays in the page.

### What is shared (`bfbeShared`)
- `shareUrl` (text) **URL**: placeholder Current page; dynamic data accepted. The address people share. It accepts dynamic data. Empty means the current page, or the listing itself on an archive outside a query loop.
- `shareTitle` (text) **Title**: placeholder Current page title; dynamic data accepted. The title sent along with the link. It accepts dynamic data. Empty means the title of the current page.
- `utm` (checkbox) **Campaign tags (UTM)**. Off by default. Tick it to add utm_source, utm_medium and utm_campaign, with the destination's key, such as facebook or email, as the source.
- `utmCampaign` (text) **Campaign**: placeholder share; only when `utm` is set. The utm_campaign value, share by default.
- `utmMedium` (text) **Medium**: placeholder social; only when `utm` is set. The utm_medium value, social by default.

### Arrangement (`bfbeLayout`)
Styling only, every key in the schema file: `direction`, `justify`, `gap`.

### Buttons (`bfbeButtons`)
- `brand` (select) **Brand colours**: options: `none` Off (default), `fill` Always, `hover` On hover. Off by default. Always fills buttons with each network's color, and On hover does it under the pointer or focus. Email, Copy link and Share use the text color.
Styling, in the schema file: `buttonSize`, `typography`, `background`, `border`, `padding`, `shadow`, `hoverColor`, `hoverBackground`.

### Icons (`bfbeIcons`)
Styling only, every key in the schema file: `iconSize`, `iconColor`, `iconGap`.

### Confirmation (`bfbeConfirm`)
- `copiedLabel` (text) **After copying**: placeholder Link copied; dynamic data accepted. The words in the small confirmation bubble, Link copied by default. Screen readers hear them too after Copy link works. It accepts dynamic data.
- `sharedLabel` (text) **After sharing**: placeholder Shared; dynamic data accepted. The same for the Share button once the share sheet completes, Shared by default. Share appears in browsers that have a share sheet.
- `confirmTime` (number) **Shown for (ms)**. How long the confirmation stays, 1500 by default. Pick a value between 300 and 10000.
- `confirmPlace` (select) **Position**: options: `above` Above the button (default), `below` Below the button. Above the button is the default. Choose Below the button when the row sits at the top of the screen.
Styling, in the schema file: `confirmTypography`, `confirmBackground`, `confirmBorder`, `confirmPadding`, `confirmShadow`.

## What it guarantees for accessibility (do not undo)
- The row is a list, destinations are links, and Copy link and Share are buttons, so each answers the keys it normally would.
- Each item is named by its visible label, and with icons alone the label text stays in the page, hidden from sight.
- Copy link and Share write their confirmation into a polite live region, so screen readers announce it while the small bubble is aria-hidden.
- Icons are marked aria-hidden, so a screen reader reads each label and not the icon glyph.
- With reduced motion requested, the confirmation bubble appears and disappears with no transition.
<!-- bfbe:generated:end -->

## Rendered DOM

On the front end (the builder canvas draws `div` for `ul` and `li`, and adds `bfbe-share--canvas` to the root):

```html
<ul id="brxe-abc123" class="brxe-bfbe-social-share bfbe-share bfbe-share--both bfbe-share--toast-above bfbe-share--brand"
    role="list" data-bfbe-copied="Link copied" data-bfbe-shared="Shared" data-bfbe-done-ms="1500">
  <li class="bfbe-share__item bfbe-share__item--facebook">
    <a class="bfbe-share__btn" href="https://www.facebook.com/sharer/sharer.php?u=..." target="_blank" rel="noopener noreferrer">
      <i class="fab fa-facebook-f bfbe-share__icon" aria-hidden="true"></i><span class="bfbe-share__label">Facebook</span>
    </a>
  </li>
  <li class="bfbe-share__item bfbe-share__item--copy">
    <button type="button" class="bfbe-share__btn" data-bfbe-copy="https://...">
      ...icon, label...<span class="bfbe-share__toast" aria-hidden="true">Link copied</span>
    </button>
  </li>
  <li class="bfbe-share__item bfbe-share__item--native is-supported">
    <button type="button" class="bfbe-share__btn" data-bfbe-share="https://..." data-bfbe-title="...">...</button>
  </li>
</ul>
```

- Root modifiers: `bfbe-share--both|icon|label` from **Show** (`show`), `bfbe-share--toast-above|below` from **Position** (`confirmPlace`), `bfbe-share--brand` or `bfbe-share--brand-hover` from **Brand colours** (`brand`), and `bfbe-share--own-word` when `brand` is on and **Typography** sets a colour.
- Each item carries `bfbe-share__item--{key}`. Email is a `mailto:` link in the same tab; the seven networks open a new tab.
- With Icon only the label stays in the button with `bfbe-sr` (hidden from view, still its name); with Label only no icon is printed.
- Script states: `is-done` on a button for `data-bfbe-done-ms` after a copy or share (it shows `.bfbe-share__toast`), and `is-supported` on the `native` item when `navigator.share` exists. One `div.bfbe-sr[aria-live="polite"]` on `body` serves every instance.
- Each button holds its brand colour in `--bfbe-share-brand` (Facebook `#1877f2`, X `#000`); Email, Copy link and Share use `--bfbe-accent`, which is the text colour.
- Where styling lands: `direction`, `justify`, `gap` and `buttonSize` (as `--bfbe-share-size`) on the root, a wrapping flex row; `typography`, `background`, `border`, `padding`, `shadow` and `iconGap` on `.bfbe-share__btn`; `hoverColor` and `hoverBackground` on its `:hover` and `:focus-visible`; `iconSize` and `iconColor` on `.bfbe-share__icon`; every `confirm*` style on `.bfbe-share__toast`.

## Wiring to other elements

Stands alone: no element points at it by attribute and it points at none. Three things touch it.

- **Dark Mode Toggle** (skill `bfbe-dark-mode`): under the toggle's dark state, the default words on a brand fill turn black or white from that fill. In the light, and on a site without the toggle, they stay `Canvas`; a **Typography** colour wins on the network buttons either way.
- **Bricks AJAX**: the script binds every `.bfbe-share` on load and again on `bricks/ajax/pagination/completed`, `bricks/ajax/load_page/completed`, `bricks/ajax/query_result/displayed` and `bricks/ajax/popup/loaded`. Rows inserted by other code need `window.bfbeSocialShare()` called once after they land.
- **Your own CSS**: reach the row through a class in `_cssClasses` (for example `share-row`) or `.bfbe-share`, never `_cssId`. Component instances share an id, and inside a query loop Bricks moves the id into a class.

## Verified patterns

**Article footer chips**, from the demo page "ZZ demo: Social Share" (`/demo-bfb-social-share/`). Icon and label, the default look, with Copy link first and its confirmation below the button. `iconColor` tints the icons; the labels keep the text colour.

```json
{
  "name": "bfbe-social-share",
  "settings": {
    "networks": [
      { "network": "copy" },
      { "network": "email" },
      { "network": "whatsapp" },
      { "network": "facebook" },
      { "network": "x" }
    ],
    "confirmPlace": "below",
    "iconColor": { "hex": "#6e44ff" }
  }
}
```

**Round icon buttons in brand colours**, from the fixture "FREE: Social Share" (`/fixture-social-share/`). `show: "icon"` with `buttonSize: "2.5em"` and zero padding draws fixed circles, and `brand: "fill"` paints each network's colour. The custom label on Copy link is hidden from view and becomes that button's accessible name.

```json
{
  "name": "bfbe-social-share",
  "settings": {
    "show": "icon",
    "buttonSize": "2.5em",
    "padding": { "top": "0", "right": "0", "bottom": "0", "left": "0" },
    "brand": "fill",
    "networks": [
      { "network": "facebook" },
      { "network": "x" },
      { "network": "linkedin" },
      { "network": "pinterest" },
      { "network": "whatsapp" },
      { "network": "telegram" },
      { "network": "reddit" },
      { "network": "email" },
      { "network": "copy", "label": "Grab the link" },
      { "network": "native" }
    ]
  }
}
```

**Text buttons with campaign tags**, from the same fixture. `show: "label"`, 8px corners from the **Border** radius, brand colour on hover, and `utm` with `utmCampaign`, so each shared URL carries `utm_source` (the destination key), `utm_medium=social` and `utm_campaign=launch`. The fixture also sets `shareUrl` and `shareTitle`; left out here, the row shares the current page.

```json
{
  "name": "bfbe-social-share",
  "settings": {
    "show": "label",
    "brand": "hover",
    "border": { "radius": { "top": "8px", "right": "8px", "bottom": "8px", "left": "8px" } },
    "utm": true,
    "utmCampaign": "launch",
    "networks": [
      { "network": "facebook" },
      { "network": "email" },
      { "network": "copy" }
    ]
  }
}
```

## Gotchas

- **Destination keys are exact.** `network` takes `facebook`, `x`, `linkedin`, `pinterest`, `whatsapp`, `telegram`, `reddit`, `email`, `copy` or `native`. Any other value (`twitter`, `share`) drops the row silently, and a row without `network` renders as Facebook. <!-- src: plugins/bfb-elements/elements/social-share.php:37-50, 561-566 -->
- **No rows, no markup.** With `networks` empty the page prints nothing at all; the "Add a destination." notice appears in the builder canvas alone. <!-- src: plugins/bfb-elements/elements/social-share.php:498-502; plugins/bfb-elements/includes/abstract-element.php:538-546 -->
- **The canvas draws divs.** In the builder the root and items are `div` elements, and `ul` and `li` exist on the front end alone. CSS written against `ul` or `li` styles the page and misses the canvas. <!-- src: plugins/bfb-elements/elements/social-share.php:554-559; plugins/bfb-elements/includes/abstract-element.php:411-421 -->
- **The canvas always shows Share; the page may not.** The `native` row stays hidden until the script finds `navigator.share`, and the canvas forces it visible for styling. In a browser without a share sheet the row has one button fewer. <!-- src: src/elements/social-share/social-share.css:67-70; src/elements/social-share/social-share.js:57-58; plugins/bfb-elements/elements/social-share.php:538-542 -->
- **A Background replaces the brand fill but not the brand words.** **Background** (`background`) and **Hover background** (`hoverBackground`) are written with the element's id and outrank the brand fill, while the brand rule still paints icon and label in the contrast colour. Measured: white words on a light grey Facebook button. <!-- src: src/elements/social-share/social-share.css:50-61; plugins/bfb-elements/includes/class-assets.php:89-94; docs/API-PROBE.md section 8 -->
- **Brand colours paint the words themselves.** With `brand` on, the icon and label take the contrast colour directly, so **Hover text colour** (`hoverColor`) on the button reaches neither. A **Typography** colour adds `bfbe-share--own-word`, and the network buttons' words follow the button again. <!-- src: src/elements/social-share/social-share.css:56-64; plugins/bfb-elements/elements/social-share.php:549-552; docs/REVIEW-2026-10-04.md "Free pack B" item 10 -->
- **Icon colour outranks the brand contrast.** **Colour** under Icons (`iconColor`) is written on `.bfbe-share__icon` with the element's id, so it stays unchanged on every brand fill (measured: green on Facebook's blue). <!-- src: plugins/bfb-elements/elements/social-share.php:339-346; src/elements/social-share/social-share.css:59-61 -->
- **In a loop card on an archive, set the Title.** An empty **URL** (`shareUrl`) follows the loop's post, but an empty **Title** (`shareTitle`) reads the post title on a singular page alone. On an archive, a search or the blog page it sends the page's document title, so set `shareTitle: "{post_title}"`. <!-- src: plugins/bfb-elements/elements/social-share.php:504-514 -->
- **Pinterest's image is the featured image, on singular pages.** The pin's `media` is the current post's featured image (size large) on a singular page and absent elsewhere. No control sets it, and a custom **URL** does not change it. <!-- src: plugins/bfb-elements/elements/social-share.php:471-473 -->
- **Campaign tags reach Copy link and Share too.** With `utm` on, Copy link copies the tagged URL with `utm_source=copy`, and Share sends `utm_source=native`. `utmCampaign` and `utmMedium` take effect while `utm` is on and are ignored otherwise. <!-- src: plugins/bfb-elements/elements/social-share.php:516-525, 573-583 -->
- **Size is a floor, for Icon only.** **Size** (`buttonSize`) writes `--bfbe-share-size`, which icon-only buttons alone read as a minimum width and height; a button grows past it when its icon and padding need more room. Corners are the **Border** radius, since there is no shape control. <!-- src: src/elements/social-share/social-share.css:35-38; docs/elements/social-share.md "Round 394" -->
- **The confirmation follows success.** The toast and the announcement come after a completed copy or a completed share; a refused clipboard or a closed share sheet shows nothing. A `confirmTime` under 300 is raised to 300. <!-- src: src/elements/social-share/social-share.js:64-75; plugins/bfb-elements/elements/social-share.php:535 -->

## Never do

- Do not write a `network` value outside the ten keys, or a row without one.
- Do not set `buttonSize` without `show: "icon"`.
- Do not set `background` or `hoverBackground` while `brand` is `fill` or `hover`.
- Do not set `iconColor` with `brand: "fill"`.
- Do not rely on `hoverColor` for the words on a brand fill; set a `typography` colour.
- Do not style the row by tag (`ul`, `li`); use `.bfbe-share`, `.bfbe-share__item` and `.bfbe-share__btn`.
- Do not hide `.bfbe-share__label` with `display: none`: with icons alone it is each button's name.
- Do not make Share (`native`) the row's only destination.
