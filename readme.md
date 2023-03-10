# Connected Vehicle Project

Hello and welcome to the connected vehicle project.

<br/>

# Project Overview

General Motors is one of the leading heavy vehicle manufacturing company. To improve their services, they are planning to rollout new features based on IOT.

General Motors have a tie up with a third party who provide a device that General Motors plugs in into their cars and other vehicles.This device has the capability to capture the vehicle temperature, speed, turbulence and a few more parameters. All these parameter are captured by this device and this telemetry data is sent to the AWS cloud by this third party device and stored in JSON file format.

<img src="images/10.jpg">

<br/>

# The Task 
The Data Engineering team at General Motors have the following tasks to do:


* Move the telemetry data stored as JSON files in AWS cloud to Microsoft Azure storage
* Validate the JSON data
* Store validated data in SQL database for use by Data Science team

<img src="images/20.jpg">

<br/>

# The Goal

The goal is to develop a Data Engineering Project for a connected vehicle use case from scratch and include all phases of development - designing, architecting, implementing and testing.

<br/>

# Architecture Diagram

<img src="images/30.jpg">

* Every architecture diagram starts with an input source, and ends with the output source. You can see that our input source is AWS Cloud S3 storage bucket. This is the storage bucket where all the telemetry data in JSON file format will be saved by the IoT devices.

* Once the data is moved, the industry standard says the data must go into the landing folder. The landing folder always contains the original, raw, unprocessed data coming from source.

* We then validate the JSON data using an Azure function. We have a storage based trigger on the Azure function. As soon as a file arrives into the landing folder, this azure function will trigger automatically and read the file to validate whether data is stored in proper JSON format or not. If it contains a proper JSON, we move the data into the staging folder, else into Rejected folder. 

<br/>

# Technologies involved

We'll use a range of technologies for this data engineering project:

* Azure Data Lake Storage Gen 2
* Azure Data Factory
* Azure Function
* Azure Key Vault
* Azure SQL DB
* AWS S3 Bucket
* Connect S3 to Azure Cloud

<br/>

# Prerequisites

* Azure account
* AWS account

Click [here](Lab-01/readme.md) to start with the implementation.