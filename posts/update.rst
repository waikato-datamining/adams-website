.. title: update
.. slug: update
.. date: 2015-02-20 17:08:27 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete


Quite a number of changes have made their way into ADAMS since the last post... 

**Libaries**

* MEKA upgraded to 1.7.5 (module: adams-meka) 
* WekaExcel upgraded to 1.0.5 (module: adams-weka) 
  ExcelLoader always omitted last row in spreadsheets 

**Fixes**

* Weka Explorer plugins FixedClassifierErrorPlot, ThresholdCurve now 
  free up memory when the dialog gets closed 
* SpreadSheetColumnRange/Index sometimes failed in conjunction with variables 
* WhileLoop control actor did not re-apply variables once the looping 
  started, ie conditions couldn't use variables that got updated within 
  the loop 

**Extensions**

* the adams-heatmap module received a fair number of changes: 

  * heatmaps no longer have the restriction of having a minimum of 0 
  * heatmap filters are now prefixed with "Heatmap" to avoid name clashes 
  * HeatmapInfo transformer for outputting some info about a heatmap 
  * added number of feature generators 
  * removed instance generators (and adams-weka dependency) 

* Weka filter "Scale" (unsupervised/instance) allows you to scale the 
  values of a row eg to interval 0 to 1 
* any spreadsheet table should now allow you to not only display a 
  histogram of a row/column, but also simply plot the row/column values 
* math/boolean expressions now offer additional functions: 
  cbrt (cube root), sinh, cosh, tanh, atan, atan2, hypot, log10, signum 
* SimplePlot sink - a simplified version of the SequencePlotter sink 

That's it for now. Have a nice weekend! 
