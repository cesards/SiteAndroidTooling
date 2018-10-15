---
id: actions-navigation
layout: page
title: Navigation
sidebar: true
category: actions
---
<!-- sidebar_link: true -->
---

# Navigation actions

## Table of contents


  - [Navigate to](#navigate-to)
    - [Symbol lookup](#symbol-lookup)
    - [Search everywhere](#search-everywhere)
    - [Show recent](#show-recent)
    - [Last edited position](#last-edited-position)
    - [Activate navigation bar](#activate-navigation-bar)
    - [File Path](#file-path)
    - [Switching between projects](#switching-between-projects)
    - [Find in Path](#find-in-path)
    - [Find Usages](#find-usages)
    - [Replace in Path](#replace-in-path)
    - [Jump to Source](#jump-to-source)
    - [Browse Type Hierarchy](#browse-type-hierarchy)
    - [Show Breadrumbs](#show-breadrumbs)
    - [Toggle between text/design mode](#toggle-between-textdesign-mode)
    - [Scroll from source](#scroll-from-source)
    - [Default](#default)
    - [Custom](#custom)

<br>

## Navigate to

[__Source__](https://www.youtube.com/watch?v=KsVWdGOnHZU)

- __Class__

  `⌘ + O` (`ctrl + N` for Win/Linux)

- __File__

  `⌘ + ⇧ + O` (`⇧ + ctrl + N` for Win/Linux)

  You can also look for paths (navigate to folders), if you start the search with a directory:
  ```
  /rx/main...
  ```

If you add a colon to the search, in order to go to an specific line in the file/class. I.e:
```
Sched:40
```

### Symbol lookup

[__Source__](https://www.youtube.com/watch?v=KsVWdGOnHZU)

It's very efficient because it allows you to search for symbols across the entire project

`⌥ + ⌘ + O` (`⇧ + Ctrl + Alt + N` for Win/Linux)

You can also filter by namespace in order to get a significant amount of repeated symbols. I.e:

```
OST.sumfl
```

### Search everywhere

`⇧ + ⇧`


### Show recent

- __Files__

  `⌘ + E`

- __Edited files__

  `⌘ + ⇧ + E`

### Last edited position

```
⌘ + ⇧ + ⌫
```

### Activate navigation bar

Invoking the navigation bar you will be able to navigate through the project folders and files

```
⌘ + ↑
```

<br>

### File Path

Action to open the File Path menu. This menu shows the path from the file system root to the selected element with individual directories as the menu items.

![](/assets/images/images/actions-file-path.png)

When you select an item in this menu (e.g. a directory), a file browser (e.g. Windows Explorer or Finder) opens, and the selected item is shown there.

```
⌥ + ⌘ + F12
```


### Switching between projects

```
⌘ + `
```
or

```
⇧ + ⌘ + `
```

<br>

### Find in Path

Action to perform a text search (the __Find in Path__ dialog will open).

```
⇧ + ⌘ + f
```
<br>

### Find Usages

Action to find the usages of the selected item. (The __Find Usages__ dialog will open.)

```
⌥ + F7
```

<br>

### Replace in Path

Action to perform text search-and-replace. (the __Replace in Path__ dialog will open.)

```
⇧ + ⌘ + r
```

<br>

### Jump to Source

Action to open the selected file in the editor. If the file is already open, the corresponding editor tab will become active.

```
⌘ + ↓
```

<br>

### Browse Type Hierarchy

For a file (normally, a class): action to see the class hierarchy for the selected file (class). (The __Hierarchy tool__ window will open.)

Very useful if you want to know more about the object you are working with.

```
⌃ + h
```

<br>

### Show Breadrumbs

Now breadcrumbs work for Java, too, where instead of tags they let you navigate through classes, lambda expressions and methods:

This lets you keep track of your current position and navigate over enclosing classes, lambda expressions and methods.

```
Editor
  - General -> Appearance
      └── ✓ Show breadcrumbs
```

### Toggle between text/design mode

Toggle between the UI designer and the XML editor.

```
⌃ + ⇧ + ←
```

### Scroll from source

You need to install a [__plugin__](https://github.com/luonanqin/intellij-idea-plugins/tree/master/ScrollFromSource) to
have access to this keymap, but it's totally worth it in order to navigate to the source of the file/class you are
working on.

```
⌃ + ⌘ + S
```

or

```
⌥ + ⌘ + S` (__Custom keymap__)
```



↓ → ↑ ←





### Default

- `⌘ + ⇧ + t` ⟹ Navigate to the `Test` class


- `⌘ + [` ⟹ Navigate left

- `⌘ + ]` ⟹ Navigate right

- Navigating to Project Window with ⌘ + 1, you can go back to editor pressing `esc`. Navigating through files
in the `Project Window editor` if you press intro the file will be opened, but if you press `⌘ + ↓` the cursor
will be placed in the editor this time.

- `⌘ + p` ⟹ Navigate to the super method

- `⌘ + b` ⟹ Navigate to declaration of a method
- `⌥ + ⌘ + b` ⟹ Navigate to implementations of a method

- `⇧ + ⌘ + h` ⟹ Navigate through the Method Hierarchy // NEED MORE INFO ON THIS
- `⌃ + ⌘ + h` ⟹ Navigate through the Call Hierarchy // NEED MORE INFO ON THIS

- `⌃ + ↓` ⟹ move cursor down


- `f2` ⟹ Navigate to next highlighted error
- `⇧ + f2` ⟹ Navigate to previous highlighted error

<br>

### Custom





Open file preview when navigating to files: option+space
![](https://pli.io/22GwYw.gif)