---
date: 2018-05-15T11:03:34+05:30
title: "Google Summer of Code with Neovim"
description:
meta_img:
categories:
- gsoc
- project
- plan
tags:
- gsoc
- c 
- vim
- neovim
---

So, I got selected as a student applicant for the [Google Summer of Code](https://summerofcode.withgoogle.com/) (or GSoC) and will be working with Neovim over the course of next three months!

[Neovim](http://neovim.io/) is a fork of [Vim](https://www.vim.org/), one of the most loved text editors that is used not only by the coding community but people from all over walks of life. I have been a devoted worshipper of Vim for about two years now and have fought in the [Editor wars](https://en.wikipedia.org/wiki/Editor_war) whenever the need arose.

Neovim got my attention when Vim implemented the asynchronous behavior after Neovim but I hadn't made the switch. Recently, when I was looking into the organizations that were selected for GSoC, I found Neovim and started looking for any projects that I may help in. And since I was going to work in Neovim, I thought might as well switch!

Coming back to what this post is about, I came across the idea of improving and extending the UI protocol on the ideas page of the organization. Turns out, Neovim allows external applications to implement Vim-mode by letting them open a Neovim instance and communicate with it via the UI protocol. The existing protocol is pretty sufficient but has scope for improvement. Since, I was working on implementing Vim-mode in my [pet project](https://github.com/coditva/A-Vim-Story), this hugely captured my interest.

I started lurking in the public chatroom and started following all progress for the idea that I wanted to work on. In March, I started working on my proposal and submitted a draft very early. The proposed mentor, [bfredl](https://github.com/bfredl) was very helpful in his feedback and helped shape the final proposal after about 6-7 iterations of changes and suggestions. I think the proposal that I ended up submitting was a result of his help.

The selection period after the submission was a very baffling time for me. On one hand I was pretty confident of my proposal and had high hopes for selection. On the other hand, I kept thinking if I could've added something more or removed something unnecessary. I reread my own proposal several times even though I knew I could not make any more changes.

Finally, the wait ended on April 23rd, when the projects were announced. I was in the computer lab in my college when I got a call from my brother congratulating me and I almost ran from the lab to my hostel all the while trying to check the result on my phone. I clearly remember not being able to breathe as I opened the [announced projects](https://summerofcode.withgoogle.com/projects/#5530001420582912) and saw my application status!

The first Saturday after that, I had a chat with my mentor and we came up with a concrete [plan](https://github.com/neovim/neovim/issues/8320) for the next three months. Over the next two weeks, since I had my end semester exams, I could not actively participate in the community but I went through all the pending work that my mentor had posted and on which I would be building upon in the summer.

So here I am, writing this post as I fly home after the exams and hope to have a great summer ahead doing what I love the most, with something that I feel passionate about. Let's code!

Follow the [gsoc](/tags/gsoc) tag for updates.
