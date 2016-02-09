.. title: updates 25/1
.. slug: updates-251
.. date: 2016-01-25 19:12:22 UTC+13:00
.. tags: updates
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

**Fixes**

* *adams-weka:* added note to *WekaAttributeSelection* transformer that cross-validation
  will not produce any reduced/transformed data
* *adams-weka:* upgraded Weka to revision 12379 to fix handling of string attributes in some filters

**Changes**

* Flow tab *Parameters* now displays arrays as ordered list
* *adams-video:* *MjpegImageSequence* and *MovieImageSequence* now have a parameter 
  to limit the number of images generated
* containers now have a short help string attached including the class that
  the item represents; this help gets displayed in an actor's help dialog, section
  *Additional information* 
* *adams-core*: 

  * *SelectObjects* interactive source can be used for objects that don't
    belong to a class hierarchy now as well, e.g., *adams.core.base.BaseString*. The
    only requirement is that the object can be instantiated from a *String*.
  * *ContainerValuePicker* now has an *ignoreMissing* flag (on by default), which
    allows you to generate logging/error in case of missing container values.

**Additions**

* *adams-core:* the *SelectArraySubset* transformer allows the user to select the 
  desired array elements interactively
* *adams-imaging:* added *Average/Median* multi-image operations
* *adams-heatmap:* added *HeatmapToBufferedImageExpression* conversion which
  uses a mathematical expression for converting the heatmap values
* *adams-weka:* 

  * added main menu item for the new *WEKA Workbench*
  * added *WekaAttributeSummary* sink for visualizing attributes in a dataset

* *adams-video* 

  * added *MovieInfo* transformer for extracting information from
    a movie file
  * added *MovieImageSampler* transformer that outputs the images
    obtained through a sampling algorithm

