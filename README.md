Phenkal
=======

Phing build scripts for Drupal projects for use with Jenkins.

This project contains a buil.xml Phing build document that can be used to inspect a Drupal project. The project also comes with two Jenkins templates that can be used to add your project to Jenkins.

Requirements
------------

In order to run this build script you will need jslint installed on the same box as your Jenkins server. Jenkins will also need some plugins in order to run the analysis and process the data.

jslint
  - download linux source from http://www.javascriptlint.com/download.htm
  - tar -xcf jsl.tar.gz
  - cd jsl/src
  - make -f Makefile.ref
  - sudo cp Linux_All_DBG.OBJ/jsl /usr/local/bin/jsl

You will need the following Jenkins plugins installed:

Static Analysis Collector Plug-in (analysis-collector)
Static Analysis Utilities (analysis-core)
Ant Plugin (ant)
Checkstyle Plug-in (checkstyle)
Clover PHP plugin (cloverphp)
Crap4J plugin (crap4j)
Dependency Analyzer Plugin (dependencyanalyzer)
DRY Plug-in (dry)
Git client plugin (git-client)
Git plugin (git)
HTML Publisher plugin (htmlpublisher)
JDepend Plugin (jdepend)
Phing plugin (phing)
Plot plugin (plot)
PMD Plug-in (pmd)
Radiator View Plugin (radiatorviewplugin)
SCM API Plugin (scm-api)
Structs Plugin (structs)
Template Project plugin (template-project)
Violations plugin (violations)
Warnings Plug-in (warnings)
Xunit Plugin (xunit)

Usage
-----

Add this repo to the project you want to inspect. The project expects itself to be in either a "scripts" directory or a ".scripts" directory depending on the flavor of project. The two flavors of Jenkins project currently are "standard" and "flat".
Copy the example.build.properties file and call it build.properties. Change the variables in here to suit you project.
In Jenkins use the appropriate command to setup your project. You will then need to tweak some of the settings to your needs. Note that the project uses git and the default branch used in these templates is "dev".

Jenkins
-------
To create a project using a template do the following.

java -jar jenkins-cli.jar -s http://localhost:9001 create-job anewproject < template.xml

Once you have imported a project you can then set about configuring it. It will contain no references to any codebases or stuff like that so you'll have to add this yourself.

Types of project currently available:

standard.xml
- This is a project that conforms to our current best practices. So the root directory contains a /docroot directory and the phing scripts are kept in a /scripts directory.

flat.xml
- This is a non standard project template that is in use on places like Aberdeen Cloud and some legacy projects.


Filesets
--------

A number of different "filesets" available in the project that are used by the build. These will include or exclude files within the Drupal site.

- exclude_all_javascript
- exclude_all_php
- exclude_custom_drupal_javascript
- exclude_custom_drupal_php
- include_all_javascript
- include_all_php
- include_custom_drupal_javascript
- include_custom_drupal_php


Codesniffer
-----------

When installing codesniffer you'll want to use the correct version for the version of Drupal that you are running.

For Drupal 7 you need to run codesniffer lower than version 2.

    "squizlabs/php_codesniffer": "<2",

For Drupal 8 you need to run codesniffer higher than (or equal to) version 2.

    "squizlabs/php_codesniffer": ">=2",
