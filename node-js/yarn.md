---
title: yarn
parent: Node.js
nav_order: 2
---

# yarn

<del>To keep things simple, I will stick to `npm` and skip `yarn` for now. As of `2020`, [it seems `npm` has largely caught up](https://iamturns.com/yarn-vs-npm-2018/). That is not to say there aren't [people that](https://dev.to/shelob9/why-i-use-yarn-not-npm-dkk) still [strongly favor](https://spin.atomicobject.com/2020/03/15/why-yarn-2020/) `yarn`.</del> 

I turns out I gave up on using `npm` only. I got burned by the dependency hell in too many projects. ([An example](https://github.com/Chronoblog/gatsby-theme-chronoblog/issues/54)).

So here is how I installed `yarn`.

First, [since we are using `nvm`](nvm.html), we must ensure that our `PATH` lists `nvm`’s shims before the version of `Node.js` installed by Homebrew:

```sh
which node
  /Users/[USERNAME]/.nvm/versions/node/v14.4.0/bin/node

echo $PATH
# /Users/[USERNAME]/.nvm/versions/node/v14.4.0/bin should come before /usr/local/bin
```

Good. Now, install it with `brew`:

```sh
brew update && brew install yarn
  [...]

which yarn
  /usr/local/bin/yarn

yarn --version
  1.22.4
```
