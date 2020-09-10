# Azure Data Factory
Version 8

Created by  on 01-Sep-2020.

Share This:
1
Shares
linkedin sharing button twitter sharing button email sharing button sharethis sharing button
 
### Short description:
Control-M Integration to Azure data factory (ADF) pipelines.
 
### Detailed description:
Azure data factory is a cloud-based ETL and data integration service that allows you to create data-driven workflows for orchestrating data movement 
and transforming data at scale 

### Installation Guide
https://pmbmc.github.io/ifdocs/#/quickstart
 
### Authentication:
This integration uses the Azure recommended OAuth2 protocol to authenticate and authorize access to Azure data factory.
No username and passwords are used. Instead the Azure service account key file concept is applied.
 
Performance:
The job type support multi-threaded parallel uploads, downloads and deletions of objects
 
Note:
The current job type supports Linux and Windows
Tested on : Python 3.6
 
Job Type description
job_gross.png
Description for each field
 
What:
Connection Profile: Used for authenticating with ADF

![image](/uploads/dd5e50f9432cdc69bcdb3c126796f25a/image.png)

The integration uses OAuth2 to authenticate and authorize access to Azure data factory.
No username and passwords are used. Instead the Azure service account key file is once, during installation downloaded to the client (= Linux server where the Control-M agent with the Azure-cloud-sdk is installed). Each time a request is made the client requests an access token to authenticate and authorize access to Azure data factory.
 
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
 
## Sample installation on Centos 7.x Linux:
 
Example:
 
 
Compatibility:
