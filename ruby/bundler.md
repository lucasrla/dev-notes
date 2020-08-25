---
title: Bundler
parent: Ruby
nav_order: 3
---

# Bundler
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

According to [Ruby 101](https://jekyllrb.com/docs/ruby-101/):

> A gem is code you can include in Ruby projects. It allows you to package up functionality and share it across other projects or with other people. Bundler installs the gems in a given project `Gemfile`. 

## Quick overview of our environments

### macOS Catalina defaults

Let's first have a look at Apple's defaults for `ruby`, `gem` and `bundle`:

```sh
which ruby
  /usr/bin/ruby

which gem
  /usr/bin/gem

which bundle
  /usr/bin/bundle

gem env
  RubyGems Environment:
    - RUBYGEMS VERSION: 3.0.3
    - RUBY VERSION: 2.6.3 (2019-04-16 patchlevel 62) [universal.x86_64-darwin19]
    - INSTALLATION DIRECTORY: /Library/Ruby/Gems/2.6.0
    - USER INSTALLATION DIRECTORY: /Users/<USER_NAME>/.gem/ruby/2.6.0
    - RUBY EXECUTABLE: /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/bin/ruby
    - GIT EXECUTABLE: /usr/local/bin/git
    - EXECUTABLE DIRECTORY: /usr/local/bin
    - SPEC CACHE DIRECTORY: /Users/<USER_NAME>/.gem/specs
    - SYSTEM CONFIGURATION DIRECTORY: /Library/Ruby/Site
    - RUBYGEMS PLATFORMS:
      - ruby
      - universal-darwin-19
    - GEM PATHS:
      - /Library/Ruby/Gems/2.6.0
      - /Users/<USER_NAME>/.gem/ruby/2.6.0
      - /System/Library/Frameworks/Ruby.framework/Versions/2.6/usr/lib/ruby/gems/2.6.0
    - GEM CONFIGURATION:
      - :update_sources => true
      - :verbose => true
      - :backtrace => false
      - :bulk_threshold => 1000
    - REMOTE SOURCES:
      - https://rubygems.org/
    - SHELL PATH:
      [...]
      - /usr/local/bin
      - /usr/local/sbin
      - /usr/bin
      - /bin
      - /usr/sbin
      - /sbin

gem list
  *** LOCAL GEMS ***

  bigdecimal (default: 1.4.1)
  bundler (default: 1.17.2)
  CFPropertyList (2.3.6)
  cmath (default: 1.0.0)
  csv (default: 3.0.9)
  date (default: 2.0.0)
  dbm (default: 1.0.0)
  did_you_mean (1.3.0)
  e2mmap (default: 0.1.0)
  etc (default: 1.0.1)
  fcntl (default: 1.0.0)
  fiddle (default: 1.0.0)
  fileutils (default: 1.1.0)
  forwardable (default: 1.2.0)
  io-console (default: 0.4.7)
  ipaddr (default: 1.2.2)
  irb (default: 1.0.0)
  json (default: 2.1.0)
  libxml-ruby (3.1.0)
  logger (default: 1.3.0)
  matrix (default: 0.1.0)
  mini_portile2 (2.4.0)
  minitest (5.11.3)
  mutex_m (default: 0.1.0)
  net-telnet (0.2.0)
  nokogiri (1.10.1)
  openssl (default: 2.1.2)
  ostruct (default: 0.1.0)
  power_assert (1.1.3)
  prime (default: 0.1.0)
  psych (default: 3.1.0)
  rake (12.3.2)
  rdoc (default: 6.1.0)
  rexml (default: 3.1.9)
  rss (default: 0.2.7)
  scanf (default: 1.0.0)
  sdbm (default: 1.0.0)
  shell (default: 0.7)
  sqlite3 (1.3.13)
  stringio (default: 0.0.2)
  strscan (default: 1.0.0)
  sync (default: 0.5.0)
  test-unit (3.2.9)
  thwait (default: 0.1.0)
  tracer (default: 0.1.0)
  webrick (default: 1.4.2)
  xmlrpc (0.3.0)
  zlib (default: 1.0.0)
```

### Environment based on ruby-install and chruby

Now, having installed `ruby` with `ruby-install` and activated it with `chruby` [in the previous steps](/ruby/), we should have:

```sh
chruby ruby-2.7.1

which ruby
  /Users/<USER_NAME>/.rubies/ruby-2.7.1/bin/ruby

which gem
  /Users/<USER_NAME>/.rubies/ruby-2.7.1/bin/gem

which bundle
  /Users/<USER_NAME>/.rubies/ruby-2.7.1/bin/bundle

gem env
  RubyGems Environment:
    - RUBYGEMS VERSION: 3.1.2
    - RUBY VERSION: 2.7.1 (2020-03-31 patchlevel 83) [x86_64-darwin19]
    - INSTALLATION DIRECTORY: /Users/<USER_NAME>/.gem/ruby/2.7.1
    - USER INSTALLATION DIRECTORY: /Users/<USER_NAME>/.gem/ruby/2.7.0
    - RUBY EXECUTABLE: /Users/<USER_NAME>/.rubies/ruby-2.7.1/bin/ruby
    - GIT EXECUTABLE: /usr/local/bin/git
    - EXECUTABLE DIRECTORY: /Users/<USER_NAME>/.gem/ruby/2.7.1/bin
    - SPEC CACHE DIRECTORY: /Users/<USER_NAME>/.gem/specs
    - SYSTEM CONFIGURATION DIRECTORY: /Users/<USER_NAME>/.rubies/ruby-2.7.1/etc
    - RUBYGEMS PLATFORMS:
      - ruby
      - x86_64-darwin-19
    - GEM PATHS:
      - /Users/<USER_NAME>/.gem/ruby/2.7.1
      - /Users/<USER_NAME>/.rubies/ruby-2.7.1/lib/ruby/gems/2.7.0
    - GEM CONFIGURATION:
      - :update_sources => true
      - :verbose => true
      - :backtrace => false
      - :bulk_threshold => 1000
    - REMOTE SOURCES:
      - https://rubygems.org/
    - SHELL PATH:
      - /Users/<USER_NAME>/.gem/ruby/2.7.1/bin
      - /Users/<USER_NAME>/.rubies/ruby-2.7.1/lib/ruby/gems/2.7.0/bin
      - /Users/<USER_NAME>/.rubies/ruby-2.7.1/bin
      [...]
      - /usr/local/bin
      - /usr/local/sbin
      - /usr/bin
      - /bin
      - /usr/sbin
      - /sbin

gem list
  *** LOCAL GEMS ***

  benchmark (default: 0.1.0)
  bigdecimal (default: 2.0.0)
  bundler (default: 2.1.4)
  cgi (default: 0.1.0)
  csv (default: 3.1.2)
  date (default: 3.0.0)
  dbm (default: 1.1.0)
  delegate (default: 0.1.0)
  did_you_mean (default: 1.4.0)
  etc (default: 1.1.0)
  fcntl (default: 1.0.0)
  fiddle (default: 1.0.0)
  fileutils (default: 1.4.1)
  forwardable (default: 1.3.1)
  gdbm (default: 2.1.0)
  getoptlong (default: 0.1.0)
  io-console (default: 0.5.6)
  ipaddr (default: 1.2.2)
  irb (default: 1.2.3)
  json (default: 2.3.0)
  logger (default: 1.4.2)
  matrix (default: 0.2.0)
  minitest (5.13.0)
  mutex_m (default: 0.1.0)
  net-pop (default: 0.1.0)
  net-smtp (default: 0.1.0)
  net-telnet (0.2.0)
  observer (default: 0.1.0)
  open3 (default: 0.1.0)
  openssl (default: 2.1.2)
  ostruct (default: 0.2.0)
  power_assert (1.1.7)
  prime (default: 0.1.1)
  pstore (default: 0.1.0)
  psych (default: 3.1.0)
  racc (default: 1.4.16)
  rake (13.0.1)
  rdoc (default: 6.2.1)
  readline (default: 0.0.2)
  readline-ext (default: 0.1.0)
  reline (default: 0.1.3)
  rexml (default: 3.2.3)
  rss (default: 0.2.8)
  sdbm (default: 1.0.0)
  singleton (default: 0.1.0)
  stringio (default: 0.1.0)
  strscan (default: 1.0.3)
  test-unit (3.3.4)
  timeout (default: 0.1.0)
  tracer (default: 0.1.0)
  uri (default: 0.10.0)
  webrick (default: 1.6.0)
  xmlrpc (0.3.0)
  yaml (default: 0.1.0)
  zlib (default: 1.1.0)
```

Note that `bundler` is already installed on both environments – and also that `bundle` and `bundler` work just fine:

```sh
bundler --version
  Bundler version 2.1.4

bundle --version
  Bundler version 2.1.4
```

## Configuring `bundler` to have isolated environments by project

Gems are (very unfortunately) installed globally by default. To avoid this and have isolated environments instead, we need to do a few more steps to configure `bundler`.

Our goal is to have executables installed in a `bin/` directory and gems in a `vendor/` directory – both directories inside our `A_PROJECT_DIRECTORY`. To achieve that with `bundle` we must add `--binstubs=bin` and `--path=vendor.noindex` every time we use `bundle install`.

From [Bundler's](https://bundler.io/man/bundle-install.1.html) [docs](https://bundler.io/man/bundle-binstubs.1.html):

> Binstubs are a shortcut-or alternative- to always using bundle exec. This gives you a file that can be run directly, and one that will always run the correct gem version used by the application.
>
> `--path` is the location to install the specified gems to. This defaults to Rubygems' setting. Bundler shares this location with Rubygems, `gem install ...` will have gem installed there, too. Therefore, gems installed without a `--path ...` setting will show up by calling `gem list`. Accordingly, gems installed to other locations will not get listed.
> 
> To apply any of --binstubs, --deployment, --path, or --without every time bundle install is run, use `bundle config`

Because we do not want to do this every single time we use `bundle install`, let's config Bundler to add them automatically:

```sh
bundle config list
  Settings are listed in order of priority. The top value will be used.

bundle config set bin bin/

bundle config set path vendor.noindex/

bundler config list
  Settings are listed in order of priority. The top value will be used.
  bin
  Set for the current user (/Users/<USER_NAME>/.bundle/config): "bin/"

  path
  Set for the current user (/Users/<USER_NAME>/.bundle/config): "vendor.noindex/"
```

But why are using `vendor.noindex` – and not just `vendor`? 

See [this comment on StackOverflow](https://stackoverflow.com/questions/486995/ruby-equivalent-of-virtualenv#comment101538390_13307346) and [this article about Spotlight](https://www.techjunkie.com/three-ways-to-prevent-spotlight-from-indexing-items-on-your-mac/).