.. title: "Roll your own"
.. slug: roll-your-own
.. date: 2015-12-18 14:46:33 UTC+13:00
.. tags: 
.. category: 
.. link: 
.. description: 
.. type: text
.. author: FracPete

.. contents::

This page allows you to generate a custom Maven_ setup of ADAMS, with the
specific version and modules that you select, for generating your own ADAMS
distribution.

Check out the `Get started <link://slug/dev-get-started>`__ section for
Developers for more information on requirements and configurations for
compiling ADAMS.

.. _Maven: http://maven.apache.org/

.. raw:: html

   <form class="form">

Project name
============

**First**, choose a name for your project:

.. raw:: html

   <p><input id="project" name="inputproject" type="text" value="MyAdams"/></p>


Build environment
=================

**Second**, download the `zip archive <srczip_>`__ containing the skeleton
build environment.

Unzip it on your machine in the location where you want to build your ADAMS
project.

.. _srczip: https://adams.cms.waikato.ac.nz/resources/rollyourown/source/src.zip


Version
=======

.. raw:: html

   <script type="text/javascript">
     // updates the modules selection tag based on selected version
     function update_modules() {
       var version = document.getElementById("selversion");
       if (version.value.length > 0) {
         $.get('/resources/rollyourown/modules/' + version.value + '.txt', function(data) {
             $('#fragmentmodules').empty();
             $('#fragmentmodules').append('<select id="selmodules" name="fragmentmodules" multiple="yes" size="10">');
             var lines = data.split("\n");
             $.each(lines, function(index, value) {
               if (value.length > 0) {
                 $('#selmodules').append('<option value="' + value + '">' + value + '</option>');
               }
             });
         }, 'text');
       }
     }
     // returns all currently selected modules
     function get_modules() {
       var result = new Array();
       var modules = document.getElementById('selmodules');
       if (modules != null) {
         for (i = 0; i < modules.options.length; i++) {
           if (modules.options[i].selected) {
             result[result.length] = modules.options[i].value;
           }
         }
       }
       return result;
     }
   </script>

**Third**, select the version that you want to use as basis (``-SNAPSHOT`` is the
version under development):

.. raw:: html

   <select id="selversion" name="version" onchange="update_modules();">
     <option value="" selected="yes">Please select</option>
     <script type="text/javascript">
       var versions = ['0.4.13-SNAPSHOT', '0.4.12', '0.4.11', '0.4.10', '0.4.9', '0.4.8', '0.4.7', '0.4.6', '0.4.5', '0.4.4', '0.4.3', '0.4.2', '0.4.1', '0.4.0']
       for (i = 0; i < versions.length; i++) {
         document.write('<option value="' + versions[i] + '">' + versions[i] + "</option>");
       }
     </script>
   </select>


Modules
=======

**Fourth**, select the modules to include (*adams-core* is included automatically):

.. raw:: html

   <span id="fragmentmodules">
   <p><em>[Once you select a version, the list of modules will appear here.]</em></p>
   </span>


Build setup
===========

**Fifth**, click on *Generate* once you are happy with the setup.

.. raw:: html

   <script type="text/javascript">
     function generate(e) {
       e.preventDefault();
       $.get('/resources/rollyourown/source/pom.xml', function(data) {
         // version
         var version = document.getElementById("version");
         var result = data.toString();
         result = result.replace(/{VERSION}/g, version.value);
         // project
         var project = document.getElementById("project");
         result = result.replace(/{PROJECT}/g, project.value);
         // modules
         var modules = get_modules();
         var dep = "";
         for (i = 0; i < modules.length; i++) {
           if (modules[i].length > 0) {
             dep += "\n";
             dep += "    <dependency>\n";
             dep += "      <groupId>nz.ac.waikato.cms.adams</groupId>\n";
             dep += "      <artifactId>" + modules[i] + "</artifactId>\n";
             dep += "      <version>" + version.value + "</version>\n";
             dep += "    </dependency>\n";
           }
         }
         result = result.toString().replace(/{MODULES}/g, dep);
         var base64 = $.base64.encode(result);
         $('#download').empty();
         $('#download').append('<p><a href="data:text/octet-stream;base64,' + base64 + '">Download &#187;pom.xml&#171;</a></p>');
       }, 'text');
       return false;
     }
   </script>
   <input id="generate" type="submit" value="Generate"/>
   <script type="text/javascript">
     $('#generate').click(function (e) {
       generate(e);
     });
   </script>


Download
========

**Sixth**, click on the download link below and save the generated build setup file
as *pom.xml* in the directory where you extracted the build environment to (in
the same directory as the *LICENSE.txt* file).

.. raw:: html

   <span id="download">
   <p><em>[Link will appear once a build setup has been generated.]</em></p>
   </span>

   </form>

