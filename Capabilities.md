IDP OSS version currently supports the CI-CD-CT onboarding of the following technology based applications. 


* Java (ANT and Maven Based)
* DotNet(C# Based)

Below are the key IDP capabilities

### Continuous Integration

IDP generates CI pipelines and scripts that build the application into deployable package while also running code analysis, unit tests, collecting code coverage and finally uploading the deployable package to artifact repositories like Nexus & JFrog Artifactory.

### Continuous Delivery

IDP's pipelines can continuously build, deploy and test the code from multiple SCM branches to multiple environments as per the role based strategy defined for each application.

### Continuous Testing

CI/CD pipelines can be augmented to continuously perform validation of applications from functional testing and non-functional test perspective using popular test tools.

### Pipeline Management

IDP offers self-service mode of creating, copying, editing and deleting pipelines without user having to know anything about the CI-CD tools and scripting. These pipelines are fully parameterized and are reusable across multiple releases, branches and environments. The pipelines can also be triggered based on scheduled intervals.

### Release Management

IDP offers capability to Add, Update and Close releases. These releases will be associated with pipelines. Multiple releases can be added to manage parallel releases of an application/component.

### Role Based Governance

IDP's application and pipeline actions are governed by roles that define permissions for Developer, Release Manager, Environment Owner, QA Owner and other configurable roles.

### Unified Dashboard

IDP's pipelines are instrumented to collect data from every step and this amalgamates into a consolidated dashboard that offers visibility in terms of adoption maturity, build, deployment, test statuses for Developers and Application Owners.


## **Additional Notes**

### Role Based Access

The different roles and permissions in IDP are depicted in the matrix below.

Roles and Privileges |	   Administrator    |   Release Manager	   | Deployment/Environment Owner|       Developer      |
---------------------|:---------------------|:---------------------|:----------------------------|:---------------------|
Create Pipeline	     |  :heavy_check_mark:  |         :x: 	   |           :x: 		 |        :x: 		|	
Copy Pipeline	     |  :heavy_check_mark:  | 	      :x:          | 	       :x:		 | 	  :x: 		|
Edit Pipeline	     |  :heavy_check_mark:  |         :x:	   | 	       :x:		 |  	  :x: 		|
Trigger Build	     |  :heavy_check_mark:  |   :heavy_check_mark: |    :heavy_check_mark:  	 |  :heavy_check_mark:  |
Trigger Deploy	     |          :x:         | 		:x:        |    :heavy_check_mark:       |   :x:  		|
Trigger Test	     |          :x:         | :x: 		   |  :heavy_check_mark:	 |     :x:  		|
Release Management   |          :x:         | :heavy_check_mark:   | :x:  			 |     :x:  		|
View Dashboard	     |  :heavy_check_mark:  |    :heavy_check_mark:|  :heavy_check_mark:         |   :heavy_check_mark: |



## Artifact Management 
Popular artifact repositories like Nexus and JFrog Artifactory are integrated with IDP for artifact management. The artifact repository manager can be configured for artifact management at two levels: 
(a)	Application
(b)	Pipeline

It is important to understand the basic difference between configuring artifact repository at the application creation level and pipeline creation level. 

 **Application level** - If artifact repository is configured while creating application all the pipelines in that application will use the same repository. 

	                  
**Pipeline level** - If it is configured while creating the pipeline, only that pipeline will be able to use that repository and this will override the application level setting.
     

### For upcoming features and releases, [click here](https://github.com/Infosys/openIDP/milestones).



## Create New Application

• Login to IDP using credentials shared by the IDP administrator

![](https://github.com/Infosys/openIDP/blob/master/docs/capabilities_images/login_page.png)
Figure 1 - IDP Login Page

• On successful login, you will be redirected to the history page which would show you a list of pipelines that you had previously created.

Login Page

* Click on ‘Manage’ drop down in the login page and select Application. 
* To create new application click on ‘Create New Application’ button. 

* Enter the user details for developers, pipeline admin and release managers. 
* Create new environment by clicking on ‘Add Env’ button. 
* Configure owners for different environment roles like DB owner, QA owner , deploy and test owner etc as shown in 

![](https://github.com/Infosys/openIDP/blob/master/docs/capabilities_images/manage_application.PNG)
Figure 2 - Manage Application
 


![](https://github.com/Infosys/openIDP/blob/master/docs/capabilities_images/create_app.PNG)
Figure 3 - Grant Access page


![](https://github.com/Infosys/openIDP/blob/master/docs/capabilities_images/create_new_app.PNG)
Figure 4 - Create new application 

![](https://github.com/Infosys/openIDP/blob/master/docs/capabilities_images/env_owners_nexus.PNG)
Figure 5 - Artifact Repository And Configure users for environment 


## Managing Releases

Release Manager has the access for configuring the releases. 

### Create new release 

 1.	Navigate to Release Management portal by choosing Manage -> Releases 
 2.	The ‘Release management portal’ is available for configuring releases
 3.	Select the application name and the pipeline from the pipeline list to which release has to be configured
 4.	Enter the release number, parent release name, expected start and end date
 5.	Enter the additional email ids to be notified for release definition/updates
 6.	Click ‘Add Release’ 
 7.	Active releases can be viewed in the ‘Active Release’ tab and update release details, if any.
 8.	The history of past releases can be seen in ‘Release History’ tab

![](https://github.com/Infosys/openIDP/blob/master/docs/capabilities_images/add_release.PNG)
Figure 6 - Add Release

![](https://github.com/Infosys/openIDP/blob/master/docs/capabilities_images/update_release.PNG)
Figure 7 - Active Releases

![](https://github.com/Infosys/openIDP/blob/master/docs/capabilities_images/active_release.png)
Figure 8 - Release History

## Schedule Pipeline

1.	The scheduler is used to schedule the pipeline to run at configured intervals
2.	The pipeline can be triggered during a specific time slot as scheduled in the scheduler
3.	Click on ‘Schedule job’, in the pipeline view screen
4.	The job can be scheduled to run daily, weekly or monthly
5.	Schedule a time slot in the scheduler and configure the pipeline input parameter values to be used for the execution
6.	The pipeline will be triggered at the scheduled time and the code changes made to the source code repository are 
        checked out, built, packaged and uniquely versioned with release and branch details and uploaded to the artifact repository. This code is then deployed and tested in multiple environments before releasing to production

![](https://github.com/Infosys/openIDP/blob/master/docs/capabilities_images/schedule_job.PNG)
Figure 9 - Pipeline view – Select schedule job

![](https://github.com/Infosys/openIDP/blob/master/docs/capabilities_images/schedule_portal.PNG)
Figure 10 - Schedule Job Portal


## Unified Dashboard

### Application Dashboard:

It shows the overall CI-CD-CT details of each application onboarded in IDP. In this view, user can choose one particular application and based on our selection, specific to that particular application, user will be able visualize following details on the dashboard, aggregated from all pipelines under that application : Total Builds, Total Jobs, Total Successful Builds, Total Failed Builds, Overall application Score, Commit history, Total/Successful/Failed SCM checkouts, Total/Successful/Failed builds, Total/Successful/Failed Deploys, Total/Successful/Failed Tests, as well the trend graph of the before mentioned stages.

![](https://github.com/Infosys/openIDP/blob/master/docs/capabilities_images/application_dashboard.png)
Figure 11 - Application dashboard

### Developer Dashboard:
It shows the results of a pipeline for every execution triggered in IDP. In this view user can choose application, pipeline and build number from the dropdown menu and specific to our selection, we will be able to visualize following details on the dashboard: status/duration of SCM checkouts, status/duration of Build, status/duration of deploy, status/duration of test, along with this it also shows the code coverage details, code analysis details and  code analysis details.

![](https://github.com/Infosys/openIDP/blob/master/docs/capabilities_images/developer_dashboard.png)
Figure 12 - Developer Dashboard









