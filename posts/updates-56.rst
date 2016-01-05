.. title: updates 5/6
.. slug: updates-56
.. date: 2015-06-05 17:05:38 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

It's been a short, but busy week - Monday was Queen's Birthday holiday. 
Not only lots of data mining related work, but also lots of changes 
happening to ADAMS. The changes mainly improved usability in the Flow 
editor. 

**Fixes**

* MetaPartitionedMultiFilter now handles duplicate 
  regular expressions, e.g., when filtering the same 
  subset of attributes with several different filters 

**Changes**

* The notification area in the flow editor (eg displaying 
  errors) now offers a "Jump to" menu item from its 
  right-click popup menu. It lists all the actor names 
  that were listed in the message, allowing you to 
  quickly get to an actor that generated the error. 
* adams-spreadsheet: the LookUpAdd transformer 
  now accepts spreadsheets as well for updating 
  the look up table, not just pairs of objects 
* CopyFile/MoveFile now support the option for 
  multiple attempts, in case the I/O operation 
  fails (useful on Windows with its file locking) 
* adams-spreadsheet: the LookUpAdd transformer 
  now accepts spreadsheets as well for updating 
  the look up table, not just pairs of objects 

**Additions**

* Control charts are now available through "Chart" 
  functionality of the spreadsheet viewer tool 
  (adams-spreadsheet module). 

**Breakpoints**

The breakpoint/debugging support in the flow has been reworked 
extensively, in order to make it much more user-friendly and 
efficient. This was possible by combining and extending the 
functionality of the "Debug" flow execution listener, which offered 
similar functionality to the "Breakpoint" control actor. However, 
setting it up was a bit tedious. 

The new Breakpoint actors no longer have a GUI at all, they simply 
configure the "Debug" flow execution listener in a complete automatic 
fashion. By moving the control panel from the Breakpoint actor into 
the Debug listener, the added benefit is now that you only have a 
single window for all your breakpoints. Large flows with multiple 
breakpoints quickly became hard to debug, with many breakpoints simply 
called "Breakpoint" (uhm.. which one was this again?). 
Furthermore, the actor that is currently suspended, it now highlighted 
in the flow, so you can see where you are at. 
A new functionality is that you can now step through a flow, one actor 
at a time. This allows you to quickly check how variables/storage 
change, without having to stop the flow and add a new breakpoint at 
another location. 

Breakpoints can be added/removed/modified/disabled/enabled at runtime 
very easily, using the new "Breakpoints" tab in the control panel (see 
attachment breakpoints_controlpanel.png). 

The line-wrap bug in the token inspection panel has finally been 
fixed. When right-clicking in the object tree, you can now either copy 
the string representation to the clipboard or export it to various 
file formats. At the moment, spreadsheets, images and Weka datasets 
are supported apart from plain text. 

Another minor, but significant modification: I added a "Run (debug)" 
menu item to the flow editor, which allows you to step through a flow, 
actor by actor, without having to have any Breakpoint control actors 
present. 

.. thumbnail:: ../../images/breakpoints_flow.png

.. thumbnail:: ../../images/breakpoints_controlpanel.png

That's all for this week! 

