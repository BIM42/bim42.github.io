---
id: 527
title: Room Finishes Update
date: 2014-08-09T04:39:58+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=527
permalink: /2014/08/room-finishes-update/
categories:
  - Revit
image: /assets/2014/08/RoomHeight.jpg
tags:
  - .NET
  - Automation
  - Revit
  - Software
  - room-finishing
---
A new version of my Revit plug-in Room Finishes is available on the Autodesk App Exchange.

This major update integrate a new feature for creating floor finishes. The main idea is to create a floor that follow the general outline of a room, at a given height offset from the room level.

The first application is to model quickly floor finishes inside every selected room. Just select a floor type, a height offset and the plug-in will model a finish floor on every selected room.

![CreateInterface]({{ "/assets/2014/08/CreateInterface.jpg" | absolute_url }})

We can see here the floor created with the previous parameters:

![ResultDetail]({{ "/assets/2014/08/ResultDetail.jpg" | absolute_url }})

The whole idea came when I have to model an insulation just under the slab for more than a thousand of rooms. Luckily, these rooms where correctly modeled, with their upper limit set just below the upper slab.

![RoomHeight]({{ "/assets/2014/08/RoomHeight.jpg" | absolute_url }})

So I wrote a small piece of code for creating a floor with the same boundaries than the selected rooms. Just like my previous plug-in for creating skirting board, you just have to select a type of floor to create, enter the desired height and the application will create the floor in the selected rooms.

In my problem, the distance between the room level and the upper slab could change, so I introduce an additional feature, the ability to select one of the parameter of the room to define the height of the floor.

![ParamSelector]({{ "/assets/2014/08/ParamSelector.jpg" | absolute_url }})

Since my rooms are modeled from slab to slab, I just have to select the Unbounded Height room parameter to create insulation at the correct elevation.

![InsultationResult]({{ "/assets/2014/08/InsultationResult.jpg" | absolute_url }})

I am also using it to draw a temporary floor at the ceilling height in every room of a project. This temporary floor is used to run a clash detection to check if every HVAC objects are correctly placed above the drop-ceiling height.

The application is already available in the [Autodesk App Exchange](http://apps.exchange.autodesk.com/RVT/en/Detail/Index?id=appstore.exchange.autodesk.com%3aroomfinishing_windows32and64%3aen "Autodesk App Exchange"). If you already have installed Room Finishes, just download the update from the same link.

I also finally clean up my code and upload it on GitHub for everyone to see. The source code is freely available [here](https://github.com/simonmoreau/RoomFinishes "GitHub") as a Visual Studio 2012 solution. Feel free to download and use it for any of your own application. I would be delighted if you can use it for something useful.