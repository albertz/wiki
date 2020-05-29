# Playground

The best way to learn new things is to play around with them.
You should have some playground.
You should make it very simple for yourself
to just start a new empty project, or file,
and type in some random code, and try it out.

For shorter things, I usually do that in my public [playground repo](https://github.com/albertz/playground).

While playing around, you will usually run into problems of various kind.
You usually would get some sort of error or exception or crash,
or it does not work the way you expect.
Now you need to do some *debugging* (also see [here](debugging.md)).
Some web search for the error often helps.
If that does not get you further,
it usually helps to formulate some very specific question about your problem,
and post it on [StackOverflow](https://stackoverflow.com/).
I do that all the time ([my questions](https://stackoverflow.com/users/133374/albert?tab=questions&sort=newest)).
If your problem does not show up in a web search,
it is even helpful for other people if you post this problem / question on StackOverflow
(even if you figured it already out)
because there are likely other people on the earth who run into the same problem,
and who would do the same search --
now they would likely end up on your StackOverflow question.
If you figured it out meanwhile, you can simply post the solution as an answer to your own StackOverflow question.


# Write a game

This is an extension to your playground, but would be a complete project.
It probably makes more sense to organize it as that, i.e. create an own independent directory / Git repo for it.
[Writing a game is a great learning playground](http://www.openlierox.net/wiki/index.php/Why_game_development_is_a_great_learning_playground).
I collected a lot of useful resources, and also other code/project examples
[here](https://github.com/albertz/Coding-Game-Intro).


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
* CPython. C. Medium size. Mostly clean code, easy to understand.
* TensorFlow. Core in C++. Another layer of Python on-top. Very big. Mostly clean code, consistent style.
* PyTorch. C++ and Python, similar as TensorFlow but much smaller.

Check out [GitHub explore](https://github.com/explore),
or [Fabien Sanglard](https://fabiensanglard.net/).
Follow other interesting developers
(e.g. [John Carmack](https://en.wikipedia.org/wiki/John_Carmack) (Quake, Doom),
[Fabrice Bellard](https://en.wikipedia.org/wiki/Fabrice_Bellard) (FFmpeg, QEMU),
[Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds) (Linux),
[Guido van Rossum](https://en.wikipedia.org/wiki/Guido_van_Rossum) (Python), ...).
(You can also check out [my GitHub repos](https://github.com/albertz),
but they cannot really be compared to these big names.)

### TensorFlow

This is an example of browsing locally through the TensorFlow code.

Experience KDevelop 5.5.0 (via Ubuntu 20.04), opening TensorFlow (1.15.2, Git checkout).
- Clicked open/import project, selected TF directory.
- Parsing takes very long.
- Does not find include files. Added custom include path.
- Parsing still takes very long (>2h. maybe it hangs, not sure).
- Conclusion: Not sure. Maybe I just misconfigured something. However, not useful in this state.

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
- Conclusion: Works very well, very fast, very useful.


# Contribute to existing projects

The simplest way to contribute is to write a bug report (e.g. GitHub issue).
Try to provide the relevant information needed for fixing, such that it is helpful.

You could also try to improve the documentation, or wiki.

Of course, you could also contribute to the code itself.
E.g. most common is by fixing a bug.
It can be a great exercise when you observe some bug in some open source software you use,
to try to fix this bug yourself.
That means that you first need to get familar with the code (see reading code above),
and then understand the problem (i.e. [debug it](debugging.md)),
and then try to actually fix it.

This could also be a new feature.

When contributing to the code, many projects have some own rules for that
(it is common that they provide some `CONTRIBUTING` file, or some other document where this is covered).
But there are some very common rules which almost always apply:

* Keep the code style consistent (to the existing style).
* Do not break things. (If there are tests, make sure they all run through.)
* If you add some new feature, and there are tests, add tests for your new feature as well.
* If unsure about sth, talk to some of the developers (better before you invest too much work).


# Coding environment

In general, you should always use Git
(or some other version control system (VCS), but I would recommend Git),
and follow the common (Git/VCS) conventions,
i.e. add only the source text files to it, or other small files, not the build products, etc.

What IDE to use?
Many people will have their own favorites here. This is a whole topic on its own.
I'm not going too much into that here.
I just state that I would recommend PyCharm for Python development,
and QtCreator for C++.
VSCode is also nice for smaller scripts or text files.

Also see the TensorFlow example above.
