---
id: 834
title: Grouping clash results
date: 2015-05-02T14:25:41+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=834
permalink: /2015/05/grouping-clash-results/
categories:
  - Coordination
image: /assets/2015/05/groupByGrid.jpg
tags:
  - .NET
  - Autodesk
  - Automation
  - Coordination
  - Navisworks
  - group-clashes
---
In any given building model, there is a number of issues to be addressed. A large part of these issues are what we call "hard clashes", when a building component physically penetrate the space occupied by another building component. In these case, two or more building elements compete for the same volume.

Finding these clashes is now quite simple thanks to clash detection software that detect geometrical interferences between elements of a building model.

But after having a hard time finding these issues through coordination sections hand-drawn from plans, we now face the inverse problem and end up with too many clashes in our models. Running a simple clash detection can quickly yield thousands of clashes, making the entire process nearly useless.

Furthermore, a clash only represent a geometrical intersection between two elements, and is more a part of an issue than the issue itself. We have to group these clashes to be able to extract meaningful issues from the meaningless clashes.

Grouping these clashes is generally a manual task, and the user have to run through thousands of clashes to sort them in relevant groups.

While trying to automate this tedious task, I run across the examples provided as part of the Autodesk Navisworks Software Development Kit. These examples include a nice Clash Grouper plugin for Navisworks, enabling various method for grouping clash results.

![grouplashes]({{ "/assets/2015/05/grouplashes.jpg" | absolute_url }})

As an example, I run a clash detection between the blue Selection A and the green Selection B, and get seven clashes, shown here as red dot:

![Ungrouped]({{ "/assets/2015/05/Ungrouped.jpg" | absolute_url }})

With the Clash Grouper, I can group these clashes by grid intersection:

![groupByGrid]({{ "/assets/2015/05/groupByGrid.jpg" | absolute_url }})

I can also group them by cluster analysis, where we search for the optimum grouping solution given the expected number of groups:

![groupByCluster]({{ "/assets/2015/05/groupByCluster.jpg" | absolute_url }})

I also add my own method for grouping clash against a specific set. I use this to group all clash belonging to a single element in one of the two selection sets.

![grouplashesEdited]({{ "/assets/2015/05/grouplashesEdited.jpg" | absolute_url }})

Here, I group by element from the Selection A (blue)

![groupBySelectionA]({{ "/assets/2015/05/groupBySelectionA.jpg" | absolute_url }})

Here, I group by elements from the selection B (green)

![groupBySelectionB]({{ "/assets/2015/05/groupBySelectionB.jpg" | absolute_url }})

If elements from one set are more relevant for the end user, the final clash report is clearer for this user when clashes are grouped against this set.

This plug-in enables a lot of possibilities for sorting clash detection results in a meaningful report, and will become a full-time member of my coordination toolbox.

To install this plug-in, you can copy-paste the ClashDetective.ADSK.dll file available [here](https://bitbucket.org/simonmoreau/clashdetective/downloads) in a new ClashDetective.ADSK folder in C:\Program Files\Autodesk\Navisworks Manage 2016\Plugins. You can also see my edited version of the example code [here](https://bitbucket.org/simonmoreau/clashdetective).