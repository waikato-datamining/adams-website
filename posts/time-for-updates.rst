.. title: time for updates
.. slug: time-for-updates
.. date: 2015-07-22 14:41:30 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

Despite being a very busy start of term last week, I managed to get in a number
of changes. Mainly due to an upcoming collaboration with the Biology department
here and being invited to talk at a workshop in August.

**Changes**

* Support for OSX builds (-app) has been removed. Users can use the bin/run.sh shell script for starting ADAMS from a terminal.
* Java code generation (eg when exporting a flow via ActorExecutionClassProducer) has seen a few readability improvements, which also makes it easy to modify the code: lists instead of arrays are being used now for assembling sub-actors; variable naming has been improved as well
* The Multi-Explorer now copies pretty much everything apart from result histories when using the "copy" button to copy a session.
* The FFmpeg sink was moved to the new adams-video addons module (see below)
* Reports in the Preview Browser now have a preview text area that shows the value of the currently selected report field; useful when the value is quite long or an error message spread out over several lines.
* The ReportDisplay sink now enables the user to use a custom entry name for the report being displaying, using a variable (eg file name)

**Additions**

* A new addons module got added, aimed at video processing: adams-video

  * WebcamImage source allows you to get a live-feed from a webcam attached to
    the computer
  * ListWebcams source outputs the names of all the webcams attached to the computer
  * WebcamInfo outputs some information on a webcam
  * MjpegImagesSequence allows the processing of each frame from a MJPEG movie
  * MovieImageSequence allows processing of frames every X msec from a large
    number of movie file formats
  * TrackObjects allows you to track objects in image sequences, e.g., obtained
    from movies
  * TransformTrackedObject transformer allows you to transform a tracked object
    using a callable transformer, e.g., for blurring a face that is being tracked
  * The ExtractTrackedObject transformer extracts the tracked object as
    separated image for further processing, e.g., feature generation

* The FileInUse boolean condition allows to check whether a file is currently
  in use by another process on the Windows platform
* The SelectCharset source allows the user to select a character set
  interactively, e.g., when loading files (= encoding).
* The adams-moa module has seen a few additions as well for regression
  (MOARegressorSetup, MOARegressing, MOARegressorEvaluator, MOATrainRegressor)
  and clustering (MOAClusterVisualization sink).

**Credits**

A lot of the code for processing movies, tracking objects and accessing webcams
was taken from BoofCV (http://boofcv.org/) and Xuggle (http://www.xuggle.com/).
