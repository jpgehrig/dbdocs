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

- [Prev Class](JDBCUtils.md)
- [Next Class](NFEConnectionDataSource.md)

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

## Class NFEAbstractDataSource

- java.lang.Object

- - oracle.spatial.network.nfe.io.jdbc.NFEAbstractDataSource

<!-- -->

- All Implemented Interfaces:
  [NFEDataSource](../NFEDataSource.md)

  <!-- -->

  Direct Known Subclasses:
  [JdbcDataSource](JdbcDataSource.md)

  ------------------------------------------------------------------------



      public abstract class NFEAbstractDataSource
      extends java.lang.Object
      implements NFEDataSource

  This class provides an implementation of the NFEDataSource interface that will return a connection already bind to the workspace specified by the method setActiveWorkspace. The method getConnectionWihoutWorkspaceHandling has to return a simple connection that will be used by the implementation of getConnection. LIVE is used as default workspace.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description  |
    |------------------------------|
    | `NFEAbstractDataSource``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type              | Method and Description                                                                                                                |
    |--------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`             | `getActiveWorkspace``()`<br>Returns the active workspace.                                                                             |
    | `java.sql.Connection`          | `getConnection``()`<br>Returns a Connection and throws the appropriate exception if it can not do so.                                 |
    | `abstract java.sql.Connection` | `getConnectionWihoutWorkspaceHandling``()`<br>Returns a database connection and throws the appropriate exception if it can not do so. |
    | `void`                         | `setActiveWorkspace``(java.lang.String workspaceName)`<br>Sets the active workspace that will be used by the connection.              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEAbstractDataSource

          public NFEAbstractDataSource()

  <!-- -->

  - ### Method Detail

    - #### getConnection

          public java.sql.Connection getConnection()
                                            throws InvalidDBConnectionException

      Description copied from interface: [`NFEDataSource`](../NFEDataSource.md)
      Returns a Connection and throws the appropriate exception if it can not do so. The connection will use the active workspace.
      Specified by:
      [`getConnection`](../NFEDataSource.md) in interface [`NFEDataSource`](../NFEDataSource.md)

      Returns:
      connection

      Throws:
      [`InvalidDBConnectionException`](../InvalidDBConnectionException.md) - if the connection is not valid.

    <!-- -->

    - #### setActiveWorkspace

          public void setActiveWorkspace(java.lang.String workspaceName)

      Description copied from interface: [`NFEDataSource`](../NFEDataSource.md)
      Sets the active workspace that will be used by the connection. Reload the model after to change the active workspace.
      Specified by:
      [`setActiveWorkspace`](../NFEDataSource.md) in interface [`NFEDataSource`](../NFEDataSource.md)

      Parameters:
      `workspaceName` - name of the workspace that will be used by the connection

    <!-- -->

    - #### getActiveWorkspace

          public java.lang.String getActiveWorkspace()

      Description copied from interface: [`NFEDataSource`](../NFEDataSource.md)
      Returns the active workspace. The method should not return null. If the model is not version enabled then LIVE should be returned.
      Specified by:
      [`getActiveWorkspace`](../NFEDataSource.md) in interface [`NFEDataSource`](../NFEDataSource.md)

      Returns:
      active workspace

    <!-- -->

    - #### getConnectionWihoutWorkspaceHandling

          public abstract java.sql.Connection getConnectionWihoutWorkspaceHandling()
                                                                            throws InvalidDBConnectionException

      Returns a database connection and throws the appropriate exception if it can not do so.
      Returns:
      connection

      Throws:
      [`InvalidDBConnectionException`](../InvalidDBConnectionException.md) - if the connection is not valid.

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

- [Prev Class](JDBCUtils.md)
- [Next Class](NFEConnectionDataSource.md)

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
