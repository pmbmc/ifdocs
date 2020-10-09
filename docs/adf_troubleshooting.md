## Troubleshooting Azure Data Factory pipelines orchestrated by Control-M
Data pipelines can be very complex, relying on many components to perform functions in specific orders.
This troubleshooting guide is intended for Azure Data Factory pipelines that are run and managed by the Control-M plugin for 
ADF.
For a comprehensive error code listing of related ADF elements, consult the Azure data factory guide via the link below

https://docs.microsoft.com/en-us/azure/data-factory/data-factory-troubleshoot-guide
### Errors
The following is a list of common errors that occur during pipeline orchestration.
### Authentication error based on incorrect credentials
#### REST request template:
Refer to the connection profile definition in the quickstart guide. Ensure all credentials are valid
``` 
URL:https://login.microsoftonline.com , URLPath:/978n2rgjo2o34f7n345g-c1fa-0=34kf9b/oauth2/token , method:POSTURLParams:null
headers:Content-Type=application/x-www-form-urlencoded
body:grant_type=client_credentials&client_id=uerferg-1a1f-oprjeg-ba80-9834jtf1b5&client_secret=-98435gnuwe8lrig3905s&resource=https://management.azure.com/
```
#### Response Error
``` 
HttpResponseInfo [m_statusCode=401, m_statusMesg=Unauthorized, m_message=Error Executing REST request to https://login.microsoftonline.com 
: java.io.IOException: Server returned HTTP response code: 401 for URL: https://login.microsoftonline.com/0934mfc5-5839-40a6-8##9-c1f9034jre69b/oauth2/token, m_contentType=application/json; charset=utf-8, m_headers=null:[HTTP/1.1 401 Unauthorized]; x-ms-ests-server:[2.1.11086.7 - CHI ProdSlices]; X-Content-Type-Options:[nosniff]; Pragma:[no-cache]; P3P:[CP="DSP CUR OTPi IND OTRi ONL FIN"]; Date:[Thu, 08 Oct 2020 12:10:03 GMT]; Strict-Transport-Security:[max-age=31536000; includeSubDomains]; Cache-Control:[no-store, no-cache]; Set-Cookie:[stsservicecookie=ests; path=/; secure; samesite=none; httponly, x-ms-gateway-slice=prod; path=/; secure; samesite=none; httponly, fpc=AgMVHzbAQitNnw62-jhLM8tUrL00AQAAAJz4ENcOAAAA; expires=Sat, 07-Nov-2020 12:10:04 GMT; path=/; secure; HttpOnly; SameSite=None]; Expires:[-1]; Content-Length:[471]; x-ms-request-id:[642598ec-7858-49f0-ab92-e610f90b6500]; Content-Type:[application/json; charset=utf-8]; ]
```
-------------------------------------------
### Missing or incorrect details in data factory field
Refer to the Job Definition fields in the quickstart guide. Ensure that the pipeline exists in the specified data factory
#### REST request template:
``` 
URL:https://management.azure.com,URLPath:/subscriptions/31681904-0560-470e-a176-edea4d195b22/resourceGroups/resgrpname/providers/Microsoft.DataFactory/factories/factoryname/pipelines/bla/createRun?api-version=2018-06-01,method:POSTURLParams:null
headers:Authorization=Bearer eyJ0eXAiOiJKV1QiLCJhbtnMkxZczJwidXRpIjoidS1QX3Z1NHJla3E0RW9mYklnSnNBQSt6pIcP16Izhf3ChDTB5GzA4tB6j0A&Content-Type=application/json
body:{}
```
#### Response Error
```
HttpResponseInfo [m_statusCode=404, m_statusMesg=Not Found, m_message=Error Executing REST request to https://management.azure.com 
: java.io.FileNotFoundException: https://management.azure.com/subscriptions/09234904-9023-470e-a176-e093495b22/resourceGroups/{{resourcegroup}}/providers/Microsoft.DataFactory/factories/bla/pipelines/bla/createRun?api-version=2018-06-01, m_contentType=application/json; charset=utf-8, m_headers=null:[HTTP/1.1 404 Not Found]; X-Content-Type-Options:[nosniff]; Pragma:[no-cache]; Date:[Thu, 08 Oct 2020 12:05:18 GMT]; x-ms-correlation-request-id:[8877fce5-f14d-4d5a-b3e5-b7bd92c23481]; Strict-Transport-Security:[max-age=31536000; includeSubDomains]; Cache-Control:[no-cache]; x-ms-failure-cause:[gateway]; x-ms-routing-request-id:[UKSOUTH:20201008T120518Z:8877fce5-f14d-4d5a-b3e5-b7bd92c23481]; Expires:[-1]; Content-Length:[210]; x-ms-request-id:[8877fce5-f14d-4d5a-b3e5-b7bd92c23481]; Content-Type:[application/json; charset=utf-8]; ]
```
-------------------------------------------
### Step failure within a pipeline
Step failures within pipelines are usually due to faulty or unavailable data components.
The example below reflects an unavailable data source in the first step of the pipeline.
#### REST request template:
```
method: 	GET
URL: 	https://management.azure.com path: /subscriptions/8923u234-0560-83gr-a176-8324hurg2/resourceGroups/rscgrp/providers/Microsoft\
.DataFactory/factories/my-data-factory-ai/pipelineruns/623eg23ef-ewiu-9792-d773-unwe812hjeed?api-version=2018-06-01
```
#### Response Error
```
'REASON_FOR_FAILURE'==> 'Operation on target firstStepCopy failed: ErrorCode=UserErrorFailedToConnectOdbcSource,'Type=Microsoft.Dat\
aTransfer.Common.Shared.HybridDeliveryException,Message=ERROR [08001] [Microsoft][ODBC PostgreSQL Wire Protocol driver]Connection r\
efused. Verify Host Name and Port Number.

ERROR [HY000] [Microsoft][ODBC PostgreSQL Wire Protocol driver]Can't connect to server on 'coolhost.cantfindme.org',Source=Microsoft.Dat\
aTransfer.Runtime.GenericOdbcConnectors,''Type=System.Data.Odbc.OdbcException,Message=ERROR [08001] [Microsoft][ODBC PostgreSQL Wir\
e Protocol driver]Connection refused. Verify Host Name and Port Number.
ERROR [HY000] [Microsoft][ODBC PostgreSQL Wire Protocol driver]Can't connect to server on 'coolhost.cantfindme.org',Source=,'' 
'RUNSTATUS'==> 'Failed' 
```
-------------------------------------------
### Go to Azure Data Factory plugin Introduction
https://pmbmc.github.io/ifdocs/
### Go to the Quick Start Guide
https://pmbmc.github.io/ifdocs/#/quickstart