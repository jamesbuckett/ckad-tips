# tmux in the CKAD shell

> [!NOTE]
> This section is for **reference only**. On the new exam platform you can open multiple shells, making `tmux` redundant.

You are able to use [tmux](https://github.com/tmux/tmux/wiki) in the CKAD shell.

`HOK` = Hands Off Keyboard

<br />

## tmux side-by-side window

```text
tmux                                # Start Terminal Multiplexer

CTRL+b    HOK   %                   # side-by-side window
CTRL+b    HOK   <right arrow>       # move to right pane
CTRL+b    HOK   <left arrow>        # move to left pane
```

<br />

## tmux over-and-under window (preference for exam)

```text
tmux                                # Start Terminal Multiplexer

CTRL+b    HOK   "                   # over-and-under window
CTRL+b    HOK   <up arrow>          # pane above
CTRL+b    HOK   <down arrow>        # pane below
```

_End of Section_
