---
name: bfbe-wishlist-bar
description: "Use when building the wishlist page's lists bar: the list's name and count, named lists, share link and gift registry, and the message after each change, with BFB Wishlist Bar (`bfbe-wishlist-bar`). Read before writing its settings."
---

# BFB Wishlist Bar (`bfbe-wishlist-bar`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-wishlist-bar.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/wishlist-bar/

## What it is
_Not in the website's approved words yet: the 2.0.0 release export fills in the summary, Not for, the badges and the accessibility list here._

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-wishlist-bar",
    "settings": {},
    "children": [
        {
            "name": "block",
            "settings": {
                "_direction": "row",
                "_flexWrap": "wrap",
                "_alignItems": "baseline",
                "_columnGap": "16px",
                "_rowGap": "8px"
            },
            "children": [
                {
                    "name": "heading",
                    "settings": {
                        "text": "{bfbe_wishlist_name}",
                        "tag": "h2"
                    }
                },
                {
                    "name": "text-basic",
                    "settings": {
                        "text": "{bfbe_wishlist_saved} saved"
                    }
                },
                {
                    "name": "text-basic",
                    "settings": {
                        "text": "{bfbe_wishlist_registry}",
                        "tag": "span",
                        "_padding": {
                            "top": "4",
                            "right": "10",
                            "bottom": "4",
                            "left": "10"
                        },
                        "_border": {
                            "radius": {
                                "top": "999",
                                "right": "999",
                                "bottom": "999",
                                "left": "999"
                            }
                        },
                        "_background": {
                            "color": {
                                "raw": "var(--bfbe-surface-hover, #f4f4f5)"
                            }
                        },
                        "_typography": {
                            "font-size": "0.8em",
                            "font-weight": "600"
                        },
                        "_conditions": [
                            [
                                {
                                    "id": "bfbewr",
                                    "key": "dynamic_data",
                                    "dynamic_data": "{bfbe_wishlist_registry}",
                                    "compare": "empty_not"
                                }
                            ]
                        ]
                    }
                }
            ]
        },
        {
            "name": "block",
            "settings": {
                "_direction": "row",
                "_flexWrap": "wrap",
                "_alignItems": "flex-end",
                "_columnGap": "16px",
                "_rowGap": "8px"
            },
            "children": [
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "pick"
                    }
                },
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "new"
                    }
                },
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "rename"
                    }
                },
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "delete"
                    }
                }
            ]
        },
        {
            "name": "block",
            "settings": {
                "_direction": "row",
                "_flexWrap": "wrap",
                "_alignItems": "flex-end",
                "_columnGap": "16px",
                "_rowGap": "8px"
            },
            "children": [
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "share"
                    }
                },
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "registry"
                    }
                },
                {
                    "name": "bfbe-wishlist-action",
                    "settings": {
                        "act": "surprise"
                    }
                }
            ]
        }
    ]
}
```

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Lists bar (`bfbeBar`)
- `barGuest` (text) **Words for guests**: placeholder Sign in to keep several lists and share them.; dynamic data accepted
- `barShared` (text) **Words on a shared list**: placeholder A list shared with you.; dynamic data accepted
Styling, in the schema file: `barNoteTypography`, `barLinkColor`.

### Notice (`bfbeNotice`)
Styling only, every key in the schema file: `noticeTypography`, `noticeBackground`, `noticeBorder`, `noticePadding`.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<div id="brxe-{id}" class="brxe-bfbe-wishlist-bar bfbe-wlbar" data-bfbe-wlbar="1">
  <div class="bfbe-wlbar__notice"><div class="woocommerce-message" role="alert">List made: Birthday.</div></div>
  <p class="bfbe-wlbar__note">Sign in to keep several lists and share them. <a class="bfbe-wlbar__link" href="/my-account/">Sign in</a></p>
  <!-- the children, as Bricks renders them: a Heading of {bfbe_wishlist_name}, Blocks of BFB Wishlist Actions -->
</div>
```

- The root is a flex column (`gap: var(--bfbe-gap)`, full width) whose direct children lose their block margins. It has no look of its own: the box is Bricks' Style tab.
- `.bfbe-wlbar__notice` comes first and holds WooCommerce's own notice markup (`.woocommerce-message`, `.woocommerce-info`, `.woocommerce-error`); it is hidden while empty. The **Notice** keys write to those three classes inside it.
- `.bfbe-wlbar__note` is one of two notes, never both: **Words for guests** (`barGuest`) with a Sign in link to WooCommerce's account page, or, on a share link, **Words on a shared list** (`barShared`), plus "It is a gift registry: mark what you buy, and nobody is told who." on a registry. A signed-in customer on their own list gets neither.
- `barNoteTypography` writes to `.bfbe-wlbar__note`, `barLinkColor` to `.bfbe-wlbar__link`.
- In the builder the notice and the notes are left out and every child draws; a bar with no children shows "Add the list name and the BFB Wishlist Action elements you want."
- The bar has no script of its own; it asks for the Lists feature's files, which a share link's Copy uses.

## Wiring to other elements

- **What goes inside.** Any Bricks element, and BFB Wishlist Action (`bfbe-wishlist-action`, schema `../bfbe-schemas/references/elements/bfbe-wishlist-action.json`), each one thing a customer does: `act` `pick`, `new`, `rename`, `delete`, `share`, `registry` or `surprise`. The actions work outside the bar too; the bar is where their result is said.
- **The tags for its own children** (BFB Shop, `bfbe-shop-tags-and-conditions`): `{bfbe_wishlist_name}` (the list shown, "Wishlist" until renamed; the shared list's on its link), `{bfbe_wishlist_saved}` (how many on the list shown), `{bfbe_wishlist_registry}` ("Gift registry" on a registry, else empty), `{bfbe_wishlist_url}`.
- **The registry badge** is a Bricks Text of `{bfbe_wishlist_registry}` with a Bricks condition on the same tag: `"_conditions": [[{ "id": "…", "key": "dynamic_data", "dynamic_data": "{bfbe_wishlist_registry}", "compare": "empty_not" }]]`.
- **The rows** are a Wishlist query loop (`bfbeShopWishlist`, `bfbe-shop-loops`) beside the bar, not inside it: it lists the list in hand, or the shared list on its link, with Move to cart, Remove and Move to list per row.
- **Where it goes.** On the page chosen as **Wishlist page** (BFB Elements, Shop, Customers), with the Wishlist loop, or on an account page of your own. A share link opens at the page where it was made, else that Wishlist page.
- **The demo's arrangement** (since 30 October): under the title row, a Bricks Block grid of three cards, Your lists (choose, new), This list (rename, delete) and Share (share link, gift registry, surprise), each a heading, one line saying what it is for, then its actions; one column from `tablet_portrait`. The first pattern below is that tree.
- Give the bar a class in `_cssClasses` for your own CSS, never `_cssId`: component instances share ids.

## Verified patterns

**The three titled cards.** From the 2.4 demo shop's Wishlist page and its account lists template (`fh_lists_bar()` in `dev/demo/shop/lib.php`, as of 30 October). The bar takes `_display: "flex"` so the panel offers its row gap; a Bricks Block grid holds the cards and drops to one column at `tablet_portrait`. Trimmed: the brand's colours and type, and the actions' look (see `bfbe-wishlist-action`).

```json
{
  "name": "bfbe-wishlist-bar",
  "settings": { "barGuest": "Sign in to keep several lists and share them.", "_display": "flex", "_rowGap": "16px", "_padding": { "top": "20", "right": "20", "bottom": "20", "left": "20" }, "_cssClasses": "lists-bar" },
  "children": [
    { "name": "block", "settings": { "_direction": "row", "_flexWrap": "wrap", "_alignItems": "baseline", "_columnGap": "14px", "_rowGap": "8px" }, "children": [
      { "name": "heading", "settings": { "text": "{bfbe_wishlist_name}", "tag": "h2" } },
      { "name": "text-basic", "settings": { "text": "{bfbe_wishlist_saved} saved" } },
      { "name": "text-basic", "settings": { "text": "{bfbe_wishlist_registry}", "tag": "span", "_conditions": [ [ { "id": "wlreg1", "key": "dynamic_data", "dynamic_data": "{bfbe_wishlist_registry}", "compare": "empty_not" } ] ] } }
    ] },
    { "name": "block", "settings": { "_display": "grid", "_gridTemplateColumns": "repeat(3, minmax(0, 1fr))", "_gridTemplateColumns:tablet_portrait": "minmax(0, 1fr)", "_gridGap": "16px", "_alignItems": "stretch" }, "children": [
      { "name": "block", "settings": { "_rowGap": "14px", "_padding": { "top": "20", "right": "20", "bottom": "20", "left": "20" } }, "children": [
        { "name": "block", "settings": { "_rowGap": "4px" }, "children": [
          { "name": "heading", "settings": { "text": "Your lists", "tag": "h3" } },
          { "name": "text-basic", "settings": { "text": "Switch to another list, or start a new one." } }
        ] },
        { "name": "block", "settings": { "_rowGap": "14px" }, "children": [
          { "name": "bfbe-wishlist-action", "settings": { "act": "pick" } },
          { "name": "bfbe-wishlist-action", "settings": { "act": "new" } }
        ] }
      ] },
      { "name": "block", "settings": { "_rowGap": "14px", "_padding": { "top": "20", "right": "20", "bottom": "20", "left": "20" } }, "children": [
        { "name": "block", "settings": { "_rowGap": "4px" }, "children": [
          { "name": "heading", "settings": { "text": "This list", "tag": "h3" } },
          { "name": "text-basic", "settings": { "text": "Give it a new name, or delete it." } }
        ] },
        { "name": "block", "settings": { "_rowGap": "14px" }, "children": [
          { "name": "bfbe-wishlist-action", "settings": { "act": "rename" } },
          { "name": "bfbe-wishlist-action", "settings": { "act": "delete" } }
        ] }
      ] },
      { "name": "block", "settings": { "_rowGap": "14px", "_padding": { "top": "20", "right": "20", "bottom": "20", "left": "20" } }, "children": [
        { "name": "block", "settings": { "_rowGap": "4px" }, "children": [
          { "name": "heading", "settings": { "text": "Share", "tag": "h3" } },
          { "name": "text-basic", "settings": { "text": "Send a link to the list, or make it a gift registry." } }
        ] },
        { "name": "block", "settings": { "_direction": "row", "_flexWrap": "wrap", "_alignItems": "flex-end", "_columnGap": "10px", "_rowGap": "10px" }, "children": [
          { "name": "bfbe-wishlist-action", "settings": { "act": "share" } },
          { "name": "bfbe-wishlist-action", "settings": { "act": "registry" } },
          { "name": "bfbe-wishlist-action", "settings": { "act": "surprise" } }
        ] }
      ] }
    ] }
  ]
}
```

**A wishlist page: the bar, the rows, the sharing apart.** From the P9 fixture (`fixture-shop-p9-wishlist`). The bar holds the title and one wrapping row of list actions; the Wishlist loop follows it, then the sharing actions placed outside the bar, which still work there and report through the bar's notice.

```json
{
  "name": "block",
  "settings": { "_rowGap": "20px" },
  "children": [
    { "name": "bfbe-wishlist-bar", "settings": { "_cssClasses": "bar" }, "children": [
      { "name": "heading", "settings": { "text": "{bfbe_wishlist_name}", "tag": "h2" } },
      { "name": "text-basic", "settings": { "text": "{bfbe_wishlist_saved} saved" } },
      { "name": "block", "settings": { "_direction": "row", "_flexWrap": "wrap", "_columnGap": "16px", "_cssClasses": "bar-row" }, "children": [
        { "name": "bfbe-wishlist-action", "settings": { "act": "pick" } },
        { "name": "bfbe-wishlist-action", "settings": { "act": "new" } },
        { "name": "bfbe-wishlist-action", "settings": { "act": "rename", "renameButton": "Save the name" } },
        { "name": "bfbe-wishlist-action", "settings": { "act": "delete" } }
      ] }
    ] },
    { "name": "block", "settings": { "hasLoop": true, "query": { "objectType": "bfbeShopWishlist", "no_results_text": "Nothing saved yet." }, "_cssClasses": "wl-rows" }, "children": [
      { "name": "product-title", "settings": { "tag": "h4", "linkToProduct": true } },
      { "name": "product-price", "settings": {} }
    ] },
    { "name": "block", "settings": { "_direction": "row", "_flexWrap": "wrap", "_columnGap": "16px", "_cssClasses": "apart" }, "children": [
      { "name": "bfbe-wishlist-action", "settings": { "act": "share" } },
      { "name": "bfbe-wishlist-action", "settings": { "act": "registry" } },
      { "name": "bfbe-wishlist-action", "settings": { "act": "surprise" } }
    ] }
  ]
}
```

## Gotchas

- **The bar prints every WooCommerce notice waiting.** It calls WooCommerce's notice printer, which empties the queue: a Bricks Notice element rendered earlier on the page takes the message first, and the bar then shows none. Keep one notice printer on the wishlist page. <!-- src: plugins/bfb-elements-pro/elements/wishlist-bar.php:129-132 -->
- **Without the bar, an action's result goes unseen.** Each action posts the page and comes back with its message as a WooCommerce notice; with no bar and no notice element on the page, nobody reads "List made: Birthday." <!-- src: plugins/bfb-elements/includes/shop/class-live.php:250-265 ; plugins/bfb-elements-pro/elements/wishlist-action.php:165 -->
- **Guests and share links see your other children only.** The actions draw nothing for a guest and on a share link, so the bar shows its note and whatever Bricks elements you put in it; words that only make sense with the actions belong in their own blocks. <!-- src: plugins/bfb-elements-pro/elements/wishlist-action.php:149-152 ; plugins/bfb-elements-pro/elements/wishlist-bar.php:133-149 -->
- **The builder hides the notice and the notes.** The canvas draws the children as for a customer, with no guest or shared note and no notice; check those states on the site, signed out and on a share link. <!-- src: plugins/bfb-elements-pro/elements/wishlist-bar.php:129, 133, 141 -->
- **Layout keys need `_display: "flex"`.** The bar's `_direction`, `_flexWrap`, `_columnGap` and `_rowGap` are offered only with `_display: "flex"`, and the grid keys only with `"grid"`, though the root is already a flex column. <!-- src: plugins/bfb-elements/includes/abstract-element.php:884-930 ; src/elements/wishlist-bar/wishlist-bar.css:5 -->
- **The registry badge needs its condition.** Without the `empty_not` condition on `{bfbe_wishlist_registry}`, a styled Text prints an empty pill on every list that is not a registry. <!-- src: plugins/bfb-elements-pro/elements/wishlist-bar.php:88-99 -->
- **`{bfbe_wishlist_saved}` is the list shown, `{bfbe_wishlist_count}` the visitor's.** On a share link `saved` counts the shared list and is not live; `count` is always the visitor's own list in hand. Use `saved` in the bar. <!-- src: plugins/bfb-elements-pro/includes/shop/class-lists.php:89, 97-98 -->
- **The notice and the note come first.** They print at the top of the bar, before every child whatever the order in the structure; to show the list's name above them, place the name's Heading outside the bar. <!-- src: plugins/bfb-elements-pro/elements/wishlist-bar.php:128-155 -->

## Never do

- Do not put a Bricks Notice element above the bar on the wishlist page; the bar shows the actions' messages.
- Do not place Wishlist Actions on a page with no bar and no notice element.
- Do not set `_direction`, `_flexWrap` or the gaps on the bar without `_display: "flex"`.
- Do not style a `{bfbe_wishlist_registry}` badge without its `empty_not` condition.
- Do not use `{bfbe_wishlist_count}` for the count of the list the bar shows; use `{bfbe_wishlist_saved}`.
- Do not judge the guest or share link state from the canvas; it draws the customer's.
- Do not give the bar a `_cssId` for styling; use `_cssClasses`.
