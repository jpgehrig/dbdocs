This chapter introduces the Oracle OLAP Java application programming interface (API). The chapter includes the following topics:

- OLAP Java API Overview

- Accessing Data Through the OLAP Java API

- Sample Schema for OLAP Java API Examples

- Tasks That an OLAP Java API Application Performs

### 1.1 OLAP Java API Overview

The Oracle OLAP Java API is an application programming interface that provides access to the online analytic processing (OLAP) technology in Oracle Database with the OLAP option. This topic lists operations that an OLAP Java API client application can perform, describes the classes in the OLAP Java API, describes the objects in a dimensional data model, and discusses organizing data for online analytical processing.

For a description of the advantages of OLAP technology, see [Oracle OLAP User's Guide](../olaug/overview.md). That document describes the capabilities that Oracle OLAP provides for the analysis of multidimensional data by business intelligence and advanced analytical applications. It describes in depth the dimensional data model, and it discusses the database administration and management tasks related to Oracle OLAP.

#### 1.1.1 What the OLAP Java API Can Do

Using the OLAP Java API, your can develop client applications that do the following operations.

- Establish one or more user sessions in a JDBC connection to an Oracle Database instance. Multiple user sessions can share the same connection and the same cache of metadata objects.

- Manage OLAP transactions with the database.

- Implement a dimensional data model using OLAP metadata objects.

- Create and maintain analytic workspaces.

- Create logical metadata objects and map them to relational sources.

- Deploy the metadata objects as an analytic workspace or as relational tables and views and commit the objects to the database.

- Explore the metadata to discover the data that is available for viewing or for analysis.

- Construct analytical queries of the multidimensional data. Enable end users to create queries that specify and manipulate the data according to the needs of the user (for example, selecting, aggregating, and calculating data).

- Modify queries, rather than totally redefine them, as application users refine their analyses.

- Retrieve query results that are structured for display in a multidimensional format.

For more information on some of these operations, see "Tasks That an OLAP Java API Application Performs".

#### 1.1.2 Describing the Classes in the OLAP Java API

The OLAP Java API has classes that represent the following types of objects.

- User sessions

- Transactions

- Metadata objects

- Build items, processes, specifications, and commands

- Queries

- Cursors that retrieve the data of a query

- Expressions that specify data objects, such as a column in a relational table or view, or that specify a function or command that operates on data

Table 1-1 lists packages that contain the majority of the OLAP Java API classes. These packages are under the `oracle.olapi` package. The table contains brief descriptions of the package contents.

Table 1-1 Packages of the OLAP Java API under oracle.olapi

| Package                                                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `data.cursor`                                                               | Contains classes that represent cursor managers and cursors that retrieve the data specified by a `Source` object. For information on `Cursor` objects, see [Understanding Cursor Classes and Concepts](understanding-cursor-classes-and-concepts.md) and [Retrieving Query Results](retrieving-query-results.md).                                                                                                                                                                                                                                                     |
| `data.source`                                                               | Contains classes that represent data sources and cursor specifications. You use `Source` objects to create queries of the data store. With the `Template` class you can incrementally build a `Source` object that represents a query that you can dynamically modify. For information on `Source` objects, see [Understanding Source Objects](understanding-source-objects.md) and [Making Queries Using Source Methods](making-queries-using-source-methods.md). For information on `Template` objects, see [Creating Dynamic Queries](creating-dynamic-queries.md). |
| `metadata`<br>`metadata.deployment`<br>`metadata.mapping`<br>`metadata.mdm` | Contains classes that represent metadata objects, classes that map the metadata objects to relational data sources, and classes that deploy the metadata objects in an analytic workspace or in relational database structures. For a description of these packages, see [Understanding OLAP Java API Metadata](understanding-olap-java-api-metadata.md). For information on using the classes in these packages, see [Discovering Metadata](discovering-metadata.md) and [Creating Metadata and Analytic Workspaces](creating-metadata-and-analytic-workspaces.md).   |
| `resource`                                                                  | Contains classes that support the internationalization of messages for `Exception` classes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `session`                                                                   | Contains a class that represents a session in a connection to an Oracle database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `syntax`                                                                    | Contains classes that represent the items and commands that specify how Oracle OLAP builds analytic workspace objects and classes that implement a syntax for creating SQL-like expressions. You use `Expression` objects in mapping metadata objects to relational data sources such as columns in a table or a view. You also use `Expression` objects to specify calculations and analytical operations for some metadata objects.                                                                                                                                  |
| `transaction`                                                               | Contains classes that represent transactions with Oracle OLAP in an Oracle Database instance. You use `Transaction` objects to commit changes to the database. For information on `Transaction` objects, see [Using a TransactionProvider](using-transaction-provider.md).                                                                                                                                                                                                                                                                                             |

The OLAP Java API also has packages organized under the `oracle.express` package. These packages date from the earliest versions of the API. The classes that remain in these packages are mostly `Exception` classes for exceptions that occur during interactions between Oracle OLAP and a client application.

For information on obtaining the OLAP Java API software and on the requirements for using it to develop applications, see [Setting Up the Development Environment](setting-up-development-environment.md).

#### 1.1.3 Describing the Dimensional Data Model

Data warehousing and OLAP applications are based on a multidimensional view of data. This view is implemented in a dimensional data model that includes the following dimensional objects.

Cubes
Cubes are containers for measures that have the same set of dimensions. A cube usually corresponds to a single relational fact table or view. The measures of a cube contain facts and the dimensions give shape to the fact data. Typically, the dimensions form the edges of the cube and the measure data is the body of the cube. For example, you could organize data on product units sold into a cube whose edges contain values for members from time, product, customer, and channel dimensions and whose body contains values from a measure of the quantity of units sold and a measure of sales amounts.

The OLAP concept of a cube edge is not represented by a metadata object in the OLAP Java API, but edges are often incorporated into the design of applications that use the OLAP Java API. Each edge contains values of members from one or more dimensions. Although there is no limit to the number of edges on a cube, data is often organized for display purposes along three edges, which are referred to as the row edge, column edge, and page edge.

Measures
Measures contain fact data in a cube. The measure values are organized and identified by dimensions. Measures are usually multidimensional. Each measure value is identified by a unique set of dimension members. This set of dimension members is called a tuple.

Dimensions
Dimensions contain lists of unique values that identify and categorize data in a measure. Commonly-used dimensions are customers, products, and times. Typically, a dimension has one or more hierarchies that organize the dimension members into parent-child relationships.

By specifying dimension members, measures, and calculations to perform on the data, end users formulate business questions and get answers to their queries. For example, using a time dimension that categorizes data by month, a product dimension that categorizes data by unit item, and a measure that contains data for the quantities of product units sold by month, you can formulate a query that asks if sales of a product unit were higher in January or in June.

Hierarchies
Hierarchies are components of a dimension that organize dimension members into parent-child relationships. Typically, in the user interface of a client application, an end user can expand or collapse a hierarchy by drilling down or up among the parents and children. The measure values for the parent dimension members are aggregations of the values of the children.

A dimension can have more than one hierarchy. For example, a time dimension could have a calendar year hierarchy and a fiscal year hierarchy. A hierarchy can be level-based or value-based.

In a level-based hierarchy, a parent must be in a higher level than the children of that parent. In a cube, the measure values for the parents are typically aggregated from the values of the children. For example, a time dimension might have levels for year, quarter, and month. The month level contains the base data, which is the most detailed data. The measure value for a quarter is an aggregation of the values of the months that are the children of the quarter and the measure value for a year is the aggregation of the quarters that are children of the year. Typically each level is mapped to a different column in the relational dimension table.

In a value-based hierarchy, the parent and the child dimension members typically come from the same column in the relational table. Another column identifies the parent of a member. For example, a value hierarchy could contain all employees of a company and identify the manager for each employee that has one. All employees, including managers, would come from the same column. Another column would contain the managers of the employees.

Levels
Levels are components of a level-based hierarchy. A level can be associated with more than one hierarchy. A dimension member can belong to only one level.

A level typically corresponds to a column in a dimension table or view. The base level is the primary key.

Attributes
Attributes contain information related to the members of a dimension. An end user can use an attribute to select data. For example, an end user might select a set of products by using an attribute that has a descriptive name of each product. An attribute is contained by a dimension.

Queries
A query is a specification for a particular set of data. The term query in the OLAP Java API refers to a `Source` object that specifies a set of data and can include aggregations, calculations, or other operations to perform using the data. The data and the operations on it define the result set of the query. In this documentation, the general term query refers to a `Source` object.

The API has a `Query` class in the `oracle.olapi.syntax` package. A `Query` represents a multirow, multicolumn result set that is similar to a relational table, a SQL `SELECT` statement, or an OLAP function. You use a `Query` object in mapping a dimension or measure to a relational table or view.

#### 1.1.4 Implementing the Dimensional Data Model

In the OLAP Java API, the dimensional data objects are represented by Multidimensional Model (MDM) classes. These classes are in the `oracle.olapi.metadata.mdm` package. Related classes are in the `oracle.olapi.metadata` package and the other packages under it. For detailed information about those classes, see [Understanding OLAP Java API Metadata](understanding-olap-java-api-metadata.md).

#### 1.1.5 Organizing the Data for OLAP

The OLAP Java API makes it possible for Java applications (including applets) to access data that resides in an Oracle data warehouse. A data warehouse is a relational database that is designed for query and analysis, rather than for transaction processing. Warehouse data often conforms to a star schema, which is a dimensional data model for a relational database. A star schema consists of one or more fact tables and one or more dimension tables. The fact tables have columns that contain foreign keys to the dimension tables. Typically, a data warehouse is created from a transaction processing database by an extraction transformation transport (ETT) tool.

For the data in a data warehouse to be accessible to an OLAP Java API application, a database administrator must ensure that the data warehouse is configured according to an organization that is supported by Oracle OLAP. The star schema is one such organization, but not the only one.

Once the data is organized in the warehouse, you can use an OLAP Java API application to design an OLAP dimensional data model of cubes, measures, dimensions, and so on, and to create the logical OLAP metadata objects that implement the model. You map the metadata objects to data in the warehouse and build an analytic workspace. Building the analytic workspace populates the OLAP views and other storage structures with the data that the OLAP metadata objects represent. You can also use Analytic Workspace Manager to do the same tasks.

An OLAP Java API application can get the OLAP metadata objects created either by Analytic Workspace Manager or through the OLAP Java API. It can use the metadata objects to create queries that operate on the data in the warehouse.

The collection of warehouse data in an analytic workspace is the data store to which the OLAP Java API gives access. Of course, the scope of the data that a user has access to is limited by the privileges granted to the user by the database administrator.

In addition to ensuring that data and metadata have been prepared appropriately, you must ensure that application users can make a JDBC connection to the data store and that users have database privileges that give them access to the data. For information about establishing a connection, see [Discovering Metadata](discovering-metadata.md).

### 1.2 Accessing Data Through the OLAP Java API

Oracle OLAP metadata objects organize and describe the data that is available to a client application. The metadata objects contain other information, as well, such as the data type of the data. However, you cannot retrieve data directly from a metadata object. To specify the data that you want, you must create a query. In specifying the data, you usually must specify one or more dimension member values. To retrieve the specified data, you create a `Cursor`. This topic briefly describes those actions.

Another way that you can query the data contained in OLAP metadata objects is through SQL queries of the views that Oracle OLAP creates for the metadata objects. For information about querying these views, see "[Using OLAP Views](understanding-olap-java-api-metadata.md)" in [Understanding OLAP Java API Metadata](understanding-olap-java-api-metadata.md).

#### 1.2.1 Creating Queries

Queries are represented by `oracle.olapi.data.source.Source` objects. You get a `Source` from a metadata object and use that `Source` object in specifying the data that you want to get. `Source` classes have methods for selecting and performing operations on the data. You can use the methods to manipulate data in any way that the user requires. For information about `Source` objects, see [Understanding Source Objects](understanding-source-objects.md) and [Making Queries Using Source Methods](making-queries-using-source-methods.md).

#### 1.2.2 Specifying Dimension Members

The members of an Oracle OLAP dimension are usually organized into one or more hierarchies. Some hierarchies have parent-child relationships based on levels and some have those relationships based on values. The value of each dimension member must be unique.

The OLAP Java API uses a three-part format to uniquely identify a dimension member. The format contains the hierarchy, the level, and the value of the dimension member, and thereby identifies a unique value in the dimension. The first part of a unique value is the name of the hierarchy object, the second part is the name of the level object, and the third part is the value of the member in the level. The parts of the unique value are separated by a value separation string, which by default is double colons (`::`). The following is an example of a unique member value of a level named `YEAR` in a hierarchy named `CALENDAR_YEAR` in a dimension named `TIME_AWJ`.

`  CALENDAR_YEAR::YEAR::CY2001`

The third part of a unique value is the local value. The local value in the preceding example identifies the calendar year 2001.

#### 1.2.3 Creating Cursors

To retrieve the data specified by a `Source`, you create an `oracle.olapi.data.cursor.Cursor` for that `Source`. You then use this `Cursor` to request and retrieve the data from the data store. You can specify the amount of data that the `Cursor` retrieves in each fetch operation (for example, enough to fill a 40-cell table in the user interface). Oracle OLAP then efficiently manages the timing, sizing, and caching of the data blocks that it retrieves for your application, so that you do not need to do so. For information about `Cursor` objects, see [Understanding Cursor Classes and Concepts](understanding-cursor-classes-and-concepts.md) and [Retrieving Query Results](retrieving-query-results.md).

### 1.3 Sample Schema for OLAP Java API Examples

The examples of OLAP Java API code in this documentation are excerpts from a set of example programs that are available on the Oracle Technology Network (OTN) website. One example, `CreateAndBuildAW.java`, has methods that create and build an analytic workspace. Another example, `SpecifyAWValues`, calls the methods of `CreateAndBuildAW.java` and specifies values, such as names for the metadata objects and names of columns of relational tables for mapping the metadata objects to data sources. The analytic workspace produced by these examples is named `GLOBAL_AWJ`. Other examples query that analytic workspace. The metadata objects in the analytic workspace are mapped to columns in relational tables that are in the Global schema.

From the OTN website, you can download a file that contains SQL scripts that create the Global schema and a file that contains the example programs. The OTN website is at [`http://www.oracle.com/technetwork/database/options/olap/index.html`](http://www.oracle.com/technetwork/database/options/olap/index.html).

To get either file, select Sample Code and Schemas in the Download section of the web page. To get the sample schema, select Global Schema 11g. To get the example programs, select Example Programs for Documentation and then select Download the Example Programs for 11g Release 2 (11.2) to download the compressed file that contains the examples.

The example programs are in a package structure that you can easily add to your development environment. The classes include a base class that the example program classes extend, and utility classes that they use. The base class is `BaseExample11g.java`. The utility classes include `Context11g.java` and `CursorPrintWriter.java`. The `Context11g.java` class has methods that create a connection to an Oracle Database instance, that store metadata objects, that return the stored metadata objects, and that create `Cursor` objects. The `CursorPrintWriter.java` class is a `PrintWriter` that has methods that display the contents of `Cursor` objects.

The OLAP metadata objects are created and built by the `CreateAndBuildAW.java` and the `SpecifyAWValues` programs. Those metadata objects include the following:

- GLOBAL_AWJ, which is the analytic workspace that contains the other objects.

- PRODUCT_AWJ, which is a dimension for products. It has one hierarchy named PRODUCT_PRIMARY. The lowest level of the hierarchy has product item identifiers and the higher levels have product family, class, and total products identifiers.

- CUSTOMER_AWJ, which is a dimension for customers. It has two hierarchies named SHIPMENTS and MARKETS. The lowest level of each hierarchy has customer identifiers and higher levels have warehouse, region, and total customers, and account, market segment, and total market identifiers, respectively.

- TIME_AWJ, which is a dimension for time values. It has a hierarchy named CALENDAR_YEAR. The lowest level has month identifiers, and the other levels have quarter and year identifiers.

- CHANNEL_AWJ, which is a dimension for sales channels. It has one hierarchy named CHANNEL_PRIMARY. The lowest level has sales channel identifiers and the higher level has the total channel identifier.

- UNITS_CUBE_AWJ, which is a cube that contains the measures COST, SALES, and UNITS. COST has values for the costs of product units. SALES has the dollar amounts for the sales of product units. UNITS has values for the quantities of product units sold. The cube is dimensioned by all four dimensions. The aggregation method for the cube is `SUM`, in which each the value for each parent is the sum of the values of the children of the parent.

- PRICE_CUBE_AWJ, which is a cube that contains the measures UNIT_COST and UNIT_PRICE. UNIT_COST has the costs of the units. UNIT_PRICE has the prices of the units. The cube is dimensioned by the PRODUCT_AWJ and TIME_AWJ dimensions. The aggregation method for the cube is `AVG`, in which the value for each parent is the average of the values of the children of the parent.

For an example of a program that discovers the OLAP metadata for the analytic workspace, see [Discovering Metadata](discovering-metadata.md).

### 1.4 Tasks That an OLAP Java API Application Performs

A client application that uses the OLAP Java API typically performs the following tasks:

1.  Connects to the data store and creates a `DataProvider` and a `UserSession`.

2.  Creates or discovers metadata objects.

3.  Deploys, maps, and builds metadata objects, as needed.

4.  Specifies queries that select and manipulate data.

5.  Retrieves query results.

The rest of this topic briefly describes these tasks, and the rest of this guide provides detailed information about how to accomplish them.

Task 1: Connect to the Data Store and Create a DataProvider and UserSession
You connect to the data store by identifying some information about the target Oracle Database instance and specifying this information in a JDBC connection method. Having established a connection, you create a `DataProvider` and use it and the connection to create a `UserSession`. For more information about connecting and creating a `DataProvider` and `UserSession`, see "[Connecting to Oracle OLAP](discovering-metadata.md)" in [Discovering Metadata](discovering-metadata.md).

Task 2: Create or Discover Metadata Objects
You use the `DataProvider` to get an `MdmMetadataProvider`. The `MdmMetadataProvider` gives access to all of the metadata objects in the data store. You next obtain the `MdmRootSchema` object by calling the `getRootSchema` method of the `MdmMetdataProvider`. The `MdmRootSchema` object contains all of the OLAP metadata objects in the database. From the `MdmRootSchema`, you get the `MdmDatabaseSchema` objects for the schemas that the current user has permission to access. An `MdmDatabaseSchema` represents a named Oracle Database user as returned by the SQL statement `SELECT username FROM all_users`.

From an `MdmDatabaseSchema`, you can discover the existing metadata objects that are owned by the schema or you can create new ones. Methods such as `getMeasures` and `getDimensions` get all of the measures or dimensions owned by the `MdmDatabaseSchema`. Methods such as `findOrCreateAW` and `findOrCreateCube` get an analytic workspace or cube, if it exists, or create one if it does not already exist.

From a top-level metadata object contained by the `MdmDatabaseSchema`, such as an analytic workspace, cube, or dimension, you can get the objects that it contains. For example, from an `MdmPrimaryDimension`, you can get the hierarchies, levels, and attributes that are associated with it. Having determined the metadata objects that are available to the user, you can present relevant lists of objects to the user for data selection and manipulation.

For a description of the metadata objects, see [Understanding OLAP Java API Metadata](understanding-olap-java-api-metadata.md). For information about how you can discover the available metadata, see [Discovering Metadata](discovering-metadata.md).

Task 3: Deploy, Map, and Build Objects
If you create a new `MdmCube` or `MdmPrimaryDimension`, you must deploy it as an analytic workspace object or as a relational OLAP (Rolap) object. To deploy a cube, you call an `MdmCube` method such as `findOrCreateAWCubeOrganization`. To deploy a `dimension`, you call an `MdmPrimaryDimension` method such as `findOrCreateAWPrimaryDimensionOrganization`.

If you create a new metadata object that represents data, you must specify an `Expression` that maps the metadata object to a relational source table or view, or that Oracle OLAP uses to generate the data. For objects that are contained by an analytic workspace, you can build the metadata objects after mapping them. For information on creating metadata, deploying, mapping, and building metadata objects, see [Creating Metadata and Analytic Workspaces](creating-metadata-and-analytic-workspaces.md).

Task 4: Select and Calculate Data Through Queries
An OLAP Java API application can construct queries against the data store. A typical application user interface provides ways for the user to select data and to specify the operations to perform using the data. Then, the data manipulation code translates these instructions into queries against the data store. The queries can be as simple as a selection of dimension members, or they can be complex, including several aggregations and calculations involving the measure values that are specified by selections of dimension members.

The OLAP Java API object that represents a query is a `Source`. Metadata objects that represent data are extensions of the `MdmSource` class. From an `MdmSource`, such as an `MdmMeasure` or an `MdmPrimaryDimension`, you can get a `Source` object. With the methods of a `Source` object, you can produce other `Source` objects that specify a selection of the elements of the `Source`, or that specify calculations or other operations to perform on the values of a `Source`.

If you are implementing a simple user interface, then you might use only the methods of a `Source` object to select and manipulate the data that users specify in the interface. However, if you want to offer your users multistep selection procedures and the ability to modify queries or undo individual steps in their selections, then you should design and implement `Template` classes. Within the code for each `Template`, you use the methods of the `Source` classes, but the `Template` classes themselves allow you to dynamically modify and refine even the most complex query. In addition, you can write general-purpose `Template` classes and reuse them in various parts of your application.

For information about working with `Source` objects, see [Understanding Source Objects](understanding-source-objects.md). For information about working with `Template` objects, see [Creating Dynamic Queries](creating-dynamic-queries.md).

Task 5: Retrieve Query Results
When users of an OLAP Java API application are selecting, calculating, combining, and generally manipulating data, they also want to see the results of their work. This means that the application must retrieve the result sets of queries from the data store and display the data in multidimensional form. To retrieve a result set for a query through the OLAP Java API, you create a `Cursor` for the `Source` that specifies the query.

You can also get the SQL that Oracle OLAP generates for a query. To do so, you create a `SQLCursorManager` for the `Source` instead of creating a `Cursor`. The `generateSQL` method of the `SQLCursorManager` returns the SQL specified by the `Source`. You can then retrieve the data by means outside of the OLAP Java API.

Because the OLAP Java API was designed to deal with a multidimensional view of data, a `Source` can have a multidimensional result set. For example, a `Source` can represent an `MdmMeasure` that is dimensioned by four `MdmPrimaryDimension` objects. Each `MdmPrimaryDimension` has an associated `Source`. You can create a query by joining the `Source` objects for the dimensions to the `Source` for the measure. The resulting query has the `Source` for the measure as the base and it has the `Source` objects for the dimensions as outputs.

A `Cursor` for a query `Source` has the same structure as the `Source`. For example, the `Cursor` for the `Source` just mentioned has base values that are the measure data. The `Cursor` also has four outputs. The values of the outputs are those of the `Source` objects for the dimensions.

To retrieve all of the items of data through a `Cursor`, you can loop through the multidimensional `Cursor` structure. This design is well adapted to the requirements of standard user interface objects for painting the computer screen. It is especially well adapted to the display of data in multidimensional format.

For more information about using `Source` objects to specify a query, see [Understanding Source Objects](understanding-source-objects.md). For more information about using `Cursor` objects to retrieve data, see [Understanding Cursor Classes and Concepts](understanding-cursor-classes-and-concepts.md). For more information about the `SQLCursorManager` class, see Oracle OLAP Java API Reference.
