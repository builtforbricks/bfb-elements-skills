---
name: bfbe-wishlist-action
description: "Use when placing, wiring or styling BFB Wishlist Action (`bfbe-wishlist-action`). Read before writing its settings."
---

# BFB Wishlist Action (`bfbe-wishlist-action`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-wishlist-action.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/wishlist-action/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Action (`bfbeAction`)
- `act` (select) **Does**: options: `new` Make a new list (default), `pick` Choose the list shown, `rename` Rename the list, `delete` Delete the list, `share` Share link, `registry` Gift registry switch, `surprise` Keep what friends buy a surprise. Shown to a signed-in customer only.
- `newLabel` (text) **Field label**: placeholder New list; only when `act` is `` or `new`
- `newButton` (text) **Button words**: placeholder Create; only when `act` is `` or `new`
- `pickLabel` (text) **Field label**: placeholder Your lists; only when `act` is `pick`
- `pickButton` (text) **Button words**: placeholder Show; only when `act` is `pick`
- `renameLabel` (text) **Field label**: placeholder Name; only when `act` is `rename`
- `renameButton` (text) **Button words**: placeholder Rename; only when `act` is `rename`
- `deleteButton` (text) **Button words**: placeholder Delete this list; only when `act` is `delete`
- `shareMake` (text) **Button words**: placeholder Make a share link; only when `act` is `share`
- `shareLabel` (text) **Field label**: placeholder Share link; only when `act` is `share`
- `shareCopy` (text) **Copy words**: placeholder Copy; only when `act` is `share`
- `shareStop` (text) **Stop words**: placeholder Stop sharing; only when `act` is `share`
- `registryButton` (text) **Button words**: placeholder Gift registry; only when `act` is `registry`
- `surpriseButton` (text) **Button words**: placeholder Keep what friends buy a surprise; only when `act` is `surprise`

### Field (`bfbeField`)
The whole group shows only when `act` is `` or `new` or `pick` or `rename` or `share`.
Styling only, every key in the schema file: `labelTypography`, `fieldTypography`, `fieldBackground`, `fieldBorder`, `fieldPadding`, `fieldWidth`, `fieldFocus`.

### List picker (`bfbeList`)
The whole group shows only when `act` is `pick`.
- `listLook` (select) **Open list**: options: `native` As the browser draws it (default), `custom` Styled with the controls below. Phones keep their own list either way.
Styling, in the schema file: `listChevron`, `listPanelBg`, `listPanelBorder`, `listPanelShadow`, `listPanelPadding`, `listOptTypography`, `listOptPadding`, `listOptHover`, `listHoverText`, `listOptOnBg`, `listOptOnColor`, `listTick`.

### Button (`bfbeLook`)
Styling only, every key in the schema file: `btnType`, `btnBackground`, `btnBorder`, `btnShadow`, `btnPadding`, `hoverBackground`, `hoverColor`, `hoverBorderColor`, `onBackground`, `onColorText`, `onBorderColor`.
<!-- bfbe:generated:end -->

## Rendered DOM

_Not written yet._

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
