.. title: entering data
.. slug: entering-data
.. date: 2015-01-14 16:36:57 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

[One of my new years resolutions is to inform people a bit more about 
what's happening in the development of ADAMS. So I will try to post 
significant enough bits (improvements, additions, bugfixes) in the 
future.] 

Today, I've submitted some minor, but very useful, tweaks to some 
interactive sources. 

**EnterManyValues**

1. ValueDefinition now has a new "display" property which is the human-readable
   display string, whereas the "name" property is used in the SpreadSheet that's
   generated. That makes it easy to convert all values directly to
   "machine-friendly" variables in one go using the SpreadSheetVariableRowIterator
   transformer. 
2. No longer modal dialog, i.e., the flow can be stopped via the 
   "stop" button now while the dialog is being displayed. 

**EnterValue**

1. No longer modal dialog, i.e., the flow can be stopped via the "stop" button
   now while the dialog is being displayed. 
2. When using buttons for displaying the selection strings, the button with the
   label that matches the "initial" string gets the initial focus when the dialog
   gets displayed. Makes it rather easy to select this default option now just by
   hitting the space bar. 
