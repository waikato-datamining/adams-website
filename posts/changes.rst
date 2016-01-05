.. title: changes
.. slug: changes
.. date: 2015-05-18 12:50:37 UTC+13:00
.. tags: updates
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

As always, there have been a number of changes again. 

**Additions**

* adams-imaging can generate UPC-A barcodes now 
* adams-timeseries now has FixedTimestampPaintlet, 
  FixedTimestampRangePaintlet paintlets and 
  TimeseriesShiftTimestamp filter 

**Changes**

* upgraded Groovy to 2.4.0, to bring it in line with 
  Weka packages 
* prefixed timeseries filters, baseline correction, 
  outlier detectors, smoothers with "Timeseries" 
  to avoid potential name clashes 
* added support for "flow" aware paintlets: 
  TextOverlayPaintlet and MultiPaintlet 
  -> affected: Canvas, SimplePlot, SequencePlot 
* TimedTee/TimedTrigger/TimedSubProcess control 
  actors now forward a TimingContainer object 
  instead of just the milli-second value (contains 
  prefix and original as well) 
* SpreadSheetAggregate/Query transformers now 
  support "RANGE" function, which is just a shortcut 
  for MAX-MIN 

**Fixes**

* "Scripted" feature generators now work with Groovy 
  (Groovy didn't like generics in return value of method) 
* code review for fixing potential locked files on Windows 
  (explicitly closing FileInputStream/FileOutputStream) 

