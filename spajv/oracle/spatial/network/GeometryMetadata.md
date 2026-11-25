Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](AStarCostFunction.md)
- [Next Class](GoalNode.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.network

## Class GeometryMetadata

- java.lang.Object

- - oracle.spatial.network.GeometryMetadata

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Cloneable

  ------------------------------------------------------------------------



      public class GeometryMetadata
      extends java.lang.Object
      implements java.lang.Cloneable, java.io.Serializable

  This class defines geometry metadata for Oracle SDO_GEOMETRY.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                            |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `GeometryMetadata``(java.sql.Connection conn, java.lang.String owner, java.lang.String tableName, java.lang.String columnName)`<br>Constructs the geometry metadata from the database. |
    | `GeometryMetadata``(java.lang.String owner, java.lang.String tableName)`<br>Constructs the geometry metadata without a geometry column.                                                |
    | `GeometryMetadata``(java.lang.String owner, java.lang.String tableName, java.lang.String columnName, int srid, int noOfDims)`<br>Constructs the geometry metadata.                     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type  | Method and Description                                                           |
    |--------------------|----------------------------------------------------------------------------------|
    | `java.lang.String` | `getColumnName``()`<br>Returns the geometry column name.                         |
    | `int`              | `getNoOfDims``()`<br>Returns the number of dimensions.                           |
    | `int`              | `getSrid``()`<br>Returns the SRID.                                               |
    | `java.lang.String` | `getTableName``()`<br>Deprecated.                                                |
    | `java.lang.String` | `getTableName``(boolean addSchemaName)`<br>Returns the geometry table name.      |
    | `void`             | `setColumnName``(java.lang.String columnName)`<br>Sets the geometry column name. |
    | `void`             | `setNoOfDims``(int noOfDims)`<br>Sets the number of dimensions                   |
    | `void`             | `setSrid``(int srid)`<br>Sets the SRID                                           |
    | `void`             | `setTableName``(java.lang.String tableName)`<br>Sets the table name              |
    | `java.lang.String` | `toString``()`                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeometryMetadata

          public GeometryMetadata(java.lang.String owner,
                                  java.lang.String tableName)

      Constructs the geometry metadata without a geometry column.

    <!-- -->

    - #### GeometryMetadata

          public GeometryMetadata(java.lang.String owner,
                                  java.lang.String tableName,
                                  java.lang.String columnName,
                                  int srid,
                                  int noOfDims)

      Constructs the geometry metadata.
      Parameters:
      `tableName` - the geometry table name

      `columnName` - the geometry column name

      `srid` - the SRID

      `noOfDims` - the number of dimensions for the specified geometry table

    <!-- -->

    - #### GeometryMetadata

          public GeometryMetadata(java.sql.Connection conn,
                                  java.lang.String owner,
                                  java.lang.String tableName,
                                  java.lang.String columnName)

      Constructs the geometry metadata from the database.
      Parameters:
      `conn` - the database connection

      `tableName` - the geometry table name

      `columnName` - the geometry column name

  <!-- -->

  - ### Method Detail

    - #### getTableName

          public java.lang.String getTableName()

      Deprecated. 
      Returns the geometry table name.

    <!-- -->

    - #### getTableName

          public java.lang.String getTableName(boolean addSchemaName)

      Returns the geometry table name. If addSchemaName is set to false, the table name stored in network metadata will be returned; otherwise, the table name prefixed with the owner schema name will be returned.
      Parameters:
      `addSchemaName` - prefix schema name or not

    <!-- -->

    - #### setTableName

          public void setTableName(java.lang.String tableName)

      Sets the table name

    <!-- -->

    - #### getColumnName

          public java.lang.String getColumnName()

      Returns the geometry column name.

    <!-- -->

    - #### setColumnName

          public void setColumnName(java.lang.String columnName)

      Sets the geometry column name.

    <!-- -->

    - #### getSrid

          public int getSrid()

      Returns the SRID.

    <!-- -->

    - #### setSrid

          public void setSrid(int srid)

      Sets the SRID

    <!-- -->

    - #### getNoOfDims

          public int getNoOfDims()

      Returns the number of dimensions.

    <!-- -->

    - #### setNoOfDims

          public void setNoOfDims(int noOfDims)

      Sets the number of dimensions

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](AStarCostFunction.md)
- [Next Class](GoalNode.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
