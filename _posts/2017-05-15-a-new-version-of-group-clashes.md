---
id: 1177
title: A new version of Group Clashes
date: 2017-05-15T09:56:12+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1177
permalink: /2017/05/a-new-version-of-group-clashes/
categories:
  - Coordination
image: /assets/2017/05/1.jpg
tags:
  - Automation
  - Coordination
  - Navisworks
  - group-clashes
---
I just updated my Clash Grouper plugin for Navisworks.

The main purpose of this update was to solve some issue encountered by early adopters. The plugin should now be more stable. Many thanks to the users who contributed to this release with their feedback and test models.

I also add some new features to the application, that I will showcase with this example. Detecting clashes in this simple layout of ducts (Selection A, in blue) and pipes (Selection B, in red) yield 8 clashes, spread like this:

![1]({{ "/assets/2017/05/1.jpg" | absolute_url }})
An example of a clash test

# Creating subgroups

Grouping with two condition will now create a first group per the first rule. It will then divide this first group into subgroups, following the second rule.

If we group this example by Selection A (the ducts), we get the following groups, named after the item used to create the group. All clashes involving the same item from selection A are grouped together:

![2]({{ "/assets/2017/05/2.jpg" | absolute_url }})
Grouping by Selection A

If we add a new group rule, say, by grid intersection, the plugin will break these groups into subgroup, according to this new rule. Here, it will rename the existing group by adding the nearest grid intersection name, and break the group {Clash 7, Clash 8} into two, each one belonging to a different grid intersection.

![3]({{ "/assets/2017/05/3.jpg" | absolute_url }})
Grouping by Selection A and Grids

# Keep existing groups

You can now keep existing groups, so the Group Clashes will run only on the remaining clashes. This open more possibilities for complex workflows to group and sort clash results.

For example, you can group by status, explode the "Active" group and keep this "Approved" group. After running again the grouping function by level, it will only take into account the clash result, and keep the "Approved" group intact, allowing you to focus on "Active" group

Another example, if we create manually the following group in our previous clash test:

![4]({{ "/assets/2017/05/4.jpg" | absolute_url }})
An existing group

We can then run a Group by Grid intersection on the remaining clashes to create the following groups for the remaining clashes, without disturbing the existing group.

![5]({{ "/assets/2017/05/5.jpg" | absolute_url }})
Remaining clashes are grouped

# Batch grouping

You can now select multiple clash tests to apply the same grouping rules to all of them

![Batch]({{ "/assets/2017/05/Batch.gif" | absolute_url }})

Batch processing

Along these new features, a few corrections have been made. Some groups where not properly named, this is now corrected, and these groups names should now be more meaningful. Handling missing grids or levels is now better managed, and the application should be generally more stable.

As usual, you will find this new version of Group Clashes on the [Autodesk App Store](https://apps.autodesk.com/NAVIS/en/Detail/Index?id=7544208847822212204&appLang=en&os=Win64). If you want to develop your own grouping rules, you can also find the entire source code on [Github](https://github.com/simonmoreau/GroupClashes).

Happy grouping!