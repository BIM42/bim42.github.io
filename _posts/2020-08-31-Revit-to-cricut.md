---
id: 1279
title: Revit to Cricut
date: 2020-09-07T10:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1279
permalink: /2020/09/revit-to-cricut
published: true
categories:
  - Revit
image: /assets/2020/09/01 - Cricut.png
tags:
  - Revit
description: Playing with the Cricut plotter
---
One of my relative recently buy a Cricut Maker and I had the opportunity to play a little bit with it.

![The Cricut Maker]({{ "/assets/2020/09/01 - Cricut.png"| absolute_url }})

The Cricut Maker is a computer numerical control cutting machine design to cut small parts out of paper or fabrics. Its small scale make it mostly suited for hobbyist to create any kind of small production with paper, fabrics, leather, and balsa wood.

![Available tools for the Cricut]({{ "/assets/2020/09/02 - Tools.png" | absolute_url }})

Along with the cutter, the Cricut Maker can also be equipped with pens or other kind of tools

My ideas behind this was to see how to plot Revit drawing with a "hand-draw" feeling to it. I also wanted to create small paper model from a pattern designed from a Revit model.

I started with the drawing of a cube. I draw it in perspective manually in Autocad.

After various test, I finally nailed the best procedure to import a design into the Cricut Software. I start the design in AutoCAd, where I am the most proficient. There, I create two layers, one for the drawing and one for the cutting. I then import the result in Adobe Illustrator.

![The design in Illustrator]({{ "/assets/2020/09/03 - IllustratorDesign.png" | absolute_url }})

In Illustrator, I ungroup every path and create one compound path for each layer.

![The resulting layers in Illustrator]({{ "/assets/2020/09/04 - Illustrator layers.png" | absolute_url }})

I finally import this design as an SVG file in Cricut Design Space where I can send it to the machine.

![The design in Cricut Design Space]({{ "/assets/2020/09/05 - CricutDesign.png" | absolute_url }})

The result is quite nice, with some of the hand draw feeling I was looking for:

![The resulting plotted cube]({{ "/assets/2020/09/06 - ResultingCube.png" | absolute_url }})

After this first test, I created an elevation in Revit and exported it in DWG. I then imported the DWG in Illustrator, created a svg file, launched the Cricut, waited two hours...

![The plotting process]({{ "/assets/2020/09/Plotting.gif" | absolute_url }})

..and got this nice "hand drawn" elevation:

![The resulting plotted Revit elevation]({{ "/assets/2020/09/07 - Elevation.png" | absolute_url }})

I also had in mind the creation of small paper model from a Revit model. I tried with plotting and cutting at the same time and get a nice cube (again) but didn't go very far in this direction.

![The paper model of the cube]({{ "/assets/2020/09/08 - CubeModel.png" | absolute_url }})

There is a lot of possibilities with this kind of machine. I only tried the standard pen and cutter, but the available tools make for a lot of interesting combinations, like drawing and cutting paper model out of a building 3D model.

I also love the "hand draw" feeling I get with this plotter. My next productions with this machine will probably be more experiences with different pens. I will also need to find a way to get the shadows out of the Revit view.

---
*I just want to emphasise that I was not paid by Cricut nor receive the Cricut Maker as gift in exchange for this blog post. I just append to kind of like this machine!*

