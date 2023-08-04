---
id: 1010
title: Using Dynamo for MEP Design – Part 2
date: 2016-04-26T07:37:48+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1010
permalink: /2016/04/using-dynamo-for-mep-design-part-2/
categories:
  - Dynamo
image: /assets/2016/04/figure7.jpg
tags:
  - Autodesk
  - Automation
  - Dynamo
  - MEP
  - Revit
---
_This is the second part of my article, originally published in the official magazine of Autodesk User Group International, [AUGIWorld](https://www.augi.com/augiworld)._

## Link between terminals and the main duct.

To fully exploit Duct sizing capabilities in Revit, we generally need a fully connected network between the mechanical equipment and Air Terminals. But drawing every duct for the entire networks from source to terminal can be time consuming and not relevant in the early phase of a project, when architectural layout is subject to major changes.

A possibility is to use Dynamo to virtually link every terminal to a placeholder family that will collect and sum Airflows in a given area and send the sum to a placeholder family used to perform duct sizing calculations on the main branch.

![figure7]({{ "/assets/2016/04/figure7.jpg" | absolute_url }})

Revit provide us the Connect the main duct to "M_Rectangular Duct Connector - Supply Air - Air Terminal". This is a generic terminal that will simulate the rest of the terminals. We connect this generic terminal to our main branch, and use it to simulate the rest of the duct networks.

The following Dynamo definition sums airflows of the selected Air Terminal and pass the value in the Airflow parameter of the placeholder family. This placeholder family now simulate the airflow of all selected air terminals. Since this family is connected to the main duct networks, we can now perform duct sizing for the main branch, without having to model the entire duct layout.

![figure8]({{ "/assets/2016/04/figure8.jpg" | absolute_url }})

A word of warning anyway, since this placeholder family is integrated into the system, flow sum for the duct system is multiplied by two, since Revit count both the airflow of every air terminal and the airflow coming from the placeholder family.

[Dynamo File](https://drive.google.com/file/d/0B_fvbfIWQ5JJdHBST0ZHc05ZelU/view?usp=sharing&resourcekey=0-kT7kbHKikDru4GrOn8n9iw)

## From Specified Airflow to actual terminal Flow

Another example of the power of Dynamo come when linking Air terminal to their enclosing MEP Space. In this example, we will see how to retrieve the required airflow in a given MEP Space, and distribute this value on every air terminal enclosed in this space.

We start by finding all MEP Space, and retrieving their "Specified Supply Airflow". We also get all Air terminals, and use the Space.IsInSpace node to find if a given terminal is in the space. We make sure to set up the lacing of this node to "Cross Product" in order to test every Air Terminal with every MEP Space. This give us multiple lists of true or false indicating whether a given Air Terminal is in the space. With the usual combination of List.AllIndiceOf and GetItemAtIndex, we find our air terminals grouped by their enclosing space. We count the number of these terminals in each group, and use this count and a division to get the specified airflow on each terminal. The List.OfRepetedItem give us an instance of this specified airflow by terminal. We finally apply these value to these terminals with the Element.SetParameterByValue.

![figure9]({{ "/assets/2016/04/figure9.jpg" | absolute_url }})

As we update the Specified Airflow of each MEP Spaces, this value will be divided by the number of terminal in the space, and applied to the said terminals.

![figure10]({{ "/assets/2016/04/figure10.jpg" | absolute_url }})

[Dynamo File](https://drive.google.com/file/d/0B_fvbfIWQ5JJVDY3WFdxSTJGcVk/view?usp=sharing&resourcekey=0-awprLlRa_1N1xKhtFQYQdg)

## Terminal Max Flow

Another application of Dynamo is the real-time checking for max values in a given terminal equipment. In this example, we will check whether the airflow of a given terminal is below is max value, and highlight in red when the airflow is above the max value. In some way, this is similar to the conditional formatting function in Excel, except we are doing it directly into Revit.

We start by finding all air terminal unit in Revit with the "All Elements Of Category" node. Using the GetParameterValueByName, we get the Airflow on each of these air terminal. Since the Maximum Airflow is a type parameter, we use the FamilyInstance.Type node to retrieve the family type, then use again the GetParameterValueByName to find the "Max Flow".

We can now compare this two values, and use the List.FilterByBooleanMask to find all terminals where Airflow is above the Max Airflow.

![figure11]({{ "/assets/2016/04/figure11.jpg" | absolute_url }})

The last step is to override the color of these terminals to override by color to highlight the results.

![figure12]({{ "/assets/2016/04/figure12.jpg" | absolute_url }})

This fairly simple example showcase the possibilities of Dynamo combined with the proper Revit objects library.

[Dynamo File](https://drive.google.com/file/d/0B_fvbfIWQ5JJaHRQbWVKZ1VBZEU/view?usp=sharing&resourcekey=0-joWDIMakld7Cc525dNb8OA)

## Conclusion

Through these five examples, we see how to use Dynamo to enhance your calculation powers in Revit. It is clear by now that Revit is far more than a modeling tool, and once combined with Dynamo, it opens a lot possibilities for mechanical engineers.

Finally, I want to give my deepest thanks to [Andrew Duncan](http://thoughts.arup.com/post/userposts/282), from Arup, for its great Autodesk university courses, where I get most of my inspiration for these examples.