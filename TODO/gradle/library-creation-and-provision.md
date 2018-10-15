# Library creation & provision

## Table of contents
- Multi-release JARs



## Multi-release JARs

[**Source**](https://blog.gradle.org/mrjars)

With Java 9 came a new feature of the Java runtime called multi-release jars.

Multi-release jars allow you to package several versions of the same class, for consumption by different runtimes. For example, if you run on JDK 8, the Java runtime would use the Java 8 version of the class, but if you run on Java 9, it would use the Java 9 specific implementation. Similarly, if a version is built for the upcoming Java 10 release, then the runtime would use it instead of the Java 9 and default (Java 8) versions.

Use Cases for multi-release JARs:
- Optimized runtime.
- Conflicting APIs.

**More information about the topic, here:**
- [**JEP 238: Multi-Release JAR Files**](http://openjdk.java.net/jeps/238)
- [**Multi-release JARs - Good or bad idea?**](https://blog.gradle.org/mrjars)

## Tooling

- For Gradle plugins, heck the [Available plugins section](#available-plugins.md)
