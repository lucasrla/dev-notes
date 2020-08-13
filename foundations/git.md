# `git`

Xcode command line developer tools have already installed `git` for us:

```zsh
git --version    
  git version 2.21.0 (Apple Git-122)

which git
  /usr/bin/git
```

But we want the flexibility and control over own tools, so:

```
brew install git

git --version
  git version 2.24.3 (Apple Git-128)

which git
  /usr/bin/git
```

Time to configure git.

To avoid leaking out your email, remember to use `<USERNAME>@users.noreply.github.com` – as explained at: https://help.github.com/en/github/setting-up-and-managing-your-github-user-account/setting-your-commit-email-address.

On to `~/.gitconfig`:

```yml
[user]
	name = <NAME>
	email = <USERNAME>@users.noreply.github.com
[github]
    user = <USERNAME>
[core]
	excludesfile = /Users/<USER>/.gitignore
[alias]
    a      = add
    ca     = commit -a
    cam    = commit -am
    cm     = commit -m
    s      = status
    pom    = push origin master
    pog    = push origin gh-pages
    puom   = pull origin master
    puog   = pull origin gh-pages
    cob    = checkout -b
    co     = checkout
    fp     = fetch --prune --all
    l      = log --oneline --decorate --graph
    lall   = log --oneline --decorate --graph --all
    ls     = log --oneline --decorate --graph --stat
    lt     = log --graph --decorate --
```

And `~/.gitignore`:

```yml
# Folder view configuration files
.DS_Store
Desktop.ini

# Thumbnail cache files
._*
Thumbs.db

# Files that might appear on external disks
.Spotlight-V100
.Trashes

# Compiled Python files
*.pyc

# Compiled C++ files
*.out

# RStudio garbage
.Rhistory

# Application specific files
env
venv
node_modules
.sass-cache
```

If you're cloning GitHub repositories using `HTTPS`, you can use a `credential helper` to tell `git` to remember your GitHub username and password every time it talks to GitHub:

```zsh
# set git to use the osxkeychain credential helper
git config --global credential.helper osxkeychain
```

The next time you clone an `HTTPS` URL that requires a password, you'll be prompted for your username and password, and to grant access to the `OSX keychain`. After you've done this, the username and password are stored in your `keychain` and you won't be required to type them in to git again. Read this guide for more details: https://help.github.com/en/github/using-git/caching-your-github-password-in-git.

If you are using two-factor authentication, you must use a `personal access token` (not your password). Read this: https://github.blog/2013-09-03-two-factor-authentication/#how-does-it-work-for-command-line-git.
