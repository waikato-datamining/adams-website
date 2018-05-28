.. title: About
.. slug: about
.. date: 2017-10-25 10:40:32 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

.. contents::

The core of ADAMS is the *workflow engine*, which follows the philosophy of *less
is more*. Instead of letting the user place operators (or actors in ADAMS terms)
on a canvas and then manually connect inputs and outputs, ADAMS uses a
tree-like structure. This structure and the control actors define how the
data is flowing in the workflow, no explicit connections necessary. The
tree-like structure stems from the internal object representation and the
nesting of sub-actors within actor-*handlers*.


Features
========

.. csv-table::
  :header: "Feature","Available"

  "Machine learning/data mining","WEKA_, WEKA webservice, MOA_, MEKA_, MEKA webservice, CNTK_, parameter optimization, experiment generation on-the-fly, setup generators, time series"
  "Data processing","WEKA_, `R-Project <R_>`_, XML, XSLT, XPath, HTML, JSON"
  "Streaming","MOA_, Twitter (record/replay)"
  "Spreadsheets","MS Excel (r/w), ODF_ (r/w), CSV (r/w), Gnumeric_ (r/w), fixed column (r/w)"
  "Databases","MySQL_, SQLite_, PostgreSQL_, HSQL_, MSSQL_, Sybase_, JDBC_, `MS Access <MSAccess_>`_, MongoDB_"
  "Imaging","ImageJ_, JAI_, BoofCV_, OpenIMAJ_, ImageMagick_, Gnuplot_, LIRE_, OCR (tesseract_), Barcodes (Zxing_)"
  "Graphics support","BMP, JPG, PNG, TIF, PDF, RAW (dcraw_, ufraw_)"
  "Audio","WAV, record, playback, spectrograms"
  "Spectral data","AniML, CAL, CML, DPT, JCampDX, MPS, NIR, Opus, Relab, SPA, SpecLib"
  "Visualization","Scatter and line plots, Control charts, Images, video, webcams, GIS (OpenStreetMap_)"
  "Scripting","Groovy_, Jython_, Python_"
  "Documentation","DocBook_, HTML"
  "Web","HTTP, FTP, SFTP, SSH, Email, `Webservices <CXF_>`_, rsync_"
  "Other","de/-compression (tar, zip, bzip2, gzip, lzma, xz), Java code generation"

.. _WEKA: http://www.cs.waikato.ac.nz/ml/weka/ 
.. _MOA: http://moa.cms.waikato.ac.nz/
.. _MEKA: http://meka.sourceforge.net/
.. _CNTK: https://cntk.ai/
.. _R: http://www.r-project.org/
.. _ODF: http://en.wikipedia.org/wiki/OpenDocument
.. _Gnumeric: http://www.gnumeric.org/
.. _Twitter: http://twitter4j.org/
.. _MSAccess: http://jackcess.sourceforge.net/
.. _MySQL: http://www.mysql.com/
.. _PostgreSQL: https://www.postgresql.org/
.. _HSQL: http://hsqldb.org/
.. _MSSQL: https://en.wikipedia.org/wiki/Microsoft_SQL_Server
.. _Sybase: https://en.wikipedia.org/wiki/Adaptive_Server_Enterprise
.. _SQLite: https://sqlite.org/
.. _JDBC: https://en.wikipedia.org/wiki/Java_Database_Connectivity
.. _MongoDB: https://www.mongodb.com/
.. _ImageJ: http://imagej.nih.gov/ij/
.. _JAI: http://en.wikipedia.org/wiki/Java_Advanced_Imaging
.. _BoofCV: http://boofcv.org/
.. _ImageMagick: http://www.imagemagick.org/
.. _OpenIMAJ: http://openimaj.org/
.. _Gnuplot: http://gnuplot.info/
.. _LIRE: http://code.google.com/p/lire/
.. _tesseract: https://code.google.com/p/tesseract-ocr/
.. _Zxing: https://github.com/zxing/zxing
.. _dcraw: http://www.cybercom.net/~dcoffin/dcraw/
.. _ufraw: http://ufraw.sourceforge.net/index.html
.. _OpenStreetMap: http://www.openstreetmap.org/
.. _Groovy: http://groovy.codehaus.org/
.. _Jython: http://jython.org/
.. _Python: http://python.org/
.. _DocBook: http://www.docbook.org/
.. _CXF: http://cxf.apache.org/
.. _rsync: https://github.com/fracpete/rsync4j


Example flow
============

.. image:: ../../images/flow_snippet.png

* Horizontal and vertical indicators show how the data flows
* Each actor has its own icon, since the name can be changed arbitrarily
* Four types of actors: standalone (red; no input, no output), source (orange;
  only output), transformer (green; input and output) and sink (greyl; only
  input)
* Control actors, i.e., actors that determine the flow of data or flow execution are blue
* Actors with parameters usually show a so-called quick info on the right-hand
  side of the name, to give the user an idea how the actor is parametrized
  without having to open up the dialog with the options.
