.. title: Updates 2018/01/12
.. slug: updates-2018-01-12
.. date: 2018-01-12 15:01:01 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

I hope everyone had a great start to the new year. It's been a busy start
here as there were some major changes in terms of Weka support within ADAMS.

The patched versions of Weka that ADAMS uses, are now available as separate
branches from the following github repository:

`waikato-datamining/weka <https://github.com/waikato-datamining/weka>`__

The *adams-weka* module has been cloned into *adams-weka-stable*, which will
continue to use our patched version of Weka 3.9.0. *adams-weka* will use more 
up-to-date versions of the developer version of Weka from now on, starting with 
a patched version of 3.9.2.

The reason for this split was to be able to offer a stable Weka version to our
commercial clients (not much fun if your serialized models are not compatible
with a newer version and you have to rebuild all your models), but regular 
ADAMS users can still enjoy using the latest version of Weka. The spectral
frameworks will continue to use the 3.9.0 version.

Another change happened, affecting the *start up scripts* for ADAMS. To avoid
collisions with user's local installations of Weka and their respective packages, 
the Launcher class used by the start up scripts now sets a custom *WEKA_HOME* 
environment variable, pointing to a directory below the project's home directory 
($HOME/.adams or %USERPROFILE%\_adams), taking the Weka version into account. 
Once again, this avoids problems with conflicting Weka packages between different versions
of Weka, when using different versions of ADAMS. This approach of separating 
Weka is something that I have used for my `weka-virtualenv <https://github.com/fracpete/weka-virtualenv>`__ 
tool as well.

**Fixes**

* *adams-weka:*

  * Fixed making predictions with the *PLS1* instances analysis algorithm, used by
    the *PLS* supervised filter.


**Changes**

* Added support for LONG to *IncVariable* and *IncStorageValue* transformers.
* It is now possible to define a dialog width for the *EnterManyValues* source actor.
* *adams-weka:* 

  * Upgraded *multisearch-weka-package* to 2017.10.1
  * Upgraded *partialLeastSquares* dependency to 1.0.5

* *adams-groovy:* removed Weka (and related) dependencies.
* *adams-jython:* removed Weka (and related) dependencies.
* *adams-rsync:* upgraded rsync4j to 3.1.2-7


**Additions**

* Added better support for collections with the *NewCollection* source and *CollectionInsert*
  transformer.
* Created copy of *adams-weka* as *adams-weka-stable*, with *adams-weka* now using Weka 3.9.2.
* Created copy of *adams-cntk-weka* as *adams-cntk-weka-stable*, using *adams-weka-stable* dependencies.

