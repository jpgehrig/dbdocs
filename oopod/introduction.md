These topics introduce Oracle OLAP Provider for OLE DB, the Oracle implementation of an OLE DB provider for [OLAP](glossary.md) (Online Analytical Processing).

- Overview of OLE DB for OLAP

- Overview of Oracle OLAP Provider for OLE DB

- System Requirements

- Oracle OLAP Provider for OLE DB Installation

- Component Certifications

### Overview of OLE DB for OLAP

OLE DB for OLAP is a data access methodology that uses a set of [Component Object Model (COM)](glossary.md) interfaces for accessing multidimensional data. OLE DB accesses tabular data; OLE DB for OLAP extends the core OLE DB functionality to support multidimensional data.

OLE DB for OLAP requires the execution of [Multidimensional Expressions (MDX)](glossary.md) statements to obtain multidimensional data and metadata.

#### About OLE DB

OLE DB centers around the concept of a [consumer](glossary.md) and [provider](glossary.md). The consumer represents the traditional client. The provider transfers data from a data source to the consumer.

This section discusses OLE DB concepts that are also applicable to Oracle OLAP Provider for OLE DB.

##### OLE DB Data Providers

OLE DB data providers consist of COM components that transfer data between a data source and a consumer.

Each provider implements a set of OLE DB interfaces to handle requests from the consumer. A provider can implement optional OLE DB interfaces to provide additional functionality.

##### OLE DB Data Consumers

The OLE DB data consumer is any application or tool that uses OLE DB interfaces of a provider to access a broad range of data.

Using standard OLE DB interfaces, any OLE DB consumer can access data from any provider. In addition, consumers can access data in any programming language that supports COM, such as C++, Visual Basic, and Java.

**See Also:**

Microsoft OLE DB and OLE DB for OLAP documentation for more details

### Overview of Oracle OLAP Provider for OLE DB

Oracle OLAP Provider for OLE DB is an Oracle implementation of an MDP (Multidimensional Data Provider) that follows the core OLE DB and OLE DB for OLAP specifications.

Oracle OLAP Provider for OLE DB accesses Oracle databases running on all platforms, although it runs only on Windows.

Throughout this guide, OraOLEDB OLAP, or the term provider specifically refer to the Oracle OLAP Provider for OLE DB. This guide specifies the functionality that the OraOLEDB OLAP supports.

#### Application Types

OLAP providers for OLE DB can be invoked directly by COM applications or indirectly through the [ADO MD](glossary.md) (Active X Data Objects - Multidimensional) automation layer. Examples in this documentation provide headings that indicate whether the code is for OLE DB (COM applications), or ADO MD.

### System Requirements

The following items are required on a system to use Oracle OLAP Provider for OLE DB:

- Refer to [Oracle Database Client Installation Guide for Microsoft Windows](../ntcli/oracle-database-client-software-requirements.md) for operating system requirements.

- Access to Oracle Database 18c release 3 (18.3) or later with Analytic Views and Database In-Memory is recommended for performance.

  **Note:**

  Data is accessed using Analytic Views and not Oracle OLAP Option cubes

- Windows Data Access Components (Windows DAC) 6.0 or higher

- For data access from Microsoft Excel, only Microsoft Excel 2016 or Microsoft Excel 2013 are supported with this release.

### Oracle OLAP Provider for OLE DB Installation

Oracle OLAP Provider for OLE DB is included as part of your Oracle installation. It contains the features and demos that illustrate how to use this product for data access.

**See Also:**

[Oracle Database Client Installation Guide for Microsoft Windows](../ntcli/index.md) for installation instructions

### Component Certifications

Oracle provides support information for components on various platforms, lists compatible client and database versions, and identifies patches and workaround information.

Find the latest certification information at:

    http://metalink.oracle.com/metalink/certify/

You must register online before using OracleMetaLink. After logging into OracleMetaLink, select Product Lifecycle from the left-hand column. From the Products Lifecycle page, select the Certifications button. Other Product Lifecycle options include Product Availability, Desupport Notices, and Alerts.
