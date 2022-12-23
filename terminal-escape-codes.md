
# Terminal emulator escape codes



Existing escape code lists and extensions:

* [iTerm2 list, with some extended escape codes](https://www.iterm2.com/documentation-escape-codes.html)
* [hterm list](https://github.com/chromium/hterm/blob/master/doc/ControlSequences.md)
* [Kitty list](https://sw.kovidgoyal.net/kitty/protocol-extensions.html)
* [Changing cursor shape](http://vim.wikia.com/wiki/Change_cursor_shape_in_different_modes)
* [Superscript/subscript](https://stackoverflow.com/questions/42473819/are-there-ansi-escape-sequences-for-superscript-and-subscript)


## Text with ANSI colors

* [list](https://stackoverflow.com/questions/4842424/list-of-ansi-color-escape-sequences)
* [Determining whether the background is light or dark](https://stackoverflow.com/a/54652367/133374)
  ([ex](https://github.com/neovim/neovim/issues/2764), [ex](https://github.com/vim/vim/blob/05c00c038bc16e862e17f9e5c8d5a72af6cf7788/src/option.c#L3974))


## Hyperlinks

* [overview in various emulators](https://gist.github.com/egmontkob/eb114294efbcd5adb1944c9f3cb5feda)


## Images

* [terminal-wg issue](https://gitlab.freedesktop.org/terminal-wg/specifications/issues/12)
* iTerm2: OSC 1337. only iTerm2 currently.
  Maybe others (xterm.js etc) will follow.
  [documentation](http://iterm2.com/documentation-images.html)
* Kitty: [Terminal graphics protocol](https://sw.kovidgoyal.net/kitty/graphics-protocol/).
  ([Issue with discussions](https://github.com/kovidgoyal/kitty/issues/33).)
* mintty: [image-support](https://github.com/mintty/mintty/wiki/CtrlSeqs#image-support)
* [xterm.js issue](https://github.com/xtermjs/xterm.js/issues/614)
* [IPython issue](https://github.com/ipython/ipython/pull/10610)
* [neofetch source code](https://github.com/dylanaraps/neofetch/blob/master/neofetch) (see `display_image`)

### Sixel

From modern and widely used terminal emulators, only Xterm supports it.

* [Wikipedia](https://en.wikipedia.org/wiki/Sixel)
* [libsixel](https://github.com/saitoha/libsixel)
* [Gnome issue](https://bugzilla.gnome.org/show_bug.cgi?id=729204)
* [Konsole issue](https://bugs.kde.org/show_bug.cgi?id=391781)


## Current directory information

* [iTerm2](https://gitlab.com/gnachman/iterm2/issues/3939)


## Text folding

* [StackOverflow question](https://stackoverflow.com/questions/52812618/ansi-escape-sequence-for-collapsing-folding-text-maybe-hierarchically)
* [xterm.js feature request](https://github.com/xtermjs/xterm.js/issues/1875)
* [terminal-wg issue](https://gitlab.freedesktop.org/terminal-wg/specifications/issues/3)

## Desktop notification

* [terminal-wg issue](https://gitlab.freedesktop.org/terminal-wg/specifications/issues/13)


## Generic HTML

No standard at all.
Some HTML terminal emulators support this.

* [DomTerm](https://domterm.org/) ([article](https://opensource.com/article/18/1/introduction-domterm-terminal-emulator), [article](https://lwn.net/Articles/670062/))
* [GraphTerm](https://github.com/mitotic/graphterm)
* [GateOne](https://github.com/liftoff/GateOne)
