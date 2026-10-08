---
name: bfbe-contact-button
description: "Use when placing, wiring or styling BFB Floating Contact Button (`bfbe-contact-button`): a button fixed in a corner that opens into seven kinds of action: Call, WhatsApp, Email, Text message, Messenger, Telegram and Link. Read before writing its settings."
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
- `showDelay` (number) **Show after (s)**: placeholder At once. How many seconds before the bubble appears, 3 by default.
- `showScroll` (number) **Or after scrolling (%)**: placeholder Off. Also shows the bubble at this scroll depth, off by default. The bubble appears at whichever comes earlier.

### Button (`bfbeButton`)
- `position` (select) **Corner**: options: `bottom-right` Bottom right (default), `bottom-left` Bottom left, `top-right` Top right, `top-left` Top left. Bottom right is the default, with Bottom left, Top right and Top left as the other choices. Offset sets the distance from the edges, 24px by default.
- `showOn` (select) **Show on**: options: `all` Every screen (default), `phones` Phones only, `large` Larger screens only. Every screen is the default. Phones only and Larger screens only split at Phones are below: 480, 640, 768 or 992 px, 768 px by default.
- `phoneBelow` (select) **Phones are below**: options: `480` 480 px, `640` 640 px, `768` 768 px (default), `992` 992 px; only when `showOn` is not `` or `all`
- `hoverGrow` (select) **On hover**: options: `grow` Grows a little (default), `none` Stays put. Grows a little by default. Choose Stays put to keep the button and the action pills still under the pointer.
- `mainLabel` (text) **Label**: placeholder Icon only; dynamic data accepted. The action's name, or the Type's name when empty. Second line adds a short note under it on the pill, such as Sales, replies in minutes. Both accept dynamic data.
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

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
