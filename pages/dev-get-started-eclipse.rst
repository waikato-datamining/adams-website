.. title: Get Started - Eclipse
.. slug: dev-get-started-eclipse
.. date: 2015-12-18 14:46:52 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

You can directly import Maven projects in Eclipse_ using the m2e_ plugin. You can
import `this code formatting setup <codeformat_>`_. See the *adams-core*
manual, section *Tools*, subsection *Eclipse* for more details.

In order to start the ADAMS user interface, you need to create a Run
configuration with the following main class:

.. code:: java

   adams.gui.Main

All example flows use the placeholder ``${EXAMPLE_FLOWS}``, which is relative to
the module's path. In order to execute the example flows from module
*adams-weka*, you need to set adams-weka as project in your launcher.


.. _Eclipse: http://www.eclipse.org/
.. _m2e: http://eclipse.org/m2e/
.. _codeformat: https://adams.cms.waikato.ac.nz/resources/eclipse-code-formatting.xml

