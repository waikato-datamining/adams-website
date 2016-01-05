.. title: weekly roundup 29/5
.. slug: weekly-roundup-295
.. date: 2015-05-29 16:45:57 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

Time to let you in on the latest changes... 

Something that has been in the making for a bit, but was accelerated 
through the bug-hunt for locked files under Windows (a feature I 
always hated!): 

  ADAMS now requires Java 8 for building and running. 

And here is the rest: 

**Fixes** 

* SpreadSheetAggregate is now more robust in 
  regards to failures, also handles empty input 
  spreadsheets now correctly (no longer adds 
  a phantom row) 

**Changes**

* TimeseriesDisplay now offers a "plot updater" option, 
  which allows you to specify at what interval to update 
  the display (or only at the end) 
* StringToValidVariableName conversion now has the 
  additional "pad" option to output a full variable like 
  "@{cool_variable}" instead of "cool_variable" 
* Quote conversion now offers "force" (always quote 
  it, even if not necessary) and "double-up" (double 
  quotes rather than using backslashes for escaping 
  them)  options 
* UnQuote conversion offers the "double-up" option 
  like Quote as well, reversing the doubling up, of 
  course 
* SpreadSheetToDouble/StringMatrix conversions 
  now allow user to specify the range of 
  rows/columns to turn into a matrix 
* data container writers (= transformers) now allow 
  the specification on how to generate the file: 
  AUTOMATIC, DATABASE_ID, ID, SUPPLIED 
  current behavior was AUTOMATIC, which either 
  uses DB-ID or if that is not available the ID of 
  a container. With SUPPLIED you can create 
  your own filename (without path) 
  Affected: TimeseriesFileWriter, HeatmapFileWriter 
* EnterManyValues now has support for displaying 
  a help via a tip text hint (when hovering over the 
  field) and allows the output of a spreadsheet 
  (default so far) and key value pairs 

**Additions** 

* added support for control charts (adams-visualstats) 
  c, u, np, p, Xbar R, Xbar S 
  
  https://en.wikipedia.org/wiki/Control_chart 
  
  http://www.qimacros.com/control-chart-formulas/ 

* added a "System performance" menu item to the 
  ADAMS main menu under "Help" 
  (for checking performance of servers in cloud or local) 

Have a good weekend! 

.. thumbnail:: ../../images/performance.png

.. thumbnail:: ../../images/uchart.png

