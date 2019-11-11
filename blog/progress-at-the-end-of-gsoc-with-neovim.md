---
date: 2018-08-14T07:33:46+05:30
title: "Progress at the end of GSoC with Neovim"
description: "The work done during the three months of code with Neovim as part of GSoC 2018"
categories:
- gsoc
- project
tags:
- gsoc
- neovim
---

As we come to the end of three months of the coding extravaganza as a part of GSoC, I would like to share the progress we made so far and what is left to do as a part of [*Improving the UI protocol in Neovim*](https://summerofcode.withgoogle.com/projects/#5530001420582912) with [Björn Linse](https://github.com/bfredl) as my mentor.


## What is in place

- **Grid based updates**<br/>
[This post](/blog/window-grid-updates-in-neovim/) describes the grid-based updates in Neovim. The work for this is almost complete with tests and documentation in place.
The progress and code for grid based updates can be found [here](https://github.com/neovim/neovim/pull/8455).
- **Externalized wincmds**<br/>
This builds up on the *Grid based updates*. The work for this is still a little unstable but seems ready to be tested out by the external UIs.
The progress and code for external wincmds can be found [here](https://github.com/neovim/neovim/pull/8707).


## Where to go from here

- The above pull requests are not merged as of writing this post. My first priority would be to get them merged.
- There are a number of elements which are yet to be externalized with *cursorline* and *messages* being the next choices. I have started some work on externalizing the *cursorline* which I will continue.


_All posts about GSoC can be found under the [GSoC](/tags/gsoc) tag._
