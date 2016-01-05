.. title: Final update for the year
.. slug: final-update-for-the-year
.. date: 2015-12-21 08:39:26 UTC+13:00
.. tags: update, clipboard, UI
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

Here is the final update for this year. Later on today, I will prepare a new release.

'Tis the season! ;-)

Well, actually mainly because of all the GUI improvements and the new adams-nlp module.

**Fixes**

* Renaming variables, callable actors, events and undo/redo no longer result in the flow wobbling around (better queuing in Swing thread)
* Improved the layout of the search panels, allowing for proper resizing and avoiding accidental hiding of search box

**Changes**

* Plots now offer a *Copy plot* menu item from the right-click menu, to copy a screenshot of the plot to the clipboard
* *Count* control actor now offers a monitor variable which allows resetting the internal count whenever the variable changes value
* The *Create callable actor* menu item from the Flow editor's right-click menu now allows the creation callable actors under *CallableActors*, *GridView* and *TabView*.

**Additions**

* *Copy to clipboard* target got added to the *Send to* functionality, which allows you to copy text, tables and graphical components (= screenshots) to the system's clipboard
* *TextOverlay* added for simple text overlays in plots (eg SequencePlotter/SimplePlot); gets used by the Weka plugin for classifier errors to display key on lines drawn on screen

Stay tuned!

