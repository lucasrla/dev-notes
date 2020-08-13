---
title: gcc
parent: Foundations
nav_order: 7
---

# gcc

The GNU Compiler Collection includes front ends for C, C++, Objective-C, Fortran, Ada, Go, and D, as well as libraries for these languages (libstdc++, ...). [Have a look at the `brew` formula here](https://formulae.brew.sh/formula/gcc).

Needless to say, several languages libraries depend on `gcc`.

```zsh
brew update && brew install gcc
```

Note: as of `2020-05-29`, the installed version was `9.3.0_1`, [the exact `brew` formula is here](https://github.com/Homebrew/homebrew-core/blob/566560476be4973d396c54e920411b07081b6722/Formula/gcc.rb).