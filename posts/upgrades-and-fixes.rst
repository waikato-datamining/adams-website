.. title: upgrades and fixes
.. slug: upgrades-and-fixes
.. date: 2016-01-11 16:05:33 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

The new year started quietly with a few library upgrades and only a few bug fixes.

**Fixes**

* The *Jump to* functionality of the *Find usages* dialog in the flow editor was broken.
* *Find usages* now also lists attached variables

**Changes**

* adams-weka: Weka was upgraded to 3.7.13 - I also uncovered/reported a
  performance bottleneck in Weka, relating to a scheme's setOptions method. Due
  to some new functionality, this call was almost 100x slower than previously.
  This was only noticeable in classifiers that configured other schemes using
  this approach.
* adams-weka: GridSearch was upgraded to 1.0.9 - mainly to work with 3.7.13
* adams-video: VLCj was upgraded to the latest 3.10.1
* adams-core: Highlight variables and Remove variable highlights menu items
  have been removed from the flow editor's View menu. Instead, you can use the
  Locate variable menu item from the Edit menu (also new is the Locate storage
  name menu item). 

**Additions**

* adams-video: new tool Screencast added, which allows you to record screencast
  data (sound/webcam/screen) to be used for creating tutorials, for instance.
* adams-video: added the following standalones for automatically recording
  screencast data while a flow runs - but there is still a performance issue,
  which I need to investigate at some stage

  * RecordingSetup
  * StartRecording
  * StopRecording

* adams-meka: added new visualization sinks for Meka

  * MekaGraphVisualizer
  * MekaMacroCurve
  * MekaMicroCurve
  * MekaPrecisionRecall
  * MekaROC

