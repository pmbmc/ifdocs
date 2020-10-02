# Control-M Azure Data Factory plugin
Version 9.15

### Go directly to the Quick Start Guide
https://pmbmc.github.io/ifdocs/#/quickstart

### Short description:
Control-M Integration plugin for Azure data factory (ADF) pipelines.


Created on 01-Sep-2020
Updated on 02-Oct-2020
 
### Detailed description:

The Azure Data Factory plugin for Control-M enables the integration of ADF pipelines with the rest of your application 
ecosystem, allowing for a true hyper automated application stack. True enterprise orchestration enables continuous SLA and business
process management.

Azure data factory is a cloud-based ETL and data integration service that allows you to create data-driven workflows 
for orchestrating data movement and transforming data at scale.

Hyper automation allows for orchestrating a multitude of steps across business processes. In the context of data pipelines
this means that a data source may be the start of a pipeline but it is not the starting point of a business process.
A number of steps would be performed prior to a data pipeline being triggered. Prior steps could be application based where the data 
source is generated as an output from the application. Automating the end to end process provides clear and decisive 
visibility and management of the entire ecosystem, bonding pipelines with supplying applications.

#### Features

* #### 1. Integrate an Azure Data Factory pipeline with external components.  

![workflow](./images/pipelineworkflow.png)

* #### 2. Monitor the pipeline status.

![workflow](./images/trackpipeline.png)

* #### 3. Return the results of the pipeline steps to the output in the Control-M Monitoring domain.  

* #### 4. Integrate Azure pipeline runs with all existing Control-M capabilities.  
    For example : 
                   
        a. Have your pipeline tasks defined in JSON and managed by your cicd process.          
        b. Attach SLA's to your pipeline.
        c. Wait for a b2b source to arrive and process it in an application and run a pipeline based on the outcome.
        d. Attach prior and post dependancy steps to your pipeline for a fully encompassed view of your environment.
        e. A single reference point for the entire lifecycle of your data, from creation to analytics.

* #### 5. Avoid connection timeouts and unnecessary pipeline reruns

  > #### Contention Scenario
 ###### Here is a typical error caused by contention on a database table due to simultaneous writes.  

![workflow](./images/pipelinetimeout.png)

  > #### Contention Challenge
 ###### As a result there are unnecessary pipeline failures

![workflow](./images/pipelinecontention.png)

  > #### Contention Management  

 ###### This can be managed with Control-M resource management  

![workflow](./images/aznocontention.png)

 ###### Below is a comparison from the Control-M monitoring domain. The pipelines on the left are failing due to a lack of resources. The pipelines on the right are only submitted when resources are available.

  > #### Results Comparison

 ![workflow](./images/contentionmanagement.png)



 

