---
title: Media
parent: Command-line Tools
nav_order: 2
---

# Media
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## ffmpeg

[`ffmpeg`](http://ffmpeg.org) is the ultimate Swiss Army Knife of Video and Audio right on your command-line.

```sh
brew update && brew install ffmpeg
  [...]
  # beware the caveats!
  ==> Caveats
  ==> libffi
  libffi is keg-only, which means it was not symlinked into /usr/local,
  because macOS already provides this software and installing another version in
  parallel can cause all kinds of trouble.

  For compilers to find libffi you may need to set:
    export LDFLAGS="-L/usr/local/opt/libffi/lib"
    export CPPFLAGS="-I/usr/local/opt/libffi/include"

  For pkg-config to find libffi you may need to set:
    export PKG_CONFIG_PATH="/usr/local/opt/libffi/lib/pkgconfig"

  ==> unbound
  To have launchd start unbound now and restart at startup:
    sudo brew services start unbound
  ==> sqlite
  sqlite is keg-only, which means it was not symlinked into /usr/local,
  because macOS already provides this software and installing another version in
  parallel can cause all kinds of trouble.

  If you need to have sqlite first in your PATH run:
    echo 'export PATH="/usr/local/opt/sqlite/bin:$PATH"' >> ~/.zshrc

  For compilers to find sqlite you may need to set:
    export LDFLAGS="-L/usr/local/opt/sqlite/lib"
    export CPPFLAGS="-I/usr/local/opt/sqlite/include"

  For pkg-config to find sqlite you may need to set:
    export PKG_CONFIG_PATH="/usr/local/opt/sqlite/lib/pkgconfig"

  ==> python@3.8
  Python has been installed as
    /usr/local/bin/python3

  Unversioned symlinks `python`, `python-config`, `pip` etc. pointing to
  `python3`, `python3-config`, `pip3` etc., respectively, have been installed into
    /usr/local/opt/python@3.8/libexec/bin

  You can install Python packages with
    pip3 install <package>
  They will install into the site-package directory
    /usr/local/lib/python3.8/site-packages

  See: https://docs.brew.sh/Homebrew-and-Python
  ==> glib
  Bash completion has been installed to:
    /usr/local/etc/bash_completion.d
  ==> icu4c
  icu4c is keg-only, which means it was not symlinked into /usr/local,
  because macOS provides libicucore.dylib (but nothing else).

  If you need to have icu4c first in your PATH run:
    echo 'export PATH="/usr/local/opt/icu4c/bin:$PATH"' >> ~/.zshrc
    echo 'export PATH="/usr/local/opt/icu4c/sbin:$PATH"' >> ~/.zshrc

  For compilers to find icu4c you may need to set:
    export LDFLAGS="-L/usr/local/opt/icu4c/lib"
    export CPPFLAGS="-I/usr/local/opt/icu4c/include"

  For pkg-config to find icu4c you may need to set:
    export PKG_CONFIG_PATH="/usr/local/opt/icu4c/lib/pkgconfig"

  ==> tesseract
  This formula contains only the "eng", "osd", and "snum" language data files.
  If you need any other supported languages, run `brew install tesseract-lang`.
```