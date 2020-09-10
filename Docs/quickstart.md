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

Download the Azure Data Factory job from http://github.com/adfai

There are 2 methods for deployment

1.) Using the Application Integrator UI
2.) Using the Control-M Automation  

### Building your ADF job in Control-M Automation API


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

### Return to ADF Getting Started 

http://localhost:3000

 
### Authentication:
This integration uses the Azure recommended OAuth2 protocol to authenticate and authorize access to Azure data factory.
No username and passwords are used. Instead the Azure service account key file concept is applied.
 
Performance:
 
Note:
The current job type supports Linux and Windows
Tested on : Python 3.7
 
Job Type description
job_gross.png
Description for each field
 
What:
Connection Profile: Used for authenticating with ADF

![image](/uploads/dd5e50f9432cdc69bcdb3c126796f25a/image.png)

 
===== Pipeline Parameters =====

Job Set Path - Path to python pipeline executable
Trigger Script - Python pipeline executable
Resource Group - Azure Resource Group Name
Factory Name - Azure Data Factory Name
Pipeline Name - Pipeline to be triggered
 
Prerequisites and installation notes:
 
Control-M Agent on a Linux System with the Application Integrator CM
python 3.6 (tested)
service account credentials
 
Installation:
The Azure data factory integration uses in the Azure data factory api. Python application.
 
1. Download the Integration Factory AI jobtype 
 
Installation instructions of gsutil can be found here:
https://cloud.Azure.com/storage/docs/gsutil_install#install
 
## Sample installation on Centos 7.x Linux:
 
