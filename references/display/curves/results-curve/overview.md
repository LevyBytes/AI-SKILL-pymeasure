# pymeasure.display.curves.ResultsCurve

*class *pymeasure.display.curves.ResultsCurve(*results*, *x*, *y*, *force_reload=False*, *wdg=None*, ***kwargs*)

Bases: `PlotDataItem`

Create a curve that loads dynamically from a file through the Results object. Each update can force a full data reload, which is useful when data changes throughout the file rather than only being appended.
