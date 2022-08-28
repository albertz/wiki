# Overall

## OSX

OSX will save/restore application state across restarts, i.e. restore all windows with the same state as before.

I want that with a deep call hierarchy, even across systems, across Terminal.app, fish, mosh, ssh, tmux, etc.
More specifically, my common call stack:

  OSX -> Terminal.app -> fish -> mosh i6-direct -> ssh sulfid -> tmux a || tmux

* OSX Terminal.app restore is already handled by OSX.
* fish save/restore (inside OSX Terminal.app) can be done via fish event handlers
* mosh: mosh-client has host, server IP and UDP port in it; mosh-server, can see open UDP socket (/proc/pid/fd), check port (/proc/pid/net/udp)


# Technical

## Generic

[CRIU: Checkpoint/Restore In Userspace, for Linux](https://criu.org/).

[DMTCP: Distributed MultiThreaded CheckPointing](https://dmtcp.sourceforge.io/).

## OSX AppKit level

[Core app design: User Interface Preservation](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/CoreAppDesign/CoreAppDesign.html#//apple_ref/doc/uid/TP40010543-CH3-SW10),
[`restoreWindow`](https://developer.apple.com/documentation/appkit/nswindowrestoration/1526251-restorewindow) and co

## OSX Terminal.app

[Restore specific Terminal history from .bash_sessions?](https://apple.stackexchange.com/questions/311548/restore-specific-terminal-history-from-bash-sessions),
`TERM_SESSION_ID` env var

## Bash

`BASH_SESSION` env var?

## Fish

`fish_history` env var?

[fish_apple_terminal.fish](https://github.com/sparanoid/fish_apple_terminal).

[`trap ... EXIT`](https://fishshell.com/docs/current/cmds/trap.html)
-> only single trap per session, so do not use this, use event handlers instead, `fish_exit` event.

Could setup [`fish_preexec` and `fish_postexec` event handlers](https://fishshell.com/docs/current/cmds/function.html#cmd-function) to store current active command,
per session ID (`TERM_SESSION_ID`).

([Autoloading functions](https://fishshell.com/docs/current/language.html#autoloading-functions)
does not work for event handler functions.)

[Fish config](https://fishshell.com/docs/current/index.html#configuration) for startup script (startup event) + setting up other events.

## Tmux

[tmux-resurrect](https://github.com/tmux-plugins/tmux-resurrect/),
[tmux resurrect fish issue 217](https://github.com/tmux-plugins/tmux-resurrect/issues/217),
[Fish issue 4705](https://github.com/fish-shell/fish-shell/issues/4705),
[tmux-continuum](https://github.com/tmux-plugins/tmux-continuum)

## Mosh

Reattach existing session: [not really possible](https://github.com/mobile-shell/mosh/issues/394), except maybe generic solutions like CRIU
