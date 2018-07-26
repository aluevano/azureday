# Hands On Exercises
This page is collection of hands on exercises which are run through during *Azure In A Day*, note with the exception of exercise 5, there no detailed step-by-steps guides provided as the exercises are generally run interactively with a presenter 

### Table Of Contents
- [Hands On 1 - Getting Started With Azure](#hands-on-1---getting-started-with-azure)
- [Hands On 2 - Deploying & Using A Virtual Machine](#hands-on-2---deploying--using-a-virtual-machine)
- [Hands On 3 - Custom Vision Cognitive Service](#hands-on-3---custom-vision-cognitive-service)
- [Hands On 4 - Using the Cloud Shell & Command Line](#hands-on-4---using-the-cloud-shell--command-line)
- [Hands On 5 - Building A Complete App in Azure](#hands-on-5---building-a-complete-app-in-azure)

# Hands On 1 - Getting Started With Azure

## Overview
- Activate your Azure Pass
- Access your new Azure Subscription
- Use the Azure Portal
- Create a Dashboard View
- Create a Azure Resource Group
- Explore the Azure Marketplace

## Resources You Will Need

Activate the Azure Pass code you have been given using the step by step guide below.  

>**Note.** The guide is provided as a PDF, and you will need to close your browser during the activation process. It is worth making a note of the URL to come back here, which is **[aka.ms/azure-day](http://aka.ms/azure-day)** or bookmark this page as, you will need to return to this page for the rest of the exercise steps

<a href="https://raw.githubusercontent.com/benc-uk/azureday/master/azurepass-guide.pdf" class="btn-blue">Activate an Azure Pass</a> 

When you have activated your Azure subscription, access the portal at **portal<span></span>.azure.com**  
<a href="https://portal.azure.com" class="btn-blue" target="_blank">Azure Portal</a>

---

# Hands On 2 - Deploying & Using A Virtual Machine

## Overview
- Use the Azure Portal
- Browse marketplace
- Deploy a 'Data Science Virtual Machine'
- Look at VM size options
- Access your new VM
- Try out the Data Science Virtual Machine features
  - Start Jupyter Notebook & experiment
- Configure VM for auto-shutdown
- Shutdown VM

## Resources You Will Need

Everything in this exercise will be done via the portal  
<a href="https://portal.azure.com" class="btn-blue" target="_blank">Azure Portal</a>

Azure Docs - *Introduction to Azure Data Science Virtual Machine*  
<a href="https://docs.microsoft.com/en-us/azure/machine-learning/data-science-virtual-machine/overview" class="btn-blue" target="_blank">Data Science Virtual Machine</a>

If you are using a Mac, install the Remote Desktop Client here:  
<a href="https://itunes.apple.com/gb/app/microsoft-remote-desktop-10/id1295203466" class="btn-blue" target="_blank">Microsoft Remote Desktop 10.0</a>

---

# Hands On 3 - Custom Vision Cognitive Service

## Overview
- Download a sample set of images
- Access the Custom Vision Service
- Create a new project
- Upload initial images to project & tag them
- Train the model & test
- Upload extra images to project & tag them
- Re-train model & re-test

## Resources You Will Need

The Custom Vision service has it's own web portal at **customvision<span></span>.ai**  
<a href="https://customvision.ai/" class="btn-blue" target="_blank">Custom Vision Portal</a>

The sample images we will use and test with can be downloaded from this link:  
<a href="custom-vision-images.zip" class="btn-green">Sample Images</a>

---

# Hands On 4 - Using the Cloud Shell & Command Line

## Overview
- Access the Azure Cloud Shell (bash)
- Try out and explore the Azure CLI (Command Line Interface)
- Create a resource group using the CLI
- Create a container (Custom Vision Python App)
- Test accessing container with public IP
- Delete container

## Resources You Will Need

The Azure Cloud Shell can be accessed from the Azure portal or directly at **shell.azure.com**  
<a href="https://shell.azure.com/" class="btn-blue" target="_blank">Azure Cloud Shell</a>

There are several quite long commands to be run, they can be copy & pasted from here

Create resource group
```
az group create -n containers -l northeurope
```

Create Custom Vision container
```
az container create -n custvision -g containers --image bencuk/cust-vision-goats --ip-address public
```


> **Optional:** If you want to use the Azure CLI on your local machine, download and install it here  
<a href="https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest" class="btn-blue" target="_blank">Azure CLI</a>

---

# Hands On 5 - Building A Complete App in Azure
In this exercise you will deploy a serverless application which uses Azure Cognitive Services to analyze photos gathered from twitter. An Azure Logic App drives the process and carries out most of the tasks. 

The Logic App flow is:
- Calls the Twitter API and searches for tweets containing a certain hashtag
- Calls the Azure cognitive service API for each photo and gets the result which is a description of the contents of the photo
- Stores the result in Azure Cosmos DB

The Azure cognitive service uses a pre-trained computer vision model to return results describing the image as a JSON object. Cosmos DB is a No-SQL database, which the Logic App uses to store the results as JSON documents, one for each photo result.

The final part of the application is a simple web app, written in Node.js. This web app is hosted in Azure as an Web App Service, it connects to Cosmos DB and displays the photo analysis results as a simple web page.

### Solution Architecture
![arch](http://code.benco.io/serverless-cosmos-lab/arch.png)

## Overview
- Create a new resource group
- Create a Computer Vision API account
- Create a new Cosmos DB account
- Create a database and collection in Cosmos DB
- Create a Logic App
- Connect Logic App to Twitter
- Connect Logic App to Cosmos DB
- Test and verify
- Create a new Web App
- Connect Web App to Cosmos DB
- View results :)

## Resources You Will Need

When configuring the Web App deployment from external git, the URL you will need to use is:
```
https://github.com/benc-uk/serverless-cosmos-lab
```

This exercise has a complete full step-by-step guide, with videos walking you through the process end to end  
<a href="http://code.benco.io/serverless-cosmos-lab/" class="btn-blue" target="_blank">Cognitive Services Lab</a>

