.. title: fixes and additions
.. slug: fixes-and-additions
.. date: 2015-02-10 12:55:28 UTC+13:00
.. tags: updates, UI, heatmap
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

Time for a little round-up of what's happened to ADAMS lately... 

**Fixes**

* sluggish behavior of flow editor (opening/saving/undo) due to 
  regression in EnumOption option handling class (finding/registering 
  property editor on demand was very slow) 
* obtaining subsets from Notes objects only returned the first element 
  of each type 
* TryCatch control actor properly flushes the tokens of its subflow 
  when an error occurs 
* Upper/LowerCase conversions take locale into account 
* ImageProcessor tool works properly with the revamped ImageFileChooser dialog 
* PreviewBrowser tool displays arrays in a more sensible fashion 
* WekaFileReader didn't output an Instances object if no rows present 

**Addtions** 

* print support got added to the PDF viewer (tool and sink) 
* ImageHistogram sink added to adams-imaging 
* additional actors for the adams-heatmap module 
  * HeatmapArrayStatistic transformer 
  * HeatmapLocateObjects transformer 
  * HeatmapHistogram sink 
* Heatmap viewer can display a histogram of current heatmap 

