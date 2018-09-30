

Customizing IDP may involved supporting a new technology or tool or customising/adding a core feature.

Key steps to add new technology support in IDP:

### IDP UI :  

1.	**Code** –  Add the new technology to the dropdown under one of STANDARD, PACKAGE or MOBILE categories.
2.	**Build** – Build page is varies based on the technology selected. For each technology, separate component should be created for the Build page and respective routing should be added. For example, to add Python technology, build page will have input fields for root directory, build operation to perform etc.
3.	**Deploy** – This section will have input fields required for deployment.
4.	**Test** – Add the new tools for testing to Test section as supported by selected technology and that section will also have input fields required by the specific tool. 


### IDP services 

1. **entities package** – Add entity to map the UI field in entities package. 
2. **restapi package**– For basic requirements, all the REST methods are already there. For specific tool or technology,  specific method created and mapped to it.
3. **businessapi package** – Any business logic related to new method has to be written here.
4. **dataapi package** – Related persistent information for specific tool or technology including the basic pipeline details will be inserted in dataapi. The specific dataapi method will be invoked by businessapi.
5. **utils package** – It will have any utility methods for the specific technology or tool.



### IDP DSL 

For adding new technology or tool, build, deploy and test steps in DSL has to be customized.
1. **Main.groovy** – It is execution starting point for pipeline creation. It will invoke methods of various stages. Eg. build.groovy, test.groovy etc.

2. **Build.groovy** – Based on the technology this file needs to be modified. For example, if the technology is Pega, 
a. It will check if the technology is Pega. If the technology is Pega, it will call specific method for job creation. 
b. Inside Pega.groovy, the steps for configuration of the pipeline will be there.
 
3. **Deploy.groovy** – It will have deployment configuration and it will create deployment job if deployment is supported by the technology.
4. **Test.groovy** – It will create test job and configure it for the provided inputs.
5. **pipeline_sequence** – This file needs to be modified for updating the flow of triggering the pipeline.

### IDP Dashboard
1. **Dashboard package** - It contains REST methods for handling dashboard data insertion in database as well as REST methods for managing data for each of the grafana dashboard panels
2. **DevOpsJsonConv package** - It contains methods to parse each report from Jenkins workspace and to further store all these data in a JSON object.
3. **ReportFetchUtil package** - It contains methods for modifying/retrieving all reports from workspace
4. **MetricsProcessor package** - It contains methods for sending pipeline's data into the postgres database using the REST API of dashboard service

### Custom Plugins

|Sl.No	|PluginName	|Description	|
|-------|---------------|---------------|
|1	|tg-copyslave	|It is used to create slave from the master slave in IDP, called TG_MASTER_SLAVE.	|
|2	|tg-addprojectrole	|It is used to automatically create roles and users in Jenkins and also map the users with the roles|
|3	|tg-credentials|It is used to add credentials.	|
|4	|tg-addnexusrepo|It is used to add Nexus server configuration in Jenkins global configuration.	|
|5	|tg-addartifactory|It is used to add Artifactory server configuration in Jenkins global configuration.	|
|6	|tg-addsshhost|It is used to add SSH server configuration in Jenkins global configuration.	|


## Jenkins 

### Add the custom tools 

1. Go to Manage Jenkins -> Global Tools configuration
2. Click on ‘Custom tool installations’ 
3. Scroll to Add Custom tools and click on that.
4. Enter URL or path of custom tool with required details.
5. When the pipeline is triggered, the custom tool will be downloaded and used.

### Add the plug-ins

1. Go to Manage Jenkins -> Manage Plugins -> Advanced tab
2. For uploading plugins manually click on Upload button or URL can be given, where the plugins are available.



 
