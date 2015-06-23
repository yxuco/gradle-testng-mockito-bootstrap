gradle-testng-mockito-bootstrap
===============================

A ready-to-use bootstrap Java project backed by gradle, TestNG, Mockito, FEST-Assert 2 and Cobertura for Eclipse and IntelliJ IDEA, with support for Jenkins CI.

## Notes added by Yueming
I forked this because it uses a combination of interesting packages useful for continuous delivery.  Unfortunately, a few things do not work on my mac.  Will come back to find fixes when I have a chance.  

# Software used in the bootstrap project

* [Gradle](http://www.gradle.org/) version 1.9 -- build tool
* [TestNG](http://testng.org/) version 6.8.x -- unit testing framework
* [Mockito](http://code.google.com/p/mockito/) version 1.9.x -- mocking framework
* [FEST-Assert 2](https://github.com/alexruiz/fest-assert-2.x) version 2.0M10 -- fluent interface for assertions that
  allows you to write assertions that read more like natural language (unfortunately Java lacks something like the
  awesome [ScalaTest](http://www.scalatest.org/) framework)
* [Cobertura plugin for Gradle](https://github.com/stevesaliman/gradle-cobertura-plugin) -- allows Gradle to generate
  Cobertura compatible test reports (mostly used for integrating test results with Jenkins)

Packages only used for showcasing the functionality:

* [Google Guava](http://code.google.com/p/guava-libraries/) -- solely used to show how compile-time dependencies are
  configured in Gradle

The latest dependency information is always available in
[build.gradle](https://github.com/miguno/gradle-testng-mockito-bootstrap/blob/master/build.gradle).


# What we want to do

We have two complimentary goals:

1. You should be able to use [Eclipse](http://www.eclipse.org/) as the IDE of choice to work with the code (e.g. run
   the build and tests locally on your machine).
2. You should be able to integrate the code with the [Jenkins](http://jenkins-ci.org/) continuous integration server
   (e.g. to let it run the build and tests for your team and publish the test results).

The first goal covers your personal workflow as a software engineer with the code.  The second goal covers integrating
the code with the your engineering team as a whole.


# How to use the bootstrap project

1. Download the bootstrap project as described below.
2. Configure IntelliJ IDEA or Eclipse (optional).
3. Configure Jenkins CI server (optional).
4. Hack away!


# Download

You have the following two options to start your own project with the bootstrap project.


## Option 1: You do not have a GitHub account -- clone the bootstrap project

If you don't have a GitHub account, the simplest way is to just clone (i.e. checkout) the original bootstrap project.
The only requirement is a local installation of [git](http://git-scm.com/) on your machine.

```
$ git clone git://github.com/miguno/gradle-testng-mockito-bootstrap.git
```

Now you can start hacking away!

```
$ cd gradle-testng-mockito-bootstrap
# ...start coding...
```

## Option 2: You do have a GitHub account  -- fork the bootstrap project

If you do have a GitHub account, I recommend that you fork the bootstrap project.  Then start writing your own code
against your personal fork.

First, open the [bootstrap project on GitHub](https://github.com/miguno/gradle-testng-mockito-bootstrap) and fork it.
Then clone (i.e. checkout) your personal fork.

```
$ git clone git@github.com:YOURUSERNAME/gradle-testng-mockito-bootstrap.git
```

_Note: Make sure to replace `YOURUSERNAME` in the git URL above with the name of your GitHub user account._

Now you can start hacking away!

```
$ cd gradle-testng-mockito-bootstrap
# ...start coding...
```


# About the actual Java code in the bootstrap project

The bootstrap project ships with only two classes:

* [BobRoss.java](https://github.com/miguno/gradle-testng-mockito-bootstrap/blob/master/src/main/java/com/miguno/bootstrap/gtm/BobRoss.java)
  -- A simple class that implements a few features that we can write unit tests for.  We pretend to be the late
  painting instructor [Bob Ross](http://en.wikipedia.org/wiki/Bob_Ross) who, well, is painting a picture with us.
* [BobRossTest.java](https://github.com/miguno/gradle-testng-mockito-bootstrap/blob/master/src/test/java/com/miguno/bootstrap/gtm/BobRossTest.java)
  -- This class tests the former class.  It illustrates the use of TestNG, Mockito and FEST-Assert 2 to write these
  unit tests.  Don't pay too much attention to the semantics of the actual tests, we're just showcasing here.


# Using Gradle on the command line


## Command Examples

The bootstrap project is a normal gradle project.  Have a look at the
[gradle documentation](http://www.gradle.org/documentation) what this allows you to do.  I will only list the most
important commands here.  If you want to see what gradle tasks are available out of the box in the bootstrap project,
run `gradle tasks`.


```
# General commands
$ ./gradlew clean          # deletes the build directory
$ ./gradlew test           # runs the unit tests (and compile before if needed)
$ ./gradlew build          # assembles and tests this project
$ ./gradlew cobertura      # generates code coverage report

# Eclipse related
$ ./gradlew cleanEclipse   # cleans all Eclipse files
$ ./gradlew eclipse        # generates all Eclipse files

# IntelliJ IDEA related
$ ./gradlew cleanIdea      # cleans all IntelliJ files
$ ./gradlew idea           # generates all IntelliJ files
```

By default, executing the commands above will create output in the following locations:

* `build/` -- this sub-directory is used by Gradle
* `build/reports/cobertura/coverage.xml` -- Cobertura test coverage report in XML format
    * Jenkins: Add a post-build action _Publish Cobertura Coverage Report_ with "Cobertura xml report pattern" set to
      `**/build/reports/cobertura/coverage.xml`.
* `build/reports/tests/index.html` -- TestNG Results in HTML format
* `build/test-results/*.xml` -- TestNG Results in JUnit XML format
    * Jenkins: Add a post-build action _Publish JUnit test result report_ with "Test report XMLs" set to
      `**/build/test-results/*.xml`.
* `bin/` -- this sub-directory is used by Eclipse

Feel free to browse the directory tree to find additional files that you might need.


# Configuring Eclipse and/or Jenkins

See [Bootstrapping a Java project with Gradle, TestNG, Mockito and Cobertura for Eclipse and Jenkins](http://www.michael-noll.com/blog/2013/01/25/bootstrapping-a-java-project-with-gradle/) for more information including screenshots.


# Contributing

If you come up with any improvements, feel free send me a pull request.

[![githalytics.com alpha](https://cruel-carlota.pagodabox.com/1ac060fa8df0e565fa8bd1a7c9169527 "githalytics.com")](http://githalytics.com/miguno/gradle-testng-mockito-bootstrap)
