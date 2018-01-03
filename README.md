Sample Web Application Example
===============================
Author: Eric Getchell   
Level: Beginner  
Technologies: Tomcat, Servlet, OpenShift, JBoss Developer Studio  
Summary: The `helloworld` quickstart demonstrates importing of a simple web application into JBoss Developer Studio, deploying on a local Tomcat instance, and then leveraging Source 2 Image to seamlessly deploy the web application as a Docker image into OpenShift  
Target Product: JBoss JWS, OpenShift, JBoss Developer Studio  
Source: <https://github.com/egetchel/SampleWebApp/>  

What is it?
-----------

Demonstrate portability between containerized and non-containerized runtimes with a sample Tomcat application.  Learn how to leverage Source 2 Image (S2I for containerizing existing applications)


System requirements
-------------------

The application this project produces is designed to be run with JBoss Developer Studio, Openshift (or Container Development Kit), and either the Tomcat that ships with JBoss Web Server or community Tomcat.

You will need Java 8.0 (Java SDK 1.8) or later and Maven 3.1.1 or later, JBoss Developer Studio 10 and Tomcat 7.


Install JBoss Developer Studio
---------------

In the following instructions, replace `EAP7_HOME` with the actual path to your JBoss EAP installation. The installation path is described in detail here: [Use of EAP7_HOME and JBOSS_HOME Variables](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/USE_OF_EAP7_HOME.md#use-of-eap_home-and-jboss_home-variables).

Import the Project
-------------------------

* From the Project Explorer menu, right-click and select "Import"
* Select "Project from Git (with smart import)" and hit Next

![import](/images/import-git.png)
* Select "Clone URI" and hit Next
* Enter the repository URL to import and hit Next
![import](/images/import-git-repo-location.png)
* Make sure the SampleWebApp is selected and hit Finish
![import](/images/import-specify-resources.png)

Install and Register Tomcat Server with JBoss Developer Studio
-------------------------
* Install JBoss Web Server 3 or Apache Tomcat.
* Create a new Server instance.  In the Servers tab towards the bottom of the screen, click the link to create a new server. If one already exists, right-click and select "New" -> "Server"
![create](/images/create-new-server.png)
* In the Apache section, select Tomcat v7.0 Server and select "Next"
![create](/images/create-tomcat-instance.png)
* If an existing Tomcat runtime environment is not available, JBDS will ask for the installation location.  Select "Browse" and navigate to the root install folder and select "Next"
![create](/images/create-tomcat-install-directory.png) 
* In the Add and Remove window, add the SampleWebApp to the Tomcat server and select "Finish"
![create](/images/create-add-web-app.png)

The server should now show in the Servers tab at the bottom of the screen.


Start the JBoss EAP Server
-------------------------

1. Open a command prompt and navigate to the root of the JBoss EAP directory.
2. The following shows the command line to start the server:

        For Linux:   EAP7_HOME/bin/standalone.sh
        For Windows: EAP7_HOME\bin\standalone.bat

 
Build and Deploy the Quickstart
-------------------------

1. Make sure you have started the JBoss EAP server as described above.
2. Open a command prompt and navigate to the root directory of this quickstart.
3. Type this command to build and deploy the archive:

        mvn clean install wildfly:deploy

4. This will deploy `target/jboss-helloworld.war` to the running instance of the server.


Access the application 
---------------------

The application will be running at the following URL: <http://localhost:8080/jboss-helloworld>. 


Undeploy the Archive
--------------------

1. Make sure you have started the JBoss EAP server as described above.
2. Open a command prompt and navigate to the root directory of this quickstart.
3. When you are finished testing, type this command to undeploy the archive:

        mvn wildfly:undeploy


Run the Quickstart in Red Hat JBoss Developer Studio or Eclipse
-------------------------------------
You can also start the server and deploy the quickstarts or run the Arquillian tests from Eclipse using JBoss tools. For general information about how to import a quickstart, add a JBoss EAP server, and build and deploy a quickstart, see [Use JBoss Developer Studio or Eclipse to Run the Quickstarts](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/USE_JBDS.md#use-jboss-developer-studio-or-eclipse-to-run-the-quickstarts) 


Debug the Application
------------------------------------

If you want to debug the source code of any library in the project, run the following command to pull the source into your local repository. The IDE should then detect it.

        mvn dependency:sources

