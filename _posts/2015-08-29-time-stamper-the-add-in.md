---
id: 929
title: Time Stamper, the Add-In
date: 2015-08-29T11:29:46+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=929
permalink: /2015/08/time-stamper-the-add-in/
categories:
  - Coordination
image: /assets/2015/08/ColorsByModel.jpg
tags:
  - BIM Manager
  - Coordination
  - Documentation
  - Revit
  - time-stamper
---
There is no easy way to override the color of an entire Revit link. Since most of my work involves linking Revit model from various subcontractors, this is something I miss badly.

Until recently, I was still using some [workset hack](https://www.bim42.com/2013/02/revit-linked-models-visibility/) to create filters on linked models. These filters were allowing me to display linked model with my color of choice.

But relying on workset leave much to be desired, and I have to find another solution.

I recently came up with [a different solution](https://www.bim42.com/2015/07/model-timestamp/), where each model element know where they came from.

The idea is to add file name, date and version in shared parameters on every model element. I created the corresponding Revit Add-In, and it is now available on the [Autodesk App Exchange](https://apps.exchange.autodesk.com/RVT/en/Detail/Index?id=appstore.exchange.autodesk.com%3Atimestamps_windows64%3Aen).

This application will:

  * Ask for identification information
  * Create four shared parameters on every category
  * Fill these shared parameters with identification information

The code itself is pretty easy, but there is a lot of applications.

First, it becomes easy to create filters on linked model. These filters allow us to display each linked model with a different color.

![ColorsByModel]({{ "/assets/2015/08/ColorsByModel.jpg" | absolute_url }})

But it also enables us to tag the origin of every element, like we can see in the following screenshot.

![IdentifyElements]({{ "/assets/2015/08/IdentifyElements.jpg" | absolute_url }})

You can create a linked models schedule, with date and version.

![LinkedFilesSchedule]({{ "/assets/2015/08/LinkedFilesSchedule.jpg" | absolute_url }})

To help you create filters and tags with these parameters, you will find [here]({{ "/assets/2015/08/BIM42_SharedParameters.txt" | absolute_url }}) the shared parameter text file. Please also note that the application uses a list of categories to create the four shared parameters. You will find this list [here]({{ "/assets/2015/08/categories.txt" | absolute_url }}).

I hope this application will help you in your work, don't hesitate to share your suggestions in the comments.