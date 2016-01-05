.. title: quiet week
.. slug: quiet-week
.. date: 2015-08-07 14:04:32 UTC+13:00
.. tags: updates
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

It's been a bit quieter with updates this past week, mainly because I've been
preparing material for my presentation/demo in Sydney at the BigMine 2015
workshop on Monday (http://bigdata-mining.org/bigmine-15/).

**Fixes**

* fixed a performance bottleneck in the GenericArrayEditor when dealing with
  large arrays (100s of elements)

**Changes**

* WekaSelectDataset (source): file chooser uses bookmarks panel now
* Instance Explorer: file chooser uses bookmarks panel now
* added multi-monitor support under the hood, i.e., child windows/dialogs show
  up on the same monitor as its parent (eg graphical actors in the Flow editor)
* added support for "atomic file move" operation to MoveFile transformer and
  several Rat inputs/outputs
* MoveFile can forward the moved file now instead of the input token (if enabled)

**Additions**

* flow debugging: Heatmap and Trail data structures now have their own renderer
  and exporter
* basic zoom functionality has been added to the Flow editor (zooms actor icons and text)
* Wizard (and flow) for creating compatible datasets for WEKA
* added EscapeLatexCharacters conversion to the adams-latex module

Have a good weekend!
