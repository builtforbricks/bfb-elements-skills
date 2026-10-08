---
name: bfbe-filter-grid
description: "Use when building a filterable portfolio, shop or post grid with BFB Filter Grid (`bfbe-filter-grid`) and its Filter Items: tag chips with counts, several tags at once, a filter in the URL, items typed in or repeated by a query loop tagged with categories. Read before writing its settings."
---

# BFB Filter Grid (`bfbe-filter-grid`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-filter-grid.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/filter-grid/

## What it is
Items behind filter chips, each Filter Item carrying its tags, typed in or taken from a query loop's dynamic tags. The chips are built from the tags actually present, and items hide and reveal in the page with an animated reflow where the browser allows. A filter can live in the URL, and several tags can be chosen at once.

**Not for:** It filters the items already in the page, so every item's markup is delivered up front. A large archive that needs paging or a server search fits a paginated query loop better, because this grid cannot fetch more items.

**Costs a page:** CSS 0.79 KB, JS 1.43 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** yes

## Structure
Nestable. Its own children: `bfbe-filter-item`.
What the builder inserts, as a tree `bricks/add-element` accepts (ids omitted):

```json
{
    "name": "bfbe-filter-grid",
    "settings": {},
    "children": [
        {
            "name": "bfbe-filter-item",
            "settings": {
                "tags": "Design"
            },
            "children": [
                {
                    "name": "block",
                    "settings": {
                        "_background": {
                            "color": {
                                "hex": "#e2e8f0"
                            }
                        },
                        "_padding": {
                            "top": "32",
                            "right": "24",
                            "bottom": "32",
                            "left": "24"
                        }
                    },
                    "children": [
                        {
                            "name": "heading",
                            "settings": {
                                "text": "Brand site",
                                "tag": "h3"
                            }
                        }
                    ]
                }
            ]
        },
        {
            "name": "bfbe-filter-item",
            "settings": {
                "tags": "Development"
            },
            "children": [
                {
                    "name": "block",
                    "settings": {
                        "_background": {
                            "color": {
                                "hex": "#e2e8f0"
                            }
                        },
                        "_padding": {
                            "top": "32",
                            "right": "24",
                            "bottom": "32",
                            "left": "24"
                        }
                    },
                    "children": [
                        {
                            "name": "heading",
                            "settings": {
                                "text": "Shop build",
                                "tag": "h3"
                            }
                        }
                    ]
                }
            ]
        },
        {
            "name": "bfbe-filter-item",
            "settings": {
                "tags": "Video"
            },
            "children": [
                {
                    "name": "block",
                    "settings": {
                        "_background": {
                            "color": {
                                "hex": "#e2e8f0"
                            }
                        },
                        "_padding": {
                            "top": "32",
                            "right": "24",
                            "bottom": "32",
                            "left": "24"
                        }
                    },
                    "children": [
                        {
                            "name": "heading",
                            "settings": {
                                "text": "Launch film",
                                "tag": "h3"
                            }
                        }
                    ]
                }
            ]
        },
        {
            "name": "bfbe-filter-item",
            "settings": {
                "tags": "Design, Print"
            },
            "children": [
                {
                    "name": "block",
                    "settings": {
                        "_background": {
                            "color": {
                                "hex": "#e2e8f0"
                            }
                        },
                        "_padding": {
                            "top": "32",
                            "right": "24",
                            "bottom": "32",
                            "left": "24"
                        }
                    },
                    "children": [
                        {
                            "name": "heading",
                            "settings": {
                                "text": "Identity",
                                "tag": "h3"
                            }
                        }
                    ]
                }
            ]
        }
    ]
}
```

`bfbe-filter-item` (BFB Filter Item), 35 controls, schema `../bfbe-schemas/references/elements/bfbe-filter-item.json`, nestable itself.

## Settings that decide the build
Also on this element, as on every element: Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Filters (`bfbeFilters`)
- `allLabel` (text) **Show-everything chip**: placeholder All; dynamic data accepted. The words on the chip that shows every item, All by default. It takes dynamic data.
- `multi` (checkbox) **Several at once**. Off by default, so one tag shows at a time. Tick it to let visitors combine chips, and items matching any chosen tag show.
- `counts` (checkbox) **Show counts**. Tick it to show on each chip the number of items that have its tag. The show-everything chip counts every item.
- `hash` (checkbox) **Filter in the URL**. Tick it to write the choice into the address as #filter=Tag. The hash belongs to the whole page, so it suits one grid per page.
- `emptyText` (text) **Nothing found text**: placeholder Nothing matches.; dynamic data accepted. Type what shows when no item matches. It reads Nothing matches unless you change it, and it takes dynamic data.
Styling, in the schema file: `emptyTypography`.

### Grid (`bfbeGrid`)
Styling only, every key in the schema file: `columns`, `columnsNarrow`, `columnsPhone`, `gap`, `barGap`.

### Chips (`bfbeChips`)
Styling only, every key in the schema file: `barAlign`, `chipGap`, `chipTypography`, `chipBackground`, `chipBackgroundHover`, `chipBorder`, `chipPadding`, `chipOnBackground`, `chipOnColor`, `chipSelectedBorder`, `countBackground`, `countTypography`, `countPadding`, `countBorder`.

### Motion (`bfbeMotion`)
- `itemEffect` (select) **Item effect**: options: `fade` Fade, `rise` Rise (default), `scale` Scale, `none` None. Rise is the default. Fade, Scale or None change how items arrive after a filter.
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Snappy by default. Pick another curve from the list, or Custom to type your own in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`, `stagger`.

## What it guarantees for accessibility (do not undo)
- Chips are native buttons with aria-pressed and an aria-controls naming the items container, so Tab, Enter and Space work and no arrow keys are bound.
- A visually hidden polite live region announces how many items are shown after each choice, or the Nothing found text when none is.
- Items that do not match carry the hidden attribute, so they leave the reading order as well as the screen.
- Under reduced motion the view transition is skipped and the new set appears at once, with no arrival animation or delay.
<!-- bfbe:generated:end -->

## Rendered DOM

On the frontend. Square brackets mark what appears when its setting is on:

```html
<div id="brxe-..." class="brxe-bfbe-filter-grid bfbe-fg bfbe-fg--fx-rise"
     data-bfbe-empty="Nothing matches." data-bfbe-showing="%d shown" [data-bfbe-multi="1"] [data-bfbe-hash="1"]>
  <div class="bfbe-fg__bar" role="group" aria-label="Filters">
    <button type="button" class="bfbe-fg__chip is-on" data-bfbe-tag="" aria-controls="bfbe-UID-items" aria-pressed="true">
      <span>All</span>[ <span class="bfbe-fg__count">6</span>]</button>
    <button type="button" class="bfbe-fg__chip" data-bfbe-tag="Design" aria-controls="bfbe-UID-items" aria-pressed="false">
      <span>Design</span>[ <span class="bfbe-fg__count">3</span>]</button>
  </div>
  <div class="bfbe-fg__items" id="bfbe-UID-items">
    <div id="brxe-..." class="brxe-bfbe-filter-item bfbe-fg__item" data-bfbe-tags="Design|Print">the item's children</div>
    <div id="brxe-..." class="brxe-bfbe-filter-item bfbe-fg__item" data-bfbe-tags>an untagged item</div>
  </div>
  <p class="bfbe-fg__empty" hidden></p>
  <span class="bfbe-sr" aria-live="polite" data-bfbe-fg-live></span>
</div>
```

- Root: a flex column and a size container (`container-type: inline-size`). `bfbe-fg--fx-fade|rise|scale|none` comes from **Item effect** (`itemEffect`); the builder adds `bfbe-fg--canvas`.
- The server renders the chips: the show-everything chip (`data-bfbe-tag=""`) first, then one per distinct tag, A to Z. The script toggles `.is-on` and `aria-pressed` on each.
- `.bfbe-fg__count` exists with **Show counts** (`counts`) on, and the four count controls are offered only then.
- Each Filter Item root is a `.bfbe-fg__item` holding its children directly, its tags joined by `|` in `data-bfbe-tags`. In a query loop each post is one such root, its id moved into a `brxe-` class.
- After a click the script sets `hidden` on items that do not match, gives a revealed item `.is-entering` and `--bfbe-fg-i` (its place among the shown items), and writes an inline `view-transition-name` on every item.
- `.bfbe-fg__empty` takes the text in `data-bfbe-empty` when no item shows. The live region speaks `data-bfbe-showing` with the number, or the empty text, after each click.
- Custom properties on the root: `--bfbe-fg-cols`, `--bfbe-fg-cols-md`, `--bfbe-fg-cols-sm`, `--bfbe-fg-bg`, `--bfbe-fg-bg-hover`, `--bfbe-fg-on-bg`, `--bfbe-fg-on-color`, `--bfbe-fg-count-bg`, `--bfbe-fg-stagger`, and the shared `--bfbe-duration`, `--bfbe-ease`, `--bfbe-ease-custom`.
- Controls on parts: `gap` to `.bfbe-fg__items`; `barGap` to the root's `gap`; `barAlign` and `chipGap` to `.bfbe-fg__bar`; `chipTypography`, `chipBorder` and `chipPadding` to `.bfbe-fg__chip`; `chipSelectedBorder` to `.bfbe-fg__chip.is-on`; `countTypography`, `countPadding` and `countBorder` to `.bfbe-fg__count`; `emptyTypography` to `.bfbe-fg__empty`.

## Wiring to other elements

- **Filter Item** (`bfbe-filter-item`, schema `../bfbe-schemas/references/elements/bfbe-filter-item.json`) is the child that filters. Its **Tags** (`tags`) take commas and dynamic data; **Query loop** (`hasLoop`) with **Query** (`query`) repeats it once per post. Its root holds your content directly, with Bricks' **Direction**, **Wrap** and gap controls once `_display` is `flex`.
- **Links into a filter.** With **Filter in the URL** (`hash: true`), a link from another page to `/work/#filter=Design` opens the grid filtered. With **Several at once** (`multi`), `#filter=Design,Print` chooses both; without it the first tag wins. Case is ignored on arrival.
- **Dark Mode Toggle** (`bfbe-dark-mode`): in its dark state the selected chip's words turn black or white from the fill behind them. A Selected **Text** (`chipOnColor`) you set wins in both states.
- **Bricks' AJAX events.** The script runs again on `bricks/ajax/pagination/completed`, `bricks/ajax/load_page/completed`, `bricks/ajax/query_result/displayed` and `bricks/ajax/popup/loaded`. A rerun keeps the visitor's choice and applies it to new items, but adds no chip and updates no count. Custom code that adds items calls `window.bfbeFilterGrid()`.
- **Styling from a stylesheet.** Add a class in `_cssClasses` and scope part selectors under it (`.work-grid .bfbe-fg__chip`), never under `_cssId`: component instances share ids. Nothing else targets the grid; its chips point at their own items container through `aria-controls`.

## Verified patterns

A shop catalogue: four columns, a count on every chip, a renamed show-everything chip and a filter that lives in the URL. From the demo page `demo-bfb-filter-grid`, with the product images and the card's inner layout blocks left out (the demo site's media and sizes). The selected chip pairs **Background** (`chipOnBackground`) with **Text** (`chipOnColor`).

```json
{"name": "bfbe-filter-grid", "settings": {
  "columns": 4, "counts": true, "allLabel": "Everything", "hash": true, "gap": "24px",
  "chipBackground": {"hex": "#f7f8fa"}, "chipOnBackground": {"hex": "#101828"}, "chipOnColor": {"hex": "#ffffff"}},
 "children": [
  {"name": "bfbe-filter-item", "settings": {"tags": "Knitwear, New"}, "children": [{"name": "block", "settings": {}, "children": [
    {"name": "text-basic", "settings": {"text": "The Fell hood", "tag": "p"}},
    {"name": "text-basic", "settings": {"text": "Merino and mohair", "tag": "p"}},
    {"name": "text-basic", "settings": {"text": "£190", "tag": "p"}}]}]},
  {"name": "bfbe-filter-item", "settings": {"tags": "Knitwear"}, "children": [{"name": "block", "settings": {}, "children": [
    {"name": "text-basic", "settings": {"text": "The Crew", "tag": "p"}},
    {"name": "text-basic", "settings": {"text": "Bluefaced Leicester", "tag": "p"}},
    {"name": "text-basic", "settings": {"text": "£160", "tag": "p"}}]}]},
  {"name": "bfbe-filter-item", "settings": {"tags": "Tops, New"}, "children": [{"name": "block", "settings": {}, "children": [
    {"name": "text-basic", "settings": {"text": "The Stripe", "tag": "p"}},
    {"name": "text-basic", "settings": {"text": "Cotton and wool", "tag": "p"}},
    {"name": "text-basic", "settings": {"text": "£95", "tag": "p"}}]}]},
  {"name": "bfbe-filter-item", "settings": {"tags": "Tailoring"}, "children": [{"name": "block", "settings": {}, "children": [
    {"name": "text-basic", "settings": {"text": "The Suit", "tag": "p"}},
    {"name": "text-basic", "settings": {"text": "Velvet, made to order", "tag": "p"}},
    {"name": "text-basic", "settings": {"text": "£680", "tag": "p"}}]}]}
 ]}
```

Typed tags with a staged arrival: Scale, 700 ms, the Overshoot curve and 60 ms between items, plus an untagged item that appears under the show-everything chip alone. From the fixture `fixture-filter-grid`, with its `hash` left out so it can share a page with the first pattern, and each card's second line dropped.

```json
{"name": "bfbe-filter-grid", "settings": {
  "counts": true, "itemEffect": "scale", "duration": 700, "easing": "cubic-bezier(0.34, 1.56, 0.64, 1)", "stagger": 60},
 "children": [
  {"name": "bfbe-filter-item", "settings": {"tags": "Design"}, "children": [{"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Brand site", "tag": "h3"}}]}]},
  {"name": "bfbe-filter-item", "settings": {"tags": "Development"}, "children": [{"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Shop build", "tag": "h3"}}]}]},
  {"name": "bfbe-filter-item", "settings": {"tags": "Video"}, "children": [{"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Launch film", "tag": "h3"}}]}]},
  {"name": "bfbe-filter-item", "settings": {"tags": "Design, Print"}, "children": [{"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Identity", "tag": "h3"}}]}]},
  {"name": "bfbe-filter-item", "settings": {"tags": "Development, Design"}, "children": [{"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "App", "tag": "h3"}}]}]},
  {"name": "bfbe-filter-item", "settings": {"tags": ""}, "children": [{"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "Untagged", "tag": "h3"}}]}]}
 ]}
```

Posts from a query loop, each tagged with its categories, several chips at once. Adapted from the fixture `fixture-filter-grid`, whose loop runs over pages tagged `{post_type}`; this one runs over posts tagged `{post_terms_category}`, rendered on the dev site. The loop sits on the Filter Item, so every post is its own item.

```json
{"name": "bfbe-filter-grid", "settings": {"multi": true, "columns": 4, "allLabel": "Everything"},
 "children": [
  {"name": "bfbe-filter-item",
   "settings": {"tags": "{post_terms_category}", "hasLoop": true, "query": {"objectType": "post", "post_type": ["post"], "posts_per_page": 8}},
   "children": [{"name": "block", "settings": {}, "children": [{"name": "heading", "settings": {"text": "{post_title}", "tag": "h4"}}]}]}
 ]}
```

## Gotchas

- **Filter Items are the grid's direct children.** The script filters `.bfbe-fg__item` and nothing else, so any other element in the grid takes a cell and shows under every chip. A block wrapped around Filter Items becomes the grid cell in their place. <!-- src: src/elements/filter-grid/filter-grid.js:60; src/elements/filter-grid/filter-grid.css:28 -->
- **The loop goes on the Filter Item.** Tick **Query loop** (`hasLoop`) and set **Query** (`query`) on the Filter Item itself. A loop on a block inside one Filter Item puts every post in a single item with one set of tags. <!-- src: plugins/bfb-elements-pro/elements/filter-item.php:49,60-72 -->
- **Chips are the tags present, A to Z.** One chip per distinct tag, sorted alphabetically and labelled with the tag as written; no control orders, renames or adds one. An item with no tags, or a tag that resolves to nothing, shows under the show-everything chip alone. <!-- src: plugins/bfb-elements-pro/elements/filter-grid.php:382-396,421-424; src/elements/filter-grid/filter-grid.js:66 -->
- **Tags match exactly and split on commas.** `Design` and `design` are two chips that never match each other. Bricks' terms tags (`{post_terms_category}`) join terms with `, ` and lose their links, so each term becomes a tag; a custom separator makes one long tag and a term name holding a comma makes two. <!-- src: plugins/bfb-elements-pro/elements/filter-item.php:66-69; src/elements/filter-grid/filter-grid.js:65-66; bricks/includes/integrations/dynamic-data/providers/provider-wp.php:1662 -->
- **Nothing found shows when the grid is empty.** Every chip matches at least one item, so the **Nothing found text** (`emptyText`) appears when there are no items at all, such as a loop that finds no posts, and then it shows on load. <!-- src: src/elements/filter-grid/filter-grid.js:72,123; plugins/bfb-elements-pro/elements/filter-grid.php:390-396 -->
- **One grid per page can use Filter in the URL.** The page has a single `#filter=` hash, so two grids with **Filter in the URL** (`hash`) read and overwrite each other's choice. <!-- src: docs/elements/filter-grid.md "One grid per page can use Filter in the URL" -->
- **The hash is read once, on load.** A link on the same page to `#filter=Design` filters nothing until a reload. A click writes the hash with `replaceState`, so Back leaves the page instead of undoing a filter. <!-- src: src/elements/filter-grid/filter-grid.js:85-88,108-123 -->
- **Columns follow the element's width, not the screen.** **Columns below 768px** (`columnsNarrow`, 2 by default) and **Columns below 480px** (`columnsPhone`, 1) are container queries on the grid's own width, so a grid in a narrow column uses them on a desktop. <!-- src: src/elements/filter-grid/filter-grid.css:3-5,15,29-30 -->
- **The selected fill is the text colour until set.** With no Selected **Background** (`chipOnBackground`) the chosen chip fills with its own `currentColor` and its words take `Canvas`. A colour in chip **Typography** (`chipTypography`) therefore recolours that fill and never the selected words. <!-- src: plugins/bfb-elements/includes/class-assets.php:66-69,78-79; src/elements/filter-grid/filter-grid.css:8-10,23,25 -->
- **Chip Border reaches the selected chip.** The stylesheet clears the selected chip's border colour, but a **Border** (`chipBorder`) colour is written under the element's id and outranks that. Set the Selected **Border** (`chipSelectedBorder`) to change it there. <!-- src: plugins/bfb-elements-pro/elements/filter-grid.php:180-183,201-207,241-247; src/elements/filter-grid/filter-grid.css:23 -->
- **Item delay multiplies by place.** **Item delay (ms)** (`stagger`) is multiplied by a revealed item's place among the shown items, with no cap, so an item with 40 shown before it waits 2.4 s at 60 ms. Items already on screen do not animate. <!-- src: src/elements/filter-grid/filter-grid.css:35; src/elements/filter-grid/filter-grid.js:67 -->
- **The canvas dims, the page hides.** In the builder a filtered-out item stays on screen at 35% opacity so it can still be selected, and the script builds the chips from the items in the canvas. <!-- src: src/elements/filter-grid/filter-grid.css:43-44; src/elements/filter-grid/filter-grid.js:19-25; docs/elements/filter-grid.md "In the builder the chips are built from the items" -->

## Never do

- Do not put anything but `bfbe-filter-item` directly in `bfbe-filter-grid`, and do not wrap Filter Items in a block.
- Do not put the query loop on an element inside a Filter Item; set `hasLoop` and `query` on the Filter Item.
- Do not tell tags apart by case, or separate them with anything but commas.
- Do not turn on `hash` on more than one grid per page.
- Do not link to `#filter=` on the grid's own page and expect it to filter.
- Do not set `countBackground`, `countTypography`, `countPadding` or `countBorder` without `counts: true`.
- Do not colour the selected chip through `chipTypography`; set `chipOnBackground` and `chipOnColor`.
- Do not judge filtering from the builder canvas; check the frontend.
