---
name: bfbe-audio-player
description: "Use when placing, wiring or styling BFB Audio Player (`bfbe-audio-player`): a player for a podcast, a track or an album, built on the Video Player so it shares its script, keys and Player Controls. Read before writing its settings."
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

**Costs a page:** CSS 1.32 KB, JS none (gzipped), no dependencies, loaded only on pages that use it.

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
- `loopTitle` (text) **Title**: dynamic data accepted; only when `source` is `loop`. The title on the Card or Bar, which also names the player for screen readers. In a playlist, the card shows each track's own title. It takes dynamic data.
- `loopPoster` (text) **Cover**: dynamic data accepted; only when `source` is `loop`. Choose the artwork for the Card. Its Size is in the Look group, 96px by default. A playlist track shows the Cover set in its own row instead.
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
- `iconSettings` (icon) **Settings menu**: only when `menu` is set. Tick it to add a menu for the speed and, on a stream, its quality and audio tracks. Where the browser plays a stream itself, as Safari and iPhones do, quality and audio tracks are left out. It works with the arrow keys.
- `iconLoop` (icon) **A-B loop**: only when `abLoop` is set. Tick it to add a button that loops a stretch. Press it where the stretch starts, again where it ends, and a third time to stop.
- `iconShare` (icon) **Copy link**: only when `share` is set. Tick it to add a button that copies a link to this page. The link starts the audio at the moment playing.
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

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
