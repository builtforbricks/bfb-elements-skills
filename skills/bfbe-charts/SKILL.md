---
name: bfbe-charts
description: "Use when adding or styling a chart, graph, stat card, gauge, progress list, treemap or activity calendar with BFB Dynamic Charts (`bfbe-charts`), from typed rows, a CSV file, an ACF repeater or a query loop counted per day. Read before writing its settings."
---

# BFB Dynamic Charts (`bfbe-charts`)

<!-- bfbe:generated:start -->
<!-- Written by dev/skills-export.php in the plugin repository from the installed plugins. Edit the plugin or the website's words, not this block. -->
**Requires** BFB Elements Pro 1.0.0-beta.3 or later, the element turned on (WordPress menu BFB Elements, Elements). Bricks 2.4 or later connects an agent to the site (MCP).
**Schema**: `../bfbe-schemas/references/elements/bfbe-charts.json` (every control, as the builder registers it). Read it before writing settings; this file names the ones that decide the build.
**Documentation**: https://builtforbricks.com/bfb-elements/docs/charts/

## What it is
Fourteen chart types, from bars, lines and donuts to a gauge, progress rows, a treemap and a dot calendar. Data comes from typed rows, a CSV file on this site, an ACF repeater, or a query loop's results counted per day. Every type also carries its figures as a real table, which Show data reveals.

**Not for:** It draws the figures present when the page is built, and fetches no new figures while the page is open. A live feed, a realtime dashboard, or a count over more than one page of query results needs a different approach.

**Costs a page:** CSS 1.74 KB, JS 5.15 KB (gzipped), plus Chart.js 4 (UMD), loaded only on pages that use it. Only where used, the average line, tracks, gradients and their direction, glow, ranges, the breakdown hover and Fill the card: JS 1.97 KB. Only where used, the donut and the gauge: JS 1.36 KB. Only where used, the lollipop, diverging bars and the radar: JS 1.75 KB. Only where used, highlight, projections and patterns: JS 2.55 KB. Only where used, names at the line ends, the guide line and bands: JS 2.19 KB. Only where used, progress rows: CSS 0.56 KB. Only where used, the treemap: CSS 0.65 KB. Only where used, the dot calendar: CSS 0.69 KB. Only where used, the versus bar: CSS 0.46 KB.

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
- `versusFigure` (select) **Figure**: options: `percent` Percentage, `value` Value, `both` Both (default). The bar is shared by the top two or three rows of your data. Show each part's Percentage, Value or Both, the default.
- `versusWord` (text) **Middle word**: dynamic data accepted. Type a word to show between two parts, such as VS. It takes dynamic data.
Styling, in the schema file: `versusNameTypography`, `versusShareTypography`, `versusValueTypography`, `versusWordTypography`, `versusWordBorder`, `versusHeight`, `versusGap`, `versusBorder`.

### Treemap (`bfbeTree`)
The whole group shows only when `type` is `treemap`.
- `treeFigure` (select) **Figure**: options: `percent` Percentage (default), `value` Value, `both` Both. Each row above zero is a tile as big as its share. Show its Percentage (the default), Value or Both.
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
- `averageLabel` (text) **Label**: placeholder Avg; dynamic data accepted; only when `average` is set and `type` is `` or `bar` or `hbar` or `lollipop` or `line` or `area`
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
- `centreText` (text) **Text**: dynamic data accepted; only when `centre` is `custom`. With Own text, type the words for the middle. It takes dynamic data.
- `centreLabel` (text) **Small label**: placeholder Total; dynamic data accepted; only when `centre` is not `` or `none`. Type the small label with the middle text, Total unless set. It takes dynamic data.
- `centreSize` (number) **Text size (px)**: only when `centre` is not `` or `none`
- `centreColor` (color) **Text colour**: only when `centre` is not `` or `none`
- `gaugeStyle` (select) **Style**: options: `arc` Arc (default), `needle` Needle; only when `type` is `gauge`. Draw a Gauge as an Arc (the default), rounded at both ends, with its Arc width (%) and Track colour, or as a Needle, which can show Tick marks.
- `gaugeOf` (select) **Out of**: options: `number` A number (default), `column` The next column; only when `type` is `gauge`. A Gauge is out of A number (the default), set in Maximum, 100 unless set, or The next column, which reads its maximum from the top row.
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
- `guideRestLabel` (text) **Label**: dynamic data accepted; only when `tooltip` is `guide` or `guideLine` and `type` is `` or `bar` or `lollipop` or `diverging` or `line` or `area` or `spark` and `guideRest` is `label`
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
- `tableLabel` (text) **Label**: placeholder Show data; only when `showTable` is not set. Type the words on the button that reveals the table, Show data unless set. It is offered while the table is hidden.
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

## Rendered DOM

One root `div` for every type. The ten canvas types (`bar` to `gauge`) draw on a `<canvas>`; the four HTML types draw markup and load no script. A canvas type on the frontend, square brackets marking parts that need their setting:

```html
<div id="brxe-..." class="brxe-bfbe-charts bfbe-chart bfbe-chart--line [bfbe-chart--minimal] [bfbe-chart--fill] [bfbe-chart--beside]"
     data-bfbe-chart="{the drawing config as JSON}" [data-bfbe-parts="round extras"] [data-bfbe-beside="640"]>
  [<p class="bfbe-chart__title" id="bfbe-UID-title">Jobs</p>]
  [<div class="bfbe-chart__head">[<span class="bfbe-chart__label">This month</span>]<span class="bfbe-chart__value">583</span>
    [<span class="bfbe-chart__delta is-up"><span class="bfbe-chart__delta-n">+11.9%</span> on last month</span>]</div>]
  [<div class="bfbe-chart__ranges" role="group" aria-label="Range">
    <button type="button" class="bfbe-chart__range" data-bfbe-n="3" aria-pressed="true">Last 3</button></div>]
  <div class="bfbe-chart__body">
    <div class="bfbe-chart__stage">
      <canvas class="bfbe-chart__canvas" role="img" aria-label="Jobs" aria-describedby="bfbe-UID-table"></canvas>
      <i class="bfbe-chart__edge bfbe-chart__edge--tip" aria-hidden="true"></i></div>
    [<ul class="bfbe-chart__breakdown"><li class="bfbe-chart__part" data-bfbe-i="0"><span class="bfbe-chart__swatch"></span>
      <span class="bfbe-chart__part-name"></span><span class="bfbe-chart__part-pct"></span><span class="bfbe-chart__part-value"></span></li></ul>]
  </div>
  <button type="button" class="bfbe-chart__toggle bfbe-chip" aria-expanded="false" aria-controls="bfbe-UID-table">Show data</button>
  <div class="bfbe-chart__table-wrap bfbe-sr" id="bfbe-UID-table">
    <table class="bfbe-chart__table">[<caption>Jobs</caption>]<tr class="bfbe-chart__tr">...</tr><tr class="bfbe-chart__tr bfbe-chart__tr--alt">...</tr></table>
    [<ul class="bfbe-chart__notes"><li class="bfbe-chart__note">Highlighted: Fri, 8.60h</li></ul>]</div>
</div>
```

- `data-bfbe-chart` is the whole drawing config, built in PHP from the settings; keys a type ignores are not written. `data-bfbe-parts` names the feature files the chart waits for before it draws.
- States: **Show data** toggles `bfbe-sr` on `.bfbe-chart__table-wrap` and `aria-expanded` on its button. A range pill sets `aria-pressed` and redraws the chart and the headline. The delta takes `is-up` or `is-down`.
- With **Show below the chart** (`showTable`) there is no button, no `bfbe-sr` and no `aria-describedby`. With **Fill the card** (`fillCard`) the button moves above `.bfbe-chart__body`.
- The `<i class="bfbe-chart__edge">` marks are invisible; the script reads the drawn boxes' Borders from them. `tooltipBorder` writes `--tip`, `legendPillBorder` `--pill`, `legendCardBorder` `--card`, `averageLabelBorder` `--avg`, `markBorder` `--mark`. **Width (px)** (`barWidth`), `stemWidth` and `dotSize` size `--bar`.
- Root custom properties: `height` writes `--bfbe-chart-h` (320px, a sparkline 64px), `chartAlign` `--bfbe-chart-align`, `breakdownAlign` `--bfbe-chart-list-align`, `breakdownWidth` `--bfbe-chart-breakdown-w`, `deltaUp` and `deltaDown` `--bfbe-chart-up` and `--bfbe-chart-down`, `tableLine` `--bfbe-chart-line`.
- The HTML types carry no `data-bfbe-chart`; their markup sits in `.bfbe-chart__stage.bfbe-chart__stage--fit`:
  - `progress`: `ul.bfbe-chart__progress > li.bfbe-chart__item`, holding `[.bfbe-chart__item-icon]`, `.bfbe-chart__item-words` (`__item-name`, `[__item-sub]`), `.bfbe-chart__item-track > .bfbe-chart__item-fill` and `.bfbe-chart__item-value`.
  - `versus`: `.bfbe-chart__versus` holding `ul.bfbe-chart__vs-figures` (`li.bfbe-chart__vs-part`, `[li.bfbe-chart__vs-word]`) and `.bfbe-chart__vs-bar > i.bfbe-chart__vs-seg`.
  - `treemap`: `ul.bfbe-chart__tiles > li.bfbe-chart__tile > .bfbe-chart__tile-box` (`__tile-name`, `__tile-value`, `[__tile-change]`), largest tile first.
  - `calendar`: `.bfbe-chart__calendar > table.bfbe-chart__cal`, each day an `i.bfbe-chart__dot` with `--l1` to `--l6`, `--plan`, `--ahead` or `--today`, then `[p.bfbe-chart__key]`.
  - Their table sits in `details.bfbe-chart__more`, whose `summary.bfbe-chart__toggle` is the Show data chip. A row's colour arrives as `--bfbe-chart-c`, a bar's share as `--bfbe-v`.
- The root is an inline-size container. The breakdown's **Beside above** (`besideAbove`), the progress rows' stacking under 480px and the treemap's squarer layout under 520px follow the element's width, not the screen's.
- In the builder canvas the table tags are divs carrying `.bfbe-chart__row`, `.bfbe-chart__cell` and `.bfbe-chart__caption`.

What each type reads, and the groups it adds to Chart, Data, Colours and Data table. Inside a group each control has its own type list, given in the block above.

| `type` | Reads from the rows | Groups added |
|---|---|---|
| `bar` (or unset), `hbar`, `lollipop`, `diverging`, `line`, `area` | the label column, then one series per column | Headline, Ranges, Axes and legend, Highlight and marks, Tooltip, Motion |
| `spark` | as above, drawn with no axes and its last point marked | the same, with no Legend, and Projected alone under Highlight and marks |
| `radar` | three rows or more, a shape per series | Headline, Axes and legend, Tooltip, Motion |
| `donut` | a slice per row; the middle and the breakdown read the first series | Headline, Axes and legend, Donut and gauge, Tooltip, Motion |
| `gauge` | the first series' first row, out of `gaugeMax` or the second series' first row | Donut and gauge, Motion |
| `progress` | a bar per row of the first series; text columns for sub-label and icon | Progress rows, Headline |
| `versus` | the first three rows of the first series | Versus bar, Headline |
| `treemap` | the first series' rows above zero; a text column for the change | Treemap, Headline |
| `calendar` | the label column as dates, one day's rows added up | Dot calendar, Headline |

Files, as the element decides per chart (the builder loads them all):
- Every chart: `charts.min.css`. An HTML type adds `charts-progress`, `-versus`, `-treemap` or `-calendar.min.css`, and no script.
- Every canvas type: Chart.js 4.4.7 (`vendor/chart.umd.min.js`) and `charts.min.js`.
- `charts-types.min.js` for `lollipop`, `diverging` and `radar`; `charts-round.min.js` for `donut` and `gauge`.
- `charts-extras.min.js`: `average`, `tracks`, a `gradient` (not on a gauge), `ranges` with a label, `legend: "list"`, `fillCard`, `glow`.
- `charts-marks.min.js`: a `highlight` (`label` with a `highlightLabel` that resolves), `projectedFrom`, a series `fill` of `hatched` or `dotted`.
- `charts-guide.min.js`: `legend: "end"` on a line or an area, `tooltip: "guide"` or `"guideLine"`, `bands`.
- Each of these loads where the chart's type draws the feature, never for a value its type ignores.

## Wiring to other elements

Nothing points at a chart by attribute, and it points at nothing. What it listens to:

- **A query loop, two ways.** With **Data comes from** (`source`) at `loop`, Bricks' **Use query loop** (`hasLoop`) and its `query` feed one chart, counted per day. With any other source, the same switch repeats the chart once per result, and dynamic tags in `rows` read each result.
- **BFB Dark Mode Toggle** (`bfbe-dark-mode`, skill `bfbe-dark-mode`): its `bfbe/theme` event redraws every canvas chart, as does an operating system colour-scheme change. Under its dark state, treemap tile words are worked out from each tile's fill.
- **Theme colours.** A colour control holding `var(--name)` is resolved against the chart's root on every draw, so the canvas follows the theme's value.
- **Bricks AJAX.** Charts set up again on `bricks/ajax/pagination/completed`, `bricks/ajax/load_page/completed`, `bricks/ajax/query_result/displayed` and `bricks/ajax/popup/loaded`. A script that inserts a chart another way calls `window.bfbeCharts()`.
- **Styling from a stylesheet.** Add a class in `_cssClasses` and scope parts under it (`.sales-chart .bfbe-chart__value`). Never `_cssId`: component instances share it, and in a query loop it becomes a class.

## Verified patterns

A stat card: a line with the last value above it and its change on the month before. From the demo page `demo-bfb-charts`, unchanged. `headline: "last"` prints 583, `delta` compares it with 521, and `legend: "none"` because the title names the one series.

```json
{"name": "bfbe-charts", "settings": {
  "type": "line", "title": "Jobs completed",
  "headline": "last", "headlineLabel": "This month", "delta": true, "deltaLabel": "on last month",
  "legend": "none", "grid": true, "gridColor": {"hex": "#e9ecf1"}, "zero": true,
  "colors": [{"color": {"hex": "#6e44ff"}}],
  "rows": "Month, Jobs\nApr, 412\nMay, 448\nJun, 470\nJul, 505\nAug, 521\nSep, 583"
}}
```

Progress rows with a sub-label and an icon from text columns. From the fixture `fixture-charts-html` (`ch-progress`), its probe class and button alignment removed. `progressSub` and `progressIcon` name columns by heading, so they leave the series. With **Full at** (`progressMax`) at 200, Summer house's 240 fills its bar and reads 120%. The fixture's Bathroom icon cell held an attachment ID (a number there draws that image); it is letters here.

```json
{"name": "bfbe-charts", "settings": {
  "type": "progress", "title": "Jobs in progress",
  "rows": "Job, Done, Town, Code\nKitchen refit, 170, Harlow, KR\nBathroom, 132, Epping, BA\nLoft conversion, 104, Ware, LC\nRear extension, 74, Hertford, RE\nGarage roof, 44, Stansted, GR\nSummer house, 240, Hatfield, SH",
  "progressMax": 200, "progressFigure": "both", "progressSub": "Town", "progressIcon": "Code",
  "headline": "avg", "headlineLabel": "Average done"
}}
```

An activity calendar counting posts per publish day. From the fixture `fixture-charts-html` (`ch-cal-loop`), its category filter, five-week window, placement and dot corners removed. `posts_per_page: -1` counts every post, and `calEnd: "last"` ends the window on the latest one.

```json
{"name": "bfbe-charts", "settings": {
  "type": "calendar", "source": "loop", "calEnd": "last", "calStart": "mon",
  "hasLoop": true,
  "query": {"post_type": ["post"], "posts_per_page": -1, "orderby": "date", "order": "ASC"}
}}
```

## Gotchas

- **Typed rows are CSV.** **Rows** (`rows`) splits a line at every comma, so `Jan, £6,440` reads 6. Quote the cell (`"£6,440"`); inside a cell a comma is a thousands separator, so `"1,5"` reads 15. <!-- src: plugins/bfb-elements-pro/elements/charts.php:3148-3164,3207-3210,3259-3268 -->
- **The first column is the label, the rest are series.** The first row names the series. **Sub-label column**, **Icon column** and **Change column** take a heading or a column number from 2, and that column leaves the series. <!-- src: plugins/bfb-elements-pro/elements/charts.php:3212-3250 -->
- **Unread data renders nothing.** Without a header row and a data row the page gets no markup; the canvas asks for rows. **CSV address** (`csvUrl`) wins over **CSV file** (`file`), is read from disk, and outside this site's uploads draws nothing. <!-- src: plugins/bfb-elements/includes/abstract-element.php:538-546; plugins/bfb-elements-pro/elements/charts.php:3118-3143,3195-3206,3306-3318 -->
- **A counted query loop reads its first page.** With `source: "loop"` and `hasLoop` off the page draws nothing; with it on, set the query to show every result. Terms and users need **Date from** (`loopDate`); WooCommerce orders in their own tables (HPOS) are not posts. <!-- src: plugins/bfb-elements-pro/elements/charts.php:241-308,3280-3289; docs/elements/charts.md "A query loop (C11)" -->
- **Labels must match a row exactly.** **Highlight label**, Projected's **From**, a band's **From** and **To**, and the guide's rest **Label** match a row label as typed, case included. A miss draws nothing, and the builder alone says why, as for a radar under three rows or unreadable calendar dates. <!-- src: plugins/bfb-elements-pro/elements/charts.php:3468-3470,3494-3504,3526-3529,3562-3564,4178-4181; plugins/bfb-elements/includes/abstract-element.php:659-665 -->
- **A value the panel hides is dropped before render.** Each control has its own type list, and the base class strips what the panel would not show. `zero` on bars, `stacked` on a donut or `tracks` on a line do nothing; bars, lollipops and radars always start at zero. <!-- src: plugins/bfb-elements/includes/abstract-element.php:77-90,141-175; plugins/bfb-elements-pro/elements/charts.php:79-84 -->
- **Some options are offered where they draw nothing.** `legend: "end"` names the lines on a line or an area and leaves any other type with no legend. `tooltip: "guideLine"` draws nothing on horizontal bars, a radar or a donut, and `"guide"` there draws the card alone. <!-- src: plugins/bfb-elements-pro/elements/charts.php:3372,3545-3548; docs/elements/charts.md "At the line ends and the guide line (C9)" -->
- **A gauge reads one cell and prints no figure by itself.** It draws the first series' first row against **Maximum** (`gaugeMax`, 100), or the second series' first row with `gaugeOf: "column"`. It has no headline: set **In the middle** (`centre`) to `total` to print the value. <!-- src: src/elements/charts-round/charts-round.js:20-28,43-57; plugins/bfb-elements-pro/elements/charts.php:3339,3355-3364 -->
- **A dot calendar ends this week.** It shows 18 weeks ending on the server's today, so rows older than that are not drawn until `calEnd: "last"`. A page cache holds today until it clears. <!-- src: plugins/bfb-elements-pro/elements/charts.php:3981-3984,4185-4196; docs/elements/charts.md "Treemap and Dot calendar (C8)" -->
- **Treemap colours follow size; a versus bar counts three rows.** The first `colors` item paints the largest tile until **Colours** (`treeOrder`) is `row`, and a colour of yours takes the element's text colour on it. A versus bar draws the first three rows, with **Middle word** (`versusWord`) between exactly two. <!-- src: plugins/bfb-elements-pro/elements/charts.php:4141-4147,4275-4289 -->
- **CSS cannot reach what the canvas paints.** The legend, axis labels, grid, tooltip, average chip and highlight pill are drawn, so use their controls. Unset, axes, legend and grid take the root's text colour, and every drawn word its font family. <!-- src: plugins/bfb-elements-pro/elements/charts.php:3381-3384; src/elements/charts/charts.js:116-127,339 -->
- **Ranges are repeater rows.** Write `ranges` as `[{"label": "Last 3", "rows": 3}]`, `rows: 0` for every row. The old text lines (`Last 3: 3`) still draw on the page and leave the chart blank in the builder canvas. <!-- src: plugins/bfb-elements-pro/elements/charts.php:3069-3089; docs/elements/charts.md "The old lines render on the page and leave the element empty in the builder canvas" -->

## Never do

- Do not put a comma inside a number in `rows` unless the cell is quoted, and never use a decimal comma.
- Do not set `source: "loop"` without `hasLoop: true` and a `query` that shows every result.
- Do not point `csvUrl` at a file outside this site's uploads.
- Do not store `ranges` as text lines.
- Do not set a control outside its type's list, such as `zero` on `bar` or `stacked` on `donut`.
- Do not set `legend: "end"` outside `line` and `area`, or `tooltip: "guideLine"` on `hbar`, `radar` or `donut`.
- Do not style the legend, axis labels or tooltip with CSS; set their controls.
- Do not hide `.bfbe-chart__table-wrap` or the Show data button: the table describes the canvas.
