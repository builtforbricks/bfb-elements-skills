---
name: bfbe-audio-player
description: "Use when placing, wiring or styling BFB Audio Player (`bfbe-audio-player`): a podcast episode, a track or an album as a cover card, a one-line bar or a layout built from Player Controls, with chapters, playlists and a waveform on the progress line. Read before writing its settings."
---

# BFB Audio Player (`bfbe-audio-player`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-audio-player.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/audio-player/

## What it is
A player for a podcast, a track or an album, built on the Video Player so it shares its script, keys and Player Controls. Skins are a Card with cover, title and artist, a Bar that holds everything on one line, and a Custom skin you build. A playlist lists its tracks under the player, and a waveform can be drawn on the line from a reading taken once in the builder.

**Not for:** Not for audio hosted on YouTube or Vimeo: no provider source is offered, and a playlist keeps just the rows that are files or streams. It also has no autoplay control, because browsers allow autoplay only without sound.

**Costs a page:** CSS 1.32 KB, JS none (gzipped), no dependencies, loaded only on pages that use it. Only where used, the waveform reader: JS 1.09 KB.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Nestable: any Bricks element goes inside (blocks, headings, text, images, a form).

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Audio (`bfbeVideo`)
- `source` (select) **Source**: options: `self` A file on this site (default), `rows` A playlist you write, `loop` A playlist from a query loop, `list` Playlist Items you place on the page. A file on this site is the default. The other choices are A playlist you write, A playlist from a query loop and Playlist Items you place on the page. YouTube, Vimeo and Another host are not offered.
- `file` (file) **Audio file**: only when `source` is `` or `self`. Choose a file from the media library. Formats WordPress refuses, such as Opus and WEBA, go in through Or an audio URL instead.
- `url` (text) **Or an audio URL**: placeholder https://example.com/episode.mp3; dynamic data accepted; only when `source` is `` or `self`. Type the address of an audio file or stream, such as a format the media library refuses. It takes dynamic data.
- `fileAlt` (file) **Second format**: only when `source` is `` or `self`. Add a second copy, the other of MP3 and Ogg, if you have it. A browser that cannot play one plays the other. Or its URL takes an address instead.
- `urlAlt` (text) **Or its URL**: placeholder https://example.com/episode.ogg; dynamic data accepted; only when `source` is `` or `self`
- `poster` (image) **Cover**. Choose the artwork for the Card. Its Size is in the Look group, 96px by default. A playlist track shows the Cover set in its own row instead.
- `title` (text) **Title**: dynamic data accepted. The title on the Card or Bar, which also names the player for screen readers. In a playlist, the card shows each track's own title. It takes dynamic data.
- `byline` (text) **Artist or show**: dynamic data accepted; only when `skin` is not `custom`. Type the line under the title on the Card. A playlist track can carry its own through Artist or note.
- `schema` (checkbox) **Structured data**: only when `source` is not `list`. Tick it to add AudioObject markup for search engines. It is not offered with Playlist Items you place on the page.
- `description` (textarea) **Description**: dynamic data accepted; only when `schema` is set and `source` is not `list`. With Structured data ticked, add a short description to that markup. It takes dynamic data.

### Playback (`bfbePlay`)
- `loop` (checkbox) **Loop**: only when `source` is `` or `self` or `youtube` or `vimeo` or `rows` or `loop` or `list`. Tick it to play the track again each time it ends, which suits a bed of sound or a short clip.
- `preload` (select) **Load ahead**: options: `metadata` The length (default), `none` Nothing until played, `auto` As much as the browser likes; only when `source` is `` or `self` or `rows` or `loop` or `list`. The length is the default, which fetches just enough to show the duration. Choose Nothing until played to hold the download back.
- `resume` (checkbox) **Remember position**: only when `source` is `` or `self` or `rows` or `loop`. Tick it to let a returning visitor resume an episode where they stopped, kept in their browser by file.

### Chapters (`bfbeChapters`)
The whole group shows only when `source` is `` or `self`.
- `chapters` (repeater) **Chapters**: placeholder Chapter; only when `source` is `` or `self`. For a file on this site, add one row per chapter with its Title and Starts at, in seconds or as 1:30. Rows sort by time, and a row with no Title is called Chapter and its number.
- `chapterMarks` (checkbox) **Marks on the line**: only when `source` is `` or `self` and `chapters` is set. Tick it to mark where each chapter starts on the progress line. Mark colour sets their color.
- `chapterList` (checkbox) **List under the player**: only when `source` is `` or `self` and `chapters` is set. Tick it to list the chapters under the player, each a button that jumps to its chapter and plays.
- `chapterMenu` (checkbox) **Menu in the bar**: only when `source` is `` or `self` and `chapters` is set and `skin` is not `custom`. Tick it to add a Chapters menu to the bar. It is not offered with the Custom skin.
Styling, in the schema file: `chapterColor`.

### Controls (`bfbeControls`)
- `bar` (select) **Buttons**: options: `full` Play, progress, time and sound (default), `essential` Play, progress and time, `bare` Play and progress; only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. The default set is Play, progress, time and sound. Play, progress and time is a shorter set, and Play and progress is the shortest.
- `volumeDir` (select) **Volume slider**: options: `across` Across, from the sound button (default), `up` Upward, above the sound button, `none` None, the button only mutes; only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom` and `bar` is `` or `full`. With the full set of Buttons, pick Across, from the sound button (the default), Upward, above the sound button, or None, the button only mutes. Across takes its width from the progress line.
- `noBig` (checkbox) **No play button on the cover**: only when `skin` is `` or `card`. With the Card skin, tick it to leave out the play button on the cover.
- `skip` (checkbox) **Skip**: only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. Tick it to add buttons that skip back and forward by Skip by (seconds). A note above the button shows how far it went.
- `skipBy` (number) **Skip by (seconds)**: only when `source` is `` or `self` or `rows` or `loop` or `list`. Set how far the Skip buttons and the j and l keys jump, 10 seconds by default.
- `playlistSkip` (checkbox) **Previous and next**: only when `skin` is not `custom` and `source` is `rows` or `loop` or `list`. With a playlist, tick it to add Previous track and Next track buttons.
- `speed` (checkbox) **Speed**: only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. Tick it to add a button that cycles through six playback speeds from 0.5x to 2x.
- `menu` (checkbox) **Settings menu**: only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. Tick it to add a menu for the speed and, on a stream, its quality and audio tracks. Where the browser plays a stream itself, as Safari and iPhones do, quality and audio tracks are left out. It works with the arrow keys.
- `abLoop` (checkbox) **A-B loop**: only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. Tick it to add a button that loops a stretch. Press it where the stretch starts, again where it ends, and a third time to stop.
- `share` (checkbox) **Copy link**: only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. Tick it to add a button that copies a link to this page. The link starts the audio at the moment playing.
- `wave` (checkbox) **Draw on the line**. Tick it to draw the progress line as the file's waveform. The waveform is read once in the builder, so visitors download nothing for it. Height sets how tall it is, 40px by default.
Styling, in the schema file: `noteTypography`, `noteBackground`, `noteBorder`, `waveHeight`.

### Playlist (`bfbePlaylist`)
The whole group shows only when `source` is `rows` or `loop` or `list`.
- `playlistRows` (repeater) **Tracks**: placeholder Video; only when `source` is `rows`. For A playlist you write, add one row per track with its Title, Audio URL or Or an audio file, Cover and Artist or note. Files and streams are kept, and YouTube or Vimeo rows are left out.
- `loopUrl` (text) **Audio URL**: dynamic data accepted; only when `source` is `loop`. Under For each result, the address of each result's audio, usually a dynamic tag.
- `loopTitle` (text) **Title**: dynamic data accepted; only when `source` is `loop`. Under For each result, the title each track shows in the list.
- `loopPoster` (text) **Cover**: dynamic data accepted; only when `source` is `loop`. Under For each result, the address of each track's cover picture.
- `loopNote` (text) **Note**: dynamic data accepted; only when `source` is `loop`. Under For each result, a short line under each title, such as the artist.
- `playlistNext` (checkbox) **Play the next one**: only when `source` is `rows` or `loop` or `list`. Tick it to send a finished track straight on to the next, since an audio playlist has no countdown card.
- `playlistRepeat` (checkbox) **Repeat the list**: only when `source` is `rows` or `loop` or `list` and `playlistNext` is set. With Play the next one ticked, tick it to go on from the last track to the opening one. Previous and next then wrap round too.
Styling, in the schema file: `playlistAround`, `playlistThumbWidth`, `playlistGap`, `playlistItemGap`, `playlistItemPadding`, `playlistItemBorder`, `playlistItemShadow`, `playlistItemBackground`, `playlistActiveBackground`, `playlistTitleTypography`, `playlistNoteTypography`.

### Look (`bfbeLook`)
- `skin` (select) **Skin**: options: `card` Card: the cover beside the title (default), `bar` Bar: everything on one line, `custom` Custom: you build it; only when `source` is `` or `self` or `rows` or `loop` or `list`. Card: the cover beside the title is the default. Bar puts everything on one line, and Custom lets you build it from Player Controls.
- `iconBig` (icon) **Play button icon**: only when `noBig` is not set and `skin` is `` or `card`
Styling, in the schema file: `iconSize`, `fg`, `accent`, `playBackground`, `playColor`, `lineTrack`, `lineLoaded`, `lineHeight`, `lineHoverHeight`, `lineRadius`, `lineThumb`, `lineThumbSize`, `coverSize`, `coverBorder`, `bigSize`, `titleTypography`, `bylineTypography`, `timeTypography`.

### Buttons (`bfbeButtons`)
The whole group shows only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`.
Styling only, every key in the schema file: `iconColor`, `iconHoverColor`, `btnBackground`, `btnHoverBackground`, `btnSize`, `btnBorder`, `btnShadow`.

### Icons (`bfbeIcons`)
The whole group shows only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`.
- `iconPlay` (icon) **Play**. Your own icon for the play button. Pause, Chapter menu, Settings menu, A-B loop and Copy link work the same way, and one left empty keeps the drawn mark.
- `iconPause` (icon) **Pause**
- `iconChapters` (icon) **Chapter menu**: only when `source` is `` or `self` and `chapters` is set and `chapterMenu` is set
- `iconSettings` (icon) **Settings menu**: only when `menu` is set
- `iconLoop` (icon) **A-B loop**: only when `abLoop` is set
- `iconShare` (icon) **Copy link**: only when `share` is set
- `iconBack` (icon) **Back**: only when `skip` is set. Under Skip buttons, your own icon for skipping back. Forward is the one for skipping forward.
- `iconForward` (icon) **Forward**: only when `skip` is set
- `iconPrev` (icon) **Previous**: only when `source` is `rows` or `loop` or `list` and `playlistSkip` is set. Under Previous and next, your own icon for the previous track. Next is the one for the next track.
- `iconNext` (icon) **Next**: only when `source` is `rows` or `loop` or `list` and `playlistSkip` is set
- `iconSound` (icon) **On**: only when `bar` is `` or `full`. Under Sound, your own icon for the sound button. Off is the one shown while the sound is off.
- `iconMuted` (icon) **Off**: only when `bar` is `` or `full`

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Snappy by default. Pick another curve from the list, or Custom to type your own in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`.

## What it guarantees for accessibility (do not undo)
- The player is a focusable group named by its title, or by the word Audio when there is none.
- It takes the same keys as the Video Player where audio can use them.
- Space or k plays and pauses, j and l skip, and M mutes.
- The left and right arrows move 5 seconds, the up and down arrows change the volume, and Home and End jump to the ends.
- A polite live region announces Playing and Paused, and the buttons carry names such as Play, Previous track and Next track.
- The seek line is a range input named Seek with the time as its value text, and the written time is hidden from assistive technology.
- A playlist marks the current track with aria-current, and its Previous and Next buttons disable at the ends of the list unless Repeat the list is on.
<!-- bfbe:generated:end -->

## Rendered DOM

The Video Player's own markup, laid out for sound: its `bfbe-vp__*` parts are driven by `video-player.min.js`, the `bfbe-ap__*` layout is `audio-player.min.css`, and there is no audio script. A Card with chapters, the full bar and a read waveform:

```html
<div class="brxe-bfbe-audio-player bfbe-vp bfbe-ap bfbe-ap--card bfbe-vp--big bfbe-ap--wave is-waved is-ready"
     tabindex="0" role="group" aria-label="Counting to ten" style="--bfbe-ap-wave:url(&quot;data:image/svg+xml,...&quot;)"
     data-bfbe-unplayable="This browser cannot play this file." data-bfbe-chapters="[[0,&quot;One to three&quot;],...]">
  <div class="bfbe-vp__stage bfbe-ap__art"><img class="bfbe-vp__cover" alt=""><button class="bfbe-vp__big" data-bfbe-do="toggle" aria-label="Play">...</button></div>
  <div class="bfbe-ap__body">
    <div class="bfbe-ap__text"><span class="bfbe-ap__title bfbe-vp__now">...</span><span class="bfbe-ap__byline bfbe-vp__byline" data-bfbe-own="...">...</span></div>
    <audio class="bfbe-vp__video" preload="metadata"><source src="..." type="audio/wav"></audio>
    <div class="bfbe-ap__own"><!-- nested elements --></div>
    <div class="bfbe-vp__bar bfbe-vp__bar--full"><div class="bfbe-vp__row">
      <span class="bfbe-vp__group bfbe-vp__group--left"><!-- button.bfbe-vp__btn[data-bfbe-do]: prev, back, toggle, fwd, next --></span>
      <span class="bfbe-vp__seek"><span class="bfbe-vp__marks">...</span><input type="range" class="bfbe-vp__range bfbe-vp__range--time" aria-label="Seek"></span>
      <span class="bfbe-vp__group bfbe-vp__group--right"><!-- .bfbe-vp__time, speed, menus, .bfbe-vp__vol, .bfbe-vp__ab, .bfbe-vp__share --></span>
    </div></div></div><span class="bfbe-sr bfbe-vp__live" aria-live="polite"></span>
  <ol class="bfbe-vp__chapters">...</ol> <ol class="bfbe-vp__list">...</ol> <script type="application/ld+json">...</script>
</div>
```

- The stage is the cover: a click on it plays or pauses. Nested elements land in `.bfbe-ap__own`, between the words and the bar in a Card or a Bar; in Custom they are the whole player and the stage is `display: none`. Until the script runs, `<audio>` carries `controls` and the browser's own bar plays it. The script removes `controls` and adds `is-ready`, which shows ours.
- **Buttons** `bar` sets `bfbe-vp__bar--full`, `--essential` (no sound) or `--bare` (no time either). Root states: `is-playing`, `is-started` (kept after the first play), `is-ended`, `is-waiting`, `is-muted`, `is-chaptered` once the marks are placed, `is-ab-a` then `is-ab`, and `is-unplayable`, whose `::after` prints `data-bfbe-unplayable`.
- The waveform: `bfbe-ap--wave` whenever **Draw on the line** `wave` is on; `is-waved` and the inline `--bfbe-ap-wave` mask only once the file has a reading. Rows and Playlist Items carry their file's reading as `data-bfbe-peaks`. In the canvas only: `data-bfbe-wave-api`, `-nonce`, `-need` (a file not read yet) and `-failed`.
- A playlist adds `bfbe-vp--list` and `bfbe-vp--tracks` (rows, loop) or `bfbe-vp--built` (Playlist Items) to the root. Rows are `button.bfbe-vp__item-btn[data-bfbe-src]` with `.bfbe-vp__item-thumb`, `-title` and `-note`; the chosen one gets `aria-current="true"` and `is-current`, and `is-playing` while it plays. Chapter buttons (`.bfbe-vp__chapter-btn[data-bfbe-at]`) take `aria-current="true"` while their chapter plays.
- Where styling lands: **Text colour** `fg` on `.bfbe-ap__text` and `.bfbe-vp__time` only; **Progress colour** `accent` on the played part of the line; the Buttons group on `.bfbe-vp__bar .bfbe-vp__btn`; `playBackground` and `playColor` on `.bfbe-vp__toggle`; `coverSize` and `coverBorder` on `.bfbe-vp__stage`.

## Wiring to other elements

- **Player Controls** (`bfbe-video-control`, schema `../bfbe-schemas/references/elements/bfbe-video-control.json`) go inside the player, at any depth, in blocks of their own. They render the built-in bar's classes and `data-bfbe-do`, so the player's script drives them with no further setting. Set **Which control** `kind`; skips take their own `skipBy`, the sound control `volumeDir`. Outside a player nothing drives them, and the builder says so.
- **Playlist Items** (`bfbe-playlist-item`, schema `../bfbe-schemas/references/elements/bfbe-playlist-item.json`): set the player's `source: "list"` and give each item `url` or `file`. Each item plays in the nearest player set to `list`: the first inside the closest ancestor that holds one, so place the items in the same section as their player. **Which player** `player` takes a CSS ID instead; avoid it, because component instances share ids. An item's own `hasLoop` and `query` repeat it per post. From the fixture page `fixture-audio-player`, addresses made generic:

```json
{ "name": "block", "settings": { "_rowGap": "12px" }, "children": [
  { "name": "bfbe-audio-player", "settings": { "source": "list", "title": "Episodes", "skin": "bar", "playlistSkip": true, "playlistNext": true } },
  { "name": "block", "settings": { "_display": "grid", "_gridTemplateColumns": "repeat(3, 1fr)", "_gridGap": "12px" }, "children": [
    { "name": "bfbe-playlist-item", "settings": { "url": "https://example.com/wp-content/uploads/episode-1.mp3", "bars": true }, "children": [ { "name": "heading", "settings": { "text": "Episode one", "tag": "h4" } } ] },
    { "name": "bfbe-playlist-item", "settings": { "url": "https://example.com/wp-content/uploads/episode-2.m4a", "bars": true }, "children": [ { "name": "heading", "settings": { "text": "Episode two", "tag": "h4" } } ] }
  ] } ] }
```

- **Every BFB player on the page.** Starting one pauses any other Audio or Video Player playing with sound. A **Copy link** address carries `?t=` seconds, which seeks every player on the page whose file is that long, and `?v=` opens that track number in every playlist.
- **Dark Mode.** Under the Dark Mode Toggle's dark state, the Card or Bar play button's mark turns black or white from its fill, unless **Icon colour** `playColor` is set.
- **Targeting.** To style one player, give it a class in `_cssClasses` and select from it; never `_cssId`, because component instances share ids. Markup added outside Bricks' AJAX events needs `window.bfbeVideoPlayer()` called, and `window.bfbeVideoPlayerPlaylist()` for a playlist.

## Verified patterns

**A podcast episode on a Card, with the full built-in bar.** From the fixture page `fixture-audio-player`, trimmed of its colours, sizes and typography; the addresses are made generic (example.com). `poster.id` 7043 is the fixture site's image: use an attachment id from the target site's media library. Chapters show in three places, `skip` with `skipBy` jumps 15 seconds, and `urlAlt` is a second format.

```json
{
  "name": "bfbe-audio-player",
  "settings": {
    "url": "https://example.com/wp-content/uploads/counting.wav",
    "urlAlt": "https://example.com/wp-content/uploads/counting.m4a",
    "title": "Counting to ten", "byline": "The fixture choir", "poster": { "id": 7043, "size": "large" },
    "skip": true, "skipBy": 15, "speed": true, "menu": true, "abLoop": true, "share": true, "resume": true, "wave": true,
    "chapters": [ { "label": "One to three", "at": "0" }, { "label": "Four to six", "at": "0:02" }, { "label": "Seven to ten", "at": "4" } ],
    "chapterMarks": true, "chapterList": true, "chapterMenu": true,
    "schema": true, "description": "Ten numbers, spoken."
  }
}
```

**A layout of your own, built from Player Controls.** From the demo page `demo-bfb-audio-player` (the newest episode), trimmed of its styling, two text lines and one inner block; the address is made generic. `poster.id` 24628 is the demo site's image: use the target site's own. With `skin: "custom"` the player draws nothing itself; the cover is a `poster` control. The demo styles each control with its own `btnColor`, `btnBackground` and `btnSize`.

```json
{
  "name": "bfbe-audio-player",
  "settings": {
    "url": "https://example.com/wp-content/uploads/rye-reading-truth.m4a",
    "title": "The Lamp of Truth", "poster": { "id": 24628, "size": "medium" },
    "skin": "custom", "wave": true, "resume": true,
    "chapters": [ { "label": "The twilight of the virtues", "at": "0" }, { "label": "Truth, the one with no degrees", "at": "0:36" },
      { "label": "The softly spoken lie", "at": "2:05" }, { "label": "Do not let us lie at all", "at": "3:48" } ],
    "chapterMarks": true, "chapterList": true,
    "schema": true, "description": "Ruskin on truth in building, read aloud."
  },
  "children": [
    { "name": "block", "settings": {}, "children": [
      { "name": "bfbe-video-control", "settings": { "kind": "poster" } }, { "name": "bfbe-video-control", "settings": { "kind": "title" } }
    ] },
    { "name": "block", "settings": {}, "children": [
      { "name": "bfbe-video-control", "settings": { "kind": "back", "skipBy": 15 } },
      { "name": "bfbe-video-control", "settings": { "kind": "play" } }, { "name": "bfbe-video-control", "settings": { "kind": "forward", "skipBy": 15 } },
      { "name": "bfbe-video-control", "settings": { "kind": "seek" } }
    ] },
    { "name": "block", "settings": {}, "children": [
      { "name": "bfbe-video-control", "settings": { "kind": "time" } }, { "name": "bfbe-video-control", "settings": { "kind": "speed" } },
      { "name": "bfbe-video-control", "settings": { "kind": "volume", "volumeDir": "up" } }
    ] }
  ]
}
```

**An album: a playlist you write.** From the fixture page `fixture-audio-player`, addresses made generic and its YouTube row left out (an audio playlist drops it anyway). `poster.id` 7043 is the fixture site's image: use the target site's own. Each row's `note` replaces the artist line, and a row without one shows `byline`. `playlistNext` with `playlistRepeat` plays on and wraps round, and each track draws its own waveform once read.

```json
{
  "name": "bfbe-audio-player",
  "settings": {
    "source": "rows", "title": "A playlist", "byline": "Various", "poster": { "id": 7043, "size": "large" }, "noBig": true,
    "playlistRows": [
      { "title": "In WAV", "url": "https://example.com/wp-content/uploads/tone.wav", "note": "Uncompressed" },
      { "title": "In FLAC", "url": "https://example.com/wp-content/uploads/tone.flac", "note": "Lossless" },
      { "title": "In AAC", "url": "https://example.com/wp-content/uploads/tone.m4a" }
    ],
    "playlistNext": true, "playlistRepeat": true, "playlistSkip": true,
    "playlistThumbWidth": "52px", "wave": true, "waveHeight": "28px"
  }
}
```

## Gotchas

- **The waveform is read in the builder, never by an agent.** `wave: true` written over MCP draws the plain line until someone opens the page in the Bricks builder, whose canvas decodes each unread file once. The reading is kept by the file's URL, so another player, query loop or Playlist Item with that URL reuses it. <!-- src: plugins/bfb-elements-pro/elements/audio-player.php:378; plugins/bfb-elements-pro/elements/audio-player.php:460; src/elements/audio-player-wave/audio-player-wave.js:70; plugins/bfb-elements-pro/includes/class-audio-peaks.php:94 -->
- **Not every editor can save a reading.** The save needs `edit_posts`, plus `edit_post` on a media-library file or `edit_others_posts` for any other URL. A refused or unreadable file (another host without CORS, a stream, a format that browser cannot decode) keeps the plain line. <!-- src: plugins/bfb-elements-pro/includes/class-audio-peaks.php:50; plugins/bfb-elements-pro/includes/class-audio-peaks.php:72; src/elements/audio-player-wave/audio-player-wave.js:26 -->
- **A waved line ignores the line's shape controls.** Its height is **Height** `waveHeight` (40px); `lineHeight`, `lineHoverHeight`, `lineRadius`, `lineThumb` and `lineThumbSize` do nothing there. The colours (`accent`, `lineTrack`, `lineLoaded`) still show through the mask. <!-- src: src/elements/audio-player/audio-player.css:76; src/elements/video-player/video-player.css:76 -->
- **The play button is not the Progress colour.** On a Card or Bar it fills with the pack's accent; set **Background** `playBackground` and **Icon colour** `playColor`. `btnBackground` skips it, and `fg` reaches only the words and the time. <!-- src: src/elements/audio-player/audio-player.css:11; src/elements/audio-player/audio-player.css:63; plugins/bfb-elements-pro/elements/audio-player.php:205; docs/elements/audio-player.md "Three skins" -->
- **Custom draws only what you nest.** With `skin: "custom"` the cover box is hidden and there are no words or bar; `byline`, `bar`, `skip`, `speed`, `menu`, `abLoop`, `share`, `chapterMenu`, `playlistSkip` and the cover, words, Buttons and Icons controls are hidden, so they are dropped before render. <!-- src: src/elements/audio-player/audio-player.css:101; plugins/bfb-elements-pro/elements/audio-player.php:224; plugins/bfb-elements/includes/abstract-element.php:86 -->
- **Four Player Control kinds draw nothing here.** `fullscreen`, `pip`, `big` and `cc` show a notice in the builder and no markup on the page: an audio player has no picture. <!-- src: plugins/bfb-elements-pro/elements/video-control.php:556 -->
- **YouTube and Vimeo rows are dropped.** A written or looped playlist keeps files and streams only; with none left, the page gets no markup and the canvas says "This playlist has no audio files yet." A row with no title is called Track and its number. <!-- src: plugins/bfb-elements-pro/elements/audio-player.php:394; plugins/bfb-elements-pro/elements/video-player.php:2337 -->
- **This query loop is the playlist.** `hasLoop` and `query` are offered only with `source: "loop"`, each result's address in `loopUrl`. For one player per post, put the player in a looping container and give `url` a dynamic tag. <!-- src: plugins/bfb-elements-pro/elements/video-player.php:725; plugins/bfb-elements-pro/elements/video-player.php:2213 -->
- **Chapters and Structured data are a single file's.** `chapters` is offered only with `source: "self"`, and a **Starts at** that is not seconds, `m:ss` or `h:mm:ss` drops its row. In a playlist the AudioObject names the first track; `uploadDate` and `duration` come only from a media-library `file`. <!-- src: plugins/bfb-elements-pro/elements/video-player.php:2394; plugins/bfb-elements-pro/elements/video-player.php:2922; plugins/bfb-elements-pro/elements/audio-player.php:422 -->
- **The media library refuses several formats.** Opus, WEBA, MP2 and similar go in through `url`. A file the browser cannot decode (MP2, CAF, AIFF or AU in Chrome) sets `is-unplayable` and prints "This browser cannot play this file." <!-- src: plugins/bfb-elements-pro/elements/audio-player.php:158; plugins/bfb-elements-pro/elements/audio-player.php:501; docs/elements/audio-player.md "Every file type, measured" -->
- **The builder's view differs from the page.** In the canvas a track ending does not go on to the next, a click on a Playlist Item selects it, and notices stand where the page prints nothing (no file, an empty playlist). <!-- src: src/elements/video-player-playlist/video-player-playlist.js:245; src/elements/video-player-playlist/video-player-playlist.js:293; plugins/bfb-elements/includes/abstract-element.php:538 -->
- **A Card reflows at 600px.** At that width and below the bar spans the card under the cover and the words, and the cover is 72px unless `coverSize` is set, which then holds at every width. <!-- src: src/elements/audio-player/audio-player.css:84 -->

## Never do

- Do not deliver `wave: true` without opening the page once in the builder, as an Editor or above, after the files are final.
- Do not shape a waved line with `lineHeight`, `lineHoverHeight`, `lineRadius`, `lineThumb` or `lineThumbSize`; use `waveHeight`.
- Do not colour the Card's play button with `accent` or `btnBackground`; use `playBackground` and `playColor`.
- Do not set `byline`, `bar`, `skip`, `speed`, `menu`, `abLoop`, `share` or `chapterMenu` with `skin: "custom"`; nest Player Controls instead.
- Do not place Player Controls of kind `fullscreen`, `pip`, `big` or `cc` in an audio player, or any Player Control outside one.
- Do not give an audio playlist YouTube or Vimeo addresses, or set `hasLoop` without `source: "loop"`.
- Do not wire Playlist Items with `player` or a player with `_cssId`; place the items near their player.
- Do not override the root's `role`, `tabindex` or `aria-label` through `_attributes`; **Title** `title` names the group.
