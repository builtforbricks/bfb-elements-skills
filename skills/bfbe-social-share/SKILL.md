---
name: bfbe-social-share
description: "Use when placing, wiring or styling BFB Social Share (`bfbe-social-share`): share buttons for ten destinations: Facebook, X, LinkedIn, Pinterest, WhatsApp, Telegram, Reddit, Email, Copy link and the browser's own share sheet. Read before writing its settings."
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

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
