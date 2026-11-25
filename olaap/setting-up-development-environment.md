This appendix describes the development environment for creating applications that use the OLAP Java API.

This appendix includes the following topics:

- Overview

- Required Class Libraries

- Obtaining the Class Libraries

### A.1 Overview

The OLAP Java API client software is a set of Java packages containing classes that implement a Java programming interface to Oracle OLAP. An Oracle Database with the OLAP option provides the OLAP Java API and other required class libraries as Java archive (JAR) files. As an application developer, you must copy the required JAR files to the computer on which you develop your Java application, or otherwise make them accessible to your development environment.

When a Java application calls methods of OLAP Java API objects, it uses the OLAP Java API client software to communicate with Oracle OLAP, which resides within an Oracle Database instance. The communication between the OLAP Java API client software and Oracle OLAP is provided through the Java Database Connectivity (JDBC) API, which is a standard Java interface for connecting to relational databases. Another required JAR file provides support for importing and exporting OLAP Java API metadata objects XML.

To use the OLAP Java API classes as you develop your application, import them into your Java code. When you deliver your application to users, include the OLAP Java API classes with the application. You must also ensure that users can access JDBC.

To develop an OLAP Java API application, you must have the Java Development Kit (JDK), such as one in Oracle JDeveloper. Users must have a Java Runtime Environment (JRE) whose version number is compatible with the JDK that you used for development.

### A.2 Required Class Libraries

Your application development environment must have the following files:

- The `olap_api.jar` file, which contains the OLAP Java API class libraries.

- The `ojdbc6.jar` file, which is an Oracle JDBC (Java Database Connectivity) library that contains classes required to connect to an Oracle Database instance. The Oracle installation includes the JDBC file. You must use that JDBC file and not one from another Oracle product or from a product from another vender.

- The `xmlparserv2.jar` file, which contains classes that provide XML parsing support.

- The Java Development Kit (JDK) version 1.6. The Oracle Database installation does not provide the JDK. If you are using Oracle JDeveloper as your development environment, then the JDK is already installed on your computer. However, ensure that you are using the correct version of the JDK in JDeveloper. For information about obtaining and using some other JDK, see the Oracle Technology Network Java website at [`http://www.oracle.com/technetwork/java/index.html`](http://www.oracle.com/technetwork/java/index.html).

### A.3 Obtaining the Class Libraries

Table A-1 lists the OLAP Java API and other JAR files that you must include in your application development environment. The table includes the locations of the files under the directory identified by the `ORACLE_HOME` environment variable on the system on which the Oracle Database is installed. You can copy these files to your application development computer, or otherwise include them in your development environment.

Table A-1 Required Class Libraries and Their Locations in the Oracle Installation

| Class Library jar File | Location under ORACLE_HOME |
|:-----------------------|:---------------------------|
| `olap_api.jar`         | `/olap/api/lib`            |
| `ojdbc6jar`            | `/jdbc/lib`                |
| `xmlparserv2.jar`      | `/lib`                     |
