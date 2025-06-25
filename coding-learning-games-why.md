# Why game development is a great learning playground

(This is an updated, extended and generalized version of [an article from the OpenLieroX wiki](http://www.openlierox.net/wiki/index.php/Why_game_development_is_a_great_learning_playground)
([Wayback Machine copy](https://web.archive.org/web/20200221020401/http://www.openlierox.net:80/wiki/index.php/Why_game_development_is_a_great_learning_playground)).)

Game development is a great way to learn coding and computer science in general.
You can learn a lot by game development.
And not only about coding itself, but also about advanced algorithms of various sorts and much more.
If you compare it to the learning value of working on any tool or whatever other application,
in most cases you will learn more by developing a game
because games include a very wide area of technics
while most other applications are mostly very limited in the amount of theories and technics involved.


# Related resources

* [Coding Game Intro](https://github.com/albertz/Coding-Game-Intro). Coding Introduction / Tutorial, mostly by writing small little fun games.
* [On Coding](coding.md)
* [On Debugging](debugging.md)
* [On Profiling](profiling.md)
* [Coding for kids](coding-for-kids.md)
* [Quora: Is game development a good way to learn a programming language?](https://www.quora.com/Is-game-development-a-good-way-to-learn-a-programming-language) (yes...)
* [Kshitij Dhar: Why Video Game Programming Is Awesome (And How to Get Started with Creating Your First Game)](https://medium.com/@kshitijdhar12/why-video-game-programming-is-awesome-and-how-to-become-a-game-programmer-12a1cf8ebe79)
* [What is a music player?](https://github.com/albertz/music-player/blob/master/WhatIsAMusicPlayer.md).
  In a similar manner, this article shows that a music player also covers various different aspects.
* [Joshua Barretto: Writing Toy Software Is A Joy](https://blog.jsbarretto.com/post/software-is-joy).
  List of toy programs rated by difficulty and time required.


# Programming languages

Of course the most basic part is the coding itself.
That includes the [programming language](https://en.wikipedia.org/wiki/Programming_language) and getting used to it.
Learning a programming language is not only learning the syntax and semantics - it is also about how you do it right.

In a medium/big sized game (and often even in small),
there are often a bunch of different languages used together.

For example, in the [OpenLieroX project](http://github.com/albertz/openlierox), you will find applications of at least these languages:

* [C++](https://en.wikipedia.org/wiki/C++). Most of the game and its core is written with it.
* [C](https://en.wikipedia.org/wiki/C_(programming_language)). Some rare parts of the game are C code.
* [Assembler](https://en.wikipedia.org/wiki/Assembly_language). Some performance critical parts of the game are written in Asm.
* [Lua](https://en.wikipedia.org/wiki/Lua). We use Lua for ingame scripting.
* [Python](https://en.wikipedia.org/wiki/Python_(programming_language)). The dedicated script and a few other scripts use Python.
* [Bash](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) / [Zsh](https://en.wikipedia.org/wiki/Z_shell). Many scripts to do some management (like preparing release packages and distributing them) are using either Bash or Zsh.
* [CMake](https://en.wikipedia.org/wiki/CMake). Our build system uses it.
* [PHP](https://en.wikipedia.org/wiki/PHP). Our homepage uses it and also the reference implementation of the HTTP masterserver.

But when you are just starting with coding,
for a simpler game project,
any single language is enough.

The programming language doesn't really matter that much for learning.
Don't be scared about C++. It isn't really that complicated.
Or maybe Rust, or Nim, or some of the other newer native languages.
Python is of course also a very good starting language.


# Libraries

Knowing programming languages is not enough.
Most languages also come with their own standard library
but in many cases,
you also need some external libraries or frameworks.

Here a list of libraries that the OpenLieroX core uses:

* [C standard library](https://en.wikipedia.org/wiki/C_standard_library)
* [C++ standard library](https://en.wikipedia.org/wiki/C%2B%2B_Standard_Library) (STL)
* [Boost](https://en.wikipedia.org/wiki/Boost_%28C%2B%2B_libraries%29)
* [SDL](https://en.wikipedia.org/wiki/Simple_DirectMedia_Layer). This is for initialising the window/screen, doing graphics operations and handling user input.
* SDL_image. For some more image formats.
* GD. Another lib for various image formats and image handlings.
* HawkNL. For networking (TCP/UDP).
* [zlib](https://en.wikipedia.org/wiki/Zlib). Compression.
* libzip. ZIP support.
* libxml2. XML support.
* libcurl. HTTP support.
* [OpenAL](https://en.wikipedia.org/wiki/OpenAL). For sound.
* ALUT. For initialising the OpenAL environment and WAV support.
* libvorbis/libogg. For Vorbis OGG support.

For the other languages, mostly only the standard library is used.
  ([Python has a "batteries included" philosophy](https://docs.python.org/3/tutorial/stdlib.html).)

Also see [this list about useful game libraries](https://github.com/albertz/Coding-Game-Intro?tab=readme-ov-file#useful-libraries).


# Cross platform

If you don't want to restrict yourself to only one platform (like Linux or MacOSX or even Windows),
you need to write your code in a way that it is mostly cross platform.

One important point is that the dependencies and libraries you are using are all also cross platform,
i.e. available for most or all platforms.
If you take a look at the list of libraries from above,
you will find that this is mostly the case.

In practice, this is not all.
You will face problems that some things will just behave and work different depending on the platform.
Also the platforms themself are by purpose somewhat different and handle things differently.
So you will still end up in having different solutions and code paths in these cases for different platforms.

By working on a cross platform game like OpenLieroX,
you will learn how to deal with this.
When you use the right libraries,
this is not that much of a problem.


# Architecture independence

This is somewhat related to cross platform.
If you don't want to restrict yourself to one architecture (like [x86](https://en.wikipedia.org/wiki/X86) 32bit)
you need to write your code in a way that it is architecture independent.
As some platforms (like iPhone or Playstation) are naturally running on a different architecture (like [arm](https://en.wikipedia.org/wiki/ARM_architecture_family) or [ppc](https://en.wikipedia.org/wiki/PowerPC)),
you are often forced to write architecture independent if you want to support those.

OpenLieroX should run on pretty much every architecture.
Problems you are facing are for example about [big/little endianness](https://en.wikipedia.org/wiki/Endianness) and 32bit versus 64bit.


# Protocols and file formats

In many cases, knowledge of protocols and file formats can be usefull,
even if a library is doing all the handling for you.
In some cases, you even need to implement some basic support for yourself.

Here a list of protocols or file formats you most likely will at least get a bit in touch with at OpenLieroX:

* [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol), [UDP](https://en.wikipedia.org/wiki/User_Datagram_Protocol)
* [HTTP](https://en.wikipedia.org/wiki/HTTP), [SMTP](https://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol), [DNS](https://en.wikipedia.org/wiki/Domain_Name_System)
* INI, [XML](https://en.wikipedia.org/wiki/XML), MP3

Of course, OpenLieroX introduces also some own protocols (for networking) and file formats (maps and mods).


# Algorithms and data structures

You will need and learn all of the basic [algorithms](https://en.wikipedia.org/wiki/Algorithm) and [data structures](https://en.wikipedia.org/wiki/Data_structure).
That are at least:

* linked lists, hash maps, vectors, stacks, queues, sets, trees
* sort, search, ...


# Graphics

When writing [graphics](https://en.wikipedia.org/wiki/Computer_graphics) related code,
you are dealing with a wide range of topics,
many of them being mathematical.
Despite the mathematical part,
you are often also dealing with performance problems and optimisations
because this is often the most performance critical part.
So you need to learn how to optimise your code and at the same time keep it maintainable.

Depending if your game is [2D](https://en.wikipedia.org/wiki/2D_computer_graphics) or [3D](https://en.wikipedia.org/wiki/3D_computer_graphics),
the type of mathematics you are applying differs a bit
(and probably 3D graphics need even some more deep knowledge of [linear algebra](https://en.wikipedia.org/wiki/Linear_algebra))
but there is also a big intersection.


# User interface

The [user interface](https://en.wikipedia.org/wiki/User_interface) is e.g. the menus, the buttons, the dialogs, etc.


# Audio

You learn about the basic calculation and principles how to calculate the sound modifications when you want to get a 3D sound experience.


# Physics

Most games need some kind of [physics engine](https://en.wikipedia.org/wiki/Physics_engine) to simulate physics of the game world.
For simple games, this is usually often kept very simple.


# Artificial intelligence

Artificial intelligence
The most obvious application of artificial intelligence in games is the computer enemy. AI in games and AI in general is really a topic for itself. Maybe the biggest and most important of all things which you learn by game development but that is up to your own focus.

Also, the subtopics of AI you can apply in a game depends a bit on the type of game,
but in general, a lot of different AI topics can be applied in games.
(The actual topics you will apply in a game are usually much simpler though.)
For example:

* [Planning](https://en.wikipedia.org/wiki/Planning) and [problem solving](https://en.wikipedia.org/wiki/Problem_solving)
* [Searching](https://en.wikipedia.org/wiki/Search_algorithm) and [pathfinding](https://en.wikipedia.org/wiki/Pathfinding) (e.g. [A*](https://en.wikipedia.org/wiki/A*_search_algorithm))
* [Machine learning](https://en.wikipedia.org/wiki/Machine_learning) (all kinds of: [supervised](https://en.wikipedia.org/wiki/Supervised_learning), [reinforced](https://en.wikipedia.org/wiki/Reinforcement_learning) and [unsupervised](https://en.wikipedia.org/wiki/Unsupervised_learning)), [neural networks](https://en.wikipedia.org/wiki/Neural_network_(machine_learning)), [genetic algorithms](https://en.wikipedia.org/wiki/Genetic_algorithm), etc.
* [Knowledge representation](https://en.wikipedia.org/wiki/Knowledge_representation_and_reasoning)
* [Pattern matching](https://en.wikipedia.org/wiki/Pattern_matching) and [recognition](https://en.wikipedia.org/wiki/Pattern_recognition)
* [Cognitive science](https://en.wikipedia.org/wiki/Cognitive_science)
* [Natural language processing](https://en.wikipedia.org/wiki/Natural_language_processing)

OpenLieroX has some advanced searching functions (variant of A* in an almost continuous space) and a bunch of hardcoded strategies and plans.
There could be much more, like a self-learning bot (based on neural networks) or a genetically engineered bot.
Or some basic support of natural language processing so that the bot can chat.


# Game theory

[Game theory](https://en.wikipedia.org/wiki/Game_theory) deals with theoretical questions about strategies and states of games.
If you want to answer questions like if there is a strategy for your game where you always will win - that is game theory.

Game theory also matters for some of the artificial intelligence applications.


# Networking

If you want to support some sort of multiplayer over a network (like the Internet),
you need to know a bit about [networking](https://en.wikipedia.org/wiki/Computer_network).
It is not just about encoding and serializing your data and transfer it somehow over network.
A game often needs very low latency.
You are usually dealing with problems like:

* [synchronisation of time](https://en.wikipedia.org/wiki/Clock_synchronization) (and events in time)
* synchronisation of the game world state
* unreliable data channel


# Operating systems

How [operating systems](https://en.wikipedia.org/wiki/Operating_system) work is also a whole huge topic for itself.
You will scratch many parts of this because a game often has many low level parts in its code where you must know some basics about operating systems.
Esp, that is:

* File operations and [file systems](https://en.wikipedia.org/wiki/File_system)
* [Pipes](https://en.wikipedia.org/wiki/Pipeline_(computing))
* [Multithreading](https://en.wikipedia.org/wiki/Thread_(computing))
* [Memory](https://en.wikipedia.org/wiki/Computer_memory)


# Memory handling

In case you need to handle with huge amounts of memory, you need to know about memory optimisations and how a computer program usually handles the [memory allocations](https://en.wikipedia.org/wiki/Memory_management) on a low level.
See the [malloc() function](https://en.wikipedia.org/wiki/C_dynamic_memory_allocation),
or [jemalloc (popular efficient malloc implementation)](https://people.freebsd.org/~jasone/jemalloc/bsdcan2006/jemalloc.pdf).

OpenLieroX provides a build with a custom malloc implementation for debugging.
See [file memstats.cpp](https://github.com/albertz/openlierox/blob/0.59/src/common/memstats.cpp).


# Parallel computing

[Parallel computing](https://en.wikipedia.org/wiki/Parallel_computing) is where many computations are done simultaniosly in parallel.
Games often need to make a lot of very heavy and intense calculations.
The trend of computers is to have [multiple CPUs](https://en.wikipedia.org/wiki/Multiprocessing) (or [cores](https://en.wikipedia.org/wiki/Multi-core_processor)) instead of having a single one.
To use them all, it is mandatory to write your code in a way that several parts can be executed in parallel.
Despite the need for it, it also often leads to more clean code (if you do it right).

So, what you will learn is how to do parallel computing in general.
That is both theoretic knowledge and practical knowledge.
In the practice, parallel computing is often solved via [multiple threads, i.e. multithreading](https://en.wikipedia.org/wiki/Thread_(computing)).
The interesting parts are about how you synchronise your threads and how you communicate your data from one thread to another in a [safe way](https://en.wikipedia.org/wiki/Thread_safety).


# Version control

You will learn how to work with some kind of [version control](https://en.wikipedia.org/wiki/Version_control) system which manages all your source code files and often also other resources of your project.
It will keep track over all changes in all files and will make it possible that multiple people can work on the same code.
With the history of the changes, you will be able to see what person has done what changes and you can hunt down bugs to specific changes.
You can also see what person has written which parts of a source file and thus ask him about some details.

Such a system is even very helpfull and nice to have if you work alone on a project.
And it is absolutely mandatory once you work in a team.

In OpenLieroX, we use [Git](https://en.wikipedia.org/wiki/Git) - a very powerfull [distributed version control system](https://en.wikipedia.org/wiki/Distributed_version_control).
Learning Git is really a whole topic for itself.
You might want to use a platform like [GitHub](https://github.com/) to host your code and to make it available for others.


# Testing

You might want to setup some kind of [testing](https://en.wikipedia.org/wiki/Software_testing) for your code,
e.g. [unit tests](https://en.wikipedia.org/wiki/Unit_testing) or [integration tests](https://en.wikipedia.org/wiki/Integration_testing).


# Continuous integration

[Continuous integration](https://en.wikipedia.org/wiki/Continuous_integration) is a way to automate the testing and building of your code.
E.g. GitHub supports this with [GitHub Actions](https://docs.github.com/en/actions).


# Debugging

You will stumble upon bugs and problems in your code.
You will need to learn how to find and fix them.
This is called [debugging](https://en.wikipedia.org/wiki/Debugging).
Fortunately, there are many tools available to help you with debugging, such as [debuggers](https://en.wikipedia.org/wiki/Debugger).
See [here for a list](debugging.md).


# Profiling

Your code might be too slow (or hang) or use too much memory.
[Profiling](https://en.wikipedia.org/wiki/Profiling_(computer_programming)) is a way to find out where your code is slow or uses too much memory.
There are many tools available to help you with profiling, usually called profilers.
See [here for a list](profiling.md).


# Media design

A game usually needs graphics, sounds, levels or other media.
Those need to be created and designed.

There are also many existing assets available online
(see [this list](https://github.com/albertz/Coding-Game-Intro?tab=readme-ov-file#assets--artwork--graphics--sounds-for-your-game)).


# Story and game design

Depending on the type of game, you need a story.
[Game design](https://en.wikipedia.org/wiki/Game_design) is a whole topic for itself.


# Teamwork

A project of the size of OpenLieroX needs teamwork.
Various people doing various different tasks (coding, designing, distribution, support, testing) need to coordinate.
This is even more important for the coding which can be the biggest of those tasks.
Once there are multiple people working on the same code, they need to coordinate.
The source code version control management system is very central for this
(see [version control](#version-control))
(but this is useful even if you are working alone on a project).


# Project management

Once the project is getting bigger,
you need to manage the project,
e.g. keep track of the tasks, bugs, features, etc.
Platforms like GitHub provide some tools for this
such as an [issue tracker](https://docs.github.com/en/issues).
[Project management](https://en.wikipedia.org/wiki/Software_project_management) is again a whole topic for itself.


# Where to start

See [Coding Game Intro](https://github.com/albertz/Coding-Game-Intro).
You could start some own simple game project
([some ideas](https://github.com/albertz/Coding-Game-Intro?tab=readme-ov-file#some-simple-game-ideas)),
or take an existing open source game and modify it
([examples](https://github.com/albertz/Coding-Game-Intro?tab=readme-ov-file#existing-open-source-games-as-a-good-project-base)),
or contribute to an existing open source game project.

## Reading code of existing games

To be able to do something usefull with the code, it is very helpfull / mandatory that you have a rough overview over the code.
Many projects have an overview document.
Also see [here](coding.md#reading-code-of-existing-projects).

## Contributing to an existing project

Many projects have a document like `CONTRIBUTING.md` describing how to contribute.
It usually also makes sense to speak to someone from the project first.
Also see [here](coding.md#contributing-to-existing-projects).

## Setting up a development environment

For a beginner, this is often the most complicated part.
It is often not straightforward how you setup an [IDE](https://en.wikipedia.org/wiki/Integrated_development_environment) / editor / compiler to build the source code.
This is somewhat silly but you have to get through that.
(The compiler will convert the source code into an executable binary; on Windows, that is an EXE-file.)

The [IDE](https://en.wikipedia.org/wiki/Integrated_development_environment) is the editor where you edit the code.
In theory, you could also use a simple text editor; however, an IDE will be mure more helpfull and easy to use.

In some cases (like MSVC), the IDE is bundled together with the compiler.
In some other cases (on Linux),
they are highly seperated and independent from each other.
That means that setting up the compiling is in some cases (like MSVC or Xcode) the same as setting up the IDE, in some cases (like on Linux) independent.

However, compiling the source code is the most important thing you need to be able to do.
You cannot do anything if you are not able to do this.

Projects usually provide some documentation how to set up the development environment.

When you start a new project, it makes sense to see some simple examples how to set up the development environment.
Usually you would create a new version control repository, which is then an empty directory,
and you would put your stuff into it.
Also see [here](coding.md#coding-environment).

It might also make sense to setup some generic playground environment to test minimal ideas, code snippets, etc.
See [here](coding.md#playground).
