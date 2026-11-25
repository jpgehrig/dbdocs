Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LODUserDataIO.md)
- [Next Class](LogicalBasicNetwork.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.network.lod

## Class LODUserDataIOSDO

- java.lang.Object

- - oracle.spatial.network.lod.LODUserDataIOSDO

<!-- -->

- All Implemented Interfaces:
  [LODUserDataIO](LODUserDataIO.md)

  ------------------------------------------------------------------------



      public class LODUserDataIOSDO
      extends java.lang.Object
      implements LODUserDataIO

  This implementation of LODUserDataIO reads all the user defined data from the node, link and path tables.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------|
    | `LODUserDataIOSDO``()`                                                                                                |
    | `LODUserDataIOSDO``(DbDataSource dataSource, `[`NetworkMetadata`](../NetworkMetadata.md)` metadata, int categoryId)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                          | Method and Description                                                                                                                                                                                        |
    |--------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                      | `getCategoryId``()`                                                                                                                                                                                           |
    | `DbDataSource`                             | `getDataSource``()`                                                                                                                                                                                           |
    | `static int`                               | `getIntTableType``(java.lang.String tableType)`                                                                                                                                                               |
    | [`NetworkMetadata`](../NetworkMetadata.md) | `getNetworkMetadata``()`                                                                                                                                                                                      |
    | `int`                                      | `getNumberOfCategories``()`                                                                                                                                                                                   |
    | `void`                                     | `init``(DbDataSource dataSource, `[`NetworkMetadata`](../NetworkMetadata.md)` metadata, int categoryId)`                                                                                                      |
    | `void`                                     | `init``(org.w3c.dom.Element parameter)`                                                                                                                                                                       |
    | `void`                                     | `init``(`[`NetworkMetadata`](../NetworkMetadata.md)` metadata, int categoryId)`                                                                                                                               |
    | `static void`                              | `main``(java.lang.String[] args)`                                                                                                                                                                             |
    | `void`                                     | `readUserData``(`[`LogicalPartition`](LogicalPartition.md)` partition)`                                                                                                                                       |
    | [`UserData`](UserData.md)`[]`              | `readUserData``(java.lang.String tableType, long[] ids)`<br>Reads user defined data from the database.                                                                                                        |
    | [`UserData`](UserData.md)`[]`              | `readUserData``(java.lang.String tableType, long[] ids, boolean allRecords)`                                                                                                                                  |
    | `void`                                     | `setCategoryId``(int categoryId)`                                                                                                                                                                             |
    | `void`                                     | `setDataSource``(IDataSource ds)`                                                                                                                                                                             |
    | `void`                                     | `setNetworkMetadata``(`[`NetworkMetadata`](../NetworkMetadata.md)` metadata)`                                                                                                                                 |
    | `boolean`                                  | `shareNetworkDataSource``()`                                                                                                                                                                                  |
    | `void`                                     | `writeUserData``(`[`LogicalPartition`](LogicalPartition.md)` partition)`                                                                                                                                      |
    | `void`                                     | `writeUserData``(java.lang.String tableType, long[] ids, `[`UserData`](UserData.md)`[] userData)`<br>Since the user data are stored in the node/link/path tables, you can only update the entry in the table. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LODUserDataIOSDO

          public LODUserDataIOSDO()

    <!-- -->

    - #### LODUserDataIOSDO

          public LODUserDataIOSDO(DbDataSource dataSource,
                                  NetworkMetadata metadata,
                                  int categoryId)

  <!-- -->

  - ### Method Detail

    - #### init

          public void init(DbDataSource dataSource,
                           NetworkMetadata metadata,
                           int categoryId)

    <!-- -->

    - #### init

          public void init(NetworkMetadata metadata,
                           int categoryId)

    <!-- -->

    - #### init

          public void init(org.w3c.dom.Element parameter)

    <!-- -->

    - #### getIntTableType

          public static int getIntTableType(java.lang.String tableType)

    <!-- -->

    - #### readUserData

          public UserData[] readUserData(java.lang.String tableType,
                                         long[] ids)

      Description copied from interface: [`LODUserDataIO`](LODUserDataIO.md)
      Reads user defined data from the database.
      Specified by:
      [`readUserData`](LODUserDataIO.md) in interface [`LODUserDataIO`](LODUserDataIO.md)

      Parameters:
      `tableType` - user data type, which can take the following values:
      - UserDataMetadata.NODE_TABLE_TYPE
      - UserDataMetadata.LINK_TABLE_TYPE
      - UserDataMetadata.PATH_TABLE_TYPE
      - Feature Layer Name

      `ids` - the IDs of the objects for which the user data are read

      Returns:
      array of user data maps, each corresponding to an ID of the same index in the ID array.

    <!-- -->

    - #### readUserData

          public UserData[] readUserData(java.lang.String tableType,
                                         long[] ids,
                                         boolean allRecords)

    <!-- -->

    - #### writeUserData

          public void writeUserData(java.lang.String tableType,
                                    long[] ids,
                                    UserData[] userData)

      Since the user data are stored in the node/link/path tables, you can only update the entry in the table. The ids must already exist in the tables. Caller cannot update a subset of the userdata columns. All user data columns must be set, otherwise null value will be assigned for the unspecified column.
      Specified by:
      [`writeUserData`](LODUserDataIO.md) in interface [`LODUserDataIO`](LODUserDataIO.md)

      Parameters:
      `tableType` - table type or feature layer name

      `ids` -

      `userData` -

    <!-- -->

    - #### readUserData

          public void readUserData(LogicalPartition partition)

      Specified by:
      [`readUserData`](LODUserDataIO.md) in interface [`LODUserDataIO`](LODUserDataIO.md)

    <!-- -->

    - #### writeUserData

          public void writeUserData(LogicalPartition partition)

      Specified by:
      [`writeUserData`](LODUserDataIO.md) in interface [`LODUserDataIO`](LODUserDataIO.md)

    <!-- -->

    - #### getNumberOfCategories

          public int getNumberOfCategories()

    <!-- -->

    - #### main

          public static void main(java.lang.String[] args)
                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### shareNetworkDataSource

          public boolean shareNetworkDataSource()

      Specified by:
      [`shareNetworkDataSource`](LODUserDataIO.md) in interface [`LODUserDataIO`](LODUserDataIO.md)

    <!-- -->

    - #### getDataSource

          public DbDataSource getDataSource()

      Specified by:
      [`getDataSource`](LODUserDataIO.md) in interface [`LODUserDataIO`](LODUserDataIO.md)

    <!-- -->

    - #### setDataSource

          public void setDataSource(IDataSource ds)

      Specified by:
      [`setDataSource`](LODUserDataIO.md) in interface [`LODUserDataIO`](LODUserDataIO.md)

    <!-- -->

    - #### getNetworkMetadata

          public NetworkMetadata getNetworkMetadata()

      Specified by:
      [`getNetworkMetadata`](LODUserDataIO.md) in interface [`LODUserDataIO`](LODUserDataIO.md)

    <!-- -->

    - #### setNetworkMetadata

          public void setNetworkMetadata(NetworkMetadata metadata)

      Specified by:
      [`setNetworkMetadata`](LODUserDataIO.md) in interface [`LODUserDataIO`](LODUserDataIO.md)

    <!-- -->

    - #### getCategoryId

          public int getCategoryId()

      Specified by:
      [`getCategoryId`](LODUserDataIO.md) in interface [`LODUserDataIO`](LODUserDataIO.md)

    <!-- -->

    - #### setCategoryId

          public void setCategoryId(int categoryId)

      Specified by:
      [`setCategoryId`](LODUserDataIO.md) in interface [`LODUserDataIO`](LODUserDataIO.md)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LODUserDataIO.md)
- [Next Class](LogicalBasicNetwork.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
