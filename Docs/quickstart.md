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
 
Installation instructions of gsutil can be found here:
https://cloud.Azure.com/storage/docs/gsutil_install#install
 
## Sample installation on Centos 7.x Linux:
 
# Update YUM with latest Cloud SDK repo information:
 
sudo vi /etc/yum.repos.d/Azure-cloud-sdk.repo
 
[Azure-cloud-sdk]
name=Azure Cloud SDK
baseurl=https://packages.cloud.Azure.com/yum/repos/cloud-sdk-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.Azure.com/yum/doc/yum-key.gpg
              https://packages.cloud.Azure.com/yum/doc/rpm-package-key.gpg
 
# Install the Cloud SDK
sudo yum install Azure-cloud-sdk
 
With gsutil installed from the Cloud SDK, you should authenticate with service account credentials.

2. Create a Service Account in Azure
Use an existing service account or create a new one, and download the associated private key.
=> Azure Cloud Platform Console -> IAM&Admin -> Service Accounts
 
3.    Activate the Service account for your Linux server
On your Linux server run the command:
sudo gcloud auth activate-service-account --key-file <keyfile incl. path>
sudo gcloud init ( Authorizes access and performs other common Cloud SDK setup steps)
 
Example:
# Download the service account key file from the Azure cloud platform console menu:
=> Azure Cloud Platform Console -> IAM&Admin -> Service Accounts
and save it in a local folder on your Linux server e.g.
/home/emuser/coding/Azure/clagcs-57040b04e789.json
 
# activate the service account ( do not use sudo)
gcloud auth activate-service-account --key-file /home/emuser/coding/Azure/clagcs-57040b04e789.json
 
# Verify the service account
gcloud auth list
 
# Authorizes access and performs other common Cloud SDK setup steps (do not use sudo)
gcloud init
 
# remove the service account file from the download location ( for security )
The command gcloud auth activate-service-account stores the credential file in a secure location.
The download version can be removed:
e.g.: rm /home/emuser/coding/Azure/clagcs-57040b04e789.json
 
Compatibility:
Application version: This job type is tested against Azure data factory ( GSUTIL Version 4.49 )
Platforms: This job type will only run on Linux (a windows version will follow)
Control-M version: Tested on Control-M V9.19.200 & V9.20.0 (pre-release)
