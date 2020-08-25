---
title: ruby-install
parent: Ruby
nav_order: 2
---

# ruby-install

[After installing chruby](chruby.html), we will need `ruby-install` to install and use any `ruby` version:

```sh
brew install ruby-install
  ==> Downloading https://homebrew.bintray.com/bottles/ruby-install-0.7.1.catalina.bottle.tar.gz
  ######################################################################## 100.0%
  ==> Pouring ruby-install-0.7.1.catalina.bottle.tar.gz
  🍺  /usr/local/Cellar/ruby-install/0.7.1: 28 files, 71.1KB

which ruby-install
  /usr/local/bin/ruby-install

ruby-install --version
  ruby-install: 0.7.1

ruby-install
  >>> Downloading latest ruby versions ...
  >>> Downloading latest jruby versions ...
  >>> Downloading latest rbx versions ...
  >>> Downloading latest truffleruby versions ...
  >>> Downloading latest mruby versions ...
  Stable ruby versions:
    ruby:
      2.4.10
      2.5.8
      2.6.6
      2.7.1
    jruby:
      9.2.13.0
    rbx:
      5.0
    truffleruby:
      20.2.0
    mruby:
      2.1.2

which ruby
  /usr/bin/ruby

ruby --version
  ruby 2.6.3p62 (2019-04-16 revision 67580) [universal.x86_64-darwin19]
```

Let's install the latest `ruby` version (`2.7.1`). It will take a while to configure and compile from source. 

For our future reference, here's the most relevant output:

```sh
ruby-install ruby 2.7.1
  >>> Installing ruby 2.7.1 into /Users/<USER_NAME>/.rubies/ruby-2.7.1 ...
  >>> Installing dependencies for ruby 2.7.1 ...
  
  Updating Homebrew...
  Warning: openssl@1.1 1.1.1g is already installed and up-to-date
  To reinstall 1.1.1g, run `brew reinstall openssl@1.1`
  Warning: readline 8.0.4 is already installed and up-to-date
  To reinstall 8.0.4, run `brew reinstall readline`
  Warning: gdbm 1.18.1_1 is already installed and up-to-date
  To reinstall 1.18.1_1, run `brew reinstall gdbm`
  Warning: libffi 3.3 is already installed and up-to-date
  To reinstall 3.3, run `brew reinstall libffi`
  
  ==> Downloading https://homebrew.bintray.com/bottles/automake-1.16.2_1.catalina.bottle.tar.gz
  ==> Pouring automake-1.16.2_1.catalina.bottle.tar.gz
  🍺  /usr/local/Cellar/automake/1.16.2_1: 131 files, 3.4MB

  ==> Downloading https://homebrew.bintray.com/bottles/bison-3.7.1.catalina.bottle.tar.gz
  ==> Pouring bison-3.7.1.catalina.bottle.tar.gz
  ==> Caveats
  bison is keg-only, which means it was not symlinked into /usr/local,
  because macOS already provides this software and installing another version in
  parallel can cause all kinds of trouble.

  If you need to have bison first in your PATH run:
    echo 'export PATH="/usr/local/opt/bison/bin:$PATH"' >> ~/.zshrc

  For compilers to find bison you may need to set:
    export LDFLAGS="-L/usr/local/opt/bison/lib"
  🍺  /usr/local/Cellar/bison/3.7.1: 94 files, 3.2MB

  ==> Downloading https://homebrew.bintray.com/bottles/libyaml-0.2.5.catalina.bottle.tar.gz
  ==> Pouring libyaml-0.2.5.catalina.bottle.tar.gz
  🍺  /usr/local/Cellar/libyaml/0.2.5: 10 files, 323.5KB

  >>> Downloading https://cache.ruby-lang.org/pub/ruby/2.7/ruby-2.7.1.tar.bz2 into /Users/<USER_NAME>/src ...

  >>> Verifying ruby-2.7.1.tar.bz2 ...
  >>> Extracting ruby-2.7.1.tar.bz2 to /Users/<USER_NAME>/src/ruby-2.7.1 ...

  [...]

  Configuration summary for ruby version 2.7.1

   * Installation prefix: /Users/<USER_NAME>/.rubies/ruby-2.7.1
   * exec prefix:         ${prefix}
   * arch:                x86_64-darwin19
   * site arch:           ${arch}
   * RUBY_BASE_NAME:      ruby
   * ruby lib prefix:     ${libdir}/${RUBY_BASE_NAME}
   * site libraries path: ${rubylibprefix}/${sitearch}
   * vendor path:         ${rubylibprefix}/vendor_ruby
   * target OS:           darwin19
   * compiler:            clang
   * with pthread:        yes
   * with coroutine:      amd64
   * enable shared libs:  no
   * dynamic library ext: bundle
   * CFLAGS:              ${optflags} ${debugflags} ${warnflags}
   * LDFLAGS:             -L. -fstack-protector-strong -L/usr/local/lib \
                          -L/usr/local/opt/openssl@1.1/lib \
                          -L/usr/local/opt/readline/lib \
                          -L/usr/local/opt/libyaml/lib \
                          -L/usr/local/opt/gdbm/lib
   * DLDFLAGS:            -Wl,-undefined,dynamic_lookup \
                          -Wl,-multiply_defined,suppress \
                          -L/usr/local/opt/openssl@1.1/lib \
                          -L/usr/local/opt/readline/lib \
                          -L/usr/local/opt/libyaml/lib \
                          -L/usr/local/opt/gdbm/lib
   * optflags:            -O3
   * debugflags:          -ggdb3
   * warnflags:           -Wall -Wextra -Wdeprecated-declarations \
                          -Wdivision-by-zero \
                          -Wimplicit-function-declaration -Wimplicit-int \
                          -Wpointer-arith -Wshorten-64-to-32 \
                          -Wwrite-strings -Wmissing-noreturn \
                          -Wno-constant-logical-operand -Wno-long-long \
                          -Wno-missing-field-initializers \
                          -Wno-overlength-strings -Wno-parentheses-equality \
                          -Wno-self-assign -Wno-tautological-compare \
                          -Wno-unused-parameter -Wno-unused-value \
                          -Wunused-variable -Wextra-tokens
   * strip command:       strip -A -n
   * install doc:         rdoc
   * JIT support:         yes
   * man page type:       doc
   * BASERUBY -v:         ruby 2.6.3p62 (2019-04-16 revision 67580) \
                          [universal.x86_64-darwin19]

  >>> Compiling ruby 2.7.1 ...
    BASERUBY = /usr/bin/ruby --disable=gems
    CC = clang
    LD = ld
    LDSHARED = clang -dynamiclib
    CFLAGS = -O3 -ggdb3 -Wall -Wextra -Wdeprecated-declarations -Wdivision-by-zero -Wimplicit-function-declaration -Wimplicit-int -Wpointer-arith -Wshorten-64-to-32 -Wwrite-strings -Wmissing-noreturn -Wno-constant-logical-operand -Wno-long-long -Wno-missing-field-initializers -Wno-overlength-strings -Wno-parentheses-equality -Wno-self-assign -Wno-tautological-compare -Wno-unused-parameter -Wno-unused-value -Wunused-variable -Wextra-tokens -std=gnu99  -pipe
    XCFLAGS = -D_FORTIFY_SOURCE=2 -fstack-protector-strong -fno-strict-overflow -fvisibility=hidden -DRUBY_EXPORT -fPIE -DCANONICALIZATION_FOR_MATHN -I. -I.ext/include/x86_64-darwin19 -I./include -I. -I./enc/unicode/12.1.0
    CPPFLAGS = -I/usr/local/opt/openssl@1.1/include -I/usr/local/opt/readline/include -I/usr/local/opt/libyaml/include -I/usr/local/opt/gdbm/include -D_XOPEN_SOURCE -D_DARWIN_C_SOURCE -D_DARWIN_UNLIMITED_SELECT -D_REENTRANT
    DLDFLAGS = -Wl,-undefined,dynamic_lookup -Wl,-multiply_defined,suppress -L/usr/local/opt/openssl@1.1/lib -L/usr/local/opt/readline/lib -L/usr/local/opt/libyaml/lib -L/usr/local/opt/gdbm/lib -fstack-protector-strong -Wl,-pie -framework Security -framework Foundation
    SOLIBS = -lpthread -lgmp -ldl -lobjc
    LANG = en_US.UTF-8
    LC_ALL =
    LC_CTYPE = UTF-8
    MFLAGS =
  Apple clang version 11.0.3 (clang-1103.0.32.62)
  Target: x86_64-apple-darwin19.6.0
  Thread model: posix
  InstalledDir: /Library/Developer/CommandLineTools/usr/bin
  
  >>> Installing ruby 2.7.1 ...
    BASERUBY = /usr/bin/ruby --disable=gems
    CC = clang
    LD = ld
    LDSHARED = clang -dynamiclib
    CFLAGS = -O3 -ggdb3 -Wall -Wextra -Wdeprecated-declarations -Wdivision-by-zero -Wimplicit-function-declaration -Wimplicit-int -Wpointer-arith -Wshorten-64-to-32 -Wwrite-strings -Wmissing-noreturn -Wno-constant-logical-operand -Wno-long-long -Wno-missing-field-initializers -Wno-overlength-strings -Wno-parentheses-equality -Wno-self-assign -Wno-tautological-compare -Wno-unused-parameter -Wno-unused-value -Wunused-variable -Wextra-tokens -std=gnu99  -pipe
    XCFLAGS = -D_FORTIFY_SOURCE=2 -fstack-protector-strong -fno-strict-overflow -fvisibility=hidden -DRUBY_EXPORT -fPIE -DCANONICALIZATION_FOR_MATHN -I. -I.ext/include/x86_64-darwin19 -I./include -I. -I./enc/unicode/12.1.0
    CPPFLAGS = -I/usr/local/opt/openssl@1.1/include -I/usr/local/opt/readline/include -I/usr/local/opt/libyaml/include -I/usr/local/opt/gdbm/include -D_XOPEN_SOURCE -D_DARWIN_C_SOURCE -D_DARWIN_UNLIMITED_SELECT -D_REENTRANT
    DLDFLAGS = -Wl,-undefined,dynamic_lookup -Wl,-multiply_defined,suppress -L/usr/local/opt/openssl@1.1/lib -L/usr/local/opt/readline/lib -L/usr/local/opt/libyaml/lib -L/usr/local/opt/gdbm/lib -fstack-protector-strong -Wl,-pie -framework Security -framework Foundation
    SOLIBS = -lpthread -lgmp -ldl -lobjc
    LANG = en_US.UTF-8
    LC_ALL =
    LC_CTYPE = UTF-8
    MFLAGS =
  Apple clang version 11.0.3 (clang-1103.0.32.62)
  Target: x86_64-apple-darwin19.6.0
  Thread model: posix
  InstalledDir: /Library/Developer/CommandLineTools/usr/bin

  [...]
  installing default gems from lib:   /Users/<USER_NAME>/.rubies/ruby-2.7.1/lib/ruby/gems/2.7.0 (build_info, cache, doc, extensions, gems, specifications)
                                      benchmark 0.1.0
                                      bundler 2.1.4
                                      cgi 0.1.0
                                      csv 3.1.2
                                      delegate 0.1.0
                                      did_you_mean 1.4.0
                                      fileutils 1.4.1
                                      forwardable 1.3.1
                                      getoptlong 0.1.0
                                      ipaddr 1.2.2
                                      irb 1.2.3
                                      logger 1.4.2
                                      matrix 0.2.0
                                      mutex_m 0.1.0
                                      net-pop 0.1.0
                                      net-smtp 0.1.0
                                      observer 0.1.0
                                      open3 0.1.0
                                      ostruct 0.2.0
                                      prime 0.1.1
                                      pstore 0.1.0
                                      racc 1.4.16
                                      rdoc 6.2.1
                                      readline 0.0.2
                                      reline 0.1.3
                                      rexml 3.2.3
                                      rss 0.2.8
                                      singleton 0.1.0
                                      timeout 0.1.0
                                      tracer 0.1.0
                                      uri 0.10.0
                                      webrick 1.6.0
                                      yaml 0.1.0
  installing default gems from ext:   /Users/<USER_NAME>/.rubies/ruby-2.7.1/lib/ruby/gems/2.7.0 (build_info, cache, doc, extensions, gems, specifications)
                                      bigdecimal 2.0.0
                                      date 3.0.0
                                      dbm 1.1.0
                                      etc 1.1.0
                                      fcntl 1.0.0
                                      fiddle 1.0.0
                                      gdbm 2.1.0
                                      io-console 0.5.6
                                      json 2.3.0
                                      openssl 2.1.2
                                      psych 3.1.0
                                      readline-ext 0.1.0
                                      sdbm 1.0.0
                                      stringio 0.1.0
                                      strscan 1.0.3
                                      zlib 1.1.0
  installing bundled gems:            /Users/<USER_NAME>/.rubies/ruby-2.7.1/lib/ruby/gems/2.7.0 (build_info, cache, doc, extensions, gems, specifications)
                                      minitest 5.13.0
                                      power_assert 1.1.7
                                      net-telnet 0.2.0
                                      xmlrpc 0.3.0
                                      test-unit 3.3.4
                                      rake 13.0.1
  >>> Successfully installed ruby 2.7.1 into /Users/<USER_NAME>/.rubies/ruby-2.7.1  
```

Let's open a new terminal window and check it out:

```sh
which ruby
  /usr/bin/ruby

ruby --version
  ruby 2.6.3p62 (2019-04-16 revision 67580) [universal.x86_64-darwin19]

# the default ruby continues to be the one Apple installed by default
# let's change that with chruby

chruby
  ruby-2.7.1

chruby ruby-2.7.1

which ruby
  /Users/<USER_NAME>/.rubies/ruby-2.7.1/bin/ruby

ruby --version
  ruby 2.7.1p83 (2020-03-31 revision a0c7c23c9c) [x86_64-darwin19]

chruby
 * ruby-2.7.1
```

In case you need more help with `chruby`, check out: [https://github.com/postmodern/chruby](https://github.com/postmodern/chruby).
