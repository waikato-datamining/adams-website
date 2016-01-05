.. title: updates 8/7
.. slug: updates-87
.. date: 2015-07-08 11:12:12 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

Last week wasn't overly busy with changes, so I've waited till now for an update.

**Fixes**

* DumpFile sink now offers buffering of X tokens before writing to disk in
  order to improve I/O performance
* ProgressBar now uses the correct font for calculating the offset for the
  percentage being display
* quick info of the NewSpreadSheet source no longer displays the columns twice,
  but sheet name and columns

**Changes**

* Added a section on setting up IntelliJ IDEA for development in the manual
* Added video on how to setup IntelliJ IDEA for development (recording time was
  1:47, almost feature film length)
* Added a button for closing tabs to Flow editor, Image viewer, Image
  processor, Spreadsheet viewer (see close_tab.png attachment)
* The GenericObjectEditor (GOE) can now load/save setups using cmdlines
  (.cmdline) and XStream XML serialization (.xml) as well, on top of Java
  serialized objects (.model), using the load/save buttons in the bottom left
  corner of any GOE window
* Wizards now allow loading/saving the current setup from any page and for the
  overall wizard - useful when setting up default parameters for various
  scenarios
* WekaChooseAttributes now offers the displayed message as customizable option
* WekaInstancesInfo can output all attributes now as well; supports output of
  array as well
* ProgressBar now offers custom prefix and suffix for surrounding the
  percentage being displayed
* generating code from flows, e.g., using the ActorExecutionClassProducer in
  the export functionality of the flow editor, now outputs much nicer source
  code, mimicking the nesting of actors using {...} blocks and using shortened
  class names wherever possible - gone is the spaghetti code and also some
  unnecessary dead code!

**Additions**

* HttpRequest source uses JSoup library for sending GET/POST requests to URLs;
  handles cookies as well - can be used for web scraping
* conversions: SplitOptions, JoinOptions
* WekaInstancesPlot allows you to plot two attributes against each other using
  Weka's plotting facility
* WekaSelectDataset source works like SelectFile, but uses Weka's file chooser component
* PlotAttributeVsAttribute got added to the main menu, allowing you to generate
  plots like the matrix plot in the Explorer's Visualize tab, but you choose what
  attributes to plot against each other

**Removals**

* HttpPost transformer now obsolete, due to introduction of HttpRequest source

The next few weeks will most likely be a bit quieter, since B semester is
starting up and I'll be busy with my students.
