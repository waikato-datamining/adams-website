.. title: update 24/10
.. slug: update-2410
.. date: 2015-10-24 09:51:18 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

It's been a while since the last update on ADAMS, as I've been busy with our
commercial projects and development mainly occurring in these frameworks.
However, there were some changes that also affected the public ADAMS code:

**Fixes**

* ConsoleWindow standalone now correctly displays the window
* fixed launching Terminal on Windows (for Windows users: you know terminals as
  command-prompts)
* StorageForLoop source now implements the VariableUpdater interface to make
  the variable usage check pass

**Changes**

* ConsoleWindow now allows saving all the messages coming through to a file

**Additions**

* adams-weka: the Veto meta-classifier favors the specified label if it is
  predicted by at least the specified number/percentage of classifiers in the
  ensemble. If not, then Vote with majority rule is used.
* adams-weka: the SuppressModelOutput meta-classifier is useful if you
  want to suppress any large model output, e.g., from large ensembles
* adams-weka: with the ThresholdedBinaryClassification meta-classifier you can
  move the default probability threshold of 0.5 to decide which label is selected
  to another value  
* adams-weka: the RemoveOutliers filter uses the outlier detection framework
  introduced here, removing all instances that get marked as outliers

Have a good weekend!
