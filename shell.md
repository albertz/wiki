# Shell

E.g. Bash, ZSH or Fish. (I mostly prefer these in reverse order.)

For scripting, I often prefer Python. It's more verbose, esp for running external commands, but much more clear for any logic.

## Environment

### History

In our research group (with shared NFS) ([i6, RWTH Aachen University](https://www-i6.informatik.rwth-aachen.de/)),
we log the history per directory (i.e. the histfile is `$PWD/.history.$USER`), and we also log the date/time.
This has been extremely helpful.
Not only checking your own history, but also being able to see others history.
E.g. imagine going through some directories of some former colleague who is gone now.
Otherwise it would often be impossible to really understand how sth was created, or ended up that way, etc.
I mean, properly documenting everything is of course nice, but even if that is done consistently, it will still miss some details.
And in practice, it never is done consistently.
([HN discussion](https://news.ycombinator.com/item?id=22912226).)

This uses [`local-history-add.py`](https://github.com/albertz/helpers/blob/master/local-history-add.py)
from my [helpers](https://github.com/albertz/helpers)
(also part as a submodule of my [system-tools](https://github.com/albertz/system-tools)).

For Bash, in `~/.bashrc`:

    export PROMPT_COMMAND="myLocalHistory"

    function myLocalHistory()
    {
      HISTORYLINE=`history | tail -1 | sed 's:^ *[0-9]* *::g'`
      ~/Programmierung/helpers/local-history-add.py "$HISTORYLINE" >/dev/null
    }

For ZSH, in `~/.zshrc`:

    preexec () {
        ~/dotfiles/system-tools/helpers/local-history-add.py $1 >/dev/null
    }

For Fish, in `~/.config/fish/config.fish`:

    function fish_preexec --on-event fish_preexec
        ~/dotfiles/system-tools/helpers/local-history-add.py $argv & disown
    end
