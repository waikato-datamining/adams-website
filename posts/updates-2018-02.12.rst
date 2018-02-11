.. title: Updates 2018/02/12
.. slug: updates-2018-02-12
.. date: 2018-02-12 09:25:07 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

Apart from some bugfixes, the biggest change is the addition of the *adams-rest*
module. This module allows you to quickly create REST webservices, a simpler
alternative to SOAP-based ones. Using the *GenericServer*, you can simply slot
together any functionality that you want, using classes that implement the
*adams.flow.rest.RESTPlugin* interface. See below for more details on what
REST functionality is already available.

**Fixes**

* *adams-spreadsheet:* Fixed handling of null values for date/time columns in the
  *SpreadSheetDbReader* source.
* Improved positioning of dialogs/frames on screen, leaving (by default) 50 pixels
  at the bottom of the screen reserved (GUIHelper.props, property *ScreenBorder.Bottom*).
  This avoids dialogs like the GenericObjectEditor to appear behind the taskbar on
  Windows.
* *adams-rats:* The *FileLister* rat input had a bug when adding the moved files
  to its output list when skipping files that were in use, generating an 
  IndexOutOfBoundsException.


**Changes**

* The *expressions* in the debug panel of the Flow editor now allow string expressions
  as well, rather than just simple strings with variables.
* Added ability to delete via regular expression: *DeleteVariable*, *DeleteStorageValue*
* The *StringCut* transformer now uses *Index* instead of *int* for the character positions,
  allowing the use of *last*.
* *adams-imaging: The conversions *RectangleToString* and *StringToRectangle* can parse 
  the x0y0x1y1 format now as well (default is xywh).
* *adams-net:* The *HttpRequest* transformer now accepts byte arrays as well as input.
* *adams-timeseries:* Updated timeseriesForecasting dependency to 1.0.25


**Additions**

* *SwapVariables* allows swapping of values of two variables.
* *Run to here* was added to the Flow editor menu, which can be used while debugging 
  a flow and you don't want to step through all the actors.
* Additional boolean conditions for tokens: IsBoolean, IsByte, IsShort, IsInteger, IsLong, 
  IsFloat, IsDouble
* Added JSON support for reports: conversions *JsonToReport* and *ReportToJson*, 
  *DefaultSimpleJsonReportReader* and *DefaultSimpleJsonReportWriter*.
* Added the *PathSplit* conversion for splitting path into its individual parts:
  drive letter or server from UCN path (if applicable), directories, file name.
* *adams-imaging:* 

  * Added modified version of *CountColor*, which performs linescan 
    from left/right for counting and stops as soon as it hits another color (used 
    for objects located in center of image): *CountColorOutside*
  * Added the *LocatedObjectToRectangle* conversion, which turns the position
    of the object into a *BaseRectangle* object.
  * The *GetImageObjectMetaData* transformer retrieves the meta-data map
    of a located object.

* The *SimpleStringReplace* transformer uses simple String.replace(..., ...) for 
  replacing sub-strings. Gets around problems with trying to specify the regular 
  expression of *StringReplace* when trying to only do a simple string replacement.
* *adams-net:*

  * Added *URLEncode* and *URLDecode* conversions for creating URL-conform strings
    and turning them back into regular strings (e.g., "hello world" into "hello+world").
  * Added *StringArrayToURLParameters* and *URLParametersToStringArray* conversions
    to turn string array of key-value pairs and a string that can be appended to a URL
    (and vice versa).

* Added *adams-rest* module, for providing REST webservice support.
* *adams-rats:* 

  * Added generic REST support via the *adams.flow.rest.RatsServer* REST server
    (same as *GenericServer*, but aware of the *Rat* actor it belongs to).
  * Generic (text) upload capability using the *adams.flow.rest.text.RatsTextUpload* 
    REST plugin.
  * Added support for controlling Rat actors (accessible via *RatControl/RegisterFlow*) 
    via REST service: *control.RatControl*

* *adams-spectral-2dim-core:* 

  * Added conversions to turn spectrum into JSON string and vice versa: 
    *SpectrumToJson*, *JsonToSpectrum*.
  * Added JSON support for reports: *DefaultSimpleJsonSampleDataReader* 
    and *DefaultSimpleJsonSampleDataWriter*.

* *adams-spectral-2dim-webservice:*

  * Added REST webservice plugins for spectra: *DeleteSpectrum* (delete from DB), 
    *GetSpectrum* (load from DB), *PutSpectrum* (store in DB), 
    *TransformSpectrum* (transform spectrum using specific filter)

* *adams-spreadsheet:* With the *SpreadSheetSubsetFromGroup* transformer it is possible 
  to retrieve specific rows from groups within spreadsheet.

