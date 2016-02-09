.. title: updates 9/2/16
.. slug: updates-9-2-16
.. date: 2016-02-09 16:54:58 UTC+13:00
.. tags: spreadsheet, weka
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

I finally finished recording my lessons for the upcoming `MOOC
<https://weka.waikato.ac.nz/>`__, which gives me a bit of breathing space for
some ADAMS stuff again:

**Fixes**

* *adams-spreadsheet:* spreadsheet file viewer's *close* operation now actually
  closes the window
* implemented more efficient undo/redo in the Flow editor, which is noticeably
  faster for large flows with 100s or 1000s of actors
* *adams-spreadsheet:* *SpreadSheetVariableRowIterator* and
  *SpreadSheetStorageRowIterator* now handle missing values correctly (not just
  missing cells)
* *adams-excel:* the *ExcelStreamingSpreadSheetReader* now handles missing cells
  in the XML data stream properly

**Changes**

* flow editor tabs *Variables* and *Storage names* now allow locating all
  usages of the selected variable/storage name - like the tree popup
  menu's *Find usages*
* *adams-weka:* Weka upgraded to revision 12423 to include new GaussianProcesses
  classifier that can handle instance weights natively

**Additions**

* *Swap* actor menu item got added to the Flow editor's tree popup menu.

Thanks for your feedback!

Cheers, Peter
