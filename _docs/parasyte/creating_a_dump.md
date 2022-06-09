---
title: Creating a Dump
tags: 
  - parasyte
  - ripping
  - dumping
  - creating a dump
authors: 
  - Scobalula
section: parasyte
description: "This tutorial explains how to produce a dump file for Parasyte to use."
---

# Creating a Dump

## Introduction

{% include alert.html title="Warning" type="danger" content="You agree that by following this tutorial that the authors take no responsibility for any damages caused such as game bans. Follow at your own risk." %}

{% include alert.html title="Note" type="info" content="Make sure to follow this tutorial step by step, failing to do so may result in issues or game bans." %}

In order for Parasyte to load fast files it requires a dump of the executable for the title you want to work with from memory, we cannot use the exectuable from disk as it is packed and protected.

In a similar fashion to how emulators cannot provide you with a BIOS, we cannot provide game dumps as they are property of those who own them, this is why you must dump it yourself.

## Dumping the Executable

{% include alert.html title="Warning" type="danger" content="I do not recommend sharing dumps, as dumps may contain personal information stored by the game." %}

{% include alert.html title="Warning" type="danger" content="Due to the use of stronger AC and KAC in modern titles, you need to be careful doing this or else may be banned, following this tutorial step by step should have virtually no risk of being banned." %}

The step by step process for dumping the executable for Parasyte to use is as follows:

1. Download Scylla: [https://github.com/NtQuery/Scylla](https://github.com/NtQuery/Scylla) to use for dumping from the "Releases" section, there are plenty of tools for dumping but Scylla is simple to use and is excellent at what it does. Once downloaded, unpack it to a directory of your choice.
2. Disconnect from the Internet, you can do this by pulling out your ethernet cable or disabling your network adapter. **This is not optional in some titles, it must be done**.
3. Go to your game's directory and open its executable, wait a few seconds for it to fully load. In some titles, you will get a screen saying the game cannot authenticate with the service, at this point, the executable is unpacked in memory.
4. Open Resource Monitor in Windows and click the CPU tab, try to find the game's executable, once found, right click on it and click "Suspend Process".
5. Return to where you unpacked Scylla and run "Scylla_x64.exe", this will open a window with several options available to you.
6. Under the "Attach to an active process" section, find the game's executable name in the drop down menu.
7. Once found, select it.
8. Once selected, the "Dump" button should become available, you can now click it.
9. Scylla will ask you where to save the dump, you'll want to save to the "Data" folder in Parasye's folder.
10. Once done, you can now close the game and all the tools we have used to dump it.