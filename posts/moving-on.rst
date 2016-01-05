.. title: moving on
.. slug: moving-on
.. date: 2015-06-26 16:17:43 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

With the ADAMS release finally out, I was able to tackle cleaning out old stuff
and updating libraries.

**Old stuff**

* Emptied Conversion.props files, which are used to keep backward compatibility
  of old flows in case class names or option names change. Upside is that loading
  of flows should be quicker again, downside that old flows might no longer work
  (simply load them with ADAMS 0.4.10 and save them again)
* Removed classes that have been marked as deprecated:

  * adams-core/src/main/java/adams/data/conversion/MakeFilename.java
  * adams-core/src/main/java/adams/data/conversion/TimestampToDouble.java
  * adams-core/src/main/java/adams/flow/processor/FixDeprecatedCommandlineTransformers.java
  * adams-core/src/main/java/adams/flow/transformer/AnyToCommandline.java
  * adams-core/src/main/java/adams/flow/transformer/CommandlineToAny.java
  * adams-core/src/main/java/adams/flow/transformer/FileSize.java
  * adams-core/src/test/java/adams/data/conversion/MakeFilenameTest.java
  * adams-core/src/test/java/adams/data/conversion/TimestampToDoubleTest.java
  * adams-core/src/test/java/adams/flow/processor/FixDeprecatedCommandlineTransformersTest.java
  * adams-core/src/test/java/adams/flow/transformer/AnyToCommandlineTest.java
  * adams-core/src/test/java/adams/flow/transformer/FileSizeTest.java
  * adams-imaging/src/main/java/adams/data/image/transformer/Crop.java
  * adams-imaging/src/main/java/adams/flow/sink/ImageMagickWriter.java
  * adams-imaging/src/main/java/adams/flow/sink/JAIWriter.java
  * adams-imaging/src/main/java/adams/flow/transformer/ImageMagickReader.java
  * adams-imaging/src/main/java/adams/flow/transformer/ImageMetaDataExtractor.java
  * adams-imaging/src/main/java/adams/flow/transformer/JAIReader.java
  * adams-imaging/src/main/java/adams/flow/transformer/SetImagePixel.java
  * adams-imaging/src/test/java/adams/data/image/transformer/CropTest.java
  * adams-imaging/src/test/java/adams/flow/sink/ImageMagickWriterTest.java
  * adams-imaging/src/test/java/adams/flow/sink/JAIWriterTest.java
  * adams-imaging/src/test/java/adams/flow/transformer/ImageMagickReaderTest.java
  * adams-imaging/src/test/java/adams/flow/transformer/ImageMetaDataExtractorTest.java
  * adams-imaging/src/test/java/adams/flow/transformer/JAIReaderTest.java
  * adams-imaging/src/test/java/adams/flow/transformer/SetImagePixelTest.java
  * adams-moa/src/main/java/adams/flow/processor/FixDeprecatedMOAClassifier.java
  * adams-moa/src/main/java/adams/flow/processor/FixDeprecatedMOAClusterer.java
  * adams-moa/src/main/java/adams/flow/transformer/MOAClassifier.java
  * adams-moa/src/main/java/adams/flow/transformer/MOAClusterer.java
  * adams-moa/src/test/java/adams/flow/transformer/MOAClassifierTest.java
  * adams-moa/src/test/java/adams/flow/transformer/MOAClustererTest.java
  * adams-net/src/main/java/adams/flow/processor/FixDeprecatedEmail.java
  * adams-net/src/main/java/adams/flow/sink/Email.java
  * adams-net/src/test/java/adams/flow/sink/EmailTest.java
  * adams-spreadsheet/src/main/java/adams/data/conversion/AggregateSpreadSheet.java
  * adams-spreadsheet/src/main/java/adams/flow/processor/FixDeprecatedStringToSpreadSheet.java
  * adams-spreadsheet/src/main/java/adams/flow/transformer/StringToSpreadSheet.java
  * adams-spreadsheet/src/test/java/adams/data/conversion/AggregateSpreadSheetTest.java
  * adams-spreadsheet/src/test/java/adams/flow/transformer/StringToSpreadSheetTest.java
  * adams-weka/src/main/java/adams/flow/processor/FixDeprecatedWekaClassifier.java
  * adams-weka/src/main/java/adams/flow/processor/FixDeprecatedWekaClusterer.java
  * adams-weka/src/main/java/adams/flow/transformer/WekaClassifier.java
  * adams-weka/src/main/java/adams/flow/transformer/WekaClusterer.java
  * adams-weka/src/test/java/adams/flow/transformer/CommandlineToAnyTest.java
  * adams-weka/src/test/java/adams/flow/transformer/WekaClassifierTest.java
  * adams-weka/src/test/java/adams/flow/transformer/WekaClustererTest.java

**Libraries**

I updated the following libraries to the specified versions:

* Jython 2.7.0 (Python scripting)
* WEKA timeseries 2015.05.19
* jackcess 2.1.2 (MS Access)
* Apache CXF 3.1.1 (webservices)
* jetty 9.2.10.v20150310 (webserver)
* postgresql 9.4-1201-jdbc41
* JSch 0.1.53 (sftp, scp, ssh, ...)
* mysql-jdbc-connector 5.1.35
* javax.mail 1.4.7 (sending emails)
* RSyntaxTextArea 2.5.7 (eg Groovy/Python syntax highlighting)
* JFlex 1.4.3 (parser generation)
* json-path 2.0.0
* sqlite-jdbc 3.8.10.1
* joda-time 2.8.1
* jide-oss 3.6.9 (eg directory chooser)
* quartz 1.8.6 (cronjobs)
* Apache POI 3.12 (MS Excel documents)
* metadata-extractor 2.8.1 (image meta-data)
* Apache pdfbox 1.8.9 (eg PDF text extraction)
* twitter4j 3.0.6

In case you feel adventurous, give the new snapshots a go! ;-)
