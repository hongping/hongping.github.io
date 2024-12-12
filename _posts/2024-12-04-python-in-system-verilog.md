---
layout: post
title: Maintaining Hardware Design Environment
date: 2024-12-12 19:41 +0800
published: false
---
As a hobbist in hardware development, I often try out different open source EDA tools in WSL2, and that involved testing different versions of a tool. Which means, I can't simply add a tool to the $PATH, or setup any others required variable by defaulting to a static version.

Most of the time, I ended up needing to write the recipe in a shell script and source them. 