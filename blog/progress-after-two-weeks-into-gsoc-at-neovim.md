---
date: 2018-05-31T01:07:50+05:30
title: "Progress After Two Weeks Into GSoC with Neovim"
description: "Two weeks have passed since the coding period began for Google Summer of Code. Here's the progress I made so far."
categories:
- GSoC
- project
tags:
- GSoC
- Neovim
---

_This post is in continuation with [this post](/blog/google-summer-of-code-with-neovim)._


Two weeks have passed since the coding period began for Google Summer of Code on 14th May. After setting up my system in a room with a loud music system, I _officially_ began coding.


## The progress so far
The first task that I needed to do was to break up the one global grid used for screen-handling into smaller per-window grids which would later let external UIs manage them individually.
[Björn](https://github.com/bfredl) had already laid the foundation for abstracting window grids. So I began my work by going through his work and cherry-picking the commits that were relevant for my task.

Building on top of that, with regular code-reviews by Björn, I modified the `screen_*` functions into `grid_*` functions which manipulated grids instead of the screen.
While this was being done, we had many discussions about keeping certain grid elements on the global grid like the window-separators (`vsep` and `statusline`), `cmdline`, `tabline` etc. These might be assigned separate grids later.


## Next steps
The next step will be to externalize the said grids for the external UIs to take advantage of. For this, we have planned to assign unique _handles_ to grids and let the UIs receive events in a per-grid basis, if they choose to.


## Experience working with Neovim
My experience working with Neovim (mainly, Björn) so far has been very pleasant. Bjorn is extremely hardworking and inspiring. Also, I learn something new every day just by reading the rich codebase and the code-reviews that I receive. Hope to keep on learning and keep on working!

**The work done so far can be found [here](https://github.com/neovim/neovim/pull/8455).**


_Follow the [gsoc](/tags/gsoc) tag for updates._
