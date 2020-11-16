---
title: shell
parent: Foundations
nav_order: 4
---

# shell
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## zsh

`zsh` is the default shell on macOS Catalina (i.e. it is already installed out-of-the-box). But since our setup is `brew`-centric, let's install a new `zsh`:

```sh
which zsh
  /bin/zsh

zsh --version
  zsh 5.7.1 (x86_64-apple-darwin19.0)

brew update && brew install zsh
```

Open a new tab on iTerm2 to make sure you have access to the `zsh` you have just installed:

```sh
which zsh
  /usr/local/bin/zsh

zsh --version
  zsh 5.8 (x86_64-apple-darwin19.3.0)
```

## prezto

Why `prezto`? [According to this reddit thread](https://www.reddit.com/r/zsh/comments/3be1fe/what_is_the_best_alternative_to_ohmyzsh_i_am/), it is faster and more comprehensive than `oh-my-zsh`.

Install it with:

```sh
git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto"

chsh -s /usr/local/bin/zsh
  Changing shell for <USER>.
  Password for <USER>:
  chsh: /usr/local/bin/zsh: non-standard shell

ls ~/.zshrc
  ls: /Users/<USER>/.zshrc: No such file or directory
```

Create `~/.zshrc` and add the following line to it:

```sh
source "${ZDOTDIR:-$HOME}/.zprezto/init.zsh"
```

Edit `~/.zpreztorc` to have:

```sh
# Set the Prezto modules to load (browse modules).
# The order matters.
zstyle ':prezto:load' pmodule \
  'environment' \
  'terminal' \
  'editor' \
  'history' \
  'directory' \
  'spectrum' \
  'utility' \
  'completion' \
  'history-substring-search' \
  'prompt' \
  'git'

# Check out https://github.com/sorin-ionescu/prezto/tree/master/modules 
# for more details on each module
```

Also, uncomment the line `zstyle ':prezto:module:utility' safe-ops 'yes'` to have `cp`,`ln`, `mv` and `rm` [aliased to their interactive variants](https://github.com/sorin-ionescu/prezto/tree/master/modules/utility#safe-ops):

```sh
#
# Utility
#

# Enabled safe options. This aliases cp, ln, mv and rm so that they prompt
# before deleting or overwriting files. Set to 'no' to disable this safer
# behavior.
zstyle ':prezto:module:utility' safe-ops 'yes'
```

For more information on `prezto`, [visit its GitHub repository](https://github.com/sorin-ionescu/prezto).