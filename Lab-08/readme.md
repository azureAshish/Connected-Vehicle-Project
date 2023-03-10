# Create Pipeline to move Data from ADLS to Azure SQL DB

Welcome to this lab where we will create another pipeline to move data from ADLS to Azure SQL database.

As per our architecture, only valid JSON files are stored in staging folder inside ADLS input container. We will write a new pipeline that will get triggered when a new file appears in staging folder, and moves it to SQL database.

So let's move to the Azure Data Factory studio and create our new pipeline.

* On Azure Data Factory studio, click on "Pipeline" to create a new pipeline.

<img src="images/10.jpg">

* Drag and drop "Copy data" activity onto designer surface.

<img src="images/20.jpg">

* Click on "Dataset" to create a new dataset.

<img src="images/30.jpg">

* For the new dataset, search and select "Azure Data Lake Storage Gen2" data store.
* Click on "Continue" button. 

<img src="images/40.jpg">

* Select "JSON" format
* Click on "Continue" button

<img src="images/50.jpg">

* Provide/Select the following for Dataset properties
    * Provide a valid name like "Valid_JSON_DS" for Name
    * Select the same ADLS linked service we created for our first pipeline
    * For File path, browse and select the path up until staging
    * Click OK button

<img src="images/60.jpg">

* The newly created "Valid_JSON_DS" dataset is shown in designer surface with all it's properties that we configured. Out input datasouce is now configured.

<img src="images/70.jpg">

* Let us now create a dataset for SQL database output. Click on "Dataset" to create a new dataset

<img src="images/80.jpg">

* For the new dataset, select "Azure SQL Database"
* Click on "Continue" button. 

<img src="images/90.jpg">

* Provide/Select the following for Dataset properties
    * Provide a valid name like "SQL_DB_DS" for Name
    * Click on "+ New" to create a new linked service 
    
<img src="images/100.jpg">

* Provide/Select the following for New Linked Service properties
    * Provide a valid name like "SQL_DB_DS_LS" for Name
    * For account selection method, use the "From Azure Subscription". However, I am using "Enter manually" method as my SQL table is not yet available for selection in "From Azure Subscription" method 
    * Provide the FQDN. Thi sinformation is available from overview page for Azure SQL database that we created earlier
    * Provide your database name
    * Provide your username and passowrd to connect to SQL server
    * Make sure to test your connection using the "Test Connection" link at bottom right of the page
    * Click on "Create" button

<img src="images/110.jpg">

* The "Set Properties" page is displayed with our linked service details
* We do not have any table in our SQL DB. Keep this page open

<img src="images/120.jpg">

* In another browser window, go to SQL Query Editor page for the newly create SQL database
* Copy paste the SQL from resource folder for creating a new table 
* Click on "Run" button. This will create a new table called "VehicleData1" in our SQL database.

```
create table [dbo].[VehicleData1](
    vehicleID nvarchar(100),
    latitude decimal,
    longitude decimal,
    City nvarchar(100),
    temperature int,
    speed int
)
```

<img src="images/130.jpg">

* Back in the set properties window in ADF, refresh the "Table name" dropdown and select the newly created "VehicleData1" table
* Click on "OK" button

<img src="images/140.jpg">

* For the Copy data action in pipeline, select "Valid_JSON_DS" as the Source dataset from the drop down

<img src="images/150.jpg">

* For the Copy data action in pipeline, select "SQL_DB_DS" as the Sink dataset from the drop down

<img src="images/160.jpg">

* Let us add a storage event trigger now
* Select the pipeline and click on Add Trigger > New/Edit Trigger

<img src="images/170.jpg">

* On the "Add Triggers" pane, click on dropdown > New to create a new trigger

<img src="images/180.jpg">

* Provide/Select the following for New Trigger 
    * Provide a valid name like "Storage_Trigger_For_JSON" for Name
    * Select "Storage events" for Type
    * Select your Azure Subscription
    * Select your Storage account name
    * Select "input" container name
    * For "Blob Path begins with", enter "Staging/" as only files dropped in Staging folder need to be processed
    * Check the event check box "Blob Created" 
    * Click "Continue" button

<img src="images/190.jpg">

* I already have a valod JSON file stored in Staging folder. This file will be processed as soon as we complete creating this trigger and publish the pipeline
* If there are no files in Staging folder, the pipeline will not trigger. In that case, just for testing this pipeline, you can manually drop a valid JSON file in Staging folder
* Click on "Continue" button

<img src="images/200.jpg">

* Click on "OK" button

<img src="images/210.jpg">

* Click on "Publish all" button to publish the pipeline

<img src="images/220.jpg">

* You can see that my pipeline ran immediately after publishing as my trigger got activated and started to process a valid JSON file in Staging folder
* After the pipeline execution completes, you will see the status of pipeline run change to "Succeeded"
* Click on the "Details" icon for pipeline run

<img src="images/230.jpg">

* Notice the input and output details that clearly show the number of files, data and rows read and written from source to destination

<img src="images/240.jpg">

* Go back to the Query editor for your Azure SQL databse
* Enter the follwoing SQL comand
```
select TOP(1000) * from [dbo].[VehicleData1]
```
* You can see that all JSON data from file has been copied into database table "VehicleData1"
<img src="images/250.jpg">

That's the end of this lab. 

I hope you followed along with me and completed all the labs successfully. I would encourage you to conduct an end to end testing yourself to see both the pipelines run successfully.

[Back](../Lab-07/readme.md)  [Next](../readme.md)