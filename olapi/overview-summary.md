Skip navigation links

- Overview
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)

**Oracle® OLAP Java API Reference**

See: Description

**Packages**

| Package                                                                                                           | Description                                                                                                                                                                               |
|-------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [oracle.express](oracle/express/package-summary.md)                                                               | Contains classes that support processing in Oracle OLAP.                                                                                                                                  |
| [oracle.express.olapi.data.full](oracle/express/olapi/data/full/package-summary.md)                               | Contains an `Exception` class that might be encountered by a client application.                                                                                                          |
| [oracle.express.spl](oracle/express/spl/package-summary.md)                                                       | Contains classes that support the execution of OLAP DML commands in Oracle OLAP.                                                                                                          |
| [oracle.olapi](oracle/olapi/package-summary.md)                                                                   | Contains an interface, a class, and exceptions that are of general use in the Oracle OLAP Java API.                                                                                       |
| [oracle.olapi.data.cursor](oracle/olapi/data/cursor/package-summary.md)                                           | Contains interfaces and classes for retrieving and accessing the result set of a query.                                                                                                   |
| [oracle.olapi.data.source](oracle/olapi/data/source/package-summary.md)                                           | Contains classes that construct a query of the data in an Oracle Database.                                                                                                                |
| [oracle.olapi.metadata](oracle/olapi/metadata/package-summary.md)                                                 | Contains interfaces and classes that represent Oracle OLAP metadata objects and that provide those objects to an application.                                                             |
| [oracle.olapi.metadata.deployment](oracle/olapi/metadata/deployment/package-summary.md)                           | Contains classes that specify the deployment of a logical OLAP model as relational OLAP (ROLAP) objects or as analytic workspace (AW) objects.                                            |
| [oracle.olapi.metadata.mapping](oracle/olapi/metadata/mapping/package-summary.md)                                 | Contains classes that map the `MdmObject` objects of a logical OLAP metadata model to physical storage structures in an Oracle Database instance.                                         |
| [oracle.olapi.metadata.mdm](oracle/olapi/metadata/mdm/package-summary.md)                                         | Contains classes that represent data supporting the multidimensional model (MDM) for metadata.                                                                                            |
| [oracle.olapi.resource](oracle/olapi/resource/package-summary.md)                                                 | Provides support for the internationalization of messages for `Exception` classes in the Oracle OLAP Java API.                                                                            |
| [oracle.olapi.session](oracle/olapi/session/package-summary.md)                                                   | Contains a class that represents a session that is associated with a specific connection to an Oracle Database instance.                                                                  |
| [oracle.olapi.syntax](oracle/olapi/syntax/package-summary.md)                                                     | Contains classes that represent data types, functions, commands, and data objects.                                                                                                        |
| [oracle.olapi.transaction](oracle/olapi/transaction/package-summary.md)                                           | Contains interfaces that define classes that are involved in transactions between Oracle OLAP and an OLAP client application and `Exception` classes that an application might encounter. |
| [oracle.olapi.transaction.metadataStateManager](oracle/olapi/transaction/metadataStateManager/package-summary.md) | Contains an interface to implement and associate with a `Template` object.                                                                                                                |

**Oracle® OLAP Java API Reference**

June 14, 2018

This is the reference documentation for the Oracle OLAP Java API, the Java application programming interface for Oracle OLAP. This overview contains the following topics.

- **Changes to the API**
- **Intended Audience**
- **Before You Begin**
- **JDK Version Required**
- **Examples of Using the Oracle OLAP Java API**
- **Compatibility with Previous Releases**
- **Unique and Local Values in the Oracle OLAP Java AP**
- **Documentation Accessibility**
- **Accessibility of Code Examples in Documentation**
- **Accessibility of Links to External Websites in Documentation**
- **Related Documentation**

**Changes to the API**

No changes have been made to the Oracle OLAP Java API since Oracle Database 12*c*, Release 1 (12.1). For a description of the changes in the Oracle OLAP Java API in that release, see [Changes in This Release](doc-files/changes.md).

**Intended Audience**

This documentation assumes that you are already familiar with Java, relational database management systems, data warehousing, and online analytical processing (OLAP) concepts. It is intended for Java programmers who are responsible for creating applications that create and maintain OLAP objects, build and maintain analytic workspaces, and perform online analytical processing.

**Before You Begin**

To use the Oracle OLAP Java API, you must have access to an Oracle Database instance that has the OLAP option installed. An Oracle Database with the OLAP option provides the Oracle OLAP Java API classes, and other required classes, in JAR files. Before you can compile an Oracle OLAP Java API program, you must get the required JAR files and add them to your Java development environment.

The following table lists the required JAR files and their location under the `ORACLE_HOME` directory in an Oracle Database installation.

| File Name           | Location          |
|---------------------|-------------------|
| `  olap_api.jar`    | `  /olap/api/lib` |
| `  ojdbc6.jar`      | `  /jdbc/lib`     |
| `  xmlparserv2.jar` | `  /lib`          |

You must use the JDBC files included in your Oracle Database installation and not those from another Oracle product or from another vendor.

You can include this reference documentation in an integrated development environment, such as JDeveloper, by downloading the `olap_api_doc.jar` file from the Oracle Technology Network (OTN) website at <http://www.oracle.com/technetwork/database/options/olap/index.html>.

To download the `olap_api_doc.jar` file, in the Download section select **Sample Code and Schemas** and then select **Oracle OLAP Java API Reference olap_api_doc.jar**. You can then add the JAR file to your IDE project.

For information on installing an Oracle Database with the OLAP option, see your Oracle Database installation documentation. For more information on administering the OLAP option, see *Oracle OLAP User's Guide*.

**JDK Version Required**

This release of the Oracle OLAP Java API requires J2SE Development Kit 6.0 (JDK 6.0).

**Examples of Using the Oracle OLAP Java API**

In the examples of the Oracle OLAP Java API code in this documentation, the metadata objects are mapped to columns of the tables of the Global sample schema. From the Oracle Technology Network (OTN) OLAP website, you can download a file that contains SQL scripts that create the Global schema. The OLAP OTN website is at <http://www.oracle.com/technetwork/database/options/olap/index.html>.

To download the sample schema, in the Download section select **Sample Code and Schemas** and then select **Global Schema 11*g***.

You can also download a file that contains example programs that include the complete code for many of the examples in this documentation and in *Oracle OLAP Java API Developer's Guide*. To download that file, in the Download section select **Sample Code and Schemas**. On the Oracle OLAP Downloads page, in the Oracle OLAP 11*g* section under Sample Schemas & Code, select **Example Programs for Documentation**.

For more information on the example programs, see [Example Oracle OLAP Java API Programs](doc-files/ExamplePrograms.md).

**Compatibility with Previous Releases**

Programs that use previous releases of the Oracle OLAP Java API can run on Oracle Database, 11*g* Release 1 (11.1), depending on the metadata reader mode. The mode specifies the type of metadata that Oracle OLAP recognizes and makes available to the client application. By default, Oracle OLAP recognizes all types of metadata. You can specify a different metadata reader mode when you create a `DataProvider`or a `UserSession`. You can use 10*g* metadata objects to query data but you cannot modify the metadata objects or create new persistent objects.

For information about setting the metadata reader mode, see the `DataProvider` class description. For information about using namespaces to specify a 10*g* Oracle OLAP metadata object, see [Using Namespaces](oracle/olapi/metadata/mdm/MdmMetadataProvider.md) in the description of `MdmMetadataProvider`.

**Unique and Local Values in the Oracle OLAP Java API**

The members of an Oracle OLAP dimension are often organized into one or more hierarchies. Some hierarchies have parent-child relationships based on levels and some have those relationships based on values. The Oracle OLAP Java API uses a three-part format to specify the hierarchy, the level, and the value of a dimension member, and thereby identify a *unique value*. The first part of a unique value is the name of the hierarchy object, the second part is the name of the level object, and the third part is the value of the member in the level. The parts of the unique value are separated by a value separation string, which by default is double colons (`::`). The following is an example of unique value in the `YEAR` level of the `CALENDAR_YEAR` hierarchy of the `TIME_AWJ` dimension:

`CALENDAR_YEAR::YEAR::CY2001`

The third part of a unique value is the *local value*. In the preceding example, the local value is `CY2001`, which is the identifier for the year 2001 in the Global schema. The Oracle OLAP Java API has classes and methods that you can use to get the local values of dimension members. See the descriptions of the `MdmPrimaryDimension` and `MdmDimensionMemberInfo` classes for more information about unique and local values.

An application can specify that Oracle OLAP use unique or local dimension hierarchy values by setting the `HierarchyValueType` property in a `java.util.Properties` object and using the `Properties` object to construct an `DataProvider`. The use of `Model` objects requires unique hierarchy values.

The selection of dimension members in the query must match the setting of the property. For a complex query, using unique dimension hierarchy values generally provides faster performance when Oracle OLAP fetches the data.

**Documentation Accessibility**

Our goal is to make Oracle products, services, and supporting documentation accessible to all users, including users that are disabled. To that end, our documentation includes features that make information available to users of assistive technology. This documentation is available in HTML format, and contains markup to facilitate access by the disabled community. Accessibility standards will continue to evolve over time, and Oracle is actively engaged with other market-leading technology vendors to address technical obstacles so that our documentation can be accessible to all of our customers. For more information, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

**Accessibility of Code Examples in Documentation**

Screen readers may not always correctly read the code examples in this document. The conventions for writing code require that closing braces should appear on an otherwise empty line; however, some screen readers may not always read a line of text that consists solely of a bracket or brace.

**Accessibility of Links to External Websites in Documentation**

This documentation may contain links to websites of other companies or organizations that Oracle does not own or control. Oracle neither evaluates nor makes any representations regarding the accessibility of these websites.

**Related Documentation**

The following documentation is helpful when using Oracle OLAP.

- *Oracle OLAP Java API Developer's Guide* – Introduces the Oracle OLAP Java API, a Java application programming interface for defining, building, and querying OLAP dimensional objects in an Oracle Database instance.
- *Oracle OLAP User's Guide* – Explains how SQL and Java applications can extend their analytic processing capabilities by using the OLAP option in the Enterprise Edition of Oracle Database.
- *Oracle OLAP DML Reference* – Describes the OLAP Data Manipulation Language (OLAP DML), which is the native language for defining and manipulating analytic workspace objects.
- *Oracle OLAP Expression Syntax Reference* – Describes the Oracle OLAP expression syntax used to generate information-rich content from the data stored in dimensional database objects such as cubes and dimensions.

Skip navigation links

- Overview
- Package
- Class
- [Tree](overview-tree.md)
- [Deprecated](deprecated-list.md)
- [Index](index-all.md)
- [Help](help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- Prev
- Next

<!-- -->

- [Frames](index.md)
- No Frames

<!-- -->

- [All Classes](allclasses-noframe.md)
