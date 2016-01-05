.. title: final roundup before next release
.. slug: final-roundup-before-next-release
.. date: 2015-06-19 14:49:13 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

It's been a busy week with a lot of little changes before the upcoming release.

**Fixes**

* The GPD classifier (package weka.classifiers.functions) now uses the
  GaussianProcesses classifier as fallback, in case it cannot build a model
  (avoids predicting only NaNs)
* The internal model used by WekaForecasting (adams-timeseries) gets correctly
  reset now
* Adding actors after the SequenceSource is no longer broken

**Changes**

* The PropertySheetPanelPage and WekaPropertySheetPanelPage wizard pages now
  have an optional button panel, for loading/saving the current properties
* The wizard framework now uses the logging infrastructure as well
* The ParameterPanelPage now offers the REGEXP option, which allows the
  entering of regular expressions
* The Listeners menu item got removed from the Flow editor tree popup menu
* The main menu of ADAMS has been rearranged, with the Machine learning menu
  getting decluttered, moving stuff into Visualization and Tools
* The Flow editor's menu got consolidated as well, with the Debug and Execution
  menu getting merged into the new Run menu
* The toolbar of the Flow editor is now configurable as well (eg through its preferences)
* The introduction of the BaseClassname wrapper for class names, make it easier
  in the GUI to give feedback on an incorrectly entered classname - affects the
  following actors: Cast, ArrayProcess, ArrayGenerate, SelectObjects,
  WekaSelectObjects
* The default class for the Cast control actor is now Unknown, which makes the
  actor now always show up in the actor tree

**Additions**

* The Dark Lord, an attribute selection algorithm using a genetic algorithm,
  has been added to the main menu
* Actor processors added for listing the usage of callable actors, variables
  and storage items
* Find usages is a new menu item in the popup menu Flow editor tree, which
  allows you to list occurrences of variables, storage and callable actors
  throughout the flow - and allows you to jump to them (you may need to remove
  your $HOME/.adams/FlowEditor.props or %USERPROFILE%/_adams/FlowEditor.props
  file to make this appear)
* The SelectDirectoryPage and SelectMultipleDirectoriesPage pages got added to the wizard
* The ListTables source (adams-core) allows you to list tables from a database,
  e.g., when you want to iterate over them and extract some information
* With the DatabaseMetaData source (adams-spreadsheet), you can output various
  types of meta-data information about a database connection/tables/columns.
* The SourceReset source actor allows you to reset all sub-actors whenever a
  monitored variable changes (like the TransformerReset and SinkReset actors)
* The Flow editor now sports a New from clipboard menu item, which allows you
  to paste the current actor on the clipboard straight into a new tab
* Main menu items Margin curve and Cost curve got added (adams-weka)
* That's it for now. At the moment, I'm in the process of updating the
  screenshots in the manual(s). Sometime in the next few days, I'll be making a
  new release.
