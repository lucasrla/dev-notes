---
title: chruby
parent: Ruby
nav_order: 1
---

# chruby

[Steve Marshall](https://stevemarshall.com/journal/why-i-use-chruby/):

> `chruby` is essentially a very small shell script that sets a few environment variables (mostly `$PATH`) to point at a given install of Ruby. It also has a separate, optional, script to auto-switch ruby versions when changing directories.

```sh
which ruby
  /usr/bin/ruby

brew install chruby
  ==> Downloading https://homebrew.bintray.com/bottles/chruby-0.3.9.catalina.bottle.tar.gz
  ######################################################################## 100.0%
  ==> Pouring chruby-0.3.9.catalina.bottle.tar.gz
  ==> Caveats
  Add the following to the ~/.bash_profile or ~/.zshrc file:
    source /usr/local/opt/chruby/share/chruby/chruby.sh

  To enable auto-switching of Rubies specified by .ruby-version files,
  add the following to ~/.bash_profile or ~/.zshrc:
    source /usr/local/opt/chruby/share/chruby/auto.sh
  ==> Summary
  🍺  /usr/local/Cellar/chruby/0.3.9: 12 files, 50.8KB

which chruby
  chruby not found
```

Add the following lines to `~/.zshrc`:

```sh
source /usr/local/opt/chruby/share/chruby/chruby.sh
source /usr/local/opt/chruby/share/chruby/auto.sh
```

Then:

```sh
which chruby
  chruby () {
    case "$1" in
      (-h | --help) echo "usage: chruby [RUBY|VERSION|system] [RUBYOPT...]" ;;
      (-V | --version) echo "chruby: $CHRUBY_VERSION" ;;
      ("") local dir star
        for dir in "${RUBIES[@]}"
        do
          dir="${dir%%/}"
          if [[ "$dir" == "$RUBY_ROOT" ]]
          then
            star="*"
          else
            star=" "
          fi
          echo " $star ${dir##*/}"
        done ;;
      (system) chruby_reset ;;
      (*) local dir match
        for dir in "${RUBIES[@]}"
        do
          dir="${dir%%/}"
          case "${dir##*/}" in
            ("$1") match="$dir"  && break ;;
            (*"$1"*) match="$dir"  ;;
          esac
        done
        if [[ -z "$match" ]]
        then
          echo "chruby: unknown Ruby: $1" >&2
          return 1
        fi
        shift
        chruby_use "$match" "$*" ;;
    esac
  }

chruby --version
  chruby: 0.3.9
```

Great. Now it's time to install [ruby-install](ruby-install.html).