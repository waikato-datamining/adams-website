.. title: Jython and MS Access
.. slug: jython-and-ms-access
.. date: 2015-01-23 16:39:17 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

  This week, I submitted more fixes in relation to Jython support in 
  ADAMS. This time, the fix resolved around execution of scripts on the 
  Windows platform. In a nutshell: it didn't work. So far, it had only 
  been used on Linux and Mac. But that's resolved now. 
  Furthermore, I automated the generation of the Jython registry 
  ($HOME/.jython or %USERPROFILE%/.jython), ensuring that the 
  "python.security.respectJavaAccessibility" property is set to "false". 
  Up till now, users had to manually create the registry file, before 
  they could make use of Jython actors. 

  More on the Jython registry here: 

  http://www.jython.org/archive/21/docs/registry.html 

  A new addition is hot off the press today: basic support for reading 
  MS Access (formats 2000 to 2010 supported) tables as spreadsheets. 
  With the next snapshot/release you can then use it in the flow by 
  adding the SpreadSheetFileReader transformer and then choosing the 
  AccessSpreadSheetReader as the actual reader. You only have to feed in 
  the Access database that you want to read from and define the correct 
  table name in the AccessSpreadSheetReader instance. Write access might 
  get added in the future. 

  The Jackcess library is used for interfacing with Access: 

  http://jackcess.sourceforge.net/ 

  Due to the issues with Jython, I will probably make a new release in 
  the coming weeks. 

Write access is now also available, using the AccessSpreadSheetWriter 
plugin for the SpreadSheetFileWriter sink. 

