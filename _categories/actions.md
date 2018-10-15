---
id: actions
layout: page
title: AS/IntelliJ Actions
sidebar: true
descendants: true
---
<!-- sidebar_link: true -->
---


### Unload modules

https://blog.jetbrains.com/idea/2017/06/intellij-idea-2017-2-eap-introduces-unloaded-modules/

This feature is supposed to help you to deal with large codebases by giving you the ability to select what modules you are going to work on in your project. Modules that you are not working with at the moment are marked as Unloaded and IntelliJ IDEA will not index or otherwise touch any files in these modules, which can help to conserve CPU and memory resources.

To access the feature, invoke the Project tree context menu and select Load/Unload Modules:

And now you just select the modules you’d like to work with at the moment.:














For assigning custom Mac Os keymaps, and if you are using Mac OS, I strongly recommend using [**Karabiner**]()

- https://pqrs.org/osx/karabiner/
- https://github.com/pqrs-org/KE-complex_modifications
- https://pqrs.org/osx/karabiner/complex_modifications


I used one of the recommended web triggers to change the caps lock by commnad + option + control + shift in order to avoid clashes with other maps. It works perfectly well, so the guide is based on the actions that you can do with those








# Edition

## Jump outside closing bracket/quote with Tab

In the upcoming IntelliJ IDEA 2018.2, you will be able to navigate outside the closing brackets, or closing quotes, by pressing Tab. To customize this behavior of Tab, go to Preferences | Editor | General | Smart keys and select Jump outside closing brackets/quote with Tab. This will work in Java, Kotlin, Groovy, SQL, and Python files.

![](assets/CHANGE-NAME.gif)


# Debugging

### breakpoint intentions

[**Source**](https://goo.gl/6LfXeZ)

which are available via Alt+Enter. This latest build further enhances this functionality: please welcome new breakpoint intentions that allow filtering by a caller method.

Sometimes it is important to stop at a breakpoint only when a certain condition applies to the call stack. Now, if you filter a breakpoint hit by the caller method, it will stop at a breakpoint only if it’s called from the specified method. (Or, vice versa, it will not stop at a breakpoint if it’s called from that method.)

![](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2018/05/Screen-Shot-2018-05-28-at-12.26.53.png)

You can also set a caller method filter by using the Caller filters field in the Breakpoint dialog.

![](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2018/05/image5.png)

While debugging in IntelliJ IDEA, you can limit the breakpoint to hit only particular object instances, or define the class where you want the breakpoint to be hit or the classes where the breakpoint should not be hit. These nice capabilities, however, required editing the properties of a particular breakpoint by hand – setting different filters, lots of button clicking, and so on.

Now, while debugging a Java project, you have some handy intention actions available:

– stop only in class
– do not stop in class
– stop only in the current object

No more fiddling about with the Breakpoint dialog and its filters! When you’re in a debugging session, simply press Alt+Enter and the IDE will offer you the new breakpoint intentions, along with all the other available intentions!

![](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2018/05/image1-1.png)

# Code refactoring

[**Source**](https://goo.gl/6LfXeZ)

 a new preview panel for the Extract Method refactoring. This can be quite useful when you perform refactoring on code fragments with duplicates.

Invoke the Extract Method refactoring using the shortcut (Ctrl+Alt+M on Windows/Linux or Cmd+Alt+M on macOS) or by selecting Refactor | Extract | Method. The IDE will show you the Extract Method dialog. Click the Preview button to preview all the changes in one place.

The IDE now provides you with an ability to review the results of your refactoring before you make any actual changes.

![](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2018/05/image2.png)





Command ⌘
Shift ⇧
Option ⌥
Control ⌃
Caps Lock ⇪
Fn
← ↑ → ↓

⌘ ↵ ⇥ ⌫ ↓


REPARTIR ENTRE LOS DIFERENTES ACTIONS

<a name="keymaps">
### Keymaps

- cmd + shift + 8 AND shift + arrow down (using column mode)

- cmd + F8 => put a breakpoint.
- shift + cmd + F8 => remove breakpoints.

- cmd + J => Live template
- cmd + alt + J => Surround templates

Shift + Shift (Search everywhere) and then use tab to navigate between different kind of objects not to press down much times

__Custom__
- `⌃ + ⌥ + ⌘ + F` => Toggle Distraction Free mode.
- `⌃ + ⌥ + ⌘ + A` => Attach debugger to android process.
- `⌃ + ⌥ + ⌘ + G` => Sync Project with Gradle Files
- `⌃ + ⌥ + ⌘ + C` => Compare with branch (Git).
- `⌃ + ⌥ + ⌘ + H` => Show History (Local - Version control).
- `⌃ + ⌥ + ⌘ + S` => Show History for Selection (Version control).
- `⌃ + ⌥ + ⌘ + R` => Resolve conflicts (Git).
- `⌃ + ⌥ + ⌘ + D` => Split Vertically.
- `⌃ + ⌥ + ⌘ + M` => Mute breakpoints.



http://www.developerphil.com/android-studio-tips-of-the-day-roundup-3/
