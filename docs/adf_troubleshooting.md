#### Troubleshooting Azure Data Factory pipelines orchestrated by Control-M

Data pipelines can be very complex, relying on many components to perform functions in specific orders.
This troubleshooting guide is intended for Azure Data Factory pipelines that are run and managed by the Control-M plugin for 
ADF.

For a comprehensive error code listing of related ADF elements, consult the Azure data factory guide via the link below

https://docs.microsoft.com/en-us/azure/data-factory/data-factory-troubleshoot-guide

##### Errors and solutions
The following is a list of common errors that occur during pipeline orchestration.

######Authentication error based on incorrect credentials
###### REST request template:
> URL:https://login.microsoftonline.com , URLPath:/######################-c1fad320c69b/oauth2/token , method:POSTURLParams:null

> headers:Content-Type=application/x-www-form-urlencoded

> body:grant_type=client_credentials&client_id=########-1a1f-####-ba80-######f1b5&client_secret=#########################s&resource=https://management.azure.com/

###### Response Error
> HttpResponseInfo [m_statusCode=401, m_statusMesg=Unauthorized, m_message=Error Executing REST request to https://login.microsoftonline.com : java.io.IOException: Server returned HTTP response code: 401 for URL: https://login.microsoftonline.com/92b796c5-5839-40a6-8dd9-c1fad320c69b/oauth2/token, m_contentType=application/json; charset=utf-8, m_headers=null:[HTTP/1.1 401 Unauthorized]; x-ms-ests-server:[2.1.11086.7 - CHI ProdSlices]; X-Content-Type-Options:[nosniff]; Pragma:[no-cache]; P3P:[CP="DSP CUR OTPi IND OTRi ONL FIN"]; Date:[Thu, 08 Oct 2020 12:10:03 GMT]; Strict-Transport-Security:[max-age=31536000; includeSubDomains]; Cache-Control:[no-store, no-cache]; Set-Cookie:[stsservicecookie=ests; path=/; secure; samesite=none; httponly, x-ms-gateway-slice=prod; path=/; secure; samesite=none; httponly, fpc=AgMVHzbAQitNnw62-jhLM8tUrL00AQAAAJz4ENcOAAAA; expires=Sat, 07-Nov-2020 12:10:04 GMT; path=/; secure; HttpOnly; SameSite=None]; Expires:[-1]; Content-Length:[471]; x-ms-request-id:[642598ec-7858-49f0-ab92-e610f90b6500]; Content-Type:[application/json; charset=utf-8]; ]

###### Missing or incorrect details in data factory field

###### REST request template:
> URL:https://management.azure.com , URLPath:/subscriptions/31681904-0560-470e-a176-edea4d195b22/resourceGroups/resgrpname/providers/Microsoft.DataFactory/factories/bla/pipelines/bla/createRun?api-version=2018-06-01 , method:POSTURLParams:null

>headers:Authorization=Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6ImtnMkxZczJUMENUaklmajRydDZKSXluZW4zOCIsImtpZCI6ImtnMkxZczJUMENUaklmajRydDZKSXluZW4zOCJ9.eyJhdWQiOiJodHRwczovL21hbmFnZW1lbnQuYXp1cmUuY29tLyIsImlzcyI6Imh0dHBzOi8vc3RzLndpbmRvd3MubmV0LzkyYjc5NmM1LTU4MzktNDBhNi04ZGQ5LWMxZmFkMzIwYzY5Yi8iLCJpYXQiOjE2MDIxNTg0MTcsIm5iZiI6MTYwMjE1ODQxNywiZXhwIjoxNjAyMTYyMzE3LCJhaW8iOiJFMlJnWURCbkQvNWdudjFtMCtteit6OTFYRjdRQUFBPSIsImFwcGlkIjoiN2Y0NzdmYTMtMWExZi00ODc3LWJhODAtZjM5YmI1NjNmMWI1IiwiYXBwaWRhY3IiOiIxIiwiaWRwIjoiaHR0cHM6Ly9zdHMud2luZG93cy5uZXQvOTJiNzk2YzUtNTgzOS00MGE2LThkZDktYzFmYWQzMjBjNjliLyIsIm9pZCI6ImRiZTA0YzhmLThhNWItNDM2ZS1iMWE3LTMyM2FiZjQxNzNmMiIsInJoIjoiMC5BQUFBeFphM2tqbFlwa0NOMmNINjB5REdtNk5fUjM4ZkduZEl1b0R6bTdWajhiVVNBQUEuIiwic3ViIjoiZGJlMDRjOGYtOGE1Yi00MzZlLWIxYTctMzIzYWJmNDE3M2YyIiwidGlkIjoiOTJiNzk2YzUtNTgzOS00MGE2LThkZDktYzFmYWQzMjBjNjliIiwidXRpIjoidS1QX3Z1NHJla3E0RW9mYklnSnNBQSIsInZlciI6IjEuMCIsInhtc190Y2R0IjoxNDA4MTM3MDU4fQ.DmdNKnyDkzoT3m0i_MKDOLYnOoQyVIGLFWBkwalh29IARZIk8yCEOtRH7QZlct6pIcP16Izhf3ChDTB5GzA4tB6j0A&Content-Type=application/json

>body:{}

###### Response Error

>HttpResponseInfo [m_statusCode=404, m_statusMesg=Not Found, m_message=Error Executing REST request to https://management.azure.com : java.io.FileNotFoundException: https://management.azure.com/subscriptions/31681904-0560-470e-a176-edea4d195b22/resourceGroups/NCU/providers/Microsoft.DataFactory/factories/bla/pipelines/bla/createRun?api-version=2018-06-01, m_contentType=application/json; charset=utf-8, m_headers=null:[HTTP/1.1 404 Not Found]; X-Content-Type-Options:[nosniff]; Pragma:[no-cache]; Date:[Thu, 08 Oct 2020 12:05:18 GMT]; x-ms-correlation-request-id:[8877fce5-f14d-4d5a-b3e5-b7bd92c23481]; Strict-Transport-Security:[max-age=31536000; includeSubDomains]; Cache-Control:[no-cache]; x-ms-failure-cause:[gateway]; x-ms-routing-request-id:[UKSOUTH:20201008T120518Z:8877fce5-f14d-4d5a-b3e5-b7bd92c23481]; Expires:[-1]; Content-Length:[210]; x-ms-request-id:[8877fce5-f14d-4d5a-b3e5-b7bd92c23481]; Content-Type:[application/json; charset=utf-8]; ]
