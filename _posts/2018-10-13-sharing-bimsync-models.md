---
id: 1269
title: Sharing bimsync models
date: 2018-10-13T10:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1269
permalink: /2018/10/sharing-bimsync-models
published: true
categories:
  - bimsync
image: /assets/2018/10/share.png
tags:
  - bimsync
  - IFC
  - Visualization
  - bimsync-manager
description: A new sharing feature for bimsync Manager
---
Letting non-technical users see a model used to be a pain. Web-based viewers have started to make it way easier. They now allow you to review any models without having to install some heavy software or buy the latest gaming computer.

I am myself a regular user of bimsync and enjoy this ability to let anyone see a model as long as there are members of a project.

But I also wanted something easier to let people see a specific version of a model without even having to be invited to a bimsync project. Think of it as the "Share" button of Dropbox or OneDrive.

Making use of the bimsync API, I created a new feature in [bimsync Manager](https://bimsyncmanager.firebaseapp.com/home) to let you share your bimsync models with a simple link.

Once logged to bimsync Manager with your bimsync account, click on the "Share" button of your project. Select one or more models to share, their version and the associated 2D view.

![Sharing Model]({{ "/assets/2018/10/share.gif" | absolute_url }})

Then click on "Publish" to get a public link. This link allows you to see the selected version of these models without having to be invited to the corresponding bimsync project. You can view the result [here](https://bimsyncmanager.firebaseapp.com/share?code=c4fc2bf0-f46e-4920-b772-1fb50787e35d).

In this window, you have access to most of the usual features of the bimsync viewer, like sectioning, showing or hiding models and spaces.

![Sharing Model]({{ "/assets/2018/10/view.gif" | absolute_url }})

A word of warning here, the sharing link is public. If you use it to share you models, everybody with the link will be able to see them, so be cautious before sharing something that might be confidential.

You can also use the second link, an iFrame, to embed the viewer in your website, like in this example below:

<iframe width="680" height="510" src="https://bimsyncmanager.firebaseapp.com/share?code=c4fc2bf0-f46e-4920-b772-1fb50787e35d" frameborder="0" allowFullScreen="true"></iframe>

Along with this new feature, I updated the link between [Power BI and bimsync](https://www.bim42.com/2018/02/data-visualization-for-bimsync/).
If you want to use it, you must now use the updated dashboards, available on the [Help](https://bimsyncmanager.firebaseapp.com/documentation) page. These new dashboards now include an access to your bimsync issues.

I had to do some modification to the inner working of bimsync manager. You might have to log out and login in again if you were already using bimsync Manager.

The entire solution is still open source, written with Angular. You can find the code on the [bimsyncManager Github repository](https://github.com/simonmoreau/bimsyncManager).