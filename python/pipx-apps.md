---
title: pipx apps
parent: Python
nav_order: 3
---

# Python apps installed via pipx
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Install and configure pipx

<div class="warning-box">Before installing the packages listed here, we must first install and configure pipx properly. For that, read <a href="https://lucasrla.github.io/python-on-macos/pipx.html">python-on-macos/pipx</a>.</div>


## pipx packages

Here is the list of Python apps that I have installed via `pipx`:

- [youtube-dl](https://github.com/ytdl-org/youtube-dl): Command-line program to download videos from YouTube.com and other video sites
- [visidata](https://www.visidata.org): VisiData is an interactive multitool for tabular data. It combines the clarity of a spreadsheet, the efficiency of the terminal, and the power of Python, into a lightweight utility which can handle millions of rows with ease
- [glances](https://nicolargo.github.io/glances/): Glances is a cross-platform system monitoring tool written in Python
- [datasette](https://github.com/simonw/datasette): An open source multi-tool for exploring and publishing data
- [pocket-to-sqlite](https://github.com/dogsheep/pocket-to-sqlite): Create a SQLite database containing data from your Pocket account
- [magic-wormhole](https://github.com/warner/magic-wormhole): Get things from one computer to another, safely (h/t [@patio11](https://twitter.com/patio11/status/1317656122937856003))

After your `pipx` setup is ready, it is trivial to install any Python application:

```sh
pipx install glances
  installed package glances 3.1.4.1, Python 3.8.2
  These apps are now globally available
      - glances
  done! ✨ 🌟 ✨

pipx install visidata
  installed package visidata 1.5.2, Python 3.8.2
  These apps are now globally available
    - vd
  done! ✨ 🌟 ✨

pipx install youtube-dl
  installed package youtube-dl 2020.5.29, Python 3.8.2
  These apps are now globally available
    - youtube-dl
  done! ✨ 🌟 ✨
```

You can also inject an optional dependency later on:

```sh
pipx inject visidata pandas
  injected package pandas into venv visidata
  done! ✨ 🌟 ✨
```

One could install any Python application with `pipx`. Another popular example that I haven't installed is [AWS CLI](https://github.com/aws/aws-cli) (`awscli`).


## Upgrade pipx packages

```sh
pipx upgrade youtube-dl
  upgraded package youtube-dl from 2020.5.29 to 2020.7.28 (location: /Users/<USER_NAME>/.local/pipx/venvs/youtube-dl)
```

## jupyterlab

Additionally, we will also install `jupyterlab` via `pipx`. Read [python-on-macos/jupyter](https://lucasrla.github.io/python-on-macos/jupyter/) for the details.


## poetry

Finally, let's also install `poetry` via `pipx`. Read [python-on-macos/poetry](https://lucasrla.github.io/python-on-macos/poetry.html) for all the details.