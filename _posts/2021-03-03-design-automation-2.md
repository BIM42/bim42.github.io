---
id: 1285
title: Design Automation For Revit - Part 2
date: 2021-03-03T10:00:00+00:00
author: Simon Moreau
layout: post
guid: https://www.bim42.com/?p=1285
permalink: /2021/02/design-automation-revit-2
published: true
categories:
  - Forge
image: /assets/2021/01/revit-to-ifc-logo-blue square.png
tags:
  - Automation
  - Forge
  - IFC
description: Using Design Automation For Revit to export an IFC file
---

After the [first part](https://www.bim42.com/2021/02/design-automation-revit-1) where we explore how to build an Revit addin for the Design Automation API, we can now upload and run this addin on the Forge server.

# Part 3: Create the application on Forge

After creating a new Forge App with the Data Management API and the Design Automation API, we use the Postman definitions provided [here](https://github.com/Autodesk-Forge/forge-tutorial-postman/tree/master/DA4Revit) to create our Design Automation application.

We need to create a bundle, a package containing our Revit addin to upload it on the cloud. We create the folder structure in our solution, then add the following to the post-build event in visual Studio

```bash
xcopy /Y /F "$(TargetDir)*.dll" "$(ProjectDir)IFCExport.bundle\Contents\"
xcopy /Y /F "$(ProjectDir)*.addin" "$(ProjectDir)IFCExport.bundle\Contents\"
"C:\Program Files\7-Zip\7z.exe" a -tzip "$(ProjectDir)$(OutputPath)IFCExport.zip" "$(ProjectDir)IFCExport.bundle\" -xr0!*.pdb
```

This small script will use [7-Zip](https://www.7-zip.org/) to create a zip file containing the folder structure and application files (.dll and .addin)

We then register an AppBundle on the Forge server where we upload the bundle zip file containing our Revit addin.

We now need to create an Activity. An Activity is a function definition you create on the Forge server before running it. In this Activity, we add the AppBundle created at the previous step and describe input and output files with the following JSON body:

```json
{
    "commandLine": [ "$(engine.path)\\\\revitcoreconsole.exe /i $(args[rvtFile].path) /al $(appbundles[IFCExportApp].path)" ],
    "parameters": {
      "rvtFile": {
        "zip": false,
        "ondemand": false,
        "verb": "get",
        "description": "Input Revit model",
        "required": true,
        "localName": "input.rvt"
      },
      "param": {
        "zip": false,
        "ondemand": false,
        "verb": "get",
        "description": "Json Parameter file",
        "required": true,
        "localName": "params.json"
      },
      "result": {
        "zip": false,
        "ondemand": false,
        "verb": "put",
        "description": "Results",
        "required": true,
        "localName": "IFCExport.ifc"
      }
    },
    "engine": "Autodesk.Revit+2021",
    "appbundles": [ "{{dasNickName}}.IFCExportApp+test" ],
    "description": "Export a Revit file to IFC."
}
```

This json text describe the behaviour of our activity:
* The engine used: Here, Revit 2021
* The name and description of the input files. Here, we have a Revit file named input.rvt and a json parameter file name param.json
* The name and description of the output. Here, we have an IFC file named IFCExport.ifc

We also need to create an alias, a name, for the activity, as Forge does not allow us to call an activity with its id, but only with its alias. I create the alias "test". This feature can also be used to retrieve a specific version of an activity (test, production, ...)

Now that our activity is created, our application is ready to receive the input Revit model. To upload it on the Forge server, we need a public URL pointing to our Revit file. To create such an URL, we use the Data Management API and create a bucket to store temporary our Revit model. We then get a temporary upload URL that we will pass to the Data Management API to retrieve our uploaded Revit model.

Within this storage, we also get a temporary download url that the Data Management API will use to store the result of our application, in our case the csv file containing the schedule.

We are now ready to run our application on the Forge server. We create a WorkItem (an instance of an Activity previously described) and pass it the URL of the input RVT file along with an URL to upload the exported IFC model.

After some trial and error, I end up with this response:

```json
{
    "status": "success",
    "reportUrl": "https://dasprod-store.s3.amazonaws.com/workItem/IFCExport/327ecd7e417d4146ac9fee526dadc77a/report.txt?AWSAccessKeyId=ASIATGVJZKM3MOAUUELC&Expires=1598475306&x-amz-security-token=IQoJb3JpZ2luX2VjEPP%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJGMEQCIB8CCQH%2ByhzCLGy8j%2BSnjyl5iWGHSDcBoOE13qfbvoXtAiBJ%2Fcb29l7c3%2BpofB871knrAtzCdjrSF56lyHalu84RaCreAQjb%2F%2F%2F%2F%2F%2F%2F%2F%2F%2F8BEAIaDDIyMDQ3MzE1MjMxMCIMIabmNymt9h8FvhNxKrIBitnBT9n07Kcl5GaR%2BxbVXeyFmHUm8xiJbI10zddAHM0CO5M%2FLE5SZy5wpMI44GPpZ7iD9DhLmVxfhOtaaKLXKcFHd3lj58VnKvT6bL5pfyG7NpXqWkHDZuatll5iZO6oRqZUFkhdUMebIk85Nq9%2BipticovIB%2B1zQJpEO9NWXkTojNUXdMWyJ9dA7E%2BJDMkIc4YcIF%2BlhsfiG4rjsfMawaCj%2BmeZyueHO5HIToHmll8S2zCKzpr6BTrhAbzfws2iAs2p1%2FieP%2F4GAskwreGMcx9d0IXPOkYJD%2BWV1GDtke9azMF%2Ftu%2FBP%2FVdA0lzqtIEcAVDsqp9z%2FSMTl1nyxBXA16eMRajpzY5d5dvBRTBuXEacNoOABs4wbmj46kzFlT3HT50mlnvcCmchqwqSIe0ZqsEWAhgOE8F2yS1h2%2B89%2FnD9B1qz9B6ukc9VU7d0N5ifH%2Bkh%2FQ8zRmtlLoGDSE%2Fhy8fs7ia8qLPn7%2FNNE7m4sloHX3TiMO1UFOkDdfVaG29tdwWw7%2FwtCdYaXX%2FjaVJJm3YgWoO8YgQyzWV6A%3D%3D&Signature=j4gt9S5NO1bNlR5KrGiVCwsKmLw%3D",
    "stats": {
        "timeQueued": "2020-08-26T19:52:13.8851515Z",
        "timeDownloadStarted": "2020-08-26T19:52:14.4542928Z",
        "timeInstructionsStarted": "2020-08-26T19:52:15.3584001Z",
        "timeInstructionsEnded": "2020-08-26T19:54:14.3353297Z",
        "timeUploadEnded": "2020-08-26T19:54:14.4511254Z",
        "timeFinished": "2020-08-26T19:54:14.6601308Z",
        "bytesDownloaded": 18907171,
        "bytesUploaded": 4344
    },
    "id": "327ecd7e417d4146ac9fee526dadc77a"
}
```

I then grab the download URL used to store the result, download it and get the resulting IFC conversion.

# Part 4: Final thoughts:

At first, this application seems slow. I used the ordinary architectural sample file on this experience (18 Mo), it takes 2 minutes and one second to run the entire WorkItem. The download part is actually very fast (2 second to upload the Revit model, a tenth of a second to download the resulting conversion). However, opening the model and running the app takes 1:59 on the Forge server. Running it my Surface Book 2 takes only 54 seconds.
However, subsequent runs where faster, my guess is that the server need some time to start the first time.

The Design Automation API allows to upload multiple linked files, with a default error handler that allows us to manage the annoying Revit warnings we sometime get when opening a file. However, a warning that need to delete elements to be resolved will prevent the Design Automation API from opening the file and send back an error.

Nonetheless, this open a LOT of possibilities. You can now do basically anything on a Revit file without having to open Revit on your workstation and I see a bright future for web-based applications making use of Revit files.

