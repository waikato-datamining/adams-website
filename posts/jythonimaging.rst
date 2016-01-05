.. title: jython/imaging
.. slug: jythonimaging
.. date: 2015-01-19 16:59:26 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

Unfortunately, the last release has a broken support for Jython inline scripts,
with the input getting rejected. This happened due to the shift to a new editor
component for source code and a left-over cast to the wrong superclass. The
unit tests didn't pick this regression up, as it is a GUI-only problem. Support
for Groovy inline scripts was working as expected in the release. Anyway,
that's fixed now.

On the bright side, there is now support for a range of barcodes available in
the adams-imaging module, thanks to my student Leo Xiong. You can, at the time
of writing, generate EAN13 and QRCode barcodes using the "Barcode" draw
operation (within the "Draw" transformer). 
Decoding is possible as well, even with a bigger range of possible barcodes.
The barcode support is availabel throught the excellent zxing/core library,
which I believe is used by Android as well.

Here is an example:

.. image:: ../../images/qr.png

Using one of the scripting modules (groovy/jython) in conjunction with the pdf
module, you can then easily create PDFs that contain QR codes. For instance for
printing labels.

