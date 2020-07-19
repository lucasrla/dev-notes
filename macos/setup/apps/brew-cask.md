# `brew cask`

```zsh
brew cask install \
  appcleaner \
  the-unarchiver \
  iterm2 \
  visual-studio-code \
  vlc \
  spotify \
  standard-notes \
  notion \
  rectangle \  
  obsidian \  
  glance
```

Most apps in the list above need no intro. Here are brief descriptions of the ones that are less famous:

- [Rectangle](https://rectangleapp.com/) is a nice window manager that is [free and open source](https://github.com/rxhanson/Rectangle).

- [Obsidian](https://obsidian.md) is a great app for note-taking and knowledge management. Check it out.

- [Glance](https://github.com/samuelmeuli/glance) is a wonderful Quick Look plugin. Free and open source.


# Application Settings

## iTerm2

- Change `Preferences > Appearance > General > Theme` to `Dark`
- Change `Preferences > Profiles > Colors > Color Presets` to `Tango Dark`

## Visual Studio Code

- Disable telemetry: https://code.visualstudio.com/docs/supporting/faq#_how-to-disable-telemetry-reporting
- Open the Command Palette (`CMD + SHIFT + P`), type `command line` and select `Shell Command: Install code command in PATH`
- Switch to the `Monokai Dimmed` theme. Do it from `Code > Preferences > Color Theme` (or simply by typing `CMD + K + T`)
- Install support to `python`, `docker`, `javascript` from the welcome screen
- Install `html`, `css` and `yaml` support as well
- Install `Highlight Matching Tag` (see: https://marketplace.visualstudio.com/items?itemName=vincaslt.highlight-matching-tag)

For more information, see https://pycon.switowski.com/01-vscode/setup/.

## Notion

- `Settings > Enable Dark Mode`