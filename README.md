# zsh-syntax-highlighting

zsh-syntax-highlighting Build Status
Fish shell-like syntax highlighting for Zsh.

Requirements: zsh 4.3.11+.

This package provides syntax highlighting for the shell zsh. It enables highlighting of commands whilst they are typed at a zsh prompt into an interactive terminal. This helps in reviewing commands before running them, particularly in catching syntax errors.

Some examples:

Before: Screenshot #1.1
After:  Screenshot #1.2

Before: Screenshot #2.1
After:  Screenshot #2.2

Before: Screenshot #3.1
After:  Screenshot #3.2

Before: Screenshot #4.1
After:  Screenshot #4.2

How to install
See INSTALL.md.

FAQ
Why must zsh-syntax-highlighting.zsh be sourced at the end of the .zshrc file?
zsh-syntax-highlighting works by hooking into the Zsh Line Editor (ZLE) and computing syntax highlighting for the command-line buffer as it stands at the time z-sy-h's hook is invoked.

In zsh 5.2 and older, zsh-syntax-highlighting.zsh hooks into ZLE by wrapping ZLE widgets. It must be sourced after all custom widgets have been created (i.e., after all zle -N calls and after running compinit) in order to be able to wrap all of them. Widgets created after z-sy-h is sourced will work, but will not update the syntax highlighting.

In zsh newer than 5.8 (not including 5.8 itself), zsh-syntax-highlighting uses the add-zle-hook-widget facility to install a zle-line-pre-redraw hook. Hooks are run in order of registration, therefore, z-sy-h must be sourced (and register its hook) after anything else that adds hooks that modify the command-line buffer.

Does syntax highlighting work during incremental history search?
Highlighting the command line during an incremental history search (by default bound to to Ctrl+R in zsh's emacs keymap) requires zsh 5.4 or newer.

Under zsh versions older than 5.4, the zsh-default underlining of the matched portion of the buffer remains available, but zsh-syntax-highlighting's additional highlighting is unavailable. (Those versions of zsh do not provide enough information to allow computing the highlighting correctly.)

See issues #288 and #415 for details.

How are new releases announced?
There is currently no "push" announcements channel. However, the following alternatives exist:

GitHub's RSS feed of releases: https://github.com/zsh-users/zsh-syntax-highlighting/releases.atom
An anitya entry: https://release-monitoring.org/project/7552/
How to tweak
Syntax highlighting is done by pluggable highlighter scripts. See the documentation on highlighters for details and configuration settings.
