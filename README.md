gradle-testng-mockito-bootstrap
===============================

A ready-to-use bootstrap Java project backed by gradle, TestNG, Mockito, FEST-Assert 2 and Cobertura for Eclipse.


How to use the bootstrap project
================================

1. Download the bootstrap project as described below.
2. Configure Eclipse (optional).
3. Configure Jenkins CI server (optional).
4. Hack away!


Download
========

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

{% img /blog/uploads/gradle-bootstrap-fork.png Fork the Gradle Bootstrap project on GitHub %}

Then clone (i.e. checkout) your personal fork.

```
$ git clone git://github.com/YOURUSERNAME/gradle-testng-mockito-bootstrap.git
```
<div class="note">
Note: Make sure to replace ``YOURUSERNAME`` in the git URL above with the name of your GitHub user account.
</div>

Now you can start hacking away!

```
$ cd gradle-testng-mockito-bootstrap
# ...start coding...
```


# About the actual Java code in the bootstrap project

The bootstrap project ships with only two classes:

* [BobRoss.java](https://github.com/miguno/gradle-testng-mockito-bootstrap/blob/master/src/main/java/com/miguno/bootstrap/gtm/BobRoss.java)
  -- A simple class that implements a few features that we can write unit tests for.  We pretend to be the late 
  painting instructor [Bob Ross](http://en.wikipedia.org/wiki/Bob_Ross), well, painting a picture with us.
* [BobRossTest.java](https://github.com/miguno/gradle-testng-mockito-bootstrap/blob/master/src/test/java/com/miguno/bootstrap/gtm/BobRossTest.java)
  -- This class tests the former class.  It illustrates the use of TestNG, Mockito and FEST-Assert 2 to write these
  unit tests.  Don't pay too much attention to the semantics of the actual tests, we're just showcasing here.


# Using the command line

The bootstrap project is a normal gradle project.  Have a look at the
[gradle documentation](http://www.gradle.org/documentation) what this allows you to do.  I will only list the most
important commands here.  If you want to see what gradle tasks are available out of the box in the bootstrap project,
run ``gradle tasks``.


```
# General commands
$ gradle clean          # deletes the build directory
$ gradle clean test     # runs the unit tests (and compile before if needed)
$ gradle clean build    # assembles and tests this project

# Eclipse related
$ gradle cleanEclipse   # cleans all Eclipse files
$ gradle eclipse        # generates all Eclipse files
```

By default, executing the commands above will create output in the following locations:

* ``build/`` -- this sub-directory is used by Gradle
* ``build/reports/cobertura/main/coverage.xml`` -- Cobertura test coverage report in XML format
* ``build/reports/tests/testng-results.xml`` -- TestNG Results in XML format
* ``bin/`` -- this sub-directory is used by Eclipse

Feel free to browse the directory tree to find additional files that you might need.


# Configuring Eclipse and/or Jenkins

See [Bootstrapping a Java project with Gradle, TestNG, Mockito and Cobertura for Eclipse and Jenkins](http://www.michael-noll.com/blog/2013/01/25/bootstrapping-a-java-project-with-gradle/) for more information including screenshots.


# Contributing

If you come up with any improvements, feel free send me a pull request.

