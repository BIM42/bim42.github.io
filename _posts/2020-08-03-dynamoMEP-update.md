---
id: 1277
title: DynamoMEP update
date: 2020-08-05T10:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1277
permalink: /2020/08/dynamomep-update
published: true
categories:
  - Dynamo
image: /assets/2020/08/00 - dynamoMEPLogo.png
tags:
  - Dynamo
description: The DynamoMEP package update
---

A few years ago, I released a [Dynamo package](https://www.bim42.com/2015/10/mep-design-and-dynamo/) that was intended to be the groundwork for a comprehensive solution for designing MEP systems in Revit. But as I move on to another company, I oriented myself to other BIM-related issues and let this package unattended.

But a quick exchange with [Sol Amour](https://twitter.com/solamour) about MEP in Dynamo make me realized that people where still using my package. So I should at least update it for the latest versions of Dynamo.

One thing leading to another, the update end up being more important that I had initially planed. I add a bunch of new functions that I needed and hope will be useful to you as well.

### Area

![Area nodes]({{ "/assets/2020/08/01 - AreaNodes.png" | absolute_url }})

Use these nodes to create areas. Areas can only be created in an Area Plan view, you will need to either select such a view or make sure that the current view is an area plan.

You can also use these nodes to extract information from an area, like boundary lines or associated level.

### AreaBoundary

![Area Boundary nodes]({{ "/assets/2020/08/02 - AreaBoundaryNodes.png" | absolute_url }})

These nodes allow you to create area boundaries in the current view or a selected one. Area boundary lines can be created from any curves in Dynamo. However, this node will not work with Polycurves, make sure that you explode them before using them has input curves.

### FamilyInstance

![Familly Instance nodes]({{ "/assets/2020/08/03 - FamilyInstanceNodes.png" | absolute_url }})

These nodes are used to manipulate family instance references. References give you access to all planes available in a given family. These planes are available directly in your model for every family instance.

![References in a family]({{ "/assets/2020/08/04 - ReferencesPlanes.png" | absolute_url }})

You can select them by type, by name or just retrieve all of them. You can select a plane in the family editor to see its name (1) and reference type (2).

![The plane associated with the reference]({{ "/assets/2020/08/05 - ResultingPLane.png" | absolute_url }})

### Group

![Group nodes]({{ "/assets/2020/08/06 - GroupNodes.png" | absolute_url }})

Use these nodes to create an instance of a Revit group. You will need a location point and a group type to use this node.

### GroupType

![GroupType nodes]({{ "/assets/2020/08/07 - GroupTypeNodes.png" | absolute_url }})

These nodes are used to create a new group from Revit elements. You can also retrieve an existing group type from your model, based on its name or on your selection.

### Room

![Room nodes]({{ "/assets/2020/08/08 - RoomNodes.png" | absolute_url }})

These nodes are now fully integrated with the default Dynamo Room nodes. They complete the out of the box offering by allowing you to retrieve bounding elements (wall, room separation lines, column, ...), doors and windows in this room or create. You can also use them to create a grid of points in a room.

### RoomSeparator

![RoomSeparation nodes]({{ "/assets/2020/08/09 - RoomSeparationNodes.png" | absolute_url }})

These nodes allow you to create room separation lines from Dynamo curve. Since room separation lines must be created in a specific view, you can either select the view or let dynamo use the current active view.

Room separation lines can be created from any curves in dynamo. However, this node will not work with Polycurves, make sure that you explode these before using them has input curves

The node will project curves into the plane of the view. In some case, that could create weird issues with your curve not being properly projected. If you encounter such issues, project the input curve in a plane parallel to the plane of the view beforehand.

### Space

![Space nodes]({{ "/assets/2020/08/10 - SpaceNodes.png" | absolute_url }})

Space nodes allow you to use MEP Spaces in Dynamo. You can use them to create new spaces, based on a point or on a point and its associated level. You can also use this note to retrieve identification data, associated level, location point or to create a grid of points in the space.

### SpaceSeparator

![SpaceSeparator node]({{ "/assets/2020/08/11 - SpaceSeparatorNode.png" | absolute_url }})

Space separations lines works like their counterpart for rooms. Just make sure you don’t use Polycurves.

### General modifications

The structure of the plugin has be modified, it will not be compatible with the previous version. If one of your Dynamo definitions relies on the previous version of DynamoMEP, you will need to update it for the new version.

In this release, I updated every node to make sure that they integrate nicely with the out of the box nodes of Dynamo for Revit. I also removed some redundant nodes. I updated the icons to be more consistent both inside the package and with the Revit icons. By the way, if you are looking for some guidance on how to design icons for Revit or Dynamo, you can look into the Revit icon guideline in the [Revit SDK](https://www.autodesk.com/developer-network/platform-technologies/revit). This document was of great help to me.

I hope these new functionalities will be useful to you. Don't hesitate to comment below if you see new way to expand this package, I would love to have your feedback.
