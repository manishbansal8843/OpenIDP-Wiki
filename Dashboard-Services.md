The Dashboard Service Api resources are used to retrieve dashboard data for grafana as well as to store data in postgres database

**REST end points**

**1. /query**

Method type: POST

**Input Json:**
```
{
    "panelId": string,
    "range": string,
    "rangeRaw": string,
    "interval": string,
    "intervalMs": string,
    "targets": [],
    "format": string,
    "maxDataPoints": string
}
```

**Output Json:**
```
[
  {
    "columns": [],
    "rows": [],
    "type": string,
    "target": string,
    "datapoints": [],
    "series": string
  }
]
```
**Uses :** To send data back to grafana based on the input json

**2. /search**

Method type: POST

**Input Json:**
```
{
    "target": string,
}
```

**Output :**

List of Strings

**Uses :** To send data back to grafana based on the query within target

**3. /{appname}/{pipname}/{pipbuildno}/update**

Method type: POST

**Input Json:** 
```
{
  "functional":{
    "accleratest":{
      "totalTest":"integer",
      "passed":"integer",
      "failed":"integer"
    },
    "itops":{
      "totalTest":"integer",
      "passed":"integer",
      "failed":"integer"
    },
    "selenium":{
      "totalTest":"integer",
      "passed":"integer",
      "failed":"integer"
    },
    "qualitia":{
      "totalTest":"integer",
      "passed":"integer",
      "failed":"integer"
    }
  },
  "sonarDetails":{
    "sonarServer":"string",
    "sonarPrjctKey":"string",
    "loc":"integer",
    "bugs":"string",
    "vulnerabilities":"string",
    "codesmells":"string",
    "rateperhour":"string",
    "technicalDebt":"string"
    
  },
  "securityTest":{
    "checkmarx":{
      "high":"integer",
      "medium":"integer",
      "low":"integer"
      
    }
  },
  "codeQuality":{
    "sonar":{
      "critical":"integer",
      "blocker":"integer",
      "major":"integer",
      "minor":"integer",
      "info":"integer"
    },
    "pmd":{
       "critical":"integer",
      "blocker":"integer",
      "major":"integer",
      "minor":"integer",
      "info":"integer"
    }
  },
  "codeCoverage":{
    "cobertura":{
      "branchCoverage":"string",
      "classCoverage":"string",
      "complexityScore":"string",
      "instructionCoverage":"string",
      "lineCoverage":"string",
      "methodCoverage":"string"
    },
    "jacoco":{
       "cobertura":{
      "branchCoverage":"string",
      "classCoverage":"string",
      "complexityScore":"string",
      "instructionCoverage":"string",
      "lineCoverage":"string",
      "methodCoverage":"string"
    },
    "istanbul":{
      "lineCoverage":"string"
    }
  },
  "log":"string",
  "folders": [
    {
      "objectStore":"string",
      "name":"string",
      "id":"string",
      "objectType":"string"
    }
    ],
    "documents": [
      {
      "objectStore":"string",
      "name":"string",
      "id":"string",
      "objectType":"string"
    }
      ],
      
    "choiceLists":[
      {
      "objectStore":"string",
      "name":"string",
      "id":"string",
      "objectType":"string"
    }
      ],
  "classDefinitions":[
    {
      "objectStore":"string",
      "name":"string",
      "id":"string",
      "objectType":"string"
    }
    ],
  "others":[
      {
      "objectStore":"string",
      "name":"string",
      "id":"string",
      "objectType":"string"
    }
    ],
    
  
  "pipelineName": "string",
  "application": "string",
  "fileNet": "string",
  "buildId": "string",
  "buildDetails":[
    {
    "stageName":"string",
    "lastBuildId":"string",
    "lastSuccessfulBuildId":"string",
    "lastCompletedBuildId":"string",
    "lastUnstableBuildId":"string",
    "lastUnsuccessfulBuildId":"string",
    "buildTime":"string",
    "builtStatus":"string",
    "timestamp":"string",
    "score":"string",
    "lastFailedBuildId":"string"
    }
    ],
  "buildOwners":[
    "id":[]
    ],
  "ruleSet": [
    {
      "id": "string",
      "severity": "string",
      "message": "string",
      "line": "string",
      "ruleName": "string",
      "category": "string"
    }
  ],
  "codeMetric":[
    {
      "id": "string",
      "coverageMetric": double,
      "cyclomaticComplexity": "string",
      "maintainabilityIndex": "string",
      "changePronenessIndex": "string",
      "defectPronenessIndex": "string"
    }
    ],
  "testCaseResult": [
    {
      "id": "string",
      "message": "string",
      "testSuiteName": "string",
      "category": "string",
      "status": "string",
      "startTime": "string",
      "duration": "string"
    }
  ],
  "codeAnalysis": [
    {
      "id": "string",
      "severity": "string",
      "message": "string",
      "line": "string",
      "ruleName": "string",
      "category": "string",
      "recommendation": "string",
      "className": "string"
    },
    
  ],
  "coverageDetails":[
    {
      "className": "string",
      "lineCoverage": "string",
      "category": "string",
      "pckage": "string"
    }
    ],
    "versionInfo":[
      {
        "lastModified": "string",
        "commitMessage": "string",
        "id": "string",
        "latestFileVersion": "string",
        "lastModifiedBy": "string",
        "commitId": "string"
      }
      ],
      "scmInfo":[
        {
        "lastModified": "string",
        "commitMessage": "string",
        "id": "string",
        "latestFileVersion": "string",
        "lastModifiedBy": "string",
        "remoteUrl": "string",
        }
        ]
}
```
**Uses :** To update database for the specific application-pipeline-pipbuildno combination based on the json object
