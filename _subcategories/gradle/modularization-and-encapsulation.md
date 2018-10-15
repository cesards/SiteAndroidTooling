# Modularization & Encapsulation

## Table of contents



[Source](https://blog.gradle.org/java-9-support-update) [Source](https://docs.gradle.org/current/userguide/java_library_plugin.html)

Achieving encapsulation with the Java Library Plugin
One of the 2 major goals of the Java 9 module system is to provide better software architecture through strong encapsulation. Gradle 3.4 introduced the Java Library Plugin that enforces strong encapsulation for libraries by separating api dependencies (those meant to be exposed to consumers) from implementation dependencies whose internals are not leaked to consumers.

This, of course, does not eliminate use of Java classpaths as is stated as another goal of Java modules. You can learn about the motivation and usage of the Java Library Plugin in this post. It’s worth noting that the Java Library Plugin is useful for projects using Java 7 and above — you do not need to migrate to Java 9 to have some stronger encapsulation.

runtimeOnly project(':bears')????? what is runtimeOnly for?

concept of an API exposed to consumers. A library is a Java component meant to be consumed by other components. It’s a very common use case in multi-project builds, but also as soon as you have external dependencies.

The plugin exposes two configurations that can be used to declare dependencies: api and implementation. The api configuration should be used to declare dependencies which are exported by the library API, whereas the implementation configuration should be used to declare dependencies which are internal to the component.

```
dependencies {
    api 'commons-httpclient:commons-httpclient:3.1'
    implementation 'org.apache.commons:commons-lang3:3.5'
}
```

Prefer the implementation configuration over api when possible

This keeps the dependencies off of the consumer’s compilation classpath. In addition, the consumers will immediately fail to compile if any implementation types accidentally leak into the public API.

Dependencies appearing in the api configurations will be transitively exposed to consumers of the library, and as such will appear on the compile classpath of consumers. Dependencies found in the implementation configuration will, on the other hand, not be exposed to consumers, and therefore not leak into the consumers' compile classpath. This comes with several benefits:

- dependencies do not leak into the compile classpath of consumers anymore, so you will never accidentally depend on a transitive dependency
- faster compilation thanks to reduced classpath size
- less recompilations when implementation dependencies change: consumers would not need to be recompiled
- cleaner publishing: when used in conjunction with the new maven-publish plugin, Java libraries produce POM files that distinguish exactly between what is required to compile against the library and what is required to use the library at runtime (in other words, don’t mix what is needed to compile the library itself and what is needed to compile against the library).

> The compile configuration still exists but should not be used as it will not offer the guarantees that the api and implementation configurations provide.



**More information about the topic, here:**

- [**building Java 9 modules**](https://guides.gradle.org/building-java-9-modules)
- [**The Java Library Plugin**](https://docs.gradle.org/current/userguide/java_library_plugin.html)