.. title: update 30/4
.. slug: update-304
.. date: 2015-04-30 09:43:55 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

It's time for a round-up of all the changes that have happened... 

**Fixes**

* the ORDER BY clause of the SpreadSheetQuery transformer 
  got applied to the input spreadsheet rather than final one, 
  screwing up the WHERE clause 
* the abstract class AbstractProcessWekaInstanceWithModel 
  did not clear the internal model when its options got 
  changed; affected transformers: MekaClassifying, 
  Weka/MOAClassifying/Clustering 

**Modifications**

* SpreadSheetTable now uses plugin architecture for 
  processing/plotting cols/rows/cells in its popup menus 
* Min/Max heatmap feature generators can output the 
  position now as well 
* spreadsheet plot generators can generate plot name 
  now also based on range of cell values 
* Excel and ODF spreadsheet readers now support 
  "no" or "custom" headers 
* ForLoop source can output integers now as array 
  as well 
* the message of the Stop control actor can contain 
  variables now as well 

**Additions**

* added NewHeatmap source to adams-heatmap 
* added HeatmapGetValue/HeatmapSetValue transformers 
  to adams-heatmap 
* added VotedImbalance meta-classifier to adams-weka 
  classifier generates X number of resampled datasets 
  from input data, limiting size to smallest class, building 
  base-classifier on them and then uses Vote meta-classifier 
  for making predictions 
* added PromptUser boolean flow condition, asking user 
  whether to execute conditional actor or not 
* added "Append datasets" and "Merge datasets" to the 
  main menu of the adams-weka modulel; uses wizards 
  to guide the user for combining datasets 
* added specialized pages to the wizard: SelectFilePage, 
  SelectMultipleFilesPage, WekaSelectDatasetPage, 
  WekaSelectMultipleDatasetsPage 
* added new (optional) Look'n'Feel: PgsLookAndFeel, 
  which can be activated in the GUIHelper.props file 
* new source for outputting integers: IntegerRange 
  uses a range string and a maximum to generate 
  these integers (eg "3-5,7,12,18-last") 

