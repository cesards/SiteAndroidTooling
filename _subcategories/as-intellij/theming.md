---
id: theming
layout: page
title: AS/IntelliJ Theming
sidebar: true
---



Appearance:

From IntelliJ IDEA 2018.2 you can use the dark window headers option from the appearance headers.
It would be better if the windows didn't have headers at all.

![](https://d3nmt5vlzunoa1.cloudfront.net/idea/files/2018/06/image3-1.png)




#### Table of contents

- [Tips](#tips)
- [IDE Appearance](#ide-appearance)
  - [Theming](#theming)
  - [Widescreen enabled](#widescreen-enabled)
  - [Show memory indicator](#show-memory-indicator)
  - [Side-by-side layout on the left/right](#side-by-side-layout-on-the-leftright)
  - [Override default fonts](#override-default-fonts)
  - [Hide Views from the IDE](#hide-views-from-the-ide)
- [Editor](#editor)
  - [Colors & fonts](#colors--fonts)
  - [Disable tabs](#disable-tabs)
  - [Hide line numbers](#hide-line-numbers)
  - [Optimize imports on the fly](#optimize-imports-on-the-fly)

<br>

### Tips

- I use it frequently - dark theme when indoors, light theme in bright daylight, usually on the bus.

Actions -> Color Scheme -> Choose the color scheme you want. WE COULD USE A HOTKEY FOR THAT

There is, it's just Ctrl on Mac, not command. Ctrl-` brings a list, up arrow to select the last item, then enter to select the alternate.

### IDE Appearance

More information about Appearance tweaks [__here__](https://www.jetbrains.com/help/phpstorm/2016.1/appearance.html)

<br>

#### Theming

There are some websites out there (like [Color Themes](www.color-themes.com)) to pick up colors for your favourite IDE.

If you want to import your `.icls` files, you have to copy the files to: (Mac OS X)

```
~/Library/Preferences/AndroidStudioX.X/colors
~/Library/Preferences/IdeaICX.X/colors
```

A recommended but not finished theme is [Material Theme UI Fork](https://plugins.jetbrains.com/plugin/9377-material-theme-ui-fork)

Other recommended themes:

- [JavaDev](http://color-themes.com/?view=theme&id=563a1a9480b4acf11273aee3)

The only drawback about using Darcula is you could have more screen reflections, but you can make difference between code colors, which is much better.

```
Appearance & Behaviour
    - Appearance
        └── Theme: Darcula
```

<br>

#### Widescreen enabled

If this check box is selected, the way the tool windows are positioned is optimized for a wide-screen display. Widescreen tool window layout is OFF:

```
Appearance & Behaviour
    - Appearance
        └── ✓ Widescreen tool window layout
```

<br>

#### Show memory indicator

Show memory indicator	Select this check box to show the Memory Indicator on the Status Bar.

```
Appearance & Behaviour
    - Appearance
        └── ✓ Show memory indicator
```

<br>

#### Side-by-side layout on the left/right

When these check boxes are selected, the way the tool windows are positioned is optimized for a wide-screen display.

```
Appearance & Behaviour
    - Appearance
        └── ✓ Side-by-side layout on the left
```

<br>

#### Override default fonts

Select this check box to enable specifying font family and size to be used instead of the default one.

Take a look to the [__fonts__](#fonts) section to have an idea of which fonts you could use.

```
Appearance & Behaviour
    - Appearance
        └── ✓ Override default fonts by (not recommended)
               Name: Dejavu Sans - Font Size: 14 (Very good readability)
```

Even if the IDE says it's not recommended, we can appreciate a big difference using a custom font in order to improve the readability of your code.

Remember that, since IntelliJ IDEA 2016.2 and Android Studio 2.2, [__font ligatures__](https://goo.gl/al5j9C) are enabled.

There a few options I would recommend:

[__FiraCode__](https://github.com/tonsky/FiraCode) (**current**)
[__Hasklig__](https://github.com/i-tu/Hasklig)
[__Monoid__](http://larsenwork.com/monoid/)

You can download some very good code fonts: [__here__](https://github.com/chrissimpkins/codeface)

Best font codes related to Android programming:

- Panic Sans Mono
- Inconsolata LGC
- Dejavu Sans Mono __(fits well)__
- [__Dejavu Sans Mono - Bront__](https://github.com/chrismwendt/bront) __(fits perfect)__
    - `0` has a slash
    - `*` is centered vertically to align with `+`, `-`, and `=`
    - `_` is narrower in order to discern consecutive characters
    - `-` is the same width as `_`
    - `~` is more wavy in order to further differentiate it from `-`
    - `i` has a tail instead of a bilateral serif
    - `l` has no serif on top
    - `%` has a more angled divider
    - `{` and `}` are the same height as `(` and `)`
    - It has [__Powerline__](https://github.com/powerline/powerline) symbols

Other good fonts:

- Source Code Pro
- Consolas
- Inconsolata-g
- Monaco
- Menlo
- Panic Sans

<br>

#### Hide Views from the IDE

Some of the views from the IDE are not going to be very useful if we are familiar to it and we are using wide screens (as we usually do, now a days). We can do this through the Menu bar:

![](/sections/1-theming/img/hide-views.png)

- __Navigation Bar__

Hide the Navigation Bar. It's pretty useless. If you ever wanted, invoked, as show in Navigation keymaps (LINK TO NAVIGATION KEYMAP) using `⌘ + ↑`

More info [__here__](https://youtu.be/eq3KiAH4IBI?t=2288)

- __Toolbar__

Hide the Toolbar. You will get use to use keymaps for all the features you'll use in your day to day work. Remove unnecessary space.

- __Status Bar__

Hide the Status Bar. It's also pretty useless, since you are not going to be looking at memory consumption of the IDE (we all already know it's pretty high). Moreover, there are keymaps for changing the branch easily :-)

<br>

### Editor

#### Colors & fonts

Use a custom font, preferably `Fira Code` (it accepts ligatures)

```
Editor
  - Colors & Fonts
    - Font
      └── ✓ Primary font:
      │       Dejavu Sans Mono - Bront / Size: 17-20 / Line spacing: 1.1-1.2
      └── ✓ Secondary font:
      │        Dejavu Sans Mono - Bront / Menlo
      └── ✓ Enable font ligatures
```

A good secondary font to use could be `Dejavu Sans Mono - Bront` since a monospace sans font is perfect for coding (it contains the same amount of space between letters).

It's also recommended using a big font (from 17 an on) in order to take care of your own wealthness (otherwise you would be looking the screen closely). Also, we should only be focused in one task, so we don't need to be looking at a lot of methods at a time.

__LogCat__

[__Source__](https://plus.google.com/+CyrilMottier/posts/Q6cZdf57cj7)

You can improve the Android LogCat Colors and remember nice colorful Material Colors in order to make difference whenever you need a specific output.

```
Editor
  - Colors & Fonts
    └── Android LogCat

    Verbose --> White:  #FFFFFF
    Error   --> Red:    #F44336
    Assert  --> Purple: #9C27B0
    Warn    --> Yellow: #FFEB3B
    Info    --> Green:  #4CAF50
    Debug   --> Blue:   #2196F3
```

#### Disable tabs

You don't need to have tabs in order to navigate between files. Either you can use keymaps or last used classes or other helpful keymaps to navigate between tabs.

```
Editor
  - General -> Editor Tabs
      └── Tab Appearance
          └── Placement: None
```

More info about why not using tabs, [__here__](https://youtu.be/eq3KiAH4IBI?t=628).

#### Hide line numbers

Even it could be useful for pairi ng purposes, you don't need to have the line numbers shown in the editor, since you can use `⌘ + l` to navigate through lines.

```
Editor
  - General -> Appearance
      └── ✗ Show line numbers
```

#### Optimize imports on the fly

Is it a pain every time you need to import unambiguous manual.

  ```
  Editor
    - General -> Auto Import
      └── ✓ Optimize imports on the fly
      └── ✓ Add unambiguous imports on the fly
  ```

<br>