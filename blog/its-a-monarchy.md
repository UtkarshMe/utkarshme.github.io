---
title: "It's a monArchy!"
date: 2017-03-05T03:15:20+05:30
tags:
- linux
- distro
- arch
categories:
- explore
---

_Why is this [Arch Linux](https://www.archlinux.org/) such a big deal among
people? It can't be that tough! I'll just install it and see for myself._

So, here I am, installing a new Linux flavor just for the heck of it. But I
won't replace my current OS just yet. Let me install it in a virtual box. After
an easy download from their website, I have my hands on the iso image and I
fire up my virtual box. I mistype the app name in excitement of a new Linux.
Damn you, brain!

![screenshot-from-2017-03-05-023157](https://debugandstuff.files.wordpress.com/2017/03/screenshot-from-2017-03-05-023157.png)

It asks me to boot Arch Linux. _No option to install it? Weird._ I select the
first option and boot into Arch Linux. After 5 secs, I find myself at the
shell, logged in as the root. For those who don't know what that is, it's just
a geeky way of saying that I am logged in as the system admin. Maybe a little
complex than that. _What is happening?! Where's the GUI? Where's the installer?
What kind of an OS is this? I hate command line._ I Google for what to do and
am not disappointed. A
[wonderful article](https://www.ostechnix.com/install-arch-linux-latest-version/)
comes to my rescue. _Hey, that looks kinda easy! I can work with that._
Suddenly, all this does not seem daunting anymore. My love for command line
interface (cli) is restored. _Long live cli_! I start typing in commands one
after another and after changing my partition table about 5 times, (yes, I
played around and made an EFI partition, unlike what's given in the article)
the OS is installed. The best thing about it was that the latest software was
downloaded at the time of update and installed! (although it took ages to
download, _sigh_!) A downside maybe that it can't be installed while offline
but that isn't a problem for me.

After reboot, I'm shown a login shell. _But I never made a user? I only created
a password for the root. Ok, got it._ I log in as the root user and the first
thing I do is _ls_, followed by _pwd_ (just Linux commands for listing files
and printing the current working directory, respectively). So I have no files
and I'm in the root folder. Let me see the contents of the _'/'_ directory.
_Well, the filesystem sure is Linux like._ I think I like it like this. Nothing
but the shell. Also, I think I'll see how to get a display manager and a
desktop environment working on this one. If I'm successful,
[goodbye Elementary](https://debugandstuff.wordpress.com/2017/02/10/elementary-my-dear-watson/)!
I check the kernel version. 4.9.11\. That's just like 15 days old! _Damn, this
thing's updated!_ And yes, this is really so cool, I'm gonna show it off to
everyone. _Oh, I'm gonna flaunt it at every possible opportunity!_

-ut
