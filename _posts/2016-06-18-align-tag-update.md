---
id: 1055
title: Align Tag Update
date: 2016-06-18T09:14:45+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1055
permalink: /2016/06/align-tag-update/
categories:
  - Revit
image: /assets/2016/06/icons1.jpg
tags:
  - .NET
  - Documentation
  - Revit
  - Software
  - align
---
It is this time of the year again, and I have finally take the time to update Align on the App Store for the new version of Revit.

However, there is more in this than a simple version update, and this new release is packed with improvement, both small and large.

The main change reside in the alignment method. In the previous version of Align Tag, I was using the center point of a given tag as a reference to align tag (either left or right). To improve on the alignment of tags of various sizes, I now use the bounding box of the tag.

![AlignSolution]({{ "/assets/2016/06/AlignSolution.jpg" | absolute_url }})

Tags will now properly align themselves along their right or left side, regardless of their size or origin point.

![Align]({{ "/assets/2016/06/Align.jpg" | absolute_url }})

However, if you want something similar to the older version, you can use the new Align Center and Align Midlle commands, which will use the center of the tag as a reference.

This new alignment method is more in line with what can be found on solutions like PowerPoint, or Adobe Illustrator, and will allows you to neatly arrange your tag whatever their size or origin point.

Another important improvement is the long awaited support for Text. You can now align Text along with Tag, using the same command.

While I was at it, I also add support for Keynote tag, Room Tag and Space Tag, basically every tag. The Area Tag is still missing, but can be expected for the next version.

However, this support came at a cost, and I have to drop the support for Revit 2015 and prior. So, if you are still using this version, you will have to keep the old Align plugin.

There is also a handful of small UI improvement that I hope will help you.

Aligned tags are now kept selected after running the command so you can align them in another direction right away.

Your Align commands are also one click closer to you! The interface have been artfully arranged in a new tab to keep every icon directly accessible in the ribbon.

![icons1]({{ "/assets/2016/06/icons1.jpg" | absolute_url }})

Under the hood, I have rewrote a large part of the code to support more types of annotation elements, and I hope to be able to use this new framework for more complex manipulations, including in the Arrange Tags function.

Of course, Align Tag is still open source, the entire code can be found on [Bitbucket](https://bitbucket.org/simonmoreau/align-tag).

This plug-in is already available on the [Autodesk App Store](https://apps.autodesk.com/RVT/en/Detail/Index?id=2903508825431715905&appLang=en&os=Win32_64). If you like it, don't hesitate to write a nice comment or add a few stars, it always means so much to me!