---
title: Using Parasyte with Greyhound
tags: 
  - parasyte
  - ripping
  - greyhound
authors: 
  - Scobalula
section: parasyte
description: "This tutorial explains how to use Parasyte with Greyhound."
---

# Using Parasyte with Greyhound

{% include alert.html title="Note" type="info" content="Make sure to follow the initial guide for [Using Parasyte](/docs/parasyte/using_parasyte)." %}

Parasyte by itself is not an extraction tool and only handles making use of executable dumps to handle loading content. All asset extraction must still be done using pre-existing tools.

Using Greyhound with Parasyte is no different to using Greyhound with a running game as Parasyte emulates the game and tools such as Greyhound to load from it.

To start, ensure you've followed the [Using Parasyte](/docs/parasyte/using_parasyte) page to load files. Once done, you can simply click `Load Game` in Greyhound to load assets and export just like before, maintaining your pre-existing workflows.

{% include alert.html title="Note" type="info" content="When you load and unload files, make sure to click `Load Game` to refresh the asset list." %}

If you've followed everything correctly, you should end up with Parasyte having files loaded and Greyhound showing assets loaded for that particular title:

![Example](/assets/img/parasyte_example_greyhound.png)