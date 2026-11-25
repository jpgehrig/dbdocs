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

- [Prev Class](Util.CheckType.md)
- [Next Class](WKB.md)

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

## Interface WKAdapter

- All Known Implementing Classes:
  [WKB](WKB.md), [WKBasis](WKBasis.md), [WKT](WKT.md)

  ------------------------------------------------------------------------



      public interface WKAdapter

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                            |
    |-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
    | `byte[]`                                | `fromJGeometry``(`[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>This transforms a JGeometry to a WKB/WKT geometry.           |
    | `byte[]`                                | `fromSTRUCT``(STRUCT geom)`<br>Creates a WKB/WKT geometry from a STRUCT object.                                                   |
    | [`JGeometry`](../geometry/JGeometry.md) | `toJGeometry``(byte[] wkContent)`<br>This transforms a WKB/WKT geometry to a JGeometry.                                           |
    | `STRUCT`                                | `toSTRUCT``(byte[] wkContent, java.sql.Connection conn)`<br>Convert the given WKB/WKT geometry into an Oracle JDBC STRUCT object. |

<!-- -->

- - ### Method Detail

    - #### toJGeometry

          JGeometry toJGeometry(byte[] wkContent)
                         throws GeometryExceptionWithContext

      This transforms a WKB/WKT geometry to a JGeometry.
      Parameters:
      `wkContent` - a byte\[\] representing the WKB/WKT geometry

      Returns:
      a JGeometry representing the Oracle Spatial geometry

      Throws:
      [`GeometryExceptionWithContext`](GeometryExceptionWithContext.md)

    <!-- -->

    - #### fromJGeometry

          byte[] fromJGeometry(JGeometry geom)
                        throws GeometryExceptionWithContext

      This transforms a JGeometry to a WKB/WKT geometry.
      Parameters:
      `geom` - a JGeometry representing the Oracle Spatial geometry

      Returns:
      a byte\[\] representing the WKB/WKT geometry

      Throws:
      [`GeometryExceptionWithContext`](GeometryExceptionWithContext.md)

    <!-- -->

    - #### toSTRUCT

          STRUCT toSTRUCT(byte[] wkContent,
                          java.sql.Connection conn)
                   throws java.sql.SQLException,
                          GeometryExceptionWithContext

      Convert the given WKB/WKT geometry into an Oracle JDBC STRUCT object. You can then bind the STRUCT object to a SQL DML statment.
      Parameters:
      `wkContent` - the WKB/WKT geometry (byte array) to be converted

      `conn` - the connection to be used

      Returns:
      an Oracle STRUCT object when successful; otherwise null

      Throws:
      `java.sql.SQLException`

      [`GeometryExceptionWithContext`](GeometryExceptionWithContext.md)

    <!-- -->

    - #### fromSTRUCT

          byte[] fromSTRUCT(STRUCT geom)
                     throws java.sql.SQLException,
                            GeometryExceptionWithContext

      Creates a WKB/WKT geometry from a STRUCT object.
      Parameters:
      `geom` - the STRUCT object from an oracle result set

      Returns:
      a WKB/WKT geometry (byte array) if successful; otherwise null

      Throws:
      `java.sql.SQLException`

      [`GeometryExceptionWithContext`](GeometryExceptionWithContext.md)

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

- [Prev Class](Util.CheckType.md)
- [Next Class](WKB.md)

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
