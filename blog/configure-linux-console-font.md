---
date: 2019-01-07T20:51:09+05:30
title: "Configure Linux Console Font"
description:
meta_img:
categories:
tags:
---

Linux provides a way to set fonts and keymaps on the virtual consoles
(`tty[1-7]`). I'll focus on fonts in this post. The available fonts can be found
in `/usr/share/kbd/consolefonts/` and can be set as follows:

If there is a file in `/usr/share/kbd/consolefonts/` named
`ter-powerline-v18n.psf.gz`, you can set it as the terminal font for the current
console by running the following command:

```bash
setfont ter-powerline-v18n
```

_Note that this won't work in a terminal emulator. You might get an error like:
`Couldn't get a file descriptor referring to the console`._

But the above command sets the font in the current console only and that too
without persistence. To set the font at boot for all consoles, edit (or create)
the file `/etc/vconsole.conf` and add this line:

```bash
# in /etc/vconsole.conf
FONT=ter-powerline-v18n
```

Now you can either reboot the machine or load the changes without reboot using
the command:

```bash
localectl set-keymap MAP  # where MAP is the locale map (us, uk etc.)
```

### References:
[1] [Linux console in Arch Wiki](https://wiki.archlinux.org/index.php/Linux_console#Fonts).\\
[2] [Linux console/Keyboard configuration in Arch Wiki](https://wiki.archlinux.org/index.php/Linux_console/Keyboard_configuration#Persistent_configuration).
