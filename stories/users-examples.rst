.. title: Examples
.. slug: users-examples
.. date: 2015-12-18 14:47:22 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

.. contents::

**Note:** the videos should only be considered educational, as some of the
concepts in ADAMS have changed over time. E.g., *global* actors are now called
*callable*, since they can appear in different scopes within the flow. Also,
*SingleFileSupplier* and *MultiFileSupplier* got merged into the *FileSupplier*
actor.


Basic
=====

Workflows don't have to be complex to get the job done. But even flows with
only 10 actors already help documenting your work, preserving all steps in
volved in generating the results. These flows are a good introduction into the
many actors that ADAMS already has on offer.

Hello world flow
----------------

Absolute simple flow that merely displays the **Hello World** string.

.. media:: https://www.youtube.com/watch?v=FRNQhPSHJ1I


Cross-validating a single classifier on one dataset
---------------------------------------------------

Cross-validates a classifier (J48) on a single UCI dataset.

.. media:: https://www.youtube.com/watch?v=56Y97zIWsow


Dynamic evaluation of multiple classifiers on multiple datasets
---------------------------------------------------------------

Reads in set ups of WEKA classifiers stored in a text file and evaluates each
against all datasets in a directory.

.. image:: ../images/multiple_classifiers_on_multiple_datasets.png
   :scale: 100 %

1. Read in text file with classifier set ups, line by line, and store set up in
   in variable attached to the global actor (see 5)
2. Iterate over all datasets in directory and load them, one after the other
3. Drop datasets that don't meet required capabilities
4. Cross-validate classifier defined in 5 on datasets and output results
5. The classifier definition used in cross-validation, with variable attached
   to set up (gets updated when the variable changes its value)


Experiment on arbitrary datasets
--------------------------------

Adds datasets located in a directory to a pre-defined WEKA experiment, runs the
experiment and displays the evaluation.

.. image:: ../images/weka_experiment.png

1. Lists datasets in specified directory
2. Executes the pre-defined WEKA experiment (containing only classifier set
   ups, no datasets) using the datasets arriving at its input
3. Performs the evaluation of the experiment


Classifier ranking of parameter sweep
-------------------------------------

Generates a parameter sweep for multiple parameters of WEKA classifiers, ranks
these using 2-fold cross-validation and subjects the top 3 to a proper
evaluation.

.. image:: ../images/classifier_ranking.png

1. Generates the parameter sweep of 3 parameters: ridge of LinearRegression, #
   of components of PLS filter and type of PLS algorithm
2. Outputs all the generated setups
3. Ranks the performance of the classifiers using 2-fold cross-validation,
   outputs the top 3
4. Displays the set ups of the top 3 classifiers
5. The global training data


Visualization
=============

A picture says more than a thousand words. This is even more so true for
statistics. Visualizing results, generating plots from data is an integral part
of ADAMS. Check out what ADAMS can do in the visual department.


Learning curve for a WEKA classifier
------------------------------------

Generates and visualizes a learning curve for J48, a non-incremental WEKA
classifier. The classifier gets trained every 25 instances and evaluated
against test set and Accuracy, RMSE and AUC gets plotted in one plot.

.. image:: ../images/learning_curve.png

1. Read in dataset incrementally and buffer incoming data
2. Every 25 instances, build classifier and evaluate against test set (defined
   as global actor, see 6)
3. Obtain accuracy and create a plot container for Accuracy plot sequence
4. Get root mean squared error and turn it into a plot container as well, this
   time for the RMSE sequence
5. Retrieve AUC (area under curve) statistics and generate plot container for
   AUC sequence.
6. Sequence of actors for reading in a test set
7. The plot for all three statistics

.. media:: https://www.youtube.com/watch?v=Bq2oAhD3qL8 


Visualization of seismic data
-----------------------------

Seismic data was retrieved using the Geonet client.

.. image:: ../images/geonet1.png

1. Read text file, line by line
2. Extract Unix timestamp, convert into double and store as variable
3. Extract amplitude, convert into double and store as variable
4. Turn timestamp and amplitude into a double array
5. Generate data structure for plot
6. The global plot

.. media:: https://www.youtube.com/watch?v=HP4wvUnUPCY


Email alerts for seismic events
-------------------------------

Seismic data was retrieved using the `Geonet client <geonet_>`__. Apart from
visualizing the data, this flow also sends out an email alert if a tremor
exceeds a certain strength.

.. image:: ../images/geonet2.png

1. Read text file, line by line
2. Extract Unix timestamp, convert into double and store as variable
3. Convert timestamp into human-readable representation for email
4. Extract amplitude, convert into double and store as variable
5. Check whether incoming token (amplitude) is larger than threshold and email
   hasn't been sent yet
6. Note that email was sent and send email with information about event (time/date and amplitude)
7. Turn timestamp and amplitude into a double array
8. Generate data structure for plot
9. The global plot

.. media:: https://www.youtube.com/watch?v=vdN9Uxson5o


LEIA - visualizing bridge sensor data
-------------------------------------

Visualizing sensor data of the InfraWatch project using the LEIA/ADAMS framework:

Bridge vibration
++++++++++++++++

Illustration of sensor data processing with the ADAMS/LEIA workflow engine.

.. media:: https://www.youtube.com/watch?v=zxReYlFjTbc


Vehicle detection
+++++++++++++++++

Demonstration of the ADAMS/LEIA workflow engine on traffic sensor data.

.. media:: https://www.youtube.com/watch?v=C32npFLSaug


**Publication**

Knobbe, A., Blockeel, H., Koopman, A., Calders, T., Obladen, B., Bosma, C.,
Galenkamp, H., Koenders, E., and Kok, J.: InfraWatch: Data Management of
Large Systems for Monitoring Infrastructural Performance. IDA Proceedings
(2010). [`pdf <infrawatch_>`__]


Time series
===========

ADAMS' efficient token-passing architecture makes it ideal to handle streams of
data. It is also very easy to extend. In these examples, we introduce new
actors for several signal analysis techniques, and show how we can quickly
build and test workflows to analyse time series data.

Convolution - Finding the signal in the noise
---------------------------------------------

Sensor data is often noisy and complex. Here, we introduce an actor for
convolution_, an operation that transforms the data into something more useful.

Smoothing
+++++++++

First, we convolute the signal with a Gaussian response function (or kernel) to
obtain a much cleaner signal.

.. image:: ../images/gaussian.png

1. Retrieve data files from the given folder. Emits the files as tokens.
2. Load and interpret the files and emit [timestamp,sensorvalue] tokens for
   every new timestamp.
3. Branch actor: each token is sent to three subflows for further processing.
4. This branch simply plots the data. Timestamp and sensor value are mapped
   straight to an X and Y coordinate, [X:timestamp,Y:sensorvalue], then sent to
   the plotter.
5. Visualize the used kernel (here, a Gaussian kernel). Emits values to plot
   the kernel, centered on the received timestamp.
6. Convolute the received data with the kernel. The agent buffers the last N
   tokens (N=kernel width), and emits the convoluted data points.
7. Global plotter for all data. Receives tokens sent to all GlobalSink actors
   linked to it.

.. media:: https://www.youtube.com/watch?v=D0F-NPerCIE


Smoothing at different levels
+++++++++++++++++++++++++++++

Changing the width of the kernel allows us to focus on events occurring on
different time scales. Simply copy-paste the last two branches and change the
kernel widths.

.. image:: ../images/gaussiandouble.png

.. raw:: html

   <br/>

.. media:: https://www.youtube.com/watch?v=9QYYzh-VLeQ


Scale-space composition
+++++++++++++++++++++++

Convoluting the same signal with a whole range of different kernel widths
creates a so-called scale space, a space of signals sensitive to events at
different time scales.

.. image:: ../images/scalespace.png

1. Copy-paste the convolution branches
2. Increase the kernel width. Here, we double it each time

.. media:: https://www.youtube.com/watch?v=-sIgbedKxVo

Scale-space decomposition
+++++++++++++++++++++++++

Decomposition of a sensor signal into components displaying events occurring on
different time scales. Detecting transient events when these events occur on
different timescales in data prone to baseline shifts can be very tricky.
Through scale-space decomposition, we decompose the raw signal into its natural
components, and use those to detect events. This is done by taking the scale
space and establishing 'regions' of the scale space where events of a certain
time scale take place. Each region will be represented by a component,
calculated by substracting the convolutions at either end of the region.
The latter is also known as a 'difference of Gaussians' filter, or
band-pass filter. The sum of the components recreates the original signal.

.. image:: ../images/decomposition.png

1. Sensor data is read and split into individual tokens as before
2. The data is subsampled: only every 100th token is passed on
3. The baseline of the data is created through convolution with a large
   Gaussian, only sensitive to large-scale events
4. The first band-pass filter is applied. It takes the difference of the
   Gaussians of width 64 and 16. The result is sent to the plotter
5. Second band-pass filter, for signals in the range sigma=[4,16]
6. Third band-pass filter, for signals in the range sigma=[0,4]

.. media:: https://www.youtube.com/watch?v=7eEjwX_5K8k


Segmentation of time series data
--------------------------------

A time series can be approximated by a piecewise linear function. This will
result in a time series that is significantly smaller in size (disk space), and
thus easier to store and process.

Segmentation through convolution
++++++++++++++++++++++++++++++++

One way of approximating the signal is to begin a new line segment if the
signal changes it's slope drastically. These points can be found by taking the
1st, 2nd, 3rd,... order derivative of the signal and start a new line segment
for every zero-crossing of these derivatives. Instead of first calculating the
convolution of a signal and then taking its derivative, we can achieve the same
result by convoluting the signal with the derivative of the kernel used for
convolution! Thus, we take the 1st, 2nd, 3rd,... order derivative of the
Gaussian kernel, do their convolutions, and start a new line segment at any
zero-crossings.

.. image:: ../images/segmentation.png

1. Load and split the data into tokens as before
2. Plot the raw sensor data
3. Compute the third order derivative of the convolution and normalize it
   between -1 and 1 (for nicer plotting)
4. Compute the second order derivative of the convolution and normalize it
   between -1 and 1
5. Compute the first order derivative of the convolution and normalize it between -1 and 1
6. The segmentation agent does the same as the above three branches, but only
   lets through a token (unaltered) if one of the derivates crosses zero
7. Compute and plot the convolution with the base Gaussion kernel
8. The plotter collects and plots all received tokens

.. media:: https://www.youtube.com/watch?v=Px82ohXmJO4

Discrete Fourier Transform of sensor data
-----------------------------------------

Applying DFT
++++++++++++

Applying discrete fourier transformation to the sensor data and displaying the
frequency domain.

.. image:: ../images/fft.png

1. Select the FFT Conversion in the Convert actor.

.. media:: https://www.youtube.com/watch?v=9QYYzh-VLeQ

Advanced
========

Large, complex flows that's where ADAMS' strength really lies. Its compact
layout helps you not to lose the overview. Use loops, internal storage and much
more to create solutions to your problems.

Pixel classification
--------------------

Performs pixel area classification (background or object) with a WEKA
classifier trained on regions selected by the user.

.. image:: ../images/pixel-selector.png

1. Parameter initialization
2. Loading and pre-processing of image, storing in internal storage for future retrieval
3. Extract image height and store it in a variable
4. Extract and store image width in variable as well
5. Interacting with the user, choosing pixel regions used as traingin data
6. Generate training data for WEKA classifier
7. Keep track of number of training instances
8. Cross-validate (and output results) on training data only if there are at
   least 10 instances in the data
9. Train the classifier, stored model on disk for future use and in the
   internal storage as well for performing the classification task
10. Outer loop for traversing X (every 3rd pixel)
11. Inner loop for traversing Y (every 3rd pixel as well)
12. Extract pixel region around current X and Y, turn into a WEKA instance and
    make prediction
13. Choose the color for background or object classification
14. Update the pixel at the current position
15. Display the modified image

.. media:: https://www.youtube.com/watch?v=cuop0RAG35w


Sample type checker
-------------------

Using the GC-MS extension modules, this flow performs a check on the sample
type of GC-MS spectra and can send the analyst an email with the results. The
spectra themselves are obtained from fruit and vegetable samples.

.. image:: ../images/sampletypechecker.png

1. Retrieve classification available classification labels
2. List all chromatogram files
3. Load and pre-process chromatograms one-by-one
4. Show Total-ion-count and take a screenshot for report
5. The same with the Baseline-ion-count
6. Turn chromatogram into WEKA instance and predict the class label
7. Determine the fruit/vegetable picture associated with the label
8. Create a spreadsheet from the class distribution (top 5)
9. Generate various output for the PDF report
10. Generate PDF report

.. media:: https://www.youtube.com/watch?v=UWS7cBerBT8

**An application of data mining to fruit and vegetable sample identification
using Gas Chromatography-Mass Spectrometry**

Geoffrey Holmes, Dale Fletcher, and Peter Reutemann (2012). An application of data mining to fruit and vegetable sample identification using Gas Chromatography-Mass Spectrometry. Proceedings of the International Congress on Environmental Modelling and Software (IEMSS), Leizpig, Germany, 2012. [`pdf <samplechecker_>`__]

Spectral analysis
-----------------

Using GC-MS extension modules, this flow processes spectral data generating
predictions for compounds. The user can correct the guessed peaks
interactively, before the concentrations are calculated.

.. image:: ../images/spectralanalysis.png

1. Set up external flows, relative to current one
2. Set up variables for serialized regression model files
3. Prompt user to select spectra
4. Determine extension of currently processed spectrum
5. Prompt user to enter additional parameters
6. Load file, executing subflow depending on file extensions
7. Guess type of compound based on filename and prompt with pre-selected choice
8. Process spectrum, guessing peaks using external flow
9. Prompt user to inspect selected peaks, allow user to correct them
10. Turn spectrum into WEKA data structure and make prediction on peak area for
    all compounds
11. Assemble predictions, display them and copy them to the clipboard as well
    before proceeding with the next data file

.. media:: https://www.youtube.com/watch?v=P6KceexcfZo


Others
======

Miscellaneous videos of various flows.

WEKA webservice
---------------

Using this webservice, any programming language can take advantage of WEKA as
long as it supports SOAP

.. media:: https://www.youtube.com/watch?v=90zhhvfzkWI


Processing data with R
----------------------

Shows how to utilize `R <R_>`__ from within ADAMS

.. media:: https://www.youtube.com/watch?v=E9m1So70fco


Classifier evaluation: from simple to complex
---------------------------------------------

Demonstrates how a flow can evolve from simple to complex

.. media:: https://www.youtube.com/watch?v=bZ85knCw30s


Flow execution listeners
------------------------

With these listeners you can *eavesdrop* on your flow, check out for instance
where most of the CPU time is used or how often actors are executed

.. media:: https://www.youtube.com/watch?v=PpEEdn_vcOs



.. _geonet: http://info.geonet.org.nz/display/appdata/Continuous+Waveform+Buffer
.. _infrawatch: http://infrawatch.liacs.nl/pubs/IDA2010-knobbe.pdf 
.. _convolution: http://en.wikipedia.org/wiki/Convolution
.. _samplechecker: http://www.cms.waikato.ac.nz/~fracpete/publications/2012/iemss2012.pdf
.. _R: http://www.r-project.org/

