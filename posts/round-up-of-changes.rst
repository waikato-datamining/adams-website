.. title: round-up of changes
.. slug: round-up-of-changes
.. date: 2015-05-08 11:39:35 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

It's that time of the week again: an overview of what's happened since 
the last update... 

**Additions**

* new BufferedImage feature generators Min and Dimensions 
  in the adams-imaging module 
* new TextAreaPage wizard component 
* new "Mark location" plugin for Image viewer, allows you to 
  highlight x/y positions in an image 
* it is now possible to retrieve the setup of a flow that is running 
  on a remote server. You attach the RemoteFlowListener 
  to the remote flow before executing it and the use the new 
  "Open remote flow" menu in the flow editor on your local 
  machine to retrieve the setup 
  (you may have to remove your FlowEditor.props file in the 
  $HOME/.adams or %USERPROFILE%\_adams directory 
  to make this menu item show up) 

**Fixes**

* added distributionsForInstances method to FilteredClassifierExt 
  meta-classifier 
* DumpFile sink should no longer leave lock files on Windows 
  (writer.close() got moved into a finally{} clause) 
* SpreadSheetDbReader now forces cells to be strings for 
  string types loaded from database 
* Image viewer "Barcode" plugin no longer requires an 
  unmodified to be loaded 
* the output buffer for predictions didn't get reset properly 
  when evaluating multiple datasets, simply appended results 
  affected: 
  WekaCrossValidationEvaluator, WekaStreamEvaluator, 
  WekaTestSetEvaluator, WekaTrainTestSetEvaluator 

**Changes**

* the JAI histogram feature generator received the 
  option "numBins" that allows you to generate less than 
  the default 256 bins 
* RelativeCrop now allows to use the x/y location as the 
  anchor point as well, placing the crop rectangle relative 
  to this location 

Have a good weekend! 
