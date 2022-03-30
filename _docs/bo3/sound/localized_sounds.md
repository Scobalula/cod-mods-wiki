---
title: Localized Audio
tags: 
  - blackops3
  - audio
  - localization
  - localized
  - aliases
authors: 
  - Scobalula
section: bo3
description: "This tutorial explains how to create localized audio."
---

# Localized Audio

## Introduction

As is the case with the majority of AAA games released in the last couple of decades, Call of Duty: Black Ops III has full support for localized audio across a wide range of locales. If you wish to utilize localized audio in your pojects, it is very simple and we will demonstrate it below.

## Preparing your audio

To start off you will need to ensure you have the required audio for the supported locales. Based off Steam and Launcher, Black Ops III supports the following regions:

**Name**|**Shorthand Name**
:-----:|:-----:
English|en
French|fr
Italian|it
Spanish|es
German|ge
Portuguese|bp
Russian|ru
Polish|po
Japanese|jp
Traditional Chinese|tc
Simplified Chinese|sc
English Arabic|ea

You will require sounds for each region during compile, if you do not have sounds for a particular region, then I recommend falling back to English by and copy and pasting it, but you will still require the folder to exist and contain the sounds for the region.

Next you'll need to create a new folder in Black Ops III's directory:

``soundloc_assets``

This is where localized sounds will reside, in this folder you'll also need to create a folder for each language using the shorthand name, for each language this would be:

```csv
soundloc_assets\en
soundloc_assets\fr
soundloc_assets\it
soundloc_assets\es
soundloc_assets\ge
soundloc_assets\bp
soundloc_assets\ru
soundloc_assets\po
soundloc_assets\jp
soundloc_assets\tc
soundloc_assets\sc
soundloc_assets\ea
```

You sound alias paths will be relative to `soundloc_assets\<locale>`, so if your audio is contained in `soundloc_assets\<locale>\some_character\scream.wav` then your alias file spec should be `some_character\scream.wav`.

{% include alert.html title="Note" type="warning" content="You cannot mix and match unlocalized/localized audio, once you decide on localized audio, you must ensure the sounds do not exist in `sound_assets` or else snd_convert will throw an error." %}

## Compiling

Once done you can compile your map/mod and with any luck you'll have working localized audio. SND_Convert isn't exactly a shining example of a good tool and may require multiple attempts to compile audio, especially when dealing with large amounts.