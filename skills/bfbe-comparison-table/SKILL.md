---
name: bfbe-comparison-table
description: "Use when placing, wiring or styling BFB Comparison Table (`bfbe-comparison-table`): plans across the top and features down the side, with ticks, crosses or text in each cell. Read before writing its settings."
---

# BFB Comparison Table (`bfbe-comparison-table`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-comparison-table.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/comparison-table/

## What it is
Plans across the top and features down the side, with ticks, crosses or text in each cell. It is a real table with scoped headers, an optional caption, an optional sticky features column and notes behind small buttons. On narrow screens it scrolls sideways, or stacks into one card per feature below a width measured on the table itself.

**Not for:** Plans and features are rows you enter in two repeaters, so it suits a short, hand-written comparison. Records from posts or a file fit a table that reads its rows from a source; this one does not sort or filter.

**Costs a page:** CSS 1.57 KB, JS 0.47 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Plans (`bfbePlans`)
- `plans` (repeater) **Plans**. Add one row per plan. Each row sets its Name, Price, Badge, Highlight, Button label and Link. Name, Price, Badge and Button label take dynamic data.

### Features (`bfbeFeatures`)
- `features` (repeater) **Features**. Add one row per feature. Each row has a Feature name, Per plan values, a Note and Use as a group heading. Feature, Per plan and Note take dynamic data.
Styling, in the schema file: `hintSize`.

### Table (`bfbeTable`)
- `caption` (text) **Caption**: dynamic data accepted. A title shown above the table, which screen readers hear as the table's caption. It takes dynamic data.
- `firstColumn` (text) **Features column heading**: placeholder Features; dynamic data accepted. The words at the top of the features column, Features unless set. It takes dynamic data.
- `sticky` (checkbox) **Sticky features column**. Off by default. Tick it to keep the features column in view while the plan columns scroll sideways beneath it.
- `narrow` (select) **On narrow screens**: options: `scroll` Scroll sideways (default), `cards` One card per feature. Scroll sideways is the default. One card per feature stacks the plans above a card for each feature.
- `stackBelow` (select) **Below**: options: `480` 480px, `640` 640px, `768` 768px (default), `992` 992px; only when `narrow` is `cards`. The width at which cards take over, 768px unless set. It is measured on the table's own container, not the screen.
Styling, in the schema file: `planMinWidth`, `tableMinWidth`.

### Look (`bfbeLook`)
Styling only, every key in the schema file: `highlightBackground`, `highlightColor`, `featureTypography`, `valueTypography`, `groupTypography`, `firstColumnWidth`, `cellPadding`, `tableBackground`, `valueAlign`, `lineColor`, `headBackground`, `featureBackground`, `stripeBackground`, `groupBackground`, `tableBorder`, `hintBackground`, `hintColor`, `captionTypography`, `noteTypography`, `labelTypography`.

### Ticks and crosses (`bfbeMarks`)
- `tickIcon` (icon) **Tick icon**. Pick any icon from the picker to replace the drawn tick. Cross icon does the same for the cross.
- `crossIcon` (icon) **Cross icon**
Styling, in the schema file: `tickColor`, `crossColor`, `iconSize`, `tickBackground`, `crossBackground`, `markPadding`, `markBorder`.

### Plan header (`bfbePlanLook`)
Styling only, every key in the schema file: `headTypography`, `priceTypography`, `badgeTypography`, `badgeBackground`, `badgePadding`, `badgeBorder`, `buttonBackground`, `buttonColor`, `buttonTypography`, `buttonPadding`, `buttonBorder`, `buttonBackgroundHover`, `buttonColorHover`.

## What it guarantees for accessibility (do not undo)
- In the table layout, plan and feature headings are header cells with scope col, row or colgroup.
- A Caption becomes the table's own caption element, and ticks and crosses carry visually hidden text, Yes or No.
- Each note button is a native button with aria-expanded and aria-controls and a hidden name, Details; Enter or Space shows and hides its note.
- Plan buttons are real links in the Tab order, and the plan names repeated for the card layout are hidden from assistive technology.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
