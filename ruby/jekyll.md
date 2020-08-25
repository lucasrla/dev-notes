---
title: Jekyll
parent: Ruby
nav_order: 4
---

# Jekyll
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

[Jekyll](https://jekyllrb.com) is a static site generator written in Ruby. In fact, this very website is powered by Jekyll (via GitHub Pages).

## Taking advantage of `.ruby-version`

[Because we added `source /usr/local/opt/chruby/share/chruby/auto.sh` to our `~/.zshrc` after installing `chruby`](chruby.html), whenever we want to use an specific Ruby version in a given project we can do the following:

```sh
mkdir my-jekyll-website
cd my-jekyll-website

which ruby
  /usr/bin/ruby

echo "ruby-2.7.1" > .ruby-version
# "ruby-2.7.1." or any other version that you have installed with ruby-install

which ruby
  /Users/<USER_NAME>/.rubies/ruby-2.7.1/bin/ruby
```

## Installing Jekyll through an existing `Gemfile`

Copy the following lines to a `Gemfile` inside the `my-jekyll-website` directory:

```sh
source "https://rubygems.org"
gem "github-pages", group: :jekyll_plugins
group :jekyll_plugins do
  gem "jekyll-feed"
  gem "jekyll-seo-tag"
end
```

Then:

```sh
cd my-jekyll-website

cat .ruby-version
  ruby-2.7.1

chruby
 * ruby-2.7.1

cat Gemfile
  source "https://rubygems.org"
  gem "github-pages", group: :jekyll_plugins
  group :jekyll_plugins do
    gem "jekyll-feed"
    gem "jekyll-seo-tag"
  end

# please make sure you have already configured bundler properly
# see: https://lucasrla.github.io/macos-setup/ruby/bundler.html#configuring-bundler-to-have-isolated-environments-by-project
bundle install
  [...]

bundle info jekyll
  * jekyll (3.9.0)
	Summary: A simple, blog aware, static site generator.
	Homepage: https://github.com/jekyll/jekyll
	Path: [REDACTED]/macos-setup/vendor.noindex/ruby/2.7.0/gems/jekyll-3.9.0

bundle exec jekyll serve

# browse to http://localhost:4000
```

## More on the `github-pages` gem

You may have noticed that we did not use `gem "jekyll"` in our `Gemfile`, instead we went with `gem "github-pages", group: :jekyll_plugins`. 

Here is why – according to [Jekyll's documentation](https://jekyllrb.com/docs/github-pages/):

> GitHub provides the `github-pages` gem which is used to manage Jekyll and its dependencies on GitHub Pages. Using it in your projects means that when you deploy your site to GitHub Pages, you will not be caught by unexpected differences between various versions of the gems.

GitHub Pages uses the following dependencies and versions: [https://pages.github.com/versions/](https://pages.github.com/versions/). You can check out there the list of whitelisted plugins (hint – they have the following pattern: `jekyll-___`)

Here is its official repository: [https://github.com/github/pages-gem](https://github.com/github/pages-gem).

If you are using GitHub Pages (like I am here on this website), then follow [their advice](https://docs.github.com/en/github/working-with-github-pages/testing-your-github-pages-site-locally-with-jekyll#updating-the-github-pages-gem):

> Jekyll is an active open source project that is updated frequently. If the `github-pages` gem on your computer is out of date with the `github-pages` gem on the GitHub Pages server, your site may look different when built locally than when published on GitHub. To avoid this, regularly update the `github-pages` gem on your computer:
>
>  ```sh
>  cd YOUR_PROJECT_DIR
>  bundle update github-pages
>  ```
