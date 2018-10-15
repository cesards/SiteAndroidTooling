---
id: plugins
layout: page
title: AS/IntelliJ Plugins
sidebar: true
---

# IDE Plugins

## Table of contents

- Considerations

- Android Related Plugins (personal selection)

- Android Related Plugins (to consider)

- Kotlin Related Plugins (personal selection)

- Kotlin Related Plugins (to consider)

- Java Related Plugins (personal selection)

- Java Related Plugins (to consider)

- CVS Related Plugins (personal selection)

- CVS Related Plugins (to consider)

- Dart & Flutter Related Plugins (personal selection)

- Other Related Plugins (personal selection)

- Other Related Plugins (to consider)

---

## Considerations

TO REORDER

This plugins can either be installed in AS or IntelliJ, so I'll classify the plugins based on Language or Platform.

SAY WHERE YOU CAN FIND THE PLUGINS

Even though nowadays Android Studio is a super powerful tool, we need to be careful not to add many Plugins, because it could affect to its performance. As [__Jake Wharton suggested__](https://www.reddit.com/r/androiddev/comments/7sxhig/android_studio_slower_when_using_kotlin/dt88pgn/?st=jg4j94t8&sh=b2c973b8), try to disable plugins that you barely use, because it's going to increase substantially your IDE speed.

These are, in my opinion, the most useful plugins for Android Development:



---

## Android Related Plugins (personal selection)

> **Last update: October, 2018**

- **ADB Idea**: Adds ADB commands to Android Studio and Intellij. Plugin code available on [**Github**](https://github.com/pbreault/adb-idea).
  
- **Android Butterknife Zelezny**: Plugin for generating ButterKnife injections from selected layout XMLs in activities/fragments/adapters. Plugin code available on [**Github**](http://github.com/avast).

- **Android Data Tools**: Plugin for review and edit android app data.

- **Android Drawable Preview**: Render drawable instead of default icon. Supports binary and vector images.

- **FindViewByMe**: Smart cast checkbox when targeting API 26, generatation of "findViewById" code for activity, support generation of "findViewById" code for fragment, and you can customize root view name. Also support generation of "findViewById" code for ViewHolder. Plugin code available on [**Github**](https://github.com/laobie/FindViewByMe)

---

## Android Related Plugins (to consider)

> **Last update: October, 2018**

- **WIFI ADB ULTIMATE**: Now you can connect your android devices over wifi really if you also use the android software I provided. Or connect devices using the USB cable for the first time. Plugin code available on [**Github**](https://github.com/huazhouwang/WIFIADB/tree/master/WIFIADBIntelliJPlugin).

- **Android API Level**: Plugin to show Android API level and version name. Plugin code available on [**Github**](https://github.com/droibit/androidapilevel-plugin)

- **Andrdoid Drawable Importer**: This plugin consists of three main features. You can access them by a right-click anywhere, but not on a file, inside an Android module under New.  
  1. AndroidIcons and Material Icons Drawable Import You are able to select the asset, specify your color, change the target resource name and select all the resolutions you want to import. All the missing folders will be created automatically. If there are already drawables with the same name, you will be warned. You can even search for your desired asset by just start typing when the first spinner has focus. Since Material Icons provide also Vector Drawables, those can be imported now as well!
  2. Batch Drawable Import Select assets (or a whole folder) and specify the source resolutions. You can change the source size of every image as well. Specify all resolutions, to which it should be resized to. This works also with 9-Patch-Images. But take care: sometimes it's necessary to remove / add the one or other "pixel" in the 9-Patch-Editor. But just give it a try :) 
  3. Multisource-Drawable Ever got a zip with drawables for your Android project by your designer with the following structure?

  Plugin code availabble on [**Github**](https://github.com/winterDroid/android-drawable-importer-intellij-plugin)

- **Name That Color**: Name the color you have in your clipboard directly inside your color resource file in Android Studio. Copy the color in your clipboard and go to your color resources files (usually colors.xml), then open the auto complete pop-up. You'll see there two suggestions go generate the whole (material) color item, with the name of the (material swatch) color. Plugin code available on [**Github**](https://github.com/galex/name-that-color-intellij-plugin)

- **PermissionsDispatcher plugin**: IntelliJ plugin for supporting PermissionsDispatcher. This is official plugin. PermissionsDispatcher is wonderful library for Runtime Permissions. However, it asks developers "attach annotations" and "delegate to generated class" and then after that "rebuild". It's hard to follow all steps correctly. This plugin generates the skelton of methods for "attach annotations" and "delegate to generated class" using GUI. Plugin code available on [**Github**](https://github.com/permissions-dispatcher/PermissionsDispatcher).

---

## Kotlin Related Plugins (personal selection)

- **Kotlin**: The Kotlin plugin provides language support in IntelliJ IDEA and Android Studio.

> **Last update: October, 2018**

---

## Kotlin Related Plugins (to consider)

> **Last update: October, 2018**

- **Parcelable Code Generator (for Kotlin)**: Parcelable Code Generator is a plugin which generates Android Parcelable boilerplate code for kotlin class. Plugin code available on [**Github**](https://github.com/nekocode/android-parcelable-intellij-plugin-kotlin).

---

## Java Related Plugins (personal selection)

> **Last update: October, 2018**

- **AutoValue plugin**: Provides context menu options, generate menu options and code intentions to generate and manipulate the builder method and/or create method on classes annotated with @AutoValue. Also works with @AutoParcel and @AutoParcelGson annotations. Plugin code available on [**Github**](https://github.com/afcastano/AutoValuePlugin).

---

## Java Related Plugins (to consider)

> **Last update: October, 2018**

- **GSONFormat**: Quickly to convert a JSON string to an `InnerClassEntity` class.

---

## CVS Related Plugins (personal selection)

> **Last update: October, 2018**

- **.gitignore**: `.ignore` is a plugin for `.gitignore` (Git), `.hgignore` (Mercurial), `.npmignore` (NPM), `.dockerignore` (Docker), `.chefignore` (Chef), `.cvsignore` (CVS), `.bzrignore` (Bazaar), `.boringignore` (Darcs), `.mtn-ignore` (Monotone), `ignore-glob` (Fossil), `.jshintignore` (JSHint), `.tfignore` (Team Foundation), `.p4ignore` (Perforce), `.prettierignore` (Prettier), `.flooignore` (Floobits), `.eslintignore` (ESLint), `.cfignore` (Cloud Foundry), `.jpmignore` (Jetpack), `.stylelintignore` (StyleLint), `.stylintignore` (Stylint), `.swagger-codegen-ignore` (Swagger Codegen), `.helmignore` (Kubernetes Helm), `.upignore (Up)`, `.prettierignore` (Prettier), `.ebignore` (ElasticBeanstalk) files in your project. Plugin code available on [**Github**](https://github.com/hsz/idea-gitignore)

## CVS Related Plugins (to consider)

> **Last update: October, 2018**

- **GitToolBox**: Enriches Git Integration with additional features. Plugin code available on [**Github**](https://github.com/zielu/GitToolBox)

- **Git Extender**: Git Extender adds an option to Update All local branches tracking a remote for all git roots in the current project Local branches that will be updated are the branches that exist locally and have been configured to track a remote branch. It tries to fast-forward commits in remote branches to local branches. It can be configured through the settings to attempt a simple merge, if the local branch cannot be merged to the tracked remote using fast-forward only. In this case, if there are conflict errors, the merge will be aborted and an error notification will be shown. The update, then, should be performed manually for the reported branch, in order to resolve the conflicts. Any possible uncommitted changes to the current branch will be stashed After updating a branch, if there were any file changes, they will be displayed in IntelliJ Version Control tab. Currently, the correct list of file changes (updated, created, removed) will be displayed. However, when performing a diff for files in a branch other than the currently checked out, the diff will most probably be incorrect. Plugin code availabble on [**Github**](https://github.com/JChrist/gitextender).

- **Git Flow Integration**: An intelliJ plugin providing a UI layer for git-flow, which in itself is a collection of Git extensions to provide high-level repository operations. Plugin code available on [**Github**](https://github.com/OpherV/gitflow4idea).

## Other Related Plugins (personal selection)

> **Last update: October, 2018**

- **Presentation Assistant**: This plugin shows name and Win/Mac shortcuts of any action you invoke (View | Descriptions of Actions).

- **Realigner**: The Realigner plugin adds three tools for reformatting code:
  - Join: Removes newlines from selected lines, optionally joining them using a "glue" string.
  - Split: Replaces arbitrary strings with newlines.
  - Wrap / Unwrap: Adds or removes a prefix- and postfix- string to a selection, the current line or each of multiple selected lines. Frequently used wraps can be stored as quick-wrap buttons, hint: quick-wrap buttons can be selected via cursor up/down keys as well.

  Plugin code availabble on [**Github**](https://github.com/kstenschke/realigner-plugin).

- **Shifter**: Detects type of selection, line or keyword at caret and shifts it "up" or "down" on keyboard shortcut. If there's only one shiftable word in a line, it can be shifted without the caret touching it. Lowercase/uppercase or lower case with upper first character of shifted words is maintained. Plugin code available on [**Github**](https://github.com/kstenschke/shifter-plugin)

## Other Related Plugins (to consider)

> **Last update: October, 2018**

- **Gherkin**: Provides support of Gherkin language. Plugin code available on [**Github**](https://github.com/JetBrains/intellij-plugins/tree/master/cucumber)

- **Codota**: Once you install the Codota plugin for IntelliJ and Android studio, you can code faster and smarter using contextual AI-based code completions, right in your IDE. As you code, Codota will suggest full statement completions learned from millions of programs.

- **Cucumber for Java**: This plugin enables Cucumber support with step definitions written in Java. Plugin code available in [**Github**](https://github.com/JetBrains/intellij-plugins/tree/master/cucumber-java).

- **YAML/Ansible support**: YAML/Ansible support with Jinja2 tags. Plugin code available in [**Github**](https://github.com/vermut/intellij-ansible).

















#### Kotlin 
- **JSON To Kotlin Class**: Available on [**Github**](https://github.com/wuseal/JsonToKotlinClass)
- **Detekt IntelliJ Plugin: Indicate warning name in error messages for this static code analysis tool for Kotlin. Available on [**Github**](https://github.com/arturbosch/detekt-intellij-plugin)
- **Kotless Plugin**: Kotlin-native serverless framework. With Kotless you can define AWS lambdas with Kotlin DSL and then deploy them from IntelliJ IDEA. Lambdas are built with Gradle and deployed using Terraform. It is also possible to prepare Terraform scripts and artifacts and deploy Lambdas manually.
- **Kotlin Sequence Debugger**: A Kotlin extension for Java Stream Debugger plugin. The extension enables debugging method chains with Kotlin Sequence usages. To see what's happening in the chain, click on the Trace Current Stream Chain button, which becomes active when debugger stops inside of a chain of Kotlin Sequences API calls.

#### Java

- **Error-prone Compiler Integration**: Allows to build project using 'error-prone java compiler' (https://code.google.com/p/error-prone) to catch common Java mistakes at compile-time.
- **InnerBuilder**: Adds a Builder action to the Generate menu (Alt+Insert) which generates an inner builder class as described in Effective Java. Available on [**Github**](https://github.com/analytically/innerbuilder).

#### CVS (Control Version System)
- **Find Pull Request**: This plugin find the pull request of the selected line. Available on [**Github**](https://github.com/shiraji/find-pull-request).

#### Dart & Flutter
- **Dart**: Support for Dart.
- **Flutter**: Support for developing Flutter applications. Flutter gives developers an easy and productive way to build and deploy cross-platform, high-performance mobile apps on both Android and iOS.
- **Flutter i18n**: This plugin create a binding between your translations from .arb files and your Flutter app.

#### Other

- **Fore Shortcuts**: Forces the user to use keyboard shortcuts by blocking click action and displaying the keyboard shortcut in a popup. Can be toggled on/off from the "Tools" drop down in the menu bar. Available on [**Github**](https://github.com/treytrahin/force-shortcuts-intellij-plugin).
- **Key Promoter X**: Shows the user the keyboard short-cuts when a button is pressed with the mouse. This provides an easy way to learn how to replace tedious mouse work with keyboard keys and helps to transition to a faster, mouse free development. Currently, it supports toolbar buttons, menu buttons, and tool windows and the actions therein. Available on [**Github**](https://github.com/halirutan/IntelliJ-Key-Promoter-X).
- **Markdown Navigator**: Markdown language support for IntelliJ platform. Available on [**Github**](https://github.com/vsch/idea-multimarkdown).


## Additional to consider

### Added: 04/10/18

#### Android
- Android Gradle Metrics: Plugin for showing code quality metrics from gradle tasks within Android Studio. This plugin adds a new menu option Get code metrics report under Analyze which runs code quality tasks on all eligible projects and shows the results in a tool window.
- Android Gradle Metrics - Checkstyle: This contributor adds support for running and showing results from Checkstyle gradle tasks. The plugin requires xml reports and ignoreFailures to be enabled for checkstyle tasks in order to work correctly.
- Android Gradle Metrics - PMD: This contributor adds support for running and showing results from PMD gradle tasks. The plugin requires xml reports and ignoreFailures to be enabled for PMD tasks in order to work correctly.
- Android IntDef code generator: Plugin which generates Android IntDef Annotation for you.
- **Android strings.xml to CSV Converter**: Allows you to translate strings.xml, arrays.xml, plurals.xml into different languages in spreadsheet form, and vice versa. Available on [Github](https://github.com/LiewJunTung/Android-strings-xml-csv-converter)
- EventBus3 IntelliJ Plugin: Provides actions which allow you quickly move around the event bus.(now it only for EventBus 3.x). Available on [Github](https://github.com/likfe/eventbus3-intellij-plugin).
- Exynap: Exynap is an Android Studio plugin which helps you find and implement the code you require in an instant.
- Jimu Mirror: Automatically open previews on connected devices when a layout file is open in the editor. Replay an animation in preview by three-finger tap, or clicking the button "Replay" in Android Studio and better search support in the main screen list.
- Kotlin ANko Converter For Xml: Convert layout xml to kotlin code use anko. Available on [Github](https://github.com/Linyuzai/LayoutXmlConverter).
- **Log Viewer: Better log viewer for Android Studio. Available on [Github](https://github.com/josesamuel/logviewer)
- **Parcelable Code Generator for Kotlin: arcelable Code Generator is a plugin which generates Android Parcelable boilerplate code for kotlin class. Available on [**Github**](https://github.com/nekocode/android-parcelable-intellij-plugin-kotlin)

#### Kotlin
- Cucumber for Kotlin: This plugin enables Cucumber support with step definitions written in Kotlin.
- JSONToKotlinClass: Plugin for Kotlin to convert Json String into Kotlin data class code quickly. Available on [Github](https://github.com/wuseal/JsonToKotlinClass).

#### Java
- CheckStyle-IDEA: This plugin provides both real-time and on-demand scanning of Java files with CheckStyle from within IDEA. Available on [Github](https://github.com/jshiell/checkstyle-idea).
- Cucumber for Java: This plugin enables Cucumber support with step definitions written in Java.
- Jackson Generator Plugin: This plugin allows you to generate Jackson ready java files from provided Json formatted string.
- JSON Model Generator: Tool to covert JSON string to Java class.
- Lombok Plugin: A plugin that adds first-class support for Project Lombok. Available on [Github](https://github.com/mplushnikov/lombok-intellij-plugin).

#### CVS (Control Version System)

- **GitLab Projects**: Simple plugin that is adding support for GitLab specific actions to JetBrain IDEs.
- **GitLab Quick Merge Request**: Quickly create Merge Request for GitLab projects.
- IDEA Git Extensions: Some lazy-guy extensions for Git integration written ASAP and not meant for production.

#### Other
- **CSV Plugin**: Lightweight CSV plugin that supports editing files in CSV/TSV format. Available on [Github](https://github.com/SeeSharpSoft/intellij-csv-validator)
- **Darkyen's Time Tracker**: Track the time spent on a project. Adds a single status bar widget. Available on [Github](https://github.com/Darkyenus/DarkyenusTimeTracker).
- **Emoji Support Plugin: Intellij plugin for supporting auto-complete for Emoji. This plugin heavily rely on emoji-cheat-sheet.com. Available on [Github](https://github.com/shiraji/emoji).
- **HighlightBracketPair**: Color highlight the Bracket Pair in editor. Inspired by Sublime BracketHighlighter Plugin.
- **IDEA Mind Map**: IDE-integrated mind map editor, it is ported version of the NetBeans Mind Map editor. It allows to create and edit mind maps represented by MMD files. The Editor allows to keep simple text notes, web links and links to files just in mind map topics.
- **IntelliJ API Watcher**: The plugin provides 'Find External Usages' action which allows developers to quickly find plugins which use IntelliJ platform classes, methods or fields and 'Check external usages' option in 'Commit Changes' dialog which checks that changes in IntelliJ platform classes don't break external plugins.
- **IntelliJ Code Golf**: This plugin for IntelliJ IDEA allows to carry out competitions on knowledge of IDEA features (e.g. 'write this code using minimum number of keystrokes', 'transform one piece of code to another using minimum number of refactorings').
- **intellij-touch**: MacBook Touch bar support for Intellij. This project has full support for customization of the buttons. . Available on [Github](https://github.com/olivernybroe/intellij-touch)
- **Json Parser**: Simple JSON Parser is an IntelliJ IDE plugin for validation and formatting JSON string.
- **Keymap exporter**: Allows exporting your keymap to a printable PDF document.
- **Protobuf Support**: Google Protobuf support for JetBrains products.
- **SQLDelight**: Sqlite interface generator. Generates interfaces for safely running SQLite statements and mapping back from a cursor.
- **SQLScout (SQL Support)**: First-class SQLite support for Android Studio and IntelliJ IDEA.  View, manage and update SQLite databases in your Android device (in real time) and file system, from Android Studio and IntelliJ IDEA.