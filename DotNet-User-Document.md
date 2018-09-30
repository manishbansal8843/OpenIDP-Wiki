# Complete working of a DotNet pipeline

## BASIC Info Page

### Pipeline Creation 

Select the Application Name under which the `Pipeline` has to be created. Give a unique name for the `Pipeline`. Select the Build Server OS on which the `Pipeline` will be executed.

![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/basic_info.png)
 

Figure 1: Basic Info Page-Pipeline Details



### Additional Mail Recepients

This is an optional section where user can choose to send email notifications to selected team members. Email can be sent to all the team members mentioned in the application by selecting **All Application Users** option. Click **Continue** Button to navigate to the next page or Click **Reset** Button to reset the contents of the current page.

![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/additional_mail_recipients.png)
 

Figure 2: Basic Info- Additional Mail Recipients


## CODE Info Page
### Technology and SCM Details

 
![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/code_info.png)

Figure 3: Code Page - Technology & SCM Details


Select the technology [.NET (C# based)]. Then configure the SCM tool used in the project. Select the SCM to download the source code. The three types of SCM’s supported – GIT, MS TFS and SVN. In IDP, we can add multiple repositories. Choose the options(Application code, Deploy Scripts, Test Scripts) depending on what each repo contains.


_**Using GIT**_:
If GIT is chosen, then add the repository URL, Username and Password along with default branch name. 
Select "include directories explicitly" option and mention directories. Select Repository Browser and its corresponding fields.

_**Using Microsoft Team Foundation Server**_:
If MS TFS is chosen, then give TFS Server URL, the path of the Project and User credentials.

_**Using SVN**_:
If SVN is chosen, then give Repository URL, User credentials.

## Custom Build Actions

This facilitates the custom build actions that needs to be performed before or after the build operations.

 ![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/postbuild_prebuild.png)

Figure 4: Code Page- Custom Build Actions




### Pre Build Action

Any action that needs to be performed before a build action is configured here. Select the Pre Build action. This platform supports ANT Script, Shell Script and Batch Script. Enter the path of the Script file. If ANT script is selected enter the targets. (Ex: init, compile)

### Post Build Action

Any action that needs to be performed after build action is configured here.
Select the Post Build action. This platform supports ANT Script, Shell Script and Batch Script. Enter the path of the Script file. If ANT script is selected enter the targets. (Ex: init, compile). Click on CONTINUE Button to navigate to the next page.

### Additional Pipeline Parameters

Pipelines can be defined with parameters as these parameters control what the pipeline does. The parameter type can be either string or password type. The parameter of the type password is encrypted. Provide any name to Parameter and give the value also. Static can be selected if the user does not want to change the parameter value at trigger time. To change the parameter value at trigger time, then the static checkbox need not be selected and this parameter value can be provided in the input box of the trigger page. These parameters can be used in the build phase of the pipeline. 

![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/additional_pipeline.png)

## BUILD Info Page

This provides the list of operation that can be integrated to the build job, which can be scheduled along with the build operations.

![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/build_info_msbuild.png)

Figure 5: Build Page- .NET Solution




Provide the Solution Name. The user can select either the default MS Build Version or any other version from the dropdown. Provide the path of the solution file and give the MS Build Arguments as debug or Deploy On Build configuration according to the requirement.

_**NUnit**_

NUnit, which is the open source unit testing framework for DotNet Applications can be selected in order to test by giving the path of NUnit project path relative to root folder.




_**Code Analysis**_

The selection of code analysis checkbox ensures tools are run for static code analysis. The user can choose either Sonar or Fxcop. To perform code analysis using Sonar, user should have configured Sonar server and the URL of that server should be provided along with User credentials. 



![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/build_page.png)

 
Figure 6: Build Page- Code Analysis


_**Unit Testing**_

The selection of Unit testing checkbox ensures the execution of test cases that are present in the project.

_**Code Coverage**_

Code Coverage option can be selected only if Unit Testing is selected.

_**Default Module**_


Default module which has to be taken for build can be specified in this section. If not, module that has to be taken for build has to be selected while triggering the pipeline.




_**Post Build Module**_

 ![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/post_build_module.png)

Figure 7: Build Page – Post Build Module

Any action that needs to be performed after a build action is configured here. Select the PostBuild action from the dropdown. It can be an ANT Script, a Batch Script, a PowerShell Script or a Shell Script. Provide the path of the Script file. If ANT script is selected enter the targets. (Ex: deploy, test) and provide the path of archive logs.


_**Staging**_

![](https://github.com/Infosys/openIDP/blob/master/docs/java_pipeline_images/overwrite_staging1.PNG)

Figure 8: Staging

To overwrite Artifact Repository Manager, select Artifact Repository Manager (Nexus/JFrog Artifactory). User can overwrite and update the repository details at pipeline level.  NA option can be chosen if the user wishes not to upload artifacts for the particular pipeline and the artifacts will not be uploaded to the Nexus.



## DEPLOY Info Page

Select the environment to which deployment has to happen. It has the capability of adding one or more deploy steps according to the need of deployment. .Net applications can be deployed to IIS container.
![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/deploy_info_page.png)
 
Figure 9: Deploy Page 

_**Run Script**_
			
Different type of scripts are - ANT Script, PowerShell Script, Batch Script, SSH Execution or Shell Script. Provide the respective details.



_**Deploy to Container**_

For deploying the DotNet applications, IIS server is used as the container. Provide the project path, IIS Machine name, IIS User credentials.


## TEST Info Page

Select the environment to which testing has to happen. It has the capability of adding one or more test steps according to the need of testing.

**Test Operations**

Click on Add Test Step button at the top-right corner to provide the test details for a particular environment and provide the Step Name. Select either Run scripts or Test tool. If Run Scripts is selected, it provides an option of ANT Script, Shell Script, Batch Script, Powershell Script and SSH Execution.

![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/test_operations_info_run_scripts.png)
 

Figure 10: Test Page


**Select Test Tool**

Provide the test category (Functional/Performance/Service).

![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/test_tools.png)

Figure 11: Test Page – Test Tool selected




### Functional Tests

![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/functional_testing.png)

Figure 12: Test Page – Functional Category selected


For Functional Test Category there are two tools available – SAHI and Selenium.

_**SAHI**_

Provide the SAHI Test Suite path, Test URL and select the browser in which this URL has to open to run the Test Suites.


_**Selenium**_

Provide the URL of the Application, project path and select the Framework(Junit/TestNG). Provide source path and selenium Test Suite file which has to be executed. If external libraries have to be added, then enable 'Include External Libraries' option and provide the directory containing external libraries.
	

### Performance Tests

![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/performance_testing.png)

Fig 13: Test Page – Performance Test Category


Under Performance category, the two types of Tools supported are – Jmeter and MSLoadTest.

_**Using Jmeter**_:

Provide the path of the test plan which has to be executed and the property file if required.

_**Using MSLoadTest**_:
	
Provide the path of project containing the MS Load Test Suite with proper extension, MS Build arguments, MS Load Test name having .loadtest extension and Test category which has to be executed.









### Service Tests

![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/service_testing.png)
 
Fig 14: Test Page – Service Test Category

Under Service Category, Saop UI and Parasoft SOA Test Tools are supported.
    
_**SOAPUI**_:
Provide the name of the project and location which contains Soap UI Test Suite, then give the name of the Test Suite which has to be executed.

_**PARASOFT SOA**_:
Provide the name of the project containing Parasoft SOA Test, name of the Parasoft SOA Test project location which has to be executed, name of the Test Suite which has to be executed and name of the test configuration.


## Submitting the Pipeline

Click on Submit button to create/edit/copy a pipeline. Below screen appears once the configuration creation is successful.


![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/build_details.png)
 
Figure 14-a:  Success Page- Project Details


 			
![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/deploy_details.png)

Figure 14-b : Success Page- Deploy Details





![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/test_details.png) 
 
Figure 14-c : Success Page- Test Details



![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/slave_label_details.png)
 
Figure 14-d:  Success Page- Slave Details

## Prerequisites

### SCM

**GIT:**
Git client should be installed on the build machine and the path of the git.exe should be added in system level environment GIT_HOME and in system PATH variable as well. 
Ex. (PATH=C:/Program files/GIT/bin). It can be installed for Linux also.
For more reference on how to install GIT refer - https://www.atlassian.com/git/tutorials/install-git

**TFS:**
TFS client (Visual Studio Team Explorer) should be installed on the build machine and the path of the tfs.exe should be added in the system PATH variable.

**SVN:**
SVN client should be installed on the build machine and the path of the git.exe should be added in the system PATH variable

**.Net Build:**

* MSTEST_HOME has to be set pointing visual Studio Code as C:\Program Files\Microsoft Visual Studio 12.0\Common7\IDE 
* To analyze code with fxcop, add C:\Program Files\Microsoft Visual Studio 12.0\Team Tools\Static Analysis Tools\FxCop in path variable and for building .net Solution add C:\Program Files\MSBuild\12.0\Bin as well in path variable

**Testing:**

**_Performance Jmeter Testing_**

JMETER_HOME has to be set and added in path variable.

**_Service SOAPUI Testing:_**

SOAPUI_BIN and SOAPUI_HOME has to be set pointing to <D:\SoapUI-5.0.0\bin> and added in path variable.

**_Functional SAHI Testing:_**

SAHI_HOME has to be set pointing to <D:\sahi\userdata\bin> and added in path variable
For SAHI installation and configuration, **refer SAHI Usage document**.



## Triggering The Pipeline

* Release has to be added to a pipeline, before triggering the pipeline. Refer [Capabilities](https://github.com/krishnakanthbn/IDP_OSS/wiki/Capabilities).
* Slave should be launched first in proper build machine.
* Select pipeline from previous configuration page.  Trigger Page will open. Select the Release number. 
* Select either or all the options from build/deploy/test as per the requirement. 
* If Build is checked, then select the modules required for build operation. 
* If Deploy is checked, then select the build/deploy slave and the environment where the application has to be deployed. 
* If test is checked, then select and submit to trigger the pipeline. 


![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/trigger_pipeline.png)
![](https://github.com/Infosys/openIDP/blob/master/docs/Trigger%20pipeline/DotNetFig2.png)

## Stage View

Stage View Page of Jenkins can be viewed after clicking on the following:

* Pipeline Name on History page.

* Submit button on trigger page.

### Pipeline Name on History page
 
![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/stageview_1.png)
When the user clicks on the blue link shown above, the stageview page of Jenkins appears as shown below.

![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/stageview_2.png)
 
### Submit button on trigger page
 
![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/stageview_3.png)

On click of submit button, if the trigger is successful then stage view appears as shown below .

![](https://github.com/Infosys/openIDP/blob/master/docs/dotnet_pipeline_images/stageview_4.png)

From here the user can check the status of build and cancel a build.





