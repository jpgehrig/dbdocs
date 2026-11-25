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

- [Prev Class](JDBCAdapter.md)
- [Next Class](JDBCUtil.md)

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

## Interface JDBCExtensionInterface

-

  ------------------------------------------------------------------------



      public interface JDBCExtensionInterface

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                       | Method and Description                                                                                          |
    |-----------------------------------------|-----------------------------------------------------------------------------------------------------------------|
    | `void`                                  | `clearStatementCache``(java.sql.Connection conn)`                                                               |
    | `void`                                  | `closeOracleConnection``(OracleConnection conn)`                                                                |
    | `ArrayDescriptor`                       | `getArrayDescriptor``(java.lang.Object obj)`<br>Deprecated. <br>Use OracleConnection.createOracleArray(...);    |
    | `javax.sql.DataSource[]`                | `getDataSource``(java.lang.String... name)`                                                                     |
    | [`JGeometry`](../geometry/JGeometry.md) | `getJGeometry``(java.lang.Object obj)`                                                                          |
    | `Datum[]`                               | `getOracleArray``(java.lang.Object obj)`<br>Deprecated. <br>Use java.sql.Array array = resultSet.getArray(...); |
    | `Datum[]`                               | `getOracleAttributes``(java.lang.Object obj)`<br>Deprecated. <br>Use java.sql.Struct.getAttributes();           |
    | `OracleConnection`                      | `getOracleConnection``(java.sql.Connection conn)`                                                               |
    | `StructDescriptor`                      | `getStructDescriptor``(java.lang.Object obj)`                                                                   |
    | `XMLType`                               | `getXMLType``(java.lang.Object obj)`<br>Deprecated. <br>Use SQLXML newXML = resultSet.getSQLXML(columnNumber);  |

<!-- -->

- - ### Method Detail

    - #### getOracleConnection

          OracleConnection getOracleConnection(java.sql.Connection conn)
                                        throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### clearStatementCache

          void clearStatementCache(java.sql.Connection conn)
                            throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getJGeometry

          JGeometry getJGeometry(java.lang.Object obj)
                          throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getOracleAttributes

          Datum[] getOracleAttributes(java.lang.Object obj)
                               throws java.sql.SQLException

      Deprecated. Use java.sql.Struct.getAttributes();
      Parameters:
      `obj` -

      Returns:
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getStructDescriptor

          StructDescriptor getStructDescriptor(java.lang.Object obj)
                                        throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getOracleArray

          Datum[] getOracleArray(java.lang.Object obj)
                          throws java.sql.SQLException

      Deprecated. Use java.sql.Array array = resultSet.getArray(...);
      Parameters:
      `obj` -

      Returns:
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getArrayDescriptor

          ArrayDescriptor getArrayDescriptor(java.lang.Object obj)
                                      throws java.sql.SQLException

      Deprecated. Use OracleConnection.createOracleArray(...);
      Parameters:
      `obj` -

      Returns:
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### closeOracleConnection

          void closeOracleConnection(OracleConnection conn)
                              throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getDataSource

          javax.sql.DataSource[] getDataSource(java.lang.String... name)

    <!-- -->

    - #### getXMLType

          XMLType getXMLType(java.lang.Object obj)
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

- [Prev Class](JDBCAdapter.md)
- [Next Class](JDBCUtil.md)

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
