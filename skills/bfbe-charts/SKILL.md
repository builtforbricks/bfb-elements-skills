---
name: bfbe-charts
description: "Use when placing, wiring or styling BFB Dynamic Charts (`bfbe-charts`): fourteen chart types, from bars, lines and donuts to a gauge, progress rows, a treemap and a dot calendar. Read before writing its settings."
---

# BFB Dynamic Charts (`bfbe-charts`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.2 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-charts.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/charts/

## What it is
Fourteen chart types, from bars, lines and donuts to a gauge, progress rows, a treemap and a dot calendar. Data comes from typed rows, a CSV file on this site, an ACF repeater, or a query loop's results counted per day. Every type also carries its figures as a real table, which Show data reveals.

**Not for:** It draws the figures present when the page is built, and fetches no new figures while the page is open. A live feed, a realtime dashboard, or a count over more than one page of query results needs a different approach.

**Costs a page:** CSS 1.74 KB, JS 5.15 KB (gzipped), plus Chart.js 4 (UMD), loaded only on pages that use it.

**Nestable:** no · **In a query loop:** yes · **Dynamic data:** yes · **Keyboard:** no · **Reduced motion:** yes

## Structure
Not nestable: nothing goes inside it.

## Settings that decide the build
Also on this element, as on every element: Bricks' query loop (`hasLoop`, `query`); Hover Effects (`bfbeHover*`, skill `bfbe-hover-effects`); Advanced Header Scroll (`bfbeHs*`, skill `bfbe-advanced-header-scroll`).

### Chart (`bfbeChart`)
- `type` (select) **Type**: options: `bar` Bars (default), `hbar` Horizontal bars, `lollipop` Lollipop, `diverging` Diverging bars, `line` Line, `area` Area, `radar` Radar, `donut` Donut, `spark` Sparkline, `gauge` Gauge, `progress` Progress rows, `versus` Versus bar, `treemap` Treemap, `calendar` Dot calendar. Pick Bars (the default), Horizontal bars, Lollipop, Diverging bars, Line, Area, Radar, Donut, Sparkline, Gauge, Progress rows, Versus bar, Treemap or Dot calendar. The last four are plain HTML, with no Chart.js.
- `look` (select) **Look**: options: `standard` Standard (default), `minimal` Minimal; only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar`. Standard is the default. Minimal fills in the axis, corner, bar and point settings you leave empty, such as a label axis alone and round bars.
- `title` (text) **Text**: dynamic data accepted. Type the chart's title, shown above it. It takes dynamic data, names the chart for screen readers and captions its data table.
- `fillCard` (checkbox) **Fill the card**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `spark`. Tick it to let the chart reach the element's edges, past its padding, for bars, lines, areas and similar types.
Styling, in the schema file: `height`, `chartAlign`, `titleTypography`, `titleAlign`, `stageBackground`, `stagePadding`, `stageBorder`.

### Data (`bfbeData`)
- `source` (select) **Data comes from**: options: `manual` Text typed here (default), `csv` A CSV file, `acf` An ACF repeater, `loop` A query loop. Choose where the figures come from: Text typed here (the default), A CSV file, An ACF repeater or A query loop, which counts its results per day. All are read when the page is built.
- `rows` (textarea) **Rows**: dynamic data accepted; only when `source` is not `csv` or `acf` or `loop`. Type a header row that names the series. Each row after it is a label followed by its values, separated by commas, as in a CSV.
- `file` (file) **CSV file**: only when `source` is `csv`. Choose a CSV file from this site. A CSV address, when you set one, is read instead.
- `csvUrl` (text) **CSV address**: placeholder /wp-content/uploads/figures.csv; dynamic data accepted; only when `source` is `csv`. Give the address of a file in this site's uploads, or a dynamic tag. An address outside the site draws nothing.
- `acfField` (text) **Repeater field name**: placeholder monthly_figures; only when `source` is `acf`. For An ACF repeater, type the repeater's name.
- `acfLabel` (text) **Label sub field**: placeholder month; only when `source` is `acf`. Type the sub field that names each row, such as month.
- `acfValues` (text) **Value sub fields**: placeholder visits, sales; only when `source` is `acf`. Type the sub fields that hold the figures, with commas between them, such as visits, sales. Each one is a series.
- `loopDate` (text) **Date from**: dynamic data accepted; only when `source` is `loop`. For a query loop, set the date each result counts on, such as a date field's tag. Left blank, it is the publish date. Loops of terms or users need one.
- `loopValue` (text) **Value from**: dynamic data accepted; only when `source` is `loop`. For a query loop, set what each result adds to its day. Left blank, each result counts as one.
- `prefix` (text) **Before each value**: placeholder £. Type text shown before every value, such as £.
- `suffix` (text) **After each value**: placeholder %. Type text shown after every value, such as %.

### Progress rows (`bfbeProgress`)
The whole group shows only when `type` is `progress`.
- `progressOf` (select) **Out of**: options: `number` A number (default), `max` The largest value, `column` The next column. Choose what each row is measured against: A number (the default), The largest value, or The next column of the same row.
- `progressMax` (number) **Full at**: only when `progressOf` is `` or `number`. Set the number that fills a bar, 100 unless set. A bar stops at full while its figure keeps the real share, so 120 of 100 reads 120%.
- `progressFigure` (select) **Figure**: options: `percent` Percentage (default), `value` Value, `both` Both. Show each row's Percentage (the default), Value or Both.
- `progressSub` (text) **Sub-label column**. Name a column, by its heading or number, whose text shows under each row's name.
- `progressIcon` (text) **Icon column**. Name a column, by its heading or number, that holds each row's icon: an image's ID, an image address, or any text.
Styling, in the schema file: `progressGap`, `progressNameTypography`, `progressSubTypography`, `progressFigureTypography`, `progressRowPadding`, `progressRowBorder`, `progressHeight`, `progressTrackBackground`, `progressTrackBorder`, `progressIconSize`, `progressIconTypography`, `progressIconBackground`, `progressIconBorder`.

### Versus bar (`bfbeVersus`)
The whole group shows only when `type` is `versus`.
- `versusFigure` (select) **Figure**: options: `percent` Percentage, `value` Value, `both` Both (default). Show each row's Percentage (the default), Value or Both.
- `versusWord` (text) **Middle word**: dynamic data accepted. Type a word to show between two parts, such as VS. It takes dynamic data.
Styling, in the schema file: `versusNameTypography`, `versusShareTypography`, `versusValueTypography`, `versusWordTypography`, `versusWordBorder`, `versusHeight`, `versusGap`, `versusBorder`.

### Treemap (`bfbeTree`)
The whole group shows only when `type` is `treemap`.
- `treeFigure` (select) **Figure**: options: `percent` Percentage (default), `value` Value, `both` Both. Show each row's Percentage (the default), Value or Both.
- `treeChange` (text) **Change column**. Name a column, by its heading or number, whose text shows on each tile, such as a change.
- `treeOrder` (select) **Colours**: options: `rank` By rank (default), `row` Per row. Color the tiles By rank (the default), from the largest down, or Per row, in your data's order.
Styling, in the schema file: `treeGap`, `treePadding`, `treeBorder`, `treeNameTypography`, `treeFigureTypography`, `treeChangeTypography`, `treeChangeBackground`.

### Dot calendar (`bfbeCal`)
The whole group shows only when `type` is `calendar`.
- `calWeeks` (number) **Weeks shown**. Set how many weeks show, 18 unless set, from 1 to 53. Each column is a week and each row a weekday. Each row of your data is a date, and rows of one day add up.
- `calEnd` (select) **Ends with**: options: `today` This week (default), `last` The latest row. End on This week (the default) or on the week of The latest row.
- `calStart` (select) **Week starts on**: options: `site` As the site (default), `mon` Monday, `sun` Sunday, `sat` Saturday. Choose As the site (the default), Monday, Sunday or Saturday.
- `calLevels` (number) **Levels**. Set how many shades a day's dot can take, 4 unless set, from 2 to 6. A past day's shade is its share of the busiest day shown.
- `calNames` (select) **Names**: options: `days` Days (default), `months` Days and months, `none` None. Show Days (the default), Days and months, or None beside and above the dots.
- `calKey` (checkbox) **Key**. Tick it to add a key under the dots, from Fewer to More, with Planned and Today.
Styling, in the schema file: `calNamesTypography`, `calKeyTypography`, `calSize`, `calGap`, `calBorder`, `calNone`, `calPlan`, `calToday`.

### Headline (`bfbeHead`)
The whole group shows only when `type` is not `gauge`.
- `headline` (select) **Headline**: options: `none` None (default), `last` Last value, `sum` Total, `avg` Average. Show one figure above the chart: None (the default), Last value, Total or Average. It is worked out from the rows when the page is built.
- `headlineSeries` (number) **Series**: only when `headline` is not `` or `none` and `type` is not `progress` or `versus` or `treemap` or `calendar`. Choose which series the headline reads, 1 unless set.
- `headlineLabel` (text) **Label**: dynamic data accepted; only when `headline` is not `` or `none`. Type words to show with the figure. It takes dynamic data.
- `delta` (checkbox) **Show the change**: only when `headline` is not `` or `none` and `type` is not `progress` or `versus` or `treemap`. Tick it to show how the last row changed from the row before it, as a percentage when that row is not zero.
- `deltaLabel` (text) **Change label**: placeholder vs last month; dynamic data accepted; only when `delta` is set and `headline` is not `` or `none` and `type` is not `progress` or `versus` or `treemap`. Type words after the change, such as vs last month. It takes dynamic data.
Styling, in the schema file: `headAlign`, `headlineTypography`, `headlineLabelTypography`, `deltaTypography`, `deltaUp`, `deltaDown`, `headBackground`, `headPadding`, `headBorder`.

### Ranges (`bfbeRanges`)
The whole group shows only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `spark`.
- `ranges` (repeater) **Ranges**. Add one pill per range. Each has a Label and Rows to show, the last so many rows, or all of them unless set. Pressing a pill redraws the chart and its headline.
- `rangeStart` (number) **Range shown first**: only when `ranges` is set. Choose which pill starts pressed, 1 unless set.
Styling, in the schema file: `rangesAlign`, `rangeTypography`, `rangeBackground`, `rangeHoverBackground`, `rangeActiveColor`, `rangeActiveBackground`, `rangeBorder`, `rangePadding`, `rangeGap`, `rangesBackground`, `rangesPadding`, `rangesBorder`.

### Axes and legend (`bfbeAxes`)
The whole group shows only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` or `spark`.
- `legend` (select) **Legend**: options: `top` Top (default), `bottom` Bottom, `left` Left, `right` Right, `list` A breakdown list, `end` At the line ends, `none` None; only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut`. Top is the default. Pick Bottom, Left, Right, A breakdown list, At the line ends or None. The breakdown list shows a swatch, name, share and value. In a legend at an edge, clicking a label switches its series off.
- `legendAlign` (justify-content) **Legend sits**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is `` or `top` or `bottom`
- `legendAlignSide` (justify-content) **Legend sits**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is `left` or `right`
- `endMarker` (select) **End marker**: options: `ring` A ring (default), `dot` A dot, `none` None; only when `legend` is `end` and `type` is `line` or `area`. With the legend At the line ends, on a Line or Area, mark each line's last point with A ring (the default), A dot or None.
- `legendColor` (color) **Colour**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is not `none` or `list` or `end`
- `legendSize` (number) **Text size (px)**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is not `none` or `list` or `end`
- `legendGap` (number) **Gap (px)**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is not `none` or `list` or `end`
- `legendSwatch` (number) **Swatch size (px)**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is not `none` or `list` or `end`
- `legendSwatchGap` (number) **Label swatch spacing**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is not `none` or `list` or `end`
- `legendDim` (number) **Off opacity (%)**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is not `none` or `list` or `end`. Clicking a label switches its series off.
- `legendPillBackground` (color) **Behind each label**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is not `none` or `list` or `end`
- `legendPillPadX` (number) **Label padding X (px)**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is not `none` or `list` or `end`
- `legendPillPadY` (number) **Label padding Y (px)**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is not `none` or `list` or `end`
- `legendCardBackground` (color) **Legend background**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is not `none` or `list` or `end`
- `legendCardPad` (number) **Legend padding (px)**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is not `none` or `list` or `end`
- `breakdownPosition` (select) **Position**: options: `below` Below (default), `beside` Beside; only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` and `legend` is `list`. Under Breakdown, put the list Below the chart (the default) or Beside it.
- `besideAbove` (select) **Beside above**: options: `480` 480 px, `640` 640 px (default), `768` 768 px, `992` 992 px; only when `breakdownPosition` is `beside` and `legend` is `list` and `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut`. With the list Beside, set the width above which it sits beside the chart: 480, 640, 768 or 992 px, 640 px unless set.
- `grid` (checkbox) **Grid lines**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar`. Tick it to draw lines along the value axis, unless Drawn along says otherwise.
- `rings` (select) **Rings**: options: `round` Round (default), `polygon` Polygon; only when `grid` is set and `type` is `radar` and `gridAxes` is not `label`. On a Radar with grid lines, draw the rings Round (the default) or as a Polygon.
- `gridAxes` (select) **Drawn along**: options: `value` The value axis (default), `label` The label axis, `both` Both; only when `grid` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar`. Draw the grid along The value axis (the default), The label axis or Both.
- `gridWidth` (number) **Line width (px)**: only when `grid` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar`
- `gridDash` (select) **Line style**: options: `solid` Solid (default), `dashed` Dashed, `dotted` Dotted; only when `grid` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar`
- `gridColor` (color) **Grid line colour**: only when `grid` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar`
- `zero` (checkbox) **Start at zero**: only when `type` is `line` or `area` or `spark`. Off by default for Line, Area and Sparkline, so tick it to start them at zero. Bars, lollipops and radars always start there, so they do not offer it.
- `stacked` (checkbox) **Stacked**: only when `type` is `` or `bar` or `hbar` or `line` or `area`. Tick it to stack the series, on Bars, Horizontal bars, Line and Area.
- `smooth` (checkbox) **Smooth lines**: only when `type` is `line` or `area` or `spark` or `radar`. Tick it to curve the lines of a Line, Area, Sparkline or Radar.
- `belowSeries` (number) **Below the line**: only when `type` is `diverging`. On Diverging bars, choose the series drawn under the middle line, the second unless set. A single series is drawn centred on the line.
- `axisColor` (color) **Axis label colour**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar`
- `axisSize` (number) **Axis text size (px)**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar`
- `axes` (select) **Axes shown**: options: `both` Both, `value` The value axis only, `label` The label axis only, `none` Neither; only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar`. Show both axes, the default, or just the value axis, just the label axis or neither. The Minimal look shows the label axis alone.
- `axisLineColor` (color) **Axis line colour**: only when `axes` is not `none` and `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area`. The line the labels sit against.
- `axisLineWidth` (number) **Axis line width (px)**: only when `axes` is not `none` and `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area`
- `axisPad` (number) **Label offset (px)**: only when `axes` is not `none` and `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area`
- `rimPad` (number) **Label offset (px)**: only when `type` is `radar` and `axes` is `` or `both` or `label`
- `average` (checkbox) **Show it**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area`. Under Average line, tick it to draw a line at the average value, with a Label that reads Avg unless you change it.
- `averageLabel` (text) **Label**: placeholder Avg; dynamic data accepted; only when `average` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area`. Type words to show with the figure. It takes dynamic data.
- `averageColor` (color) **Colour**: only when `average` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area`
- `averageWidth` (number) **Line width (px)**: only when `average` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area`
- `averageDash` (select) **Line style**: options: `dashed` Dashed (default), `solid` Solid, `dotted` Dotted; only when `average` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area`
- `averageLabelSize` (number) **Label size (px)**: only when `average` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area`
- `averageLabelWeight` (select) **Label weight**: options: `400` Normal, `500` Medium, `600` Semi-bold (default), `700` Bold; only when `average` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area`
- `averageLabelColor` (color) **Label colour**: only when `average` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area`. The line colour, until you set this.
- `averageLabelBackground` (color) **Label background**: only when `average` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area`
- `averageLabelPad` (number) **Label padding (px)**: only when `average` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area`
- `focus` (checkbox) **Dim the others on hover**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `donut`. Tick it to fade the other bars or slices while the pointer is on one, on Bars, Horizontal bars, Lollipop, Diverging bars and Donut.
Styling, in the schema file: `legendPillBorder`, `legendCardBorder`, `breakdownAlign`, `breakdownTypography`, `breakdownPadding`, `swatchSize`, `breakdownWidth`, `breakdownGap`, `breakdownRowGap`, `breakdownBackground`, `breakdownBoxPadding`, `breakdownBorder`, `partBackground`, `partBorder`, `averageLabelBorder`.

### Colours (`bfbeColors`)
- `colors` (repeater) **Series colours**. Add one color per series, in order, or per slice, row or tile where a chart draws one shape per row. Each has Fades to, for a gradient To the second colour, and Fill: Solid, Hatched or Dotted.
- `gradient` (select) **Gradient**: options: `none` None (default), `fade` To transparent, `second` To the second colour; only when `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area` or `spark` or `gauge`. Fill with None (the default), To transparent, or To the second colour, which uses each color's Fades to.
- `gradientRuns` (select) **Gradient runs**: options: `values` With the values (default), `labels` Along the labels; only when `type` is `` or `bar` or `hbar` or `line` or `area` or `spark` and `gradient` is not `` or `none`. With a gradient, run it With the values (the default) or Along the labels.
- `glow` (checkbox) **Glow**: only when `type` is `line` or `area` or `spark`. Tick it to give a Line, Area or Sparkline a glow.
- `compare` (number) **Comparison series**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area` or `spark` or `radar`. Type a series number to draw that series dashed and lighter, as a comparison. 0, the default, is none.
- `radius` (number) **Corner radius (px)**: placeholder Auto; only when `type` is `` or `bar` or `hbar` or `diverging` or `donut` or `gauge`. 6, or round in Minimal and on an arc.
- `tracks` (checkbox) **Tracks**: only when `type` is `` or `bar` or `hbar`. Tick it to draw a track behind every bar, on Bars and Horizontal bars, in the Track colour.
- `trackColor` (color) **Track colour**: only when `tracks` is set and `type` is `` or `bar` or `hbar`
Styling, in the schema file: `barWidth`, `stemWidth`, `dotSize`.

### Highlight and marks (`bfbeMarks`)
The whole group shows only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `spark`.
- `highlight` (select) **Highlight**: options: `none` None (default), `last` The last, `max` The highest, `min` The lowest, `label` A label; only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area`. Make one value stand out: None (the default), The last, The highest, The lowest or A label. It reads the leading series, or the stacked totals, and the data table's notes name it.
- `highlightLabel` (text) **Highlight label**: dynamic data accepted; only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` and `highlight` is `label`. With A label, type the label of the row to highlight. It takes dynamic data.
- `quietColor` (color) **Quiet colour**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` and `highlight` is not `` or `none`. The other bars; the text colour at 60% until set.
- `markSize` (number) **Size (px)**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` and `highlight` is not `` or `none`
- `markWeight` (select) **Weight**: options: `400` Normal, `500` Medium, `600` Semi-bold (default), `700` Bold; only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` and `highlight` is not `` or `none`
- `markColor` (color) **Colour**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` and `highlight` is not `` or `none`. The text colour, until you set this.
- `markBackground` (color) **Background**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` and `highlight` is not `` or `none`
- `markPad` (number) **Padding (px)**: only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` and `highlight` is not `` or `none`
- `projectedFrom` (text) **From**: dynamic data accepted; only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `spark`. Under Projected, type a row's label. That row and every row after it are drawn as projected, and the table and tooltip say so.
- `projectedLook` (select) **Drawn as**: options: `hatched` Hatched (default), `dashed` Dashed, `faded` Faded; only when `type` is `` or `bar` or `hbar` or `diverging` or `area` and `projectedFrom` is set. Draw projected rows Hatched (the default), Dashed or Faded, on Bars, Horizontal bars, Diverging bars and Area.
- `bands` (repeater) **Spans**: only when `type` is `` or `bar` or `lollipop` or `diverging` or `line` or `area`. Under Bands, add one band per span of labels, each with From, To and a Label. The band is shaded behind its span, and its label is said under the data table.
- `bandFill` (select) **Fill**: options: `dotted` Dotted (default), `hatched` Hatched, `tinted` Tinted; only when `type` is `` or `bar` or `lollipop` or `diverging` or `line` or `area` and `bands` is set. Shade the bands Dotted (the default), Hatched or Tinted.
- `bandColor` (color) **Colour**: only when `type` is `` or `bar` or `lollipop` or `diverging` or `line` or `area` and `bands` is set. The text colour at 35%, until you set this.
Styling, in the schema file: `markBorder`.

### Donut and gauge (`bfbeDonut`)
The whole group shows only when `type` is `donut` or `gauge`.
- `centre` (select) **In the middle**: options: `none` Nothing (default), `total` The total, `custom` Own text; only when `type` is `donut` or `gauge`. Show Nothing (the default), The total, or Own text in the middle of a Donut or Gauge, at the Text size (px) and Text colour you set.
- `centreText` (text) **Text**: dynamic data accepted; only when `centre` is `custom`. Type the chart's title, shown above it. It takes dynamic data, names the chart for screen readers and captions its data table.
- `centreLabel` (text) **Small label**: placeholder Total; dynamic data accepted; only when `centre` is not `` or `none`. Type the small label with the middle text, Total unless set. It takes dynamic data.
- `centreSize` (number) **Text size (px)**: only when `centre` is not `` or `none`
- `centreColor` (color) **Text colour**: only when `centre` is not `` or `none`
- `gaugeStyle` (select) **Style**: options: `arc` Arc (default), `needle` Needle; only when `type` is `gauge`. Set where a Donut, Gauge or Dot calendar sits in Chart sits, the title's typography and alignment, and the chart area's background, padding and border.
- `gaugeOf` (select) **Out of**: options: `number` A number (default), `column` The next column; only when `type` is `gauge`. Choose what each row is measured against: A number (the default), The largest value, or The next column of the same row.
- `gaugeMax` (number) **Maximum**: only when `type` is `gauge` and `gaugeOf` is `` or `number`
- `arcWidth` (number) **Arc width (%)**: only when `type` is `gauge` and `gaugeStyle` is not `needle`. Of the radius, from the outside.
- `gaugeTrack` (color) **Track colour**: only when `type` is `gauge`
- `gaugeTicks` (checkbox) **Tick marks**: only when `type` is `gauge` and `gaugeStyle` is `needle`
- `pullOut` (checkbox) **Pull out on hover**: only when `type` is `donut`. Tick it to pull a Donut's slice out while the pointer is on it.

### Tooltip (`bfbeTip`)
The whole group shows only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` or `spark`.
- `tooltip` (select) **Tooltip**: options: `point` One value (default), `index` Every series at that point, `guide` A guide line and the values, `guideLine` A guide line only, `none` None. Show One value (the default), Every series at that point, A guide line and the values, A guide line only, or None. The guide line follows the pointer from column to column.
- `tooltipTotal` (checkbox) **Total row**: only when `tooltip` is `index` or `guide` and `type` is not `donut`. With Every series at that point or A guide line and the values, tick it to add a total to the tooltip. A Donut has no total row.
- `guideRest` (select) **Rests on**: options: `last` The last point (default), `label` A label, `none` Nowhere; only when `tooltip` is `guide` or `guideLine` and `type` is `` or `bar` or `lollipop` or `diverging` or `line` or `area` or `spark`. When the pointer leaves, the guide line rests on The last point (the default), A label you type in Label, or Nowhere.
- `guideRestLabel` (text) **Label**: dynamic data accepted; only when `tooltip` is `guide` or `guideLine` and `type` is `` or `bar` or `lollipop` or `diverging` or `line` or `area` or `spark` and `guideRest` is `label`. Type words to show with the figure. It takes dynamic data.
- `guideColor` (color) **Colour**: only when `tooltip` is `guide` or `guideLine` and `type` is `` or `bar` or `lollipop` or `diverging` or `line` or `area` or `spark`. The axis labels' colour, until you set this.
- `guideWidth` (number) **Line width (px)**: only when `tooltip` is `guide` or `guideLine` and `type` is `` or `bar` or `lollipop` or `diverging` or `line` or `area` or `spark`
- `guideDash` (select) **Line style**: options: `dashed` Dashed (default), `solid` Solid, `dotted` Dotted; only when `tooltip` is `guide` or `guideLine` and `type` is `` or `bar` or `lollipop` or `diverging` or `line` or `area` or `spark`
- `tooltipBackground` (color) **Background**: only when `tooltip` is not `none` or `guideLine`
- `tooltipColor` (color) **Text colour**: only when `tooltip` is not `none` or `guideLine`
- `tooltipSize` (number) **Text size (px)**: only when `tooltip` is not `none` or `guideLine`
- `tooltipPadding` (number) **Padding (px)**: only when `tooltip` is not `none` or `guideLine`
Styling, in the schema file: `tooltipBorder`.

### Data table (`bfbeTable`)
- `showTable` (checkbox) **Show below the chart**. Off by default, the table stays visually hidden behind a Show data button. Tick it to put the table under the chart for everyone.
- `tableLabel` (text) **Label**: placeholder Show data; only when `showTable` is not set. Type words to show with the figure. It takes dynamic data.
Styling, in the schema file: `toggleAlign`, `toggleTypography`, `toggleBackground`, `toggleBorder`, `tableTypography`, `tableLine`, `tableCellPadding`, `tableCaptionTypography`, `tableBackground`, `tablePadding`, `tableBorder`, `tableRowBackground`, `tableAltBackground`, `tableHeadBackground`, `tableRowBorder`.

### Motion (`bfbeMotion`)
The whole group shows only when `type` is `` or `bar` or `hbar` or `lollipop` or `diverging` or `line` or `area` or `radar` or `donut` or `spark` or `gauge`.
- `animate` (checkbox) **Draw animation**. Tick it to make the bars, lines or slices draw in over the Duration when the chart paints.
- `animDuration` (number) **Duration (ms)**: only when `animate` is set. Set how long the draw takes, 1000 unless set. It appears once Draw animation is ticked.
- `animEasing` (select) **Easing**: options: `easeInOutSine` Soft, `easeInOutCubic` Medium, `easeOutExpo` Snappy (default), `easeInQuad` Ease in, `easeOutQuad` Ease out, `easeInOutQuad` Ease in and out, `linear` Linear, `easeOutBack` Overshoot, `easeOutElastic` Soft spring; only when `animate` is set. Choose from nine named curves, Snappy by default. Chart.js takes names, so there is no custom curve here.

## What it guarantees for accessibility (do not undo)
- A canvas chart is an image named by its Text, or Chart, and described by its data table unless Show below the chart is ticked.
- The table is a real table with the Text as its caption when set, scope col on column headings and scope row on row headings.
- Show data is a native button with aria-expanded and aria-controls on canvas charts, and a details summary on the HTML types.
- Range pills are native buttons with aria-pressed, so Enter and Space work, while the tooltip and canvas legend answer the pointer.
- Under reduced motion the draw animation is skipped and the chart appears at once.
<!-- bfbe:generated:end -->

## Wiring to other elements

_Not written yet._

## Verified patterns

_Not written yet._

## Gotchas

_Not written yet._

## Never do

_Not written yet._
