---
title: Using Parasyte
tags: 
  - parasyte
  - ripping
authors: 
  - Scobalula
section: parasyte
description: "This tutorial explains how to use Parasyte."
---

# Using Parasyte

{% include alert.html title="Note" type="warning" content="When sending commands to Parasyte, it looks for spaces to split commands and data by, when providing file paths or names that contain spaces, make sure to put them in quotes so that Parasyte doesn't split them, like this: ```loadlist \"C:\I have a space\which makes me sad if there are no quotes around me.txt\"```" %}

While Parasyte's CLI can be intimidating to many, it's incredibly simple to use for most people. Once you get the hang of it, it's like a walk in the park.

First off, make sure you have followed the [Creating a Dump](/docs/parasyte/creating_a_dump) for the title/s you want to work with, it's very important to do this step carefully to produce what Parasyte needs and to ensure you do not get targetted by the anti-cheats.

An example of what Parasyte should look like with a game initialized and a file loaded:

![Example](/assets/img/parasyte_example.png)

## Quick Start

### Launching straight in

If you just want to deep dive into using Parasyte and have followed the page detailing producing a dump file, then a quick way to launch into working with the title you want is the following command string:

```
sethandler <name> init "C:\GameDirectory\Example" setlocaleprefix <locale> loadcommonfiles
```

For example:

```
sethandler mw4 init "C:\Battlenet\Call of Duty Modern Warfare" setlocaleprefix "english\eng_" loadcommonfiles
```

The `setlocaleprefix` and `init` must be changed to match your installation depending on the title. You can get an idea of what the localization prefix is by looking at your install folder/storage to see what prefix is generally applied to localized files.

It can take some time to initialize some titles, so please be patient while it does its work.

Some common files may fail to load, you can ignore this, as its due to installation differences and older files that have been renamed.

### Loading Files

Loading files is very simple, you can simply pass into the command:

```
load filename
```

For example:

```
load mp_hackney_yard
```

You can also load multiple at once:

```
load mp_hackney_yard load mp_shipment
```

You can also make a txt file list and load it like so:

```
loadlist C:\list.txt
```

Once done you can unload files by simply passing in the unload command:

```
unload filename
```

For example:

```
unload mp_hackney_yard
```

You can also unload all files, or non-common files, useful for switching levels for export:

```
unloadall
```

```
unloadallnoncommon
```

{% include alert.html title="Note" type="info" content="If you're stuck for what file names are for particular levels, the wiki usually has names of each level's codename you can use." %}

### Loading Files by UI Names

Modern titles contain thousands of files with some assets being shared in single files with different names, with this in mind it might be more desirable to be able to load the content you want by the name you see in the UI. This can be done using the **loadalias** command.

{% include alert.html title="Note" type="warning" content="Not all titles support alias based loading. The list of titles that support it and what is supported within the alias files is constantly changing, so make sure to check the .JSON files in Parasyte's Data folder to see what it is supported." %}

The set of data we parse for the `loadalias` command is:

* Campaign Levels
* Multiplayer Maps
* Operators
* Weapons

When loading Operators and Weapons you only need to know the name of it and not the bundle names, for example entering `loadalias "AK-47"` will load the AK-47 and all attachments and variants for it. For operators, this includes all their skins including head, body, and viewhands models.

To load maps, simply pass the map name, for example: `loadalias "Eagle's Nest"`

## Creating Batch Files

All commands that Parasyte accepts through the CLI can be passed to its exe. This makes it useful to create batch files that handle specific tasks in 1 click.

An example would be creating a batch file for each title and simply having to click 1 button to work with that title, Parasyte comes with batch files for each supported handler that you can modify to work with what you want.

## Detailed Command Information

For those who just want the juicy details straight up, here's a list of commands:

| Command             | Description                                                             | Example                                                                |
|---------------------|-------------------------------------------------------------------------|------------------------------------------------------------------------|
| explain             | Explains the provided command.                                          | `explain help explain loadcommonfiles`                                 |
| help                | Shows this help message.                                                | `help`                                                                 |
| sethandler          | Sets the current handler.                                               | `sethandler mw4`                                                       |
| deinit              | Unloads all files and deinitializes the current handler.                | `deinit`                                                               |
| init                | Initializes the current handler with a given game path.                 | `init "C:\Path\To\Game"`                                               |
| setlocaleprefix     | Sets the game specific locale prefix.                                   | `setlocaleprefix english\en_`                                          |
| loadcommonfiles     | Loads common files for the current handler.                             | `loadcommonfiles`                                                      |
| load                | Loads a file with the given name.                                       | `load mp_shipment`                                                     |
| loadalias           | Loads files from the alias cache with the given name.                   | `loadalias "AK-47" loadalias "Polina" loadalias "Eagle's Nest"`        |
| loadwc              | Loads a file using wildcard matching if supported by the handler.       | `loadwc *mpapa5*`                                                      |
| loadlist            | Loads files using a list file.                                          | `loadlist C:\list.txt`                                                 |
| cachelist           | Caches a list of files, useful for games that store old files.          | `cachelist C:\list.txt`                                                |
| cacheload           | Loads files from the cache list, useful for games that store old files. | `cacheload *mpapa5* cacheload mp_filename_tr`                          |
| unload              | Unloads a file with the given name.                                     | `unload Ma_rv`                                                         |
| unloadall           | Unloads all files, including common files.                              | `unloadall`                                                            |
| unloadallnoncommon  | Unloads all non-common files.                                           | `unloadallnoncommon`                                                   |
| unloadalias         | Unloads all files potentially loaded by the given alias.                | `unloadalias "AK-47" unloadalias "Polina" unloadalias "Eagle's Nest"`  |
| listfiles           | Lists all potential files to the log.                                   | `listfiles`                                                            |
| enableprogress      | Enables progress bars if supported by the handler.                      | `enableprogress`                                                       |
| disableprogress     | Disables progress bars if supported by the handler.                     | `enableprogress`                                                       |
| exit                | Exits Parasyte.                                                         | `exit`                                                                 |
