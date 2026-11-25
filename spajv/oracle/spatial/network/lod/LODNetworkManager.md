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

- [Prev Class](LODNetworkFactory.md)
- [Next Class](LODNetworkWrapper.md)

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

## Class LODNetworkManager

- java.lang.Object

- - oracle.spatial.network.lod.LODNetworkManager

<!-- -->

-

  ------------------------------------------------------------------------



      public class LODNetworkManager
      extends java.lang.Object

  This class is the entry point of all functionalities provided by the lod package.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    |------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`CachedNetworkIO`](CachedNetworkIO.md)     | `getCachedNetworkIO``(java.sql.Connection conn, java.lang.String networkName, java.lang.String globalNetworkName, `[`NetworkMetadata`](../NetworkMetadata.md)` metadata, boolean readFromBlob, `[`LODUserDataIO`](LODUserDataIO.md)`[] udios, `[`PartitionBlobTranslator`](PartitionBlobTranslator.md)` translator)`<br>Deprecated. <br>user getCachedNetworkIO(Connection conn, String networkName, String globalNetworkName, NetworkMetadata metadata);   |
    | `static `[`CachedNetworkIO`](CachedNetworkIO.md)     | `getCachedNetworkIO``(java.sql.Connection conn, java.lang.String networkName, java.lang.String globalNetworkName, `[`NetworkMetadata`](../NetworkMetadata.md)` metadata, `[`LODUserDataIO`](LODUserDataIO.md)`[] udios)`<br>Deprecated. <br>user getCachedNetworkIO(Connection conn, String networkName, String globalNetworkName, NetworkMetadata metadata);                                                                                               |
    | `static `[`CachedNetworkIO`](CachedNetworkIO.md)     | `getCachedNetworkIO``(DbDataSource dataSource, java.lang.String networkName, java.lang.String globalNetworkName, `[`NetworkMetadata`](../NetworkMetadata.md)` metadata)`                                                                                                                                                                                                                                                                                    |
    | `static `[`CachedNetworkIOWM`](CachedNetworkIOWM.md) | `getCachedNetworkIOWM``(java.sql.Connection conn, java.lang.String networkName, java.lang.String globalNetworkName, `[`NetworkMetadata`](../NetworkMetadata.md)` metadata, boolean readFromBlob, `[`LODUserDataIO`](LODUserDataIO.md)`[] udios, `[`PartitionBlobTranslator`](PartitionBlobTranslator.md)` translator)`<br>Deprecated. <br>use getCachedNetworkIOWM(Connection conn, String networkName, String globalNetworkName, NetworkMetadata metadata) |
    | `static `[`CachedNetworkIOWM`](CachedNetworkIOWM.md) | `getCachedNetworkIOWM``(DbDataSource dataSource, java.lang.String networkName, java.lang.String globalNetworkName, `[`NetworkMetadata`](../NetworkMetadata.md)` metadata)`                                                                                                                                                                                                                                                                                  |
    | `static `[`ConfigManager`](config/ConfigManager.md)  | `getConfigManager``()`<br>Returns the LOD configuration manager singleton.                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static OracleConnection`                            | `getConnection``(java.lang.String connectURL, java.lang.String user, java.lang.String password)`<br>Returns a new OracleConnection instance.                                                                                                                                                                                                                                                                                                                |
    | `static `[`NetworkAnalyst`](NetworkAnalyst.md)       | `getNetworkAnalyst``(`[`NetworkIO`](NetworkIO.md)` reader)`<br>Returns a new NetworkAnalyst instance, which uses the input network IO adaptor to retrieve information about the network.                                                                                                                                                                                                                                                                    |
    | `static javax.sql.DataSource`                        | `getNetworkDataSource``(java.lang.String networkName)`                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`NetworkIO`](NetworkIO.md)                 | `getNetworkIO``(java.sql.Connection conn, java.lang.String networkName, java.lang.String globalNetworkName, `[`NetworkMetadata`](../NetworkMetadata.md)` metadata, boolean readFromBlob, `[`LODUserDataIO`](LODUserDataIO.md)`[] udios, `[`PartitionBlobTranslator`](PartitionBlobTranslator.md)` translator)`<br>Deprecated. <br>use getNetworkIO(Connection conn, String networkName, String globalNetworkName, NetworkMetadata metadata);                |
    | `static `[`NetworkIO`](NetworkIO.md)                 | `getNetworkIO``(DbDataSource dataSource, java.lang.String networkName, java.lang.String globalNetworkName, `[`NetworkMetadata`](../NetworkMetadata.md)` metadata)`                                                                                                                                                                                                                                                                                          |
    | `static `[`NetworkIO`](NetworkIO.md)                 | `getNetworkIOForInMemoryNetwork``(`[`LogicalBasicNetwork`](LogicalBasicNetwork.md)`[] networks)`<br>Return the NetworkIO object for the in-memory network.                                                                                                                                                                                                                                                                                                  |
    | `static `[`NetworkMetadata`](../NetworkMetadata.md)  | `getNetworkMetadata``(java.sql.Connection conn, java.lang.String networkName, java.lang.String globalNetworkName)`<br>Returns the network metadata for the specified network.                                                                                                                                                                                                                                                                               |
    | `static `[`NetworkMetadata`](../NetworkMetadata.md)  | `getNetworkMetadata``(DbDataSource dataSource, java.lang.String networkName, java.lang.String globalNetworkName)`                                                                                                                                                                                                                                                                                                                                           |
    | `static javax.sql.DataSource`                        | `getOracleDataSource``(java.lang.String url, java.lang.String user, java.lang.String password)`<br>Returns a new OracleDataSource instance.                                                                                                                                                                                                                                                                                                                 |
    | `static java.lang.Object`                            | `readJavaObject``(java.sql.Connection conn, java.lang.String name)`<br>Reads in the given Java object from the database to memory Explicit casting is required before use                                                                                                                                                                                                                                                                                   |
    | `static `[`NetworkMetadata`](../NetworkMetadata.md)  | `readMetadata``(java.sql.Connection conn, java.lang.String networkName)`                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static java.lang.Object`                            | `readNetworkConstraint``(java.sql.Connection conn, java.lang.String networkConstraintName)`<br>Reads in the given network constraint from the database to memory                                                                                                                                                                                                                                                                                            |
    | `static void`                                        | `setNetworkDataSource``(java.lang.String networkName, javax.sql.DataSource dataSource)`                                                                                                                                                                                                                                                                                                                                                                     |
    | `static void`                                        | `setNetworkMetadata``(java.lang.String globalNetworkName, `[`NetworkMetadata`](../NetworkMetadata.md)` metadata)`                                                                                                                                                                                                                                                                                                                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getOracleDataSource

          public static javax.sql.DataSource getOracleDataSource(java.lang.String url,
                                                                 java.lang.String user,
                                                                 java.lang.String password)
                                                          throws java.sql.SQLException

      Returns a new OracleDataSource instance.
      Parameters:
      `url` - database url

      `user` - database user

      `password` - database password

      Returns:
      a new DataSource instance

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setNetworkDataSource

          public static void setNetworkDataSource(java.lang.String networkName,
                                                  javax.sql.DataSource dataSource)

    <!-- -->

    - #### getNetworkDataSource

          public static javax.sql.DataSource getNetworkDataSource(java.lang.String networkName)

    <!-- -->

    - #### getConnection

          public static OracleConnection getConnection(java.lang.String connectURL,
                                                       java.lang.String user,
                                                       java.lang.String password)
                                                throws java.sql.SQLException

      Returns a new OracleConnection instance.
      Parameters:
      `connectURL` - database url

      `user` - database user

      `password` - database password

      Returns:
      a new OracleConnection instance

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getNetworkAnalyst

          public static NetworkAnalyst getNetworkAnalyst(NetworkIO reader)
                                                  throws LODNetworkException

      Returns a new NetworkAnalyst instance, which uses the input network IO adaptor to retrieve information about the network.
      Parameters:
      `reader` - the cached network IO adaptor

      Returns:
      a new NetworkAnalyst instance

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getNetworkMetadata

          public static NetworkMetadata getNetworkMetadata(java.sql.Connection conn,
                                                           java.lang.String networkName,
                                                           java.lang.String globalNetworkName)
                                                    throws LODNetworkException

      Returns the network metadata for the specified network. If network metadata exists in the cache for the `globalNetworkName`, then the cached network metadata is returned; otherwise, a new network metadata instance is returned. If the `globalNetworkName` is not null, the returned network metadata instance is cached using `globalNetworkName` as the cache key.
      Parameters:
      `conn` - database connection for the network

      `networkName` - network name

      `globalNetworkName` - global network name that is used as the cache key for the network metadata. globalNetworkName should be unique across different connections as well as different subnetworks with the same master network.

      Returns:
      network metadata

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setNetworkMetadata

          public static void setNetworkMetadata(java.lang.String globalNetworkName,
                                                NetworkMetadata metadata)

    <!-- -->

    - #### getNetworkMetadata

          public static NetworkMetadata getNetworkMetadata(DbDataSource dataSource,
                                                           java.lang.String networkName,
                                                           java.lang.String globalNetworkName)
                                                    throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readMetadata

          public static NetworkMetadata readMetadata(java.sql.Connection conn,
                                                     java.lang.String networkName)
                                              throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getNetworkIOForInMemoryNetwork

          public static NetworkIO getNetworkIOForInMemoryNetwork(LogicalBasicNetwork[] networks)

      Return the NetworkIO object for the in-memory network.
      Parameters:
      `networks` - network objects on different link levels for the same network of interest. network\[i\] is the network on link level i+1. For example, network\[0\] is the network on link level 1; network\[1\] is the network on link level 2, and so on. If the network of interest is a flat network, the length of the networks array is 1, and network\[0\] should be the flat network.

    <!-- -->

    - #### getNetworkIO

          public static NetworkIO getNetworkIO(DbDataSource dataSource,
                                               java.lang.String networkName,
                                               java.lang.String globalNetworkName,
                                               NetworkMetadata metadata)
                                        throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getNetworkIO

          public static NetworkIO getNetworkIO(java.sql.Connection conn,
                                               java.lang.String networkName,
                                               java.lang.String globalNetworkName,
                                               NetworkMetadata metadata,
                                               boolean readFromBlob,
                                               LODUserDataIO[] udios,
                                               PartitionBlobTranslator translator)
                                        throws LODNetworkException

      Deprecated. use getNetworkIO(Connection conn, String networkName, String globalNetworkName, NetworkMetadata metadata);
      Returns the network I/O object for the specified network.
      Parameters:
      `conn` - database connection for the network

      `networkName` - network name

      `globalNetworkName` - global network name. `globalNetworkName` should be unique across different connections as well as different subnetworks with the same master network.

      `metadata` - network metadata. If not null, the input metadata will be used for the returning network I/O object; Otherwise, the network metadata will be retrieved from the database and assigned to the returning network I/O object.

      `readFromBlob` - true if partitions are loaded from BLOB table; false if partitions are loaded from node/link tables.

      `udios` - user data I/O implementation

      `translator` - partition BLOB translator

      Returns:
      network I/O

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getCachedNetworkIO

          public static CachedNetworkIO getCachedNetworkIO(DbDataSource dataSource,
                                                           java.lang.String networkName,
                                                           java.lang.String globalNetworkName,
                                                           NetworkMetadata metadata)
                                                    throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getCachedNetworkIO

          public static CachedNetworkIO getCachedNetworkIO(java.sql.Connection conn,
                                                           java.lang.String networkName,
                                                           java.lang.String globalNetworkName,
                                                           NetworkMetadata metadata,
                                                           LODUserDataIO[] udios)
                                                    throws LODNetworkException

      Deprecated. user getCachedNetworkIO(Connection conn, String networkName, String globalNetworkName, NetworkMetadata metadata);
      Returns the cached network IO object for the specified network.
      Parameters:
      `conn` -

      `networkName` -

      `globalNetworkName` -

      `metadata` -

      `udios` -

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getCachedNetworkIO

          public static CachedNetworkIO getCachedNetworkIO(java.sql.Connection conn,
                                                           java.lang.String networkName,
                                                           java.lang.String globalNetworkName,
                                                           NetworkMetadata metadata,
                                                           boolean readFromBlob,
                                                           LODUserDataIO[] udios,
                                                           PartitionBlobTranslator translator)
                                                    throws LODNetworkException

      Deprecated. user getCachedNetworkIO(Connection conn, String networkName, String globalNetworkName, NetworkMetadata metadata);
      Returns the cached network IO object for the specified network.
      Parameters:
      `conn` -

      `networkName` -

      `globalNetworkName` -

      `metadata` -

      `readFromBlob` -

      `udios` -

      `translator` -

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getCachedNetworkIOWM

          public static CachedNetworkIOWM getCachedNetworkIOWM(DbDataSource dataSource,
                                                               java.lang.String networkName,
                                                               java.lang.String globalNetworkName,
                                                               NetworkMetadata metadata)
                                                        throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getCachedNetworkIOWM

          public static CachedNetworkIOWM getCachedNetworkIOWM(java.sql.Connection conn,
                                                               java.lang.String networkName,
                                                               java.lang.String globalNetworkName,
                                                               NetworkMetadata metadata,
                                                               boolean readFromBlob,
                                                               LODUserDataIO[] udios,
                                                               PartitionBlobTranslator translator)
                                                        throws LODNetworkException

      Deprecated. use getCachedNetworkIOWM(Connection conn, String networkName, String globalNetworkName, NetworkMetadata metadata)
      Returns the cached network I/O object for the specified network. If network reader exists in the cache for the `globalNetworkName`, then the cached network reader is returned; otherwise, a new network reader instance is returned. If the `globalNetworkName` is not null, the returned network reader instance is cached using `globalNetworkName` as the cache key.
      Parameters:
      `conn` - database connection for the network

      `networkName` - network name

      `globalNetworkName` - global network name that is used as the cache key for the network reader. `globalNetworkName` should be unique across different connections as well as different subnetworks with the same master network.

      `metadata` - network metadata. If not null, the input metadata will be used for the returning network I/O object; Otherwise, the network metadata will be retrieved from the database and assigned to the returning network I/O object.

      Returns:
      cached network I/O

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getConfigManager

          public static ConfigManager getConfigManager()

      Returns the LOD configuration manager singleton. This method is equivalent to ConfigManager.getConfigManager.
      Returns:
      the LOD configuration manager singleton

    <!-- -->

    - #### readNetworkConstraint

          public static java.lang.Object readNetworkConstraint(java.sql.Connection conn,
                                                               java.lang.String networkConstraintName)
                                                        throws java.sql.SQLException,
                                                               NetworkDataException,
                                                               java.lang.ClassNotFoundException,
                                                               java.lang.InstantiationException,
                                                               java.lang.IllegalAccessException

      Reads in the given network constraint from the database to memory
      Parameters:
      `conn` - database connection

      `networkConstraintName` - the name of the network constraint

      Returns:
      the desired network constraint

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](../NetworkDataException.md)

      `java.lang.ClassNotFoundException`

      `java.lang.InstantiationException`

      `java.lang.IllegalAccessException`

    <!-- -->

    - #### readJavaObject

          public static java.lang.Object readJavaObject(java.sql.Connection conn,
                                                        java.lang.String name)
                                                 throws java.sql.SQLException,
                                                        NetworkDataException,
                                                        java.lang.ClassNotFoundException,
                                                        java.lang.InstantiationException,
                                                        java.lang.IllegalAccessException

      Reads in the given Java object from the database to memory Explicit casting is required before use
      Parameters:
      `conn` - database connection

      `name` - the name of the object

      Returns:
      the desired Java object

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](../NetworkDataException.md)

      `java.lang.ClassNotFoundException`

      `java.lang.InstantiationException`

      `java.lang.IllegalAccessException`

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

- [Prev Class](LODNetworkFactory.md)
- [Next Class](LODNetworkWrapper.md)

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
