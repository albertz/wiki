# Idea

* Write code for logic of some application.
* User interface (GUI) automatically derived, e.g. from classes.
   * Attributes are shown.
   * Methods become clickable buttons.

## Some problems

* Not all attributes, objects, classes, methods should be shown.
  Some or just relevant for the internal code.
  Distinction public / private in many languages is not enough
  -- not all public attribs/methods should be shown.
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
* Event system to signal object/attribute updates
* API for dynamic/big content (list, dict)
  * Show partial content, make scrollable or so
* Throw some AI into the mix?


# Related projects

* MusicPlayer GUI
  ([Traits](https://github.com/albertz/music-player/blob/master/src/Traits.py),
   [UserAttrib](https://github.com/albertz/music-player/blob/master/src/UserAttrib.py),
   [GUI](https://github.com/albertz/music-player/blob/master/src/gui.py))
* [IPython Traitlets](https://github.com/ipython/traitlets) (used in IPython/Jupyter)
* [Enthought Traits](https://github.com/enthought/traits) and [TraitsUI](https://github.com/enthought/traitsui) (for GUIs)
