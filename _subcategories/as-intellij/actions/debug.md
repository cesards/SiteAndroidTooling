---
id: actions-debug
layout: page
title: Debug
sidebar: true
category: actions
---

# Debug actions


#### Table of Contents

- [__Compile__](#compile)
- [__Run__](#run)
- [__Custom Rendering for Objects when Evaluating Expressions__](#custom-rendering-for-object-when-evaluating-expressions)

<br>

### Compile

Action to compile the selected source file or all the source files in the selected directory.

```
⇧ + ⌘ + F9
```

<br>

### Run

Action to execute all the statements contained in the selected file or console (or terminal, in case of Android). It is intended to work for SQL files or database console.

```
⌃ + R
```

<br>

### Custom Rendering for Objects when Evaluating Expressions

[__Source__](https://goo.gl/l4DHsh)

Custom rendering for objects while you are evaluating expressions.

Using debugger, objects are displayed using their `.toString()` value. If anytime
we need to evaluate collections, using a custom renderer for an specific object
type to understand their state it's the right solution:

![](https://cdn-images-1.medium.com/max/800/1*D6xJW1DalD9K8miVemhmAg.gif)


<br>




- [Default](#default)
- [Custom](#custom)

<br>

### Default

<br>

### Custom

- analyze stacktrace

It adds clickable list of the files.

In case you are using Proguard, you can use the checkbox `Unscramble stacktrace` in order to
get the obfuscated code.

- Customize Data Views

  Enables the chance of transfrom to actual objects the `toString()` list of any kind of objects.

  Open the dialog, add a new `Java Data Type Renderer` and then apply the renderer to the object you want
  to transform

  More info [__here__](https://youtu.be/Y2GC6P5hPeA?t=1489)

  __IT ONLY WORKS FOR RECYCLER VIEWS???__


- Resolve integer id resources

Just right click on the resource id -> View as -> Type integer meanwhile you are debugging.

More info [__here__](https://youtu.be/Y2GC6P5hPeA?t=1357)

- Evaluate expressions

ALT + f8

- Conditional breakpoints



Command ⌘
Shift ⇧
Option ⌥
Control ⌃
Caps Lock ⇪
Fn
