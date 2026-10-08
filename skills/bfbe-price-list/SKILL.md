---
name: bfbe-price-list
description: "Use when placing, wiring or styling BFB Price List (`bfbe-price-list`): a list of menu or service items, each with a title, description, price, optional image, optional struck-through original price and an optional link. Read before writing its settings."
---

# BFB Price List (`bfbe-price-list`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-price-list.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/price-list/

## What it is
A list of menu or service items, each with a title, description, price, optional image, optional struck-through original price and an optional link. A leader line, dotted by default, runs from the title to the price, and any row can be highlighted with its own styling group. Every text field takes dynamic data, and the list can run a query loop.

**Not for:** Each row holds one title, one price and an optional original price, so plans compared across several features need a table with column headings.

**Costs a page:** CSS 0.64 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** no · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Items (`bfbeItems`)
- `items` (repeater) **Items**. One row per item, with Title, Description, Price, Original price, Image, Link and Highlight this item. The text fields accept dynamic data. A row with nothing filled in is skipped.
- `leader` (select) **Leader line**: options: `dots` Dotted (default), `line` Solid, `none` None. The line from title to price. Dotted is the default, with Solid or None as the alternatives. Line colour, Line thickness and Leader offset, 25% by default, adjust it.
Styling, in the schema file: `leaderColor`, `leaderWidth`, `leaderOffset`.

### Item layout (`bfbeLayout`)
- `divided` (checkbox) **Line between items**. Off by default. Tick it to draw a divider between rows, with its own Divider colour and Divider thickness, 1px by default.
Styling, in the schema file: `itemGap`, `dividerColor`, `dividerWidth`, `itemPadding`, `itemBackground`, `itemBorder`.

### Title (`bfbeTitle`)
Styling only, every key in the schema file: `titleTypography`, `titleHoverColor`.

### Description (`bfbeDesc`)
Styling only, every key in the schema file: `descTypography`, `descGap`.

### Price (`bfbePrice`)
Styling only, every key in the schema file: `priceTypography`, `originalTypography`, `priceBackground`, `pricePadding`, `priceBorder`.

### Image (`bfbeImage`)
Styling only, every key in the schema file: `imageSize`, `imageBorder`, `imageGap`.

### Highlighted items (`bfbeHighlight`)
Styling only, every key in the schema file: `highlightBackground`, `highlightBorder`, `highlightPadding`, `highlightShadow`, `highlightTitleTypography`, `highlightDescTypography`, `highlightPriceTypography`, `highlightOriginalColor`, `highlightLeaderColor`, `highlightImageSize`, `highlightImageBorder`.

## What it guarantees for accessibility (do not undo)
- The list is a ul with role list and each row is an li, so screen readers can announce it as a list.
- The leader line is aria-hidden, so a screen reader reads each title and then its price without the dots.
- A title with a Link becomes a real anchor that shows an underline on hover and on keyboard focus.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
