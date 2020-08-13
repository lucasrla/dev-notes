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

Why `prezto`? According to [reddit](https://www.reddit.com/r/zsh/comments/3be1fe/what_is_the_best_alternative_to_ohmyzsh_i_am/), it is faster and more comprehensive than `oh-my-zsh`.

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

Edit `~/.zpreztorc` to:

- Add `'git'` under `zstyle ':prezto:load' pmodule \`
- Uncomment the line `zstyle ':prezto:module:utility' safe-ops 'yes'`

For more information on `prezto`, see [https://github.com/sorin-ionescu/prezto](https://github.com/sorin-ionescu/prezto).