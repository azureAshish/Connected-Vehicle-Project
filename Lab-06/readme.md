# Create Azure Function with Blob Storage Trigger

Welcome to this lab where we will create Azure Function with Blob Storage Trigger.

Now that the data is pulled into our landing folder in ADLS by virtue or running ADF pipkline on a daily basis, we have our data available to be processed for the next stage.

In this lab, we will create an Azure function, that will get triggered when a file is uploaded into Landing folder in ADLS. This Azure function will validate the JSON, checking if JSON is valid or not. Azure function will then move this JSON file to either Rejected or Staging folder.

So let's move to the Azure portal and create our Azure function.


* In Azure Portal, search for Function App. Click on Function App in search results

<img src="images/10.jpg">

* Click on "Create Function App" button to create a new function app
* Select you subscription 
* Select the existing Resource group that we created earlier
* Provide a unique function name
* For Publishing option, keep the default radio button code as selected
* For runtime stack, use Node.js
* For Version, select the most recent version available
* Select your appropriate region for this function app

<img src="images/20.jpg">

* For Operating system, select Windows
* For Plan type, select Serverless
* Click on "Review + Create" button

<img src="images/30.jpg">

* Click on Create button to create the function app

<img src="images/40.jpg">

* When the deployment is complete, click on "Go To Resource" button

<img src="images/50.jpg">

* Click on Functions in left hand menu, then click Create to create a new function.

<img src="images/60.jpg">

* Select Azure Blob storage trigger from the list of Templates and click Create button

<img src="images/70.jpg">

* Click on new and select a new storage account connection
* Click on Create button

<img src="images/80.jpg">

* On the integration page, click on Azure Blob STorage Trigger

<img src="images/90.jpg">

* On the Edit Trigger pane, provide input/landing as the path because in our ADLS, we have a Landing folder inside input container where files will be dropped

Click on Save.

<img src="images/100.jpg">

* We will create two outputs - validated JSON file will be moved to staging folder and invalid JSON file will be moved to rejected folder
* Click on Outputs in Integration page
* Click on Add output
* For Blob parameter name, provide stagingFolder
* For Path, provide input/staging/{rand-guid}.json
* Click on OK button.

<img src="images/110.jpg">

* Let's create the other outputs now
* Click on Outputs in Integration page
* Click on Add output
* For Blob parameter name, provide rejectedFolder
* For Path, provide input/rejected/{rand-guid}.json
* Click on OK button

<img src="images/120.jpg">

* This is the code that can be found in the resources folder of this lab
* We are using JSON.Parse() method to check if the file content is valid JSON
* Depending on the result of validation, we move the file to either staging or rejected folder

<img src="images/130.jpg">

* Click on "Code + Test" in the left hand navigation 

* Copy paste the code from resource folder and overwrite it on index.js
* Click on Save

<img src="images/140.jpg">

* Let us upload a file into our blob storage
* A sample upload file can be found in Resource folder for this lab
* Ensure that you upload the file in the correct date folder when testing this function

<img src="images/150.jpg">

* Click on Test/Run to run Azure function

<img src="images/160.jpg">

* For the input parameter, provide the path to the uploaded file
* Click on Run button

<img src="images/170.jpg">

* Check the logs. You will see message that file was copied to Staging Folder successfully

<img src="images/180.jpg">

* Go to ADLS blob storage and check if the input file appears in staging folder

That's the end of this lab. 

[Back](../Lab-05/readme.md)  [Next](../Lab-07/readme.md)