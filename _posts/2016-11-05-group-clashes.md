---
id: 1078
title: Group Clashes
date: 2016-11-05T17:05:09+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1078
permalink: /2016/11/group-clashes/
categories:
  - Coordination
image: /assets/2016/11/neuro.gif
tags:
  - Autodesk
  - Automation
  - Coordination
  - Navisworks
  - group-clashes
---
If you have already run some clash detection, you have probably ended up with thousand of clashes, and wondering how you could find something interesting in this mess.

![neuro]({{ "/assets/2016/11/neuro.gif" | absolute_url }})

Furthermore, finding clashes is not really useful in itself. The purpose of clash detection is to be able to find and hopefully solve issues in the design. And we quickly realize that a clash is not an issue in itself, but can be the symptom of an issue. Being able to extract a real issue from a meaningless bunch of clashes is what we are looking for. This is how we can gain some return from clash detection.

To do so, I tend to focus on specific subjects. Instead of running useless clash detections between entire model, I rather focus on specific issues and know beforehand what I am looking for.

For example, instead of running a clash detection between an architectural and a structural model, and end up with thousand of clashes, we can run a clash detection only between architectural rooms and structural concrete beams. As we know which type of element are involved in the clash detection, we can understand what a "clash" mean. Here, it means that there is a beam below the ceiling height. Furthermore, we can also group these clashes by room, and immediately highlight the problematic area where we can focus our efforts.

![clearHeadroom]({{ "/assets/2016/11/clearHeadroom.jpg" | absolute_url }})

To help in this regards, I created a plugin for Navisworks Manage to automatically group these clashes. After a beta version published last year, I finally take the time to properly develop a full-fledged application and publish it on the [Autodesk App Store](https://apps.autodesk.com/NAVIS/en/Detail/Index?id=7544208847822212204&appLang=en&os=Win64). It is a fully redesigned Group Clashes Navisworks plugin, with a new interface that integrates seamlessly into the Navisworks interface.

![Interface]({{ "/assets/2016/11/Interface.jpg" | absolute_url }})

The grouping rules have also been redesigned, and now include the following methods :

  * Group by Level: This rule will group clashes according to their nearest level, and name the group after the level.

![ByLevels]({{ "/assets/2016/11/ByLevels.jpg" | absolute_url }})

  * Group by Grid Intersection: This rule will group clashes according to their nearest grid intersection, and name the group after these grids.

![ByGrids]({{ "/assets/2016/11/ByGrids.jpg" | absolute_url }})

  * Group by Selection A: This rule will group all clashes belonging to an element of the selection A, and name the group after this element. As an example, if a room in Selection A has many clashes with beams in Selection B, all these clashes will be grouped.

![BySelectionA]({{ "/assets/2016/11/BySelectionA.jpg" | absolute_url }})

  * Group by Selection B: This rule will group all clashes belonging to an element of the selection B, and name the group after this element.

![BySelectionB]({{ "/assets/2016/11/BySelectionB.jpg" | absolute_url }})

  * Group by Assigned To, Approved By, and Status: These three rules will use various properties of the clash to group them. As an example, you can use this rule to group all clashes assigned to you.

You can also group with two rules, the first one will rename the clash group created by the second one. This enables various possibilities, like having clashes grouped by a given selection and renamed according to the one assigned to.

Group Clashes can have difficulties in managing clash reports with more than 10 000 clashes. Be smart when you set up your clash tests, and everything will be fine.

Group Clashes is now out of beta, and you will have to pay $10 to download it on the [Autodesk App Store](https://apps.autodesk.com/NAVIS/en/Detail/Index?id=7544208847822212204&appLang=en&os=Win64).

Yet, Group Clashes is also open-source. You can find the entire source code on [Github](https://github.com/simonmoreau/GroupClashes), build your own plugin, and develop your own grouping rules.