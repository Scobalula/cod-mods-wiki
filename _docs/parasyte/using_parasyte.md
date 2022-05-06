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
description: "This tutorial explains how to use Parasyte."
---

# Using Parasyte

While Parasyte's CLI can be intimidating to many, it's incredibly simple to use for most people.

First off, make sure you have followed the [Creating a Dump](docs/parasyte/creating_a_dump) for the title/s you want to work with, it's very important to do this step carefully to produce what Parasyte needs and to ensure you do not get targetted by the anti-cheats.

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
sethandler mw4 init "C:\Battlenet\Call of Duty Modern Warfare" setlocaleprefix "english\\eng_" loadcommonfiles
```

The `setlocaleprefix` must be changed to match your installation depending on the title.

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

{% include alert.html title="Example" type="info" content="If you're stuck for what file names are for particular levels, the wiki usually has names of each level's codename you can use." %}

## Detailed Command Information

For those who just want the juicy details straight up, here's a list of commands:

| Command            | Description                                                                                                    | Example                           |
|--------------------|----------------------------------------------------------------------------------------------------------------|-----------------------------------|
| sethandler         | Sets the current handler to use for loading.                                                                   | `sethandler mw4`                  |
| deinit             | Deinitializes the current handler, unloading all data loaded by it                                             | `deinit`                          |
| init               | Initializes the current handler, loading required data and creating the required state file.                   | `init`                            |
| setlocaleprefix    | Sets the locale prefix, this is game dependent and is dependent on the installation you have.                  | `setlocaleprefix "english\\eng_"` |
| loadcommonfiles    | Loads the common files for the current handler. These are required for referenced common content to be loaded. | `loadcommonfiles`                 |
| load               | Loads the provided file and its localized files.                                                               | `load mp_shipment`                |
| loadlist           | Loads a list of files from a text file. The file should contain the file names on each line.                   | `loadlist C:\List.txt`            |
| unload             | Unloads the provided file and all implicitly loaded by it.                                                     | `unload mp_shipment`              |
| unloadallnoncommon | Unloads all files that aren't marked as common files.                                                          | `unloadallnoncommon`              |
| exit               | Exits Parasyte.                                                                                                | `exit`                            |
