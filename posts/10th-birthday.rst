.. title: 10th Birthday
.. slug: 10th-birthday
.. date: 2019-07-17 10:37:00 UTC+12:00
.. tags: 
.. status: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

Happy birthday!
===============

Today marks 10 years since the first code was committed to the ADAMS repository
(back then still stored in an in-house subversion repository)!

Back then, ADAMS wasn't yet a standalone project, but merely the common code
base between a project for processing `GC-MS <https://en.wikipedia.org/wiki/Gas_chromatography%E2%80%93mass_spectrometry>`__ 
data and one for processing `NIR <https://en.wikipedia.org/wiki/Near-infrared_spectroscopy>`__ data.
The GC-MS research project never really took off, but the NIR one (whic started 
off as an unofficial side-project) was successfully turned into a commercial application.
The code-based for this offshoot project was migrated to ADAMS data structures
again over the last few years and a new version for processing NIR data has been
successfully launched this year at `Eurofins Agro <https://www.eurofins.com/agro>`__ in 
the Netherlands and `Ravensdown/ARL <https://www.ravensdown.co.nz/services/testing>`__
here in New Zealand.

Recently, we embarked on better integrating deeplearning frameworks, such as `Keras <https://keras.io/>`__.
These frameworks can (in theory) now be used as a regular Weka classifier thanks to
the `Pyro4 <https://github.com/irmen/Pyro4>`__ library which we use for exchanging data. 
You only need to implement the Pyhton side of things for parsing the data and making use
of it (predictions and/or training). This opens up doors for models that work better on 
certain domains, like data fusion, and still being able to integrate them with all the 
functionality within ADAMS.

**Exciting times ahead!**


Flow editor
-----------

The Flow editor, the heart of ADAMS, goes back further than the initial commit, has seen a constant
evolution of features and appearance. But one thing that has never changed: never uses
explicit connections between operators (or actors in ADAMS terms). It is more of a
graphic programming language than other workflow engines, with flow control, variables
and internal data storage. You could say that it is `Scratch <https://scratch.mit.edu/>`__
**for Data Scientists**. It leaves out the nitty-gritty details of the underlying APIs involved
and allows you to concentrate on rapidly developing machine learning and data processing 
applications, which you can then deploy as Linux daemons or Windows services.

Flow editor from the (internal) 0.2.0 release (June 2011)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

This version only allowed a single flow to be edited and
only offered the list of actors as side panel.

.. thumbnail:: /galleries/floweditor/0.2.0.png


Flow editor from the 18.12.0 release (Dec 2018)
+++++++++++++++++++++++++++++++++++++++++++++++

Much has happened since then, multiple open flows, 
various context-sensitive tabs, locating of variables
and storage items, much improved context-sensitive 
menus and object editor.

.. thumbnail:: /galleries/floweditor/18.12.0.png


Powerful tools
--------------

Over the years, ADAMS has added its own set of tools to better support the users in their tasks. 
Below are some of them:


Weka Investigator
+++++++++++++++++

The *Weka Investigator* is a much more powerful tool than the vanilla Weka
Explorer. It allows you to manage multiple sessions in one interface and each
session can manage multiple files and multiple tabs for the same operation
(e.g., classification). It allows you to predefine various outputs for
evaluations (rather than manually requesting them via popup menus) and you can
also compare them side by side.

.. thumbnail:: /galleries/screenshots/weka_investigator.png


Preview browser
+++++++++++++++

The *Preview browser* allows you to browse a directory and quickly display file
content with various handlers.  Inspect Weka models? Check! Display annotations
for images?  Check! Many more file types are supported.

.. thumbnail:: /galleries/screenshots/previewbrowser-default.png


Spreadsheet file viewer
+++++++++++++++++++++++

A built-in spreadsheet application that can handle many different types of file
formats (depending on modules): CSV, fixed tabular, Gnumeric, ODF, MS Excel, ...

.. thumbnail:: /galleries/screenshots/spreadsheet_file_viewer.png


Spreadsheet processor
+++++++++++++++++++++

You are performing the same operation on several spreadsheets
all the time? You might want to check out the *Spreadsheet processor*,
which allows you to extract, transform and load spreadsheets of 
various types.

.. thumbnail:: /galleries/screenshots/spreadsheet-processor.png


SQL Workbench
+++++++++++++

Need to work with databases then you can use the *SQL Workbench*
to connect to (theoretically) any database via JDBC and retrieve
data from it.

.. thumbnail:: /galleries/screenshots/sqlworkbench.png


File commander
++++++++++++++

Need a file manager that can handle 10s of thousands of files
and doesn't need minutes to display them (like the Windows File 
Explorer) but mere seconds? Need to copy things from/to remote servers?
Then the *File commander* tool might be for you. It sports a two-panel
layout with optional filtering, that was inspired by similar tools
(`Norton Commander <https://en.wikipedia.org/wiki/Norton_Commander>`__, 
`Midnight Commander <https://en.wikipedia.org/wiki/Midnight_Commander>`__, 
`Double Commander <https://en.wikipedia.org/wiki/Double_Commander>`__).

.. thumbnail:: /galleries/screenshots/filecommander.png


Spectrum Explorer
+++++++++++++++++

For exploring spectral like NIR (near infrared), MIR (mid infrared),
XRF (x-ray fluorescence), you can use the *Spectrum explorer*.
It allows you to explore and filter the data and also apply PLS or PCA.

.. thumbnail:: /galleries/screenshots/spectrum_explorer.png


3-way Heatmap Viewer
++++++++++++++++++++

For multi-dimensional spectra, like 3D fluorescence spectra, you
can use the *3-way heatmap viewer*.

.. thumbnail:: /galleries/screenshots/3way_heatmap_viewer.png


