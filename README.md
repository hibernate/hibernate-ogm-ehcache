# Hibernate OGM EhCache

*Version: 5.1.0.Final - 01-03-2017*

## Description

[Hibernate OGM](http://hibernate.org/ogm/) stores data in a NoSQL data
grid using the Hibernate ORM engine.

The benefits are fairly obvious:
 - write your model once using well known JPA annotations and select the right NoSQL data grid for your project
 - Hibernate is familiar to many people
 - you end up being able to use all the tools of the Hibernate ecosystem such as Hibernate Search or Hibernate Validator

Checkout <http://hibernate.org/ogm/> for more information.

This projects collection dialects for different datastores coming from contributors.

## Useful pointers

Latest Hibernate OGM Documentation:

 * Reference guide: <https://docs.jboss.org/hibernate/stable/ogm/reference/en-US/html_single/>
 * Additional content: <http://community.jboss.org/en/hibernate/ogm>

Bug Reports:

 * Hibernate JIRA (preferred): <https://hibernate.atlassian.net/projects/OGM/>
 * Mailing list: <hibernate-dev@lists.jboss.org>

Support:

 * The hibernate-ogm tag on Stackoverflow: <http://stackoverflow.com/questions/tagged/hibernate-ogm>
 * Our forum: <https://forum.hibernate.org/viewforum.php?f=31>

## Build instructions

The code is available on GitHub at <https://github.com/hibernate/hibernate-ogm-ehcache>.

To run the full project build including tests for all backends, documentation etc. execute:

    mvn clean install -s settings-example.xml

To speed things up, there are several options for skipping parts of the build.
To run the minimum project build without integration tests, documentation and distribution execute:

    mvn clean install -DskipITs -DskipDocs -DskipDistro -s settings-example.xml

The following sections describe these options in more detail.

### Importing sources in Eclipse

Import the project as any standard Maven project.
This might trigger a dialog to automatically find and install additional m2e plugins: allow that.

Make sure that annotation processing is enabled in your project settings
(see "Properties" - "Maven" - "Annotation Processing",
the setting should be "Automatically configure JDT APT").

### Integration tests

You can skip integration tests by specifying the `skipITs` property:

    mvn clean install -DskipITs -s settings-example.xml

### Documentation

The documentation is built by default as part of the project build.
You can skip it by specifying the `skipDocs` property:

    mvn clean install -DskipDocs -s settings-example.xml

If you just want to build the documentation, run it from the _documentation/manual_ subdirectory.

By default, the following command only builds the HTML version of the documentation:

    mvn clean install -f documentation/manual/pom.xml -s settings-example.xml

If you also wish to generate the PDF version of the documentation,
you need to use the `documentation-pdf` profile:

    mvn clean install -f documentation/manual/pom.xml -s settings-example.xml -Pdocumentation-pdf

### Distribution

The distribution bundle is built by default as part of the project build. You can skip it by specifying the `skipDistro` property:

    mvn clean install -DskipDistro -s settings-example.xml

### Integration tests

Integration tests can be run from the integrationtest module and the default behaviour is to download the WildFly application server,
unpack the modules in it and run the tests using Arquillian.

#### WARNING
Be careful when using on existing installation since the modules used by the build are going to be extracted into the
server you want to run the test, changing the original setup.

## Notes

If you want to contribute, come to the <hibernate-dev@lists.jboss.org> mailing list
or join us on #hibernate-dev on freenode (login required)

This software and its documentation are distributed under the terms of the
FSF Lesser Gnu Public License (see license.txt).
