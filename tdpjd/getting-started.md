To develop a Java application that connects to Oracle Database 12c Release 2 (12.2), you must ensure that certain components are installed as required. This chapter covers the following topics:

- What You Need to Install

- Verifying the Oracle Database 12c Release 2 (12.2) Installation

- Installing Oracle JDeveloper or any Java IDE (Eclipse, NetBeans, Intellij)

### What You Need to Install

To be able to develop the sample application, you need to install the following products and components:

- Oracle Database 12c Release 2 (12.2)

- J2SE or JDK

- Apache Maven

- JDeveloper IDE

- Web Server (Tomcat)

- Oracle Database 12c Release 2 (12.2)

  To develop the Java web application, you need a working installation of Oracle Database 12c Release 2 (12.2) server with the HR schema, which usually comes with the database. There are two ways you can install the Oracle Database 12c Release 2 (12.2).

  Oracle Database Services on Cloud

  The Oracle Database Services on Cloud offer access to a single Oracle Database with Oracle providing the computing power, physical storage, and tools for maintenance and management operations. You can get access to a working database in just a few minutes. After creating an instance of the database on the Oracle cloud, you will have full access to the features and the operations available with the Oracle Database excluding the EECS option.

  Oracle Cloud gives you the flexibility to start at a cost and level suitable to your needs. Later, you can adapt with your changing requirements.

  You can login to Database Cloud Services page to review various options available and to sign-up. Some of the options are listed here for easy reference:

  Oracle Database Cloud Service (DBCS)

  Oracle Database Cloud Service on Oracle Cloud Infrastructure (CS)

  Oracle Database Exadata Express Cloud Service (EECS) - Fully Managed

  Oracle Database Exadata Cloud Service (ExaCS)

  Oracle Database Exadata Cloud Machine (ExaCM)

  Create an account in the Oracle Database Cloud Service (DBCS). This will give you access to HR schema as well.
  **Note:**

  [Using Java Applications and IDEs with Oracle Database Cloud Service(DBCS)](http://www.oracle.com/technetwork/database/application-development/jdbc/documentation/default-3396167.html) OTN page provides instructions to create a database instance and also try to connect to it using JDBC and UCP code samples provided in the beginning of the guide
  Step 1:

  Oracle Database Installation Available on OTN

  As an alternative option, Oracle Database 12c Release 2 can also be installed on premise. Follow the links to install Oracle Database and check out the release notes.

- [Oracle Database 12c Release 2 for Linux](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/oracle12c-linux-12201-3608234.html)

- [Oracle Database 12c Release 2 for Windows](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/oracle12c-windows-3633015.html)

  **Note:**

  Download JDK 8 — a Java Development Kit (JDK 8) to create and compile Java applications. Refer <http://www.oracle.com/technetwork/java/javase/downloads/index.html> for more information about installing Java.
  Refer <http://www.oracle.com/technetwork/java/overview-141217.html> for information about the JDBC API.

#### Oracle Database 12c Release 2 (12.2)

To develop the Java application, you need a working installation of Oracle Database 12c Release 2 (12.2) Server with the `HR` schema, which comes with the database. The installation creates an instance of Oracle Database 12c Release 2 (12.2) and provides additional tools for managing this database.

Oracle Database Services on Cloud

The Oracle Database Services on Cloud offer access to a single Oracle Database with Oracle providing the computing power, physical storage, and tools for maintenance and management operations. You can get access to a working database in just a few minutes. After creating an instance of the database on the Oracle cloud, you will have full access to the features and the operations available with the Oracle Database excluding the EECS option.

Oracle Cloud gives you the flexibility to start at a cost and level suitable to your needs. Later, you can adapt with your changing requirements.

You can login to Database Cloud Services page to review various options available and to sign-up. Some of the options are listed here for easy reference:

Oracle Database Cloud Service (DBCS)

Oracle Database Cloud Service on Oracle Cloud Infrastructure (CS)

Oracle Database Exadata Express Cloud Service (EECS) - Fully Managed

Oracle Database Exadata Cloud Service (ExaCS)

Oracle Database Exadata Cloud Machine(ExaCM)

Create an account in the Oracle Database Cloud Service (DBCS). This will give you access to HR schema as well.

Follow the step-by-step instructions provided on [Using Java Applications and IDEs with Oracle Database Cloud Service(DBCS)](http://www.oracle.com/technetwork/database/application-development/jdbc/documentation/default-3396167.html) OTN page to create a database instance and also try to connect to it using JDBC and UCP code samples provided in the beginning of the guide.

Step 1:

Oracle Database Installation Available on OTN

As an alternative option, Oracle Database 12c Release 2 can also be installed on premise. Follow the links to install Oracle Database and check out the release notes.

For more information, refer to the following Oracle Database 12c Release 2 (12.2) installation guides and release notes:

- Oracle Database Installation Guide for Linux

- Oracle Database Installation Guide for Microsoft Windows

##### Unlocking the HR Schema for the JDBC Application

The `HR` user account, which owns the sample HR schema used for the Java application in this guide, is initially locked. You must log in as a user with administrative privileges (`SYS`) and unlock the account before you can log in as `HR`.

If the database is locally installed, use the Run SQL Command Line to unlock the account as follows:

1.  To access the Run SQL Command Line, from the Start menu, select Programs (or All Programs), then Oracle Database 12c Release 2 (12.2), and then click Run SQL Command Line. Log in as a user with DBA privileges, for example:
        > CONNECT SYS AS SYSDBA;
        Enter password: password
2.  Run the following command:
        > ALTER USER HR ACCOUNT UNLOCK;

    or,

        > ALTER USER HR IDENTIFIED BY HR;
3.  Test the connection as follows:
        > CONNECT HR
        Enter password: password

You should see a message indicating that you have connected to the database.

**Note:**

For information about creating and using secure passwords with Oracle Database 12c Release 2 (12.2), refer to Oracle Database Security Guide.

In addition, some of the constraints and triggers present in the `HR` schema are not in line with the scope of the Java application created in this guide. You must remove these constraints and triggers as follows using the following SQL statements:

    DROP TRIGGER HR.UPDATE_JOB_HISTORY;
    DROP TRIGGER HR.SECURE_EMPLOYEES;
    DELETE FROM JOB_HISTORY;

#### JDK 8

You will need JDK8 — a Java Development Kit to create and compile Java applications.

**Note:**

Oracle Database 12c Release 2 (12.2) JDBC driver supports JDK8. Refer <http://www.oracle.com/technetwork/java/javase/downloads/index.html> for information about installing Java.

#### JDeveloper IDE

In this guide, Oracle JDeveloper Release 12c is the integrated development environment (IDE) used to create the sample Java web application. JDeveloper is used to edit the source code, compile the application, create a war file, and deploy the war file onto the integrated weblogic server (WLS).

#### J2SE or JDK

To create and compile Java applications, you need the full Java 2 Platform, Standard Edition, Software Development Kit (J2SE SDK), formerly known as the Java Development Kit (JDK).

**Note:**

Oracle Database 12c Release 2 (12.2) supports JDK 8.

**See Also:**

- [`http://www.oracle.com/technetwork/java/javase/downloads/index.html`](http://www.oracle.com/technetwork/java/javase/downloads/index.html) for information about installing Java

- [`http://www.oracle.com/technetwork/java/overview-141217.html`](http://www.oracle.com/technetwork/java/overview-141217.html) for information about the JDBC API

#### Integrated Development Environment

For ease in developing the application, you can choose to develop your application in an integrated development environment (IDE). This guide uses Oracle JDeveloper to create the files for this application.

#### Web Server

The sample application developed in this guide uses JavaServer Pages (JSP) technology to display information and accept input from users. To deploy these pages, you need a Web server with a servlet and JSP container, such as the Apache Tomcat application server.

This guide uses the embedded server called the Oracle WebLogic Server in JDeveloper for deploying the JSP pages. If you choose not to install Oracle JDeveloper, then any Web server that enables you to deploy JSP pages should suffice.

For more information about these servers, please refer to vendor-specific documentation.

### Verifying the Oracle Database 12c Release 2 (12.2) Installation

Oracle Database 12c Release 2 (12.2) installation is platform-specific. You must verify that the installation was successful before you proceed to create the sample application. This section describes the steps for verifying an Oracle Database 12c Release 2 (12.2) installation.

Verifying a installation involves the following tasks:

### Github Repository Details

Table 4-1 Github Repository Details

| Name and Location                                                                  | Details                                                                                                                                              |
|:-----------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------|
| 2DaysJavaGuide-Workspace                                                           | This zip contains outlines of Java classes, for building the HR web application. Download the zip, unzip to a location, and follow the instructions. |
| [HRWebApp](https://github.com/oracle/oracle-db-examples/tree/master/java/HRWebApp) | This repository contains the complete code samples of the application. Refer to this when you face issues or exceptions.                             |

### Import the Application in JDeveloper

Use the following steps to import the application in JDeveloper:

1\. Navigate to the location where the HRWebApp_Workspace is extracted.

2\. Choose a name for the application.

3\. It creates a project with all files required to build HR web application. Now, you can start editing.

### Compile Applications in JDeveloper

You can compile or create a .war file using maven commands through JDeveloper.

1\. Right click on the project.

2\. Run Maven

3\. Navigate to compile/package/clean

### Compile Using Maven and Run the Application in any Java EE Container

a\. Compile Using Maven:

HR web application can also be easily compiled using the Maven commands. If you are using Oracle maven repository, then make sure to have the settings.xml file with all the required details available for easy access. After you download the HRWebApp_workspace and add the required code, use the commands below to clean, compile and package the source code.

Execute the following commands:

`mvn –s settings.xml clean `

`mvn –s settings.xml compile `

`mvn –s settings.xml package`

b\. Deploy the .war file on any Java EE container

Once the source code is packaged using the maven command “mvn –s settings.xml package”, the war file will be placed under the folder “target/JdbcWebSamples.war”. Place this war file under TOMCAT_HOME/webapps/ and start the tomcat server. Once the tomcat is started, access the HR web application using the URL http://localhost:8080/JdbcWebSamples/.

If the login/logout modules are added, then login with either hradmin or hrstaff user.

Run the the Application in JDeveloper

JDeveloper uses the integrade WebLogic Server to run the web application.

List All Employees

HR web Application has several functionalities. “List All” is the functionality where the details of employees such as Employee_id, First_name, Last_Name, Email, Phone_number, Job_id, Salary etc., are retrieved from the “Employees” table and shown on a web page. See the screenshot below that shows “List All” functionality.
