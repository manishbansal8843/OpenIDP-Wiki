
**application-services : Application Services**

The Application Services API resources are used to manage Application, these resources allow to add , update and delete Application data. 
Note: These resources can be used as a part of scripts or programs to allow authorized administrators to manage the application.

**REST end points**


1./applicationService/applications/mail

**Method type**: POST
#### Input JSON:

````
{
  "applicationName": "string",
  "envName": "string",
  "mailBody": "string",
  "method": "string",
  "pipelineName": "string",
  "platformName": "string",
  "releaseNumber": "string",
  "userName": "string"
}
````
#### Output JSON:

````
{
"errorMessage": "string",
"resource": "string",
"status": "string",
"statusCode": 0
}
````

**Uses** : to send the mail for Application creation status.

2. /applicationService/{id}/createApplication

**Method type**: POST

**Input JSON**:
```
{
  "applicationName": "string",
  "artifactToStage": {
    "artifact": "string",
    "artifactRepo": {
      "repoName": "string",
      "repoPassword": "string",
      "repoURL": "string",
      "repoUsername": "string"
    },
    "artifactRepoName": "string",
    "flattenFileStructure": "string",
    "nexusAPIKey": "string",
    "nuspecFilePath": "string"
  },
  "developers": "string",
  "environmentOwnerDetails": [
    {
      "client": "string",
      "connType": "string",
      "dBOwners": "string",
      "envConfig": [
        {
          "keyName": "string",
          "keyValue": "string"
        }
      ],
      "environmentName": "string",
      "environmentOwners": "string",
      "hostName": "string",
      "instanceNumber": "string",
      "landscapeType": "string",
      "language": "string",
      "password": "string",
      "port": "string",
      "qa": "string",
      "sapPISystemID": "string",
      "sapPISystemNum": "string",
      "serverName": "string",
      "systemId": "string",
      "userName": "string"
    }
  ],
  "environmentProvDetails": [
    {
      "ansPassword": "string",
      "ansUserName": "string",
      "environmentProvName": "string",
      "invName": "string",
      "playName": "string",
      "playPath": "string",
      "serverName": "string",
      "toolName": "string"
    }
  ],
  "ibmRQMServerDetails": {
    "password": "string",
    "serverURL": "string",
    "userName": "string"
  },
  "pipelineAdmins": "string",
  "releaseManager": "string",
  "sapApplication": "string",
  "sapPIApplication": "string",
  "slavesDetails": [
    {
      "build": "string",
      "buildServerOS": "string",
      "createNewSlave": "string",
      "deploy": "string",
      "labels": "string",
      "slaveName": "string",
      "slaveUsage": "string",
      "sshkeyPath": "string",
      "test": "string",
      "workspacePath": "string"
    }
  ],
  "testAdmins": "string",
  "testers": "string",
  "virtualServiceServerDetails": {
    "password": "string",
    "serverUrl": "string",
    "userName": "string"
  }
}
```

**Output JSON:**
```
{
"errorMessage": "string",
"resource": "string",
"status": "string",
"statusCode": 0
}
```
**Uses** : to create Application in IDP.

3. /applicationService/{id}/getAppInfo

**Method type**: POST

**Input parameter**:

"applicationName": "string"



**Output JSON:**
````
{
"errorMessage": "string",
"resource": "string",
"status": "string",
statusCode": 0
}
````
**Uses** : to get the details of an Application.

4. /applicationService/{id}/getEnvironmentNames

**Method type**: POST

**Input parameter:**

"applicationName": "string"



**Output JSON**:
```
{
"errorMessage": "string",
"resource": "string",
"status": "string",
"statusCode": 0
}
```

**Uses**: to get the names of Environment of an Application.

 5. /applicationService/{id}/updateAppinfo

**Method type**: POST

**Input JSON**:
```
{
  "applicationName": "string",
  "artifactToStage": {
    "artifact": "string",
    "artifactRepo": {
      "repoName": "string",
      "repoPassword": "string",
      "repoURL": "string",
      "repoUsername": "string"
    },
    "artifactRepoName": "string",
    "flattenFileStructure": "string",
    "nexusAPIKey": "string",
    "nuspecFilePath": "string"
  },
  "developers": "string",
  "environmentOwnerDetails": [
    {
      "client": "string",
      "connType": "string",
      "dBOwners": "string",
      "envConfig": [
        {
          "keyName": "string",
          "keyValue": "string"
        }
      ],
      "environmentName": "string",
      "environmentOwners": "string",
      "hostName": "string",
      "instanceNumber": "string",
      "landscapeType": "string",
      "language": "string",
      "password": "string",
      "port": "string",
      "qa": "string",
      "sapPISystemID": "string",
      "sapPISystemNum": "string",
      "serverName": "string",
      "systemId": "string",
      "userName": "string"
    }
  ],
  "environmentProvDetails": [
    {
      "ansPassword": "string",
      "ansUserName": "string",
      "environmentProvName": "string",
      "invName": "string",
      "playName": "string",
      "playPath": "string",
      "serverName": "string",
      "toolName": "string"
    }
  ],
  "ibmRQMServerDetails": {
    "password": "string",
    "serverURL": "string",
    "userName": "string"
  },
  "pipelineAdmins": "string",
  "releaseManager": "string",
  "sapApplication": "string",
  "sapPIApplication": "string",
  "slavesDetails": [
    {
      "build": "string",
      "buildServerOS": "string",
      "createNewSlave": "string",
      "deploy": "string",
      "labels": "string",
      "slaveName": "string",
      "slaveUsage": "string",
      "sshkeyPath": "string",
      "test": "string",
      "workspacePath": "string"
    }
  ],
  "testAdmins": "string",
  "testers": "string",
  "virtualServiceServerDetails": {
    "password": "string",
    "serverUrl": "string",
    "userName": "string"
  }
}
```

**Output JSON**:
```
{
"errorMessage": "string",
"resource": "string",
"status": "string",
"statusCode": 0
}
```

**Uses** :to update the application details.


6./applicationService/{platformName}/{id}/getExistingApps

**Method type**: POST

**Input parameter**:
" platformName ": "string",

**Output JSON**:
```
{
"errorMessage": "string",
"resource": "string",
"status": "string",
"statusCode": 0
}
```
**Uses** : to get the list of Application of a particular Platform.
