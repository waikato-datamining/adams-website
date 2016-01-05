.. title: updates from a busy week
.. slug: updates-from-a-busy-week
.. date: 2015-06-12 08:20:51 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

It's been a busy week and debugging support has seen quite some improvements. 

**Debugging**

* PathBreakpoint now allows you to select the 
  actor through a dialog rather than having to 
  enter the path manually 
* due to some API changes to input consumers, 
  it is now possible to inspect the current token 
  when stepping through the flow manually, 
  rather than only when reaching a Breakpoint 
  control actor 
* instead of only outputting a textual representation 
  of tokens (inspection panel), a class hierarchy for 
  custom renderers has been implemented 
  plain text (used so far; fallback), images, 
  spreadsheets, reports, Weka Instance(s), 
  timeseries 
* these rendering classes are now also used 
  when previewing items from the internal storage 
  ("storage" tab) 
* started work on adding ability to edit items 
  in internal storage; at this stage primitives 
  and arrays of primitives are supported, as 
  well as objects that can be manipulated 
  through the GenericObjectEditor 
  (more will come) 

Here is the summary of the remaining updates: 

**Fixes**

* The vertical marker paintlet used by the 
  SequencePlotter now uses the actual 
  minimum/maximum of the canvas, not 
  just the one derived from the data 

**Changes**

* control charts plots can now be initialized with 
  a container from the ControlChart transformer 
  and subsequently display data using the last 
  known limits; furthermore, added support for 
  post-processsing, e.g., limiting the number of 
  data points visible at any given time 
* spreadsheets are now editable in the viewer; 
  the SpreadSheetDisplay sink offers the new 
  "readOnly" option (default = readonly) 

**Additions**

* OpenFile sink opens the incoming file with 
  the application associated with it as 
  determined by the operating system 
* MissionControl control actor is a minimalistic 
  interface for pausing/resuming/stopping a 
  flow; useful when starting a flow from the 
  commandline using the FlowRunner class 
  instead of from the GUI 
* InputOutputListener control actor allows 
  you to listen in on the tokens go into and 
  coming out from a sub-flow by forwarding 
  them to callable actors for further processing 

Thanks for the feedback regarding the debugging functionality and have 
a good weekend! 
