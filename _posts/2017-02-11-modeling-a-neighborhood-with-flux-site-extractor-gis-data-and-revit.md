---
id: 1131
title: Modeling a neighborhood with Flux Site Extractor, GIS data and Revit
date: 2017-02-11T20:47:17+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1131
permalink: /2017/02/modeling-a-neighborhood-with-flux-site-extractor-gis-data-and-revit/
categories:
  - Revit
image: /assets/2017/02/01-Flux-Site-EXtractor.jpg
tags:
  - Flux
  - GIS
  - Plugin
  - Revit
---
Since [my last post](https://www.bim42.com/2017/01/modeling-paris-with-infraworks/), I kept on working on urban development. I particularly think about importing GIS data into our usual authoring tools. My experience with Infraworks was interesting, but it is still difficult to use this data in a Revit model.

The most promising resource out there for creating a context in a Revit model is the [Flux Site Extractor](https://labs.flux.io/extractor/). You select an area, add some features to extract and send them to a Flux project.

![01-Flux-Site-EXtractor]({{ "/assets/2017/02/01-Flux-Site-EXtractor.jpg" | absolute_url }})
The Flux Site Extractor interface

After retrieving this data in my Flux Site Project, I use the [Flux Dynamo nodes](https://drive.google.com/file/d/0B_fvbfIWQ5JJMTVLbUtxUGxfZ2M/view?usp=sharing&resourcekey=0-LuPiAcnDmuqftKy26eqXGw) to get the topography as a mesh, extract the vertices of this mesh as points and use these points to create a toposurface in Revit.

![02-Toposurface-from-Flux]({{ "/assets/2017/02/02-Toposurface-from-Flux.jpg" | absolute_url }})
Creating a toposurface from the Flux Site Extractor

Building profiles and heights came from OpenStreetMap, and aren't accurate enough to be used for site analysis. But I am using building profiles to draw on a plan view the footprint of every building retreived with Flux. This will help me futher down the road to align my buildings on the toposurface.

![03-Buildings-Footprints]({{ "/assets/2017/02/03-Buildings-Footprints.jpg" | absolute_url }})
Buildings footprints drawn in a plan view

I found more accurate data on the parisian buildings on the [APUR Open Data plateform](http://cassini-apur.opendata.arcgis.com/). I download this data as a shapefile containing every building in Paris.

Obviously, this dataset is too large to be imported as it in Revit. I am using [QGIS](http://www.qgis.org/en/site/), an open source GIS application, to extract a subset of this file. To do so, I draw a polygon encompassing the few city blocks I want to retrieve and use the "Clip" function to create a new shapefile containing only the selected buildings.

![03-Isolate-Buildings-Blocks]({{ "/assets/2017/02/03-Isolate-Buildings-Blocks.jpg" | absolute_url }})
Isolate the propers city blocks

I am using the [DynamoGIS](https://github.com/sharadkjaiswal/DynamoGIS) package to import this shapefile into Revit. These nodes allow me to read the file and extract the shapes of the buildings.

The most difficult thing here was to include inner boundaries in a building shape. These boundaries are not taken into account by the Surface.ByPatch node. I manage to split the first surface (the largest) using the inner curve. This allow me to create the hollowed surface.

![04-Inner-boundaries]({{ "/assets/2017/02/04-Inner-boundaries.jpg" | absolute_url }})
Highlight of inner boundaries

The DynamoGIS include nodes to query any value associated with shapes. I am using them to retrieve building heights in the dataset and extrude my buildings at their proper height.

Since it is GIS data, I am using a nice tip from [LandArch](https://landarchbim.com/2016/06/15/import-shapefiles-with-dynamogis/) to move my geometry near the project base point, and make it usable in Revit.

I am using the FamilyInstance.ByGeometry node from the great [Spring nodes](https://dynamonodes.com/2016/01/28/what-is-spring-nodes/) of [Dimitar Venkov](https://twitter.com/5devene?lang=en) to create the buildings as mass families.

[This Dynamo definition](https://drive.google.com/file/d/0B_fvbfIWQ5JJeExWd0szejFtM1k/view?usp=sharing&resourcekey=0-KSzx2eDvtB_ER5cpKnqaGQ) create a mass family for every building in the shapefile, extruded up to its actual height. Combined with the toposurface created with Flux, this look like an actual neighborhood, where you can think about massing and site integration directly in Revit.

![05-Site-integration]({{ "/assets/2017/02/05-Site-integration.jpg" | absolute_url }})
Site integration of a project

This process still has a few issues. The buildings aren't adjusted at the toposurface and aligning them with the toposurface created with the Flux Site Extractor involve some manipulations. I still have some work to do on this process to streamline it, and get a more accurate representation of an existing site.

![06-Site-intégration]({{ "/assets/2017/02/06-Site-intégration.jpg" | absolute_url }})
Another view of the project