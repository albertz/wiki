# Idea

* Write code for logic of some application.
* User interface (UI) automatically derived, e.g. from classes.
   * Attributes are shown.
   * Methods become clickable buttons.
* Multiple types of UIs:
   * GUI for Windows, Mac, Linux (e.g. using Qt, or the native frameworks)
   * Web interface
   * Console interface
   * API
   * ...

## Some problems

* Not all attributes, objects, classes, methods should be shown.
  Some or just relevant for the internal code.
  Distinction public / private in many languages is not enough
  -- not all public attribs/methods should be shown.
  * If there are multiple UIs, maybe accessed by multiple different users,
    might even needs some access control...
* How to show them? Many different ways, e.g. just the order/organization on screen.
* How to delegate updates on the object (via GUI independent logic) back to the GUI
* Extra care in multi-threaded environment
* Some objects are dynamic or too big
  (list, dict, or maybe just iterable, infinite list),
  cannot load & show all, need to load it dynamically

## Some solutions

* Add extra information (often called "traits"):
  * What should be visible to the user
  * Attribute: Just readable, or also writeable
  * How to show it
  * Where to show it
* Event system to signal object/attribute updates,
  to keep internal state & GUI in sync
* API for dynamic/big content (list, dict)
  * Show partial content, make scrollable or so
* Throw some AI into the mix?

These solutions come with their own further problems.
Most importantly:

* You don't want to mix too much UI logic into your app logic,
  or if possible very little only, or none.
  * (But defining it externally is maybe also not nice?)
* It might all become too complicated to handle.
  Lot's of edge cases, which then probably require lots of ugly hacks.
* Some solutions tend to do too much magic,
  which makes it hard to understand, and then also hard to debug,
  esp in cases where it is not quite as expected/wanted.


# Related projects

* MusicPlayer GUI
  ([Traits](https://github.com/albertz/music-player/blob/master/src/Traits.py),
   [UserAttrib](https://github.com/albertz/music-player/blob/master/src/UserAttrib.py),
   [GUI](https://github.com/albertz/music-player/blob/master/src/gui.py))
* [IPython Traitlets](https://github.com/ipython/traitlets) (used in IPython/Jupyter)
* [Enthought Traits](https://github.com/enthought/traits) and [TraitsUI](https://github.com/enthought/traitsui) (for GUIs)
* [GoKi Views](https://github.com/goki/gi/wiki/Views)
* [Glamorous Toolkit](https://gtoolkit.com/)
* Smalltalk / [Pharo](https://pharo.org/) (Live customizable objects inspection)
