---
id: gradle
layout: page
title: Gradle
sidebar: true
---

### Table of Contents

- [__Tips__]()
- [__Gradle build performance__](#gradle-build-performance)
  - [__Avoid using dynamic dependencies__](#avoid-using-dynamic-dependencies)
  - [__Enable incremental builds__](#enable-incremental-builds)
  - [__Removing unnecessary flavors__](#removing-unnecessary-flavors)
  - [__Avoid compiling unnecessary resources__](#avoid-compiling-unnecesssary-resources)
  - [__Create library modules__](#create-library-modules)
  - [__Disable PNG crunching__](#disable-png-crunching)
  - [__Avoid legacy multidex__](#avoid-legacy-multidex)
  - [__Enable Build Cache__](#enable-build-cache)
  - [__Enable new DEX Compiler__](#enable-new-dex-compiler)
  - [__Disable Splits (single APK)__](#disable-splits-single-apk)
  - [__More sources__](#more-sources)
- [__Related sources__](#related-sources)

### Tips

- From Gradle 4.8+, you can fetch text resources from URIs, very handy for checkstyle tasks:

```groovy
checkstyle {
    config = resources.text.fromUri("http://company.com/checkstyle-config.xml")
}
```

Gradle will apply the same caching that it does for remote build scripts.

- From Gradle 4.8+, Gradle provides a mechanism for locking dynamic versions.It makes builds reproducible even when declaring dependencies using version ranges.

This enables, amongst others, the following scenarios:

- Companies dealing with multi repositories no longer need to rely on `-SNAPSHOT` or changing dependencies, which sometimes result in cascading failures when a dependency introduces a bug or incompatibility. Now dependencies can be declared against major or minor version range, enabling to test with the latest versions on CI while leveraging locking for stable developer builds.

- Teams that want to always use the latest of their dependencies can use dynamic versions, locking their dependencies only for releases. The release tag will contain the lock files, allowing that build to be fully reproducible when bug fixes need to be developed.

In order to use dependency locking, you first enable it on configurations:

```
dependencyLocking {
    lockAllConfigurations()
}
```

You then run a build, telling Gradle to persist lock state:

```groovy
gradle test --write-locks
```

Assuming you add the lock files to source control, from this point onward, all configurations that have a lock state will resolve the locked versions.

Changes to published dependencies will not impact your build, you will have to re-generate or update the lock before they are considered as dependencies. Similarly, changes to your build script that would impact the resolved set of dependencies will cause it to fail, ensuring the dependencies do not change without a matching update in the lock file.

More information related, [**here**](https://docs.gradle.org/4.8-rc-1/userguide/dependency_locking.html)

- Use `--fail-fast` in your test executions, since it stops Gradle immediately after a test fails. Combined with `--tests`, and `--continuous` makes it more efficient

[**Source**](https://twitter.com/tasomaniac/status/1003597432981245952)


### Gradle bubild performance

#### Use static build config values with your debug build

Always use static/hard-coded values for properties that go in the manifest file or resource files for your debug build type. If the values in your manifest file or your app resources need to update with every build, then Instant Run cannot perform a code swap—it must build and install a new APK.

For example, using dynamic version codes, version names, resources, or any other build logic that changes the manifest file requires a full APK build every time you want to run a change—even though the actual change might otherwise require only a hot swap. If your build configuration requires such dynamic properties, then isolate them to your release build variants and keep the values static for your debug builds, as shown in the build.gradle file below.


It’s quite common to use date as app version code like this:

```
def dateTime = new Date().format("ddMMyyHHmm").toInteger()

android {
    ...
    defaultConfig {
        ...
        versionCode dateTime
    }
}
```
This means that every time you run the app, the AndroidManifest changes and it costs time (2,5 times slower than without changes). What you can do is to use the property that we set before (‘devBuild’). So, if the project has that property, it sets the version code to a static value else, it generates a unique value:
def dateTime = project.hasProperty('devBuild') ? 100 : new Date().format("ddMMyyHHmm").toInteger()

android {
    ...
    defaultConfig {
        ...
        versionCode dateTime
    }
}  

Another important thing you have to take care is Fabric. Fabric by default generates a unique build id on every build. Fortunately you can disable it on your build.gradle:

android {
    ...
    buildTypes {
        debug {
        	ext.alwaysUpdateBuildId = false
        	...
        }
    }
}  

There is also a flag to disable crashlytics all together. You can think to use that as well.

android {
    ...
    buildTypes {
        debug {
        	ext.enableCrashlytics = false
        	...
        }
    }
}

But you also need to disable Crashlytics initialisation

Crashlytics crashlyticsKit = new Crashlytics.Builder()
    .core(new CrashlyticsCore.Builder().disabled(BuildConfig.DEBUG).build())
    .build();

Fabric.with(this, crashlyticsKit);

To be honest I had to do the opposite test here because the project already had a static versionCode and I have never used a date for it. The difference was impressive.. 27 seconds more.



#### Avoid using dynamic dependencies

The clearest case scenario of a bad performance on a build is using dynamic dependencies, like the sample below:

```groovy
implement com.google.dagger:dagger-compiler:2.*
```

Which makes Gradle checking for a new library version every day, so the build becomes non-deterministic, increasing the build times for the Gradle project. Instead, we should be using the desired versioning:

```groovy
implement com.google.dagger:dagger-compiler:2.11
```

That said, using dynamic dependencies is a really bad thing because we could be breaking our project every time to time due to breaking changes in our dependencies.

#### Enable incremental builds

[__Source__](https://youtu.be/rvwAlbtbtmM?t=1721)

- By default on Gradle 3.0+?
- Allow Gradle already compiled resources to make builds faster.
- It only compiles only those java classes that were changed for that are dependencies to the changed classes.
- Libraries such as AutoValue, Glide, Butterknife or Dagger, that use annotation processing, disable incremental builds.

```java
tasks.withType(JavaCompile) {
  // JavaCompile with incremental builds and forking.
  options.incremental = true
  options.fork = true
  doFirst {
    // JavaCompile tasks will print annotation processors.
    println "Task ${path} annotation processors: ${effectiveAnnotationProcessorPath.asPath}"
  }
}
```

#### Removing unnecessary flavors

[__Source__](https://youtu.be/rvwAlbtbtmM?t=2029)

The more flavors we have, the more inneficient:

```groovy
android {
  buildTypes {
    debug {}
    release {
      minifyEnabled = true
    }
  }

  flavorDimensions "dim"

  productFlavors {
    nightly { dimension "dim" }
    prod { dimension "dim"}
  }
}
```

We can minimize the gradle build time trying to avoid assembbling all the build+flavor combination tasks (we can check how many there are, using the command `gradlew tasks`). To do that, we can use variables in order to "hack" the build. The following build is the same build example as above, with no productFlavors.

```groovy
def isNightly = project.hasProperty("nightly")

android {
  buildTypes {
    debug {
      if (isNightly) {
        minifyEnabled = true
        applicationIdSuffix = ".nightly"
      } else {
        applicationIdSuffix = ".debug"
      }
    }
    release {
      minifyEnabled = true
    }
  }
}
```

Then run `gradlew -Pnightly` for `nightly` builds.

You can also use `android.variantFilter` in order to remove the `nightly` flavor.

```groovy
android {
  buildTypes {
    debug {}
    release {
      minifyEnabled = true
    }
  }

  flavorDimensions "dim"

  productFlavors {
    nightly { dimension "dim" }
    prod { dimension "dim"}
  }

  variantFilter { variant ->
    def names = variant.flavors*.name
    if (names.contains("nightly")) {
      variant.ignore = true
    }
  }
}
```

#### Avoid compiling unnecessary resources

**Update**: From Android Gradle Tools (AGT) 3.2+, you can use `bundle` configuration attribute in order to achieve the same, since the plugin will 


ignore `resConfigs`????? in favour of the new Android App BUndles, the new app packaging.


Use `resConfigs` to **filter out localizations and other resources you don't want to support** in your app.

For example, if you are using a library that includes language resources (such as AppCompat or Google Play Services), then your APK includes all translated languages strings for the messages in those libraries whether the rest of your app is translated to the same language or not. If you'd like to keep only those languages that your app officially supports, you can specify those languages as shown in the sample below. Any resources for languages not specified are removed.

```groovy
android {
  defaultConfig {
    // Keeps language resources for only the locales specified below.
    resConfigs "en", "fr"
  }
}
```

> Note: **Be careful**, as said, "Any resources for languages not specified are removed", which means that whenever we support new languages we should be adding the new language resource to the `resConfigs`, and we could easily forget about it (like adding the Activity to the manifest) and deploy an app we think supports that specific language, but it doesn't.

You can also use this property to filter resources for screen densities. For example, specifying `hdpi` will remove all other screen density resources (such as `mdpi`, `xhdpi` and so on) from the final APK. Gradle, however, **will have fallback in consideration**, so if a resource is not specified in the desired density, it will be backed by a non-filter specific density resource.

A trick here, is defining properties for the most used debugging devices, assigning the known specs as shown in the sample below:

```groovy
android {
  defaultConfig {
    if (project.hasProperty('nexus5')) {
      resConfigs "en", "fr", "xxhdpi", "sw640dp"
    } else if (project.hasProperty('nexus6')) {
      resConfigs "en", "fr", "xxxhdpi", "sw720dp"
    } else {
      resConfigs "en", "fr"
    }
  }
}
```

[**This site**](https://material.io/tools/devices/) can help on figuring out some of those resource values, and [**this site**](https://developer.android.com/guide/topics/resources/providing-resources#AlternativeResources) can help you figuring out what available resource config parameters you can use for `resConfigs`.

Remember to run `gradlew -Pnexus5` or `gradlew -Pnexus6` to enable `resConfigs` for those specific examples.

**Having said all of this, the less resources linked in the `resources.arsc` file, the more impact will have in the build time.**





--------

??? NO TENGO CLARO SI ESTO ESTA RELACIONADO CON LAS CONSTANTES FOR OUR BUILDS

NO CREO QUE ESTO TENGA QUE VER CON LAS BUILDS...





> Note: `resConfigs` values related to non-language resources are not going be recognized by the Android Gradle Tool, so values like 'v21', 'lang' and so on, will be ignored

__We should use constants for our builds__ ????

- Using dynamic variables that change your current `build.gradle` files or resources will add to the build time.
- Resources changed on each build prevent Instant Run from performing a code swap.
- Use static values for debug builds to prevent full rebuilds of APK.

```groovy
android {
  compileSdkVersion 27
  buildToolsVersion "27.0.0"

  defaultConfig {
    applicationId "burrows.apps.example"
    versionCode new Date().format("ddMMyyHHmm").toInteger()
    versionName "1.0"
    minSdkVersion 19
    targetSdkVersion 27
  }
}
```

On each build, `versionCode` is updated with a new value, and that can be optimised:

```groovy
def isRelease = project.hasProperty("release")

android {
  compileSdkVersion 27
  buildToolsVersion "27.0.0"

  defaultConfig {
    applicationId "burrows.apps.example"
    versionCode isRelease ? new Date().format("ddMMyyHHmm").toInteger() : 1
    versionName "1.0"
    minSdkVersion 19
    targetSdkVersion 27
  }
}
```

Now, only release builds will be given an updated value. As we saw before, we should run `gradlew -Prelease`.

---

#### Create library modules

[__Source__](https://youtu.be/rvwAlbtbtmM?t=2493)

- Gradle will only compile the modules you modify
- Cache those outputs for future builds
- Improves effectiveness of "configuration on demand" and "parallel" execution
- Particularly helpful when packaging by feature.

If the project keeps scaling, you will be willing to create feature modules and model specific modules. Anyhow, creating folders to keep modules inside is a huge win. In order to do that, you just need to create the desired folders, move the modules in and review that both `settings.gradle` and dependencies from other modules, point to the new modules, so paths should look like:

```groovy
// settings.gradle
include ':features:feature-1'
include ':features:feature-2'
include ':features:feature-3'
```

where:

```groovy
root
  build.gradle
  settings.gradle
  features
    feature-1
      build.gradle
    feature-2
      build.gradle
    feature-3
      build.gradle
```

#### Disable PNG crunching

[__Source__](https://youtu.be/rvwAlbtbtmM?t=2636)

- If you can't convert your PNGs to WebP, use PNG crunching.
- With Android Gradle Plugin (AGP) 3+, PNG cunrching is disabled by default for "debug" build types.
- by disabling it, AGP will not compress the PNGs on each build.

```
android {
  aapOptions {
    cruncherEnabled = project.hasProperty("ci")
  }
}
```

#### Avoid legacy multidex

[__Source__](https://youtu.be/rvwAlbtbtmM?t=2697)

- "minSdkVersion" < 21 --> Legacy multidex.
- "minSdkVersion" >= 21 --> Native multidex.
- We can speed up development builds by using "productFlavors" or Gradle properties to toggle the "minSdkVersion" for faster build times.

```groovy
android {
  compileSdkVersion 27
  buildToolsVersion "27.0.0"

  defaultConfig {
    applicationId "burrows.apps.example"
    versionCode isRelease ? new Date().format("ddMMyyHHmm").toInteger() : 1
    versionName "1.0"
    minSdkVersion rootProject.hasProperty("lollipop") ? 21 : 19 // We add this property.
    multiDexEnabled true
  }
}
```

__Disable pre-dexing libraries on production__

- Java class files need to be converted to DEX files.
- Helps to speed up the build for incremental builds locally.
- On a CI server, where you run clean builds, pre-dexing can have the reverse affect, so we can disable it.

```groovy
android {
  dexOptions {
    preDexLibraries = !project.hasProperty("ci")
  }
}
```

#### Enable Build Cache

[__Source__](https://youtu.be/rvwAlbtbtmM?t=2899)

- Stores certain outputs that the Android plugin for Gradle generates when building your project.
- Improves performance of clean builds by reusing cached files.
- With Android Gradle Plugin (AGP) 2.3+, build cache is enabled by default.

#### Enable new DEX Compiler

[__Source__](https://youtu.be/rvwAlbtbtmM?t=2899)

- DEX compilation is the process of transforming `.class` bytecode into `.dex` bytecode
- DX vs D8: compiles faster and outputs smaller `.dex` files.
- D8 has the same or better app runtime performance.
- With Android Gradle Plugin (AGP) 3.1+, D8 is enabled by default.

In your `gradle.properties` file:

```groovy
android.enableD8=true
```

#### Disable Splits (single APK)

**Update**: From Android Gradle Tools (AGT) 3.2+, you can use `bundle` configuration attribute in order to achieve the same, since the plugin will ignore `splits` in favour of the new Android App BUndles, the new app packaging.

Spliting APKs will reduce the apk size substantially if you are using native libraries, and will help to reduce non desired resources, but disabling multi-APK builds will help to reduce build times for debugging purposes, since this option is really worth it only for APK delivery (client) purposes.

We could use a property to avoid `splits` for certain kind of builds:
```groovy
android {
  if (project.hasProperty('release')){
      splits.abi.enable = false
      splits.density.enable = false
  }
}
```

Now, only `release` builds will be splitting APKs. Remember to run `gradlew -Prelease` to enable `splits`.

#### More sources

- [**Optimize Your Build Speed**](https://developer.android.com/studio/build/optimize-your-build)
- [**Shrink Your Code and Resources**](https://developer.android.com/studio/build/shrink-code)


### Related sources

- [**Android Plugin DSL Reference**](https://google.github.io/android-gradle-dsl/current/index.html)
- [**App resources overview**](https://developer.android.com/guide/topics/resources/providing-resources)

























Potential Investments to reduce waiting time
- Only rebuild files that have changed (Incremental Builds)
- Reuse build output across machines (Build Cache)
- Collect build metrics to optimize performance (Build Performance Management)







- [__Settings__](#settings)
- [__Tips__](#tips)
  - [__Stop Gradle builds for real__](#how-to-stop-gradle-builds-for-real)
  - [__Optimize multidex development builds__](#optimize-multidex-development-builds)
  - [__Increment build version number__](#increment-build-version-number)
- [__Resolve Gradle dependencies problems__](#resolve-gradle-dependencies-problems)
- [__Related sources__](#related-sources)

<br>

### Settings

- [Enable the new D8 compiler](https://android-developers.googleblog.com/2017/08/next-generation-dex-compiler-now-in.html), setting the following parameter in project's `gradle.properties` file. From Android Studio 3.1 __this is not necessary anymore__:
  ```
  android.enableD8=true

  ```


### Tips

#### How to stop Gradle builds for real

Don't try to stop them using Android Studio. Instead, do it using the command line tool, running `./gradlew stop`.

#### Optimize multidex development builds

Creating multidex output for your project typically adds a significant amount of time to your build due to the merging process. You can mitigate this by setting a minimum SDK version of 21, which allows the Android plugin to perform more efficient dexing.

Here is a partial sample configuration with two different flavors:
```
android {
    productFlavors {
        dev {
            minSdkVersion 21
        }
        prod {
            minSdkVersion 14
        }
    }
}
```

### Increment build version number

**Through a file**

```
task incrementVersion << {
    def propsFile = file("../gradle.properties")
    def propsText = propsFile.getText()

    def patternVersionNumber = Pattern.compile("app_version=(\\d+)\\.(\\d+)\\.(\\d+)")
    def matcherVersionNumber = patternVersionNumber.matcher(propsText)
    matcherVersionNumber.find()

    def majorVersion = Integer.parseInt(matcherVersionNumber.group(1))
    def minorVersion = Integer.parseInt(matcherVersionNumber.group(2))
    def patchVersion = Integer.parseInt(matcherVersionNumber.group(3))
    patchVersion++
    if(patchVersion > 15) {
        patchVersion = 0
        minorVersion++
    }
    if(minorVersion > 10) {
        minorVersion = 0
        majorVersion++
    }

    propsText = matcherVersionNumber.replaceAll("app_version=" + majorVersion + "." + minorVersion + "." + patchVersion)
    propsFile.write(propsText)
}
```

### Resolve Gradle dependencies problems

[__Source__](https://proandroiddev.com/android-gradle-and-the-curious-case-of-invisible-dependency-7f1bcc8bb79e)

 These dependencies could further have their own dependencies and those dependencies could have their own and so on. This is called Transitive dependency and Gradle needs to include all the direct/indirect dependencies in the app.

 ```
 gradlew app:dependencies
 ```

 This will show dependency resolution tree for all build variants. We can add a flag to the above command to view configuration for specific build variant. For example --configuration releaseCompileClasspath will show us dependency tree for release variant.


If Gradle finds out multiple dependency to the same library but different versions then it has to make a choice. Including different versions of the same library wouldn’t make sense. In such case, Gradle by default chooses the newest version of that library.
```
| + — — com.android.support:support-v4:21.0.3
| | \ — — com.android.support:support-annotations:21.0.3 -> 27.0.2
```

Above, Gradle is telling that although the support-v4:21.0.3 depends on support-annotations:21.0.3 there is also a dependency to newer version support-annotations:27.0.2 in the dependency tree so 27.0.2 will be used.


All support libraries belong to the following group com.android.support. As we see in Gradle dependency tree, com.android.support:support-v4:21.0.3 is the only support library with version 21.0.3 and not resolved to the newest version 27.0.2. This is causing the conflict.

How to resolve this issue? There are few ways to do it:

- To implement a [__resolution strategy__](https://docs.gradle.org/current/dsl/org.gradle.api.artifacts.ResolutionStrategy.html) and forcing Gradle to use a particular version of the library.

```
android {
  configurations.all {
    resolutionStrategy.force 'com.android.support:support-v4:27.0.2'
  }
}
```

- To explicitly add com.android.support:support-v4:27.0.2 in build.gradle. This will let Gradle override older version with new one.

- Use the same version for all the libraries (**as we normally do**).













### Related sources

- [__Implementing Crashlytics on a multiflavour and multi-key environment Raw__](https://gist.github.com/tiwiz/b5fac29f4bacc3dfb0c9)
- [__Gradle performance guide__](https://gradle.github.io/performance-guide/)
- [__Gradle Wrapper__](https://docs.gradle.org/current/userguide/gradle_wrapper.html)
- [__More about Tasks__](https://docs.gradle.org/current/userguide/more_about_tasks.html#sec:up_to_date_checks)


























- Android File Grouping??

[__Source__](https://goo.gl/TCznje)

How declare screen resource folder?

```
android {
  sourceSets {
    main {
        res.srcDirs = [
                'src/main/res-main',
                'src/main/res-screen/about',
                'src/main/res-screen/chat',
                'src/main/res-screen/event-detail',
                'src/main/res-screen/event-list',
                'src/main/res-screen/home',
                'src/main/res-screen/login',
        ]
    }
  }
}
```

or

```
android {
  sourceSets {
      main {
          file('src/main/res-screen')
                  .listFiles()
                  .each { res.srcDirs += it.path }
      }
  }
}
```

> __Note: above works only if you are in Project view__

Before decompose.

```
res/
  layout/
    chat_activity.xml
    chat_toolbar.xml
    chat_item.xml
    chat_share_view.xml
    home_activity.xml
    home_toolbar.xml
    home_fragment_sign_in.xml
    home_fragment_sign_up.xml
```

After decompose.

```
res/
  layout/
    chat/
      chat_activity.xml
      chat_toolbar.xml
      chat_item.xml
      chat_share_view.xml
    home/
      home_activity.xml
      home_toolbar.xml
      home_fragment_sign_in.xml
      home_fragment_sign_up.xml
```



### Use prefixes for your resources

Declare `resourcePrefix` in your build in order to use them in libraries

```
android {
  resourcePrefix 'prefix_'
}
```

More info [__here__](https://youtu.be/Y2GC6P5hPeA?t=898)

- List Gradle tasks



### Offline mode

You can also run gradle or gradle wrapper with the flag enabled, like:

```
./gradlew assembleDebug --offline
```














- __Using Kotlin in tests avoiding code in production__ // LOOK FOR THE SOURCE

  We should do:
```groovy
main.java.srcDirs += 'src/main/kotlin'
```
and we need this as well to compile only tests written in Kotlin:
```groovy
afterEvaluate {
    android.sourceSets.all {
      sourceSet ->
        if (!sourceSet.name.startsWith("test")) {
          sourceSet.kotlin.setSrcDirs([])
        }
    }
}
```

- __Dynamic folders for variants__
```groovy
android {
  sourceSets {
      debug {
          res.srcDirs = ['src/main/res-debug/']
          assets.srcDirs = ['src/main/assets-dev/']
      }
      release {
          assets.srcDirs = ['src/main/assets-release/']
      }
  }
}
```

- __Optimize multidex development builds__

Creating multidex output for your project typically adds a significant amount of time to your build due to the merging process. You can mitigate this by setting a minimum SDK version of 21, which allows the Android plugin to perform more efficient dexing.

- __Adding concrete dependencies related to the build__ // LOOK FOR THE SOURCE

  Having different `productFlavors`:
```groovy
productFlavors {
  flavorDimensions "x", "y"

  random {
    dimension "x"
  }

  production {
   dimension "x"
  }

  staging {
    dimension "y"
  }

  dev {
      dimension "y"
  }
}
```

  Later, declare configurations to be able to define the dependencies:
  ```
  configurations {
    randomStagingDebugCompile
    debugCompile
    releaseCompile
  }
  ```

  And finally, definde dependencies:
  ```
  dependencies {
    randomStagingCompile 'com.squareup.leakcanary:leakcanary-android-no-op:1.3.1'
    releaseCompile 'com.squareup.leakcanary:leakcanary-android-no-op:1.3.1'
    debugCompile 'com.squareup.leakcanary:leakcanary-android:1.3.1'
  }
  ```
