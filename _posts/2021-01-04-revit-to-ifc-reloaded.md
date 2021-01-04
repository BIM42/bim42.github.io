---
id: 1283
title: Revit To IFC Reloaded
date: 2021-01-04T10:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1283
permalink: /2021/01/revit-to-ifc-reloaded
published: true
categories:
  - Coordination
image: /assets/2021/01/revit-to-ifc-logo-blue square.png
tags:
  - Automation
  - Coordination
  - IFC
  - revit-to-ifc
description: The new version of the Revit To IFC Online converter
---

A while ago, I created an online conversion tool to transform Revit files to IFC. At the time, I wanted to experiment with the Model Derivate API of Autodesk Forge. I published this small service for free and made use of the free Tier of my Autodesk Forge account to allow anyone to use it.

This solution ended up being more successful than I expected and my free Forge credits where quickly depleted. Since I can’t really fund the conversion of every Revit file in the work, I had to stop the service.

However, it seemed to be a valuable solution for a lot of people without a Revit licence. So, I build a new version of the Revit To IFC, this time with an actual business model behind it.

This new version is now named [RVT To IFC](https://rvt-to-ifc.bim42.com/) and is a new application build from the ground up. However, the main and only feature remains the same, uploading a Revit file and downloading back its conversion in IFC.

![The main page]({{ "/assets/2021/01/01 - Home.png" | absolute_url }})

Behind the scene, the application makes use of a different service in the Autodesk Forge offering. Instead of converting directly with the Model Derivative API, I am using the Design Automation API to run online my own Revit plugin to export IFC.

![The application architecture]({{ "/assets/2021/01/02 - Architecture.png" | absolute_url }})

This offers a more interesting cost structure based on the time of the conversion. Furthermore, this will allow access to the settings of the IFC export, something that what not possible with the Model Derivative API. I have yet to implement this feature, it should come with my next version of the application.

![The upload page]({{ "/assets/2021/01/03 - Upload.png" | absolute_url }})

I am also using the Forge Data Management API to upload and download Revit and resulting IFC. All Revit and IFC files are only stored for the time of the conversion and are deleted afterward. The entire back-end is built with Azure Functions to keep the solution easy to build and deploy.

In this new version, each conversion will cost you one euro. They are sold as bundles of 10 or 50 conversions, with a fixed unit price. Even if the Design Automation API is the less expensive solution, I can’t offer any free tier.

If you want to use your own Forge account to run the conversion, the entire solution is open-source and available [on GitHub](https://github.com/simonmoreau/RevitToIFCApp).
I hope you will find this application useful, don’t hesitate to share it with all your ArchiCAD-lover friends who ended up with a Revit model from their contractor or engineer.
