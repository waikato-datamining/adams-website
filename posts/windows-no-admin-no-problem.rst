.. title: Windows - No admin, no problem!
.. slug: windows-no-admin-no-problem
.. date: 2024-03-13 11:45:00 UTC+13:00
.. tags: installation, java
.. status:
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

Especially in corporate or institutional environments, users typically don't have any permissions to install software.
Linux users are typically familiar with installing software in their own home directory, but Windows users are often
not aware that this is even possible.

ADAMS itself does not rely on an installer, all you have to do is download a ZIP file (either release or snapshot),
decompress the archive and then you are good to go - as long as you have Java installed on your system.

But what if you shouldn't have Java already on your computer? No problem, you don't need admin rights in order to
get Java on your computer. You can simply download a JDK, decompress the archive and set the `JAVA_HOME` environment
variable to that directory. ADAMS automatically looks for the `JAVA_HOME` environment variable.

JDKs can be downloaded from here:
https://adoptium.net/temurin/releases/

E.g., Java 11 for Windows 64bit (download the zip):
https://adoptium.net/temurin/releases/?variant=openjdk11&os=windows&arch=x64&package=jdk

Or Java 11 for Linux 64bit (download the tar.gz):
https://adoptium.net/temurin/releases/?variant=openjdk11&os=linux&arch=x64&package=jdk

Later LTS (long term support) versions like 17 or 21 should work as well, but you only need 11 as a minimum at the
time of writing.

Setting environment variables under Windows:

* Windows 10: https://www.alphr.com/environment-variables-windows-10/
* Windows 11: https://www.alphr.com/set-environment-variables-windows-11/

If you are running Linux, I presume you know how to manage environment variables via the `export` command in your
`$HOME/.bashrc.` config file :-)

More detailed instructions:

* Download the JDK archive from the above URL
* Decompress the downloaded archive and move the decompress directory into your home directory. At the time of writing,
  you would find a directory called `jdk-11.0.21+9` after decompressing the archive, that is the directory to move.
  E.g., on a Windows machine, I would place simply in my `Documents` directory. On Linux, I could place it straight
  in my home directory.
* Copy the location of this directory onto the clipboard (e.g., for me that would be `C:\Users\fracpete\Documents\jdk-11.0.21+9`)
* Create the `JAVA_HOME` environment variable and set its value to this directory
* Download the ZIP file for the ADAMS version that you want to use (e.g., a shapshot: https://adams.cms.waikato.ac.nz/download/snapshot/)
* Decompress the ADAMS zip file and move the directory in there into your home directory. As a Windows user, this could
  be your `Documents` directory again.

That's it for the setup. You can now start ADAMS via the `start_gui.bat` (Windows) or `start_gui.sh` (Linux) script,
which is located in the `bin` directory of your ADAMS installation.
