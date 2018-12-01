# Tmux Sideman

Tmux-sideman is a plugin for tmux which, when the user hits `Prefix + M`, will create a new pane and open a relevant manpage on it.

It's built using [tmux sidelib](https://www.github.com/alexsaalberg/tmux-sidelib), a shell script library which can be used to easily create plugins in the same ilk.

### Example

If you are editing something in vim, and then hit `Prefix + M`, a new pane will open with the vim manpage in it.

The tmux session will then look like this.

![Example use screenshot](screen.png)

## How to use

1. Hit the key binding (`Prefix + M`) to open up a manpage in a new pane next to the current one.

   This new pane, the *sidepane*, is noted as being attached to the original pane, the *mainpane*. If you activate the key binding in a  pane that is neither of these it will create a new *sidepane* for **that** *mainpane*.
   
   What man page is opened depends upon the state of the mainpane. For Example:

    - If you're in a program, it will open up `man PROGRAM_NAME`
    
    - If you're in bash, it will use the information on the shell line.
      
      - `$ ` (empty line) will result in `man bash` 
      
      - `$ ls` will result in `man ls`
      
      - `$ ls -l` will result in `man ls`, and `tmux-sideman` will subsequently search the manpage for the flag `-l`
    
2. When you hit the key binding (`Prefix + M`) again, one of two things could happen.

   - If you're in the same program, or the shell line is the same, the pane with man in it will be closed.
   
   - If you're in a different program, or the shell line has changed, it will update the sidepane. (Open a new manpage for the new program or shell line).
   
## How to install

### Installation with [Tmux Plugin Manager](https://github.com/tmux-plugins/tpm) (recommended)

Add plugin to the list of TPM plugins in `.tmux.conf`:

    set -g @plugin 'alexsaalberg/tmux-sideman'

Hit `prefix + I` to fetch the plugin and source it. You should now be able to
use the plugin.

### Manual Installation

Clone the repo:

    $ git clone https://github.com/alexsaalberg/tmux-sideman ~/clone/path

Add this line to the bottom of `.tmux.conf`:

    run-shell ~/clone/path/tmux_sidelib.tmux

Reload TMUX environment:

    # type this in terminal
    $ tmux source-file ~/.tmux.conf

You should now be able to use the plugin.

## Requirements

- `tmux 1.8` or higher

## Changes

**v1.0**

- Initial release.

- Built on [tmux-sidelib](https://www.github.com/alexsaalberg/tmux-sidelib) version v0.2

- Timeout functionality currently disabled.

## Other Stuff

- [tmux-sidelib](https://www.github.com/alexsaalberg/tmux-sidelib)

- [tmux plugin manager](https://github.com/tmux-plugins/tpm)

- [tmux-sidebar](https://www.github.com/tmux-plugins/tmux-sidebar) 
    - Inspiration for tmux-notepane, tmux-sidelib, etc.
    
- [tmux-notepane](https://www.github.com/tmux-plugins/tmux-notepane) 
  - Similar thing, but built using python and [libtmux](https://github.com/tmux-python/libtmux)

