.. title: time for an update
.. slug: time-for-an-update
.. date: 2015-11-05 10:03:56 UTC+13:00
.. tags: updates, date/time, UI
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

I'm running out of space on my piece of paper here, so I think it's time for an
update. ;-)

**Fixes**

* fixed some regressions in the flow editor due to changes relating to better
  Swing thread queuing

  * when copy/pasting actor with variable, variable disappeared
  * creating a callable actor didn't no update the tree immediately

* the showProperties option of the ImageViewer sink now works inside the
  DisplayPanelManager as well

**Changes**

* added the DATETIMEMSEC type to the DateTimeType enum
* added DATETIMEMSEC support to the following conversions

  * ConvertDateTimeType
  * DateTimeTypeToString
  * ExtractDateTimeField
  * StringToDateTimeType

* added DATETIMEMSEC support to the following actors

  * DateTimeTypeDifference
  * SpreadSheetConvertCells
  * SpreadSheetConvertHeaderCells

* Flow editor: long files now get shortened for the tab; hovering over
  the tab reveals the full name
* Cast control actor no longer throws a cast exception when using Unknown
* data containers now list Notes and Reports in the debug inspection as well
* adams-spreadsheet: SpreadSheetSetCell and SpreadSheetGetCell now support Row
  objects as well apart from SpreadSheet ones
* adams-heatmap: the report table in the HeatmapDisplay can be hidden now
* native ADAMS file choosers now offer a Filter text field which allows the
  display of files/dirs to be restricted to the ones that contain this
  substring (case-sensitive) - useful when looking for a single file or group of
  files in directories with 1000s of files
* adams-weka: the WekaModelReader now has an option makeThreadSafe which
  attempts to make the loaded classifier thread-safe, if necessary (using the
  ThreadSafeClassifierWrapper mentioned below)

**Additions**

* adams-heatmap: added the CountValues meta-generator
* adams-heatmap: added TextOverlay for HeatmapDisplay sink
* adams-core: added support for named counters, i.e., counters that count how
  often a string passes through

  * CounterInit (standalone/transformer) - initializes/resets a named counter
    in internal storage
  * CounterAdd (transformer) - increments the counter for the string
    representation of the token passing through
  * Counter (source) - outputs the names with their associated counts as spreadsheet

* adams-weka: added an interface ThreadSafeClassifier that indicates that a
  classifier is thread-safe (Weka classifiers/filters aren't by design) and a
  generic ThreadSafeClassifierWrapper meta-classifier that attempts to make the
  wrapped classifier safer (there are no guarantees, though; if the code is bad
  by design, this won't help either)

Just a heads-up... There will be a new release coming up in the next couple of
weeks (as part of my preparations for a data mining workshop end of
November).
