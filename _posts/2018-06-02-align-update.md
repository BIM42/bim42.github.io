---
id: 1265
title: Align Update
date: 2018-06-02T08:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1265
permalink: /2018/05/align-update
published: true
categories:
  - Revit
image: /assets/2018/06/UntagleTags.gif
tags:
  - .NET
  - BIM Manager
  - Revit
  - align
description: The yearly update of Align for Revit
---

I have finally find the time to update Align, my plugin for aligning elements, tags and text in Revit.

The app now supports Revit version from 2016 to 2019 and it is available on the [Autodesk App Store](https://apps.autodesk.com/RVT/en/Detail/Index?id=2903508825431715905&appLang=en&os=Win32_64).

The main update this year is the Untangle function. This function comes with two new buttons, "Untangle Vertically" and "Untangle Horizontally".

![The new interface]({{ "/assets/2018/06/Interface.jpg" | absolute_url }})

You can now select a few randomly placed tags, click on Untangle and the tags will sort themselves nicely:

![Untangle Tags]({{ "/assets/2018/06/UntagleTags.gif" | absolute_url }})

As you can see, the tags will move vertically (or horizontally) so they don't overlap, while keeping themselves as close as possible. They will also be sorted so the leaders won't cross.

If you are using text annotation, this function will also work these texts, with or without leaders:

![Untangle Texts]({{ "/assets/2018/06/UntangleTexts.gif" | absolute_url }})

It also works with every Revit elements. If you have a bunch of overlapping element, like furniture for example, select them and hit "Untangle" to see them sort themselves:

![Untangle Chairs]({{ "/assets/2018/06/UntangleChairs.gif" | absolute_url }})

I also made a few modifications to the code source repository. I have migrated the repository to Github and I won't be using Bitbucket anymore. You can now find the source code here: [Align-Tag](https://github.com/simonmoreau/align-tag)

I also add a proper Readme explaining what this application is about and how you can contribute to it. I hope this will encourage anyone to propose Pull Requests, point out issues or simply ask for new features.

The source code is now licensed under the MIT licence. I am far from a licence expert, so I take the word from [ChooseALicense](https://choosealicense.com/):

> "The MIT License is a permissive license that is short and to the point. It lets people do anything they want with your code as long as they provide attribution back to you and don’t hold you liable."

As usual, feel free to use this code in your own application.

I must give my deepest thanks to all of you who have contributed to this application by your code, remarks and sample models. Don't hesitate to keep asking me new features!