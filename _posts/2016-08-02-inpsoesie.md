---
layout:     post
title:      "Ins—poésie"
date:       2016-08-02
categories: Coding with haphazardness
tags:       ["french", "gui"]
published:  true
---

is almost finished…

![Ins—poésie gui](https://pbs.twimg.com/media/CotxajNUAAE-5ac.jpg "Inspoésie gui")

the GUI & CLI intefaces works well on Mac OSⅩ & GNU/Linux but nothing is printed well on Windows.

## Why?

- Windows uses `cp1252` instead of `utf-8` so all accents get printed wrong.
- Tkinter have an object to store variable `tk.StringVar` it's the only way to store variables and show them in the window, but it stores it in binary, and I can't see the way to reconvert it before "printing"
- as for the Windows CLI it's pretty much the same problem but considering I don't have a Windows machine it takes a bunch of time to get feedbacks.

So fuck it, I'm tired.

you can find the repo in my [gitlab](https://gitlab.com/Ryuutei/inspoesie), the software works as is, you only need Python3 and the db somewhere and setup on the python file.␄
