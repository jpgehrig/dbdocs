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

- [Prev Class](KML.md)
- [Next Class](Las2SqlLdr.md)

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

## Class KML2

- java.lang.Object

- - oracle.spatial.util.KML2

<!-- -->

-

  ------------------------------------------------------------------------



      public class KML2
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `KML2``()`                  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type         | Method and Description                                                                                                                                                                                   |
    |---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`             | `setConnection``(java.sql.Connection conn)`                                                                                                                                                              |
    | `static void`             | `setsrsAlias``(java.lang.String srsAlias)`                                                                                                                                                               |
    | `static void`             | `setsrsNameSpace``(java.lang.String srsNameSpace)`                                                                                                                                                       |
    | `static java.lang.String` | `to_KMLGeometry``(STRUCT geom)`<br>Deprecated.                                                                                                                                                           |
    | `static java.lang.String` | `to_KMLGeometry``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Deprecated.                                                                                                 |
    | `static CLOB`             | `to_KMLGeometryCLOB``(java.sql.Struct geom)`<br>Deprecated. <br>Use `to_KMLGeometryCLOBJS(java.sql.Struct)` instead.                                                                                     |
    | `static CLOB`             | `to_KMLGeometryCLOB``(STRUCT geom)`<br>Deprecated. <br>Use `to_KMLGeometryCLOBJS(java.sql.Struct)` instead.                                                                                              |
    | `static CLOB`             | `to_KMLGeometryCLOB``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Deprecated. <br>Use `to_KMLGeometryCLOBJS(java.sql.Struct, String, String)` instead.           |
    | `static CLOB`             | `to_KMLGeometryCLOB``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Deprecated. <br>Use `to_KMLGeometryCLOBJS(java.sql.Struct, String, String)` instead.                    |
    | `static OracleClob`       | `to_KMLGeometryCLOBJS``(java.sql.Struct geom)`<br>Returns KML OracleClob object for the java.sql.Struct Geometry Object.                                                                                 |
    | `static OracleClob`       | `to_KMLGeometryCLOBJS``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Returns KML OracleClob object for the java.sql.Struct Object with srsNameSpace and srsAlias. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### KML2

          public KML2()

  <!-- -->

  - ### Method Detail

    - #### setConnection

          public static void setConnection(java.sql.Connection conn)

    <!-- -->

    - #### setsrsNameSpace

          public static void setsrsNameSpace(java.lang.String srsNameSpace)

    <!-- -->

    - #### setsrsAlias

          public static void setsrsAlias(java.lang.String srsAlias)

    <!-- -->

    - #### to_KMLGeometryCLOB

          public static CLOB to_KMLGeometryCLOB(STRUCT geom,
                                                java.lang.String srsNameSpace,
                                                java.lang.String srsAlias)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                java.lang.Exception

      Deprecated. Use `to_KMLGeometryCLOBJS(java.sql.Struct, String, String)` instead.
      Returns KML CLOB object for the oracle.sql.STRUCT Object with srsNameSpace and srsAlias.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_KMLGeometryCLOB

          public static CLOB to_KMLGeometryCLOB(java.sql.Struct geom,
                                                java.lang.String srsNameSpace,
                                                java.lang.String srsAlias)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                java.lang.Exception

      Deprecated. Use `to_KMLGeometryCLOBJS(java.sql.Struct, String, String)` instead.
      Returns KML CLOB object for the java.sql.Struct Object with srsNameSpace and srsAlias.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_KMLGeometry

          public static java.lang.String to_KMLGeometry(STRUCT geom,
                                                        java.lang.String srsNameSpace,
                                                        java.lang.String srsAlias)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Deprecated. 
      Returns KML String object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_KMLGeometry

          public static java.lang.String to_KMLGeometry(STRUCT geom)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException

      Deprecated. 
      Returns KML String object for the oracle.sql.STRUCT Geometry Object.
      Parameters:
      `geom` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_KMLGeometryCLOB

          public static CLOB to_KMLGeometryCLOB(STRUCT geom)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                java.lang.Exception

      Deprecated. Use `to_KMLGeometryCLOBJS(java.sql.Struct)` instead.
      Returns KML CLOB object for the oracle.sql.STRUCT Geometry Object.
      Parameters:
      `geom` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_KMLGeometryCLOB

          public static CLOB to_KMLGeometryCLOB(java.sql.Struct geom)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                java.lang.Exception

      Deprecated. Use `to_KMLGeometryCLOBJS(java.sql.Struct)` instead.
      Returns KML CLOB object for the java.sql.Struct Geometry Object.
      Parameters:
      `geom` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_KMLGeometryCLOBJS

          public static OracleClob to_KMLGeometryCLOBJS(java.sql.Struct geom)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Returns KML OracleClob object for the java.sql.Struct Geometry Object.
      Parameters:
      `geom` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_KMLGeometryCLOBJS

          public static OracleClob to_KMLGeometryCLOBJS(java.sql.Struct geom,
                                                        java.lang.String srsNameSpace,
                                                        java.lang.String srsAlias)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Returns KML OracleClob object for the java.sql.Struct Object with srsNameSpace and srsAlias.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

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

- [Prev Class](KML.md)
- [Next Class](Las2SqlLdr.md)

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
