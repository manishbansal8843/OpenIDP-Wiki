
## Prerequisites:

IDP OSS 1.0.0 is currently supported on Unix based systems and has been tested on RHEL 7.x, Ubuntu 16.x and CentOS 7. The deployment of IDP OSS version is currently supported on a single node environment.


Before setting up IDP in the system, please ensure that the following pre-requisites are met.

### Hardware (minimum requirements):
1. 16GB RAM
2. 200GB HDD
3. 4 CPU cores

### Network:

Following ports need to be opened from the Unix server on which IDP will be installed. If you need to change any ports, you can set the ports in build.sh, present in the repository.

|Services |	Ports|
|:------|:-------|
|postgres|	5432|
|idpsubscription	|8090|
|zookeeper|	2181|
|grafana	|3000|
|keycloak|	8989|
|idpeureka	|8761
|kafka	|9092|
|idpdashboard|	8184|
|idpapp	|8080|
|idpservices|	8889|
|jenkins	|8085|
|Jenkins Slave|	50000|
|idpconfig|8888|
|idpoauth|	8181|
|idpscheduler	|8222|

### Internet connectivity:

Following internet URLs need to be whitelisted for the installation process to complete. In places where corporate firewalls restrict access, proxy details would be required to be configured in the installation script.

|Links|
|:------|
|https://updates.jenkins-ci.org/|
|http://central.maven.org|
|https://updates.jenkins.io|
|http://repo.spring.io|
|https://archive.apache.org|
|https://updates.jenkins-ci.org|
|https://download.docker.com/linux/centos/docker-ce.repo|
|https://auth.docker.io|
|https://registry-1.docker.io|
|https://index.docker.io/|
|https://dseasb33srnrn.cloudfront.net/|
|http://repo1.maven.org|
|https://sourceforge.net|
|http://prdownloads.sourceforge.net|
|https://repo.jenkins-ci.org/|
|https://github.com|
|https://raw.githubusercontent.com|
|https://dist.nuget.org|


### Software:
1. Docker
2. Git

To validate that Docker & Git are installed, execute the below commands which will display the versions of these components.
```
[root@hostname ~]# docker -v
**Docker version 18.06.1-ce, build e68fc7a

[root@hostname ~]# git --version
git version 1.8.3.1
```

### Steps to Install IDP OSS

**Step 1. Cloning repository**
 
```git clone https://github.com/Infosys/openIDP.git```

**NOTE:** While cloning the repository it will ask you for the username and password please provide your credentials to proceed further.
**NOTE:** If you have already cloned the repository/want to update the IDP instance, use ```git pull``` command.

```git clone https://github.com/Infosys/openIDP.git```

**Step 2. Execute build script to install and configure IDP_OSS on your machine.**

Please navigate to the path where the repository is cloned from git.

	
```[root@hostname]# cd /root/IDP_OSS_git/openIDP```

Execute ls –l command to list out the files and folders which are cloned.

	 
![](https://github.com/Infosys/openIDP/blob/master/docs/installation_images/build_script_dir.png)

Next step is to execute the script setup(**build.sh** script)

**NOTE**: Before executing the script there are certain steps that you need to perform manually, please execute the below steps before executing setup script. The configurations are also critical depending on whether you are installing IDP for the first time or upgrading it. Please refer to Additional Notes section at the bottom of the page to understand different configuration options.

1.``` mkdir /root/.m2```

Create above directory where all the cache will be stored.

2.```docker swarm init```

The above command will make sure that the Docker Swarm has been initialized into the system.
After the successful execution of above command you are good to go with setup script.

3.You can mention IP address if you wish to host it with IP address. By default it will take hostname of the system. You can edit the below line in the script (Optional - If hostname is not configured properly, then ip address have to be specified in the script).
export HOSTNAME=$(hostname) change it to export HOSTNAME='ip.of.the.system'

4.```[root@hostname]# sh build.sh```

**Note:** No manual inputs are required from user’s end. After successful completion of the script user will be redirected to terminal prompt.

**Note:** if you want to skip the rebuild or re-deploy your IDP_OSS you can change the value of SKIP_BUILD and REMOVE_OLDER set to true/false

5.To validate all the services and docker containers are up and running, execute the below commands.

```[root@hostname]#docker service list```
  
![](https://github.com/Infosys/openIDP/blob/master/docs/installation_images/docker_service_list_dir.png)

6.```[root@hostname]#docker ps```
 
![](https://github.com/Infosys/openIDP/blob/master/docs/installation_images/docker_ps_dir.png)

To display the containers of different services that are created by Docker to manage various features to manage the IDP application.

7.Once all the services are up and running, you can open a web browser (Chrome/IE) and check the URL by providing your system's host name along with the port for 'idpapp' which is 8080 followed by service name idpapp, if the installation and configuration has been completed without any error, IDP Login page appears.

Eg: http://hostname:8080/idpapp/

![](https://github.com/Infosys/openIDP/blob/master/docs/installation_images/login_page.png)

Try logging with the default username and password. 

Username: **idpadmin**  
Password: **idpadmin@123**

**Note**:
Any new user will have default password as “**firstlogon@idp**”. This password can be changed after first logon.
If hostname details are unavailable, build script has to be modified to replace hostname with ip address

### Additional notes on setup script (build.sh) variables:

The Build Script has environment variables which can help you switch the flow or behaviour of script from default options.

**SKIP_TESTS**<br>
Default Value: true<br>
Allowed Values: true | false<br>
Implications: If set false, will skip the test during build. If set true, then test cases will execute with build section. 
<br>
<br>
**REMOVE_OLDER**<br>
Default Value: true<br>
Allowed Values: true | false<br>
Implications: If set false, will skip the removing older IDP stack from docker. If set true, then script will remove older IDP stack from docker, in case stack is not deployed earlier, then it will just pass.<br><br>

**SKIP_BUILD**<br>
Default Value: false<br>
Allowed Values: true | false<br>
Implications: If set True, will skip the whole build section. Useful if only configuration refresh like IP/hostname update is required.<br><br>

**SKIP_CLOUD**<br>
Default Value: false<br>
Allowed Values: true | false<br>
Implications: If set True, will skip the Cloud Config Server Build Section. If SKIP_BUILD is set true, then this will have no effect<br><br>

**SKIP_EUREKA**<br>
Default Value: false<br>
Allowed Values: true | false<br>
Implications: If set True, will skip the Eureka Server Build Section. If SKIP_BUILD is set true, then this will have no effect<br>

**SKIP_SERVICES**<br>
Default Value: false<br>
Allowed Values: true | false<br>
Implications: If set True, will skip the Services Server Build Section. If SKIP_BUILD is set true, then this will have no effect<br><br>

**SKIP_DSL**<br>
Default Value: false<br>
Allowed Values: true | false<br>
Implications: If set True, will skip the DSL Server Build Section. If SKIP_BUILD is set true, then this will have no effect<br>

**SKIP_UI**<br>
Default Value: false<br>
Allowed Values: true | false<br>
Implications: If set True, will skip the UI Server Build Section. If SKIP_BUILD is set true, then this will have no effect
<br><br>
**SKIP_SUBSCRIPTION**<br>
Default Value: false<br>
Allowed Values: true | false<br>
Implications: If set True, will skip the Subscription Server Build Section. If SKIP_BUILD is set true, then this will have no effect<br>

**SKIP_DASHBOARD**<br>
Default Value: false<br>
Allowed Values: true | false<br>
Implications: If set True, will skip the Dashboard Server Build Section. If SKIP_BUILD is set true, then this will have no effect<br><br>

**SKIP_SCHEDULER**<br>
Default Value: false<br>
Allowed Values: true | false<br>
Implications: If set True, will skip the Scheduler Server Build Section. If SKIP_BUILD is set true, then this will have no effect<br><br>

**SKIP_JENKINS**<br>
Default Value: false<br>
Allowed Values: true | false<br>
Implications: If set True, will skip the Jenkins Server Build Section. If SKIP_BUILD is set true, then this will have no effect<br><br>

**SKIP_TOOLS_CONFIG**<br>
Default Value: false<br>
Allowed Values: true | false<br>
Implications: If set True, will skip the Configuration Section to configure tools for handshake across given hostname.
<br><br>
**LOCAL_M2_CACHE (Recommended)**<br>
Default Value: NA<br>
Allowed Values: "-v <Path_Of_M2_Folder>:/root/.m2/"<br>
Implications: If set, all component build will pool common local M2 cache and will use settings.xml placed in that folder (helpful if you have Nexus server for all resolution)<br><br>

**ANSIBLE_IMAGE**<br>
Default Value: williamyeh/ansible:centos7<br>
Allowed Values: Any docker image having ansible.<br>
Implications: This docker image will be used in configuration stage for configuring stack for handshake on provided hostname. <br><br>

**MAVEN_BUILD_IMAGE**<br>
Default Value: maven:3.5.4-jdk-8-alpine<br>
Allowed Values: Any docker image having maven.<br>
Implications: This docker image will be used in build stage.<br><br>

**ANGULAR_BUILD_IMAGE**<br>
Default Value: alexsuch/angular-cli:6.2<br>
Allowed Values: Any docker image having Angular CLI.<br>
Implications: This docker image will be used in UI build stage.<br><br>

**ARCHIVE_MGMT_IMAGE**<br>
Default Value: alexsuch/angular-cli:6.2<br>
Allowed Values: Any docker image having unzip binaries.<br>
Implications: This docker image will be used in packaging manipulation in DSL build stage.<br><br>

**ARCHIVE_CREATE_IMAGE**<br>
Default Value: kramos/alpine-zip<br>
Allowed Values: Any docker image having zip binaries.<br>
Implications: This docker image will be used in packaging of artifacts as per stack requirements.<br><br>

**WGET_IMAGE**<br>
Default Value: mwendler/wget<br>
Allowed Values: Any docker image having wget binaries.<br>
Implications: This docker image will be used in downloading packages as per stack requirements.<br><br>

**NETWORK_IMAGE**<br>
Default Value: gochain/netstats:0.0.30<br>
Allowed Values: Any docker image having network statistics binaries.<br>
Implications: This docker image will be used in checking network as per stack requirements.<br><br>

**WGET_PROXY**<br>
Default Value: NA<br>
Allowed Values: "-e use_proxy=yes -e http_proxy=http(s)://<username>:<password>@<hostname>:<port> -e https_proxy= http(s)://<username>:<password>@<hostname>:<port> -e ftp_proxy= http(s)://<username>:<password>@<hostname>:<port>"<br>
Implications: If set, all artifact downloads will use this proxy to fetch (helpful if you have Corporate firewall blocking downloads via wget)<br><br>

**PIP_PROXY**<br>
Default Value: NA<br>
Allowed Values: "--proxy http(s)://<username>:<password>@<hostname>:<port>"<br>
Implications: If set, ansible configuration module will use this proxy to fetch required python module (helpful if you have Corporate firewall blocking downloads via pip)<br><br>

**NPM_PROXY**<br>
Default Value: NA<br>
Allowed Values: "npm config set proxy http(s)://<username>:<password>@<hostname>:<port>&&npm config set https-proxy http(s)://<username>:<password>@<hostname>:<port>"<br>
Implications: If set, NPM will use this proxy to fetch required node modules (helpful if you have Corporate firewall blocking downloads via npm)<br>

**HOSTNAME**<br>
Default Value: $(hostname)<br>
Allowed Values: Hostname/IP Address of your system (Docker Master)<br>
Implications: By default, it will record your systems hostname for component handshake. If your system has some issue with DNS resolution of own hostname, its recommended set this variable to IP address of your system.<br><br>
