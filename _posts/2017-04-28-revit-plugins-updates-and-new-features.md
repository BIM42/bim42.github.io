---
id: 1161
title: Revit plugins updates and new features
date: 2017-04-28T04:54:57+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1161
permalink: /2017/04/revit-plugins-updates-and-new-features/
categories:
  - Revit
  - Uncategorized
image: /assets/2017/04/AlignAirTerminal.gif
tags:
  - .NET
  - Documentation
  - Plugin
  - Revit
  - align
  - room-finishing
  - time-stamper
---
As usual during this time of the year, I published the new version of my plugins for Revit.

# Align

The big improvement this year is the ability to align any type of elements, annotations or tags. I must thank [Deyan Nenov](https://twitter.com/@didonenov) and his large contribution to the source code for this new feature.

From now on, you can select any kind of element and align or distribute them evenly. This feature use the bounding box of the element in the view as a reference.

![AlignAirTerminal]({{ "/assets/2017/04/AlignAirTerminal.gif" | absolute_url }})
Align or distribute all elements

The Align command is still view-dependent, so using it in section view or in a plan view will not have the same effect on the overall position of a given element. A word of caution however, the align function can be unreliable in a 3D view.

![AlignAirTerminalSection]({{ "/assets/2017/04/AlignAirTerminalSection.gif" | absolute_url }})
View-dependent align functions

Of course, you can still use it to align or distribute your tags and annotations, and it even works with viewports:

![AlignViews]({{ "/assets/2017/04/AlignViews.gif" | absolute_url }})
Align viewports

Along with these improvement, Align now fully support Area tags, and a few bugs have been eliminated. You can now use Align even if on tag without a leader, and multi-leader text are now fully supported, and some selection subtlety have been introduced.

![AlignTag]({{ "/assets/2017/04/AlignTag.gif" | absolute_url }})
Align tags and texts

I haven’t tested it with all categories, if you find something weird, please let me know, I would be happy to fix it.

You can find this new version on the [Autodesk App Store](https://apps.autodesk.com/ACD/en/Detail/Index?id=2903508825431715905&appLang=en&os=Win32_64).

# Room Finishing

Along with the support for Revit 2018, I corrected an issue where a skirting board was created even if the room was not bound by a wall. From now on, Room Finishing will not create a skirting board along room bounding lines.

![RoomFinishes]({{ "/assets/2017/04/RoomFinishes.gif" | absolute_url }})
Support room with room boundary lines

Room Finishing is also available on the [App Store](https://apps.autodesk.com/ACD/en/Detail/Index?id=5641957956279354474&appLang=en&os=Win64).

# Time Stamper

The Time Stamper plugin got a few improvements this year along with the usual bug smashing.

You can now choose between applying your time stamp to every element, or just the one visible in the view. This will give you the ability to filter on which element you want to apply a stamp.

You can also choose to keep or override an existing value, this should help you keep the history of a given element.

A few bugs where corrected, making the creation of the four shared parameters far more reliable. Groups are now supported.

![TimeStamp]({{ "/assets/2017/04/TimeStamp.gif" | absolute_url }})
Support for groups

Time Stamper is now available [here](https://apps.autodesk.com/ACD/en/Detail/Index?id=232313135819866372&appLang=en&os=Win64).

These new versions are now available on the [Autodesk App Store](https://apps.autodesk.com/en/Publisher/PublisherHomepage?ID=200810282052581). Don't hesitate to report any issue you might find in them or ask for improvement.

These plugins are open source, you can find the source code [here](https://github.com/simonmoreau/RoomFinishes), [here](https://bitbucket.org/simonmoreau/align-tag) and [here](https://bitbucket.org/simonmoreau/timestamp). Feel free to use it on your own project or contribute to these projects.