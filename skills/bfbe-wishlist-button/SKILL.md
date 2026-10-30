---
name: bfbe-wishlist-button
description: "Use when placing, wiring or styling BFB Wishlist Button (`bfbe-wishlist-button`). Read before writing its settings."
---

# BFB Wishlist Button (`bfbe-wishlist-button`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-wishlist-button.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/wishlist-button/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

**Costs a page:** CSS 1.02 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Ungrouped
- `shows` (select) **Shows**: options: `button` The button (default), `count` A count for the header

### Button (`bfbeButton`)
The whole group shows only when `shows` is not `count`.
- `postType` (select) **Saves**: options: `product` Products (default), `post` Posts, `page` Pages, `bfbe_shop_review` Shop Reviews, `bfbe_review` Review, `bfbe_demo` Demos, `bfbe_feature` Feature visuals, `bfbe_fixture` Fixtures, `bfbe_sweep` Sweeps, `bfbe_scratch` Scratch, `bricks_template` My Templates
- `textAdd` (text) **Words to add**: placeholder Add to wishlist; dynamic data accepted
- `textOn` (text) **Words when saved**: placeholder In your wishlist; dynamic data accepted
- `content` (select) **Button shows**: options: `both` Icon and words (default), `icon` Icon only, `words` Words only
- `iconAdd` (icon) **Icon to add**: only when `content` is not `words`
- `iconOn` (icon) **Icon when saved**: only when `content` is not `words`

### Header count (`bfbeCount`)
The whole group shows only when `shows` is `count`.
- `countHide` (select) **Hide while empty**: options: `on` On (default), `off` Off. Appears once something is added, with no reload.
- `countPlace` (select) **Badge place**: options: `corner` Over the icon corner (default), `beside` Beside the icon
- `countIcon` (icon) **Icon**
Styling, in the schema file: `countIconSize`, `countIconColor`, `countBadgeBg`, `countBadgeColor`, `countBadgeSize`, `countBadgeBorder`, `countBadgeTypography`.

### Look (`bfbeLook`)
The whole group shows only when `shows` is not `count`.
- `iconPlace` (select) **Icon sits**: options: `row` Before the words (default), `row-reverse` After the words; writes CSS; only when `content` is not `icon` or `words`
Styling, in the schema file: `btnType`, `btnBackground`, `btnBorder`, `btnShadow`, `btnPadding`, `hoverBackground`, `hoverColor`, `hoverBorderColor`, `iconSize`, `iconColor`, `gap`, `onBackground`, `onColorText`, `onBorderColor`, `onColor`.
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
