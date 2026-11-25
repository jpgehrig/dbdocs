This chapter describes how to connect to an Oracle Database instance and how to discover existing Oracle OLAP metadata objects. It includes the following topics:

- Connecting to Oracle OLAP

- Overview of the Procedure for Discovering Metadata

- Creating an MdmMetadataProvider

- Getting the MdmSchema Objects

- Getting the Contents of an MdmSchema

- Getting the Objects Contained by an MdmPrimaryDimension

- Getting the Source for a Metadata Object

### 3.1 Connecting to Oracle OLAP

To connect to the Oracle OLAP server in an Oracle Database instance, an OLAP Java API client application uses the Oracle implementation of the Java Database Connectivity (JDBC) API. The Oracle JDBC classes that you use to establish a connection to Oracle OLAP are in the Java archive file `ojdbc6.jar`. For information about getting that file, see [Setting Up the Development Environment](setting-up-development-environment.md).

The following topics describe creating a connection to Oracle OLAP.

- Prerequisites for Connecting

- Establishing a Connection

- Closing the Connection and the DataProvider

#### 3.1.1 Prerequisites for Connecting

Before attempting to connect to the Oracle OLAP server, ensure that the following requirements are met:

- The Oracle Database instance is running and was installed with the OLAP option.

- The Oracle Database user ID that you are using for the connection has access to the relational schemas that contain the data.

- The Oracle JDBC and OLAP Java API jar files are in your application development environment. For information about setting up the required jar files, see [Setting Up the Development Environment](setting-up-development-environment.md).

#### 3.1.2 Establishing a Connection

To connect to the OLAP server, perform the following steps:

1.  Create a JDBC connection to the database.
2.  Create a `DataProvider` and a `UserSession`.

These steps are described in the following topics:

- Creating a JDBC Connection

- Creating a DataProvider and a UserSession

##### 3.1.2.1 Creating a JDBC Connection

One way to create a connection to an Oracle Database instance is to use `oracle.jdbc.OracleDataSource` and `oracle.jdbc.OracleConnection` objects. For example, the following code creates an `oracle.jdbc.OracleDataSource`, sets properties of the object, and then gets a JDBC `OracleConnection` object from the `OracleDataSource`.

The values of the properties for the `OracleDataSource` are from a `java.util.Properties` object. The `url` property has the form `jdbc:oracle:thin:@serverName:portNumber:sid`, where `serverName` is the hostname of the server on which the Oracle Database instance is running, `portNumber` is the number of the TCP/IP listener port for the database, and `sid` is the system identifier (SID) of the database instance.

Example 3-1 Getting a JDBC OracleConnection

    oracle.jdbc.OracleConnection conn = null;
    try
    {
      OracleDataSource ods = new OracleDataSource();
      ods.setURL(props.getProperty("url"));
      ods.setUser(props.getProperty("user"));
      ods.setPassword(props.getProperty("password"));
      conn = (oracle.jdbc.OracleConnection) ods.getConnection();
    }
    catch(SQLException e)
    {
      System.out.println("Connection attempt failed. " + e);
    }

In the example, the connection uses the Oracle JDBC thin driver. There are many ways to specify your connection characteristics using the `getConnection` method. There are also other ways to connect to an Oracle Database instance. For more information about Oracle JDBC connections, see Oracle Database JDBC Developer’s Guide.

After you have the `OracleConnection` object, you can create OLAP Java API `DataProvider` and `UserSession` objects.

##### 3.1.2.2 Creating a DataProvider and a UserSession

The following code creates a `DataProvider` and a `UserSession`. The `conn` object is the `OracleConnection` from Example 3-1.

Example 3-2 Creating a DataProvider

    DataProvider dp = new DataProvider();
    try
    {
      UserSession session = dp.createSession(conn);
    }
    catch(SQLException e)
    {
      System.out.println("Could not create a UserSession. " + e);
    }

Using the `DataProvider`, you can get the `MdmMetadataProvider`, which is described in "Creating an MdmMetadataProvider". You use the `DataProvider` to get the `TransactionProvider` and to create `Source` and `CursorManager` objects as described in [Understanding Source Objects](understanding-source-objects.md) and [Making Queries Using Source Methods](making-queries-using-source-methods.md).

#### 3.1.3 Closing the Connection and the DataProvider

If you are finished using the OLAP Java API, but you want to continue working in your JDBC connection to the database, then use the `close` method of your `DataProvider` to release the OLAP Java API resources.

    dp.close();     // dp is the DataProvider

When you have completed your work with the database, use the `OracleConnection.close` method.

Example 3-3 Closing the Connection

    try
    {
      conn.close();     // conn is the OracleConnection
    }
    catch(SQLException e)
    {
      System.out.println("Cannot close the connection. " + e);
    }

### 3.2 Overview of the Procedure for Discovering Metadata

The OLAP Java API provides access to the data of an analytic workspace or that is in relational structures. This collection of data is the data store for the application.

Potentially, the data store includes all of the subchemas of the `MdmRootSchema`. However, the scope of the data store that is visible when an application is running depends on the database privileges that apply to the user ID through which the connection was made. A user can see all of the `MdmDatabaseSchema` objects that exist under the `MdmRootSchema`, but the user can see the objects that are owned by an `MdmDatabaseSchema` only if the user has access rights to the metadata objects,

The following topics describe discovering metadata.

- Purpose of Discovering the Metadata

- Steps in Discovering the Metadata

#### 3.2.1 Purpose of Discovering the Metadata

The metadata objects in the data store help your application to make sense of the data. They provide a way for you to find out what data is available, how it is structured, and what the characteristics of it are.

Therefore, after connecting, your first step is to find out what metadata is available. You can then present choices to the end user about what data to select or calculate and how to display it.

After an application discovers the metadata, it typically goes on to create queries for selecting, calculating, and otherwise manipulating the data. To work with data in these ways, you must get the `Source` objects from the metadata objects. These `Source` objects specify the data for querying. For more information on `Source` objects, see [Understanding Source Objects](understanding-source-objects.md).

#### 3.2.2 Steps in Discovering the Metadata

Before investigating the metadata, your application must make a connection to Oracle OLAP. Then, your application might perform the following steps:

1.  Create a `DataProvider`.
2.  Get the `MdmMetadataProvider` from the `DataProvider`.
3.  Get the `MdmRootSchema` from the `MdmMetadataProvider`.
4.  Get all of the `MdmDatabaseSchema` objects or get individual ones.
5.  Get the `MdmCube`, `MdmDimension`, and `MdmOrganizationalSchema` objects owned by the `MdmDatabaseSchema` objects.

The following topics describe these steps in detail.

- Creating an MdmMetadataProvider

- Getting the MdmSchema Objects

- Getting the Contents of an MdmSchema

- Getting the Objects Contained by an MdmPrimaryDimension

### 3.3 Creating an MdmMetadataProvider

An `MdmMetadataProvider` gives access to the metadata in a data store by providing the `MdmRootSchema`. Before you can create an `MdmMetadataProvider`, you must create a `DataProvider` as described in [Creating Metadata and Analytic Workspaces](creating-metadata-and-analytic-workspaces.md). Example 3-4 creates an `MdmMetadataProvider`. In the example, `dp` is the `DataProvider`.

Example 3-4 Creating an MdmMetadataProvider

    MdmMetadataProvider mp = null;
    try
    {
      mp = (MdmMetadataProvider) dp.getMdmMetadataProvider();
    }
    catch (Exception e)
    {
      println("Cannot get the MDM metadata provider. " + e);
    }

### 3.4 Getting the MdmSchema Objects

The Oracle OLAP metadata objects that provide access to the data in a data store are organized by `MdmSchema` objects. The top-level `MdmSchema` is the `MdmRootSchema`. Getting the `MdmRootSchema` is the first step in exploring the metadata in your data store. From the `MdmRootSchema`, you can get the `MdmDatabaseSchema` objects. The `MdmRootSchema` has an `MdmDatabaseSchema` for each database user. An `MdmDatabaseSchema` can have `MdmOrganizationalSchema` objects that organize the metadata objects owned by the `MdmDatabaseSchema`.

Example 3-5 Getting the MdmSchema Objects

This example demonstrates getting the `MdmRootSchema`, the `MdmDatabaseSchema` objects under it, and any `MdmOrganizationalSchema` objects under them.

    private void getSchemas(MdmMetadataProvider mp)
    {
      MdmRootSchema mdmRootSchema = (MdmRootSchema)mp.getRootSchema();
      List<MdmDatabaseSchema> dbSchemas = mdmRootSchema.getDatabaseSchemas();
      for(MdmDatabaseSchema mdmDBSchema : dbSchemas)
      {
        println(mdmDBSchema.getName());
        getOrgSchemas(mdmDBSchema);
      }
    }

    private void getOrgSchemas(MdmSchema mdmSchema)
    {
      ArrayList orgSchemaList = new ArrayList();

      if (mdmSchema instanceof MdmDatabaseSchema)
      {
        MdmDatabaseSchema mdmDBSchema = (MdmDatabaseSchema) mdmSchema;
        orgSchemaList = (ArrayList) mdmDBSchema.getOrganizationalSchemas();
      }
      else if (mdmSchema instanceof MdmOrganizationalSchema)
      {
        MdmOrganizationalSchema mdmOrgSchema = (MdmOrganizationalSchema)
                                                mdmSchema;
        orgSchemaList = (ArrayList) mdmOrgSchema.getOrganizationalSchemas();
      }

      if (orgSchemaList.size() > 0)
      {
        println("The MdmOrganizationalSchema subschemas of "
                + mdmSchema.getName() + " are:");
        Iterator orgSchemaListItr = orgSchemaList.iterator();
        while (orgSchemaListItr.hasNext())
        {
          MdmOrganizationalSchema mdmOrgSchema = (MdmOrganizationalSchema)
                                                orgSchemaListItr.next();
          println(mdmOrgSchema.getName());
          getOrgSchemas(mdmOrgSchema);
        }
      }
      else
      {
        println(mdmSchema.getName() + " does not have any" +
                " MdmOrganizationalSchema subschemas.");
      }
    }

Example 3-6 Getting a Single MdmDatabaseSchema

Rather than getting all of the `MdmDatabaseSchema` objects, you can use the `getDatabaseSchema` method of the `MdmRootSchema` to get the schema for an individual user. This example demonstrates getting the `MdmDatabaseSchema` for the GLOBAL user.

    MdmDatabaseSchema mdmGlobalSchema = mdmRootSchema.getDatabaseSchema("GLOBAL");

### 3.5 Getting the Contents of an MdmSchema

From an `MdmSchema`, you can get all of the subschema, `MdmCube`, `MdmPrimaryDimension`, and `MdmMeasure` objects that it contains. Also, the `MdmRootSchema` has an `MdmMeasureDimension` that has a `List` of all of the available `MdmMeasure` objects.

If you want to display all of the dimensions and methods that are owned by a particular user, then you could get the lists of dimensions and measures from the `MdmDatabaseSchema` for that user.

Example 3-7 Getting the Dimensions and Measures of an MdmDatabaseSchema

This example gets the dimensions and measures from the `MdmDatabaseSchema` from Example 3-6. It displays the name of each dimension and measure.

    private void getObjects(MdmDatabaseSchema mdmGlobalSchema)
    {
      List dimList = mdmGlobalSchema.getDimensions();
      String objName = mdmGlobalSchema.getName() + " schema";
      getNames(dimList, "dimensions", objName);

      List measList = mdmGlobalSchema.getMeasures();
      getNames(measList, "measures", objName);
    }

    private void getNames(List objectList, String objTypes, String objName)
    {
      println("The " + objTypes + " of the " + objName + " are:");
      Iterator objListItr = objectList.iterator();
      while (objListItr.hasNext())
      {
        MdmObject mdmObj = (MdmObject) objListItr.next();
        println(mdmObj.getName());
      }
    }

The output of the example is the following.

    The dimensions of the GLOBAL schema are:
    CHANNEL_AWJ
    CUSTOMER_AWJ
    PRODUCT_AWJ
    TIME_AWJ
    The measures of the GLOBAL schema are:
    UNIT_COST
    UNIT_PRICE
    SALES
    UNITS
    COST

Example 3-8 Getting the Dimensions and Measures of an MdmCube

To display just the dimensions and measures associated with an `MdmCube`, you could use the `findOrCreateCube` method of an `MdmDatabaseSchema` to get the cube and then get the dimensions and measures of the cube. This example gets an `MdmCube` from the `MdmDatabaseSchema` of Example 3-6 and displays the names of the dimensions and measures associated with it using the `getNames` method of Example 3-7.

    private void getCubeObjects(MdmDatabaseSchema mdmGlobalSchema)
    {
      MdmCube mdmUnitsCube = (MdmCube)
        mdmGlobalSchema.findOrCreateCube("PRICE_CUBE_AWJ");
      String objName = mdmUnitsCube.getName() + " cube";
      List dimList = mdmUnitsCube.getDimensions();
      getNames(dimList, "dimensions", objName);

      List<MdmMeasure> measList = mdmUnitsCube.getMeasures();
      getNames(measList, "measures", objName);
    }

The output of the example is the following.

    The dimensions of the PRICE_CUBE_AWJ cube are:
    TIME_AWJ
    PRODUCT_AWJ
    The measures of the PRICE_CUBE_AWJ cube are:
    UNIT_COST
    UNIT_PRICE

### 3.6 Getting the Objects Contained by an MdmPrimaryDimension

In discovering the metadata objects to use in creating queries and displaying the data, an application typically gets the `MdmSubDimension` components of an `MdmPrimaryDimension` and the `MdmAttribute` objects that are associated with the dimension. The following topics demonstrate getting the components and attributes of a dimension.

- Getting the Hierarchies and Levels of an MdmPrimaryDimension

- Getting the Attributes for an MdmPrimaryDimension

#### 3.6.1 Getting the Hierarchies and Levels of an MdmPrimaryDimension

An `MdmPrimaryDimension` has zero or more component `MdmHierarchy` objects, which you can obtain by calling the `getHierarchies` method of the dimension. That method returns a `List` of `MdmHierarchy` objects. The levels of an `MdmPrimaryDimension` are represented by `MdmDimensionLevel` objects.

If an `MdmHierarchy` is an `MdmLevelHierarchy`, then it has `MdmHierarchyLevel` objects that associate `MdmDimensionLevel` objects with it. You can obtain the `MdmHierarchyLevel` objects by calling the `getHierarchyLevels` method of the `MdmLevelHierarchy`.

Example 3-9 Getting the Hierarchies and Levels of a Dimension

This example gets an `MdmPrimaryDimension` from the `MdmDatabaseSchema` of Example 3-6 and displays the names of the hierarchies and the levels associated with them.

    private void getHierarchiesAndLevels(MdmDatabaseSchema mdmGlobalSchema)
    {
      MdmPrimaryDimension mdmCustDim = (MdmPrimaryDimension)
        mdmGlobalSchema.findOrCreateStandardDimension("CUSTOMER_AWJ");
      List<MdmHierarchy> hierList = mdmCustDim.getHierarchies();
      println("The hierarchies of the dimension are:");
      for (MdmHierarchy mdmHier : hierList)
      {
        println(mdmHier.getName());
        if (mdmHier instanceof MdmLevelHierarchy)
        {
          MdmLevelHierarchy mdmLevelHier = (MdmLevelHierarchy) mdmHier;
          List<MdmHierarchyLevel> hierLevelList = mdmLevelHier.getHierarchyLevels();
          println("  The levels of the hierarchy are:");
          for (MdmHierarchyLevel mdmHierLevel : hierLevelList)
          {
            println("  " + mdmHierLevel.getName());
          }
        }
      }
    }

The output of Example 3-9 is the following.

    The hierarchies of the dimension are:
    SHIPMENTS
      The levels of the hierarchy are:
      TOTAL_CUSTOMER
      REGION
      WAREHOUSE
      SHIP_TO
    MARKETS
      The levels of the hierarchy are:
      TOTAL_MARKET
      MARKET_SEGMENT
      ACCOUNT
      SHIP_TO

#### 3.6.2 Getting the Attributes for an MdmPrimaryDimension

An `MdmPrimaryDimension` and the hierarchies and levels of it have associated `MdmAttribute` objects. You can obtain many of the attributes by calling the `getAttributes` method of the dimension, hierarchy, or level. That method returns a `List` of `MdmAttribute` objects that an application has explicitly added to or specified for the `MdmPrimaryDimension`. You can obtain specific attributes, such as a short or long description attribute or a parent attribute by calling the appropriate method of an `MdmPrimaryDimension` or an `MdmHierarchy`.

Example 3-10 Getting the MdmAttribute Objects of an MdmPrimaryDimension

This example demonstrates getting the `MdmAttribute` objects for an `MdmPrimaryDimension`. It also gets the parent attribute separately. The example displays the names of the `MdmAttribute` objects. The attribute names that end in `_LD` and `_SD` are the attributes that are added to the `MdmHierarchyLevel` objects, as mentioned in "[Populating OLAP Views with Hierarchical Attribute Values](understanding-olap-java-api-metadata.md)".

    private void getAttributes(MdmDatabaseSchema mdmGlobalSchema)
    {
      MdmTimeDimension mdmTimeDim = (MdmTimeDimension)
        mdmGlobalSchema.findOrCreateTimeDimension("TIME_AWJ");
      List attrList = mdmTimeDim.getAttributes();
      Iterator attrListItr = attrList.iterator();
      println("The MdmAttribute objects of " + mdmTimeDim.getName() + " are:");
      while (attrListItr.hasNext())
      {
        MdmAttribute mdmAttr = (MdmAttribute) attrListItr.next();
        println("  " + mdmAttr.getName());
      }

      MdmAttribute mdmParentAttr = mdmTimeDim.getParentAttribute();
      println("The parent attribute is " + mdmParentAttr.getName() + ".");
    }

The output of the example is the following.

    The MdmAttribute objects of TIME_AWJ are:
     LONG_DESCRIPTION
     SHORT_DESCRIPTION
     END_DATE
     TIME_SPAN
     TOTAL_TIME_LD
     YEAR_LD
     QUARTER_LD
     MONTH_LD
     TOTAL_TIME_SD
     YEAR_SD
     QUARTER_SD
     MONTH_SD
     TOTAL_TIME_ED
     YEAR_ED
     QUARTER_ED
     MONTH_ED
     TOTAL_TIME_TS
     YEAR_TS
     QUARTER_TS
     MONTH_TS
    The parent attribute is PARENT_ATTRIBUTE.

### 3.7 Getting the Source for a Metadata Object

A metadata object represents a set of data, but it does not provide the ability to create queries on that data. The object is informational. It records the existence, structure, and characteristics of the data. It does not give access to the data values.

To access the data values for a metadata object, an application gets the `Source` object for that metadata object. The `Source` for a metadata object is a primary `Source`.

To get the primary `Source` for a metadata object, an application calls the `getSource` method of that metadata object. For example, if an application needs to display the quantity of product units sold during the year 1999, then it must use the `getSource` method of the `MdmMeasure` for that data, which is `mdmUnits` in the following example.

Example 3-11 Getting a Primary Source for a Metadata Object

    Source units = mdmUnits.getSource();

For more information about getting and working with primary `Source` objects, see [Understanding Source Objects](understanding-source-objects.md).
