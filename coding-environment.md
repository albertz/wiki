# Playground

The best way to learn new things is to play around with them.
You should have some playground.
You should make it very simple for yourself
to just start a new empty project, or file,
and type in some random code, and try it out.

For shorter things, I usually do that in my public [playground repo](https://github.com/albertz/playground).


# Read existing code

This greatly helps learning how other people write, common conventions, it gets you ideas, etc.
This will greatly improve your own coding style.
You can learn infinitely many things this way, depending how deep you want to dive.
You will see how different coding styles can be,
how well organized a project can be or how unorganized,
you will see how an old project has evolved over time,
and much historical garbage there is in.

Many projects are easily browsable directly on GitHub.
GitHub has improved the browsing experience to some degree
(it sometimes works now to click on functions to get to their definition).
If you get more serious about some project,
it is much more comfortable to checkout the code locally,
and use some IDE (e.g. PyCharm for Python code, or QtCreator for C++),
to easily jump to definitions, to easily find usages of functions/attributes, etc.

There are also external code reviews.
E.g. [Fabien Sanglard](https://fabiensanglard.net/) has gained certain fame
of doing very nice code reviews, mostly for games, such as Quake and Doom.
E.g. check out [Quake 3](https://fabiensanglard.net/quake3/).
I can very much recommend these code reviews.

## How to read the code?

Many projects are big, and you cannot just read all.
Reading from start to end is also not such a good idea.
There are different approaches, and probably you would do a mixture of them.

* Start from `main`, dive deeper and deeper into parts.
  Not really breadth first search nor depth first search
  but rather you would selectively go to interesting functions.
* Get an overview of the directory and file structure,
  and randomly go into files of interest.
* For classes or functions of interest, find their usages,
  and understand how they are used.
  Continue this until you reach `main` at some point.
  This is kind of the opposite of starting from `main`.

## Recommended projects

This is not meant to be complete.
This will also depend on your interests and backgrounds.

* Linux kernel. C code. Very big. Style somewhat inconsistent, depending on the part.
* Chrome / Chromium. C++. Very big. Mostly clean code, consistent style.
* Firefox. C++. Very big. Older than Chrome (you will notice).
* Quake 1, 2, 3, and also Doom, basically all id engines. Mostly C.
  Very clean code, very easy to understand. Highly recommended.
* TensorFlow. C++. Very big. Mostly clean code, consistent style.

### TensorFlow

This is an example of browsing locally through the TensorFlow code.

Experience KDevelop 5.5.0 (via Ubuntu 20.04), opening TensorFlow (1.15.2, Git checkout).
- Clicked open/import project, selected TF directory.
- Parsing takes very long.
- Does not find include files. Added custom include path.
- Parsing still takes very long (>2h. maybe it hangs, not sure).

Experience QtCreator 4.11.0 (via Ubuntu 20.04), opening TensorFlow (1.15.2, Git checkout).
- Import existing project by directory
- Parsing very fast (10 secs)
- Does not find include files.
  Needed to modify include paths (QtCreator .includes file).
  Removed all entries, just added `.`.
  That still was missing a few, so I also added:
  `/home/az/.local/lib/python3.7/site-packages/tensorflow_core/include`
  and `/usr/lib/llvm-10/lib/clang/10.0.0/include`.
- Parsing again very fast (10 secs), now all seems fine.
- Some strange errors/crashes with clangbackend, but seems fine though/now.
