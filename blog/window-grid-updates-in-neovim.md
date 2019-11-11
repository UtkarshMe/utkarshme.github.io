---
date: 2018-06-28T22:43:26+05:30
title: "Window Grid Updates in Neovim"
description: "About the (experimental) addition of per-window grid based updates in Neovim"
categories:
- GSoC
- project
tags:
- GSoC
- Neovim
---

_This post is in continuation with [this post](/blog/progress-after-two-weeks-into-gsoc-with-neovim)._

Neovim has come to be a very hackable, developer friendly version of Vim. It actually is what [their website](https://neovim.io/) claims to be: **literally the future of vim** and **Vim-fork focused on extensibility and usability**.
One of the goals of `nvim` is to allow UIs to set different grid-sizes for each window and receive grid-based events.

### Why do we need grid-based updates and different grid-sizes than what `nvim` sets?

- **To allow UIs to set different font sizes for each window in a view.**<br>
Currently, UIs must use the same font size for each and every window because of the inability to manage window size. When UIs get the option to set different grid sizes for each window, they can easily setup different font sizes for each window.
- **To allow UIs to add their own scrollbars for each window.**<br>
Currently, the UIs display the window splits as dictated by `nvim` in one screen update i.e. as a single grid. They don't have the ability to introduce decorations like scrollbars. Once the UIs can set grid sizes, they can easily add scrollbars to individual windows.
- **To allow UIs to add their own window decorations like shadows/outlines etc.**<br>
Currently, the UIs can add shadows/outlines but doing that requires parsing the screen updates, looking for window separator characters and then adding any decoration that they choose. Getting grid wise updates would simplify this task to a great degree.
- *And many more.*

After a month and a half of working with Neovim, we have an [experimental working prototype](https://github.com/neovim/neovim/pull/8455) that breaks up the screen grid in per-window grids, allows UIs to set different sizes for each window grid and receive grid based events.

Although we don't have it yet, but we expect to have it implemented in a GUI like [python-gui](https://github.com/neovim/python-gui) as an example by the end of the GSoC coding period i.e. mid August. We also would encourage GUI implementers of `nvim` to test out the experimental API and report the inevitable bugs that have crept in. This would be a step towards finalizing the said prototype and allow easy transition of GUIs to better control of UI in their projects.

**The work done so far can be found [here](https://github.com/neovim/neovim/pull/8455).**

_Follow the [gsoc](/tags/gsoc) tag for updates._
