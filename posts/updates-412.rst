.. title: updates 4/12
.. slug: updates-412
.. date: 2015-12-04 17:34:30 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

Last week, I gave a data mining workshop using ADAMS in Kuching, Malaysia. The
material of the workshop is `available
<https://github.com/fracpete/kuching-2015>`_ from `my github account
<https://github.com/fracpete>`_.

I noticed that Windows is not particular great in regards to displaying unicode
characters (e.g., emoticons). During my workshop we were also covering twitter
sentiment analysis and showing all emoticons as little squares is not a very
useful. My Linux Mint displayed them without any issues, on the other hand.

Thanks to these issues and the workshop, there have been a number of changes:

**Fixes**

* Flow editor: annotations/quick info/input+output menu items in the View menu
  now get correctly updated when switching tabs
* run/run.bat start scripts now specify the correct java-cup jar library in the CLASSPATH
* Flow editor: Parameters tab now displays inline scripts in a more sensible format

**Changes**

* added support for reading/writing flow files (.flow, .flow.gz format) with
  different file encodings (eg UTF-8/16)

**Additions**

* adams-weka: added more string tokenizers and new token cleaner class hierarchy
* adams-core: SwitchedSource actor allows you to output tokens based on boolean
  conditions, similar to the Switch control actor
* adams-video: simple VLC-based video player got added by my student Steven
  Brown - requires VLC to be installed locally
* added dialog for customizing fonts of widgets, e.g., to select more suitable
  font for displaying various unicode characters
* the module adams-nlp has left the incubating stage and got moved to adams-addons

Have a good weekend!
