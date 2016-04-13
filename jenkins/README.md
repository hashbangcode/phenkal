To extract a template from an existing project do the following.
java -jar jenkins-cli.jar -s http://localhost:9001/ get-job anexistingproject > template.xml

This will contain a bunch of config stuff you might not want to it's important to reivew it after you create it.


To create a project using a tempalte do the following.

java -jar jenkins-cli.jar -s http://localhost:9001 create-job anewproject < template.xml

Once you have imported a project you can then set about configuring it. It will contain no references to any codebases or stuff like that so you'll have to add this yourself.


Types of project currently available:

standard.xml
- This is a project that conforms to our current best practices. So the root directory contains a /docroot directory and the phing scripts are kept in a /scripts directory.

flat.xml
- This is a non standard project template that is in use on places like Aberdeen Cloud and some legacy projects.
