.. title: update 13/11
.. slug: update-1311
.. date: 2015-11-13 17:14:35 UTC+13:00
.. tags: updates, imaging, storage, variable
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

It's this time of the week again and there have been a number of updates again.

**Fixes**

* adams-core: the Inspect control actor no longer interprets skip as cancel
* adams-core: the BreakPoint actor no longer locks the application when
  attempting to stop the flow inside a block that uses atomic execution (=
  finishedBeforeStopping option in Tee/Trigger/etc)

**Changes**

* adams-core: the ImagePanel now allows undo/redo through the right-click popup
  menu as well
* adams-imaging: Crop paint selection plugin offers undo/redo and also stores
  the x/y and width/height of the crop (in relation to the original image);
  PaintSelection supports undo/redo now too
* option parsing of integer types now handles float-type strings (eg 11.0) as
  well, by parsing them as float and the retrieving the correct value - this is
  useful when dealing with numeric values stored in reports, as the default type
  there is float (even if you store an integer)
* adams-meka: MEKA has been upgraded to 1.9.0
* Index/Range (and spreadsheet/WEKA related classes) now allow enforcing of
  numeric indices by preceding them with "#" (eg "#13"); all names
  (columns/attributes/labels) can be enclosed with double quotes now
* tool tips in the GenericObjectEditor have been improved; e.g., classes that
  implement ExampleProvider (eg Index/Range) now automatically append the example
  text

**Additions**

* adams-core: new actor processors ListAllVariables and ListAllStorageNames
* adams-weka: LeanMultiScheme is an extended version of Weka's MultiScheme
  meta-classifier with better memory management
* adams-core: ReportToVariables and ReportToStorage transformers allow the
  transfer for multiple report values into variables/storage items in one go
* adams-core: ModuleInfo source actor outputs information on the ADAMS module
  that make up the ADAMS application

Have a good weekend!
