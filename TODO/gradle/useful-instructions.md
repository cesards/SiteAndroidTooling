

From the top level `build.gradle` in a project

Therefore we decided to set the targetSdk (and others) for all our modules in the top level build.gradle file. This also keeps submodule build.gradle files lean.

```
subprojects {
    afterEvaluate { project ->
        if (project.plugins.findPlugin('android') ?: project.plugins.findPlugin('android-library')) {
            android {
                buildToolsVersion Config.buildTools
                compileSdkVersion Config.compileSdk

                defaultConfig {
                    minSdkVersion Config.minSdk
                    targetSdkVersion Config.compileSdk
                }

                compileOptions {
                    sourceCompatibility Config.javaVersion
                    targetCompatibility Config.javaVersion
                }
            }
        }
    }
}