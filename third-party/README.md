Plovr Dependencies
===========================

The BUCK build file in this directory is autogenerated from pom.xml.

To update `closure-compiler` or `closure-templates`, first install Maven.
Then update the maven version in the pom.xml. Then run:

```
mvn de.evosec:export-dependencies-maven-plugin:buck
```

Maven will resolve all the transitive dependencies and write the output to `target/BUCK`.
Manually inspect the file and copy it over the BUCK file in this dir.

Extra Steps for Closure Templates
---------------------------------

Closure Templates relies on a small JS support library [soyutils_usegoog.js](javascript/soyutils_usegoog.js).

You need to manually build this by checking out the Closure Templates repo, running `mvn install`, and
copying the computed file into this repo. I wish there was a better way to do this.

Extra Steps for Closure Compiler
--------------------------------

To test Closure Compiler's custom-externs-only option, we copy the externs from the Closure Compiler repo
into the [externs](externs) directory.

This is only used for testing. You only need to worry about this step if the tests don't pass and you're
getting weird errors about externs.