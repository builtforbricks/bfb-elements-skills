---
name: bfbe-video-player
description: "Use when placing, wiring or styling BFB Video Player (`bfbe-video-player`): plays a file from your site, YouTube, Vimeo or another host, with a control bar in three skins and room for content over the picture. Read before writing its settings."
---

# BFB Video Player (`bfbe-video-player`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-video-player.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/video-player/

## What it is
Plays a file from your site, YouTube, Vimeo or another host, with a control bar in three skins and room for content over the picture. For video files, keys work as a video site's do without a setting, and starting one pauses any other video or audio file playing with sound. Playlists, chapters, subtitles, an A-B loop and a remembered position are options, and hls.js is a declared dependency that loads only for HLS streams.

**Not for:** Not for restyling a provider's own controls: YouTube, Vimeo and other hosts play inside their own frame, which this page cannot reach. Chapters are offered for a single video file, and the A-B loop and the Settings menu for video files and streams, alone or in a playlist. For YouTube, Use our bar adds the pack's own bar under their player.

**Costs a page:** CSS 2.75 KB, JS 2.99 KB (gzipped), no dependencies, loaded only on pages that use it.

**Nestable:** yes · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** yes · **Reduced motion:** no

## Structure
Nestable. Its own children: `bfbe-video-control`, `bfbe-playlist-item`.

`bfbe-video-control` (BFB Player Control), 71 controls, schema `../bfbe-schemas/references/elements/bfbe-video-control.json`.

`bfbe-playlist-item` (BFB Playlist Item), 45 controls, schema `../bfbe-schemas/references/elements/bfbe-playlist-item.json`, nestable itself.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Video (`bfbeVideo`)
- `source` (select) **Source**: options: `self` A file on this site (default), `youtube` YouTube, `vimeo` Vimeo, `embed` Another host, `rows` A playlist you write, `loop` A playlist from a query loop, `list` Playlist Items you place on the page. A file on this site is the default. You can also pick YouTube, Vimeo or Another host, or a playlist: A playlist you write, A playlist from a query loop or Playlist Items you place on the page.
- `file` (file) **Video file**: only when `source` is `` or `self`. Choose the file to play. It sits in a plain video element with the browser's controls, so it plays before the script arrives or without it.
- `providerUrl` (text) **Video URL**: placeholder https://www.youtube.com/watch?v=...; dynamic data accepted; only when `source` is `youtube` or `vimeo` or `embed`. For YouTube, Vimeo or Another host, paste the address of the video's page. It takes dynamic data. Another host works when WordPress knows how to embed its videos.
- `privacy` (checkbox) **Privacy**: only when `source` is `youtube` or `vimeo` or `rows` or `loop` or `list`. For YouTube, Vimeo and every playlist. Tick it and nothing loads from YouTube or Vimeo until someone presses play, their thumbnails included, so set a Poster. A single YouTube video then plays from YouTube's no-cookie domain, and a playlist's YouTube rows do too. A browser with scripts off still loads their player with the page.
- `bridge` (checkbox) **Use our bar**: only when `source` is `youtube`. Tick it for a YouTube video to add our bar under their player, as their terms require. It has play, progress, time, sound and fullscreen.
- `startAt` (number) **Start at (seconds)**: only when `source` is `youtube` or `vimeo`. For YouTube and Vimeo, the second the video starts from, 0 by default.
- `url` (text) **Or a video URL**: placeholder https://example.com/film.mp4; dynamic data accepted; only when `source` is `` or `self`. Type the address of a video file or an HLS stream (.m3u8) in place of a file from the media library. It takes dynamic data.
- `fileAlt` (file) **Second format**: only when `source` is `` or `self`. Add a second copy of the video, the other of WebM and MP4, if you have it. A browser that cannot play one plays the other. Or its URL takes an address instead.
- `urlAlt` (text) **Or its URL**: placeholder https://example.com/film.webm; dynamic data accepted; only when `source` is `` or `self`
- `poster` (image) **Poster**. Choose the picture shown before the video plays. For YouTube and Vimeo it replaces the provider's own thumbnail. With Privacy ticked, your Poster is what shows before play.
- `posterAt` (number) **Poster frame (s)**: only when `source` is `` or `self` and `poster` is not set. With no Poster, a video file shows its frame at this second until it plays. Playing still starts from the beginning.
- `subtitles` (file) **File (.vtt)**: only when `source` is `` or `self`. Add a subtitles file for a video file on your site.
- `subtitlesLang` (text) **Language**: placeholder en; only when `source` is `` or `self` and `subtitles` is set. Type the language code of the subtitles, en by default.
- `subtitlesOn` (checkbox) **On from the start**: only when `source` is `` or `self` and `subtitles` is set. Tick it so the subtitles show without the visitor turning them on.
- `title` (text) **Title**: dynamic data accepted. Names the player for screen readers, and the play button of a YouTube, Vimeo or other-host video. It takes dynamic data.
- `schema` (checkbox) **Structured data**: only when `source` is not `list`. Tick it to add VideoObject markup for search engines. It is not offered with Playlist Items you place on the page.
- `description` (textarea) **Description**: dynamic data accepted; only when `schema` is set and `source` is not `list`. With Structured data ticked, add a short description to that markup. It takes dynamic data.

### Playback (`bfbePlay`)
- `autoplay` (checkbox) **Autoplay, muted**: only when `source` is `` or `self` or `youtube` or `vimeo` or `rows` or `loop` or `list`. Tick it to start a video file muted on load, since browsers allow autoplay without sound. A YouTube or Vimeo video still waits for a press, then plays muted, and any video waits for a press when the visitor asks their device for less motion.
- `muted` (checkbox) **Start muted**: only when `source` is `` or `self` or `youtube` or `vimeo` or `rows` or `loop` or `list` and `autoplay` is not set. Tick it to start with the sound off. It hides once Autoplay, muted is ticked, which mutes the video anyway.
- `loop` (checkbox) **Loop**: only when `source` is `` or `self` or `youtube` or `vimeo` or `rows` or `loop` or `list`. Tick it to play the video again from the start each time it ends. It works for a single YouTube or Vimeo video too.
- `preload` (select) **Load ahead**: options: `metadata` The first frame and the length (default), `none` Nothing until played, `auto` As much as the browser likes; only when `source` is `` or `self` or `rows` or `loop` or `list`. It loads the opening frame and the length by default. Pick Nothing until played to hold the download back, or As much as the browser likes to load more.
- `pauseAway` (checkbox) **Pause off-screen**: only when `source` is `` or `self` or `rows` or `loop` or `list`. Tick it to pause a video file or stream whenever it scrolls out of view.
- `resume` (checkbox) **Remember position**: only when `source` is `` or `self` or `rows` or `loop`. Tick it so a returning visitor resumes where they stopped, kept in their browser by file. A resume is skipped under five seconds in or within ten of the end.

### Chapters (`bfbeChapters`)
The whole group shows only when `source` is `` or `self`.
- `chapters` (repeater) **Chapters**: placeholder Chapter; only when `source` is `` or `self`. For a video file on your site, add one row per chapter with its Title and Starts at, in seconds or as 1:30. Rows sort by time, and a row with no Title is called Chapter and its number.
- `chapterMarks` (checkbox) **Marks on the line**: only when `source` is `` or `self` and `chapters` is set. Tick it to mark where each chapter starts on the progress line. Mark colour sets their color.
- `chapterList` (checkbox) **List under the video**: only when `source` is `` or `self` and `chapters` is set. Tick it to list the chapters under the video, each a button that jumps to its chapter and plays.
- `chapterMenu` (checkbox) **Menu in the bar**: only when `source` is `` or `self` and `chapters` is set and `skin` is not `custom`. Tick it to add a Chapters menu to the bar. It is not offered with the Custom skin.
Styling, in the schema file: `chapterColor`.

### Controls (`bfbeControls`)
- `bar` (select) **Buttons**: options: `full` Play, progress, time, sound, fullscreen (default), `essential` Play, progress, fullscreen, `bare` Play and progress; only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. The default set is Play, progress, time, sound, fullscreen. Play, progress, fullscreen is a shorter set, and Play and progress is the shortest.
- `volumeDir` (select) **Volume slider**: options: `across` Across, from the sound button (default), `up` Upward, above the sound button, `none` None, the button only mutes; only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom` and `bar` is `` or `full`. With the full set of Buttons, pick Across, from the sound button (the default), Upward, above the sound button, or None, the button only mutes. Across takes its width from the progress line.
- `noBig` (checkbox) **No large play button**. Tick it to leave out the large play button in the middle of the picture.
- `skip` (checkbox) **Skip**: only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. Tick it to add buttons that skip back and forward by Skip by (seconds). A note above the button shows how far it went.
- `skipBy` (number) **Skip by (seconds)**: only when `source` is `` or `self` or `rows` or `loop` or `list`. Set the jump for the Skip buttons, the j and l keys and a double tap on either half of the picture. It is 10 seconds by default.
- `playlistSkip` (checkbox) **Previous and next**: only when `skin` is not `custom` and `source` is `rows` or `loop` or `list`. With a playlist, tick it to add buttons that step to the previous and next video. A playlist made just of YouTube or Vimeo videos has no bar to hold them.
- `speed` (checkbox) **Speed**: only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. Tick it to add a button that steps through six speeds, from 0.5x to 2x.
- `menu` (checkbox) **Settings menu**: only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. Tick it to add a menu for speed, subtitles and, on a stream, its quality and audio tracks. Where the browser plays a stream itself, as Safari and iPhones do, quality and audio tracks are left out. It works with the arrow keys.
- `pip` (checkbox) **Picture in picture**: only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. Tick it to add a button that plays the video in a small floating window. Firefox does not let a page open one, so there the button does nothing.
- `abLoop` (checkbox) **A-B loop**: only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. Tick it to add a button that loops a stretch. Press it where the stretch starts, again where it ends, and a third time to stop.
- `share` (checkbox) **Copy link**: only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`. Tick it to add a button that copies a link to this page. The link starts the video at the moment playing.
- `preview` (checkbox) **Frame preview**: only when `source` is `` or `self` or `rows` or `loop` or `list`. Tick it to show a frame above the progress line as the pointer moves. The browser draws it from the video itself, with no extra files, so the file must be on this site or on a host that lets other sites read it. A stream shows none in a browser that cannot play streams itself.
- `idle` (number) **Auto-hide (ms)**: only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `studio` and `skin` is not `custom`. Set how long the bar waits without pointer movement before it fades, 2000 by default. It stays while focus is inside the player, and it is not offered with the Studio or Custom skin.
Styling, in the schema file: `noteTypography`, `noteBackground`, `noteBorder`.

### Over the video (`bfbeOver`)
- `overWhen` (select) **Visibility**: options: `always` Always, `idle` Only on hover, once it plays, `paused` While it is not playing (default), `start` Until it first plays, `after` A set time after it starts playing. Anything you put inside the player sits over the video. Choose when it shows: Always, "Only on hover, once it plays", While it is not playing (the default), Until it first plays, or A set time after it starts playing. Over YouTube, Vimeo and other hosts, it hides once their player starts, whatever you choose.
- `overDir` (select) **Direction**: options: `column` Down the video (default), `row` Across the video; writes CSS. Lay out what sits over the video Down the video, the default, or Across the video. You can set it per breakpoint.
- `overJustify` (select) **Justify content**: options: `flex-start` Start, `center` Middle (default), `flex-end` End, `space-between` Pushed apart, `space-around` Spaced evenly; writes CSS. Where it sits along that direction: Start, Middle (the default), End, Pushed apart or Spaced evenly. You can set it per breakpoint.
- `overAlign` (select) **Align items**: options: `flex-start` Start, `center` Middle (default), `flex-end` End, `stretch` Stretched to fill; writes CSS. Where it sits the other way: Start, Middle (the default), End or Stretched to fill. You can set it per breakpoint.
Styling, in the schema file: `overAfter`, `overPadding`, `overScrim`.

### Playlist (`bfbePlaylist`)
The whole group shows only when `source` is `rows` or `loop` or `list`.
- `playlistRows` (repeater) **Videos**: placeholder Video; only when `source` is `rows`. For A playlist you write, add one row per video with its Title, Video URL or Or a video file, Poster and Note. A row can be a file, an HLS stream, or a YouTube or Vimeo address.
- `loopUrl` (text) **Video URL**: dynamic data accepted; only when `source` is `loop`. For YouTube, Vimeo or Another host, paste the address of the video's page. It takes dynamic data. Another host works when WordPress knows how to embed its videos.
- `loopTitle` (text) **Title**: dynamic data accepted; only when `source` is `loop`. Names the player for screen readers, and the play button of a YouTube, Vimeo or other-host video. It takes dynamic data.
- `loopPoster` (text) **Poster**: dynamic data accepted; only when `source` is `loop`. Choose the picture shown before the video plays. For YouTube and Vimeo it replaces the provider's own thumbnail. With Privacy ticked, your Poster is what shows before play.
- `loopNote` (text) **Note**: dynamic data accepted; only when `source` is `loop`. Under For each result, a short line under each title.
- `playlistNext` (checkbox) **Play the next one**: only when `source` is `rows` or `loop` or `list`. Tick it to offer the next video when a video file or stream ends, on an Up next card with Play now and Stay here buttons. YouTube and Vimeo videos do not move on by themselves.
- `playlistRepeat` (checkbox) **Repeat the list**: only when `source` is `rows` or `loop` or `list` and `playlistNext` is set. With Play the next one ticked, tick it to go on from the last video to the opening one. Previous and next then wrap round too.
- `playlistCountdown` (number) **Countdown (s)**: only when `source` is `rows` or `loop` or `list` and `playlistNext` is set. How long the Up next card counts down, 5 seconds by default and up to 30. Zero plays the next video straight away.
- `playlistLayout` (select) **Position**: options: `right` Beside the video, on the right (default), `left` Beside the video, on the left, `top` Above the video, as cards, `below` Under the video, as cards, `strip` Under the video, as a strip; only when `source` is `rows` or `loop`. Beside the video, on the right is the default. The other choices are Beside the video, on the left, Above the video, as cards, Under the video, as cards and Under the video, as a strip.
- `playlistScroll` (select) **Overflow**: options: `bar` A scrollbar (default), `fade` A gradient edge, `both` Both, `none` Neither; only when `source` is `rows` or `loop` and `playlistLayout` is `` or `right` or `left`. For a list beside the video, how it shows there is more to scroll: A scrollbar (the default), A gradient edge, Both or Neither.
Styling, in the schema file: `playlistWidth`, `playlistAround`, `playlistThumbWidth`, `playlistScrollGap`, `playlistBarWidth`, `playlistBarRadius`, `playlistBarTrack`, `playlistBarThumb`, `playlistFade`, `playlistGap`, `playlistItemGap`, `playlistItemPadding`, `playlistItemBorder`, `playlistItemShadow`, `playlistItemBackground`, `playlistActiveBackground`, `playlistTitleTypography`, `playlistNoteTypography`, `nextBackground`, `nextLabelTypography`, `nextTitleTypography`, `nextBtnColor`, `nextBtnBackground`, `nextBtnHoverBackground`, `nextBtnBorder`, `nextBtnPadding`.

### Look (`bfbeLook`)
- `skin` (select) **Skin**: options: `cinema` Cinema: the bar over the picture (default), `minimal` Minimal: a line and a pill, `studio` Studio: the bar under the picture, `custom` Custom: you build the bar; only when `source` is `` or `self` or `rows` or `loop` or `list`. Cinema, the bar over the picture, is the default. Minimal is a line and a pill, Studio puts the bar under the picture, and Custom uses Player Controls you place.
- `ratio` (select) **Frame**: options: `16-9` 16 : 9 (default), `4-3` 4 : 3, `1-1` Square, `9-16` 9 : 16, portrait, `21-9` 21 : 9, `auto` The video's own. Choose the frame's shape: 16 : 9 (the default), 4 : 3, Square, 9 : 16, portrait, 21 : 9 or The video's own.
- `fit` (select) **Fit**: options: `cover` Fill the frame, cropping (default), `contain` Fit inside the frame; only when `source` is `` or `self` or `rows` or `loop` or `list` and `ratio` is not `auto`. The default fills the frame, cropping the video. Pick Fit inside the frame so nothing is cut off. It is not offered with The video's own.
- `iconBig` (icon) **Icon**: only when `noBig` is not set. Your own icon in place of the drawn mark. While playing, While muted and While fullscreen take the icon for the other state, and one left empty keeps the drawn mark.
Styling, in the schema file: `stageBackground`, `frameBorder`, `shadow`, `fg`, `accent`, `lineTrack`, `lineLoaded`, `lineHeight`, `lineHoverHeight`, `lineRadius`, `lineThumb`, `lineThumbSize`, `barBackground`, `barShade`, `barPadding`, `bridgeBarPadding`, `iconSize`, `timeTypography`, `bridgeTimeTypography`, `bigSize`.

### Buttons (`bfbeButtons`)
The whole group shows only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`.
Styling only, every key in the schema file: `iconColor`, `iconHoverColor`, `btnBackground`, `btnHoverBackground`, `btnSize`, `btnBorder`, `btnShadow`, `groupBackground`, `groupBorder`, `groupShadow`.

### Icons (`bfbeIcons`)
The whole group shows only when `source` is `` or `self` or `rows` or `loop` or `list` and `skin` is not `custom`.
- `iconPlay` (icon) **Play**. With YouTube and Use our bar, this group styles that bar's buttons with the same settings, and under Icons takes your own Play icon. Pause, Sound on, Sound off, Fullscreen and Exit fullscreen work the same way.
- `iconPause` (icon) **Pause**
- `iconCc` (icon) **Subtitles**: only when `source` is `` or `self` and `subtitles` is set
- `iconChapters` (icon) **Chapter menu**: only when `source` is `` or `self` and `chapters` is set and `chapterMenu` is set
- `iconSettings` (icon) **Settings menu**: only when `menu` is set. Tick it to add a menu for speed, subtitles and, on a stream, its quality and audio tracks. Where the browser plays a stream itself, as Safari and iPhones do, quality and audio tracks are left out. It works with the arrow keys.
- `iconLoop` (icon) **A-B loop**: only when `abLoop` is set. Tick it to add a button that loops a stretch. Press it where the stretch starts, again where it ends, and a third time to stop.
- `iconShare` (icon) **Copy link**: only when `share` is set. Tick it to add a button that copies a link to this page. The link starts the video at the moment playing.
- `iconPip` (icon) **Picture in picture**: only when `pip` is set. Tick it to add a button that plays the video in a small floating window. Firefox does not let a page open one, so there the button does nothing.
- `iconBack` (icon) **Back**: only when `skip` is set. Under Skip buttons, your own icon for skipping back. Forward is the one for skipping forward.
- `iconForward` (icon) **Forward**: only when `skip` is set
- `iconPrev` (icon) **Previous**: only when `source` is `rows` or `loop` or `list` and `playlistSkip` is set. Under Previous and next, your own icon for the previous video. Next is the one for the next video.
- `iconNext` (icon) **Next**: only when `source` is `rows` or `loop` or `list` and `playlistSkip` is set
- `iconSound` (icon) **On**: only when `bar` is `` or `full`. Under Sound, your own icon for the sound button. Off is the one shown while the sound is off.
- `iconMuted` (icon) **Off**: only when `bar` is `` or `full`
- `iconFull` (icon) **Enter**: only when `bar` is not `bare`. Under Fullscreen, your own icon for going fullscreen. Exit is the one shown while fullscreen.
- `iconExit` (icon) **Exit**: only when `bar` is not `bare`

### Buttons (`bfbeBridgeButtons`)
The whole group shows only when `source` is `youtube` and `bridge` is set.
- `bridgeIconPlay` (icon) **Play**. With YouTube and Use our bar, this group styles that bar's buttons with the same settings, and under Icons takes your own Play icon. Pause, Sound on, Sound off, Fullscreen and Exit fullscreen work the same way.
- `bridgeIconPause` (icon) **Pause**
- `bridgeIconSound` (icon) **Sound on**
- `bridgeIconMuted` (icon) **Sound off**
- `bridgeIconFull` (icon) **Fullscreen**
- `bridgeIconExit` (icon) **Exit fullscreen**
Styling, in the schema file: `bridgeIconColor`, `bridgeIconHoverColor`, `bridgeBtnBackground`, `bridgeBtnHoverBackground`, `bridgeBtnSize`, `bridgeBtnBorder`, `bridgeBtnShadow`.

### Motion (`bfbeMotion`)
- `easing` (select) **Easing**: options: `cubic-bezier(0.45, 0.05, 0.55, 0.95)` Soft, `cubic-bezier(0.65, 0, 0.35, 1)` Medium, `cubic-bezier(0.16, 1, 0.3, 1)` Snappy (default), `ease-in` Ease in, `ease-out` Ease out, `ease-in-out` Ease in and out, `linear` Linear, `cubic-bezier(0.34, 1.56, 0.64, 1)` Overshoot, `linear(0, .38 8%, .78 17%, 1.02 25%, 1.08 30%, 1.03 40%, .99 50%, 1)` Soft spring, `var(--bfbe-ease-custom, ease)` Custom; writes CSS. Snappy by default. Pick another curve from the list, or Custom to type your own in Custom curve.
Styling, in the schema file: `duration`, `easingCustom`.

## What it guarantees for accessibility (do not undo)
- A player for a video file is a focusable group named by its Title, so its keys work while focus is on or inside it.
- Space or k plays and pauses, and j and l skip back and forward by Skip by (seconds).
- The left and right arrows move 5 seconds, and the up and down arrows change the volume.
- M mutes, F enters fullscreen, C toggles subtitles and P opens picture in picture, except in Firefox.
- Home and End jump to the ends, and the digits 0 to 9 jump to that tenth of the video.
- Buttons carry names such as Play, Pause, Play again and Fullscreen, mute and subtitles report aria-pressed, and a polite live region announces Playing and Paused.
- The seek line is a range input named Seek with the time as its value text, and the volume slider reports its percentage the same way.
- A YouTube, Vimeo or other-host video shows a button named Play followed by its Title, or by the provider's name without one. With scripts on, their player frame is built on a press, so nothing of it loads before then. Until then the page shows your Poster, or, for YouTube and Vimeo without Privacy, the provider's own thumbnail image when none is set.
- The Settings menu opens with aria-expanded, moves with the arrow keys, Home and End, and Escape closes it and returns focus to its button.
- Bar transitions run on the shared motion duration, which reduced motion sets to zero, and the playlist's playing marker stands still; reduced motion also stops the loading ring.
- Autoplay, muted, waits for a press when the visitor has asked for reduced motion.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
