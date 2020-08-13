---
title: General purpose utilities
parent: Command-line Tools
nav_order: 1
---

# General purpose utilities
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## tmux

```sh
# tmux - the terminal multiplexer
brew update && brew install tmux
```

In case you want to tweak `tmux`:

> `tmux`:  
> Example configuration has been installed to: `/usr/local/opt/tmux/share/tmux`  
> Bash completion has been installed to: `/usr/local/etc/bash_completion.d`


## tree

Tree is a recursive directory listing command that produces a depth indented listing of files, which is colorized ala dircolors if the `LS_COLORS` environment variable is set and output is to `tty`. `tree` is, in many ways, a nicer `ls`.

Install it with:

```sh
# tree - a recursive directory listing command that produces a depth indented listing of files
brew update && brew install tree
```

Here is an example of it in use:

```sh
tree ~ -L 1
  /Users/<USER>
  ├── Desktop
  ├── Documents
  ├── Downloads
  ├── Library
  ├── Movies
  ├── Music
  ├── Pictures
  └── Public

  8 directories, 0 files
```

For more information, read: http://mama.indstate.edu/users/ice/tree/. 


## rsync

```sh
# rsync - a utility for efficiently transferring and synchronizing files between computers
brew update && brew install rsync
```