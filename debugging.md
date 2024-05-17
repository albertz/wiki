
Stacktraces with maybe some additional information are pretty useful.

This document is also related to [profiling](profiling.md).

# Python

* My own project: [better_exchook](https://github.com/albertz/py_better_exchook)
* My own proof-of-concept project: [pydbattach - attach to running Python process](https://github.com/albertz/pydbattach).
  More references on this topic in the README.
* [LLDB CPython script](https://github.com/malor/cpython-lldb)
* [LLDB Python scripting](https://lldb.llvm.org/use/python.html), [LLDB Python reference](https://lldb.llvm.org/use/python-reference.html)
* [Background ZMQ IPython/Jupyter kernel](https://github.com/albertz/background-zmq-ipython)
* `faulthandler` module (for crashes, like segfault)
* `py-spy dump --pid 12345` (via [py-spy](https://github.com/benfred/py-spy))
* [PyStack](https://bloomberg.github.io/pystack/) (Python). show stack, even including locals.
* See also C below. Esp. if your Python project involves heavy C libs. E.g. load `libSegFault.so` ([example](https://github.com/rwth-i6/returnn/blob/5b8e34ec1fd725d0e20b5b422d213dbf17d9e069/Debug.py#L226))
* It can be useful to install a signal handler on SIGUSR1 and then print all stacktraces from all threads (via `better_exchook`).
* See also [profiling](profiling.md).

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

