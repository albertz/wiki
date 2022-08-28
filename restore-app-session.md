OSX AppKit level:
[Core app design: User Interface Preservation](https://developer.apple.com/library/archive/documentation/General/Conceptual/MOSXAppProgrammingGuide/CoreAppDesign/CoreAppDesign.html#//apple_ref/doc/uid/TP40010543-CH3-SW10),
[`restoreWindow`](https://developer.apple.com/documentation/appkit/nswindowrestoration/1526251-restorewindow) and co

OSX Terminal:
[Restore specific Terminal history from .bash_sessions?](https://apple.stackexchange.com/questions/311548/restore-specific-terminal-history-from-bash-sessions),
`TERM_SESSION_ID` env var

Bash: `BASH_SESSION` env var?

Fish:
`fish_history` env var?
[fish_apple_terminal.fish](https://github.com/sparanoid/fish_apple_terminal).
[`trap ... EXIT`](https://fishshell.com/docs/current/cmds/trap.html).

Tmux:
[tmux-resurrect](https://github.com/tmux-plugins/tmux-resurrect/),
[tmux resurrect fish issue 217](https://github.com/tmux-plugins/tmux-resurrect/issues/217),
[Fish issue 4705](https://github.com/fish-shell/fish-shell/issues/4705),
[tmux-continuum](https://github.com/tmux-plugins/tmux-continuum)

[CRIU: Checkpoint/Restore In Userspace, for Linux](https://criu.org/).

[DMTCP: Distributed MultiThreaded CheckPointing](https://dmtcp.sourceforge.io/).
