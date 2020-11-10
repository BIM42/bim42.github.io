---
id: 1282
title: Group Clashes 2020 Update
date: 2020-11-10T10:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1282
permalink: /2020/11/group-clashes-update
published: true
categories:
  - Coordination
image: /assets/2020/11/group-clashes-icon-large.png
tags:
  - Automation
  - Coordination
  - Navisworks
  - group-clashes
description: The 2020 Group Clashes update
---

I have finally found the time to update Group Clashes, my Navisworks plugin for grouping clash results. The app now supports Navisworks version from 2016 to 2021.

Along with the update, I added a new grouping mode called "Model". This mode will help you grouping clashes in a test containing elements from multiple models.

In my example below, I run a clash test between structural walls (Selection A) and all services (Selection B). In the Selection B, we have elements coming from 3 models (Duplex_Plumbing.rvt, Duplex_Mechanical.rvt and Duplex_Electrical.rvt).

![The Products page]({{ "/assets/2020/11/01 - Clash Test.png" | absolute_url }})

I select this clash test in the Group Clashes panel and group the result using the "ModelB" grouping rule. I end up with a group for each model in the Selection B.

![The Products page]({{ "/assets/2020/11/02 - Grouped Clashes.png" | absolute_url }})

As usual, you will find this new version of Group Clashes on the [Autodesk App Store](https://apps.autodesk.com/NAVIS/en/Detail/Index?id=7544208847822212204&appLang=en&os=Win64). If you want to develop your own grouping rules, you can also find the entire source code on [Github](https://github.com/simonmoreau/GroupClashes).

Happy grouping!

 