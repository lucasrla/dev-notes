---
title: VS Code settings
parent: Apps
nav_order: 4
---

# Visual Studio Code settings
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Basics

- Disable the telemetry. [Here is how](https://code.visualstudio.com/docs/supporting/faq#_how-to-disable-telemetry-reporting).

- Install the `code` command. Open the Command Palette (`CMD + SHIFT + P`), type `command line` and select `Shell Command: Install code command in PATH`

## Theme

Switch to the `Monokai Dimmed` theme.

Do it from `Code > Preferences > Color Theme` (or simply by typing `CMD + K + T`).

## Settings

On the Mac, access settings by pressing `CMD` + `,`:

- Tab Size: I prefer `2 spaces` for most file types
- Word Wrap: `bounded`

Tip: type `@modified` in the Search bar to see all settings that were modified.

## Extensions

Quick keyboard access via `CMD` + `SHIFT` + `X`. Here is a list the ones I have installed:

- [Python `ms-python.python`](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [Prettier `esbenp.prettier-vscode`](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) – official project website is [here](https://prettier.io)
- [ESLint `dbaeumer.vscode-eslint`](https://marketplace.visualstudio.com/items?itemName=dbaeumer) – official project website is [here](https://eslint.org)
<!-- - [HTML CSS Support `ecmel.vscode-html-css`](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css) -->
- [Highlight Matching Tag `vincaslt.highlight-matching-tag`](https://marketplace.visualstudio.com/items?itemName=vincaslt.highlight-matching-tag)
- [MDX `silvenon.mdx`](https://marketplace.visualstudio.com/items?itemName=silvenon.mdx)
- [YAML `redhat.vscode-yaml`](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml)
- [DotENV `mikestead.dotenv`](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv)
- [MDX Preview `xyc.vscode-mdx-preview`](https://marketplace.visualstudio.com/items?itemName=xyc.vscode-mdx-preview)
- [systemd `coolbear.systemd-unit-file`](https://marketplace.visualstudio.com/items?itemName=coolbear.systemd-unit-file)

## Global `settings.json`

Here are the contents of my `$HOME/Library/Application Support/Code/User/settings.json`:

```json
{
  "telemetry.enableTelemetry": false,
  "workbench.colorTheme": "Monokai Dimmed",
  "python.pythonPath": "/Users/<USER_NAME>/.pyenv/shims/python",
  "python.formatting.provider": "black",
  "editor.formatOnSave": true,
  "python.showStartPage": false,
  "editor.wordWrap": "bounded",
  "editor.tabSize": 2,
  "prettier.disableLanguages": ["markdown"]
}
```

By the way, there are three locations/scopes for `settings.json`: User Preferences (Global, the one above), in Folder, and in Workspace. [Read this article for more details](https://supunkavinda.blog/vscode-editing-settings-json).

To access 

---

For more information on setting up VS Code, check out [this guide](https://pycon.switowski.com/01-vscode/setup/) by Sebastian Witowski.

Here is [another guide by Andrey K.](https://dev.to/cat__logic/working-faster-in-vscode-255a)
