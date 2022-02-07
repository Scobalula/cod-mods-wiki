---
title: Setting up a Destructible Wall
tags: 
  - blackops3
  - radiant
  - ape
  - mapping
  - destruction
  - destructible cars
  - vehicles
  - damage
  - destructible
authors: 
  - Scobalula
section: bo3
description: "This tutorial explains how to set up a basic destructible wall."
---

# Setting up a Destructible Wall

Following from the previous page we will now use what we have learned and make a basic destructible wall, this includes showing how bound joints control the meshes that are hidden and applying some basic sounds and FX.

{% include alert.html title="Note" type="warning" content="Tools such as Autodesk Maya and Blender are very complicated and therefore we will very quickly glance over it in Autodesk Maya 2016 as anything more is beyond the scope of this document. A lot of destructibles coming from other Call of Duty titles will more than likely already be set up with bound meshes for destruction." %}

## Creating our destructible tags

{% include alert.html title="Note" type="info" content="If you're familiar with setting up joints and binding the required joints for each piece and state, or you already have a model ready such as a ported model, then you can skip to [Creating the destructible asset](#creating-the-destructible-asset)." %}

As mentioned in the previous page destructible states hide and show based off tags/bones. This allows us to store our entire destructible object in 1 global model that contains all states.

To begin we will be working with a basic wall that we will have destroyed by the player, in Maya we will start with the following:

TODO

We will make the following joints and give them names we can quickly recognize and remember for later, we will want to create a joint for each piece and for each state that piece has:

TODO

{% include alert.html title="Note" type="info" content="It is not necessary that your joints are moved to where the piece it controls it, but it is useful for quickly identifying them in APE and tools such as Maya, and can be useful if you decide to animate the destructible." %}

Next we will ensure that we have the meshes/vertices bound to the joints, as mentioned previously each part that is broken is a piece, and each piece will have states, so will bind them like so:

TODO

Once that is done we export 2 models, one for the actual destructible system, and one for Radiant that just has the clean parts:

TODO

Once we have done that we will create the XModel asset, we'll want to assign bullet collision and LODs, along with setting the XModel asset to animated, depending on the complexity of your model we can use the lower lods to reduce the performance impact of having bullet collision on a complicated model.

Finally, depending on your model, you can assign a collision map to the model, however I prefer to avoid this and create clips that cover my particular use case as collision is a fine tuned process to ensure players don't get stuck on objects.

## Creating the destructible asset
