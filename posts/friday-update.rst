.. title: Friday update
.. slug: friday-update
.. date: 2015-08-21 17:16:37 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

It's time to bring you up-to-date what's been happening under the hood of ADAMS lately.
Well, for one thing, I got invited to give a `demo
<http://open.fracpete.org/2015/08/adams-demo-at-bigmine-2015-workshop/>`_ at
the BigMine 2015 workshop as part of KDD 2015 in Sydney. Eventually, a paper
will be out.

The other major thing is that we definitely stick now with Java 8, mainly due
to the better support of Java 8 in regards to file handling (java.nio.Files
namely) and atomic moves of files/directories. I had the problem with a
commercial product (and, of course, Windows) that files got move, but Windows
still thought that they might be in use. Resulted in failures to process files.
Rather annoying. However, moving to atomic moves, this problem has gone away
now.

**Fixes**

* AbstractChooserPanel and its derived component no longer doubles up the entry
  when pasting text into it.
* PropertySheetPanelPage (used in wizards) now correctly updates the buttons
  when values change.
* Fixed a performance issue in the Instance Explorer when selecting the color
  for many selected rows.
* The Clear graphical output menu item in the Flow editor was a bit to
  aggressive in the cleanup and left the editor in a broken state
  (NullPointerExceptions galore).

**Updates**

* The message option of the EnterManyValues source handles variables now as
  well, automatically expanding them
* The storage panel, as used in the Breakpoint's user interface, now allows the
  export of selected objects, just like the object tree.
* SpreadSheetTable/Model now allow you to toggle between cell value and cell
  type view. Sometimes it's easier to spot a string value where a number should
  be with this functionality (via popup menu).
* Instance Explorer now allows you to use the value of an attribute as ID
  rather than the row number.
* Tables now offer copy row/column as well through their popup menus.
* HashSetAdd transformer now accepts spreadsheets and arrays of objects as
  well, for speeding up the add operation.
* The CsvSpreadSheetReader received a performance boost option, which can be
  used for spreadsheets that have uniform column types: it allows you to specify
  a number of rows to use for identifying the column type automatically. The
  speedup on my laptop for a 2400 column by 2000 row spreadsheet with mainly
  floating values was 50% (30s instead of 60s).

**Additions**

* WekaGeneticAlgorithm transformer added, which allows you to use the DarkLord
  genetic algorithm now also in the flow, not just through the wizard.
* String conversion dialog added to the maintenance section (requires developer
  user mode), allows you to backquote/unbackquote etc strings.
* RemoveTestInstances filter (package weka.filters.unsupervised.instance)
  allows you to remove rows from the data passing through (only first batch),
  by matching the IDs from a selected test set against the current data. Allows
  you to avoid manually removal of instances from a data set (hold out dataset)
  when training a classifier on the full dataset.

Have a great weekend!
