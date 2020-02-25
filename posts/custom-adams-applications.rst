.. title: Custom ADAMS applications
.. slug: custom-adams-applications
.. date: 2020-02-25 12:38:00 UTC+13:00
.. tags: 
.. status: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

For a long time, I have been mulling over on how to make it easier on building
ADAMS applications. Most importantly, without having to write Maven configuration files
and/or requiring compilation. The initial approach (on the ADAMS homepage) was
to let the user select a number of modules and then generate a download with
a complete Maven environment. However, this required that the user not only
had Java installed, but also Maven. Not something your average data scientist
would have readily available.

Enter `bootstrapp <https://github.com/fracpete/bootstrapp>`__, my just released
Java library for bootstrapping Maven applications. With this library, you only 
have to supply the Maven artifacts that should make up the application. It will 
also generate simple start-up scripts for launching the application (Linux/Mac/Windows).

Using this generic approach under the hood, I put together a similar library for ADAMS, 
`instant-adams <https://github.com/waikato-datamining/instant-adams>`__. 
This makes it easy to put together your own, custom applications now, 
with only those modules and libraries that you really need.

The following command-line generates an application using the ADAMS modules
*adams-weka*, *adams-groovy* and *adams-excel*, plus the *kfGroovy* Weka
package:

.. code:: 

   java -jar instant-adams-0.0.1-spring-boot.jar \
     -M adams-weka,adams-groovy,adams-excel \
     -V 20.2.0-SNAPSHOT \
     -d nz.ac.waikato.cms.weka:kfGroovy:1.0.12 \
     -o ./out \
     -v -Xmx1g

In terms of ADAMS version, you can either use the ones from the daily builds
(*Y.M.x-SNAPSHOT*, Y=2-digit year, M=month, x=patch level, usually 0) or ones
from releases (e.g., *20.1.1*). Be aware, only the releases are kept indefinitely,
daily builds are only available for a short number of days (or number of builds).

The above command-line generates scripts which start up ADAMS with 1GB of
heap size (*-v -Xmx1g*).

Please note, since all ADAMS artifacts are managed by one of our inhouse servers and are
not available from `Maven Central <https://search.maven.org/>`__, the library
downloads a `custom Maven configuration file <https://raw.githubusercontent.com/waikato-datamining/adams-website/master/files/resources/settings.xml>`__
behind the scenes to download these artifacts through our server instead. If 
necessary, This can be changed by pointing to a custom Maven user settings file 
using the *-u/--maven_user_settings* option.

Feedback welcome!

