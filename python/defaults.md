---
title: Apple defaults
parent: Python
nav_order: 1
---

# Python defaults on macOS Catalina
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## The default versions of Python

For the record, here are the default Python interpreters after a successful install of [Xcode command line developer tools](/foundations/xcode-select.html):

```sh
which python
  /usr/bin/python

python --version
  Python 2.7.16

ls -l /usr/bin/python
  lrwxr-xr-x  1 root  wheel  75 May 29 10:18 /usr/bin/python -> ../../System/Library/Frameworks/Python.framework/Versions/2.7/bin/python2.7

which python3
  /usr/bin/python3

python3 --version
  Python 3.7.3
```

## LibreSSL, not OpenSSL

Note that both `python` by Apple use `LibreSSL` (and [not `openssl` that we have installed from Homebrew](/foundations/openssl.html)):

```sh
python -c 'import ssl; print(ssl.OPENSSL_VERSION)'
  LibreSSL 2.8.3

python3 -c 'import ssl; print(ssl.OPENSSL_VERSION)'
  LibreSSL 2.8.3
```
