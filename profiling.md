# Profiling

Native (C/C++) and Python
(relevant for me now, maybe extend later)
(native maybe enough initially, Python support can maybe be added).

Also see [debugging](debugging.md).

Most importantly Linux.
Probably this is platform dependend.
MacOSX has DTrace.
(Windows has [UIforETW](https://github.com/google/UIforETW/). See the [randomascii blog](https://randomascii.wordpress.com/).)
Linux also has eBPF now.

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

* [perf](https://en.wikipedia.org/wiki/Perf_(Linux)) (C).
    Run `perf record -p pid` and then `perf report --stdio`.
    Maybe `perf record -g dwarf -p pid`.
* [gperftools](https://github.com/gperftools/gperftools) (C).
    Google.
* gperf (C). GNU. Needs to be compiled with such support.
* `gdb -p pid` (C). No real profiling, but helps at least to debug a permanent hang.
* [Sysprof](http://www.sysprof.com/) (C).
    System-wide, i.e. not quite what I want here.
* [IgProf](https://igprof.org/) (C)
* DTrace (C).
* eBPF (C, native), like DTrace, since Linux 4.9.
* ftrace (C)
* LTTng (C)
* [magic-trace](https://github.com/janestreet/magic-trace) (C)
* [Pyflame](https://github.com/uber/pyflame) (Python). deprecated.
* [Py-Spy](https://github.com/benfred/py-spy) (Python). CPU. Fast.
* [PyStack](https://bloomberg.github.io/pystack/) (Python). show stack, even including locals.
* [austin](https://github.com/P403n1x87/austin) (Python). CPU+memory. Fast.
* [memray](https://github.com/bloomberg/memray) (Python). Memory.
  [HN](https://news.ycombinator.com/item?id=31102089).
* [Scalene](https://github.com/plasma-umass/scalene) (Python). CPU+GPU+memory. Fast.
* Tracing UI: [Perfetto](https://ui.perfetto.dev/) with [Chromium Event JSON Format](https://docs.google.com/document/d/1CvAClvFfyA5R-PhYUmn5OOQtYMH4h6I0nSsKchNAySU/preview), [Fuchsia Trace Format](https://fuchsia.dev/fuchsia-src/reference/tracing/trace-format), [Perfetto Protobuf](https://github.com/google/perfetto/blob/master/protos/perfetto/trace/perfetto_trace.proto) ([details](https://thume.ca/2023/12/02/tracing-methods/))
* Tracing/profiling UI: [Speedscope](https://www.speedscope.app/) ([GitHub](https://github.com/jlfwong/speedscope))
* GDB scripting: [GEF](https://github.com/hugsy/gef)
* Tracing UI: [magic-trace](https://magic-trace.org/) ([GitHub](https://github.com/janestreet/magic-trace), [blog post](https://blog.janestreet.com/magic-trace/))
* [Tracy](https://github.com/wolfpld/tracy) (C)
* [optick](https://github.com/bombomby/optick) (C)
* [0x.tools](https://0x.tools/) using eBPF ([GitHub](https://github.com/tanelpoder/0xtools), [HN](https://news.ycombinator.com/item?id=40869877))
* [otel-profiling-agent](https://github.com/elastic/otel-profiling-agent) using eBPF, support for many languages including Python
* [Grafana Beyla](https://grafana.com/oss/beyla-ebpf/) eBPF-based, supports Python

Some useful StackOverflow questions:

* [How can I profile C++ code running on Linux?](https://stackoverflow.com/questions/375913/how-can-i-profile-c)
* [How can I get perf to find symbols in my program](https://stackoverflow.com/questions/10933408/how-can-i-get-perf-to-find-symbols-in-my-program)
* [Can I get the python call stack with the linux perf?](https://stackoverflow.com/questions/26902991/can-i-get-the-python-call-stack-with-the-linux-perf)

Other refs:

* [Tristan Hume - All my favorite tracing tools: eBPF, QEMU, Perfetto, new ones I built and more](https://thume.ca/2023/12/02/tracing-methods/)
