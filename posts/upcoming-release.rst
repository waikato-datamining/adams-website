.. title: upcoming release
.. slug: upcoming-release
.. date: 2015-11-17 16:40:28 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

Just a heads-up that I'll be making a new release tomorrow.

Since last week, only a few things changed:

* fixed a flicker issue when processing videos in the flow and displaying the
  individual frames with a custom zoom in the ImageViewer (zoom got reset to 100%
  before changed to custom zoom)
* adams-weka: added WekaGetCapabilities transformer to retrieve capabilities
  from classes like Filter, Classifier and Clusterer. The
  WekaCapabilitiesToInstances and WekaCapabilitiesToSpreadSheet conversion use
  this information. The former to generate random data, the latter to output the
  capabilities in tabular format.
* the Flow editor now allows you to define keyboard actions (eg adding or
  enclosing actors using a specific actor) to speed up flow development (see
  manual "Keyboard actions")

Fingers crossed that tomorrow's release goes smoothly. :-)
