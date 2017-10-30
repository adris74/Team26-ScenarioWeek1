# Team26-ScenarioWeek1
UCL Endorsed Project

Scenario week 1: LET THE HELL BEGIN:

deploying a robust web application to run on Microsoft Azure services and infrastructure. You need to design your web application, define your cloud infrastructure, and automate build, testing and deployment, using tools and scripts of one form or another. 
Azure, the aim is to learn about the basics of setting up and running a cloud service, 
Specs: 

-	Defining a cloud infrastructure consisting of multiple services and machines. 
-	How the creation of cloud infrastructure can be automated. This is often referred to as IAAS or Infrastructure as a Service, where the infrastructure needed is defined and controlled by the developer (see https://en.wikipedia.org/wiki/Cloud_computing) 
-	How the deployment of a web application can be automated. Creating a working web application to deploy onto your cloud service. 
-	Some basic testing of web applications, primarily to confirm they are working correctly. 
-	Some basic data management. 
-----------------------------------------------------------------------------------------------------------------------------

Specific Goals:

Design a web application that could act as a notebook and log book for your COMP214P project (see specification later) but can support many users and projects. Hence, scalability is a core design concern. 

Design the cloud architecture needed to support your web application. At a minimum this would include a web-server, database server, and elements such as an Azure Virtual Network with a gateway machine in order to not expose the servers directly to the internet. See https://docs.microsoft.com/en-us/azure/index#pivot=get-started to get started. 

Aim to automate the creation and activation of your cloud infrastructure as much as you can, using Microsoft PowerShell (https://docs.microsoft.com/en- us/powershell/#pivot=main&panel=getstarted, https://docs.microsoft.com/en-us/powershell/azure/overview? view=azurermps-4.4.1). Note that Azure Cloud Shell allows you to use PowerShell from within the Azure portal (https://docs.microsoft.com/en- us/azure/cloud-shell/overview). 

You should use git version control to manage your source code and other assets. Git must be used properly with all members of the team contributing to the same repository with regular commits, branches (e.g., for experimental work), and proper commit messages. Preferably use GitHub for your shared repository. If you haven't already done so sign up for the GitHub Student Developer Pack (https://education.github.com/pack). 

The web application should auto restart if it crashes or the server reboots. One way this is done is to have a 'keep alive' service that pings the application or makes an http request to see if there is a response. If not then an application restart is triggered. 

Testing. As well as 'keep alive', provide some basic testing to confirm that the web application has been deployed and is running properly. For example, is it possible to login and search for a notebook entry. Some web application frameworks have built-in unit and integration/acceptance testing tools, otherwise look at using Selenium (http://www.seleniumhq.org), which provides an easy to use approach to testing web applications. 

It is common practice to have multiple instances of your cloud infrastructure, with one instance for production and others for testing (see later section). It should be possible to setup and deploy to these different instances. 

Database backup and restore to protect your data. Data should be backed up on a regular basis, and it should be possible to restore a selected backup to a new instance of your cloud infrastructure or to a running version. Azure does provide data backup services or you can provide your own. It is important to confirm that restoring data from a backup does actually work! The back up should occur frequently to ensure that in the event of the loss of the production server (e.g., everything wiped), then as little data is lost as possible. The actual data loss will depend on when the last backup took place, and you need to balance backing up with storage space. Also how do you backup the database when the application is running, as data might not be in a consistent state at the moment of the backup? This means that backup may not be as simple as copying the database, maybe you need to read and transfer data to another database on another machine? 

Consider the use of features like content delivery network (CDN) services, caching (e.g., Redis Cache), Azure Search, elastic compute (https://azure.microsoft.com/en-gb/overview/what-is-elastic- computing/) or other services that a heavily used application might need. These are not core requirements and features like elastic compute (load balancer) can be quite heavy on credit usage. 

Docker (https://www.docker.com, https://opensource.com/resources/what-docker) is a container technology for packaging up an application and all its dependencies into a single unit that can then be distributed and run on a virtual machine. It provides a good alternative way of managing and deploying a web application than doing everything via scripts, and Azure provides Docker support. As an additional challenge you could aim to deploy your web application via Docker. There is a learning curve to understand Docker, so take that into account if you decide to use it. 


----------------------------------------------------------------------------------------------------------------------------
Web Application Specification :

The purpose of developing a web application is to provide an application to deploy, not to develop a large or complex application in its own right. The specification is as follows: 
The application should provide a straightforward online notebook or logbook, that would be useful for keeping information about development projects such as the one you are working on in COMP214P. Hence, think of yourself as the client for this application. 

A user can create an account and then create, edit, display and delete notebook or logbook entries. Decide what data is needed to represent a user account (e.g., email address and password). 
Entries can be tagged and organised into categories. 

An entry can be any text, and can include URLs, images, embedded video if you decide to support those features. 
All the date, including user account information, is stored in a database. 

A user has a username/email address and password, as is very familiar on many websites. 

You can add to this if you want, but bear in mind that the purpose is not to create an elaborate application, it is to create an application with a database that can be deployed onto Azure. 

It is up to you which web frameworks you use, but they have to work in the Azure environment. Examples include: 
Django (https://www.djangoproject.com) this is implemented in Python language. 

Rails (http://rubyonrails.org) this is implemented in the Ruby language. Grails (https://grails.org) this is implemented in the Groovy language. and many others you may be familiar with already. 
