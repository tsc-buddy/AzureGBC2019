# AzureGBC2019
Auckland Azure GBC 2019 Content

TWelcome! This repo has a bunch of content that will be getting covered in the Global Azure Bootcamp Auckland event for 2019. Here you can find the steps which we shall go through in the lab, the slide desk and some links to additional quick starts hosted on technet.

Lets get amongst it!!

## Content

### What will you need for the lab?
1. A Microsoft Azure Account. You can sign up for a free trial [here](https://azure.microsoft.com/en-us/free/). - - If you dont have one already!
2. A computer running a Desktop OS such as WIndows, Mac or Linux with a browser such as Edge, Chrome or Firefox


### What you will learn

At the end of this session you should hopefully have a fresh setup of an environment based on the 'Web and SQL' model discussed in the workshop, with the addition to some Azure SQL Replication. The second part of the lab will guide you through the 'Static Site' scenario we covered on in the workshop, where you will deploy a basic JavaScript website inside an Azure Storage account.

These labs are short & designed to give you an insight into some of the steps required for setting up PaaS infrastructure ready for a code release. One of the key take aways here should be to note how many manual steps you go through, so that when you complete the afternoon session, you get an appreciation for automating the majority of this process with ARM.

## Lab Steps

### Deploying an App Service

First up, once you are logged into Azure, lets create our first resource for this lab. Web App.

1. Select 'Create a resource' and search for 'ASP.NET Starter Web App', select Create & fill in the panes as below.

NOTE -  Give your App Name, Resource Group (not compulsoru) & App Service Plan a name unique to you. If you try to use a name already used on a web app, it will say you cant use it.

NOTE - Set Application Insights to disabled.

![alt text](/Images/2019-1.png)

![alt text](/Images/2019-2.png)

![alt text](/Images/2019-3.png)

Click 'Create', Once validation has completed, your resource deployment will begin.

### Check your Web app deployment

2. On the left toolbar pane, select "Resource Groups', this will present a list of available resource groups in your subscription, you should see the one you made as part of your Web App Deployment.

![alt text](/Images/2019-4.png)

![alt text](/Images/2019-5.png)

### Deploying Azure SQL

3. Next up, we will deploy an Azure SQL DB. Select 'Create a resource' and search for 'SQL Database', select Create & fill in the panes as below.

NOTE - your database can be named what ever you like, however, your Azure SQL Server needs to be unique. 

NOTE - Select the same Resource group you already made for the web app.

![alt text](/Images/2019-5.png)

![alt text](/Images/2019-6.png)

![alt text](/Images/2019-7.png)

![alt text](/Images/2019-8.png)

![alt text](/Images/2019-9.png)

### Deploy Azure Storage Account

### Setting up App Insights

### Adding Application Settings

### Setting up Web App Backups

### Browse Kudu

### 

###