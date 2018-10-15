# Gradle Build Plugins

## Table of contents

- Gradle Plugin
- Android Gradle Plugin (AGP)
- Android Related Plugins
- Kotlin Gradle plugin
- Kotlin Related Plugins
- Artifact Publishing Plugins
- Other Plugins

---

## Android Related Plugins

- [**Easy Launcher**]: Add a different ribbon to each of your Android app variants using this gradle plugin. Of course, configure it as you will. This plugin is based on another existing plugin called [**Ribonizer**](https://github.com/maskarade/gradle-android-ribbonizer-plugin). The code available on [**Github**](https://github.com/akaita/easylauncher-gradle-plugin).

- [**Gradle Android Command**]: Handy commands for testing Android on CI. The code is available on [**Github**](https://github.com/novoda/gradle-android-command-plugin).

- [**Android cache fix Gradle plugin**]: Some Android plugin versions have issues with Gradle's build cache feature. When applied to an Android project this plugin applies workarounds for these issues based on the Android plugin and Gradle versions. The code is available on [**Github**](https://github.com/gradle/android-cache-fix-gradle-plugin).

- [**DexCount-Gradle-Plugin**]: A Gradle plugin to report the number of method references in your APK or AAR on every build. This helps you keep tabs on the growth of your app, with an eye to staying under the 65,536 method-reference limit, and avoiding the headache of eliminating methods or enabling multidex. The code is available on [**Github**](https://github.com/KeepSafe/dexcount-gradle-plugin).

---

## Artifact Publishing Plugins

- [**Gradle Maven Publish plugin**](: Gradle plugin that configures an uploadArchives task to automatically upload all of your Java, Kotlin or Android libraries to any Maven instance. The code is available on [**Github**](https://github.com/vanniktech/gradle-maven-publish-plugin).

- [**Bintray release**]: A helper for releasing from gradle up to bintray. The code is available on [**Github**](https://github.com/novoda/bintray-release).

---

## Other Plugins

- [**Protobuf Plugin for Gradle**]: More information about the plugin [**here**](https://grpc.io/blog/kotlin-gradle-projects). The code is available on [**Github**](https://github.com/google/protobuf-gradle-plugin).

















## Gradle Plugin

## Android Plugin (AGP)
All the Android Gradle Plugin updates are [**here**](https://developer.android.com/studio/releases/gradle-plugin)

https://google.github.io/android-gradle-dsl/

### Personal Global based gradle.properties
```
# Gradle plugin
org.gradle.jvmargs=-Xmx4096M
org.gradle.parallel=true                        # Enabled by default?
org.gradle.caching=true                         # Enabled by default? / GLC: --build-cache)

# Android plugin
android.enableR8.fullMode=true                  # More info: https://goo.gl/jYczoJ / GLC: X
android.enableD8=true
android.debug.obsoleteApi=true                  # More info: https://goo.gl/jYczoJ / GLC: X
android.enableSeparateAnnotationProcessing=true # More info: https://goo.gl/CDNxaE / GLC: X
android.databinding.enableV2=true               # More info: https://goo.gl/yejYTF / GLC: X

# * GLC: Gradle command-line parameter
```

Explain command line = ./gradlew --build-cache

### Personal Project based gradle.properties
```
# Android plugin
android.useAndroidX=true
android.enableJetifier=true
```

### Depecreated & Unnecessary parameters

```
# Gradle plugin
org.gradle.daemon=true                    # Enabled by default. More info: https://goo.gl/jaQ2zP
org.gradle.configureondemand=true         # Disabled by default. More info: https://goo.gl/Fazivj

# Android plugin
android.enableR8=true                     # Enabled by default.
android.enableD8.desugaring=true          # Enabled by default. More info: https://goo.gl/sEfN5s
android.enableIncrementalDesugaring=true  # Enabled by default. More info: https://goo.gl/Sbu7AY
android.enableAapt2=true                  # Enabled by default. More info: https://goo.gl/mLdNGi
android.enableBuildCache=true             # Enabled by default. More info: https://goo.gl/NTL482

# Kotlin plugin
kotlin.incremental=true                   # Enabled by default. More info:  / GCL: -Pkotlin.incremental=true

# * GLC: Gradle command-line parameter
```



android.incremental??















### Updates
[**Source**](https://androidstudio.googleblog.com/)

## Kotlin Gradle Plugin

### Updates
[**Source**](https://androidstudio.googleblog.com/)

#### 3.3.X
- When using Gradle Kotlin DSL, you can now set source and target compatibility in `compileOptions` via the following syntax:
```
compileOptions {
  sourceCompatibility = JavaVersion.VERSION_1_8
  targetCompatibility = JavaVersion.VERSION_1_8
}
```

- CMake version 3.10.2 is now included with SDK Manager. Note that Gradle still uses version 3.6.0 by default. To specify a CMake version for Gradle to use, add the following to your module’s build.gradle file:
```
android {
    ...
    externalNativeBuild {
        cmake {
            ...
            version "3.10.2"
        }
    }
}
```
For more information on configuring CMake in build.gradle, [**check this out**](https://developer.android.com/studio/projects/gradle-external-native-builds#configure-gradle).

### 3.2.X
- Lint checks to ensure Java code interops well with Kotlin in order to make sure your Java code interoperates well with your Kotlin code, enforcing the best practices. To enable these checks from the command-line builds, add the following line in your `build.gradle` file:
```
 android {
    lintOptions {
        check 'Interoperability'
    }
}
```

### 3.1.X
- Make sure to include Google's Maven repository in the top-level build.gradle file
```
allprojects {
    repositories {
        // The order in which you list these repositories matter.
        google()
        jcenter()
    }
}
```

### 3.0.X
The flavorSelection property has moved to the ProductFlavor class. This means that you can choose the default variant your app consumes from a producer at the flavor level. Add this property to android.defaultConfig to apply it to all flavors:

android {
  defaultConfig {
    flavorSelection 'shape', 'square'
  }
}

Specifying PNG crunching is now a BuildType property and is disabled by default on debug builds:
android {
    …
    buildTypes {
        release {
            crunchPngs true
        }
    }
}













# Kotlin Compiler Plugin


Kotlion 1.2.5-

support for the Kotlin compiler plugins like kotlin-allopen and kotlin-spring



In this release, we introduce an experimental progressive compiler mode intended for actively developed codebases whose maintainers regularly update to latest versions of the Kotlin compiler and tools. In this mode, some of the deprecations and bug-fixes for unstable code take effect immediately. Consequently, some code may break upon enabling the mode or upon updating Kotlin to future versions while keeping the progressive mode enabled.

Fixes that are chosen to be enabled in the progressive mode won’t affect too many places in the codebases, though they won’t work silently and will require the maintainers to fix the erroneous pieces of code. We are going to provide automated migration tools in the IDE plugin for this where possible. Any code fixed in this way will stay valid outside the progressive mode, too. For examples of issues with fixes applied in the progressive mode, see KT-9580, KT-16681, or KT-17981.

You can enable the progressive mode on a per-module basis by adding the flag -Xprogressive to the arguments passed to the Kotlin compiler.

You can do it like this:

compileKotlin {
kotlinOptions {
freeCompilerArgs = [“-Xprogressive”]
}
}

https://kotlinlang.org/docs/reference/using-gradle.html#compiler-options

https://kotlinlang.org/docs/reference/compiler-plugins.html