# Installation instructions 
Version 8

Created by Neil Cullum on 01-Sep-2020.

Share This:
1
Shares
linkedin sharing button twitter sharing button email sharing button sharethis sharing button

 
### Quick Start:
Control-M Integration to Azure data factory (ADF) pipelines.
 
### Installation Details

Download the Azure Data Factory job from http://github.com/adfaijob

There are 2 methods for deploying the jobtype

1. Using the Application Integrator UI
2. Using the Control-M Automation  

Prerequisites and installation notes:
 
Control-M Agent on a Linux System with the Application Integrator CM
python 3.6 (tested)
service account credentials
 
Installation:
The Azure data factory integration uses in the Azure data factory api. Python application.

#### Performance:
Performance is dependant on your connectivity to Azure. The job is based on REST communication using the Azure
recommended api calls for Azure Data Factory.

https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipeline-execution-triggers
 
### Authentication:
This plugin uses the Azure recommended OAuth2 protocol to authenticate and authorize access to Azure data factory.
No username and passwords are used.
   
1. Download the Integration Factory AI jobtype.
2. Download the python package and unzip the contents.
3. Deploy the plugin through Control-M Application Integrator.
4. Define a connection profile
5. Run your first Azure Data Factory pipeline from Control-M

 
Note:
The current job type supports Linux and Windows
Tested on : Python 3.7
 
Job Type description

Description for each field
 
What:
Connection Profile: Used for authenticating with ADF

![connectionprofile](./images/datafactconnprofimage.png)

 
===== Pipeline Parameters =====

1. Job Set Path - Path to python pipeline executable
2. Trigger Script - Python pipeline executable
3. Resource Group - Azure Resource Group Name
4. Factory Name - Azure Data Factory Name
5. Pipeline Name - Pipeline to be triggered
 
![jobfields](./images/adfjobfields.png)

### Building your ADF job in Control-M Automation API

Control-M automation api allows for the creation of jobs in a JSON format.
Once you have deployed the ADF plugin you have immediate support for the creation of ADF pipeline
jobs in JSON format.

Sample JSON

```
{
  "adfpython": {
    "Type": "SimpleFolder",
    "ControlmServer": "production",
    "OrderMethod": "Manual",
    "AzureDataFactorypython_Job_2": {
      "Type": "Job:ApplicationIntegrator:AzureDataFactorypython",
      "ConnectionProfile": "<youradfprofile>",
      "AI-Pipeline Name": "<yourPipelineName>",
      "SubApplication": "<Subapp>",
      "Host": "<yourhost>",
      "CreatedBy": "emuser",
      "RunAs": "<youradfprofile>",
      "Application": "<Application>",
      "When": {
        "WeekDays": [
          "NONE"
        ],
        "MonthDays": [
          "ALL"
        ],
        "SpecificDates": [],
        "DaysRelation": "OR"
      }
    }
  }
}


```
 
 #### Return to Azure Data Factory plugin Introduction

https://pmbmc.github.io/ifdocs/

