# Skip Tests When Packaging with Maven

## Problem
Running `mvn package` runs all tests, which takes a long time during development builds.

## Solution
Use the `-DskipTests` flag to skip test execution but still compile test classes:
```bash
    mvn package -DskipTests
  ```  
If you want to skip both compiling and running tests, use:

```bash
    mvn package -Dmaven.test.skip=true
```
Why not just ignore tests?
Skipping tests should only be used for quick local builds. In CI/CD pipelines, always run tests to catch regressions.

Permanent configuration (not recommended)
Add to pom.xml:
```xml
<properties>
    <maven.test.skip>true</maven.test.skip>
</properties>
```
But better to keep tests enabled by default and override on command line when needed.

