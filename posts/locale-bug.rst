.. title: locale bug
.. slug: locale-bug
.. date: 2014-09-16 16:10:41 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

Last Friday, I fixed a bug in regards to how float/double are handled 
in the GenericObjectEditor. The bug was introduced with the locale 
handling after release 0.4.2. In non-English locales, or more general, 
ones that use a comma as the decimal point, numbers like 4.25 got 
interpreted incorrectly as 425 in the GUI. Simply executing existing 
flows doesn't result in any data corruption. However, bringing up 
options in the GUI and then saving them again may result in incorrect 
values being saved. It is therefore recommended to either set the 
locale to en_US in the preferences dialog or download a current 
snapshot to avoid this issue. 

Sorry about that. 
