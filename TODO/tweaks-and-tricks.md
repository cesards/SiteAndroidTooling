---
id: tweaks-and-tricks
layout: page
title: AS/IntelliJ Tweaks & Tricks
sidebar: true
---

#### Table of contents

- [__Exclude `build` files in quick file search__](#exlude-build-files-in-quick-file)
- [__Android Monitor__](#android-monitor)
- [__Custom Data Views__](#custom-data-views)
- [__Related sources__](#related-sources)


### Exclude transitive dependencies when adding libraries to the project

[__Source__](https://blog.jetbrains.com/idea/2018/06/whats-new-in-intellij-idea-2018-2-eap-4/)

In the library properties editor, there is a new ‘Configure’ action link, which opens a new ‘Configure Transitive Dependencies’ dialog where you can select only the necessary transitive dependencies to add to your current project.

![](/assets/images/tweaks-and-tricks-transitive-dependencies-1.png)
![](/assets/images/tweaks-and-tricks-transitive-dependencies-2.png)




### Exclude `build` files in quick file search

You can exclude the generated files from the build folder and avoid having undesired results whenever you do a quick search or search for an specific string in your project. You just need to add an exclusion as a scope:

![](/assets/images/tweaks-and-tricks-scopes-1.png)

And then you can select your custom scope whenever you want to use features as "Find in Path":

![](/assets/images/tweaks-and-tricks-scopes-2.png)

<br>

### Android Monitor

#### Remove useless information from the LogCat

We can remove `Show process and thread IDs (PID-TID)` and `Show package name` from the Log Header

![](/assets/images/tweaks-and-tricks-logcat-header-location.png)
![](/assets/images/tweaks-and-tricks-logcat-header.png)

#### Clear log prevention during a crash

From `Edit Filter Configuration`, we just need to add a filter based on our app package name and that will fix the problem:

![](/assets/images/tweaks-and-tricks-logcat-crash-filter-location.png)
![](/assets/images/tweaks-and-tricks-logcat-crash-filter.png)

### Custom Data Views

[__Source__](https://tips.seebrock3r.me/use-custom-viewers-for-your-data-android-studio-protip-4-9010d43772e2)

Sometimes, you need a specific type to be shown in the debugger in a certain way instead of the default one. The default representation for an object that has no toString() is the class name and the instance hashcode. That’s usually not helpful at all.

You can create a custom **Java Data Type Renderer** for your class, that better suits your current needs, being confident you’re not altering the observed classes while still getting the information you want. The IDE will start showing the information structured as you defined for the different renders.

**ALSO: you can change the way data appears in the debugger.**

The only thing you need to do is to right click a variable in the debugger, and pick the kind of representation you need in the View as menu.

**The nice thing about data renderers is that, as we have seen for Credential, you can use them for classes you don’t own and you don’t have the sources for.**

#### More info

- [__Customize data views__](https://www.jetbrains.com/help/idea/2016.1/customize-data-views.html)

### Related sources

- [__Android Studio Tips and Tricks__](http://michaelevans.org/blog/2016/01/06/android-studio-tips-and-tricks/)
- [__Use tasks to bring the stories to you__](https://tips.seebrock3r.me/use-tasks-to-bring-the-stories-to-you-android-studio-protip-5-7458380439d0)

<br>

























- [__Remove `File Header` from Includes__](#remove-file-header-code-from-includes)
- [__Modify Test templates__](#modify-test-templates)
- [__IDE behaviour__](#ide-behaviour)
- [__Language Injection__](#offline-mode)
- [__Autoscroll from Source__](#autoscroll-from-source)
- [__Creating files properly__](#creating-files-properly)
- [__Inspections__](#inspections)
- [__Test RESTful Web Service__](#test-restful-web-service)
- [__Increasing IDE Memory__](#increasing-ide-memory)
- [__Changing idea properties__](#changing-idea-properties)


### Remove `File Header` from Includes

Nowadays git versioning is much more useful rather than having headers.
Get rid of the header.

If you are using Kotlin, I would also recommend removing it from all the Kotlin files. You can either remove the code from the `Includes` tab, or remove the `#parse("File Header.java")`
from the desired files in the `Files` tab:

```
Class
Interface
Enum
AnnotationType
package-info
Singleton
```

![](/sections/3-tweaks/img/file_header.png)

You can do the same with Test files:
```
Groovy JUnit Test Case
JUnit3 Test Class
TestNG Test Class
...
```

### Modify test templates

After reading [__this Sandro Mancuso's post__](http://goo.gl/Oa62oT) and trying this naming for a while, I think tests are more readable. Why having the `Test` suffix in a file we already know it's in the test container? Why having `test` prefix in every JUnit method in a test class? Do you also think it's redundant? Try this:

- `JUnit4 Test Class`

  ```
  import static org.junit.Assert.*;
  #parse("File Header.java")
  public class ${NAME} {
    ${BODY}
  }
  ```

  to

  ```
  import static org.junit.Assert.*;
  public class ${NAME}Should {
    ${BODY}
  }
  ```


- `JUnit3/JUnit4/TestNG Setup Method`

  ```
  public void setUp() throws Exception {
    ${BODY}
  }
  ```

  to

  ```
  public void setUp() {
    super.setUp();
    ${BODY}
  }
  ```

- `JUnit3/JUnit4/TestNG TearDown Method`

  ```
  public void tearDown() throws Exception {
    ${BODY}
  }
  ```

  to

  ```
  public void tearDown() {
    ${BODY}
  }
  ```

- `JUnit3/JUnit4/TestNG Test Class`

  ```
  public class ${NAME} extends TestCase {
    ${BODY}
  }
  ```

  to

  ```
  public class ${NAME}Should {
    ${BODY}
  }
  ```

- `JUnit3/JUnit4/TestNG Test Method`

  ```
  public void test${NAME}() throws Exception {
    ${BODY}
  }
  ```

  to

  ```
  public void ${NAME}() {
    ${BODY}
  }
  ```

  PS: We don't need to extends from the JUnit3 `TestCase` class anymore.


### IDE behaviour

#### Project in New Window

  In case you haven't got configured this parameter, this would be likely to be your setting.

  ```
  Appearance & Behaviour
      - System Settings
          └── ✓ Open project in a new window
  ```

<br>

### Language injection

In a String, let's say:

```
final String titleJson = "";
```

You could press alt + enter and select `Inject language or reference` and choose between the different options. The most used injected code will be `JSON` and `RegExp`. Once selected the injected language, we need to press `alt + enter` again and open the editor related to the chosen injected language.

![](/sections/3-tweaks/img/language-injection.png)

More info [__here__](https://www.jetbrains.com/help/idea/2016.1/using-language-injections.html) and [__here__](https://youtu.be/eq3KiAH4IBI?t=1562).

<br>

### Creating files properly

Instead of creating folders and then files, you can use the Window in order to create the file properly

![](/sections/3-tweaks/img/creating-files-properly.png)

More info [__here__](https://youtu.be/eq3KiAH4IBI?t=851)

<br>

### Inspections

// RUN INSPECTIONS
// RUN INSPECTIONS BY Name
// Inspect code --> inspect code in our entire code

You can also enable inspections for a certain code pattern, for example using
[__Structural search__](#structural-search) and enable quick fixes for those pieces
of code.

https://youtu.be/Y2GC6P5hPeA?t=494

<br>

### Test RESTful Web Service

Allows you to basically any calls to any endpoint http

<br>

### Increasing IDE Memory

By default, the IDE is assigned a maximum of 750 MB. If you want to increase the IDE memory, you should place a `studio.vmoptions` file in the following directory (using MAC OS):

```
~/Library/Preferences/{FOLDER_NAME}/studio.vmoptions
```

and add `-Xmx4096m`. This lets the IDE take as much as 4MB of Ram for its operations. If you need to tweak other memory options, these are the flags you should modify:

```
-Xms512m
-Xmx4096m
-XX:MaxPermSize=350m
-XX:ReservedCodeCacheSize=96m
-XX:+UseCompressedOops
```

More info [__here__](http://tools.android.com/tech-docs/configuration)

<br>

### Changing idea properties

If you want to override an IDE property, create a new `idea.properties` file in the following directory (using MAC OS):

```
~/Library/Preferences/{FOLDER_NAME}/idea.properties
```

where you specify just the override properties. This file will be merged with the default properties in the IDE.

- Start a project with the `Project View` instead of the `Android View`:

  ```
  studio.projectview=false
  ```

More info about properties that could be overriden, [__here__](http://tools.android.com/tech-docs/configuration) and [__here__](https://www.jetbrains.com/help/idea/2016.1/file-idea-properties.html?origin=old_help)



















```

    - Scopes
        └── Build Out
```
