---
name: bfbe-form-fields
description: "Use when building or styling Bricks' own `form` element with BFB Form Fields (`form-fields`): radio and checkbox options as cards (with descriptions, icons or pictures) or pills, a field shown only when another field has a value, and floating labels. Read before writing its settings."
---

# BFB Form Fields (`form-fields`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/form-fields.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/form-fields/

## What it is
A feature on Bricks' own form element: radio and checkbox fields can show as cards or pills, and any field can wait for another field's value. Cards and pills keep the native radio and checkbox inputs, so each choice stays operable from the keyboard. A field hidden by its condition is disabled, so it is neither required nor sent, and the server drops its answer again on send.

**Not for:** Not for rules beyond one field's value: a condition here reads a single field, so wider tests belong in BFB Advanced Forms. It works on Bricks' own form element, not on BFB Advanced Forms.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** yes · **Reduced motion:** yes

## Where it lives
A feature, not an element: its controls are added to Bricks' own form element (`form`).
It also adds controls to each field of the form (the rows of its `fields` repeater), listed under `fieldControls` in the schema file: `bfbeChoice`, `bfbeChoiceText`, `bfbeChoiceMedia`, `bfbeChoiceSide`, `bfbeShowWhen`, `bfbeShowValue`.

## Settings that decide the build

### Cards and pills (`bfbeFields`)
- `choicePicRatio` (select) **Proportions**: options: `1 / 1` Square, `4 / 3` 4:3, `3 / 2` 3:2, `16 / 9` 16:9, `3 / 4` Upright 3:4; writes CSS. Its own by default, or Square, 4:3, 3:2, 16:9 or Upright 3:4. Once set, Fit chooses Fill, trimmed or Whole, with space, and Border frames the picture.
- `choicePicFit` (select) **Fit**: options: `cover` Fill, trimmed (default), `contain` Whole, with space; writes CSS; only when `choicePicRatio` is set
Styling, in the schema file: `choiceMin`, `choiceColumns`, `choiceGap`, `choicePadding`, `choiceBorder`, `choiceBackground`, `choiceShadow`, `choiceHover`, `choiceAccent`, `choiceChosenBackground`, `choiceChosenText`, `choiceDirection`, `choiceJustify`, `choiceAlignItems`, `choiceInGap`, `choiceIcon`, `choiceIconColor`, `choicePicWidth`, `choicePicBorder`, `choiceTextAlign`, `choiceTitleTypography`, `choiceTextTypography`.

### Floating labels (`bfbeFloat`)
- `labelsAt` (select) **Labels**: options: `above` Above the field (default), `border` Floating, on the border; only when `showLabels` is set. Above the field by default. Choose Floating, on the border, and each label rests inside its empty field, then rises onto the field's top border when the visitor clicks in or types. The group shows once Show labels is on. Floating labels come with Form Fields: with it switched off on the Elements page, labels stay above the field.
Styling, in the schema file: `floatHeight`, `floatInset`, `floatGap`, `floatRestColor`, `floatFocusColor`.

### In the builder (`bfbeBuilder`)
- `floatPreview` (select) **Floating labels**: options: `page` As the page shows them (default), `up` Risen, so you can style them; only when `labelsAt` is `border` and `showLabels` is set

## What it guarantees for accessibility (do not undo)
- Each card is the label of a native radio or checkbox input that stays focusable, so keyboard use is the browser's own.
- A card shows an outline in the accent color when its input has keyboard focus.
- Icons and pictures inside a card are marked aria-hidden, so the option's title is what a screen reader reads.
- A field hidden by a condition is disabled and loses its required attribute, so it leaves the tab order and cannot block the send.
- Under reduced motion cards stop transitioning and no longer lift on hover.
<!-- bfbe:generated:end -->

## Rendered DOM

Bricks draws the form; the server adds marks to Bricks' own markup and `form-fields.js` builds the cards from them. A cards field and a waiting field, after the script:

```html
<form id="brxe-{id}" class="brxe-form bfbe-ff" data-element-id="{id}" data-bfbe-fields="1">
  <div class="form-group" role="radiogroup" aria-labelledby="label-{uid}" data-bfbe-choice="cards"
       data-bfbe-choice-text='["Boilers, bathrooms, servicing.", …]' data-bfbe-choice-media='["<img …>", "<i …></i>", ""]'>
    <div class="label" id="label-{uid}">What do you do</div>
    <ul class="options-wrapper">
      <li>
        <input type="radio" id="form-field-{uid}-0" name="form-field-{fieldId}[]" value="Heating and plumbing">
        <label for="form-field-{uid}-0" class="bfbe-ff__card">
          <img class="bfbe-ff__media bfbe-ff__pic" alt="" aria-hidden="true" loading="lazy" …>
          <span class="bfbe-ff__body"><span class="bfbe-ff__title">Heating and plumbing</span><span class="bfbe-ff__text">Boilers, bathrooms, servicing.</span></span>
        </label>
      </li>
    </ul>
  </div>
  <div class="form-group" role="group" data-bfbe-rule='{"a":"show","m":"all","r":[["ff1now","is","Another system"]]}'>…</div>
</form>
```

- The form root gets `bfbe-ff` and `data-bfbe-fields="1"` once any field uses cards, pills or a condition. In the builder canvas it also gets `data-bfbe-live="1"`, unless Form Steps' `builderView` is `open`.
- A radio or checkbox field's wrapper (`.form-group`) carries `data-bfbe-choice="cards"` or `"pills"`, and `data-bfbe-side="1"` for pills with the question beside them. A cards field adds `data-bfbe-choice-text` and `data-bfbe-choice-media`, JSON lists in option order; each media entry is server-drawn markup, `img.bfbe-ff__pic` (WordPress' image, empty `alt`) or Bricks' icon with `bfbe-ff__icon`.
- The script adds `bfbe-ff__card` to each option's `<label>`, moves its words into `.bfbe-ff__body > .bfbe-ff__title`, adds `.bfbe-ff__text`, and puts the media first with `aria-hidden="true"`. Pills get the card and the title, never a description or media. The native input stays in its `li`, stretched over the whole card at opacity 0, so pressing and focus are the browser's own. A radio or checkbox question is Bricks' `<div class="label">`, not a `<label>`.
- States, all CSS: chosen is `li:has(input:checked)` (border and a 1px inset ring in the accent, Chosen background and text); keyboard focus is `li:has(input:focus-visible)` (a 2px accent outline); hover lifts the card 1px and takes the hover border.
- `.options-wrapper` is a grid, `repeat(auto-fill, minmax(min(160px, 100%), 1fr))` or `--bfbe-ff-cols` once **Per row** is set; for pills it is a wrapping flex row. Each `li` is a block, so a card fills its cell.
- A failing condition: the rules engine (`form.js`, the BFB Form's) sets `data-bfbe-off="1"` and inline `display: none` on the wrapper, disables its inputs and parks `required` as `data-bfbe-req="1"` until the condition holds again.
- Floating labels: the root gets `bfbe-pc--float`, plus `data-bfbe-fl-preview="1"` in the canvas with `floatPreview: "up"`. A floating field's wrapper gets `data-bfbe-float="1"`, its label `.bfbe-fl__label`, its control `.bfbe-fl__input` and `placeholder=" "` where it had none. `form-float.js` marks the box `data-bfbe-fl-box`, writes `--bfbe-fl-*` measurements inline on the wrapper, then adds `data-bfbe-fl-ready`.
- Where controls write: `choiceMin`, `choiceColumns`, `choiceGap`, `choicePadding`, `choiceHover`, `choiceAccent`, `choiceChosenBackground`, `choiceChosenText`, `choiceIcon`, `choiceIconColor` and `choicePicWidth` set `--bfbe-ff-*` on the form root. `choiceBorder`, `choiceBackground` and `choiceShadow` write to `.bfbe-ff__card`; `choiceDirection`, `choiceJustify`, `choiceAlignItems` and `choiceInGap` to a cards field's `.bfbe-ff__card`; `choicePicRatio`, `choicePicFit` and `choicePicBorder` to `.bfbe-ff__pic`; `choiceTextAlign` to a cards field's `.bfbe-ff__body`; `choiceTitleTypography` and `choiceTextTypography` to `.bfbe-ff__title` and `.bfbe-ff__text`. `floatHeight`, `floatInset` and `floatGap` set `--bfbe-fl-height`, `--bfbe-fl-inset` and `--bfbe-fl-gap` on the root. `floatRestColor` colours a resting `.bfbe-fl__label`, `floatFocusColor` the label of a field holding focus.

## Wiring to other elements

The feature lives on Bricks' own `form` element and targets no other element. Its keys sit in two places.

**On each row of the form's `fields` list**, beside Bricks' own `id`, `type`, `label` and `options`:
- **Show the options as** `bfbeChoice`: `list` (the default), `cards` or `pills`, on `radio` and `checkbox` fields.
- **Option descriptions** `bfbeChoiceText` (cards): one line per option, in order. A blank line keeps its place.
- **Icons and pictures** `bfbeChoiceMedia` (cards): rows of `{ "icon": { "library", "icon" } }` or `{ "image": { "id", "size", "url" } }`, one per option, in order. A picture wins over an icon in the same row; an empty row leaves that card its words alone.
- **Question beside the options** `bfbeChoiceSide` (pills): `true` puts the question at the start and the pills at the end of one row.
- **Show only when field** `bfbeShowWhen`: another field's `id` in the same form (a leading `#` is dropped). **Has the value** `bfbeShowValue`: `a`, `a, b` for any of them, `!a` or `!a, b` for none of them, or empty for any answer.

**On the form**, in the **Floating labels** group, offered once Bricks' **Show labels** `showLabels` is on:
- **Labels** `labelsAt`: `above` (the default) or `border`, floating. Then **Height on the border** `floatHeight` (0px centres the label on the line, less is higher), **Inset** `floatInset` (12px), **Gap** `floatGap` (4px), **Resting colour** `floatRestColor` and **Colour while typing** `floatFocusColor`. In the **In the builder** group, **Floating labels** `floatPreview`: `page` (the default) or `up`, which shows every label risen in the canvas and changes nothing on the page.

And:
- **Form Steps** reads the same rows. A field's condition and its step's **Show this step only when field** (`bfbeStepWhen`, `bfbeStepValue`) must both hold; a step whose condition fails has every field hidden. In the canvas the conditions run as on the page, so a waiting field is hidden there too; Form Steps' **Show it** `builderView: "open"` shows every field to style.
- **BFB Advanced Forms** (`bfbe-form`) is a separate form with its own cards, pills, rules and floating labels (the same `labelsAt` and `float*` keys). This feature never acts on it; read the `bfbe-form` skill.
- Style a set of forms by a class in `_cssClasses` (`.quote-form .bfbe-ff__card`), never by `_cssId`: component instances share ids.
- `window.bfbeFormFields()` and `window.bfbeFormFloat()` build again for markup added another way. Both run again by themselves after Bricks loads a popup or query results by AJAX.

## Verified patterns

**Quote request: cards, pill rows and a field that waits** (demo page `demo-bfb-form-fields`). `bfbeChoice: "cards"` with `bfbeChoiceText` gives each trade a description; two `pills` fields with `bfbeChoiceSide` read as question rows. "Which one" appears once "Another system" is chosen.

```json
{
  "name": "form",
  "settings": {
    "showLabels": true, "requiredAsterisk": true, "submitButtonText": "Send it", "actions": ["save-submission"],
    "successMessage": "Thanks. We will come back today with a number.",
    "fields": [
      { "id": "ff1trd", "type": "radio", "label": "What do you do", "required": true, "options": "Heating and plumbing\nElectrical\nRefrigeration", "bfbeChoice": "cards", "bfbeChoiceText": "Boilers, bathrooms, servicing.\nDomestic or commercial.\nCold rooms and cellar cooling." },
      { "id": "ff1siz", "type": "radio", "label": "Engineers on the road", "required": true, "options": "2 to 5\n6 to 15\n16 to 40\nMore", "bfbeChoice": "pills", "bfbeChoiceSide": true },
      { "id": "ff1now", "type": "radio", "label": "Using anything now", "options": "Paper\nSpreadsheets\nAnother system", "bfbeChoice": "pills", "bfbeChoiceSide": true },
      { "id": "ff1wht", "type": "text", "label": "Which one", "placeholder": "The name of it", "bfbeShowWhen": "ff1now", "bfbeShowValue": "Another system" },
      { "id": "ff1eml", "type": "email", "label": "Where to send it", "required": true, "placeholder": "you@firm.co.uk" }
    ]
  }
}
```

**Cards with a picture or an icon, a row on desktop and a column on a phone** (fixture page `fixture-form-fields`, the `ff-phone` form, trimmed to three options). `bfbeChoiceMedia` gives option one a picture, option two a Themify icon and option three nothing; `choiceColumns` puts two cards to a row. `choiceDirection: "row"` sets the picture 72px beside the words, and `choiceDirection:mobile_portrait: "column"` stacks it full width on a phone. The picture's `id` 24628 is the demo site's, and `https://example.com/...` stands in for its address: use an attachment id and URL from the target site's media library.

```json
{
  "name": "form",
  "settings": {
    "showLabels": true, "submitButtonText": "Send", "actions": ["save-submission"], "successMessage": "Sent.",
    "choiceColumns": "2", "choiceDirection": "row", "choiceDirection:mobile_portrait": "column",
    "fields": [
      { "id": "da1bpkg", "type": "radio", "label": "Which package", "options": "Studio\nField\nRemote", "bfbeChoice": "cards",
        "bfbeChoiceText": "In our rooms, with the kit.\nWe come to you.\nOn a call, from anywhere.",
        "bfbeChoiceMedia": [
          { "id": "824a8f", "image": { "id": 24628, "size": "medium", "url": "https://example.com/wp-content/uploads/studio.jpg" } },
          { "id": "e10478", "icon": { "library": "themify", "icon": "ti-bolt" } },
          { "id": "fcdf6b" }
        ] }
    ]
  }
}
```

**Floating labels with their own colours** (fixture page `fixture-form-float`, the `nf-colours` form, trimmed to five fields). `labelsAt: "border"` floats the labels, `floatInset` and `floatGap` move and widen the opening in the border, and the two colours set the resting and the typing label. The dropdown's label is always risen, and the radio field keeps its label above.

```json
{
  "name": "form",
  "settings": {
    "showLabels": true, "labelsAt": "border", "floatInset": "24px", "floatGap": "8px",
    "floatRestColor": { "hex": "#6b4a12" }, "floatFocusColor": { "hex": "#0b6e4f" },
    "submitButtonText": "Send", "actions": ["save-submission"], "successMessage": "Sent.",
    "fields": [
      { "id": "5b2nam", "type": "text", "label": "Your name", "required": true },
      { "id": "5b2eml", "type": "email", "label": "Email", "placeholder": "name@example.com" },
      { "id": "5b2cit", "type": "select", "label": "City", "options": "Iasi\nPascani", "placeholder": "Choose a city" },
      { "id": "5b2msg", "type": "textarea", "label": "Message" },
      { "id": "5b2rad", "type": "radio", "label": "Plan", "options": "Starter\nTeam" }
    ]
  }
}
```

## Gotchas

- **Every field row needs its own `id`.** Bricks names each input `form-field-{id}`: a row with none renders `form-field-[]` with a PHP notice, and no condition can read it. Keep ids to lower-case letters, digits and underscores: a condition lower-cases the id it names and strips anything else, and Bricks does neither. <!-- src: harness render of a row with no id, wp-content/themes/bricks/includes/elements/form.php:3710 ; plugins/bfb-elements-pro/includes/class-form-rules.php:238 ; src/elements/form/form.js:117 -->
- **A watched field must keep Bricks' input name.** Conditions read the inputs named `form-field-{id}`, in the browser and again on the server. Give the watched field Bricks' **Attribute: Name** (`name`) and the condition reads it as empty, whatever the visitor picks. <!-- src: src/elements/form/form.js:117 ; plugins/bfb-elements-pro/includes/class-form-engine.php:333 ; wp-content/themes/bricks/includes/elements/form.php:2970, 3713 -->
- **A condition compares the option's value, not its label.** With Bricks' **Set options as value:label** (`valueLabelOptions`), `DE:Germany` sends `DE`, so **Has the value** must say `DE`. Case is ignored, numbers compare as numbers, and `!` covers the whole list: `!a, b` means neither. <!-- src: src/elements/form/form.js:36-52, 120 ; plugins/bfb-elements-pro/includes/class-form-rules.php:216-235 ; wp-content/themes/bricks/includes/elements/form.php:3702 -->
- **Descriptions and media follow option order.** Line N of `bfbeChoiceText` and row N of `bfbeChoiceMedia` belong to option N, so inserting or reordering an option shifts every card after it. Descriptions are plain text; tags are stripped. <!-- src: plugins/bfb-elements-pro/includes/class-form-fields.php:425-435, 475-482 ; src/elements/form-fields/form-fields.js:19-35 -->
- **Pills ignore the card layout.** **Per row**, **Width, at least**, every **Inside a card** control, descriptions and media act on cards alone. Pills stay one wrapping row of words, each as wide as its own text. <!-- src: src/elements/form-fields/form-fields.css:20-21, 31 ; plugins/bfb-elements-pro/includes/class-form-fields.php:89, 105, 139 ; docs/elements/form-fields.md "Pills are deliberately not in it" -->
- **A colour in Border or Background holds through hover and chosen.** Measured: with a colour in **Border** `choiceBorder`, a chosen card keeps that colour and **Hover border** `choiceHover` does nothing; with **Background** `choiceBackground` set, Chosen **Background** never shows. The control's id-weighted rule outranks the state rules, leaving the 1px inset ring in **Colour** `choiceAccent` to mark the choice, and a **Shadow** `choiceShadow` replaces that ring too. <!-- src: src/elements/form-fields/form-fields.css:32-33 ; plugins/bfb-elements-pro/includes/class-form-fields.php:195-215 ; measured headless on fixture-form-steps-designed and demo-bfb-form-fields, 2026-10-08 -->
- **Chosen Text reaches inherited words alone.** **Text** `choiceChosenText` sets the chosen card's `color`, but a colour in Bricks' **Label typography** `labelTypography` (it styles every `label`, cards included) outranks it, measured. A colour in the card **Typography** `choiceTitleTypography` sits on the title itself, so the title ignores it too. <!-- src: src/elements/form-fields/form-fields.css:33 ; wp-content/themes/bricks/includes/elements/form.php:821-835 ; measured headless on fixture-form-steps-designed, 2026-10-08 -->
- **A picture's width follows `choiceDirection` alone.** As inserted, a picture is the card's width in a column and 72px in a row, read from `--bfbe-ff-row`, which only that control writes, per breakpoint. A flex direction set any other way leaves the picture full width beside the words. <!-- src: src/elements/form-fields/form-fields.css:42-46 ; plugins/bfb-elements-pro/includes/class-form-fields.php:140-142, 249-256 -->
- **A picture comes from its attachment id.** The server draws `image.id` at its `size` (`medium_large` when none) and falls back to `image.url` when that id draws nothing. **Fit** `choicePicFit` is offered once **Proportions** `choicePicRatio` is set; without a ratio the picture keeps its own shape. <!-- src: plugins/bfb-elements-pro/includes/class-form-fields.php:314-336, 453-463 -->
- **Not every field floats.** Text, email, phone, URL, number, password, long text, the date picker and a dropdown with options float, the dropdown always risen since it shows a choice. Radio and checkbox fields (cards and pills too), files, images, rich text, Remember me and a field with no label keep their label above. <!-- src: plugins/bfb-elements-pro/includes/class-form-float.php:22-24, 73-83 ; docs/elements/form.md "Round 447" -->
- **A resting label wears the text colour at 70%.** At rest it takes the field's text size and outranks **Label typography**'s colour, which reaches the risen label alone; set **Resting colour** `floatRestColor`. A box's own **Placeholder** shows once its label has risen. <!-- src: src/elements/form-float/form-float.css:38-45 ; docs/elements/form.md "Floating labels (round 401)", "Round 444" -->
- **A risen label needs room above its field.** It stands half its own height over the field's top border, so the first field needs that much space above it, and the space between fields at least as much. <!-- src: docs/elements/form.md "Known limits" ; src/elements/form-float/form-float.css:22-28 -->

## Never do

- Do not leave a field row without its own `id`, or give a watched field an id with capitals, hyphens or spaces.
- Do not set Bricks' `name` on a field another field's `bfbeShowWhen` names.
- Do not write an option's label in `bfbeShowValue` when `valueLabelOptions` is on; write its value.
- Do not insert or reorder options without moving the matching `bfbeChoiceText` line and `bfbeChoiceMedia` row.
- Do not put a colour in `choiceBorder`, or set `choiceBackground` or `choiceShadow`, when hover and chosen cards must look different.
- Do not set a card's direction with custom CSS; use `choiceDirection`, per breakpoint.
- Do not expect `choiceColumns`, `choiceMin` or the Inside a card controls to change pills.
- Do not set `labelsAt` or a `float*` key without `showLabels: true`.
