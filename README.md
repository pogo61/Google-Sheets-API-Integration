# Akana API HOOK
![Image of Akana] 
(https://www.akana.com/img/formerlyLOGO8.png) 
[Akana.com](http://akana.com)

## Google Sheets API Integration 
### About the API
- this API will get the value of the first Cell in the first Worksheet, of the first Google Sheets Spreadsheet
- API Documentation: [Google Sheets API docs] (https://developers.google.com/google-apps/spreadsheets/)

### Pre-Reqs
- You must install the [Google Sheets API Hook](https://github.com/pogo61/Google-Sheets-API-Hook"Google Sheets API Hook"). As this integration API relies on the connections and security in that API.

### Getting Started Instructions
#### Download and Import
- Download GoogleSheetsHookAPI.zip
- Download the migrations.properties file, and edit it to replace the <replace this with your key> text with the "Container Key" of the ND or ND cluster in your target PM
- Login to PolicyManager  example: http://localhost:9900
- Select the root "Registry" organisation and click on the "Import Package" from the Actions navigation window on the right side of the screen
  - click on button to browse for the GoogleSheetsHookAPI.zip archive file 
  - make sure select the migrations.properties file 
  - click Okay to start the importation of the hook.
- this will create a Google Sheets API Hook Organisation with the requisite artefacts needed to run the API.
- you can us the API as is calling http://"URL of the Listener of your ND"/cell/cell, or you can create an API in CM and expost it.
    - if you chose to create an API in CM, you must create a Service in your CM tenant which is a Virtual Service of the Google_Sheets_Integrator VS that was created by the import. Then Go to CM and create a API from an existing Service.

#### Verify Import
- Expand the services folder in the Google Sheets API Hook you imported and find Google_Sheets_Integrator VS

#### Activate Anonymous Contract
- Expand the contracts folder in the Google Sheets API Hook you imported and find the "Anonymous" contract under the "Provided Contracts" folder
- click on the "Activate Contract" workflow activity in the righ-hand Activities portlet
- ensure that the status changes to "Workflow Is Completed"

#### Configure Security
- Go to Google Sheets API Hook -> Policies -> Operational Policies ->    Insert JWT into Downstream request policy
- Click "modify" in the XML Policy Tab. An XML Policy Content editor dialog will be displayed.
- change the value of the tns:fileLocation element to be the location and name of the file containing the private key of the Service account (this is obtain by exporting the key for the App in the [Google Developers Console] (https://console.developers.google.com/)). Note that the location must be absolute, not relative.
- change the value of the tns:serviceAccountEmail element to be the email address of the Service account (this is obtain by exporting the key for the App in the [Google Developers Console] (https://console.developers.google.com/)).
- change the value of the tns:userAccountEmail element to be the email address of the person who's spreadsheets the API is going to use (this must be a user in the Google Apps for work domain that the administrator has created).
- save the changes
- click on the "Activate Policy" workflow activity in the righ-hand Activities portlet
- ensure that the status changes to "State: Active"

#### Verify Connectivity
- Using curl http://"URL of the Listener of your ND"/cell/cell
-  the response should be {"status":"success", "cellContent": "value"} where "value" is the contents of the first cell, in the first workbook, of the first spreadsheet, that the user defined in the tns:userAccountEmail element of the security policy assertion.

### Modify and Build
In the event you need to change the API Hook.   Here are the instructions to do so. 

### License
Put a link to an open source license

