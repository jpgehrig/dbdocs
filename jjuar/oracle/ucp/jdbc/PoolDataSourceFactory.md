Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/PoolDataSourceFactory.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](PoolDataSource.md)
- [Next Class](PoolDataSourceImpl.md)

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

oracle.ucp.jdbc

## Class PoolDataSourceFactory

- java.lang.Object

- - oracle.ucp.jdbc.PoolDataSourceFactory

<!-- -->

-

  ------------------------------------------------------------------------



      public class PoolDataSourceFactory
      extends java.lang.Object

  Data source factory for creating instances of the pool-enabled `PoolDataSource` or `PoolXADataSource` that provide access to Universal Connection Pool functionalities.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description  |
    |------------------------------|
    | `PoolDataSourceFactory``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                  | Method and Description                                                                                                                |
    |----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`PoolDataSource`](PoolDataSource.md)     | `getPoolDataSource``()`<br>Obtains a pool-enabled `PoolDataSource` instance.                                                          |
    | `static `[`PoolDataSource`](PoolDataSource.md)     | `getPoolDataSource``(java.util.Properties configuration)`<br>Creates and configures a new data source to a shared pool instance.      |
    | `static `[`PoolDataSource`](PoolDataSource.md)     | `getPoolDataSource``(java.lang.String dataSourceName)`<br>Obtains a pool-enabled `PoolDataSource` instance.                           |
    | `static `[`PoolXADataSource`](PoolXADataSource.md) | `getPoolXADataSource``()`<br>Obtains a pool-enabled `PoolXADataSource` instance.                                                      |
    | `static `[`PoolXADataSource`](PoolXADataSource.md) | `getPoolXADataSource``(java.util.Properties configuration)`<br>Creates and configures a new XA data source to a shared pool instance. |
    | `static `[`PoolXADataSource`](PoolXADataSource.md) | `getPoolXADataSource``(java.lang.String dataSourceName)`<br>Obtains a pool-enabled `PoolXADataSource` instance.                       |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### PoolDataSourceFactory

          public PoolDataSourceFactory()

  <!-- -->

  - ### Method Detail

    - #### getPoolDataSource

          public static PoolDataSource getPoolDataSource()

      Obtains a pool-enabled `PoolDataSource` instance.
      Returns:
      A `PoolDataSource` instance.

    <!-- -->

    - #### getPoolDataSource

          public static PoolDataSource getPoolDataSource(java.lang.String dataSourceName)
                                                  throws java.sql.SQLException

      Obtains a pool-enabled `PoolDataSource` instance. The location of the XML configuration file is specified using the Java system property "oracle.ucp.jdbc.xmlConfigFile".
      Parameters:
      `dataSourceName` - name of the data source present in configuration file.

      Returns:
      A `PoolDataSource` instance.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getPoolDataSource

          public static PoolDataSource getPoolDataSource(java.util.Properties configuration)
                                                  throws java.sql.SQLException

      Creates and configures a new data source to a shared pool instance. The following properties are supported in the "configuration" parameter: `connectionPoolName`, `dataSourceName`, `user`, `password`, `description`, `serviceName`, `pdbRoles`.
      Parameters:
      `configuration` - the configuration input as Properties

      Returns:
      A `PoolDataSource` instance.

      Throws:
      `java.sql.SQLException` - If an error occurs while configuring new data source.

    <!-- -->

    - #### getPoolXADataSource

          public static PoolXADataSource getPoolXADataSource()

      Obtains a pool-enabled `PoolXADataSource` instance.
      Returns:
      A `PoolXADataSource` instance.

    <!-- -->

    - #### getPoolXADataSource

          public static PoolXADataSource getPoolXADataSource(java.lang.String dataSourceName)
                                                      throws java.sql.SQLException

      Obtains a pool-enabled `PoolXADataSource` instance. The location of the XML configuration file is specified using the Java system property "oracle.ucp.jdbc.xmlConfigFile".
      Parameters:
      `dataSourceName` - name of the data source present in configuration file.

      Returns:
      A `PoolXADataSource` instance.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getPoolXADataSource

          public static PoolXADataSource getPoolXADataSource(java.util.Properties configuration)
                                                      throws java.sql.SQLException

      Creates and configures a new XA data source to a shared pool instance. The following properties are supported in the "configuration" parameter: `connectionPoolName`, `dataSourceName`, `user`, `password`, `description`, `serviceName`, `pdbRoles`.
      Parameters:
      `configuration` - the configuration input as Properties

      Returns:
      A `PoolXADataSource` instance.

      Throws:
      `java.sql.SQLException` - If an error occurs while configuring new XA data source.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/PoolDataSourceFactory.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](PoolDataSource.md)
- [Next Class](PoolDataSourceImpl.md)

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

Copyright © 2007, 2022, Oracle and/or its affiliates.
