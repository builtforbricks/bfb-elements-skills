---
name: bfbe-contact-button
description: "Use when adding a floating WhatsApp, call, email or chat button fixed in a page corner with BFB Floating Contact Button (`bfbe-contact-button`), or when setting its menu of actions, speech bubble, opening hours, delayed appearance or click tracking. Read before writing its settings."
---

# BFB Floating Contact Button (`bfbe-contact-button`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-contact-button.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/contact-button/

## What it is
A button fixed in a corner that opens into seven kinds of action: Call, WhatsApp, Email, Text message, Messenger, Telegram and Link. With one action the button is the link itself; with several, it opens a menu that closes on Escape or a click outside. Actions, a speech bubble, opening hours and a delay or scroll trigger each have their own controls.

**Not for:** The button is fixed to a viewport corner, so it always overlays page content there. Every action is a link, such as tel: or mailto:, so a message form needs its own element.

**Costs a page:** CSS 2.05 KB, JS 1.67 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Actions (`bfbeActions`)
- `actions` (repeater) **Actions**. One row per way to reach you. Pick its Type: Call, WhatsApp, Email, Text message, Messenger, Telegram or Link, and fill in Number, address or URL, which accepts dynamic data.
- `track` (checkbox) **Track clicks**. Off by default. Tick it and each click on an action sends a bfbe_contact event, with its channel and label, to window.dataLayer for Tag Manager and GA4.

### Bubble (`bfbeBubble`)
- `bubbleText` (text) **Text**: placeholder None; dynamic data accepted. A short speech-bubble message beside the button. It accepts dynamic data, and it acts as the button when clicked.
- `bubbleDelay` (number) **Show after (s)**: only when `bubbleText` is set. How many seconds before the bubble appears, 3 by default.
- `bubbleScroll` (number) **Or after scrolling (%)**: placeholder Off; only when `bubbleText` is set. Also shows the bubble at this scroll depth, off by default. The bubble appears at whichever comes earlier.
- `bubbleAgain` (select) **Once closed**: options: `session` Stays away this visit (default), `week` Stays away a week, `always` Comes back on the next page; only when `bubbleText` is set. Stays away this visit by default. Choose Stays away a week or Comes back on the next page.
- `bubbleNoClose` (checkbox) **No close button**: only when `bubbleText` is set. Tick it to remove the bubble's cross.
- `bubbleNoTail` (checkbox) **No tail**: only when `bubbleText` is set. Tick it to remove the bubble's small pointer toward the button.
Styling, in the schema file: `bubbleBackground`, `bubbleColor`, `bubbleTypography`, `bubblePadding`, `bubbleWidth`, `bubbleBorder`, `bubbleGap`, `bubbleShadow`.

### Opening hours (`bfbeHours`)
- `hours` (repeater) **Hours**. One row per day. Pick the Day, then tick Closed or type Opens and Closes as 24-hour hh:mm, read in the site's time zone. Empty means always open.
- `closedText` (text) **Closed message**: placeholder Nothing different; dynamic data accepted. Replaces the bubble text outside the hours you listed. Empty means nothing changes.
- `closedHide` (checkbox) **Hide when closed**. Off by default. Tick it and the whole button disappears outside the hours you listed. The hours are rechecked every minute.

### When it appears (`bfbeShow`)
- `showDelay` (number) **Show after (s)**: placeholder At once. The button waits this many seconds before appearing. Empty shows it at once.
- `showScroll` (number) **Or after scrolling (%)**: placeholder Off. Reveals the button at that scroll depth. Whichever trigger fires earlier shows it.

### Button (`bfbeButton`)
- `position` (select) **Corner**: options: `bottom-right` Bottom right (default), `bottom-left` Bottom left, `top-right` Top right, `top-left` Top left. Bottom right is the default, with Bottom left, Top right and Top left as the other choices. Offset sets the distance from the edges, 24px by default.
- `showOn` (select) **Show on**: options: `all` Every screen (default), `phones` Phones only, `large` Larger screens only. Every screen is the default. Phones only and Larger screens only split at Phones are below: 480, 640, 768 or 992 px, 768 px by default.
- `phoneBelow` (select) **Phones are below**: options: `480` 480 px, `640` 640 px, `768` 768 px (default), `992` 992 px; only when `showOn` is not `` or `all`
- `hoverGrow` (select) **On hover**: options: `grow` Grows a little (default), `none` Stays put. Grows a little by default. Choose Stays put to keep the button and the action pills still under the pointer.
- `mainLabel` (text) **Label**: placeholder Icon only; dynamic data accepted. The words shown on the button beside the icon. Left empty, the button shows just the icon, and its hidden name is Contact us, or with one action, that action's name.
- `mainIcon` (icon) **Icon**. With several actions, your own icon for the button in place of the chat icon. With one action, the button shows that action's icon.
Styling, in the schema file: `offset`, `background`, `backgroundHover`, `mainPadding`, `mainBorder`, `shadow`, `iconSize`, `mainIconColor`, `color`, `colorHover`, `mainGap`, `mainTypography`.

### Action pills (`bfbePills`)
- `sameWidth` (checkbox) **Same width**. Tick it to make every pill as wide as the widest. Contents then places each pill's icon and words at the start, center or end.
Styling, in the schema file: `gap`, `actionAlign`, `actionBackground`, `actionBackgroundHover`, `actionPadding`, `actionBorder`, `actionShadow`, `menuOffset`, `pillIconSize`, `actionIconColor`, `actionColor`, `actionColorHover`, `actionGap`, `labelTypography`, `noteTypography`, `wordsGap`, `photoSize`, `photoBorder`.

### Opening (`bfbeMotion`)
- `animEasing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium (default), `cubic-bezier(0.16, 1, 0.3, 1)` Snappy, `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. How they speed up and slow down, Medium by default. Pick Custom and type your own curve in Custom curve.
Styling, in the schema file: `animDuration`, `animEasingCustom`, `animStagger`, `animRise`.

### In the builder (`bfbeBuilder`)
- `builderView` (select) **Show it**: options: `open` Open, so you can style it (default), `closed` Closed, as the site leaves it, `live` Working, as on the site. The actions show open by default, so you can style them. Closed shows the button as the site leaves it. Working lets a click open them in the builder.

## What it guarantees for accessibility (do not undo)
- With several actions the main control is a button with aria-expanded and aria-controls pointing at a list of links.
- Escape closes the open menu from anywhere on the page and returns focus to the main button.
- While the menu is closed its links are hidden with visibility, which keeps them out of the tab order and the accessibility tree.
- With one action the button is a plain link, named by the typed Label or, without one, by that action's label.
- With several actions and an empty Label, the button keeps the hidden name Contact us.
- Icons are aria-hidden and action photos have empty alt text, so each link is named by its label.
- With reduced motion requested, the opening, the rise of the pills and the bubble's fade run with no duration.
<!-- bfbe:generated:end -->

## Rendered DOM

The root is a `div.bfbe-fab`, `position: fixed` at `z-index: 9970`, a flex column holding a row (bubble and button) and, with several actions, a menu. In the bottom corners the column runs in reverse, so the button sits on the corner and the pills open upward; in the top corners they open downward.

```html
<div id="brxe-…" class="brxe-bfbe-contact-button bfbe-fab bfbe-fab--bottom-right bfbe-fab--all" data-bfbe-phone="768">
  <div class="bfbe-fab__row">
    <div class="bfbe-fab__bubble"><button type="button" class="bfbe-fab__bubble-text">…</button><button type="button" class="bfbe-fab__bubble-x" aria-label="Close">…</button></div>
    <button type="button" class="bfbe-fab__main" aria-expanded="false" aria-controls="bfbe-…-menu">
      <span class="bfbe-fab__glyph"><i class="bfbe-fab__icon"></i><svg class="bfbe-fab__x"></svg></span><span class="bfbe-fab__label">Contact us</span>
    </button>
  </div>
  <ul class="bfbe-fab__menu" id="bfbe-…-menu" role="list">
    <li class="bfbe-fab__item bfbe-fab__item--whatsapp" data-bfbe-open-only>
      <a class="bfbe-fab__action bfbe-fab__action--two" href="https://wa.me/…" target="_blank" rel="noopener" data-bfbe-type="whatsapp">
        <i class="bfbe-fab__icon"></i><span class="bfbe-fab__words"><span class="bfbe-fab__label">…</span><span class="bfbe-fab__note">…</span></span>
      </a>
    </li>
  </ul>
</div>
```

- **One action**: no menu and no glyph cell; `.bfbe-fab__main` is an `<a>` with `data-bfbe-type`, the action's icon and a `.bfbe-fab__label`.
- **Pill modifiers**: `bfbe-fab__action--two` with a **Second line** (`note`), `bfbe-fab__action--photo` with a **Photo** (`img.bfbe-fab__photo` in the icon's place). A skipped row leaves an empty `<li hidden>`, so every pill keeps its `:nth-child` place.
- **Root classes from settings**: `bfbe-fab--{corner}`, `bfbe-fab--{all|phones|large}`, `--labelled` (typed Label), `--same-width`, `--still` (On hover: Stays put), `--no-tail`, `--hide-closed`, `--waiting` (until When it appears is due).
- **Read by the script**: `data-bfbe-bubble`, `data-bfbe-show` and `data-bfbe-hours` (JSON), `data-bfbe-closed-text`, `data-bfbe-track`; `data-bfbe-live` only in the builder with Working.
- **States**: `is-open` on the root with `aria-expanded="true"` (the icon turns into `.bfbe-fab__x`), `is-bubble` while the bubble shows, `is-closed` outside opening hours. The closed menu is hidden with `visibility`.
- **Where styling lands**: Background, Colour and their hover controls (button and pills), Offset, the button's Icon size, Space between, Photo size, the bubble's colours, padding and width, and Opening are custom properties on the root (`--bfbe-fab-bg`, `--bfbe-fab-color`, `--bfbe-fab-action`, `--bfbe-fab-icon`, `--bfbe-fab-dur`). Padding, Border, Shadow and Icon gap write to `.bfbe-fab__main` or `.bfbe-fab__action`; the Icon colours and the pills' Icon size to the `.bfbe-fab__icon` inside; bubble Border and Shadow to `.bfbe-fab__bubble`. Unstyled, button and pills take the pack's `--bfbe-accent`.

## Wiring to other elements

Stands alone; nothing targets it and it targets nothing. Three outside contacts:

- **Track clicks** (`track`) pushes `{event: "bfbe_contact", channel, label}` to `window.dataLayer`, where `channel` is the row's Type key (`phone`, `whatsapp`, `email`, `sms`, `messenger`, `telegram`, `link`).
- Under the dark state of **BFB Dark Mode Toggle** (`bfbe-dark-mode`, Pro), the button's default words turn black or white from its fill; a set **Colour** (`color`) wins.
- The script re-runs on Bricks' AJAX and popup events. For markup added any other way, call `window.bfbeContactButton()`.

## Verified patterns

Three ways to reach a shop behind one labelled button, the pills styled apart from the button. From the demo page "ZZ demo: Floating Contact Button", with its sizes, opening hours and closed message trimmed (the hours drove nothing there).

```json
{"name": "bfbe-contact-button", "settings": {
  "position": "bottom-right", "mainLabel": "Message us",
  "background": {"hex": "#6e44ff"}, "color": {"hex": "#ffffff"},
  "actionBackground": {"hex": "#ffffff"}, "actionColor": {"hex": "#101828"},
  "actions": [
    {"type": "whatsapp", "value": "+44 7700 900184", "message": "Hello, could I order a bag of beans?", "label": "WhatsApp"},
    {"type": "phone", "value": "0113 496 0184", "label": "Ring the counter"},
    {"type": "email", "value": "hello@northwind.coffee", "label": "Email"}
  ]
}}
```

A single call button for phones: one row makes the button the `tel:` link itself, with no menu. From the fixture page "FREE: Floating Contact Button".

```json
{"name": "bfbe-contact-button", "settings": {
  "position": "bottom-left", "showOn": "phones", "mainLabel": "Call",
  "actions": [{"type": "phone", "value": "+44 20 7946 0000", "label": "Call us"}]
}}
```

A team menu with a bubble, opening hours and tracking: the two rows marked `openOnly` leave outside the hours, and the bubble switches to `closedText`. From the same fixture, its styling and photo trimmed and the bubble's words shortened; the fixture is open all day for its tests, so the hours here are its own "Weekdays 9 to 5", and the weekend, having no rows, reads as closed.

```json
{"name": "bfbe-contact-button", "settings": {
  "mainLabel": "Chat with us", "sameWidth": true, "track": true,
  "bubbleText": "Questions about a project? We answer fast.", "bubbleDelay": 1, "bubbleAgain": "session",
  "closedText": "We are closed now. Leave a message and we reply tomorrow.",
  "hours": [
    {"day": "mon", "open": "09:00", "close": "17:00"}, {"day": "tue", "open": "09:00", "close": "17:00"},
    {"day": "wed", "open": "09:00", "close": "17:00"}, {"day": "thu", "open": "09:00", "close": "17:00"},
    {"day": "fri", "open": "09:00", "close": "17:00"}
  ],
  "actions": [
    {"type": "whatsapp", "value": "442079460000", "label": "Devon Lane", "note": "Sales, replies in minutes", "openOnly": true},
    {"type": "phone", "value": "+44 20 7946 0000", "label": "Call the desk", "note": "Weekdays 9 to 5", "openOnly": true},
    {"type": "email", "value": "hello@example.com", "label": "Email us", "note": "Any time"}
  ]
}}
```

## Gotchas

- **One action turns the button into the link.** The menu, the pill controls and **Icon** (`mainIcon`) then do nothing, and the row's **Colour** becomes the button's fill over **Background**. That link never opens a new tab, while pills with an `http` address get `target="_blank"`. <!-- src: plugins/bfb-elements/elements/contact-button.php:1037-1044, 1059 -->
- **A row without a usable address is dropped silently.** An empty **Number, address or URL** (`value`), or a scheme WordPress refuses such as `viber:` or `skype:`, removes the row; with no row left the page gets no markup at all. <!-- src: plugins/bfb-elements/elements/contact-button.php:941-963; plugins/bfb-elements/includes/abstract-element.php:538 -->
- **Call, Text message and WhatsApp keep only digits and `+`.** WhatsApp also drops the `+` and builds `https://wa.me/<digits>`, so type the country code. Messenger and Telegram take a bare handle (an `@` is dropped) or a full `https://` address as typed. <!-- src: plugins/bfb-elements/elements/contact-button.php:897-920 -->
- **`mainLabel` is the button's words; a row's `label` is the pill's.** A typed **Label** shows on the button, which widens from a circle to fit it (`bfbe-fab--labelled`). Empty, the button is an icon circle named "Contact us" for screen readers, or the row's label with one action. <!-- src: plugins/bfb-elements/elements/contact-button.php:969-972, 1039-1042; src/elements/contact-button/contact-button.css:133-136 -->
- **Listing any hours closes every day without a row.** A row ticked **Closed**, or with **Opens** or **Closes** not in `hh:mm` form, also reads as closed (`9:00` is fine). A closing time earlier than the opening time runs past midnight. <!-- src: plugins/bfb-elements/elements/contact-button.php:64-82; src/elements/contact-button/contact-button.js:71-73 -->
- **The hours act only through three settings.** They hide the rows marked **Only during opening hours** (`openOnly`), swap the bubble to **Closed message** (`closedText`, which needs `bubbleText`), or hide everything with **Hide when closed** (`closedHide`). With one action marked `openOnly` the whole button goes; with several all marked, an empty menu stays. <!-- src: src/elements/contact-button/contact-button.js:76; src/elements/contact-button/contact-button.css:118-119; plugins/bfb-elements/elements/contact-button.php:1022 -->
- **When it appears hides the whole button, not the bubble.** `showDelay` and `showScroll` keep the root invisible and unclickable (`bfbe-fab--waiting`); unset, it shows at once. The bubble's own delay also counts from page load, so it arrives with the button unless `bubbleDelay` is longer. <!-- src: plugins/bfb-elements/elements/contact-button.php:1003-1008; src/elements/contact-button/contact-button.js:51, 90 -->
- **The bubble remembers by element id, and only through its cross.** Closing it stores the choice under the root's id (`session` for the visit, `week` for seven days). Opening the menu hides it for that page only, and **No close button** (`bubbleNoClose`) brings it back on every page. <!-- src: src/elements/contact-button/contact-button.js:47, 87-96 -->
- **A copy per page asks again on every page.** Each copy has its own id, so a dismissal holds across the site only for one instance in a template every page loads. <!-- src: src/elements/contact-button/contact-button.js:47 -->
- **The canvas is not the page.** In the default **Show it** view (`builderView: "open"`) the element sits in the flow with menu and bubble open, ignores the wait and runs no script; `closed` shows the rest state, and only `live` responds to clicks. <!-- src: src/elements/contact-button/contact-button.css:186-192; src/elements/contact-button/contact-button.js:40-42 -->
- **Two controls act only with another.** **Phones are below** (`phoneBelow`) splits on viewport width, not Bricks' breakpoints, and only with `showOn` at `phones` or `large`. **Contents** (`actionAlign`) writes under `.bfbe-fab--same-width`, so it needs `sameWidth`. <!-- src: src/elements/contact-button/contact-button.css:176-184; plugins/bfb-elements/elements/contact-button.php:684-695 -->
- **A row's Colour paints the pill, not its words.** It sets `--bfbe-fab-action` on that `.bfbe-fab__item:nth-child(n)` over the pills' **Background**, and the words keep the pills' **Colour**, so check the contrast. <!-- src: plugins/bfb-elements/elements/contact-button.php:186-189, 197; docs/API-PROBE.md "8. The `css` control mapping" -->
- **Track clicks needs a data layer already on the page.** The script pushes only when `window.dataLayer` exists and never creates it, so Tag Manager or gtag must be on the page. <!-- src: src/elements/contact-button/contact-button.js:100-103 -->

## Never do

- Do not type a WhatsApp number without its country code.
- Do not use a Link row for a scheme WordPress strips, such as `viber:` or `skype:`.
- Do not add `hours` without `openOnly` rows, `closedText` with a `bubbleText`, or `closedHide`; alone they change nothing.
- Do not leave out a day that should be open once `hours` has rows.
- Do not set `actionAlign` without `sameWidth: true`, or `phoneBelow` with `showOn: "all"`.
- Do not set `bubbleDelay` at or below `showDelay` when the bubble should follow the button.
- Do not place a copy on each page when a closed bubble should stay closed across the site; put one in a template.
- Do not judge the build from the canvas in the Open view; check the front end, or set `builderView: "live"`.
