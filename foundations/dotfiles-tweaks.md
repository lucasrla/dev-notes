---
title: dotfiles
parent: Foundations
nav_order: 8
---

# dotfiles

## Tweaks to `.zshrc`

Edit `~/.zshrc` to have the following content:

```zsh
source "${ZDOTDIR:-$HOME}/.zprezto/init.zsh"

# aliases for using vs-code to edit config files
alias config-zshrc="code ~/.zshrc"
alias config-prezto="code ~/.zpreztorc"
alias config-ssh="code ~/.ssh/config"
```

Now you can type `config-zsh` or `config-ssh` or `config-prezto` and edit them on VS Code.