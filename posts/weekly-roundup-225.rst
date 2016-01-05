.. title: weekly roundup 22/5
.. slug: weekly-roundup-225
.. date: 2015-05-22 17:05:01 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

Time flies by and so do the updates... 

**Additions**

* adams-timeseries: new TimeseriesAutocorrelation filter 
* added array statistic: ArrayLinearRegression 
  computes slope/intercept 
* adams-weka now has a simple wizard for 
  batch-filtering datasets 
* added overlays: LinearRegressionOverlay and 
  LOWESSOverlay 

**Fixes**

* further fixes regarding locked files under Windows, 
  reworked the text file readers in the process 
  (used by the TextFileReader transformer) 

**Changes**

* Weka/MOA/Meka/Classifying/Clustering transformers 
  now have a variable for monitoring purposes. Whenever 
  this variable changes, the model gets reset and needs 
  to be loaded again. Useful when using multiple models. 
* upgraded JSch library to 0.1.52 
  (used for ssh, scp, ...) 
* System property "adams.io.tmpdir" allows overriding 
  of Java's default temp directory 
* added support for intercept/slope formulas in spreadsheets 
* the SimplePlot sink now allows to specify an overlay as well 
* adams-weka: the FixedClassifierErrorsPlot plugin for the 
  Weka Explorer now allows the specifying of the meta-data 
  attribute range and whether to overlay a "trend" (= a linear 
  regression line derived from the data points) 

Have a good weekend! 

