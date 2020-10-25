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

## List of Extensions

Quick keyboard access via `CMD` + `SHIFT` + `X`. Here is a list the ones I have installed:

### General

- [Python `ms-python.python`](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
- [Liquid](https://marketplace.visualstudio.com/items?itemName=sissel.shopify-liquid) – which [will soon](https://github.com/panoply/vscode-liquid/issues/56) become [Liquify](https://liquify.dev/)

### Formatting and linting

- [Prettier `esbenp.prettier-vscode`](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode) – official project website is [here](https://prettier.io)
- [ESLint `dbaeumer.vscode-eslint`](https://marketplace.visualstudio.com/items?itemName=dbaeumer) – official project website is [here](https://eslint.org)

> Note: Prettier can be too naïve and mess up Markdown and HTML with [Jekyll's Liquid tags](https://github.com/panoply/vscode-liquid/issues/34). The solution is to disable it in `markdown` and `html` files.

### Config file formats

- [YAML `redhat.vscode-yaml`](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml)
- [DotENV `mikestead.dotenv`](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv)
- [systemd `coolbear.systemd-unit-file`](https://marketplace.visualstudio.com/items?itemName=coolbear.systemd-unit-file)

### MDX

- [MDX `silvenon.mdx`](https://marketplace.visualstudio.com/items?itemName=silvenon.mdx)
- [MDX Preview `xyc.vscode-mdx-preview`](https://marketplace.visualstudio.com/items?itemName=xyc.vscode-mdx-preview)

### Git

- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)

### HTML

- [Highlight Matching Tag `vincaslt.highlight-matching-tag`](https://marketplace.visualstudio.com/items?itemName=vincaslt.highlight-matching-tag)

### Markdown and Note-taking

- [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one)
- [Markdown Notes](https://marketplace.visualstudio.com/items?itemName=kortina.vscode-markdown-notes)
- [Markdown Links](https://marketplace.visualstudio.com/items?itemName=tchayen.markdown-links)

> Credit: [FOAM's Recommended Extensions](https://foambubble.github.io/foam/recommended-extensions).

## Global `settings.json`

Here are the contents of my `$HOME/Library/Application\ Support/Code/User/settings.json`:

```json
{
  "telemetry.enableTelemetry": false,
  "workbench.colorTheme": "Monokai Dimmed",
  "python.pythonPath": "$HOME/.pyenv/shims/python",
  "python.formatting.provider": "black",
  "editor.formatOnSave": true,
  "python.showStartPage": false,
  "editor.tabSize": 2,
  "prettier.disableLanguages": [
    "markdown",
    "html"
  ],
  "prettier.htmlWhitespaceSensitivity": "strict",
  "editor.wordWrap": "bounded",
  "liquid.format": true
}
```

By the way, there are three locations/scopes for `settings.json`: User Preferences (Global, the one above), in Folder, and in Workspace. [Read this article for more details](https://supunkavinda.blog/vscode-editing-settings-json).

---

For more information on setting up VS Code, check out [this guide](https://pycon.switowski.com/01-vscode/setup/) by Sebastian Witowski.

Here is [another guide by Andrey K.](https://dev.to/cat__logic/working-faster-in-vscode-255a)
