---
id: 1272
title: Create folders in your bimsync project
date: 2019-03-30T10:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1272
permalink: /2019/03/create-folders-in-bimsync
published: true
categories:
  - bimsync
image: /assets/2019/03/createFolders.png
tags:
  - bimsync
  - bimsync-manager
description: An update to bimsyncManager to create folders in your bimsync project
---
Thank to [the update of Documents](https://catenda.no/blog/new-feature-release-for-documents-in-bimsync) in bimsync, I was able to update [bimsyncManager](https://bimsyncmanager.firebaseapp.com).

It now has the ability to create folders in an existing project, based on a text file. This text file contains all the information required to create you folder structure in bimsync Document Library.

So if you have an existing project with already some folder, you can use bimsyncManager to create your own folders structure in your bimsync project.

Click on "Create folders and boards" button, paste in your configuration file and select "Create" :

![Create folders in bimsync]({{ "/assets/2019/03/createFolders.gif" | absolute_url }})

You can also use this new feature when creating a new bimsync project.

A word of warning, if you try to create folders with the same name than the existing one, the creation will fail.

Your configuration file must follow the following structure, with folders defined between "{ }" by a name and an optional list of sub folders, themselves defined between "{ }" :

```json
[{
    "folders": [{
            "name": "Design Phase",
            "folders": [{
                    "name": "Architect"
                },
                {
                    "name": "Structure"
                },
                {
                    "name": "MEP"
                }
            ]
        },
        {
            "name": "Detailing"
        }
    ]
}]
```

The complete documentation can be found on the [help page](https://bimsyncmanager.firebaseapp.com/documentation) of bimsyncManager.

You can also use this configuration files to add new members to your project, create issue boards with specific status and types and create models.

I take the opportunity to also add a few corrections to make bimsyncManger more stable and easy to use. Don't hesitate to give me your feedback!