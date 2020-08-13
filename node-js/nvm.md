---
title: nvm
parent: Node.js
nav_order: 1
---

# nvm

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

# how to upgrade nvm (in the future, of course)
# (btw, see: https://github.com/nvm-sh/nvm/issues/2236 and https://github.com/nvm-sh/nvm/issues/1091)
nvm install node --reinstall-packages-from=node
```
