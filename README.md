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

Inside it, you will have your App Service and App Service Plan.

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

Click 'Review & Create' at the bottom, followed by 'create'. This will kick of the provision of your Azure SQL Server and DB.

REMEMBER - You do not have access to a virtual machine with this service.

### Deploy Azure Storage Account

4. Next up, is going to be a storage account for backups, this can also be used for other content such as diagnostics should we wish. For the purpose of this lab, we will work with just backups.

Though if you want to go and point your web app diagnostic logs to it,feel free to go work it out! :)

Select 'Create a resource' and search for 'Storage Account', select Create & fill in the panes as below.

NOTE- storage account names must be lowercase, no spaces or special characters. Also, it must be less that 25 characters.

![alt text](/Images/2019-10.png)

![alt text](/Images/2019-11.png)

![alt text](/Images/2019-12.png)

Once the Storage account deployment has completed, you should see the following resources within your Resource Group.

![alt text](/Images/2019-13.png)

### Setting up App Insights

5. Now that we have all the resources we need, we are going to start some basic configuration.

First, lets hook up Application Insights to our web app. Navigate to your App Service within Azure. On the left hand pane, you should see Application Insights, the following message will appear.

![alt text](/Images/2019-14.png)

Click 'Turn on Site Extension' & then fill out the pane as below. 

![alt text](/Images/2019-15.png)

This will now go and install the Application Insights Site extension within your web app. Telemetry will soon start to flow. We will come back to this shortly.

### Adding Application Settings

6. Now, we will want to hook up the Azure SQL Database we provisioned to our App Service. We do this by providing the App Service the connection string to our Azure SQL database & server.

Go to your Azure SQL Database, not the server. On the left pane you will see Connection Strings, copy the 'ADO.NET' connection string and update it with the username and password you provided at creation and save to your clipboard.

![alt text](/Images/2019-16.png)

Now, navigate back to your App Service and on the left pane you will see Application Settings. Select it and scroll down to Connection Strings. Click '+ Add new connection string',name it 'db-connectionstring' and paste the value into the require field.

Click 'Save up the top'.

![alt text](/Images/2019-17.png)


NOTE-This database is blank and the web app wont leverage it, but this is the manual process you would have to go through when setting up an App Service and Azure SQL DB in prep for a code release when ready.

### Setting up Web App Backups

7. Next, we will setup a routine backup of our App Service. Browse to your App Service and in the left pane, select 'Backups'.

Click 'Configure', you will now be prompted to specify the following:

-- Storage Account
    -- Container (Create one called Backup)
-- Set a schedule
-- Retention Period
-- Optional Database backup (dont select for this lab)

![alt text](/Images/2019-18.png)

Once configured, give it a few minutes before clicking 'Backup', if one is already in progress, the task will fail.

Kick off a backup and go check the storage account for the backup data once the job has finished.

![alt text](/Images/2019-19.png)

### Hit the site and watch live telemetry.

8. Finally for this part of the lab, we are going to browse to the site and watch some live telemetry as we do. Navigate to your App Service in Azure and make sure you are on the overview pane.

Click 'browse' and Azure should open your site into a new tab.

![alt text](/Images/2019-20.png)

Split off the web site tab from your Azure Portal tab and run them side by side. In Azure, on the App Service, click 'Application Insights', then 'view application insights'.

![alt text](/Images/2019-21.png)

From here, click 'Live Metric Stream' - with the two windows open side by side, browse around your site, click on page links. You should see live metrics coming through on the other window.

This is great to give you a live feed of performance when debugging issues with performance.

![alt text](/Images/2019-22.png)

### Well Done!!!

So if you have got this far, you haev successfully gotten infrastructure setup similar to what we covered earlier in session based on 'Web & SQL'. This deployment will now be ready for you or your development team to go a deploy some code to and populate your new database.

You have backups, monitoring and a basic understanding of how it all got put together. You should have found this pretty quick, quicker that building VM's from scratch atleast. Now imagine if you had stamp this environment out 20 time, that would take a while.

Good News, Daniel is going to cover off building this lab out in ARM with you after lunch. 

Good luck and thanks for following.

## Additional Content & Steps

If you want, try and work out some of the following:

-- Deleting your web app and restoring from backup
-- Enable GEO replication on your Azure SQL Database
-- Place a traffic manager in front of your web app and browse to it.

Some links to help you out are below:



