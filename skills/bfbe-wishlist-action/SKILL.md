---
name: bfbe-wishlist-action
description: "Use when placing one wishlist action for customers (choose a list, new list, rename, delete, share link, gift registry, surprise) in the lists bar or anywhere on the page, with BFB Wishlist Action (`bfbe-wishlist-action`). Read before writing its settings."
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

One root per action, holding one or two small forms. **Does** `act: "new"` (the default):

```html
<div id="brxe-{id}" class="brxe-bfbe-wishlist-action bfbe-wlact bfbe-wlact--new">
  <form method="post" class="bfbe-wlact__form">
    <input type="hidden" name="bfbe_shop_act" value="list_new"><input type="hidden" name="_bfbe_nonce" value="…">
    <label class="bfbe-wlact__label" for="{uid}-new">New list</label>
    <input class="bfbe-wlact__field" id="{uid}-new" name="name" maxlength="60" required>
    <button type="submit" class="bfbe-list__btn bfbe-wlact__btn">Create</button>
  </form>
</div>
```

- The root is `bfbe-wlact bfbe-wlact--<act>`, a wrapping flex row (`gap: 8px`, `align-items: stretch`). The form is `display: contents`, so the label, the field and the button are the root's own flex items.
- `.bfbe-wlact__label` takes a line of its own (`flex-basis: 100%`); the field (`inline-size: 12em`) and its button share the next, the button as tall as the field.
- `pick`: a `select.bfbe-wlact__field` named `list`, one option per list; with **Open list** `listLook: "custom"` it sits in `span.bfbe-dd.bfbe-dd__field[data-bfbe-dd]`. `rename`: an `input` filled with the list's name, plus a hidden `list`.
- `delete`: one `button.bfbe-wlact__btn--quiet`. `registry` and `surprise`: one button with `aria-pressed="true|false"`, posting the opposite state.
- `share` before a link: one button, **Make a share link**. After: the label, `input.bfbe-wlact__field.bfbe-wlact__share[readonly]` with the address, `button[data-bfbe-copy-from][data-bfbe-copied="Link copied."][hidden]` (Copy), and a form with **Stop sharing** (`--quiet`).
- Where the groups write: Field to `.bfbe-wlact__label` and `.bfbe-wlact__field` (`fieldWidth` is `inline-size`, `fieldFocus` the `:focus` border colour); List picker to the select and its open list; Button keys to `.bfbe-list__btn`, with `btnBackground` and `onBackground` as `--bfbe-list-bg` and `--bfbe-list-on-bg` on the root, and `onColorText`, `onBorderColor` on `[aria-pressed="true"]`.
- The button is the one the Wishlist, Compare and Quote List Buttons share (`list-button.css`), without the icon.

## Wiring to other elements

- **The list in hand.** Every action acts on the customer's current list: the one `pick` last chose or `new` last made. That list is also what every Wishlist Button fills, the header count counts and the Wishlist loop (`bfbeShopWishlist`, `bfbe-shop-loops`) shows.
- **The bar says what happened.** Each action posts its own page and comes back with a WooCommerce notice ("List made: Birthday."), which BFB Wishlist Bar prints at its top (`bfbe-wishlist-bar`). Place actions inside the bar or anywhere on the same page as one.
- **Its words, one set per act.** `new`: **Field label** `newLabel`, **Button words** `newButton`. `pick`: `pickLabel`, `pickButton`. `rename`: `renameLabel`, `renameButton`. `delete`: `deleteButton`. `share`: `shareMake`, `shareLabel`, `shareCopy`, `shareStop`. `registry`: `registryButton`. `surprise`: `surpriseButton`. Each left empty uses its placeholder.
- **The share link** opens at the page the action stood on when it was made, read-only for anyone with it: the bar's shared-list note, `{bfbe_wishlist_name}` of that list and the Wishlist loop's rows, with **Mark as bought** on a registry.
- **The gift registry** (`registry`) gives the link's visitors Mark as bought; `surprise`, drawn only on a registry, hides those marks from the owner. The bar's `{bfbe_wishlist_registry}` badge follows the switch.
- **Move to list is the loop's, not an action.** For a customer with two or more lists, each Wishlist loop row gets a Move to list select (`select.bfbe-lrow__select`), sized like the row's buttons since 30 October and styled by the loop's `bfbeShopWishlistMove*` keys, never by this element's List picker.
- **Layout.** Line the parts up or stack them with Bricks' own keys on the action (`_display: "flex"`, `_flexDirection`), and line actions up with a Bricks Block around them. For CSS, a class in `_cssClasses`, never `_cssId`.

## Verified patterns

**The sharing, placed apart from the bar.** From the P9 fixture's wishlist page (`fixture-shop-p9-wishlist`, "Sharing, placed apart from the bar"). A wrapping Bricks Block row with `_alignItems: "flex-end"`: the lone registry and surprise buttons line up with the share field's button. The probe reads that these work outside the bar.

```json
{
  "name": "block",
  "settings": { "_direction": "row", "_flexWrap": "wrap", "_alignItems": "flex-end", "_columnGap": "16px", "_rowGap": "10px", "_cssClasses": "apart" },
  "children": [
    { "name": "bfbe-wishlist-action", "settings": { "act": "share", "_cssClasses": "wa-share" } },
    { "name": "bfbe-wishlist-action", "settings": { "act": "registry", "_cssClasses": "wa-registry" } },
    { "name": "bfbe-wishlist-action", "settings": { "act": "surprise", "_cssClasses": "wa-surprise" } }
  ]
}
```

**Choose a list and make one, with the field and button styled.** From the 2.4 demo shop's "Your lists" card (`fh_lists_bar()` in `dev/demo/shop/lib.php`). `pick` takes the styled open list (`listLook: "custom"` and its colours); both share pill buttons and rounded fields. The brand's colours are kept as hex; trimmed: the type.

```json
{
  "name": "block",
  "settings": { "_rowGap": "14px" },
  "children": [
    { "name": "bfbe-wishlist-action", "settings": { "act": "pick", "listLook": "custom", "listPanelBg": { "hex": "#ffffff" }, "listOptHover": { "hex": "#f6f6f8" }, "listOptOnBg": { "hex": "#f0ecff" }, "listTick": { "hex": "#6e44ff" }, "fieldBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "12", "right": "12", "bottom": "12", "left": "12" } }, "fieldPadding": { "top": "9", "right": "12", "bottom": "9", "left": "12" }, "fieldFocus": { "hex": "#6e44ff" }, "btnPadding": { "top": "9", "right": "16", "bottom": "9", "left": "16" }, "btnBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } }, "btnBackground": { "hex": "#ffffff" } } },
    { "name": "bfbe-wishlist-action", "settings": { "act": "new", "fieldBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "12", "right": "12", "bottom": "12", "left": "12" } }, "fieldPadding": { "top": "9", "right": "12", "bottom": "9", "left": "12" }, "fieldFocus": { "hex": "#6e44ff" }, "btnPadding": { "top": "9", "right": "16", "bottom": "9", "left": "16" }, "btnBorder": { "width": { "top": "1", "right": "1", "bottom": "1", "left": "1" }, "style": "solid", "color": { "hex": "#e9ecf1" }, "radius": { "top": "999", "right": "999", "bottom": "999", "left": "999" } }, "btnBackground": { "hex": "#ffffff" } } }
  ]
}
```

**Rename with your own words, and a delete that reads as a warning.** From the P9 fixture (`renameButton: "Save the name"`) and the demo's "This list" card (Delete in the sale colour, given a white fill). The quiet Delete has no fill until `btnBackground` is set.

```json
{
  "name": "block",
  "settings": { "_rowGap": "14px" },
  "children": [
    { "name": "bfbe-wishlist-action", "settings": { "act": "rename", "renameLabel": "Name", "renameButton": "Save the name" } },
    { "name": "bfbe-wishlist-action", "settings": { "act": "delete", "deleteButton": "Delete this list", "btnType": { "font-weight": "700", "color": { "hex": "#c2410c" } }, "btnBackground": { "hex": "#ffffff" } } }
  ]
}
```

## Gotchas

- **Signed-in customers only.** For a guest and on a share link every action prints nothing on the site, while the builder always draws it; a guest learns why from the bar's **Words for guests**. <!-- src: plugins/bfb-elements-pro/elements/wishlist-action.php:149-152 ; plugins/bfb-elements-pro/elements/wishlist-bar.php:141-149 -->
- **Some acts wait for their moment.** `pick` draws only once there are two lists, `delete` never on the first list, `surprise` only on a gift registry; the canvas shows all three regardless. <!-- src: plugins/bfb-elements-pro/elements/wishlist-action.php:156-159 -->
- **Every action reloads the page, script or not.** Its forms carry no `data-bfbe-list-act`, so the lists' script leaves them to post; the result is a WooCommerce notice on the page that comes back. <!-- src: plugins/bfb-elements-pro/elements/wishlist-action.php:165 ; src/elements/shop-lists/shop-lists.js:137-139 ; plugins/bfb-elements/includes/shop/class-live.php:229-265 -->
- **Where the share action stands is where the link opens.** Making a link records the page the action is on (when public), else the Shop page's **Wishlist page**, else the home page; put it on the page with the Wishlist loop. <!-- src: plugins/bfb-elements-pro/elements/wishlist-action.php:160, 191 ; plugins/bfb-elements-pro/includes/shop/class-lists.php:629-634, 1196-1198 -->
- **Copy appears only where the browser can copy.** The Copy button starts `hidden` and shows only with the Clipboard API, which browsers give to secure (https) pages; elsewhere the read-only field stays for copying by hand. <!-- src: plugins/bfb-elements-pro/elements/wishlist-action.php:188 ; src/elements/shop-lists/shop-lists.js:170-174 -->
- **Stop sharing kills the address.** The link's id is forgotten, so the old address opens nothing; a new link is a new address to send again. <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:1189-1192 -->
- **Each act's keys show only with it.** The words are offered for their own `act` (an empty `act` counts as `new`); the Field group only for `new`, `pick`, `rename` and `share`; the List picker only for `pick`. Delete, registry and surprise take the Button group alone. <!-- src: plugins/bfb-elements-pro/elements/wishlist-action.php:48-50, 76-98 -->
- **Delete and Stop sharing are quiet.** They have no fill until the Button group's **Background** (`btnBackground`) is set. <!-- src: src/elements/wishlist-action/wishlist-action.css:17 ; plugins/bfb-elements-pro/elements/wishlist-action.php:182, 189 -->
- **A button beside a field is the field's height** (since 30 October), so in a row of actions with `_alignItems: "flex-end"` the lone buttons' feet meet the field buttons'. Field padding and type size therefore set the button's height too. <!-- src: src/elements/wishlist-action/wishlist-action.css:8-10 ; docs/SHOP-LABELS-2.0.0.md "From Alex's notes on the demo shop (30 October)" -->
- **Limits a customer meets.** Twenty lists ("You can keep up to 20 lists."), names of up to 60 characters, an empty name refused, and the first list cannot be deleted ("The first list stays. Empty it instead."). <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:65, 1090-1097, 1142-1144 -->

## Never do

- Do not rely on an action to tell guests anything; give the page a BFB Wishlist Bar.
- Do not place actions on a page that prints no WooCommerce notice (no bar, no Notice element).
- Do not set Field keys on `delete`, `registry` or `surprise`, or List picker keys on anything but `pick`.
- Do not set another act's words (`renameButton` on `act: "new"`); each word key belongs to its own act.
- Do not put the share action on a page that does not show the list; the link opens there.
- Do not style the wishlist loop's Move to list select from this element; use the loop's `bfbeShopWishlistMove*` keys.
- Do not give it a `_cssId` for styling; use `_cssClasses`.
