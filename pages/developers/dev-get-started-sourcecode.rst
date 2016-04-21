.. title: Get Started - Source code
.. slug: dev-get-started-sourcecode
.. date: 2015-12-18 14:46:52 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

.. contents::


Obtaining the source code
=========================

The ADAMS source code is hosted in the following subversion repository:

`https://svn.cms.waikato.ac.nz/svn/adams/base/trunk/ <base_>`_

You can check out the code ("trunk") in the console with the following command:

.. code:: bash

   svn checkout https://svn.cms.waikato.ac.nz/svn/adams/base/trunk adams

Anonymous access
----------------

The subversion repository allows *public* or *anonymous* read access. 
When performing a checkout, subversion will usually use your user name to 
perform the checkout and ask for a password for this user (in the example 
below, this is *fracpete*). Simply hit *Enter* and when prompted for user
name, use *anonymous* with an empty password.

.. code::

   mymachine:~/tmp>svn checkout https://svn.cms.waikato.ac.nz/svn/adams/base/trunk adams
   Authentication realm: <https://svn.cms.waikato.ac.nz:443> Subversion repository
   Password for 'fracpete': 
   
   Authentication realm: <https://svn.cms.waikato.ac.nz:443> Subversion repository
   Username: anonymous
   Password for 'anonymous': 
   
   A    adams/adams-twitter
   A    adams/adams-twitter/LICENSE.txt
   A    adams/adams-twitter/src
   A    adams/adams-twitter/src/test
   ...


Other modules
-------------

Further modules are available:

* **addons** (less common used):

  `https://svn.cms.waikato.ac.nz/svn/adams/addons/trunk/ <addons_>`_

* **incubator** (experimental):

  `https://svn.cms.waikato.ac.nz/svn/adams/incubator/trunk/ <incubator_>`_

* **spectral-base** (spectral data processing):

  `https://svn.cms.waikato.ac.nz/svn/adams/spectral-base/trunk/ <spectral-base_>`_

* **applications** (domain-specific applications):

  `https://svn.cms.waikato.ac.nz/svn/adams/applications/trunk/ <applications_>`_


Compiling the source code
=========================

ADAMS uses Maven_ as build tool. See the Requirements section for more details
on what you need for compiling the code.

Download the settings.xml_ file and place it in the following directory (if you
are behind a proxy, see section Proxy_ below):

* Linux/Unix/Mac: 

  ``$HOME/.m2``

* Windows: 

  ``%USERPROFILE%\.m2``

You need to set the environment variable ``JAVA_TOOL_OPTIONS`` to
``-Djsse.enableSNIExtension=false`` to avoid the ``Server SSL Error - handshake
alert: unrecognized_name`` error message.

Also recommended, is adding the following parameter to the ``JAVA_TOOL_OPTIONS`` in
order to always get a full strack traces whenever an error occurs:
``-XX:-OmitStackTraceInFastThrow``

You can compile the source code in the console as follows:

.. code:: bash

   mvn clean install

If you want to skip the tests, use the following:

.. code:: bash

   mvn clean install -DskipTests=true

This will generate a ZIP archive in the target directory of the adams-base-all
module that contains all the jars and scripts to start ADAMS and the generated
documentation.


Proxy
=====

If you are behind a proxy, you need to tell Maven about it. Let's assume that
your proxy is called ``proxy.blah.com`` and its port 3128.

If you don't need a password to connect to it, you can add the following tag to
your ``settings.xml`` file:

.. code:: xml

   <proxy>
     <active>true</active>
     <protocol>http</protocol>
     <host>proxy.blah.com</host>
     <port>3128</port>
     <nonProxyHosts>localhost|*.blah.com</nonProxyHosts>
   </proxy>

If your proxy requires a user/password, then you have to **1)** generate a master
password with Maven (which gets stored in your home directory's
``.m2/settings-security.xml`` file) and then **2)** the actual password for the
proxy. The details are explained `here <encryption_>`_ on the Maven
homepage. Once you've created the passwords, you have to add the following
tag to your ``settings.xml`` file and replace the ``USER`` and
``ENCRYPTED_PASSWORD`` placeholders accordingly.

.. code:: xml

   <proxy>
     <active>true</active>
     <protocol>http</protocol>
     <host>proxy.blah.com</host>
     <port>3128</port>
     <username>USER</username>
     <password>{ENCRYPTED_PASSWORD}</password>
     <nonProxyHosts>localhost|*.blah.com</nonProxyHosts>
   </proxy>


.. _base: https://svn.cms.waikato.ac.nz/svn/adams/base/trunk/
.. _addons: https://svn.cms.waikato.ac.nz/svn/adams/addons/trunk/
.. _incubator: https://svn.cms.waikato.ac.nz/svn/adams/incubator/trunk/
.. _spectral-base: https://svn.cms.waikato.ac.nz/svn/adams/spectral-base/trunk/
.. _applications: https://svn.cms.waikato.ac.nz/svn/adams/applications/trunk/
.. _Maven: http://maven.apache.org/
.. _settings.xml: https://adams.cms.waikato.ac.nz/resources/settings.xml
.. _encryption: http://maven.apache.org/guides/mini/guide-encryption.html

