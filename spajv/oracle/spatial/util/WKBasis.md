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

- [Prev Class](WKB.md)
- [Next Class](WKInputStream.md)

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

## Class WKBasis

- java.lang.Object

- - oracle.spatial.util.WKBasis

<!-- -->

- All Implemented Interfaces:
  [WKAdapter](WKAdapter.md)

  <!-- -->

  Direct Known Subclasses:
  [WKB](WKB.md), [WKT](WKT.md)

  ------------------------------------------------------------------------



      public abstract class WKBasis
      extends java.lang.Object
      implements WKAdapter

  This class provides some implementations common to WKB and WKT, particularly the translation between WKB/WKT and STRUCT. This translation is based on the translation between WKB/WKT and JGeometry (which is specific to the WKB and WKT subclasses of this class).

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                  |
    |--------------------------------------------------------------|
    | `WKBasis``()`                                                |
    | `WKBasis``(`[`ByteOrder`](ByteOrder.md)` defaultByteOrder)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                                            |
    |-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
    | `byte[]`                                | `fromJGeometry``(`[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>This transforms a JGeometry to a WKB/WKT geometry.           |
    | `byte[]`                                | `fromStruct``(java.sql.Struct geom)`<br>Creates a WKB/WKT geometry from a Struct object.                                          |
    | `byte[]`                                | `fromSTRUCT``(STRUCT geom)`<br>Creates a WKB/WKT geometry from a STRUCT object.                                                   |
    | [`JGeometry`](../geometry/JGeometry.md) | `toJGeometry``(byte[] wkb)`<br>This transforms a WKB/WKT geometry to a JGeometry.                                                 |
    | `java.sql.Struct`                       | `toStruct``(byte[] wkContent, java.sql.Connection conn)`<br>Convert the given WKB/WKT geometry into an Oracle JDBC Struct object. |
    | `STRUCT`                                | `toSTRUCT``(byte[] wkContent, java.sql.Connection conn)`<br>Convert the given WKB/WKT geometry into an Oracle JDBC STRUCT object. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### WKBasis

          public WKBasis(ByteOrder defaultByteOrder)

    <!-- -->

    - #### WKBasis

          public WKBasis()

  <!-- -->

  - ### Method Detail

    - #### fromJGeometry

          public byte[] fromJGeometry(JGeometry geom)
                               throws GeometryExceptionWithContext

      Description copied from interface: [`WKAdapter`](WKAdapter.md)
      This transforms a JGeometry to a WKB/WKT geometry.
      Specified by:
      [`fromJGeometry`](WKAdapter.md) in interface [`WKAdapter`](WKAdapter.md)

      Parameters:
      `geom` - a JGeometry representing the Oracle Spatial geometry

      Returns:
      a byte\[\] representing the WKB/WKT geometry

      Throws:
      [`GeometryExceptionWithContext`](GeometryExceptionWithContext.md)

    <!-- -->

    - #### toSTRUCT

          public final STRUCT toSTRUCT(byte[] wkContent,
                                       java.sql.Connection conn)
                                throws java.sql.SQLException,
                                       GeometryExceptionWithContext

      Convert the given WKB/WKT geometry into an Oracle JDBC STRUCT object. You can then bind the STRUCT object to a SQL DML statment. This function is final, for it calls the function toJGeometry, which is not final. Any code specific to WKB/WKT should be in toJGeometry.
      Specified by:
      [`toSTRUCT`](WKAdapter.md) in interface [`WKAdapter`](WKAdapter.md)

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

          public final byte[] fromSTRUCT(STRUCT geom)
                                  throws java.sql.SQLException,
                                         GeometryExceptionWithContext

      Creates a WKB/WKT geometry from a STRUCT object. This function is final, for it calls the function fromJGeometry, which is not final. Any code specific to WKB/WKT should be in fromJGeometry.
      Specified by:
      [`fromSTRUCT`](WKAdapter.md) in interface [`WKAdapter`](WKAdapter.md)

      Parameters:
      `geom` - the STRUCT object from an oracle result set

      Returns:
      a WKB/WKT geometry (byte array) if successful; otherwise null

      Throws:
      `java.sql.SQLException`

      [`GeometryExceptionWithContext`](GeometryExceptionWithContext.md)

    <!-- -->

    - #### toStruct

          public final java.sql.Struct toStruct(byte[] wkContent,
                                                java.sql.Connection conn)
                                         throws java.sql.SQLException,
                                                GeometryExceptionWithContext

      Convert the given WKB/WKT geometry into an Oracle JDBC Struct object. You can then bind the Struct object to a SQL DML statment. This function is final, for it calls the function toJGeometry, which is not final. Any code specific to WKB/WKT should be in toJGeometry.
      Parameters:
      `wkContent` - the WKB/WKT geometry (byte array) to be converted

      `conn` - the connection to be used

      Returns:
      an Oracle Struct object when successful; otherwise null

      Throws:
      `java.sql.SQLException`

      [`GeometryExceptionWithContext`](GeometryExceptionWithContext.md)

      Since:
      Oracle Database 12c Release 1 (12.1)

    <!-- -->

    - #### fromStruct

          public final byte[] fromStruct(java.sql.Struct geom)
                                  throws java.sql.SQLException,
                                         GeometryExceptionWithContext

      Creates a WKB/WKT geometry from a Struct object. This function is final, for it calls the function fromJGeometry, which is not final. Any code specific to WKB/WKT should be in fromJGeometry.
      Parameters:
      `geom` - the Struct object from an oracle result set

      Returns:
      a WKB/WKT geometry (byte array) if successful; otherwise null

      Throws:
      `java.sql.SQLException`

      [`GeometryExceptionWithContext`](GeometryExceptionWithContext.md)

      Since:
      Oracle Database 12c Release 1 (12.1)

    <!-- -->

    - #### toJGeometry

          public JGeometry toJGeometry(byte[] wkb)
                                throws GeometryExceptionWithContext

      Description copied from interface: [`WKAdapter`](WKAdapter.md)
      This transforms a WKB/WKT geometry to a JGeometry.
      Specified by:
      [`toJGeometry`](WKAdapter.md) in interface [`WKAdapter`](WKAdapter.md)

      Parameters:
      `wkb` - a byte\[\] representing the WKB/WKT geometry

      Returns:
      a JGeometry representing the Oracle Spatial geometry

      Throws:
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

- [Prev Class](WKB.md)
- [Next Class](WKInputStream.md)

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
