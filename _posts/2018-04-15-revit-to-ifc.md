---
id: 1263
title: Online Revit To IFC Converter
date: 2018-04-15T10:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1263
permalink: /2018/04/online-revit-to-ifc-converter
published: true
categories:
  - IFC
image: /assets/2018/04/revitToIFC.jpg
tags:
  - IFC
  - Forge
  - Revit
  - revit-to-ifc
description: An online application to convert Revit files to IFC, powered by Autodesk Forge.
---

You always need to export your Revit files to IFC. A lot of great solutions run with IFC and having an efficient workflow to transfer your models to them is essential.

I recently add to convert about 2 Gb worth of Revit files to IFC. The process is relatively easy, but having to open the file, convert it to Revit 2018 (I sadly didn’t have Revit 2017 on my computer), convert it to IFC, close the file and start again with a new file wasn’t particularly enjoyable.

Exporting IFC files from Revit can be long, way too long, and blocks a Revit session during the conversion. Even if you can always leave your computer and go grab a coffee, I was looking for something more efficient.

I start by playing with the idea of a computer running Revit, controlled from the outside and used exclusively to run IFC conversions. It can quite powerful but you still need a dedicated computer and Revit licence. Furthermore, running Revit from the outside is far from reliable.

# Online Revit to IFC converter

The solution came when I realized that [Forge](https://forge.autodesk.com/) could be used to convert Revit files to IFC. After some tinkering, I was able to upload a Revit file to Forge and convert it to IFC.

Originally developed as a proof-of-concept, I finally take the time to package the whole thing into a fully-fledged web application. You can now access to [Revit to IFC](https://revittoifc.bim42.com/home), a web application to convert online your Revit files to IFC.

Just upload a Revit file, wait for a while and you will be able to download the converted IFC file.

![Revit To IFC]({{ "/assets/2018/04/revitToIfc.gif" | absolute_url }})

I tried it with a few Revit files to came up with this benchmark:

**Revit File Size**|**File Type**|**Time**
---|---|---
168 Mb|Architecture|7:40
238 Mb|Architecture|8:50
105 Mb|Furniture|3:14
130 Mb|MEP|10:53

It is obviously not exhaustive, but it can give you an idea of the performance of the service.

A word of warning : _Do not close your browser_. Even if the conversion is performed on the Forge server, you will still need the web page to download your IFC file when the conversion is complete.

A few issues are remaining. I didn't get how to set up the IFC export settings with the Forge API, so you will have to take the conversion as it is. Take care when downloading your IFC file, the button can be irresponsible as the application is downloading the file in cache before downloading it on your browser.  I also run into issues when I try to upload rather large (more than 300 Mb) Revit file. Even if the conversion started smoothly, the Forge service quickly send a “failed” error message.

![Failed Conversion]({{ "/assets/2018/04/revitToIfc - Failed.jpg" | absolute_url }})

# How it works?

After retrieving an access token using Azure Function, I am using this authorization token (in yellow in my drawing) for every subsequent action on Forge. I start by uploading the Revit file (in blue) to a "bucket" (in green), an online storage area provided by Forge. This bucket is "transient", meaning that every file uploaded in it will only stay here for 24h before being automatically deleted.

Once the file is in this bucket, I can use Forge to perform various operations called « Jobs » on this file. Here, I launch a « Job » (in red) to convert it in IFC. This job run asynchronously on the Forge servers and I check periodically the progress of the conversion.

Once the conversion is done, I can download the resulting "derivative" (converted file in the Forge lingo) as an IFC file (in blue).

![Principle]({{ "/assets/2018/04/schema.jpg" | absolute_url }})

# About the business model

I spend some time thinking about the possibilities for a business model based on the Autodesk Forge API. Forge [cost](https://forge.autodesk.com/pricing) 100 € for 100 tokens, giving you about 67 conversions.

My business model, giving away this for free, is obviously not sustainable. I am not really into cluttering the page with adds or using [your browser to mine bitcoins](https://99bitcoins.com/webmining-monetize-your-website-through-user-browsers/), so for now on, the service is running with the Forge free tier. When the free tier will run out, the service will stop working. I put a donation button, so if I can gather enough donation, I will keep the service running. But don’t expect too much.

However, my source code is available on [Github](https://github.com/simonmoreau/RevitToIFC), and if you don’t want to share your Forge credits with the rest of the world, you can use this code to run your own conversion service.