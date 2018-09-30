
### user-service : User Service


The User Services API resources are used to manage users and get the details of a user. 
**Note**: These resources can be used as a part of scripts or programs to allow authorized administrators to manage the application.

**REST end points**

1. /userService/applications/roles/{application_name}

**Method type:** GET

**Input Parameter:**
"applicationName": "string"

**Output JSON:**
```
{
"errorMessage": "string",
"resource": "string",
"status": "string",
"statusCode": 0
}
```

**Uses**: to get the roles of a user in an application.
      


2. /userService/{id}/getUserRolesPermissions

**Method type**: POST

**Input Parameter**:
"id": "string"

**Output JSON**:
```
{
"errorMessage": "string",
"resource": "string",
"status": "string",
"statusCode": 0
}
```
**Uses**: to get the user role permission of a user in an application.
      



      

