---
title: "Wolfram Language for Jupyter"
parent: "Wolfram Language"
nav_order: 2
---

# Wolfram Language for Jupyter

## Installation

First, make sure you have installed both the Wolfram Engine and `wolframscript`. [Check out the instructions here](engine.html).

Next, download the latest `.paclet` file [available](https://github.com/WolframResearch/WolframLanguageForJupyter/releases) in their repository [WolframLanguageForJupyter](https://github.com/WolframResearch/WolframLanguageForJupyter).

Then, run:

```sh
# list your current jupyter kernels
jupyter kernelspec list
  Available kernels:
    ...
    python3    /Users/<USER_NAME>/.local/pipx/venvs/jupyterlab/share/jupyter/kernels/python3
    ...

# run the wolfram engine from the command line and install the paclet
wolframscript
```

```wl
Wolfram Engine activated. See https://www.wolfram.com/wolframscript/ for more information.
Wolfram Language 12.1.1 Engine for Mac OS X x86 (64-bit)
Copyright 1988-2020 Wolfram Research, Inc.

In[1]:= PacletInstall["~/Downloads/WolframLanguageForJupyter-0.9.2.paclet"]

Out[1]= PacletObject[WolframLanguageForJupyter, 0.9.2, <>]

In[2]:= Needs["WolframLanguageForJupyter`"]
# ATTENTION: do not forget the `

In[3]:= ConfigureJupyter["Add"]
Loading from Wolfram Research server ...

In[4]:= Quit
```

```sh
# check if the kernel has been installed
jupyter kernelspec list
  Available kernels:
    ...
    wolframlanguage12.1    /Users/lucas/Library/Jupyter/kernels/wolframlanguage12.1
    python3                /Users/lucas/.local/pipx/venvs/jupyterlab/share/jupyter/kernels/python3
    ...
```

Success! Now, simply run `jupyter lab` or `jupyter notebook` and a `Wolfram Language 12.1` kernel will appear as an option for you to use.

For more information on how to setup Jupyter, read my [Python setup guide](https://lucasrla.github.io/python-on-macos/).