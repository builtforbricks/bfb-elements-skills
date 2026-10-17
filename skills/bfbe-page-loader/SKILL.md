---
name: bfbe-page-loader
description: "Use for a loading screen, splash screen or preloader shown over the page until it is ready, with BFB Page Loader (`page-loader`, Pro): a Bricks template of type BFB Page Loader (`bfbe_page_loader`), its screen built from elements, where it shows by its Conditions, every page or the first of a visit, its limit, Screen colour and fade. A template type, not an element."
---

# BFB Page Loader (`page-loader`)

Read `bfbe-start-here` first. The Page Loader is a Bricks template, not an element you place on a page: an agent builds
one by filling a template of type `bfbe_page_loader` with elements (the screen), writing its four settings and its
Conditions with the template abilities. Describe it by what it does (gone when the page is ready, three seconds at the
latest, it holds nothing back); never as making a page fast, nor as helping performance or SEO.

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.3.0 or later. Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/features/page-loader.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/page-loader/

## What it is
A feature with a Bricks template type of its own, BFB Page Loader, not an element: a screen you build in the builder, shown over the page while it is being drawn wherever its Conditions say, the most specific match winning as a header's does. It leaves once the page is ready, three seconds at the latest by CSS alone, holds nothing back, and never shows to a visitor who asks for less motion.

**Not for:** It shows a screen while the page draws; it does not make a page load sooner. A loader with no conditions shows nowhere. A Lottie works on it but starts late, since its player loads at the end of the page: for a loader, use an animated SVG or CSS.

**Nestable:** no · **In a query loop:** no · **Dynamic data:** no · **Keyboard:** no · **Reduced motion:** yes

## Where it lives
A Bricks template type of its own, not an element: a template of type BFB Page Loader (`bfbe_page_loader`), built in the builder like any template and shown as a screen over the page wherever its Conditions say (nowhere without them), gone when the page is ready or at its limit, whichever comes first. It adds no control to any element; its four settings (`bfbePlShow`, `bfbePlLimit`, `bfbePlColor`, `bfbePlFade`: Show, At most, Screen colour, Fade) sit in the template's own settings panel.

## Settings that decide the build

### Page loader (`bfbePageLoader`)
- `bfbePlShow` (select) **Show**: options: `every` On every page (default), `first` On the first page of a visit. On every page, the default, or On the first page of a visit, so later pages in the same browser tab never show it.
- `bfbePlLimit` (number) **At most (s)**. The longest the screen stays, 3 seconds unless set lower, down to 0.5. It leaves sooner when the page is ready.
- `bfbePlColor` (color) **Screen colour**. The colour behind the screen's contents. Unset, it is the page's own background (the body's, else the root's, else white).
- `bfbePlFade` (number) **Fade (ms)**. How long it takes to leave, 200 unless set.

## What it guarantees for accessibility (do not undo)
- Hidden from screen readers: the screen is decoration, and its contents never take keyboard focus.
- While it is up it takes the clicks it covers, so nothing unseen is pressed through it.
- Visitors who ask their device for less motion never see it.
- A page brought back by the browser's Back button never shows it.
<!-- bfbe:generated:end -->

## Rendered DOM

On a page whose Conditions name a loader, the screen is printed first in the body (Bricks' `bricks_body`), before the
page's own header and content:

```html
<div class="bfbe-pl" aria-hidden="true" data-bfbe-pl="123" data-bfbe-pl-first
     style="position:fixed;inset:0;z-index:99990;display:flex;flex-direction:column;align-items:center;
            justify-content:center;--bfbe-pl-max:3000ms;--bfbe-duration:200ms;background-color:#101828">
  <script>/* reduced motion, first page of a visit, page colour */</script>
  <div class="bfbe-pl__body" inert><!-- the template's elements, rendered by Bricks --></div>
</div>
```

- **On the screen**: `data-bfbe-pl` (the template id), `data-bfbe-pl-first` only with **Show** `first`, and inline: its place and layer, `--bfbe-pl-max` (**At most**, in ms), `--bfbe-duration` only when **Fade** is set, `background-color` only when **Screen colour** is set. <!-- src: plugins/bfb-elements-pro/includes/class-page-loader.php:359-381 -->
- **`.bfbe-pl__body`** is `display: contents` and `inert`: the template's root elements are the flex children of the screen, a centred column with a 16px gap (`--bfbe-gap`). <!-- src: src/elements/page-loader/page-loader.css:3-14,32 -->
- **The inline script** runs where it is printed, before the first paint: it removes the screen for reduced motion or a later page of a visit, and paints the page's colour when Screen colour is unset. It is found by the string `bfbe-pl-seen`; the plugin asks the common script optimisers to leave it alone.
- **States**: the CSS fades the screen out at `--bfbe-pl-max` (animation `bfbe-pl-out`); when the page is ready the script adds `.is-done` (animation `bfbe-pl-done`, starting now), then removes the screen from the page once faded.
- **Files**: `bfbe-page-loader` CSS (0.36 KB gzipped, in the head, with the loader's elements' CSS, global classes included, and their own files) and JS (0.70 KB, at the end of the page), only on pages with a loader.
- **In the builder**, editing the loader template, the body has `bfbe-pl-canvas`: `#brx-content` is full height, its contents centred, on the Screen colour.

## Wiring to other elements

- **Its Conditions decide where it shows**, stored as `templateConditions` in the template's settings, written with `bricks/set-template-conditions` (or as that key through `bricks/set-template-settings`): `any` (entire website), `frontpage`, `postType`, `archiveType`, `search`, `error`, `terms`, `ids`, each with `exclude` to invert.
- **One loader per page.** Every published loader is scored with Bricks' own conditions, as a header is: an individual page (`ids`) beats a post type, which beats the entire website. A site can keep a site-wide loader and a page of its own.
- **The four settings** (`bfbePlShow`, `bfbePlLimit`, `bfbePlColor`, `bfbePlFade`) go into the same template settings with `bricks/set-template-settings`, never into an element.
- **Its elements** go into the template like any content template's: `bricks/add-element` or `bricks/set-page-elements` with the template's id as `postId`. Bricks' own elements and pack elements both work; the screen centres them.
- **The page under it** needs nothing and knows nothing of it. Nothing targets the screen, and nothing inside it targets the page: its contents are inert.
- **The first screen's pictures** are what it waits for, so the page's own hero `<img>` decides when it leaves.
- **The switch**: BFB Elements, Elements, Features, Page Loader. Off, no loader shows anywhere.

## Verified patterns

**The demo's loader: a steaming cup, the roastery's name and a line.** The library template `bfb-page-loader` ("Page
Loader: the roastery's name while the page arrives"), shown on `/demo-bfb-page-loader/`. Its stored settings are
`templateConditions` (`ids`: the demo page) and `bfbePlColor`; the other three are written here at their defaults, which
is the same as leaving them out. The id is the page's own.

```json
{
  "templateConditions": [ { "main": "ids", "ids": [ 123 ] } ],
  "bfbePlShow": "every",
  "bfbePlLimit": 3,
  "bfbePlColor": { "hex": "#101828" },
  "bfbePlFade": 200
}
```

Its elements. The motion is an SVG with its own CSS animation in Bricks' SVG element (upload it with `bricks/upload-media`
and use the attachment it returns); it moves from the first paint with no script. The section's padding is zeroed so the
screen centres the group.

```json
{ "name": "section", "settings": { "_padding": { "top": "0", "right": "0", "bottom": "0", "left": "0" } }, "children": [
  { "name": "container", "settings": { "_alignItems": "center", "_rowGap": "8px" }, "children": [
    { "name": "svg", "settings": { "file": { "id": 456, "url": "https://example.com/wp-content/uploads/steam.svg", "filename": "steam.svg" }, "width": "112px", "height": "112px", "_margin": { "bottom": "8" } } },
    { "name": "text-basic", "settings": { "text": "Northwind", "tag": "p", "_typography": { "font-size": "clamp(30px, 24px + 1.4vw, 44px)", "font-weight": "700", "line-height": "1.1", "letter-spacing": "-0.025em", "color": { "hex": "#ffffff" } }, "_margin": { "bottom": "0" } } },
    { "name": "text-basic", "settings": { "text": "Coffee roasters, Bailey Street", "tag": "p", "_typography": { "font-size": "14px", "line-height": "1.5", "color": { "hex": "#98a2b3" } }, "_margin": { "bottom": "0" } } }
  ] }
] }
```

**Search results, once a visit.** The settings of the feature visual's loader "Northwind, search results": shown on
the search results page, the first time in the tab only.

```json
{ "templateConditions": [ { "main": "search" } ], "bfbePlShow": "first", "bfbePlColor": { "hex": "#101828" } }
```

**Every archive, two seconds at most.** The feature visual's loader "Northwind, the journal".

```json
{ "templateConditions": [ { "main": "archiveType", "archiveType": [ "any" ] } ], "bfbePlLimit": 2, "bfbePlColor": { "hex": "#101828" } }
```

## Gotchas

- **No Conditions, no loader.** A loader template with an empty `templateConditions` shows on no page. Set them in the same build. <!-- src: plugins/bfb-elements-pro/includes/class-page-loader.php:148-153 -->
- **`bricks/create-template` refuses the type.** Its list of template types is Bricks' own, so `type: "bfbe_page_loader"` is an invalid parameter. The owner makes the template (Bricks, Templates, Add New, type BFB Page Loader); find it with `bricks/list-templates` and `type: "bfbe_page_loader"`, then fill it. <!-- src: themes/bricks/includes/abilities/templates.php:24-54,682 (Bricks 2.4.2) -->
- **A loader with no elements draws nothing**, not even a coloured screen. <!-- src: plugins/bfb-elements-pro/includes/class-page-loader.php:354-357 -->
- **Ready means three things**: the document read, the fonts in, and every `<img>` in the first screen loaded (one with no size yet counted by where it sits, a lazy-load placeholder counted until its `data-src` picture comes). CSS background images, videos, iframes and other scripts are not waited for. <!-- src: src/elements/page-loader/page-loader.js:26-59 -->
- **At most is held to 0.5 to 3 seconds**, and Fade to 0 to 1000 ms (the pack's 200 ms unset). The limit is CSS alone, so the screen leaves even when its script is blocked; a page ready after the limit lets that fade finish. <!-- src: plugins/bfb-elements-pro/includes/class-page-loader.php:359-366; src/elements/page-loader/page-loader.css:15-22; docs/elements/page-loader.md "The honest rule" -->
- **A Lottie starts late.** Its player loads at the end of the page, so on a loader it starts about when the screen leaves. Use an animated SVG (Bricks' SVG element) or CSS. <!-- src: docs/elements/page-loader.md "Motion on the screen"; docs/RELEASE-BRIEF-1.3.0.md BOUNDS -->
- **It is decoration.** The screen is `aria-hidden` and its contents `inert`: links, buttons and forms in it do nothing and never take focus. While up, it takes the clicks it covers. <!-- src: plugins/bfb-elements-pro/includes/class-page-loader.php:381,398; src/elements/page-loader/page-loader.css:31-32 -->
- **Never shown** to a visitor who asks for reduced motion, on a page brought back by Back from the browser's cache, or in print. Test with reduced motion off. <!-- src: plugins/bfb-elements-pro/includes/class-page-loader.php:394; src/elements/page-loader/page-loader.js:62-67; src/elements/page-loader/page-loader.css:35-41 -->
- **First page of a visit is one mark per tab**: `sessionStorage` key `bfbe-pl-seen`, shared by every loader set to `first`. A visitor who blocks site data sees it on every page. <!-- src: plugins/bfb-elements-pro/includes/class-page-loader.php:394 -->
- **Screen colour unset is the page's own background**: the body's, else the root's, else white. A see-through colour lets the page show through as it is drawn. <!-- src: plugins/bfb-elements-pro/includes/class-page-loader.php:384-394; src/elements/page-loader/page-loader.css:12-13; docs/elements/page-loader.md "How" -->
- **The builder never shows it on a page.** Loaders are resolved on the front end only; the loader template's own canvas is drawn as the screen. Check it by visiting a page its Conditions name. <!-- src: plugins/bfb-elements-pro/includes/class-page-loader.php:143-147,70-86 -->
- **It needs Pro.** Bricks takes a template type it does not know for page content. Pro deactivated parks its loaders as drafts and publishes them again on activation; imported to a site without Pro, a published loader takes over the pages its Conditions name. <!-- src: plugins/bfb-elements-pro/includes/class-page-loader.php:20-24,195-235; docs/REVIEW-2026-10-15.md loader-1 (d) -->

## Never do

- Do not leave `templateConditions` empty on a loader.
- Do not build a loader as a `section`, `content` or `popup` template to get round `bricks/create-template`: only the type `bfbe_page_loader` makes it a loader.
- Do not put a link, button, form or anything a visitor must read or press in the loader.
- Do not use a Lottie for the loader's motion; use an animated SVG or CSS.
- Do not set `bfbePlLimit` above 3 or `bfbePlFade` above 1000; they are held there.
- Do not set a see-through `bfbePlColor`.
- Do not publish a loader template on a site without BFB Elements Pro active.
- Do not write the four `bfbePl*` keys into an element or a page's settings; they belong to the loader template.
