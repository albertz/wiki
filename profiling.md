# Profiling

Native (C/C++) and Python
(relevant for me now, maybe extend later)
(native maybe enough initially, Python support can maybe be added).

Also see [debugging](debugging.md).

Most importantly Linux.
Probably this is platform dependend.
MacOSX has DTrace.

Common situations:

* Some process behaves strange, is much slower than usual,
    or totally hangs.
    I want to see, where does it hang.

Features I want:

* Be able to attach live to running process,
    without preparation.

* Multi-threading support.
    Although in many cases I'm mostly interested in the main thread
    (or one specific thread).
    Some more clever handling would be nice (although not sure how easy),
    e.g. if that (main) thread is hanging at a mutex,
    I would want to see which thread has the mutex currently,
    and what that thread is doing.
    But this can maybe also be configurable and simple,
    such that it just prints the threads which names match to some regexp.

Existing software:

* [perf](https://en.wikipedia.org/wiki/Perf_(Linux)).

    Run `perf record -p pid` and then `perf report --stdio`.
    Maybe `perf record -g dwarf -p pid`.

* [gperftools](https://github.com/gperftools/gperftools).
    Google.

* gperf. GNU. Needs to be compiled with such support.

* `gdb -p pid`. No real profiling, but helps at least to debug a permanent hang.

* [Sysprof](http://www.sysprof.com/).
    System-wide, i.e. not quite what I want here.

* [IgProf](https://igprof.org/)

* DTrace.

* eBPF, like DTrace, since Linux 4.9.

* ftrace

* LTTng

* [Pyflame](https://github.com/uber/pyflame). For Python.

* [Py-Spy](https://github.com/benfred/py-spy). For Python.


Some useful StackOverflow questions:

* [How can I profile C++ code running on Linux?](https://stackoverflow.com/questions/375913/how-can-i-profile-c)
* [How can I get perf to find symbols in my program](https://stackoverflow.com/questions/10933408/how-can-i-get-perf-to-find-symbols-in-my-program)
* [Can I get the python call stack with the linux perf?](https://stackoverflow.com/questions/26902991/can-i-get-the-python-call-stack-with-the-linux-perf)
