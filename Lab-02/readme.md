# Create ADLS Storage Account

Welcome to this lab where we will create the Azure data storage account.

Here are the steps to follow for creating Azure Data Lake Storage (ADLS) account in Azure Portal:

* On the Azure portal home page, click on "Create a resource" icon to create a new resource

<img src="images/05.jpg">

* In the search box for Marketplace, type in "Storage Account" and press Enter

<img src="images/06.jpg">

* Click on "Storage Account" and then click on "Create" button

<img src="images/07.jpg">

* In the Project Details section, select your Azure subscription 
* Provide a name for Resource Group
* In the instance details section, provide a storage account name 
* Select your region

<img src="images/10.jpg">

* In the instance details section, select Redundancy for your storage account
* Click on "Next : Advanced" button

<img src="images/20.jpg">

* In the Data Lake Storage Gen2 section in the Advanced tab, check the check box for "Enable Hierarchical Namespace"
* Click on "Next: Networking" button

<img src="images/30.jpg">


* Keep the default sesstings in Networking, Data Protection, Encyption and Tags tabs
* On the Review tab, review your settings and click "Create" button

<img src="images/40.jpg">

* Wait for a few seconds for the deployment to complete. Ensure that the deployment succeded and the resource was created. 
* Click on the "Go to resource" button

<img src="images/50.jpg">

* Click on Data Lake Storage

<img src="images/60.jpg">

* Let's create the container now
* Click on container and provide "Input" as name for this container

<img src="images/70.jpg">

* Inside the container "Input", let us now create a folder by clikcing on "Add a Directory" button and providing "Landing" as the name
* Click on "Save" button

<img src="images/80.jpg">

* "Landing" folder is the place where we want to see all our files get dropped from AWS.

<img src="images/90.jpg">

That's the end of this lab. 

[Back](../Lab-01/readme.md)  [Next](../Lab-03/readme.md)