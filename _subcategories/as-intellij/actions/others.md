---
id: others
layout: page
title: Others
sidebar: true
category: actions
---
# Other actions


#### Table of Contents

- [__Hide and Restore Windows__](#hide-and-restore-windows)
- [__Presentation mode__](#presentation-mode)
- [__Distraction mode__](#distraction-mode)
- [__Live templates and Code Completion__](#live-templates-and-code-completion)
- [__Documentation__](#documentation)


<br>

### Hide and Restore windows

You can define a default layout using the Menu Bar.

Because of the debugger and Android Monitor opens by itself, sometimes, you want to close those
windows rapidly. Well using:

`⌘ + ⇧ + f12` you will hide all the windows in order to be focused on the Editor, but if you want to restore the layout you've been saved as default, you only need to use `⌘ + f12`

### Presentation mode

`⌃ + ⌥ + ⌘ + P` (__Custom keymap__)

### Distraction mode

`⌃ + ⌥ + ⌘ + F` (__Custom keymap__)

<br>

### Live templates and code completion

- __Live templates__

  `⌘ + j`

<br>

<a name="documentation">

### Documentation

Using `F1` key in code/resources, you will be able to see documentation of the method/class resource in which the cursor is placed to:

![Layout sample](/assets/images/images/actions-layout-documentation.png)
![Class sample](/assets/images/images/actions-class-documentation.png)

If you use it for styles, it also tells you the entire inheritance structure of the selected style

![Styles sample](/assets/images/images/styles-documentation.png)







<br><br><br><br><br><br><br><br>

- [__Structural Search, Replace, and Inspection__](#structural-search-replace-and-inspection)

### Structural Search, Replace, and Inspection (THIS MUST BE IN NAVIGATION SECTION)

It allows you to search for, and replace, code patterns (based on templates). Very useful for code smells.

// WORK ON THIS SECTION, LOOKING AT THE VIDEO [__here__](https://youtu.be/Y2GC6P5hPeA?t=411)

An example could be:
```
Timber.log($text$)
```

// THIS TEXT IS COPIED. DELETE
Moreover you can enable `Structural Search Inspection`. You can then
save a Structural Search Templates that will flag code that matches that pattern
warning, displaying the hint text you provide.

Even more powerfully, you can create Structural Replace Templates. Like
Structure Search Templates, the pattern will be flagged as a warning — but in
this case, the replacement code will be offered as a quick fix!

This is perfect for creating quick fixes for deprecated code, or common
anti-patterns in code your reviewing, or which is being submitted by other team
members.










- [Default](#default)
- [Custom](#custom)

<br>

### Default

- #### Hide all windows

  It's ideal for presentations or whenever you want to get focused only on the code

- #### Clipboard buffer

  [__Source__](https://stanfy.com/blog/use-android-studio-like-a-pro/)

  Shift+Cmd+V

- #### New scratch file

  [__Source__](https://stanfy.com/blog/use-android-studio-like-a-pro/)

Every time  you need to open an external text editor just to edit some text before pasting it into a code editor, you should use a scratch buffer. You can easily create a new buffer with the “Find command by name” dialog. Also, when you close the buffer you always can reopen it with the “Recently edited files” panel.

In addition to this feature AS also has a scratch files function. The main difference between scratch buffers and files is that with files you can choose the syntax of an edited text and editor will correctly highlight it.


- `⇧ + ⌘ + ↑` ⟹ Stretch to top (Resize Tool Window)
- `⇧ + ⌘ + ↓` ⟹ Stretch to bottom (Resize Tool Window)
- `⇧ + ⌘ + ←` ⟹ Stretch to left  (Resize Tool Window)
- `⇧ + ⌘ + →` ⟹ Stretch to right (Resize Tool Window)



<br>

### Custom

- #### Switch scheme

  [__Source__](https://stanfy.com/blog/use-android-studio-like-a-pro/)

  Helps to switch keymaps and other configurations easily.

  ⌘ + ⇧ + f12 !!!! NO ESTÁ BIEN SEGURO






- [__Android API Level__](https://plugins.jetbrains.com/plugin/8121?pr=) also available on [__Github__](https://github.com/droibit/androidapilevel-plugin)

You presses button on toolbar, or to launch from the following shortcut.

Windows, Linux: Ctrl + Shift + Alt + V
Max: Cmd + Shit + Alt + V







Command ⌘
Shift ⇧
Option ⌥
Control ⌃
Caps Lock ⇪
Fn
← ↑ → ↓
