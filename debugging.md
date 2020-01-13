
Stacktraces with maybe some additional information are pretty useful.

This document is also related to [profiling](profiling.md).

# Python

* My own project: [better_exchook](https://github.com/albertz/py_better_exchook)
* [LLDB CPython script](https://github.com/malor/cpython-lldb)
* [LLDB Python scripting](https://lldb.llvm.org/use/python.html), [LLDB Python reference](https://lldb.llvm.org/use/python-reference.html)
* `faulthandler` module.

# C/C++ and other native

* LLDB and GDB.
* Otherwise `backtrace_symbols_fd()` etc.
* [Google Breakpad](https://chromium.googlesource.com/breakpad/breakpad/).
* `libSegFault` library (on Linux)
