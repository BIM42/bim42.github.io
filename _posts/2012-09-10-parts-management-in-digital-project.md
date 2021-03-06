---
id: 220
title: Parts Management in Digital Project
date: 2012-09-10T20:08:17+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=220
permalink: /2012/09/parts-management-in-digital-project/
categories:
  - Coordination
  - Digital Project
image: /assets/2012/09/facade.jpg
tags:
  - .NET
  - BIM Manager
  - Coordination
  - Digital Project
  - Software
---
Because of its industrial origins, Digital Project give all its power in pieces-oriented construction project where the building can be divided in a bunch of small parts easily manageable one by one. One of my current project is the design of a set of precast concrete pieces for a stone-covered looking facade.

![facade]({{ "/assets/2012/09/facade.jpg" | absolute_url }})

We have something like 2000 unique pieces of glass fiber reinforced concrete to organize, model and design. We use Digital Project for modeling these pieces, insert them in a global model for coordination purpose and extract their production drawings.

Following the production of these pieces, from the basic design to the creation of shop drawings, requires a little more investment than the usual Excel data-sheet and highlights the need for new production follow-up tools.

First, all pieces references are stored in a SQL database linked to various Excel data-sheets for visualization purpose.

These pieces are organized in a global .CATProduct, used for coordination and visualization. The main .CATProduct  datatree is regularly parsed with an .NET routine in order to check its coherence with the production records.

All .CATPart and .CATProduct are stored on a Subversion server where we can retrieve the whole editing history for each piece and cross-check it with our production records.
  
While reading the CATIA tree, I came through a lot of errors, mostly solved by cleaning the incriminated CATPart. After some research, it appears than the CATDUA function for checking and cleaning CATPart cannot be accessed through the CATIA API. Instead, I used the CATDUA V5 Batch utility with an hand-made configuration xml file in order to have only specific CATPart cleaned.

All data retrieved from our production records, the CATIA data tree and the SVN log are sorted and summarized to create a sound overview of our production.

These tools used here made us realise the need for a global and standardized way to follow the progress of BIM deliverable. Autodesk’s purchase of Glue and Vela System to create a global cloud-based solution along with the creation of GTeam by Gehry Technology seems to be the beginning of this new trend of product.