h2-console: Example Using the H2 Console with JBoss
===================================================
Author: Pete Muir  
Level: Beginner  
Technologies: H2  
Summary: Shows how to use the H2 console with JBoss EAP  
Target Product: EAP  
Product Versions: EAP 6.1, EAP 6.2  
Source: <https://github.com/jboss-developer/jboss-eap-quickstarts/>  

What is it?
-----------

JBoss EAP bundles H2 as an in-memory, in-process database. H2 is written in Java so can run on any platform JBoss EAP runs.

This is quickstart shows you how to use the H2 console with Red Hat JBoss Enterprise Application Platform. It uses the `greeter` quickstart as a GUI for entering data.

_Note: This quickstart uses the H2 database included with JBoss EAP 6. It is a lightweight, relational example datasource that is used for examples only. It is not robust or scalable and should NOT be used in a production environment!_

System requirements
-------------------

The application this project produces is designed to be run on Red Hat JBoss Enterprise Application Platform 6.1 or later. 

All you need to build this project is Java 6.0 (Java SDK 1.6) or later, Maven 3.0 or later.
 

Configure Maven
---------------

If you have not yet done so, you must [Configure Maven](https://github.com/jboss-developer/jboss-developer-shared-resources/blob/master/guides/CONFIGURE_MAVEN.md#configure-maven-to-build-and-deploy-the-quickstarts) before testing the quickstarts.


Prerequisites
-----------

This quickstart depends on the deployment of the 'greeter' quickstart. Before running this quickstart, see the [greeter README](../greeter/README.md) file for details on how to deploy it.

You can verify the deployment of the `greeter` quickstart by accessing the following URL: <http://localhost:8080/jboss-greeter> 


Deploy the H2 Console
------------------------

This quickstart comes bundled with a version of the H2 Console built for JBoss EAP. The changes that have been made to the stock console are described below. 

Deploy the console by copying the `QUICKSTART_HOME/h2-console/h2console.war` to the `$JBOSS_HOME/standalone/deployments` directory. 


Access the H2 Console 
---------------------

You can access the console at the following URL:  <http://localhost:8080/h2console>.

You need to enter the JDBC URL, and credentials. To access the "test" database that the `greeter` quickstart uses, enter these details:

* JDBC URL: `jdbc:h2:mem:greeter-quickstart;DB_CLOSE_ON_EXIT=FALSE;DB_CLOSE_DELAY=-1`
* User Name: `sa`
* Password: `sa`

Click on the *Test Connection* button to make sure you can connect. If you can, go ahead and click *Connect*.

Investigate the H2 Console
-------------------------

Take a look at the data added by the `greeter` application. Run the following SQL command:

        select * from users;

You should see the two users seeded by the `greeter` quickstart, plus any users you added when testing that application.


Changes to the H2 Console for JBoss EAP
----------------------------------------

To make the H2 console run on JBoss EAP, the H2 libraries were removed from the WAR and a dependency on the H2 module was added to the META-INF/MANIFEST.MF fle. The rebuilt console is provided with this quickstart.


Server Log: Expected warnings and errors
-----------------------------------

_Note:_ You will see the following warnings in the server log. You can ignore this warning.

        JBAS018568: Deployment "deployment.h2console.war" is using an unsupported module ("com.h2database.h2:main") which may be changed or removed in future versions without notice.


