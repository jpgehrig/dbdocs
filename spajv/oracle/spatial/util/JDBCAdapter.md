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

- [Prev Class](Hilbert.md)
- [Next Class](JDBCExtensionInterface.md)

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

oracle.spatial.util

## Class JDBCAdapter

- java.lang.Object

- - oracle.spatial.util.JDBCAdapter

<!-- -->

-

  ------------------------------------------------------------------------



      public class JDBCAdapter
      extends java.lang.Object

  This Class helps to encapsulate calls to Oracle JDBC Extensions that does not work with some J2EE connection pools implementations. If initialize is not call, casting to oracle.sql.STRUCT and oracle.sql.ARRAY will be used.

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                | Method and Description                                                                                                                                      |
    |--------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`                                    | `clearStatementCache``(java.sql.Connection conn)`                                                                                                           |
    | `static void`                                    | `closeOracleConnection``(OracleConnection conn)`                                                                                                            |
    | `static ArrayDescriptor`                         | `getArrayDescriptor``(java.lang.Object obj)`<br>Deprecated. <br>Use OracleConnection.createOracleArray(...);                                                |
    | `static javax.sql.DataSource[]`                  | `getDataSource``(java.lang.String... dataSourceName)`                                                                                                       |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `getJGeometry``(java.lang.Object obj)`                                                                                                                      |
    | `static Datum[]`                                 | `getOracleArray``(java.lang.Object obj)`<br>Deprecated. <br>Use java.sql.Array array = resultSet.getArray(...);                                             |
    | `static Datum[]`                                 | `getOracleAttributes``(java.lang.Object obj)`<br>Deprecated. <br>Use java.sql.Struct.getAttributes();                                                       |
    | `static OracleConnection`                        | `getOracleConnection``(java.sql.Connection conn)`                                                                                                           |
    | `static StructDescriptor`                        | `getStructDescriptor``(java.lang.Object obj)`                                                                                                               |
    | `static XMLType`                                 | `getXMLType``(java.lang.Object obj)`<br>Deprecated. <br>Use SQLXML newXML = resultSet.getSQLXML(columnNumber);                                              |
    | `static void`                                    | `initialize``(`[`JDBCExtensionInterface`](JDBCExtensionInterface.md)` oracleExtension)`<br>This method should be called before any interaction with the db. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### initialize

          public static void initialize(JDBCExtensionInterface oracleExtension)

      This method should be called before any interaction with the db. JDBCExtensionInterface provides the implementation details to deal with Connection Wrappers.
      Parameters:
      `oracleExtension` -

    <!-- -->

    - #### getOracleConnection

          public static OracleConnection getOracleConnection(java.sql.Connection conn)
                                                      throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### clearStatementCache

          public static void clearStatementCache(java.sql.Connection conn)
                                          throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getJGeometry

          public static JGeometry getJGeometry(java.lang.Object obj)
                                        throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getOracleAttributes

          public static Datum[] getOracleAttributes(java.lang.Object obj)
                                             throws java.sql.SQLException

      Deprecated. Use java.sql.Struct.getAttributes();
      Parameters:
      `obj` -

      Returns:
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getStructDescriptor

          public static StructDescriptor getStructDescriptor(java.lang.Object obj)
                                                      throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getOracleArray

          public static Datum[] getOracleArray(java.lang.Object obj)
                                        throws java.sql.SQLException

      Deprecated. Use java.sql.Array array = resultSet.getArray(...);
      Parameters:
      `obj` -

      Returns:
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getArrayDescriptor

          public static ArrayDescriptor getArrayDescriptor(java.lang.Object obj)
                                                    throws java.sql.SQLException

      Deprecated. Use OracleConnection.createOracleArray(...);
      Parameters:
      `obj` -

      Returns:
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### closeOracleConnection

          public static void closeOracleConnection(OracleConnection conn)
                                            throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getDataSource

          public static javax.sql.DataSource[] getDataSource(java.lang.String... dataSourceName)

    <!-- -->

    - #### getXMLType

          public static XMLType getXMLType(java.lang.Object obj)
                                    throws java.sql.SQLException

      Deprecated. Use SQLXML newXML = resultSet.getSQLXML(columnNumber);
      Parameters:
      `obj` -

      Returns:
      Throws:
      `java.sql.SQLException`

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

- [Prev Class](Hilbert.md)
- [Next Class](JDBCExtensionInterface.md)

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
