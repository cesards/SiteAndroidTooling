# Build performance

(DESCRIPTION)

## Table of contents

- Gradle build cache with Kotlin



## Gradle build cache with Kotlin

[**Source**](https://blog.gradle.org/kotlin-build-cache-use)

You can follow these steps to enable the build cache:

First, you need to ensure you’re using Gradle 4.3 or above, so the Kotlin Gradle Plugin can opt-in to using new APIs in Gradle. You can upgrade Gradle easily using the Gradle wrapper.

Next, we need to ensure we are compiling with Kotlin version 1.2.20 or above. You might have something like this declared in your `buildscript {}` block in build.gradle:

```groovy
dependencies {
    classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:1.2.21"
}
```

Next, we need to tell Gradle to use the build cache. There are 3 ways to do this:

- Enable for the current build using `--build-cache` on the command-line.
- Enable for the project by adding `org.gradle.caching=true` to `$PROJECT_ROOT/gradle.properties`.
- Enable for all builds for the current user by adding `org.gradle.caching=true` to `$GRADLE_HOME/gradle.properties`.

**NOTE: Android developers still need to do this even if android.enableBuildCache=true is set, because Gradle’s build cache is separate from the Android build cache.**

You can also use the Kotlin Annotation Processor (`kapt`) cache by adding to your build:

```groovy
kapt {
    useBuildCache = true
}
```

More information about this, [**here**](https://blog.gradle.org/kotlin-build-cache-use).

**More sources about the topic:**

- [**Build Cache**](https://docs.gradle.org/current/userguide/build_cache.html)
- [**Using the Build Cache**](https://docs.gradle.org/current/userguide/build_cache.html)
