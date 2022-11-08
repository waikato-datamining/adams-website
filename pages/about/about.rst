.. title: About
.. slug: about
.. date: 2022-11-09 08:50:32 UTC+13:00
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

  "Machine learning/data mining","WEKA_, MOA_, MEKA_, parameter optimization, experiment generation on-the-fly, setup generators, time series"
  "Data processing","WEKA_, `R-Project <R_>`_, XML, XSLT, XPath, HTML, JSON, YAML"
  "Streaming","MOA_"
  "Spreadsheets","MS Excel (r/w), ODF_ (r/w), CSV (r/w), Gnumeric_ (r/w), fixed column (r/w), Matlab_ (r/w)"
  "Databases","MySQL_, SQLite_, PostgreSQL_, HSQL_, MSSQL_, Sybase_, JDBC_, `MS Access <MSAccess_>`_, Redis_"
  "Imaging","JAI_, BoofCV_, OpenCV_, Gnuplot_, LIRE_, OCR (tesseract_), Barcodes (Zxing_)"
  "Graphics support","BMP, JPG, PNG, TIF, PDF"
  "Audio","WAV, record, playback, spectrograms"
  "Spectral data","AniML, CAL, CML, DPT, EEM, JCampDX, MPS, NIR, Opus, Relab, SPA, SPC, SpecLib, spreadsheet-based"
  "Visualization","Scatter and line plots, Control charts, Images, video, webcams, GIS (OpenStreetMap_)"
  "Scripting","Groovy_, Python_"
  "Documentation","HTML"
  "Web","HTTP, FTP, SFTP, SSH, Email, `Webservices <CXF_>`_, rsync_"
  "Other","de/-compression (tar, zip, bzip2, gzip, lzma, xz, zstd), Java code generation"

.. _WEKA: http://www.cs.waikato.ac.nz/ml/weka/ 
.. _MOA: http://moa.cms.waikato.ac.nz/
.. _MEKA: http://meka.sourceforge.net/
.. _R: http://www.r-project.org/
.. _ODF: http://en.wikipedia.org/wiki/OpenDocument
.. _Gnumeric: http://www.gnumeric.org/
.. _Matlab: https://www.mathworks.com/help/pdf_doc/matlab/matfile_format.pdf
.. _Twitter: http://twitter4j.org/
.. _MSAccess: http://jackcess.sourceforge.net/
.. _MySQL: http://www.mysql.com/
.. _PostgreSQL: https://www.postgresql.org/
.. _HSQL: http://hsqldb.org/
.. _MSSQL: https://en.wikipedia.org/wiki/Microsoft_SQL_Server
.. _Sybase: https://en.wikipedia.org/wiki/Adaptive_Server_Enterprise
.. _SQLite: https://sqlite.org/
.. _JDBC: https://en.wikipedia.org/wiki/Java_Database_Connectivity
.. _JAI: http://en.wikipedia.org/wiki/Java_Advanced_Imaging
.. _BoofCV: http://boofcv.org/
.. _Gnuplot: http://gnuplot.info/
.. _LIRE: http://code.google.com/p/lire/
.. _tesseract: https://code.google.com/p/tesseract-ocr/
.. _Zxing: https://github.com/zxing/zxing
.. _OpenStreetMap: http://www.openstreetmap.org/
.. _Groovy: http://groovy.codehaus.org/
.. _Python: http://python.org/
.. _CXF: http://cxf.apache.org/
.. _rsync: https://github.com/fracpete/rsync4j
.. _OpenCV: https://github.com/bytedeco/javacv
.. _Redis: https://redis.io/


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
