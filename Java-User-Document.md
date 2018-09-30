# Complete working of a Java pipeline

## Basic Info Page
### *Pipeline* Creation

Select the Application Name under which the `Pipeline` has to be created. Give a unique name for the `Pipeline`. Select the Build Server OS on which the `Pipeline` will be executed.

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/basic_info.png)

Figure 1: Basic Info Page-Pipeline Details

### Additional Mail Recipients

This is an optional section where user can choose to send email notifications to selected team members. Email can be sent to all the team members mentioned in the application by selecting **All Application Users** option. Click **Continue** Button to navigate to the next page or Click **Reset** Button to reset the contents of the current page.

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/additional_mail_recipients.png)

Figure 2: Basic Info- Additional Mail Recipients
 

## CODE Info Page
### Technology And SCM Details
 
![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/code_info.png)
	
Figure 3: Code Page - Technology & SCM Details


Select the technology [Java/J2EE (Maven Based)/ Java/J2EE(ANT Based)]. Then configure the SCM tool used in the project. Select the SCM to download the source code. The three types of SCM’s supported – GIT, MS TFS and SVN. In IDP, we can add multiple repositories. Choose the options(Application code, Deploy Scripts, Test Scripts) depending on what each repo contains.


_**Using GIT**_:

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/git_scm.png)

For example: If GIT is chosen, then add the repository URL, Username and Password along with default branch name. 
Select "include directories explicitly" option and mention directories. Select Repository Browser and its corresponding fields. Provide Proxy Details if required to connect to the repo.


_**Using MICROSOFT TEAM FOUNDATION SERVER**_:
If MS TFS is chosen, then give TFS Server URL, the path of the Project and User credentials.

_**Using SVN**_:
If SVN is chosen, then give Repository URL, User credentials.


## Custom Build Actions
This facilitates the custom build actions that needs to be performed before or after the build operations.

 
![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/postbuild_prebuild.png)

Figure 4: Code Page- Custom Build Actions

**Pre Build**

Any action that needs to be performed before a build action is configured here. Select the Pre Build action. This platform supports ANT Script, Shell Script and Batch Script. Enter the path of the Script file. If ANT script is selected enter the targets. (Ex: init, compile)

**Post Build**

Any action that needs to be performed after build action is configured here.
Select the Post Build action. This platform supports ANT Script, Shell Script and Batch Script. Enter the path of the Script file. If ANT script is selected enter the targets. (Ex: init, compile). Click on CONTINUE Button to navigate to the next page.

**Additional Pipeline Parameters**

Pipelines can be defined with parameters as these parameters control what the pipeline does. The parameter type can be either string or password type. The parameter of the type password is encrypted. Provide any name to Parameter and give the value also. Static can be selected if the user does not want to change the parameter value at trigger time.
	To change the parameter value at trigger time, then the static checkbox need not be selected and this parameter value can be provided in the input box of the trigger page. These parameters can be used in the build phase of the pipeline. For example, jar version in Maven project will be varying and it can be passed as a parameter which is defined in pom.xml.

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/additional_pipeline.png)


## BUILD Info Page

This page provides the list of operations that can be integrated to the build pipeline, which can be scheduled along with the build operations.

**Build Info Page(Maven Based)**




![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/maven_project%20_details.png)
			
Figure 5: Build Page- Maven Project Details


Provide the Maven Project Name on which various build/testing operations need to be performed. Enter the relative path to the root POM. If the project is multi module (Multiple maven projects within a single parent), select that option. Select the Global goals if needed: 

**Clean**: Deletes the output of a build by deleting the build directory of earlier created files.

**Install**: Installs the package in local/remote maven repository.
Enter other custom goals and MAVEN OPTS if required.

Note: There is also an option(sub-modules) to select specific modules in a Maven multi-module project while building. We can also set default module.

### Build Operations
Select **Compile** to compile the project.

***Code Analysis***

Select the Code Analyzing tools(**Sonar**/**PMD**/**CheckStyle**/**FindBugs**) to run rules for static code analysis for Maven Project. Any number of tools can be selected for code analysis. Select Compile option to enable FindBug functionality.

***Unit Testing***

The selection of Unit testing checkbox ensures the execution of JUnit test cases that are present in the project.

***Code Coverage***

The selection of Code Coverage checkbox ensures the coverage of JUnit test cases that are present in the project using Cobertura. This option can be enabled only if Unit Testing is selected. Click on CONTINUE Button to navigate to the next page

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/build_operations.png)

Figure 6: Build Page- Build Operations

**Build Info Page(ANT Based)**

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/ant_module_details_1.png)
![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/ant_modules_details_2.png)

This provides the list of operation that can be integrated to the build job, which can be scheduled along with the build operations.Provide the ANT Module Name upon which various build/testing operations need to be performed and also provide relative path to the source code directory.

_**Build through Custom Build XML**_

If this is selected then all the other options except Code Analysis are disabled, else they are enabled. Provide the relative path to custom build file and ANT targets to execute. 


***Code Analysis***

Select the Code Analyzing tools(**Sonar**/**PMD**/**CheckStyle**/**FindBugs**) to run rules for static code analysis for ANT Project. Any number of tools can be selected for code analysis. Select Compile option to enable FindBug functionality.


***Unit Testing***

The selection of Unit testing checkbox ensures the execution of JUnit test cases that are present in the project.

***Code Coverage***

The selection of Code Coverage checkbox ensures the coverage of JUnit test cases that are present in the project using Cobertura. It can be selected only if Unit Testing is selected. Click on CONTINUE Button to navigate to the next page


**JAR** and **WAR** packaging can be done only if the code is compiled. 

_**JAR Packaging**_

The two types of modules are Java module and EjB module. If Java module is selected for JAR packaging then provide path of main class. If EJB Module is selected, EJB descriptors (path of the xml file) should be provided.

_**WAR Packaging**_

For WAR packaging provide web.xml file. 

_**Default Module**_

If Default module is selected then default modules present in the application will be automatically checked in the trigger page.

_**EAR Packaging**_

For EAR packaging, select Java/EJB modules or Web modules from the drop down. 

_**Post Build Module**_

 ![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/post_build_module.png)

Figure 7: Build Page – Post Build Module

Any action that needs to be performed after a build action is configured here. Select the PostBuild action from the dropdown. It can be an ANT Script, a Batch Script, a PowerShell Script or a Shell Script. Provide the path of the Script file. If ANT script is selected enter the targets. (Ex: deploy, test) and path of archive logs.

_**Overwrite Artifact Repository Details**_

Artifact Repository details can be updated, if there is any change in the repository details which has been provided while creating application. The build files which has to be staged has to be given in Artifact pattern using | as seperator

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/overwrite_staging1.PNG)

Figure 8: Build Page – Overwrite Artifact Repository

Click on **CONTINUE** button to navigate to the next page





 

## DEPLOY Info Page

### **Deploy Information**

Select the environment to which deployment has to happen. It has the capability of adding one or more deploy steps according to the need of deployment. For Java, deployment to containers like Tomcat and Websphere is supported.

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/deployment_configuration_info.png)

Figure 9: Deploy Page

___**Add Deploy Step**___

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/deployment_configuration_info%20(2).png)

Click on Add deploy Step button at the top-right corner to provide the deployment details for a particular environment. If username and password for running deploy script is required, it can be passed as Admin username and password. If credentials are required for authenticating an application, then Application username and password can be provided.
Give the Step Name.Provide Admin username,password,Application username and password if applicable. Select Run scripts if required.It provides an option of ANT Script, Shell Script, Batch Script, PowerShell Script and SSH Execution.
If Deploy to container is selected, choose the application server from the options:

**_Using TOMCAT_**

Provide the Server Manager URL, path of WAR/EAR file relative to the checkout path, Context path for the application that has to be deployed and the credentials.

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/tomcat_deployment.png)
 
Figure 10: Deploy Page – Deploy to Container - Tomcat

**_USING WebSphere_**

Provide the WebSphere IP/DNS, path of WAR/EAR file relative to the checkout path. SOAP port to connect to IBM WebSphere Application Server. Enter the Target Cell Name, Target Node Name, Target Server Name where the application that has to be deployed and User credentials.

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/websphere_deployment.PNG)

Figure 11: Deploy Page – Deploy to Websphere

## TEST Info Page

### Test Information

Select the environment to which testing has to happen. It has the capability of adding one or more test steps according to the need of testing.
![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/test_operation_info.png)
 
Figure 12: Test Page

**Add Test Step**

Click on Add Test Step button at the top-right corner to provide the test details for a particular environment and provide the Step Name. Select either Run scripts or Test tool. If Run Scripts is selected, it provides an option of executing ANT Script, Shell Script, Batch File, Powershell Script and SSH Execution.

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/test_operations_info_run_scripts.png)
 
Figure 13: Test Page – Run Scripts selected
 

**Select Test Tool**

Provide the Test Category (Functional/Performance/Service).

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/test_tools.png)
 
Figure 14: Test Page – Test Tool selected
 

## Functional Testing


![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/functional_testing.png)

Figure 15: Test Page – Functional Category selected


_**Selenium**_:
Provide the URL of the Application, project path and select the Framework(Junit/TestNG). Provide source path and selenium Test Suite file which has to be executed. If external libraries have to be added, then enable 'Include External Libraries' option and provide the directory containing external libraries.
	
_**SAHI**_:
Provide the SAHI Test Suite path, Test URL and select the browser in which this URL has to open to run the Test Suites.


## Performance Testing
 
![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/performance_testing.png)

Figure 16: Performance test selected

_**Using Jmeter**_:
Provide the path of the test plan which has to be executed and the property file if required.


## Service Testing
 
![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/service_testing.png)
Figure 17: Service testing selected


_**SOAPUI**_:
Provide the name of the project and location which contains Soap UI Test Suite, then give the name of the Test Suite which has to be executed.

_**PARASOFT SOA**_:
	Provide the name of the project containing Parasoft SOA Test, name of the Parasoft SOA Test project location which has to be executed, name of the Test Suite which has to be executed and name of the test configuration.

 

## Submitting The Pipeline

Click on Submit button to create/edit/copy a pipeline. Below screen appears once the configuration creation is successful.
 
![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/build_details.png)

Figure 18.a : Success Page- Project Details

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/deploy_details.png)

Figure 18.b : Success Page- Deploy Details

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/test_details.png)

Figure 18.c : Success Page- Test Details

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/slave_label_details.png)
 
Figure 18.d : Success Page- Pipeline agent Details

## Prerequisites

### SCM

**GIT:**

 Git client should be installed on the build machine and the path of the git.exe should be added in system level environment GIT_HOME and system PATH variable. 
Ex. (PATH=C:/Program files/GIT/bin). It can be installed for Linux also.
For more reference on how to install GIT refer - https://www.atlassian.com/git/tutorials/install-git

**TFS:**

TFS client (Visual Studio Team Explorer) should be installed on the build machine and the path of the tfs.exe should be added in the system PATH variable.

**SVN:**

SVN client should be installed on the build machine and the path of the svn.exe should be added in the system PATH variable.

**Java ANT Build:**

* Java jdk has to be installed in the respective build machine by setting JAVA_HOME to the jdk directory in the machine. For ex. C:\Program Files\Java\jdk1.8.0_141 and add it in path variable as
C:\Program Files\Java\jdk1.8.0_141\bin.
* ANT_HOME has to be set to <D:\apache-ant-1.9.6-bin\apache-ant-1.9.6> and add it in path variable as %ANT_HOME%/bin
* For Code Analysis using Sonar: Sonar server and Sonar scanner setup is required. SONAR_SCANNER_HOME has to be set, and in SONAR_SCANNER_Installation_dir/conf/sonar_scanner.properties has to point to correct sonar server url. It is done through property sonar.host.url= ht<span>tp://</span>sonarserverName:port

**Java Maven Build:**

* Java jdk has to be installed in the respective build machine by setting JAVA_HOME to the jdk directory in the machine. For ex. C:\Program Files\Java\jdk1.8.0_141 and add in path variable like 
C:\Program Files\Java\jdk1.8.0_141\bin.
* MAVEN_HOME has to be set and added in path variable as well
*For code analysis using Sonar, dependencies have to be added in pom.xml and Sonar server url has to be provided in M2_HOME/settings.xml

**Testing:**

**_Performance Jmeter Testing_**

JMETER_HOME has to be set and added in path variable.

**_Service SOAPUI Testing:_**

SOAPUI_BIN and SOAPUI_HOME has to be set pointing to <D:\SoapUI-5.0.0\bin> and added in path variable.

**_Functional SAHI Testing:_**

SAHI_HOME has to be set pointing to <D:\sahi\userdata\bin> and added in path variable
For SAHI installation and configuration, **refer SAHI Usage document**.

_For Running jenkins slave, JAVA_HOME is necessary_


 

## Triggering The Pipeline

* Release has to be added to a pipeline, before triggering the pipeline. Refer [Capabilities](https://github.com/krishnakanthbn/IDP_OSS/wiki/Capabilities).
* Slave should be launched first in proper build machine.
* Select pipeline from previous configuration page.  Trigger Page will open. Select the Release number. 
* Select either or all the options from build/deploy/test as per the requirement. 
* If Build is checked, then select the modules required for build operation. 
* If Deploy is checked, then select the build/deploy slave and the environment where the application has to be deployed. 
* If test is checked, then select and submit to trigger the pipeline. 


![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/trigger_pipeline.png)
![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/trigger_pipeline_2.png)


## Stage View

Stage View Page of Jenkins can be viewed after clicking on the following:

* Pipeline Name on History page.

* Submit button on trigger page.

### Pipeline Name on History page
 
![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/stageview_1.png)
When the user clicks on the blue link shown above, the stageview page of Jenkins appears as shown below.

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/stageview_2.png)
 
### Submit button on trigger page
 
![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/stageview_3.png)

On click of submit button, if the trigger is successful then stage view appears as shown below .

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/stageview_4.png)

From here the user can check the status of build and cancel a build.
