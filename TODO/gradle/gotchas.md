# Gotchas

## Table of contents

- Build problems
- Related sources


## Build problems

If you ever encounter weird build problems related to Gradle, make sure you follow the following steps:
- Restart AS using the “Invalidate Cache” option
Access this in AS from: File\”Invalidate Caches and Restart…”

Delete the system Gradle cache:
Delete this folder:
/<userhome>/.gradle/cache


## Related sources

- [**Fixing Gradle dependency resolution when TLS v1.1 and v1.0 support is discontinued**](https://blog.gradle.org/unable-to-download-maven-central-bintray)



