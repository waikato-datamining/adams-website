.. title: fixed Weka performance issue
.. slug: fixed-weka-performance-issue
.. date: 2016-01-15 14:24:35 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

This week, I have been mainly working on bugfixes in various frameworks,
website development (including the ADAMS one!) and on my content for the
third MOOC in the Weka MOOC series. Hence it was a bit quieter on
the ADAMS side of things.

**Fixes**

* I took the unusual step of adding a non-release Weka to ADAMS. It is a
  post-3.7.13 release Weka (rev 12311), which fixes the severe performance issue
  that I uncovered the other week when using the setOptions method of Weka
  classes. Several large flows, with lots of Weka classes defined, in one of our
  commercial tools suddenly took more than 10 minutes to load.

**Changes**

* adams-weka: the multi-search-weka-package dependency got upgraded to
  2016.1.15

**Additions**

* the new flow editor tabs *Variables* and *Storage names* allow you to list
  all variables/storage names that are used in the current flow. These tabs
  simply make the ListAllVariables and ListAllStorageNames actor processors
  available in a convenient way.

That's it for this week!

