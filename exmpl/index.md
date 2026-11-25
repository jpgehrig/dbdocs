Database Examples Installation Guide

19c

E96357-01

January 2019

This document describes how to install and configure the products available with Oracle Database Examples. It includes the following sections:

- Products Available on the Oracle Database Examples Media

- Preinstallation Considerations

- Accessing the Installation Software

- About Installing Oracle Database Examples

- Documentation Accessibility

### 1.1 Products Available on the Oracle Database Examples Media

The following sections describe the products that are installed. You must install these products in an existing Oracle Database 19c Oracle home:

- Oracle Database Examples

- Oracle JDBC Development Drivers

- Oracle Text Knowledge Base

#### 1.1.1 Oracle Database Examples

Oracle Database Examples include a variety of examples and product demonstrations that you can use to learn about the products, options, and features of Oracle Database.

Many of these examples are designed to work with the sample schemas, which you can install in any Oracle Database. Many documents in the Oracle Documentation Library use the example programs and scripts provided with the Oracle Database Examples.

This section contains the following topics:

- About Oracle Data Mining Demos

- About Oracle Globalization Support Demos

- About Oracle Message Gateway Common Companion Files

- About Oracle Multimedia Demos

- About Oracle Precompiler Demos

- About Oracle Spatial and Graph Demos

- About Oracle Internet Directory Client Demos

- About Oracle XML Demos

- About Oracle Call Interface Demos

- About Oracle C++ Call Interface Demos

- About Oracle ODBC Companion

##### 1.1.1.1 About Oracle Data Mining Demos

Oracle Data Mining Demos include Data Mining sample programs that can help you in learning about Oracle Data Mining APIs.

The Data Mining sample programs illustrate typical approaches to data preparation, algorithm selection, algorithm tuning, testing, and scoring. Each program creates a mining model in the database. All the programs include extensive inline comments to help you understand the code.

**Related Topics**

- [Oracle Data Mining User’s Guide](../dmprg/data-mining-sample-programs.md)

##### 1.1.1.2 About Oracle Globalization Support Demos

Oracle Globalization Demos showcase the features and APIs of the Oracle Globalization Development Kit.

Oracle Globalization Development Kit (GDK) offers a complete framework to ease the development of globalized internet applications. The GDK Example demo illustrates individual functionalities such as, locale-sensitive data formatting, linguistic sorting, locale mapping, locale determination, and language detection. The Oracle Store demo illustrates how the GDK features can be integrated to build a complete multilingual J2EE web application that serves users with vastly different locale preferences.

**Related Topics**

- [Oracle Database Globalization Support Guide](../nlspg/oracle-globalization-development-kit.md)

##### 1.1.1.3 About Oracle Message Gateway Common Companion Files

Oracle Messaging Gateway enables communication between applications based on non-Oracle messaging systems and Oracle Database Advanced Queuing.

Oracle Database Advanced Queuing provides propagation between two Oracle Database Advanced Queuing queues to enable e-business (HTTP through IDAP). Messaging Gateway extends this to applications based on non-Oracle messaging systems. The samples provided for Messaging Gateway illustrate message propagating with Oracle AQ, WebSphere MQ Series, and Tibco Rendezvous using message formats that include JMS, LCR, and XML.

There are seven different samples provided with Messaging Gateway, each located in their own subdirectory. Each sample includes a README file that contains detailed information for setting up and executing the samples.

##### 1.1.1.4 About Oracle Multimedia Demos

Oracle Multimedia (formerly Oracle interMedia) is a feature that enables Oracle Database to store, manage, and retrieve images, audio, video, or other heterogenous media data in an integrated fashion with other enterprise information.

Oracle Multimedia extends Oracle Database reliability, availability, and data management to multimedia content in traditional, Internet, electronic commerce, and media-rich applications. It includes several scripts and sample applications that you can use. These consist of OCI, SQL, Java, PL/SQL, and ASP/VBScript sample applications (demos).

**Related Topics**

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/LOB-demonstration-files.md)

##### 1.1.1.5 About Oracle Precompiler Demos

Oracle Precompiler Demos show application programmers how to embed SQL operations in C/C++ and COBOL code in a way that is compatible with ANSI standard.

A Pro\*C program is a C program containing embedded SQL statements. Oracle Pro\*C/C++ and Pro\*COBOL Demos offer extensions to support dynamic SQL operations, which are operations that can change in real time. It is also possible to use dynamic SQL operations through PL/SQL code (known as anonymous PL/SQL block) with a Pro\*C/C++ and Pro\*COBOL application. Typical applications contain much more static SQL than dynamic SQL. The precompiler translates each embedded SQL statement into calls to the Precompiler run-time library (SQLLIB).

**Related Topics**

- [Pro\*C/C++ Programmer's Guide](../lnpcc/sample-programs.md)
- [Pro\*COBOL Programmer's Guide](../lnpcb/Pro-COBOL-for-Windows.md)

##### 1.1.1.6 About Oracle Spatial and Graph Demos

Oracle Spatial and Graph Demos provide SQL schema and functions that facilitate the storage, retrieval, update, and query of collections of spatial features in an Oracle database.

Oracle Spatial and Graph is an integrated set of functions and procedures that enables spatial data to be stored, accessed, and analyzed quickly and efficiently in an Oracle database. Spatial data represents the essential location characteristics of real or conceptual objects as those objects relate to the real or conceptual space in which they exist.

**Related Topics**

- [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-concepts.md)
- [Oracle Spatial and Graph GeoRaster Developer's Guide](../geors/georaster-overview-and-concepts.md)
- [Oracle Spatial and Graph Topology Data Model and Network Data Model Graph Developer's Guide](../topol/network-data-model-graph-overview.md)

##### 1.1.1.7 About Oracle Internet Directory Client Demos

Oracle Internet Directory Client Demos show application programmers how to use LDAP C and PL/SQL APIs.

All LDAP operations based on the C API, require clients to establish an LDAP session with the LDAP server. For LDAP operations based on the PL/SQL API, a database session must first initialize and open an LDAP session. The DBMS_LDAP package enables PL/SQL applications to access data located in LDAP servers. The names and syntax of the function calls are similar to those of the C API.

**Related Topics**

- [Oracle Fusion Middleware Application Developer's Guide for Oracle Identity Management](https://docs.oracle.com/middleware/11119/oid/develop/capi.htm#OIMAD2299)

##### 1.1.1.8 About Oracle XML Demos

Oracle XML Demos showcase the features of the Oracle XML Developer's Kit (XDK), which is a versatile set of components that enables you to build and deploy C, C++, and Java software programs that process XML.

**Related Topics**

- [Running Oracle XML Developer's Kit JavaBean Demo Programs](../adxdk/XDK-JavaBeans.md)
- [Using the XML C++ Class Generator Examples](../adxdk/using-XML-class-generator-for-C-plus-plus.md)
- [Using the XML Parser Command-Line Utility: Example](../adxdk/using-XML-parser-for-C.md)

##### 1.1.1.9 About Oracle Call Interface Demos

Oracle Call Interface (OCI) demos include sample C programs to use the OCI APIs.

These programs provide examples of the data types, calling conventions, syntax, and semantics of C.

**Related Topics**

- [Oracle Call Interface Programmer's Guide](../lnoci/oci-demo-programs.md)

##### 1.1.1.10 About Oracle C++ Call Interface Demos

Oracle C++ Call Interface (OCCI) demos provide database access APIs for applications written in C++. The control classes enable the applications to connect to the database and create resources like statements and resultsets. The data classes contain various types of data. The object classes and methods provide a navigational interface to access and manipulate objects. The Object Type Translator (OTT) can be used to generate the C++ class headers for the data types defined in Oracle database. The installed demos illustrate the use of classes and methods for OTT and OCCI.

**Related Topics**

- [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

##### 1.1.1.11 About Oracle ODBC Companion

Oracle ODBC Driver demos provide basic structure of an ODBC application which can be extended to make a full-fledged ODBC application.

ODBC being a standard, plenty of sample applications may be found in books which discuss the concept of ODBC driver. For Oracle ODBC Driver specific options, see Help while setting up Data Source Name on Windows.

**Related Topics**

- [Oracle Database Administrator's Reference for Linux and UNIX-Based Operating Systems](../unxar/using-oracle-ODBC-driver.md)

#### 1.1.2 Oracle JDBC Development Drivers

Oracle provides a set of JDBC drivers that you can use for debugging the code and other deployment scenarios. These drivers can access Oracle Database 10g Release 2 or later.

#### 1.1.3 Oracle Text Knowledge Base

Oracle Database Examples media installs two Oracle Text knowledge bases, English and French. You can extend the supplied knowledge bases depending on your requirements. Alternatively, you can create your own knowledge bases, in languages other than English and French.

**Related Topics**

- [Oracle Text Reference](../ccref/oracle-text-utilities.md)

### 1.2 Preinstallation Considerations

The requirements for installing Oracle Database Examples are as follows:

- Free Disk Space

- Required Products

#### 1.2.1 Free Disk Space

Verify that the file system that contains the Oracle home directory has at least:

- 1.1 GB of free disk space on UNIX systems.

- 800 MB of free disk space on Windows systems.

The following topics contain details about determining free disk space on UNIX and Windows platforms:

- Determining Free Disk Space on UNIX Platforms

- Determining Free Disk Space on Windows Systems

##### 1.2.1.1 Determining Free Disk Space on UNIX Platforms

Explains how to check free disk space on UNIX platforms.

Use the following command to check that the Oracle home directory has enough space:

- `df —k ``oracle_home_path`

where `oracle_home_path` is the path to the Oracle home directory.

##### 1.2.1.2 Determining Free Disk Space on Windows Systems

Explains how to determine free disk space on Windows systems.

Perform the following steps to check that the Oracle home directory has enough space:

1.  Double-click My Computer.
2.  Right-click the drive where the Oracle software is to be installed.
3.  Select Properties.

#### 1.2.2 Required Products

Explains the products that are required to use Oracle Database Examples.

Before you can use the Oracle Database Examples, you must install the sample schemas in an Oracle Database. When you install Oracle Database, or use Database Configuration Assistant to create a database, you can choose to include the sample schemas. You can also manually install the sample schemas in an existing database.

**Note:**

Starting with Oracle Database 12c Release 2 (12.2), only the HR sample schema is automatically installed after a database installation. All sample schemas, including HR, are distributed on GitHub:

[Oracle Database Sample Schemas](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/exmpl&id=github_schemas)

### 1.3 Accessing the Installation Software

Explains how to identify the Oracle home directory used by Oracle Database installation.

Before you install products from the Oracle Database Examples media, you must ensure that your system has access to an Oracle Database 19c Oracle home. If required, you must first install or upgrade to this release of Oracle Database.

Identify the Oracle home directory used by the Oracle Database installation.

On UNIX platforms, the `oratab` file is located in the `/etc` directory or in the `/var/opt/oracle` directory. Use the `more` command to check the contents of the `oratab` file. For example:

    # more /etc/oratab

On Windows platforms:

1.  From the Start menu, choose Programs, then Oracle - HOME_NAME, then Oracle Installation Products, then Universal Installer.
2.  When the Welcome screen appears, click Installed Products.
    The Inventory screen appears, listing all of the Oracle homes on the system and the products installed in each Oracle home.
3.  On the Inventory screen, expand each Oracle home and locate Oracle Database 19c.
4.  Click Close and then Cancel to exit Oracle Universal Installer.

**Related Topics**

- [Oracle Database Installation Guide](../install-and-upgrade.md)

#### 1.3.1 Downloading Oracle Database Examples

You must download and install Oracle Database Examples in an existing Oracle home to view the product demonstrations.

This section describes how to download Oracle Database Examples on your computer to a location other than Oracle Database 19c Oracle home.

1.  Go to the Oracle Database 19c download page on Oracle Technology Network:
    <http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index.html>
2.  Select the See All link, and then select the Oracle Database Examples zip file under the heading Oracle Database 19c Examples.

### 1.4 About Installing Oracle Database Examples

Oracle Database Examples installs the product demonstrations in the Oracle home directory and the SQL scripts for the sample schemas in the `$ORACLE_HOME/demo/schema` directory. To use these product demonstrations, you must install the sample schemas in the database. If the sample schemas are not included during an Oracle database installation or during database creation using Database Configuration Assistant, then you can manually install them by running the SQL scripts.

Use one of the following methods to install Oracle Database Examples:

- Installing Oracle Database Examples Using Oracle Universal Installer

- Silent Installation of Oracle Database Examples Using Response Files

- About demo Directories in Read-Only Oracle Homes

**Related Topics**

- [Manually Installing Sample Schemas](../comsc/installing-sample-schemas.md)

#### 1.4.1 Installing Oracle Database Examples Using Oracle Universal Installer

You must install Oracle Database Examples in an existing Oracle Database 19c Oracle home.

Perform the following steps to install Oracle Database Examples:

1.  Log in to the computer where Oracle Database is installed.
    On UNIX platforms, log in as the Oracle software owner user (`oracle`) and set the `DISPLAY` environment variable.

    On Windows platforms, log in as an Administrator or as a member of the Administrators group to the computer on which you want to install Oracle components. If you are installing on a Primary Domain Controller (PDC) or a Backup Domain Controller (BDC), log on as a member of the Domain Administrators group.
2.  Verify that the Oracle Database that you plan to use is accessible.
    Refer to “Accessing the Installation Software” for details.
3.  Navigate to the directory where you downloaded the installation files.
4.  Extract the contents of the zip file.
5.  Run the following command to start Oracle Universal Installer:
    On UNIX platforms:
        $ ./runInstaller

    On Windows platforms:
    Double-click `setup.exe`.
6.  On the Specify Installation Location screen, enter the following:
    - Oracle Base: The Oracle base path appears by default. You can change the path based on your requirement. Specify the Oracle Base path.

      The Oracle base directory is a top-level directory for Oracle software installations.

    - Software Location: In the Software Location field, accept the default value or enter the Oracle home directory path where you want to install Oracle Database Examples. You must install Oracle Database Examples in an existing Oracle Database home.
      **Note:**

      If you try to install Oracle Database Examples in an Oracle Database home that is different from the current release, then the installation fails with an error.

    If Oracle Real Application Clusters (Oracle RAC) is installed in the Oracle home that you select, then Oracle Universal Installer displays the Grid Installation Options screen. The examples software is installed in the selected Oracle RAC home on all the nodes where it exists. The nodes listed in the table are the nodes on which the Oracle Inventory has registered an installed Oracle RAC home.
    Ensure that each node listed is up and running before you click Next.
    **Note:**

    On an Oracle RAC installation, the software is installed on all the cluster nodes.
7.  On the Perform Prerequisite Checks screen, check for and correct any errors that may have occurred while Oracle Universal Installer was checking your system. If you click Check Again, then you can run the prerequisite check again to see if the minimum requirements are met to carry on with the installation. Click Fix & Check Again, if you want the installer to fix the problem and check the system requirements again.
    **Note:**

    TheFix & Check Again option generates a script (UNIX only) that sets some system parameters to Oracle-recommended values. You must run the script as the `root` user. Oracle recommends that you do not modify the contents of this script.
    From the list, select an option:
    - Show All: To get a list of all the prerequirement checks run.
    - Show Failed: To get a list of prerequirement checks that failed.
    - Show Succeeded: To get a list of the prerequirement checks that were successful.
8.   Review the information displayed on the Summary screen and click Install.
    **Note:**

    Click Save Response File to save all the installation steps into a response file. Later, you can use this file for a silent installation.
9.  The Install Product screen appears when the product is installing. Installation operations include executing actions such as file copy and adding services on Windows systems and linking on UNIX systems, and executing decision points and calculations.
    The Finish screen appears when the installation is completed.
10. Click Close to exit Oracle Universal Installer.

#### 1.4.2 Silent Installation of Oracle Database Examples Using Response Files

A silent installation runs in the background and does not require input from the user. The interactive dialogs normally seen by the user are not displayed. Silent installations can be useful if you have to install an Oracle product multiple times on multiple computers.

To perform a silent installation of Oracle Database Examples, you must start Oracle Universal Installer in silent or response file mode. Enter a command similar to the following:

1.  On UNIX platforms:
    `$ /``directory_path``/runInstaller [-silent] -responseFile ``responsefilename`
    **Note:**

    Do not specify a relative path to the response file. If you specify a relative path, then Oracle Universal Installer fails.
    where:

    - `directory_path` is the path of the database directory on the DVD or on the hard drive.
    - `-silent` runs Oracle Universal Installer in silent mode.
    - `responsefilename` is the full path and file name of the installation response file that you configured.
2.  On Windows platforms:
    `DRIVE_LETTER:\setup.exe_location`` setup [-silent] "variable=setting" [-nowelcome] [-noconfig] [-nowait] -responseFile`
    where:

    - `DRIVE_LETTER`: Identifies the full path of the response file.
    - `setup.exe_location`: Indicates the location of `setup.exe`.
    - `"variable=setting"` refers to a variable within the response file that you may prefer to run at the command line rather than set in the response file. Enclose the variable and its setting in quotes.
    - `-noconfig`: Suppresses running the configuration assistants during installation.
    - `-nowait`: Closes the console window when the silent installation completes.

#### 1.4.3 About demo Directories in Read-Only Oracle Homes

If you have configured a read-only Oracle home, then you must copy some `demo` directories from ORACLE_HOME to ORACLE_BASE_HOME.

For more information, see [Oracle Database Installation Guide for Linux](../ladbi/running-demo-from-oracle-base-home.md).

### 1.5 Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### 1.6 Set Up Java Access Bridge to Implement Java Accessibility

Install Java Access Bridge so that assistive technologies on Microsoft Windows systems can use the Java Accessibility API.

Java Access Bridge is a technology that enables Java applications and applets that implement the Java Accessibility API to be visible to assistive technologies on Microsoft Windows systems.

Refer to Java Platform, Standard Edition Accessibility Guide for information about the minimum supported versions of assistive technologies required to use Java Access Bridge. Also refer to this guide to obtain installation and testing instructions, and instructions for how to use Java Access Bridge.

**Related Topics**

- [Java Platform, Standard Edition Java Accessibility Guide](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/exmpl&id=JSACC-GUID-7890D37B-16F2-48EC-B45F-2A6CF0613EE5)

------------------------------------------------------------------------

Oracle Database Database Examples Installation Guide, 19c

E96357-01

Copyright © 2011, 2019, Oracle and/or its affiliates. All rights reserved.

This software and related documentation are provided under a license agreement containing restrictions on use and disclosure and are protected by intellectual property laws. Except as expressly permitted in your license agreement or allowed by law, you may not use, copy, reproduce, translate, broadcast, modify, license, transmit, distribute, exhibit, perform, publish, or display any part, in any form, or by any means. Reverse engineering, disassembly, or decompilation of this software, unless required by law for interoperability, is prohibited.

The information contained herein is subject to change without notice and is not warranted to be error-free. If you find any errors, please report them to us in writing.

If this is software or related documentation that is delivered to the U.S. Government or anyone licensing it on behalf of the U.S. Government, then the following notice is applicable:

U.S. GOVERNMENT END USERS: Oracle programs, including any operating system, integrated software, any programs installed on the hardware, and/or documentation, delivered to U.S. Government end users are "commercial computer software" pursuant to the applicable Federal Acquisition Regulation and agency-specific supplemental regulations. As such, use, duplication, disclosure, modification, and adaptation of the programs, including any operating system, integrated software, any programs installed on the hardware, and/or documentation, shall be subject to license terms and license restrictions applicable to the programs. No other rights are granted to the U.S. Government.

This software or hardware is developed for general use in a variety of information management applications. It is not developed or intended for use in any inherently dangerous applications, including applications that may create a risk of personal injury. If you use this software or hardware in dangerous applications, then you shall be responsible to take all appropriate fail-safe, backup, redundancy, and other measures to ensure its safe use. Oracle Corporation and its affiliates disclaim any liability for any damages caused by use of this software or hardware in dangerous applications.

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.

Intel and Intel Xeon are trademarks or registered trademarks of Intel Corporation. All SPARC trademarks are used under license and are trademarks or registered trademarks of SPARC International, Inc. AMD, Opteron, the AMD logo, and the AMD Opteron logo are trademarks or registered trademarks of Advanced Micro Devices. UNIX is a registered trademark of The Open Group.

This software or hardware and documentation may provide access to or information about content, products, and services from third parties. Oracle Corporation and its affiliates are not responsible for and expressly disclaim all warranties of any kind with respect to third-party content, products, and services unless otherwise set forth in an applicable agreement between you and Oracle. Oracle Corporation and its affiliates will not be responsible for any loss, costs, or damages incurred due to your access to or use of third-party content, products, or services, except as set forth in an applicable agreement between you and Oracle.
