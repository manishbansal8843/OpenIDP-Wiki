### job-service : Job Service

The Job Services API resources are used to manage IDP Job , these resources allows to add , update and delete IDP Job data.
Note: These resources can be used as a part of scripts or programs to allow authorized administrators to manage the application.
### REST end points

1. /jobService/pipelineAdmins

**Method type**: POST

**Input Parameter**:

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
**Uses**: to get the list of pipeline admins.

2. /jobService/pipelines/sapApplication/{application_name}


**Method type**: GET

**Input Parameter**:

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
**Uses** : to check wether application is SAP application or general. 

3. /jobService/{id}/TriggerInputs

**Method type**: POST

**Input JSON**:
```
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
**Uses** : to get the inputs for triggering a pipeline.
      
4. /jobService/{id}/deletePipeline

**Method type**: POST

**Input JSON**:
```
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
**Uses** : to delete a pipleine.
      

    
5. /jobService/{id}/jobCreationSuccessMail

**Method type**: POST

**Input JSON**:
```
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
**Uses** : to send mail to users for the notification of successfully created pipeline.

6. /jobService/{id}/downloadArtifact

**Method type**: POST

**Input JSON**:
```
{
  "buildNumber": "string",
  "jobName": "string",
  "subJobName": "string"
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
**Uses** : to download artifact from nexus.
      
  
7. /jobService/{id}/triggerJob 

**Method type**: POST

**Input JSON:**
````
{
  "appId": "string",
  "applicationName": "string",
  "apprBuildNo": "string",
  "apprComment": "string",
  "apprInput": "string",
  "apprStepName": "string",
  "artifactName": "string",
  "artifactorySelected": "string",
  "branchOrTag": "string",
  "branchOrTagList": [
    true
  ],
  "branchOrTagValue": "string",
  "build": {
    "branchSelected": "string",
    "cast": "string",
    "codeAnalysis": "string",
    "currentDate": "string",
    "manifestFileName": "string",
    "module": [
      "string"
    ],
    "newVersion": "string",
    "oldVersion": "string",
    "srcEnv": "string",
    "unitTest": "string"
  },
  "buildDeploy": "string",
  "buildartifactNumber": "string",
  "castSlaveName": "string",
  "charmRequests": [
    "string"
  ],
  "client": "string",
  "componentSprint": [
    {
      "dataFile": "string",
      "projectId": 0,
      "resultURL": "string",
      "sourceFile": "string",
      "sprintId": 0,
      "sprintName": "string"
    }
  ],
  "copyTR": true,
  "dashBoardLink": "string",
  "dbOperations": "string",
  "depParam": "string",
  "deploy": {
    "allEnvOwner": "string",
    "artifactID": "string",
    "dbDeployFailSafe": "string",
    "dbDeployOperation": "string",
    "dbDeployPipelineList": "string",
    "dbDeployPipelineOwners": "string",
    "dbDeployRollbackType": "string",
    "dbDeployRollbackValue": "string",
    "deployArtifact": {
      "artifactID": "string",
      "artifactName": "string",
      "buildModulesList": [
        "string"
      ],
      "downloadURL": "string",
      "environment": "string",
      "groupId": "string",
      "nexusURL": "string",
      "repoName": "string",
      "timestamp": "string",
      "userInfo": "string",
      "version": "string"
    },
    "deployModule": [
      "string"
    ],
    "deployOperationSelected": "string",
    "deployStep": [
      "string"
    ],
    "deploymentType": "string",
    "destEnvOwner": "string",
    "destLandscape": "string",
    "manifestFileName": "string",
    "nexusId": "string",
    "pairName": "string",
    "password": "string",
    "sourceEnvName": "string",
    "srcEnv": "string",
    "subModule": [
      "string"
    ],
    "version": "string"
  },
  "deployDB": "string",
  "emailed": "string",
  "envParamList": {
    "envName": "string",
    "envParam": [
      {
        "keyName": "string",
        "keyValue": "string"
      }
    ]
  },
  "envSelected": "string",
  "errorCode": "string",
  "fileName": "string",
  "gitTag": "string",
  "hpAlmTestSuite": "string",
  "ibmRQMServerDetails": {
    "password": "string",
    "serverURL": "string",
    "userName": "string"
  },
  "ibmRQMTestSuiteId": "string",
  "instance": "string",
  "itawSuite": [
    "string"
  ],
  "jiraProjectKey": "string",
  "jobBuildId": "string",
  "jobParam": [
    {
      "jobParamName": "string",
      "jobParamSatic": true,
      "jobParamValue": "string",
      "jobType": "string"
    }
  ],
  "jobType": "string",
  "landscapeType": "string",
  "language": "string",
  "lanscapeName": "string",
  "mtmProjectName": "string",
  "mtmStepName": "string",
  "nonRepoDeployStatus": "string",
  "notify": "string",
  "nugetPackaging": true,
  "pairName": "string",
  "password": "string",
  "pipId": "string",
  "pipelineName": "string",
  "pipelineSelection": [
    {
      "appSelectionDetails": [
        {
          "pipelineSelectionDetails": [
            "string"
          ]
        }
      ]
    }
  ],
  "pipelines": [
    {}
  ],
  "platform": "string",
  "postTestSelected": "string",
  "processSelected": "string",
  "rebase": {
    "bugFixTR": "string",
    "sourceEnvSelected": "string",
    "targetEnvSelected": "string",
    "transportObject": "string",
    "transportObjectType": "string"
  },
  "reconcileSlaveName": "string",
  "releaseManagers": "string",
  "releaseNumber": "string",
  "repoDeployStatus": "string",
  "restoreDB": "string",
  "restoreTRFlag": true,
  "restoreTRParams": "string",
  "rmAssemblies": "string",
  "sapUserName": "string",
  "saptestName": "string",
  "scmBranch": "string",
  "slaveName": "string",
  "sonardashBoardLink": "string",
  "srcEnv": "string",
  "stubHref": [
    {
      "href": "string",
      "stubNameVersion": "string"
    }
  ],
  "subApplicationName": "string",
  "systemId": "string",
  "systemName": "string",
  "technology": "string",
  "testPlanId": "string",
  "testSelected": "string",
  "testSlaveName": "string",
  "testStep": [
    "string"
  ],
  "testStepDetails": [
    {
      "testStepName": "string",
      "testStepTool": "string"
    }
  ],
  "testSuitId": "string",
  "testsStepSelected": [
    {
      "stepName": "string",
      "testSlave": "string"
    }
  ],
  "tfsWorkItem": "string",
  "tokenValue": "string",
  "transportRequest": [
    "string"
  ],
  "triggerId": 0,
  "usePreviousArtifact": "string",
  "userName": "string",
  "userStories": "string",
  "userStoryString": "string",
  "virtualServicesList": [
    "string"
  ],
  "virtualTestStep": "string",
  "virtualization": "string"
}
````

**Output JSON**:
````
{
"errorMessage": "string",
"resource": "string",
"status": "string",
"statusCode": 0
}
````
**Uses**: to trigger a pipline from IDP.
      
8. /jobService/{platformName}/{id}/submitJob

**Method type**: POST

**Input Parameter**:
"platformName": "string",
"idpJOSN": "string",

**Output JSON**:
````
{
"errorMessage": "string",
"resource": "string",
"status": "string",
"statusCode": 0
}
````
**Uses** : to submit job for creation of pipeline in Jenkins.

9. /jobService/{platform}/{id}/getPipelineDetails

**Method type:** POST

**Input JSON:**
```
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

**Uses** : to get the details of a pipeline.
 