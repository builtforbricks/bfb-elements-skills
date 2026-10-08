---
name: bfbe-form-fields
description: "Use when placing, wiring or styling BFB Form Fields (`form-fields`): a feature on Bricks' own form element: radio and checkbox fields can show as cards or pills, and any field can wait for another field's value. Read before writing its settings."
---

# BFB Form Fields (`form-fields`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/form-fields.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/form-fields/

## What it is
A feature on Bricks' own form element: radio and checkbox fields can show as cards or pills, and any field can wait for another field's value. Cards and pills keep the native radio and checkbox inputs, so each choice stays operable from the keyboard. A field hidden by its condition is disabled, so it is neither required nor sent, and the server drops its answer again on send.

**Not for:** Not for rules beyond one field's value: a condition here reads a single field, so wider tests belong in BFB Advanced Forms. It works on Bricks' own form element, not on BFB Advanced Forms.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Where it lives
A feature, not an element: its controls are added to Bricks' own form element (`form`).

## Settings that decide the build

### Cards and pills (`bfbeFields`)
- `choicePicRatio` (select) **Proportions**: options: `1 / 1` Square, `4 / 3` 4:3, `3 / 2` 3:2, `16 / 9` 16:9, `3 / 4` Upright 3:4; writes CSS. Its own by default, or Square, 4:3, 3:2, 16:9 or Upright 3:4. Once set, Fit chooses Fill, trimmed or Whole, with space, and Border frames the picture.
- `choicePicFit` (select) **Fit**: options: `cover` Fill, trimmed (default), `contain` Whole, with space; writes CSS; only when `choicePicRatio` is set
Styling, in the schema file: `choiceMin`, `choiceColumns`, `choiceGap`, `choicePadding`, `choiceBorder`, `choiceBackground`, `choiceShadow`, `choiceHover`, `choiceAccent`, `choiceChosenBackground`, `choiceChosenText`, `choiceDirection`, `choiceJustify`, `choiceAlignItems`, `choiceInGap`, `choiceIcon`, `choiceIconColor`, `choicePicWidth`, `choicePicBorder`, `choiceTextAlign`, `choiceTitleTypography`, `choiceTextTypography`.

## What it guarantees for accessibility (do not undo)
- Each card is the label of a native radio or checkbox input that stays focusable, so keyboard use is the browser's own.
- A card shows an outline in the accent color when its input has keyboard focus.
- Icons and pictures inside a card are marked aria-hidden, so the option's title is what a screen reader reads.
- A field hidden by a condition is disabled and loses its required attribute, so it leaves the tab order and cannot block the send.
- Under reduced motion cards stop transitioning and no longer lift on hover.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
