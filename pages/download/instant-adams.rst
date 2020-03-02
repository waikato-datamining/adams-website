.. title: Instant ADAMS
.. slug: instant-adams
.. date: 2020-03-03 12:02:0 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

Unlike Weka, ADAMS does not have a package manager. The reason is that we tend to compile
custom applications for our clients (frontend and backend) using automated builds. This
ensures that their workflows never run into the problem of a package being the incorrect
version after an update. For end-users, we therefore provide some custom ADAMS builds,
(e.g., adams-base-all and adams-addons-all), but they may be overkill for some.

To make it easier for end users to get their hands on tailored ADAMS applications, without
having to build ADAMS from code itself, the `Instant ADAMS <https://github.com/waikato-datamining/instant-adams>`__
tool can be used. This command-line tool allows you to build a cross-platform ADAMS
application by simply specifying what modules you want to have and what version (e.g., 
daily build or from a release).

Using `version 0.1.2 <https://github.com/waikato-datamining/instant-adams/releases/download/instant-adams-0.1.2/instant-adams-0.1.2-spring-boot.jar>`__ of the tool, the following Linux command-line generates an ADAMS application
that consists of the modules for Weka, Groovy and Excel (`-M`). Any modules that these ones depend
on get automatically pulled in, i.e., you will never have to specify `adams-core`. As version,
it uses the daily build for March 2020 (`20.3.0-SNAPSHOT`). For a release, you would use, e.g., `20.1.1`.
The option `-o` specifies the output directory and with `-v` you can supply one or more JVM arguments,
in this case to use 1GB for the heap size in the start up scripts. 
The command will generate start up scripts for Linux/Mac and Windows in the `bin` directory.

.. code::

   java -jar instant-adams-0.1.2-spring-boot.jar \
     -C \
     -M adams-weka,adams-groovy,adams-excel \
     -V 20.3.0-SNAPSHOT \
     -o ./out \
     -v -Xmx1g

The same command for Windows:

.. code::

   java -jar instant-adams-0.1.2-spring-boot.jar ^
     -C ^
     -M adams-weka,adams-groovy,adams-excel ^
     -V 20.3.0-SNAPSHOT ^
     -o .\out ^
     -v -Xmx1g

This tool also allows you to generate Debian and Redhat packages, making it
easy to deploy custom ADAMS applications within Docker containers.


**Notes:** 

* The command gets issued from the same directory that contains the
  `instant-adams-0.1.2-spring-boot.jar` library.
* Use `-h` or `--help` to see the full list of options.
