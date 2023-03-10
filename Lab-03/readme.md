# Create Azure Data Factory account for Data Pipelines

Welcome to this lab where we will create Azure Data Factory account for Data Pipelines. 

As per our architecture diagram, we have already created an AWS bucket and stored our sample file there. Now, we want to move the IoT data from AWS bucket to the Azure cloud. In order to move this data, we need an ADF account. Here are the steps to follow for creating Azure Data Factory account for Data Pipelines in Azure Portal:

* Go to the Azure portal home page

<img src="images/10.jpg">

* In the search box, type "Data Factories"

<img src="images/20.jpg">

* Click on the "Data Factories" service. This will open up the Data Factories page
* Click on "Create" link to create ADF

<img src="images/30.jpg">

* In the Project details section,select your Azure subscripion and provide a name for your ADF
* In the Instance details section, provide a name and select a region for your ADF
* Click "Next: Git Configuration" button

<img src="images/40.jpg">

* Select all default values in Git Configuration, Networking, Advanced and Tags tabs

<img src="images/50.jpg">

* Click on "create" button in "Review + create" tab

<img src="images/60.jpg">

* Ensure that the ADF is created successfully
* Click on the "Go to resource" button

<img src="images/70.jpg">

* Click on "Launch Studio" in Azure Data Factory Studio page

<img src="images/80.jpg">

That's the end of this lab. 

[Back](../Lab-02/readme.md)  [Next](../Lab-04/readme.md)