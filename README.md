# Akana API HOOK
![Image of Akana] 
(https://www.akana.com/img/formerlyLOGO8.png) 
[Akana.com](http://akana.com)

## Google Sheets API Integration 
### About the API
- this API will get the value of the first Cell in the first Worksheet, of the first Google Sheets Spreadsheet
- API Documentation: [Google Sheets API docs] (https://developers.google.com/google-apps/spreadsheets/)

### Pre-Reqs
- You must install the [Google Sheets API Hook](https://github.com/pogo61/Google-Sheets-API-Hook). As this integration API relies on the connections and security in that API.

### Getting Started Instructions
#### Download and Import
- Download GoogleSheetsAPIIntegration.zip
- Download the migrations.properties file, and edit it to replace the <replace this with your key> text with the "Container Key" of the ND or ND cluster in your target PM.
    - the container key is found by going to the "Deatils Tab" of the ND cluster, or ND defined in the Policy Manager Console, then looking at the " Container Overview" tab on that page, and copying the "Container Key:" value. ![container key screenshot](https://github.com/pogo61/Google-Sheets-API-Integration/blob/master/Screen%20Shot%202015-03-18%20at%2011.24.45%20am.png "ND Container Key")

- Login to PolicyManager  example: http://localhost:9900
- Select the root "Registry" organisation and click on the "Import Package" from the Actions navigation window on the right side of the screen
  - click on button to browse for the GoogleSheetsAPIIntegration.zip archive file 
  - make sure select the migrations.properties file you have edited 
  - click Okay to start the importation of the hook.
- this will create a Google Sheets API Integration Organisation with the requisite artefacts needed to run the API.
- you can us the API as is calling http://"URL of the Listener of your ND"/sheets_int/cell, or you can create an API in CM and expost it.
    - if you chose to create an API in CM, you must create a Service in your CM tenant which is a Virtual Service of the Google_Sheets_Integrator VS that was created by the import. Then Go to CM and create a API from an existing Service.

#### Verify Import
- Expand the services folder in the Google Sheets API Integration you imported and find Google_Sheets_Integrator VS

#### Activate Anonymous Contract
- Expand the contracts folder in the Google Sheets API Hook you imported and find the "Anonymous" contract under the "Provided Contracts" folder
- click on the "Activate Contract" workflow activity in the righ-hand Activities portlet
- ensure that the status changes to "Workflow Is Completed"

#### Configure Security
- See the [Google Sheets API Hook](https://github.com/pogo61/Google-Sheets-API-Hook)

#### Verify Connectivity
- Using curl http://"URL of the Listener of your ND"/sheets_int/cell
-  the response should be {"status":"success", "cellContent": "value"} where "value" is the contents of the first cell, in the first workbook, of the first spreadsheet, that the user defined in the tns:userAccountEmail element of the security policy assertion.

### Modify and Build
In the event you need to change the API Hook.   Here are the instructions to do so. 

### License
Put a link to an open source license

