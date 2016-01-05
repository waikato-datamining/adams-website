.. title: EnterValue interactive actor, simple input dialogs
.. slug: entervalue-interactive-actor-simple-input-dialogs
.. date: 2014-12-04 16:56:15 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text

I've just committed changes to the repository that affect how simple 
input dialogs and the EnterValue source actor now operate. Instead of 
using the JOptionPane.showInputDialog(...) this is now handled via the 
GUIHelper.showInputDialog(...) methods. 

Why this? 

The JOptionPane-based dialogs block the complete application, whereas 
the GUIHelper-based ones only block the current dialog/frame. 

Furthermore, it is now also possible to have an input dialog with 
several options that get displayed as buttons (omitting the OK/Cancel 
buttons altogether) rather than having a dropdown list with the 
options. This can make repetitive interactive actors like the 
EnterValue source much faster. Instead of selecting the desired item 
and then hitting OK, you can simply hit the button associated with the 
desired option. 

Also, these new input dialogs support Esc/Enter for 
cancelling/accepting the current input rather than forcing the user to 
click a button. 

Since this change affected quite a few code locations, let me know if 
you come across some (newly introduced) bugs. 

.. image:: ../../images/entervalue-freetext.png

.. image:: ../../images/entervalue-buttons.png

.. image:: ../../images/entervalue-combobox.png

