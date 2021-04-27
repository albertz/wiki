
# Logging

Of apps, tools, scripts, etc.
Usually to stdout. Related are the [terminal escape codes](terminal-escape-codes.md).

Further *very* helpful features I want from logging:

* Foldable text! This is maybe one of the most important features.
  E.g. there could be an error message, and folded away the stacktrace.
  The stacktrace could have the local variables (like [better_exchook](https://pypi.org/project/better_exchook/))
  but they are also folded away.
  In general, you want to have a short overview of the log, and not see all details,
  but be able to see the details which are of interest to you.

* Different logging levels.
  It would be nice to store at highest level,
  but visualize only the lowest level,
  and be able to dynamically switch to higher level.

* Should work seamlessly together with code which uses:
  - the Python `logging` module
  - simple stdout
    (even external code, or subprocesses, so capture the OS stream)


Possible implementations:

* Foldable text feature request for terminal emulators: e.g. [xterm.js feature request](https://github.com/xtermjs/xterm.js/issues/1875).
  It does not look like this is coming any time soon.
  So this is basically not an option now.
  However, we still can use some of the escape codes suggested there.
  However, the text should be visible just fine in a standard terminal
  (in that case, I guess, just everything would be unfolded).

* Use HTML directly.
  - This could still use simple ANSI escaped stdout text,
    but a JS prefix would deal with automatic conversion/handling
    (not sure if this scales to very large log files, though...).
  - In general, this should work with very large log files.
    (Maybe the HTML conversion logic can first split it in parts...)


Refs:

* [Python logging](https://docs.python.org/3/library/logging.html)
* [Python logging howto](https://docs.python.org/3/howto/logging.html)
* [Python logging cookbook](https://docs.python.org/3/howto/logging-cookbook.html)
* [Capture stdout](https://docs.pytest.org/en/latest/capture.html)
* [ansi2html](https://pypi.org/project/ansi2html/) ([GitHub](https://github.com/ralphbean/ansi2html)):
  convert ANSI terminal escape codes to HTML
  (could be extended by the folding feature)
* [html_logger.py](https://gist.github.com/ColinDuquesnoy/8296508)
* Discuss on [Freenode #Python](https://webchat.freenode.net/)
* [TeXMe (Self-Rendering (live) Markdown)](https://opendocs.github.io/texme/examples/demo.html)
  (Nice because it only needs a small prefix in the HTML,
   and the rest can stay standard stdout, so can also be read in terminal.
   The same property would be useful for logging to HTML.)


# Structured logging

Can use nested hierarchies.
Very straight-forward extension of foldable data.
Straight-forward would be to use sth like JSON.
E.g. a stacktrace would be very straight-forward to save as structured data.

References:

* [Python structlog](https://github.com/hynek/structlog)
* [python-json-logger](https://github.com/madzak/python-json-logger)
* [Fluentd](https://www.fluentd.org/)
* [Kibana](https://www.elastic.co/kibana)
* [Message Templates](https://messagetemplates.org/)
* Maybe use systemd journald, or its file format?
* Maybe directly dump to some binary JSON-like format?
* TensorFlow event files?
