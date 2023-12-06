---
title: Creating a Dump
tags: 
  - cordycep
  - ripping
  - dumping
  - creating a dump
authors: 
  - Scobalula
  - ItsNatoriousB
section: cordycep
description: "This tutorial explains how to produce a dump file for Cordycep to use."
---

# Creating a Dump

## Introduction

{% include alert.html title="Warning" type="danger" content="You agree that by following this tutorial that the authors take no responsibility for any damages caused such as game bans. Follow at your own risk." %}

{% include alert.html title="Note" type="info" content="Make sure to follow this tutorial step by step, failing to do so may result in issues or game bans." %}

In order for Cordycep to load fast files it requires a dump of the executable for the title you want to work with from memory, we cannot use the exectuable from disk as it is packed and protected.

In a similar fashion to how emulators cannot provide you with a BIOS, we cannot provide game dumps as they are property of those who own them, this is why you must dump it yourself.

## Dumping the Executable

{% include alert.html title="Warning" type="danger" content="I do not recommend sharing dumps, as dumps may contain personal information stored by the game." %}

{% include alert.html title="Warning" type="danger" content="Due to the use of stronger AC and KAC in modern titles, you need to be careful doing this or else may be banned, following this tutorial step by step should have virtually no risk of being banned." %}

The step by step process for dumping the executable for Cordycep to use is as follows:

1. Download Scylla: [https://github.com/NtQuery/Scylla](https://github.com/NtQuery/Scylla) to use for dumping from the "Releases" section, there are plenty of tools for dumping but Scylla is simple to use and is excellent at what it does. Once downloaded, unpack it to a directory of your choice.
2. Close down any platforms you have running such as Steam or BattleNET. They can get in the way by intercepting load and running integrity checks.
3. Copy both .dll files from Syclla to the Data/Deps folder of Cordycep
4. Disconnect from the Internet, you can do this by pulling out your ethernet cable or disabling your network adapter. **This is not optional in some titles, it must be done**.
5. Launch Cordycep.
6. Type "dump" and hit the spacebar once. Go to your game's directory and drag the executable to the Cordycep window. You should now see 
```
dump "D:\Battlenet\Call of Duty\_retail_\cod.exe"
```
7. Wait a few moments and you will have a successful dump created.