---
id: 1061
title: Room Finishes Update
date: 2016-07-02T11:58:29+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1061
permalink: /2016/07/room-finishes-update-2/
categories:
  - Revit
image: /assets/2016/07/join.jpg
tags:
  - Plugin
  - Revit
  - Software
  - room-finishing
  
---
I keep on working on my Revit add-ins. After Align, it is now Room Finishes who have been updated to support Revit 2017. Along with this update, I also have integrated some new features.

First of all, Room Finishes now support all kind of units. You just have to type your dimension with its unit symbol, and the plugin will convert it in a floor height or a skirting board height. The plug-in will now also use the default length unit of your model.

![interface]({{ "/assets/2016/07/interface.jpg" | absolute_url }})

I have to thanks [Brian Winterscheidt](https://www.linkedin.com/in/brianwinterscheidt) for this update, who was kind enough to contribute to my plug-in on Github, and point me to the Revit unit conversion system available in the API.

The other major update is the ability to join skirting board with their supporting wall. You can now join both geometries automatically. This enable one of the most wanted feature, the ability to cut the skirting board around the door.

Just select "Join geometry" before running the command, and every skirting board will be joined with its host wall.

![join]({{ "/assets/2016/07/join.jpg" | absolute_url }})

This feature could generate its fair share of warning, so I have remove every related error message. You will now be able to run this command without having to dismiss every warning that come up.

I also add some minor UI improvements, like the ability to resize the window, or sorting wall type names by alphabetical order to be able to quickly find the specific wall type you have created for your skirting board or your floor finish.

Of course, Room Finishes is still open source, the entire code can be found on [Github](https://github.com/simonmoreau/RoomFinishes).

This plug-in is already available on the [Autodesk App Store](https://apps.autodesk.com/RVT/en/Detail/Index?id=5641957956279354474&appLang=en&os=Win64). If you like it, don't hesitate to write a nice comment or add a few stars, it always means so much to me!