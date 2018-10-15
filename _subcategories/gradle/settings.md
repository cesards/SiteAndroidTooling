# Gradle Settings

Since Gradle is a build system for the JVM, most of the configuration parameters used are based on the Android Gradle Plugin, Kotlin Graddle Plugin and Gradle.











# Gradle Settings

// TODO
kapt.use.worker.api=true

Salio con AGP 1.2.60, pero decían que en 1.2.70 lo pondrían por defecto

 permite que el annotation processor se ejecute en un worker de gradle. Esto abre camino a paralelización si el desarrollador usa el Worker api de gradle.

 https://blog.jetbrains.com/kotlin/2018/08/kotlin-1-2-60-is-out/


## Current Gradle Global Settings

```
org.gradle.jvmargs=-Xmx4098m -XX:MaxPermSize=512m -XX:+HeapDumpOnOutOfMemoryError
org.gradle.daemon=true
org.gradle.parallel=true
org.gradle.configureondemand=true
android.enableBuildCache=true
android.buildCacheDir=../../android-build-cache


org.gradle.jvmargs=-Xmx3096m -XX:MaxPermSize=1024m -XX:+HeapDumpOnOutOfMemoryError -Dfile.encoding=UTF-8
org.gradle.parallel=true
org.gradle.daemon=true
org.gradle.configureondemand=true
```


```
org.gradle.jvmargs=-Xmx4096M
org.gradle.parallel=true
org.gradle.caching=true
# Configuration on demand is not supported by the current version of the Android Gradle plugin since you are using Gradle version 4.6 or above. Suggestion: disable configuration on demand by setting org.gradle.configureondemand=false in your gradle.properties file or use a Gradle version less than 4.6.


## Android specific ##
android.enableBuildCache=true
android.enableR8=true
android.enableD8=true
android.enableSeparateAnnotationProcessing=true
# android.databinding.enableV2=true
# android.enableAapt2=true - always enabled from AGP 3.3
```

## Current Project Local Settings

android.useAndroidX=true
android.enableJetifier=true


## Updates

```org.gradle.daemon=true```
creo que está a true por defecto

android.enableBuildCache yo diría que es default true hace eones

ConfigureOnDemand dejó de ir, ahora lo han arreglado pero igualmente me dijo Stefan Oehme que se lo quieren cargar porque no aporta casi nada