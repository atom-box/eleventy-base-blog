---
title: Linux places
description:
date: 2019-12-05
tags:
  - linux

layout: layouts/post.njk
---

The high level directories that are outside of /home are a source of fascination. Exploring them feels like Lewis & Clark journeying to the west (or 玄奘 in 西遊記).

## Daemons

Both of these are lists of things that can be daemonized on the Ubuntu Linux. Daemonized things can run in the background. Another way to think about them is they are the things that are invoked with `systemctl`
```
$ ls /etc/systemd/system/multi-user.target.wants/   # (61 items, no sudo needed to list)
$ sudo ls /lib/systemd/system/                      # (349 items, sudo ls to list)
```