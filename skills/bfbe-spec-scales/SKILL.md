---
name: bfbe-spec-scales
description: "Use when showing product attributes as scales on a product page or card with `bfbe-spec-scales`: warmth, firmness or softness as a meter with its figure in words, read from WooCommerce attributes."
---

# BFB Spec Scales (`bfbe-spec-scales`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 2.0.0 or later, WooCommerce active, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-spec-scales.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/spec-scales/

## What it is
Product attributes drawn as scales, such as Warmth: Warm, 3 of 4, or Softness: 4 of 5, each a real meter with its figure in words beside it. It reads the attributes you already keep in WooCommerce, so the scale changes when the product does, and a product without an attribute prints nothing for it.

**Not for:** It does not make a scale of an attribute that is not one: a colour, a material or the sizes a product comes in prints nothing. It does not follow the chosen variation or compare products side by side; for that, use BFB Comparison Table.

**Costs a page:** CSS 0.60 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** no · **Keyboard:** no · **Reduced motion:** no

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`); Tooltips (`bfbeTooltip*`, skill `bfbe-tooltips`).

### Scales (`bfbeScales`)
- `scales` (repeater) **Scales**: placeholder Scale. A list, one row per scale.

### Look (`bfbeLook`)
- `layout` (select) **Layout**: options: `rows` Name, scale and figure in a row (default), `stacked` Name above the scale. Name, scale and figure in a row by default, or Name above the scale for a narrow column; **Name width** (9em when empty, in the row layout), **Row gap** (10px when empty) and **Column gap**.
Styling, in the schema file: `nameWidth`, `gap`, `columnGap`, `rowBackground`, `rowBorder`, `rowPadding`, `height`, `fill`, `track`, `border`, `nameTypography`, `figureTypography`.

## What it guarantees for accessibility (do not undo)
- A description list: the name is the term, the meter and its figure the description.
- Each meter carries 0, the maximum and the value, is named by its row's name, and its own text says the name and the figure where a meter is not drawn.
- The figure is printed text, so the value never depends on reading a bar.
<!-- bfbe:generated:end -->

## Rendered DOM

```html
<dl id="brxe-{id}" class="brxe-bfbe-spec-scales bfbe-scales bfbe-scales--rows">
  <div class="bfbe-scales__row">
    <dt class="bfbe-scales__name" id="bfbe-{uid}-scale-0">Warmth</dt>
    <dd class="bfbe-scales__value">
      <meter class="bfbe-scales__meter" min="0" max="4" value="3" aria-labelledby="bfbe-{uid}-scale-0"
             style="--bfbe-scales-pct:75%">Warmth: Warm: 3 of 4</meter>
      <span class="bfbe-scales__figure">Warm: 3 of 4</span>
    </dd>
  </div>
  …one row per scale the product can fill
</dl>
```

- The root is the description list itself, `dl.bfbe-scales`, with `bfbe-scales--rows` or `bfbe-scales--stacked` from **Layout** `layout`. No script: everything is in the server's HTML.
- Each row is a real `meter`, named by its `dt`; its own text is the row's name and figure, for where a meter is not drawn. The bar is a gradient on the meter itself, filled to `--bfbe-scales-pct`, so every browser draws it alike. The printed `.bfbe-scales__figure` carries the value as words.
- Where controls write: on the root, `nameWidth` sets `--bfbe-scales-name` (9em), `height` `--bfbe-scales-h` (10px), `fill` `--bfbe-scales-fill`, `track` `--bfbe-scales-track`, `columnGap` `--bfbe-scales-col-gap` and `gap` the root's `row-gap`. `border` writes to `.bfbe-scales__meter`; `rowBackground`, `rowBorder` and `rowPadding` to `.bfbe-scales__row`; `nameTypography` to `.bfbe-scales__name`, `figureTypography` to `.bfbe-scales__figure`.

## Wiring to other elements

- **It reads the product, nothing else.** On a product template it reads that product; in a product query loop it reads each card's product, so one element in the loop's card shows every product's own scales (loops: skill `bfbe-shop-loops`; the shop as a whole: `bfbe-shop`).
- **The values come from WooCommerce attributes**: a global attribute (Products, Attributes, a key such as `pa_warmth`) in **Attribute** `attribute`, or a product's own attribute by name in **Custom attribute** `custom`. Reordering the global attribute's terms moves every product's scale.
- Nothing targets it and it targets nothing. A class in `_cssClasses` is for your own CSS only.

## Verified patterns

**Two scales in the product summary** (fixture template `bfbe-shop-product-p4`, `.p4-scales`, in its summary column). The first row reads the global attribute `pa_warmth`, a term's place in its ordered list, with **Figure** `pattern` adding the term's name; the second reads a custom attribute holding one number, so it needs **Scale maximum** `max`. `pa_warmth` is the dev site's attribute: use the target site's own.

```json
{
  "name": "block",
  "settings": { "_rowGap": "12px" },
  "children": [
    { "name": "product-title", "settings": {} },
    { "name": "product-price", "settings": {} },
    { "name": "product-add-to-cart", "settings": {} },
    { "name": "bfbe-spec-scales", "settings": { "scales": [
      { "id": "adccff", "attribute": "pa_warmth", "pattern": "{words}: {value} of {max}" },
      { "id": "ccbcfd", "custom": "Softness", "max": 5 }
    ], "_cssClasses": "p4-scales" } }
  ]
}
```

**Each card's scale in a product loop, stacked** (built from the schema). The Block's `hasLoop` repeats the card over products; `layout: "stacked"` puts the name above the meter for a narrow card, and **Name shown** `label` replaces the attribute's label. A product without the attribute prints no scale in its card.

```json
{
  "name": "block",
  "settings": { "hasLoop": true, "query": { "objectType": "post", "post_type": [ "product" ], "posts_per_page": 8 } },
  "children": [
    { "name": "heading", "settings": { "text": "{post_title}", "tag": "h3" } },
    { "name": "bfbe-spec-scales", "settings": { "layout": "stacked", "scales": [ { "id": "sswarm", "attribute": "pa_warmth", "label": "Warmth", "pattern": "{words}" } ], "height": "6px", "_cssClasses": "card-scales" } }
  ]
}
```

## Gotchas

- **A row that cannot be read is left out silently.** No scale when the product lacks the attribute, carries several of its terms (a choice, such as sizes), or holds words in a custom attribute; with no row left the element prints nothing at all. <!-- src: plugins/bfb-elements-pro/includes/shop/class-spec-scales.php:83 ; plugins/bfb-elements-pro/includes/shop/class-spec-scales.php:112 ; plugins/bfb-elements-pro/elements/spec-scales.php:269 -->
- **A number needs a maximum.** A numeric term or custom attribute has no natural top, so a row without `max` is dropped. A global attribute's top is its number of terms. <!-- src: plugins/bfb-elements-pro/elements/spec-scales.php:259 ; plugins/bfb-elements-pro/includes/shop/class-spec-scales.php:87 -->
- **Unused terms count.** The maximum and a term's place are read from every term of the attribute, used or not, in WooCommerce's **Default sort order** for it; adding a term or reordering shifts every product's figure. <!-- src: plugins/bfb-elements-pro/includes/shop/class-spec-scales.php:93 ; plugins/bfb-elements-pro/includes/shop/class-spec-scales.php:120 -->
- **Custom attribute wins.** With both `custom` and `attribute` set on a row, `custom` is read and `attribute` ignored. <!-- src: plugins/bfb-elements-pro/elements/spec-scales.php:254 -->
- **The row's name key is `label`.** **Name shown** is `label` in each `scales` row; any other key, such as `name`, is ignored and the attribute's own label shows. <!-- src: plugins/bfb-elements-pro/elements/spec-scales.php:78 -->
- **Over the top fills the meter, not the figure.** A value above `max` draws a full bar while the figure says the real value ("7 of 5"). <!-- src: plugins/bfb-elements-pro/elements/spec-scales.php:266 ; plugins/bfb-elements-pro/elements/spec-scales.php:285 -->
- **It never follows the chosen variation.** A variation reads its parent's attributes, and variation attributes are choices, so the scale stays the same while the shopper picks options. <!-- src: plugins/bfb-elements-pro/includes/shop/class-spec-scales.php:67 ; docs/elements/spec-scales.md "What it does not do" -->
- **Figure words are fixed.** `pattern` fills `{value}`, `{max}` and `{words}` (the term's name), numbers in the shop's decimal format; it takes no dynamic data. Empty, it prints "{value} of {max}". <!-- src: plugins/bfb-elements-pro/elements/spec-scales.php:265 ; plugins/bfb-elements-pro/elements/spec-scales.php:279 -->
- **The bar is the text colour on a light track.** `fill` defaults to `currentColor` and `track` to the shared surface token; on a dark section set both. <!-- src: src/elements/spec-scales/spec-scales.css:2 -->
- **Name width is for rows only.** `nameWidth` is offered only while `layout` is not `stacked`. <!-- src: plugins/bfb-elements-pro/elements/spec-scales.php:115 -->

## Never do

- Do not put a name in a `scales` row under any key but `label`.
- Do not leave `max` empty on a row that reads a number.
- Do not point a row at an attribute that holds a choice (several terms per product, such as sizes or colours).
- Do not set `nameWidth` with `layout: "stacked"`.
- Do not expect the scale to change with the chosen variation.
- Do not copy `pa_*` keys from another site; read the target site's attributes.
