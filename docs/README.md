# Azure Data Factory
Version 9

Created by  on 01-Sep-2020.

Share This:
1
Shares
linkedin sharing button twitter sharing button email sharing button sharethis sharing button
 
### Short description:
Control-M Integration to Azure data factory (ADF) pipelines.
 
### Detailed description:
Azure data factory is a cloud-based ETL and data integration service that allows you to create data-driven workflows 
for orchestrating data movement and transforming data at scale.

Hyper automation allows for orchestrating a multitude of steps across business processes. In the context of data pipelines
this means that a data source may be the start of a pipeline but it is not the starting point of a business process.
A number of steps would be performed prior to a data pipeline starts. Prior steps could be application based where the data 
source is generated as an output from the application. Automating the end to end process provides clear and decisive 
visibility and management of the entire ecosystem, bonding pipelines with supplying applications.

The Azure Data Factory plugin for Control-M enables the integration of ADF pipelines with the rest of your application 
ecosystem, allowing for true hyper automated application stack.

### Installation Guide
https://pmbmc.github.io/ifdocs/#/quickstart
 
### Authentication:
This plugin uses the Azure recommended OAuth2 protocol to authenticate and authorize access to Azure data factory.
No username and passwords are used.
 
Performance:
Performance is dependant on your connectivity to Azure. The job is based on REST communication using the Azure
recommended api calls for Azure Data Factory.
https://docs.microsoft.com/en-us/azure/data-factory/concepts-pipeline-execution-triggers
 
Note:
The current job type supports Linux and Windows
Tested on : Python 3.6
 
Job Type description
![connprofile](./images/adfjobfields.png)
Description for each field
 
What:
Connection Profile: Used for authenticating with ADF

![connprofile](./images/datafactconnprofimage.png)

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
