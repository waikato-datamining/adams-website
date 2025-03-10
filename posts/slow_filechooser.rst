.. title: Windows - Slow filechooser
.. slug: windows-slow-filechooser
.. date: 2025-03-11 09:31:00 UTC+13:00
.. tags: windows
.. status:
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

Are you a Windows user trying to open a file from a directory with lots of files in it?

It seems that there has been a regression in OpenJDK since the 11 LTS release that
turns the JFileChooser component unusable for directories with 100s or 1000s of files when
using a Look'n'feel other than the cross-platform one, with the dialog taking several minutes
to appear.

Here is a Github issue describing the problem:

`https://github.com/JFormDesigner/FlatLaf/issues/953 <https://github.com/JFormDesigner/FlatLaf/issues/953>`__

Up till recently, ADAMS only used the cross-platform one, but switched to `Flatlaf <https://github.com/JFormDesigner/FlatLaf>`__
for its sleek, modern look. Currently, we are waiting for the 3.6 release of the FlatLaf Look'n'feel
to be made available, which addresses this issue for Windows users.

In the meantime, you can switch to the cross-platform Look'n'feel from the main menu as follows:

**Program > Look'n'feel > Cross-platform**

And then restart ADAMS for the changes to take effect.
