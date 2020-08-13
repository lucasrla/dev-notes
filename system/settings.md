---
title: Other Settings
parent: System Settings
nav_order: 3
---

# Other Settings
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Default Apps

### Safari

Customize your toolbar to something like this: ![](settings-safari-toolbar.png)

`Safari > Preferences... > General`
- Uncheck `Open "safe" files after downloading`
- `Safari opens with`: set `A new window`
- `New windows open with`: set `Empty Page`
- `New open open with`: set `Empty Page`

`Safari > Preferences... > Search`
- Set `DuckDuckGo` as your default search engine
- Uncheck all options from `Smart Search Field`

`Safari > Preferences... > Advanced`
- Enable `Show Develop menu in menu bar`


### TextEdit

- `Preferences...` > Uncheck `Wrap to page`

This will make it will wrap to window instead.


## macOS System Settings

### `General`
- `General > Appearance` to `Dark`
- `General > Show scroll bars` to `When scrolling`

### `Dock`
- Enable `Magnification` and adjust its intensity
- Set `Position` to `Right`
- Adjust `Size`

### `Mission Control`
- Add Hot Corners: `Bottom Left` is `Mission Control`, `Bottom Right` is `Desktop`
- Create Spaces 2 and 3

### More tweaks

Here are a few more tweaks, [cortesy of Tania Rascia](https://www.taniarascia.com/setting-up-a-brand-new-mac-for-development/):

```zsh
# Show Library folder
chflags nohidden ~/Library

# Show hidden files
defaults write com.apple.finder AppleShowAllFiles YES

# Show path bar
defaults write com.apple.finder ShowPathbar -bool true

# Show status bar
defaults write com.apple.finder ShowStatusBar -bool true
```

You may also want to tweak `Finder` and the `Desktop` a bit – e.g. hide all tags, etc.