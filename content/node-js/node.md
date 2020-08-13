# `Node.js`

This section was heavily inspired by [a great guide written by Tania Rascia](https://www.taniarascia.com/setting-up-a-brand-new-mac-for-development/).

## `nvm`

We will use `Node Version Manager` (`nvm`) to install `Node.js`. This allows us to easily switch between `Node` versions, which is essential. 

For more info about `nvm`, see: https://github.com/nvm-sh/nvm.

```zsh
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
```

Add the following two lines to `~/.zshrc`:

```zsh
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
```

Check if `nvm` has been installed successfully:

```zsh
command -v nvm
  nvm

nvm --version
  0.35.3
```

Now, install latest version of `node` (`npm` and `npx` come with it):

```zsh
which node
  node not found

nvm install node
  Downloading and installing node v14.4.0...
  Downloading https://nodejs.org/dist/v14.4.0/node-v14.4.0-darwin-x64.tar.xz...
  [...]
  Computing checksum with shasum -a 256
  Checksums matched!
  Now using node v14.4.0 (npm v6.14.5)
  Creating default alias: default -> node (-> v14.4.0)  

exec "$SHELL"

nvm use node
  Now using node v14.4.0 (npm v6.14.5)

which node
  /Users/<USER>/.nvm/versions/node/v14.4.0/bin/node

node -v
  v14.4.0

which npm
  /Users/<USER>/.nvm/versions/node/v14.4.0/bin/npm

npm -v
  6.14.5

which npx
  /Users/<USER>/.nvm/versions/node/v14.4.0/bin/npx

npx -v
  6.14.5

tree /Users/<USER>/.nvm/versions/node/v14.4.0/bin/
  /Users/<USER>/.nvm/versions/node/v14.4.0/bin/
  ├── node
  ├── npm -> ../lib/node_modules/npm/bin/npm-cli.js
  └── npx -> ../lib/node_modules/npm/bin/npx-cli.js
  
  0 directories, 3 files
```

If you need more information on `npx`, read up: https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b.

For you reference, here is a couple of useful `nvm` commands:

```zsh
# installing and using version `xx.xx`
nvm install xx.xx
nvm use xx.xx

# setting a new default version
nvm alias default xx.xx

# updating `nvm`
# (in the future, no need to run this now)
nvm install node --reinstall-packages-from=node
```

## yarn

<del>To keep things simple, I will stick to `npm` and skip `yarn` for now. As of `2020`, it seems `npm` has largely caught up. For instance: https://iamturns.com/yarn-vs-npm-2018/. That is not to say there aren't [people that](https://dev.to/shelob9/why-i-use-yarn-not-npm-dkk) still [strongly favor](https://spin.atomicobject.com/2020/03/15/why-yarn-2020/) `yarn`.</del> 

I gave up. I got burned by the dependency hell in too many projects while using `npm`. ([An example](https://github.com/Chronoblog/gatsby-theme-chronoblog/issues/54)).

So here is how to install `yarn`.

First, since we are using `nvm`, we must ensure that your `PATH` lists `nvm`’s shims before the version of `Node.js` installed by Homebrew.

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

