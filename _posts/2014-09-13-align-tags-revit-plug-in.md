---
id: 571
title: Align Tags Revit Plug-In
date: 2014-09-13T09:00:25+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=571
permalink: /2014/09/align-tags-revit-plug-in/
categories:
  - Revit
image: /assets/2014/09/DistributeAfter.jpg
tags:
  - .NET
  - BIM Manager
  - Revit
  - align
---
I just release a new add-in for Revit on the Autodesk App Exchange for aligning and sorting tags on a view.

This tool is based on the Align command you probably already know from a large bunch of software, from PowerPoint to Adobe Illustrator. It is composed of a set of commands to align or distribute tags on a Revit view, and it is pretty easy to use:

![Commands]({{ "/assets/2014/09/Commands.png" | absolute_url }})

To align two or more of tags, just select them, and select one of the direction of the Align command.

For example, with the Align Left command :

![AlignBefore]({{ "/assets/2014/09/AlignBefore.jpg" | absolute_url }}) ![AlignAfter]({{ "/assets/2014/09/AlignAfter.png" | absolute_url }})

Every selected tag is aligned with the left one. The alignment reference point is the tag base point (where their reference planes intersect).

To distribute three or more tags along an axis, select them and specify the direction.

For example, with the Distribute Vertically command:

![DistributeBefore]({{ "/assets/2014/09/DistributeBefore.jpg" | absolute_url }}) ![DistributeAfter]({{ "/assets/2014/09/DistributeAfter.jpg" | absolute_url }})

Vertical space between selected tags is distributed evenly among them. The position reference point is still the tag base point.

Under the hood, everything is pretty simple. The application pick up every tag origin point, and sort them along the _View.RightDirection_ or _View.UpDirection_ regarding the direction you select.

Once these origin points are placed along the chosen vector, each _Tag.TagHeadPosition_ is set to its new position.

The entire source code can be found on [Bitbucket](https://bitbucket.org/simonmoreau/align-tag "Align Tags"), my new place of choice for code hosting. Feel free to use it for whatever you want.

The Align Revit add-in is already available for Revit 2014 and 2015 on the [Autodesk App Exchange](https://apps.exchange.autodesk.com/RVT/en/Detail/Index?id=appstore.exchange.autodesk.com%3aalign_windows32and64%3aen "Align").