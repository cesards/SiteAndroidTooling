# IDE Plugins

This plugins can either be installed in AS or IntelliJ, so I'll classify the plugins based on Language or Platform

## My recommendation

### Added: 04/10/18

#### Android
- **ADB Idea**: Available on [**Github**](https://github.com/pbreault/adb-idea)
- **Android Butterknife Zelezny**: Plugin for generating ButterKnife injections from selected layout XMLs in activities/fragments/adapters. Available on [**Github**](http://github.com/avast).
- **Android Data Tools**: Plugin for review and edit android app data. 
- **Android Drawable Preview**: Render drawable instead of default icon. Supports binary and vector images.
- **FindViewByMe**: Smart cast checkbox when targeting API 26, generatation of "findViewById" code for activity, support generation of "findViewById" code for fragment, and you can customize root view name. Also support generation of "findViewById" code for ViewHolder. Available on [**Github**](https://github.com/laobie/FindViewByMe)

#### Kotlin 
- **JSON To Kotlin Class**: Available on [**Github**](https://github.com/wuseal/JsonToKotlinClass)
- **Detekt IntelliJ Plugin: Indicate warning name in error messages for this static code analysis tool for Kotlin. Available on [**Github**](https://github.com/arturbosch/detekt-intellij-plugin)
- **Kotless Plugin**: Kotlin-native serverless framework. With Kotless you can define AWS lambdas with Kotlin DSL and then deploy them from IntelliJ IDEA. Lambdas are built with Gradle and deployed using Terraform. It is also possible to prepare Terraform scripts and artifacts and deploy Lambdas manually.
- **Kotlin Sequence Debugger**: A Kotlin extension for Java Stream Debugger plugin. The extension enables debugging method chains with Kotlin Sequence usages. To see what's happening in the chain, click on the Trace Current Stream Chain button, which becomes active when debugger stops inside of a chain of Kotlin Sequences API calls.

#### Java
- **AutoValue plugin**: Provides context menu options, generate menu options and code intentions to generate and manipulate the builder method and/or create method on classes annotated with @AutoValue. Also works with @AutoParcel and @AutoParcelGson annotations. Available on [**Github**](https://github.com/afcastano/AutoValuePlugin).
- **Error-prone Compiler Integration**: Allows to build project using 'error-prone java compiler' (https://code.google.com/p/error-prone) to catch common Java mistakes at compile-time.
- **InnerBuilder**: Adds a Builder action to the Generate menu (Alt+Insert) which generates an inner builder class as described in Effective Java. Available on [**Github**](https://github.com/analytically/innerbuilder).

#### Dart & Flutter
- **Dart**: Support for Dart.
- **Flutter**: Support for developing Flutter applications. Flutter gives developers an easy and productive way to build and deploy cross-platform, high-performance mobile apps on both Android and iOS.
- **Flutter i18n**: This plugin create a binding between your translations from .arb files and your Flutter app.

#### Other
- **Find Pull Request**: This plugin find the pull request of the selected line. Available on [**Github**](https://github.com/shiraji/find-pull-request).
- **Fore Shortcuts**: Forces the user to use keyboard shortcuts by blocking click action and displaying the keyboard shortcut in a popup. Can be toggled on/off from the "Tools" drop down in the menu bar. Available on [**Github**](https://github.com/treytrahin/force-shortcuts-intellij-plugin).
- **Key Promoter X**: Shows the user the keyboard short-cuts when a button is pressed with the mouse. This provides an easy way to learn how to replace tedious mouse work with keyboard keys and helps to transition to a faster, mouse free development. Currently, it supports toolbar buttons, menu buttons, and tool windows and the actions therein. Available on [**Github**](https://github.com/halirutan/IntelliJ-Key-Promoter-X).
- **Markdown Navigator**: Markdown language support for IntelliJ platform. Available on [**Github**](https://github.com/vsch/idea-multimarkdown).
- **Presentation Assistant**: This plugin shows name and Win/Mac shortcuts of any action you invoke (View | Descriptions of Actions).

## Additional to consider

### Added: 04/10/18

#### Android
- Android Gradle Metrics: Plugin for showing code quality metrics from gradle tasks within Android Studio. This plugin adds a new menu option Get code metrics report under Analyze which runs code quality tasks on all eligible projects and shows the results in a tool window.
- Android Gradle Metrics - Checkstyle: This contributor adds support for running and showing results from Checkstyle gradle tasks. The plugin requires xml reports and ignoreFailures to be enabled for checkstyle tasks in order to work correctly.
- Android Gradle Metrics - PMD: This contributor adds support for running and showing results from PMD gradle tasks. The plugin requires xml reports and ignoreFailures to be enabled for PMD tasks in order to work correctly.
- Android IntDef code generator: Plugin which generates Android IntDef Annotation for you.
- Android strings.xml to CSV Converter: Allows you to translate strings.xml, arrays.xml, plurals.xml into different languages in spreadsheet form, and vice versa. Available on [Github](https://github.com/LiewJunTung/Android-strings-xml-csv-converter)
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
- GSONFormat: Quickly to convert a JSON string to an InnerClassEntity class.
- Jackson Generator Plugin: This plugin allows you to generate Jackson ready java files from provided Json formatted string.
- JSON Model Generator: Tool to covert JSON string to Java class.
- Lombok Plugin: A plugin that adds first-class support for Project Lombok. Available on [Github](https://github.com/mplushnikov/lombok-intellij-plugin).

#### CVS (Control Version System)
- GitLab Projects: Simple plugin that is adding support for GitLab specific actions to JetBrain IDEs.
- GitLab Quick Merge Request: Quickly create Merge Request for GitLab projects.
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