.. title: bunch of changes
.. slug: bunch-of-changes
.. date: 2015-07-31 17:11:19 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete


It's been quite busy here again, with lots of things happening. Most notably,
there is now a new data structure available for managing tracked objects: Trail.

**Fixes**

* WekaStreamFilter now handles Instances objects correctly
* adams-events/adams-rats: the default scheduler instantiation is now
  centralized and synchronized to avoid exception that scheduler has already been
  instantiated (race condition)
* debugging renderer fixed: WekaInstancesRender displayed more than one
  instance in the table

**Changes**

* Once/TriggerOnce control actors can be reset now using a monitor variable
* HeatmapDisplay actor now works inside a TabView
* Inspect control actor now allows the automatic closing of the frame after
  accept/skip was clicked (useful when only using once)
* MathExpression source/transformer now offer rouding (ie output of integer
  instead of double)
* timeseries now use 1 milli-second as resolution rather than 0.1 second
* FileInUse boolean condition now works on Unix as well
* added IsAndroid boolean condition
* Console sink now allows new lines (\n) and tabs (\t) in the prefix string
* the GenericObjectEditor now places the popup with the class tree better;
  especially on Windows, it no longer gets stuck behind the taskbar

**Additions**

* new conversion

  * Point2DToString/StringToPoint2D
  * QuadrilateralLocationToString/StringToQuadrilateralLocation
  * QuadrilateralLocationCenter

* added support for timestamp strings with milli-seconds: BaseDateTimeMsec
  experimental support for spreadsheet cells that use a float instead of a double
  as internal data representation (for conserving memory)
* WaitForFile transformer waits for a file to become fully available (eg when
  being written or uploaded; confer FileInUse boolean condition)
* Trail data structure for handling tracked objects, supported by the following
  actors:

  * source: NewTrail
  * transformers; AddTrailBackground, AddTrailStep, GetTrailBackground,
    TrailFileReader, TrailFileWriter, TrailFilter
  * sink: TrailDisplay

* Trail viewer for loading, saving, filtering trails

That's it for now and have a good weekend!
