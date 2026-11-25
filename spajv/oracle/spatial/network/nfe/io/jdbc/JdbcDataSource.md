Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](DbConnectionData.md)
- [Next Class](JDBCUtils.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.network.nfe.io.jdbc

## Class JdbcDataSource

- java.lang.Object

- - [oracle.spatial.network.nfe.io.jdbc.NFEAbstractDataSource](NFEAbstractDataSource.md)

  - - oracle.spatial.network.nfe.io.jdbc.JdbcDataSource

<!-- -->

- All Implemented Interfaces:
  [NFEConnectionDataSource](NFEConnectionDataSource.md), [NFEDataSource](../NFEDataSource.md)

  ------------------------------------------------------------------------



      public class JdbcDataSource
      extends NFEAbstractDataSource
      implements NFEConnectionDataSource

  This implementation of NFEConnectionDataSource gets the connections using oracle.jdbc.OracleDataSource.
  Example to use it:

              //Initialize the datasource
              JdbcDataSource dataSource = new JdbcDataSource();
              DbConnectionData connectionData = new DbConnectionData();
              connectionData.setHost("localhost");
              connectionData.setJdbcDriverMode("thin");
              connectionData.setPort("1521");
              connectionData.setSid("view");
              connectionData.setUserName("");
              connectionData.setPassword("");
              dataSource.setConnectionData(connectionData);
              dataSource.setActiveWorkspace(NFEConstants.DEFAULT_PARENT_WORKSPACE);
              dataSource.initDatasource();


<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `JdbcDataSource``()`        |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                         |
    |-------------------------------------------|----------------------------------------------------------------------------------------------------------------|
    | `void`                                    | `closeDataSource``()`<br>Closes this data source.                                                              |
    | [`DbConnectionData`](DbConnectionData.md) | `getConnectionData``()`<br>Gets the connection data.                                                           |
    | `java.sql.Connection`                     | `getConnectionWihoutWorkspaceHandling``()`<br>Obtains a connection from the Pool Data Source.                  |
    | `void`                                    | `initDatasource``()`<br>Initializes the Pool Data Source to be able to serve DB connections.                   |
    | `void`                                    | `setConnectionData``(`[`DbConnectionData`](DbConnectionData.md)` connectionData)`<br>Sets the connection data. |
    | `void`                                    | `testConnection``()`<br>Tests a connection to the database.                                                    |

    - ### Methods inherited from class oracle.spatial.network.nfe.io.jdbc.[NFEAbstractDataSource](NFEAbstractDataSource.md)

      [`getActiveWorkspace`](NFEAbstractDataSource.md)`, `[`getConnection`](NFEAbstractDataSource.md)`, `[`setActiveWorkspace`](NFEAbstractDataSource.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.io.[NFEDataSource](../NFEDataSource.md)

      [`getActiveWorkspace`](../NFEDataSource.md)`, `[`getConnection`](../NFEDataSource.md)`, `[`setActiveWorkspace`](../NFEDataSource.md)

<!-- -->

- - ### Constructor Detail

    - #### JdbcDataSource

          public JdbcDataSource()

  <!-- -->

  - ### Method Detail

    - #### initDatasource

          public void initDatasource()
                              throws InvalidDBConnectionException

      Initializes the Pool Data Source to be able to serve DB connections.
      Specified by:
      [`initDatasource`](NFEConnectionDataSource.md) in interface [`NFEConnectionDataSource`](NFEConnectionDataSource.md)

      Throws:
      [`InvalidDBConnectionException`](../InvalidDBConnectionException.md) - if the connection is not valid.

    <!-- -->

    - #### closeDataSource

          public void closeDataSource()

      Closes this data source.

    <!-- -->

    - #### getConnectionWihoutWorkspaceHandling

          public java.sql.Connection getConnectionWihoutWorkspaceHandling()
                                                                   throws InvalidDBConnectionException

      Obtains a connection from the Pool Data Source. If the connection pool is not initialized, executes its initialization.
      Specified by:
      [`getConnectionWihoutWorkspaceHandling`](NFEAbstractDataSource.md) in class [`NFEAbstractDataSource`](NFEAbstractDataSource.md)

      Returns:
      connection.

      Throws:
      [`InvalidDBConnectionException`](../InvalidDBConnectionException.md) - if the connection is not valid.

    <!-- -->

    - #### getConnectionData

          public DbConnectionData getConnectionData()

      Gets the connection data.
      Returns:
      connection data

    <!-- -->

    - #### setConnectionData

          public void setConnectionData(DbConnectionData connectionData)

      Description copied from interface: [`NFEConnectionDataSource`](NFEConnectionDataSource.md)
      Sets the connection data.
      Specified by:
      [`setConnectionData`](NFEConnectionDataSource.md) in interface [`NFEConnectionDataSource`](NFEConnectionDataSource.md)

      Parameters:
      `connectionData` - the data for the connection

    <!-- -->

    - #### testConnection

          public void testConnection()
                              throws java.lang.Exception

      Description copied from interface: [`NFEConnectionDataSource`](NFEConnectionDataSource.md)
      Tests a connection to the database.
      Specified by:
      [`testConnection`](NFEConnectionDataSource.md) in interface [`NFEConnectionDataSource`](NFEConnectionDataSource.md)

      Throws:
      `java.lang.Exception` - thrown if something goes wrong with the test.

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](DbConnectionData.md)
- [Next Class](JDBCUtils.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
