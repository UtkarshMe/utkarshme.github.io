---
title: "First pull request"
date: 2017-03-04T08:08:26+05:30
tags:
- elementary os
- patch
categories:
- open source
---

Since I had switched to Elementary OS and I had to tweak it, I foraged the
internet for a tweak tool and found it by the name of [Elementary
Tweaks](https://github.com/elementary-tweaks/elementary-tweaks). Although it
looked promising, it soon turned out that it didn't really offer that many
customizations. But you can't really blame the devs for this, as the EOS is
built with
[a principle](https://elementary.io/docs/human-interface-guidelines#avoid-configuration)
in mind to avoid configurations as much as possible. It does provide speed but
on the opportunity cost of configuring the applications to the user's
preference.

![screenshot-from-2017-03-04-201334](https://debugandstuff.files.wordpress.com/2017/03/screenshot-from-2017-03-04-201334.png)

Going back to the point that this post is about, I was exploring the source
code and realized that it essentially was just modifying the settings in the
applications database. As this tool interested me greatly, I decided to why not
add a few more settings for the user and quickly forked the repo to my own
[Github account](https://github.com/coditva). I made a few edits here and
there to add about 4 featured and decided to push these for the developer.

Creating a pull request for the first time was an experience of mixed emotions.
_Should I really create this request? Will my code be good enough for them?
Will this even be worth their time?_ And after an FAQ session with myself, I
thought, "What the heck? Let's just do it," and opened a
[pull request](https://github.com/elementary-tweaks/elementary-tweaks/pull/41).
My first pull request to an open source organization! Although it didn't get
merged with the code, it did receive positive comments from the developer
himself and that made my day! I still have these changes in my own fork and am
using it in my system. To see and/or use these, you can always find my repo
[here](https://github.com/coditva/elementary-tweaks/tree/mine).
Happy customizing!

-ut
