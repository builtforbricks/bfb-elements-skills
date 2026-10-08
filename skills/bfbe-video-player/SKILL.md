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

**Costs a page:** CSS 2.75 KB, JS 2.99 KB (gzipped), no dependencies, loaded only on pages that use it. Only where used, the provider façade: JS 0.77 KB. Only where used, the menus: CSS 0.99 KB, JS 1.77 KB. Only where used, the Minimal and Studio skins: CSS 0.65 KB. Only where used, the extras: CSS 0.66 KB, JS 2.08 KB. Only where used, the playlist: CSS 1.81 KB, JS 2.83 KB. Only where used, our controls on YouTube: JS 1.53 KB. Only where used, hLS streams: JS 0.81 KB.

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
- `loopUrl` (text) **Video URL**: dynamic data accepted; only when `source` is `loop`. Under For each result, the address of each result's video, usually a dynamic tag.
- `loopTitle` (text) **Title**: dynamic data accepted; only when `source` is `loop`. Under For each result, the title each video shows in the list.
- `loopPoster` (text) **Poster**: dynamic data accepted; only when `source` is `loop`. Under For each result, the address of each video's poster picture.
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
- `iconPlay` (icon) **Play**. Your own icon for the play button. Pause, Subtitles, Chapter menu, Settings menu, A-B loop, Copy link and Picture in picture work the same way, and one left empty keeps the drawn mark.
- `iconPause` (icon) **Pause**
- `iconCc` (icon) **Subtitles**: only when `source` is `` or `self` and `subtitles` is set
- `iconChapters` (icon) **Chapter menu**: only when `source` is `` or `self` and `chapters` is set and `chapterMenu` is set
- `iconSettings` (icon) **Settings menu**: only when `menu` is set
- `iconLoop` (icon) **A-B loop**: only when `abLoop` is set
- `iconShare` (icon) **Copy link**: only when `share` is set
- `iconPip` (icon) **Picture in picture**: only when `pip` is set
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

## Rendered DOM

```html
<div class="brxe-bfbe-video-player bfbe-vp bfbe-vp--cinema bfbe-vp--big is-ready" tabindex="0" role="group" aria-label="{title}"
     style="--bfbe-vp-ratio:16 / 9" data-bfbe-idle="2000" data-bfbe-play="Play" data-bfbe-pause="Pause" ...>
  <div class="bfbe-vp__stage" data-bfbe-unplayable="This browser cannot play this file.">
    <video class="bfbe-vp__video" playsinline preload="metadata" controls poster="..."><source src="..." type="video/mp4"><track kind="subtitles"></video>
    <button class="bfbe-vp__big" data-bfbe-do="toggle" aria-label="Play">...</button>        <!-- unless noBig -->
    <span class="bfbe-vp__wait"></span><span class="bfbe-vp__chip"></span>
    <div class="bfbe-vp__over bfbe-vp__over--paused">...nested elements...</div>       <!-- with children; --{overWhen} -->
    <div class="bfbe-vp__bar bfbe-vp__bar--full" data-bfbe-skips><div class="bfbe-vp__row"> <!-- Cinema, Minimal -->
      <span class="bfbe-vp__group bfbe-vp__group--left">[prev] [back] toggle [fwd] [next] <span class="bfbe-vp__time"></span></span>
      <span class="bfbe-vp__seek">[marks] <input type="range" class="bfbe-vp__range bfbe-vp__range--time"> [preview] <output class="bfbe-vp__hint"></output></span>
      <span class="bfbe-vp__group bfbe-vp__group--right">[speed] [cc] [chapters] [settings] sound [ab] [share] [pip] full</span>
    </div></div>
    <div class="bfbe-vp__next">Up next, title, Play now (n), Stay here</div>          <!-- playlist with playlistNext -->
  </div>
  <!-- Studio: the bar here, after the stage -->
  <span class="bfbe-sr bfbe-vp__live" aria-live="polite"></span>
  <ol class="bfbe-vp__chapters">...</ol>                                               <!-- chapterList -->
  <ol class="bfbe-vp__list"><li class="bfbe-vp__item"><button class="bfbe-vp__item-btn" data-bfbe-kind data-bfbe-src aria-current>...</button></li></ol>
  <script type="application/ld+json">...</script>                                     <!-- schema -->
</div>
```

- Every bar button is `button.bfbe-vp__btn[data-bfbe-do]` (`toggle`, `back`, `fwd`, `prev`, `next`, `mute`, `cc`, `speed`, `menu`, `ab`, `share`, `pip`, `full`). The player's script handles clicks delegated from the root, so a Player Control with the same markup is driven the same way.
- Root classes: `bfbe-vp--{cinema|minimal|studio|custom}`, `bfbe-vp--own` (Custom), `bfbe-vp--big` (unless `noBig`), `bfbe-vp--auto` or `bfbe-vp--contain` (the frame). Attributes follow settings: `data-bfbe-skip`, `data-bfbe-hls`, `data-bfbe-chapters`, `data-bfbe-resume`, `data-bfbe-away`, `data-bfbe-private`.
- Skins: Cinema's bar is the stage's second grid row, on a shade (`barShade`). Minimal's bar is `display: contents`: the line rides the picture's bottom edge and the buttons float as a pill 14px above it. Studio's bar follows the stage, on the page's surface, and never hides. Custom draws none. Minimal and Studio rules load from `video-player-skins.css` when used.
- Provider façade (`youtube`, `vimeo`, `embed`, or a playlist of providers alone): root `bfbe-vp--embed` with `data-bfbe-embed`; the stage holds `img.bfbe-vp__poster`, the layer, `button.bfbe-vp__big[data-bfbe-do="embed"]` named "Play {title}" and a `<noscript>` iframe. A press appends `iframe.bfbe-vp__frame` and adds `is-embedded`. With `bridge`, the root adds `bfbe-vp--bridge bfbe-vp--studio` and `.bfbe-vp__bar--bridge` (play, line, time, sound, fullscreen) follows the stage.
- States on the root: `is-ready` once the script runs (before it, the browser's own controls and none of ours), `is-playing`, `is-started` (first play, kept), `is-ended`, `is-idle` (bar faded), `is-waiting`, `is-muted`, `is-full`, `is-pip`, `is-cc`, `is-unplayable`, `is-embedded`, `is-next` (Up next showing), `has-items` (a `list` player found an item).
- Playlists: root `bfbe-vp--list` plus `bfbe-vp--{right|left|top|below|strip}`, or `bfbe-vp--built` for Playlist Items; side lists add `bfbe-vp--scroll-bar` or `--scroll-fade` and toggle `is-list-above` and `is-list-more`. The current row has `aria-current="true"` and `is-current`, and `is-playing` while it plays.
- Styling targets: `fg` writes `--bfbe-vp-fg` (everything over the picture, white unset, and a Studio bar, the page's colour unset); `accent` the played part and handle; `stageBackground`, `frameBorder` and `shadow` the stage (`frameBorder` the root in Studio); `barBackground` writes `--bfbe-vp-bar-bg`, the large button's fill, Studio's bar, Minimal's pill and Cinema's two clusters unless `groupBackground` is set; `overScrim` paints `.bfbe-vp__stage::after` across the whole picture; `overPadding` pads `.bfbe-vp__over`.
- A Player Control renders `.bfbe-vc.bfbe-vc--{kind}` (plus `bfbe-vc--when-{show}`, and `bfbe-vc--wide` on `seek`) around the part the bar draws: `.bfbe-vp__btn`, `.bfbe-vp__seek`, `.bfbe-vp__time`, `.bfbe-vp__now` (title), `.bfbe-vp__chapter-now`, `img.bfbe-vp__cover`, `a.bfbe-vp__dl`.
- A Playlist Item renders `.bfbe-pi[data-bfbe-kind][data-bfbe-src]` with a visually hidden `button.bfbe-pi__pick` named "Play {title}" ("Play this item" with no `title`), its children, and `.bfbe-pi__bars` with `bars`. It takes `is-current`, `is-playing` and `aria-current`; with no video it is `.bfbe-pi--empty`.

## Wiring to other elements

- **Player Control** (`bfbe-video-control`, schema `../bfbe-schemas/references/elements/bfbe-video-control.json`). Nest it anywhere inside the player, at any depth, for example in a block that makes a row; the player's script drives it with no setting. **Which control** `kind` is one of `play`, `big`, `back`, `forward`, `seek`, `time`, `title`, `chapter`, `volume`, `mute`, `cc`, `settings`, `chapters`, `speed`, `fullscreen`, `pip`, `prev`, `next`, `poster`, `download`, `share`, `ab`. **Show it** `show` (`idle`, `paused`, `playing`, `start`, `after`; empty is always) applies on top of the layer's `overWhen`. **Skip by** `skipBy` on `back` and `forward` overrides the player's `skipBy`; empty follows it. `volumeDir` (`across`, `up`) shapes `volume`.
- A Player Control reads its player: `seek` shows the frame preview when the player has `preview`; `cc`, `chapters`, `chapter`, `poster` and `download` read its subtitles, chapters, poster and file; `title` follows the video playing. It is built for `skin: "custom"` and works in every skin: a `title` control over a Studio player is a common pairing.
- **Playlist Item** (`bfbe-playlist-item`, schema `../bfbe-schemas/references/elements/bfbe-playlist-item.json`). It is not nested in the player, though the schema names the player as parent: place items anywhere on the page and set the player's `source: "list"`. Each item loads into the nearest such player, found by walking up from the item to the first ancestor that holds one, so keep a player and its items under one wrapper. **Which player** `player` names another by HTML id (`second-player` or `#second-player`, the player's or a wrapper's); it is an id lookup with no class form, so it breaks when a component holding the player appears twice on a page. Items set `url` or `file`; `title` and `poster` fall back to the first heading and picture inside the card.
- **Query loop playlist**: `source: "loop"`, then `hasLoop: true` and `query` on the player itself, with `loopUrl`, `loopTitle`, `loopPoster` (a text field: give it a tag that returns an image address) and `loopNote` as dynamic tags read per result. The player renders once; Bricks does not repeat it. Playlist Items take a query loop on themselves or on a container around them.
- **Other players**: starting a player with sound pauses every other player on the page that is playing with sound (`bfbe-vp:play` on `document`); a muted one keeps going.
- **Addresses**: `?v=2` opens a playlist on its second video; Copy link copies the page's address with `?t=` at the current second. Both open ready, not playing.
- **Targeting**: give the player a class in `_cssClasses` (`film-player` in the first pattern) and select `.film-player .bfbe-vp__bar`. Never `_cssId`: component instances share ids. The scripts scan again after Bricks' AJAX pagination, query results and popups; for markup added any other way, call `window.bfbeVideoPlayer()` and, for a playlist, `window.bfbeVideoPlayerPlaylist()`.

## Verified patterns

**A film library: a playlist beside the video, with a bar built from Player Controls.** From the Video Player demo (`demo-bfb-video-player`). Its films and posters are replaced with https://example.com/... addresses and cut to three, its styling, `muted` and three keys the Custom skin hides (`share`, `idle`, `groupBackground`) are left out, `title` and the class are added, and the blocks keep the demo's layout. `skin: "custom"` draws no bar, so the nested controls are the bar; `overWhen: "idle"` fades them while it plays untouched; `playlistNext` offers the next film on an 8 second Up next card. On a real site, choose each `poster` from the media library so it carries that site's own attachment id.

```json
{
  "name": "bfbe-video-player",
  "settings": {
    "_cssClasses": "film-player",
    "source": "rows",
    "title": "Film library",
    "playlistLayout": "right",
    "playlistWidth": "330px",
    "playlistRows": [
      { "title": "The first fitting", "note": "Part one, 2 min", "url": "https://example.com/wp-content/uploads/fitting.mp4", "poster": { "url": "https://example.com/wp-content/uploads/fitting.jpg" } },
      { "title": "Reading the eye", "note": "Part two, 3 min", "url": "https://example.com/wp-content/uploads/eyetest.mp4", "poster": { "url": "https://example.com/wp-content/uploads/eyetest.jpg" } },
      { "title": "Camel and horn", "note": "Part three, 2 min", "url": "https://example.com/wp-content/uploads/horn.mp4", "poster": { "url": "https://example.com/wp-content/uploads/horn.jpg" } }
    ],
    "playlistNext": true,
    "playlistCountdown": 8,
    "skin": "custom",
    "accent": { "hex": "#6e44ff" },
    "preview": true,
    "overWhen": "idle",
    "overScrim": { "raw": "linear-gradient(transparent 36%, rgba(16, 24, 40, 0.52) 64%, rgba(16, 24, 40, 0.6))" }
  },
  "children": [
    {
      "name": "block",
      "settings": { "_width": "100%", "_height": "100%", "_justifyContent": "space-between" },
      "children": [
        { "name": "bfbe-video-control", "settings": { "kind": "title" } },
        {
          "name": "block",
          "settings": { "_display": "grid", "_gridTemplateColumns": "auto auto minmax(0, 1fr) auto", "_alignItems": "center", "_columnGap": "10px", "_width": "100%" },
          "children": [
            { "name": "block", "settings": { "_direction": "row", "_alignItems": "center" }, "children": [
              { "name": "bfbe-video-control", "settings": { "kind": "prev" } },
              { "name": "bfbe-video-control", "settings": { "kind": "play" } },
              { "name": "bfbe-video-control", "settings": { "kind": "next" } }
            ] },
            { "name": "bfbe-video-control", "settings": { "kind": "time" } },
            { "name": "bfbe-video-control", "settings": { "kind": "seek" } },
            { "name": "block", "settings": { "_direction": "row", "_alignItems": "center" }, "children": [
              { "name": "bfbe-video-control", "settings": { "kind": "volume" } },
              { "name": "bfbe-video-control", "settings": { "kind": "fullscreen" } }
            ] }
          ]
        }
      ]
    }
  ]
}
```

**Episodes as cards anywhere on the page.** From the fixture `fixture-playlist-item` (its first player and three of its items), with the files and the picture moved to https://example.com/... addresses; the YouTube address is the fixture's own public video. `source: "list"` makes the player wait for items, and the cards find it as the nearest player under the shared block. Studio puts the bar under the picture, so its Previous and Next stay usable while the YouTube item plays.

```json
{
  "name": "block",
  "children": [
    {
      "name": "bfbe-video-player",
      "settings": { "source": "list", "title": "Episodes", "skin": "studio", "playlistNext": true, "playlistRepeat": true, "playlistSkip": true, "overWhen": "always", "overJustify": "flex-start", "overAlign": "flex-start" },
      "children": [ { "name": "bfbe-video-control", "settings": { "kind": "title" } } ]
    },
    {
      "name": "block",
      "settings": { "_direction": "row", "_columnGap": "16px" },
      "children": [
        { "name": "bfbe-playlist-item", "settings": { "url": "https://example.com/wp-content/uploads/episode-one.mp4", "bars": true }, "children": [
          { "name": "image", "settings": { "image": { "url": "https://example.com/wp-content/uploads/episode-one.jpg" } } },
          { "name": "heading", "settings": { "text": "Episode one", "tag": "h4" } }
        ] },
        { "name": "bfbe-playlist-item", "settings": { "url": "https://example.com/wp-content/uploads/episode-two.mp4", "bars": true }, "children": [
          { "name": "heading", "settings": { "text": "Episode two", "tag": "h4" } }
        ] },
        { "name": "bfbe-playlist-item", "settings": { "url": "https://www.youtube.com/watch?v=aqz-KE-bpKQ" }, "children": [
          { "name": "heading", "settings": { "text": "On YouTube", "tag": "h4" } }
        ] }
      ]
    }
  ]
}
```

**A YouTube film that loads nothing from YouTube before play.** From the fixture `fixture-handback-458`, with a `poster` added at an https://example.com/... address and a plainer `title`. `privacy` holds back YouTube's thumbnail and player until the press, so `poster` is what shows. The heading and button sit over the poster and step aside once their player arrives; the button keeps its own link, and a press anywhere else on the picture opens the player.

```json
{
  "name": "bfbe-video-player",
  "settings": {
    "source": "youtube",
    "providerUrl": "https://www.youtube.com/watch?v=aqz-KE-bpKQ",
    "privacy": true,
    "poster": { "url": "https://example.com/wp-content/uploads/film-poster.jpg" },
    "title": "Workshop film",
    "overJustify": "flex-end",
    "overAlign": "flex-start"
  },
  "children": [
    { "name": "heading", "settings": { "text": "Before you press play", "tag": "h3" } },
    { "name": "button", "settings": { "text": "Book a visit", "style": "primary", "link": { "type": "external", "url": "#book" } } }
  ]
}
```

## Gotchas

- **The Custom skin draws no bar.** With `skin: "custom"` the controls are the Player Controls you nest, the large play button and a click on the picture. The Buttons and Icons groups, `idle`, `share`, `abLoop` and `chapterMenu` are hidden there and dropped; nest the `share`, `ab` and `chapters` Player Controls instead. <!-- src: plugins/bfb-elements-pro/elements/video-player.php:2868; plugins/bfb-elements-pro/elements/video-player.php:212; plugins/bfb-elements-pro/elements/video-player.php:538 -->
- **A Player Control with nothing to work with draws nothing on the page.** `cc` needs the player's `subtitles`, `chapters` and `chapter` need `chapters`, `poster` a poster on a single video, `download` a video file rather than a provider; outside a player every kind draws nothing. The canvas says why. `prev` and `next` render outside a playlist but do nothing. <!-- src: plugins/bfb-elements-pro/elements/video-control.php:552; plugins/bfb-elements-pro/elements/video-control.php:585; plugins/bfb-elements-pro/elements/video-control.php:669 -->
- **Nothing of ours stays over a provider's player.** Once a YouTube, Vimeo or other-host frame is on the stage (`is-embedded`), the layer over the video, nested Player Controls included, and a Cinema or Minimal bar step aside, whatever `overWhen` says. A Studio bar keeps its Previous and Next, being under the picture. <!-- src: src/elements/video-player/video-player.css:190; src/elements/video-player/video-player.css:157; src/elements/video-player-skins/video-player-skins.css:33 -->
- **A façade without a Poster shows only the frame background and the play button.** With `privacy`, YouTube's and Vimeo's thumbnails are not fetched, and Another host never brings a picture of its own. <!-- src: plugins/bfb-elements-pro/elements/video-player.php:2011; plugins/bfb-elements-pro/elements/video-player.php:2035; plugins/bfb-elements-pro/elements/video-player.php:2041; docs/elements/video-player.md "Where the video lives (round 2, 2026-09-21)" -->
- **Autoplay is muted and conditional.** `autoplay` mutes the video and hides `muted`. YouTube and Vimeo still wait for a press, since their player is built on it, then play muted; under reduced motion a file waits too; Another host does not offer it. A muted autoplay loop keeps playing when another player starts. <!-- src: plugins/bfb-elements-pro/elements/video-player.php:403; src/elements/video-player-embed/video-player-embed.js:14; src/elements/video-player-extras/video-player-extras.js:27; src/elements/video-player/video-player.js:182 -->
- **A playlist row is a file unless its URL is YouTube or Vimeo.** Rows, `loopUrl` results and Playlist Items are read from the URL alone, so an other-host address goes to the `<video>` as a file and does not play. Another host works as a single video's `source: "embed"`. <!-- src: plugins/bfb-elements-pro/elements/video-player.php:2192; plugins/bfb-elements-pro/elements/video-player.php:2273 -->
- **HLS is recognised by `.m3u8` in the address.** A stream URL without it is treated as a file. Where the browser cannot open HLS itself, hls.js loads from the plugin when a pointer enters the player or on a click, so `autoplay` does not start a stream there; quality and audio tracks appear in the Settings menu through hls.js alone. <!-- src: plugins/bfb-elements-pro/elements/video-player.php:1703; src/elements/video-player-hls/video-player-hls.js:55; src/elements/video-player-hls/video-player-hls.js:63; docs/elements/video-control.md:69 -->
- **Up next follows files and streams.** `playlistNext` acts when the `<video>` ends; a YouTube or Vimeo row never ends for the player, so the list stops there. `playlistCountdown: 0` plays the next at once, and without `playlistRepeat` the step buttons at either end are disabled. <!-- src: src/elements/video-player-playlist/video-player-playlist.js:245; src/elements/video-player-playlist/video-player-playlist.js:199; src/elements/video-player-playlist/video-player-playlist.js:114 -->
- **Visibility has two traps.** Studio sets no idle delay, so `overWhen: "idle"` and a Player Control's `show: "idle"` never hide there. `overWhen: "after"` hides the whole layer `overAfter` seconds into playback, nested Player Controls included, until a pause; for a Custom bar use `idle`. <!-- src: plugins/bfb-elements-pro/elements/video-player.php:2699; src/elements/video-player/video-player.js:104; src/elements/video-player/video-player.css:196; docs/elements/video-player.md "Alex's review, round one (round 366, 2026-09-21)" -->
- **In Minimal the layer reaches the foot of the picture.** Minimal collapses the bar's row, so content placed at the bottom of the layer sits on its line and pill; in Cinema the layer stops above the bar. Justify the content to the top or give the layer `overPadding`. <!-- src: src/elements/video-player-skins/video-player-skins.css:11; src/elements/video-player-skins/video-player-skins.css:22; src/elements/video-player/video-player.css:169 -->
- **A side list stacks under the video below 700px.** On screens narrower than that, `playlistLayout: "right"` or `"left"` puts the list under the picture, capped at 42% of the screen's height, and `playlistWidth` stops applying. <!-- src: src/elements/video-player-playlist/video-player-playlist.css:29 -->
- **The canvas is not the page.** The Up next card never appears in the builder; a click on a Playlist Item there selects it rather than loading it; a `list` player shows "Place BFB Playlist Items on this page." until an item exists; a Player Control with `show` set is drawn faded rather than hidden. <!-- src: src/elements/video-player-playlist/video-player-playlist.js:245; src/elements/video-player-playlist/video-player-playlist.js:293; plugins/bfb-elements-pro/elements/video-player.php:2864; src/elements/video-control/video-control.css:63 -->

## Never do

- Do not set `skin: "custom"` without nesting Player Controls for at least `play` and `seek`.
- Do not set `share`, `abLoop`, `chapterMenu` or `idle` with `skin: "custom"`; nest the `share`, `ab` and `chapters` Player Controls.
- Do not set `privacy`, or use `source: "embed"`, without a `poster`.
- Do not put an other-host address in `playlistRows`, `loopUrl` or a Playlist Item; use it as `source: "embed"`.
- Do not place a Player Control outside a player, and do not give a Playlist Item a player that is not `source: "list"`.
- Do not use `overWhen: "after"` over a bar built from Player Controls, or count on `idle` hiding anything in Studio.
- Do not expect YouTube or Vimeo rows to advance with `playlistNext`; a list that plays through holds files or streams.
- Do not name a player in `player` when it sits in a component used twice; keep the player and its items under one wrapper.
