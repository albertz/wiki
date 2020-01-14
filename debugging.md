
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

From [CppCon 2018: Greg Law “Debugging Linux C++”](https://www.youtube.com/watch?v=V1t6faOKjuQ&feature=youtu.be&t=1s):
* GDB
  - Ctrl X-A: curses interface
  - GDB has Python
  - `~/.gdbinit` (`set history save on`, `set print pretty on`)
  - Breakpoints / watchpoints (read/writes on var, conditional)
  - `dprintf` (add printf at runtime)
  - Catchpoints
  - Remote debugging, gdbserver
  - Multiprocess debuggin (`set follow-fork-mode child|parent`, `set detach-on-fork off`)
  - Temporary breakpoint (`tbreak`), reg-ex breakpoint (`rbreak`)
* Valgrind & Sanitizers
  - memcheck
  - `valgrind --vgdb ...`
  - `clang -g -fsanitize=address foo.c`
* strace (syscall tracing)
* ltrace (dynamic library call tracing)
* ftrace
  - `/sys/kernel/debug/tracing/events/signal/enable` etc
  - `trace-cmd`
* perf trace (similar as strace)
* GDB + rr/Undo
* GDB + Valgrind
* GDB + Asan
* Fortify, compile with `-D_FORTIFY_SOURCE=1`

