---
title: Ambient Rooms
tags: 
  - blackops3
  - radiant
  - mapping
  - ambient
  - audio
authors: 
  - Scobalula
section: bo3
description: "This tutorial will demonstrate how to add Ambient Rooms to your map."
---

# Ambient Rooms

## Introduction

This tutorial will show you how to add Ambient Rooms to your map, these will allow you to make your maps more immersive by providing different sound effects and settings, etc. when in different areas.

## Adding Ambient Files

{% include alert.html type="primary" title="Note" content="For Ambient Rooms to work you must have your weapon aliases set up properly using Contexts, Reverb settings, etc. All stock weapons are set up correctly for ambient rooms." %}

{% include alert.html title="Ambient Example" type="info" content="An example of a map using ambient rooms can be downloaded [Here](https://mega.nz/file/07wB2YSL#dl3vd5y-DterveyG_89wVacxX57h-JSOkwpwC65Mqgw)." %}

{% include alert.html title="Ambient Example" type="info" content="An example of an ambient file can be downloaded [Here](https://mega.nz/file/A6Zx3aAR#2jU0caM89xsSrJRJ4C5Dy8T6hmGJcxIQwpYWPHeYgBo). This example file is included in the map example above as well." %}

To start go to `Call of Duty Black Ops III\share\raw\sound\ambients` and make a copy of the file `ambient_mod.csv` and name it whatever you like, you can also use the example provided above if you wish.

The file will look like this in a text editor:

```csv
Name,Loadspec,DefaultRoom,Reverb,ReverbDryLevel,ReverbWetLevel,EntityContextType0,EntityContextValue0,EntityContextType1,EntityContextValue1,EntityContextType2,EntityContextValue2,GlobalContextType,GlobalContextValue,Loop,Duck
mp_mod_outdoor,mpl_mod,yes,global_urban_outdoor,1,1,ringoff_plr,outdoor,water,over,,,ringoff_plr,outdoor,,
```

Here we can define "rooms" for our map, that will be played based off the area in the map we have defined below. Before we continue here is an explaination of the columns:

* **Name** - The Name of the room, this can then be used in Radiant for any rooms.
* **Loadspec** - Essentially a group name, that can be used in the config like sound aliases. It is not necessary to assign one.
* **DefaultRoom** - If set to true, this is the default room that will play if the player is not in any other room.
* **Reverb** - Reverb to use, a list of stock ones can be found in `Call of Duty Black Ops III\share\raw\sound\reverb`
* **ReverbDryLevel** - Defines the Reverb Dry Level, between 0 and 1
* **ReverbWetLevel** - Defines the Reverb Wet Level, between 0 and 1
* **EntityContextType/Value\<X\>** - Used alongside the context values in your Sound Aliases, stock weapons will generally have multiple sound aliases with different context values, these then define the contexts to play.
* **GlobalContextType/Value** - Similar to above, but sets globally.
* **Loop** - Sets a loop sound to play when in the room, useful for rain, etc.
* **Duck** - Duck to use, a list of stock ones can be found in `Call of Duty Black Ops III\share\raw\sound\ducks`

If you'd like to simply use Treyarch's ambient settings, you can extract them in-game using [HydraX](https://github.com/Scobalula/HydraX/) which should give you plenty of good examples and usable room values alongside the example above.

## Adding Triggers

We're going to need to add triggers to our map to define the ambient rooms, to do this, open your `Entity Browser` (Press B by default) and search for `trigger_multiple`, once you have found it, place it down and round any indoor areas, etc. (for example, you may want a particular "room" for sewers in your map, then a different one for small rooms).

We'll need to give it some KVPs for the compiler to find it and get data from it, open the `Entity Info` Window (Press N by default) and add the following KVPs by pressing `Add KVP`:

```
script_ambientroom - <Name of the room to play in this area>
script_ambientpriority - <Priority this room has, for example if you have subsections of an area you can overlap them and use this to give the subsections priority>
targetname - ambient_package
```

You can give the ambient triggers the audio texture in the `Textures` window to diffrentiate them from the other triggers, but this is not necessary.

Once you're done, you should end up with something like this:

![Example](https://i.imgur.com/oZc4yP6.jpg)


## Editing your Sound Zone Config

In order to actually compile the ambient data, we'll need to add our .map file and ambient file to our sound zone config.

Open your Sound Zone Config file (.szc) (`Call of Duty Black Ops III\usermaps\mapname\sound\zoneconfig\mapname.szc`) in a text editor of your choice (An editor such as VS Code with JSON built-in is recommended).

An unedited file will look like this:

```json
{
 "Name" : "mapname",
 "GameMode" : "mpl",
 "IsCommon" : false,
 "Parent" : "",
 "Overlay" : "",
 "IsStandalone" : true,
 "IsProduction" : false,
 "IsShipped" : false,
 "DontDeploy" : false,
 "NoStreamBank" : false,
 "MapFile" : "",
 "Standalone" : true,
 "Builds" : [ "T7" ],
 "Sources" : [
 {
 "Type" : "ALIAS",
 "Name" : "user_aliases",
 "Filename" : "user_aliases.csv",
 "Specs" : [ ]
},
{
 "Type" : "AMBIENT",
 "Name" : "ambient_mod",
 "Filename" : "ambient_mod.csv",
 "Specs" : [
  "mpl_mod"
  ]
},
]
}
```

For the `MapFile` property you'll want to set this to the map with the ambient triggers in it, this can be any map file but the ambient triggers **CANNOT** be in prefabs within the map provided, you can thank the person who made snd_convert not parse prefabs for this. The ambient data is compiled directly into the sound xasset struct which is why snd_convert needs to know the map file, snd_convert will generate a file called `mapname.ambientgeometry.json` for Linker to use.

This path is relative to `Call of Duty Black Ops III\map_source`, for example if we were to add The Giant's map file:


```json
"MapFile" : "zm\\zm_giant.map",
```

Keep note of the double backslash, it is required.

Next similar to sound aliases, we'll add an entry for our ambient file, for example:

```json
{
 "Type" : "AMBIENT",
 "Name" : "zm_ambient",
 "Filename" : "zm_ambient.csv",
 "Specs" : []
},
```

You can add multiple ambient files if you like from different sources.

## Complete

Assuming you've followed all the steps, everything should be working in-game, keep in mind snd_convert has quite a number of bugs and sometimes it can take several attempts to compile, keep an eye on the folder `Call of Duty Black Ops III\usermaps\mapname\sound\zone`, if you see a file named `mapname.ambientgeometry.json` you're good to go!
