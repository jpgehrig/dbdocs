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

- [Prev Class](GML.md)
- [Next Class](GML3.md)

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

## Class GML2

- java.lang.Object

- - oracle.spatial.util.GML2

<!-- -->

-

  ------------------------------------------------------------------------



      public class GML2
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `GML2``()`                  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type         | Method and Description                                                                                                                                                                                                                                                                                                      |
    |---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                 | `geometryHasArcs``(`[`JGeometry`](../geometry/JGeometry.md)` theGeom)`                                                                                                                                                                                                                                                      |
    | `static void`             | `setConnection``(java.sql.Connection conn)`                                                                                                                                                                                                                                                                                 |
    | `static void`             | `setsrsAlias``(java.lang.String srsAlias)`                                                                                                                                                                                                                                                                                  |
    | `static void`             | `setsrsNameSpace``(java.lang.String srsNameSpace)`                                                                                                                                                                                                                                                                          |
    | `static java.lang.String` | `to_GMLGeometry``(java.sql.Struct geom)`<br>Returns GML2 String object for the java.sql.Struct Geometry Object.                                                                                                                                                                                                             |
    | `static java.lang.String` | `to_GMLGeometry``(STRUCT geom)`<br>Deprecated. <br>Use `to_GMLGeometry(java.sql.Struct)` instead.                                                                                                                                                                                                                           |
    | `static java.lang.String` | `to_GMLGeometry``(java.sql.Struct geom, int coordOrder)`<br>Returns GML2 String object for the java.sql.Struct Geometry Object.                                                                                                                                                                                             |
    | `static java.lang.String` | `to_GMLGeometry``(STRUCT geom, int coordOrder)`<br>Deprecated. <br>Use `to_GMLGeometry(java.sql.Struct, int)` instead.                                                                                                                                                                                                      |
    | `static java.lang.String` | `to_GMLGeometry``(java.sql.Struct geom, java.lang.String is_srsname_in_urn_form)`<br>Returns GML2 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.                                                                                                                                    |
    | `static java.lang.String` | `to_GMLGeometry``(STRUCT geom, java.lang.String is_srsname_in_urn_form)`<br>Deprecated. <br>Use `to_GMLGeometry(java.sql.Struct, String)` instead.                                                                                                                                                                          |
    | `static java.lang.String` | `to_GMLGeometry``(java.sql.Struct geom, java.lang.String is_srsname_in_urn_form, int coordOrder)`<br>Returns GML2 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.                                                                                                                    |
    | `static java.lang.String` | `to_GMLGeometry``(STRUCT geom, java.lang.String is_srsname_in_urn_form, int coordOrder)`<br>Deprecated. <br>Use `to_GMLGeometry(java.sql.Struct, String, int)` instead.                                                                                                                                                     |
    | `static java.lang.String` | `to_GMLGeometry``(java.sql.Struct geom, java.lang.String is_srsname_in_urn_form, int coordOrder, java.sql.Connection conn)`<br>Returns GML2 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.                                                                                          |
    | `static java.lang.String` | `to_GMLGeometry``(STRUCT geom, java.lang.String is_srsname_in_urn_form, int coordOrder, java.sql.Connection conn)`<br>Deprecated. <br>Use `to_GMLGeometry(java.sql.Struct, String, int, Connection)` instead.                                                                                                               |
    | `static java.lang.String` | `to_GMLGeometry``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Returns GML2 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.                                                                                                                    |
    | `static java.lang.String` | `to_GMLGeometry``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Deprecated. <br>Use `to_GMLGeometry(java.sql.Struct, String, String)` instead.                                                                                                                                                 |
    | `static java.lang.String` | `to_GMLGeometry``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form)`<br>Returns GML2 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.                                           |
    | `static java.lang.String` | `to_GMLGeometry``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form)`<br>Deprecated. <br>Use `to_GMLGeometry(java.sql.Struct, String, String, String)` instead.                                                                                                |
    | `static java.lang.String` | `to_GMLGeometry``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form, int coordOrder)`<br>Returns GML2 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.                           |
    | `static java.lang.String` | `to_GMLGeometry``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form, int coordOrder)`<br>Deprecated. <br>Use `to_GMLGeometry(java.sql.Struct, String, String, String, int)` instead.                                                                           |
    | `static java.lang.String` | `to_GMLGeometry``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form, int coordOrder, java.sql.Connection conn)`<br>Returns GML2 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form. |
    | `static java.lang.String` | `to_GMLGeometry``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form, int coordOrder, java.sql.Connection conn)`<br>Deprecated. <br>Use `to_GMLGeometry(java.sql.Struct, String, String, String, int, Connection)` instead.                                     |
    | `static CLOB`             | `to_GMLGeometryCLOB``(java.sql.Struct geom)`<br>Deprecated. <br>Use `to_GMLGeometryCLOBJS(java.sql.Struct)` instead.                                                                                                                                                                                                        |
    | `static CLOB`             | `to_GMLGeometryCLOB``(STRUCT geom)`<br>Deprecated. <br>Use `to_GMLGeometryCLOBJS(java.sql.Struct)` instead.                                                                                                                                                                                                                 |
    | `static CLOB`             | `to_GMLGeometryCLOB``(java.sql.Struct geom, NUMBER coordOrder)`<br>Deprecated. <br>Use `to_GMLGeometryCLOBJS(java.sql.Struct, NUMBER)` instead.                                                                                                                                                                             |
    | `static CLOB`             | `to_GMLGeometryCLOB``(STRUCT geom, NUMBER coordOrder)`<br>Deprecated. <br>Use `to_GMLGeometryCLOBJS(java.sql.Struct, NUMBER)` instead.                                                                                                                                                                                      |
    | `static CLOB`             | `to_GMLGeometryCLOB``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Deprecated. <br>Use `to_GMLGeometryCLOBJS(java.sql.Struct, String, String)` instead.                                                                                                                              |
    | `static CLOB`             | `to_GMLGeometryCLOB``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Deprecated. <br>Use `to_GMLGeometryCLOBJS(java.sql.Struct, String, String)` instead.                                                                                                                                       |
    | `static CLOB`             | `to_GMLGeometryCLOB``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, NUMBER coordOrder)`<br>Deprecated. <br>Use `to_GMLGeometryCLOBJS(java.sql.Struct, String, String, NUMBER)` instead.                                                                                                   |
    | `static CLOB`             | `to_GMLGeometryCLOB``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias, NUMBER coordOrder)`<br>Deprecated. <br>Use `to_GMLGeometryCLOBJS(java.sql.Struct, String, String, NUMBER)` instead.                                                                                                            |
    | `static OracleClob`       | `to_GMLGeometryCLOBJS``(java.sql.Struct geom)`<br>Returns GML2 OracleClob object for the java.sql.Struct Geometry Object.                                                                                                                                                                                                   |
    | `static OracleClob`       | `to_GMLGeometryCLOBJS``(java.sql.Struct geom, NUMBER coordOrder)`<br>Returns GML2 OracleClob object for the java.sql.Struct Geometry Object.                                                                                                                                                                                |
    | `static OracleClob`       | `to_GMLGeometryCLOBJS``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Returns GML2 OracleClob object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.                                                                                                          |
    | `static OracleClob`       | `to_GMLGeometryCLOBJS``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, NUMBER coordOrder)`<br>Returns GML2 OracleClob object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.                                                                                       |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GML2

          public GML2()

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

    - #### geometryHasArcs

          public boolean geometryHasArcs(JGeometry theGeom)

    <!-- -->

    - #### to_GMLGeometryCLOB

          public static CLOB to_GMLGeometryCLOB(STRUCT geom,
                                                java.lang.String srsNameSpace,
                                                java.lang.String srsAlias)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                java.lang.Exception

      Deprecated. Use `to_GMLGeometryCLOBJS(java.sql.Struct, String, String)` instead.
      Returns GML2 CLOB object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GMLGeometryCLOB

          public static CLOB to_GMLGeometryCLOB(java.sql.Struct geom,
                                                java.lang.String srsNameSpace,
                                                java.lang.String srsAlias)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                java.lang.Exception

      Deprecated. Use `to_GMLGeometryCLOBJS(java.sql.Struct, String, String)` instead.
      Returns GML2 CLOB object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(java.sql.Struct geom,
                                                        java.lang.String srsNameSpace,
                                                        java.lang.String srsAlias)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Returns GML2 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(STRUCT geom,
                                                        java.lang.String srsNameSpace,
                                                        java.lang.String srsAlias)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Deprecated. Use `to_GMLGeometry(java.sql.Struct, String, String)` instead.
      Returns GML2 String object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(java.sql.Struct geom,
                                                        java.lang.String srsNameSpace,
                                                        java.lang.String srsAlias,
                                                        java.lang.String is_srsname_in_urn_form)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Returns GML2 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      `is_srsname_in_urn_form` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(STRUCT geom,
                                                        java.lang.String srsNameSpace,
                                                        java.lang.String srsAlias,
                                                        java.lang.String is_srsname_in_urn_form)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Deprecated. Use `to_GMLGeometry(java.sql.Struct, String, String, String)` instead.
      Returns GML2 String object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      `is_srsname_in_urn_form` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(java.sql.Struct geom)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException

      Returns GML2 String object for the java.sql.Struct Geometry Object. is_srsname_in_urn_form is NULL.
      Parameters:
      `geom` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(STRUCT geom)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException

      Deprecated. Use `to_GMLGeometry(java.sql.Struct)` instead.
      Returns GML2 String object for the oracle.sql.STRUCT Geometry Object. is_srsname_in_urn_form is NULL.
      Parameters:
      `geom` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(java.sql.Struct geom,
                                                        java.lang.String is_srsname_in_urn_form)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException

      Returns GML2 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(STRUCT geom,
                                                        java.lang.String is_srsname_in_urn_form)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException

      Deprecated. Use `to_GMLGeometry(java.sql.Struct, String)` instead.
      Returns GML2 String object for the oracle.sql.STRUCT Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GMLGeometryCLOB

          public static CLOB to_GMLGeometryCLOB(STRUCT geom)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                java.lang.Exception

      Deprecated. Use `to_GMLGeometryCLOBJS(java.sql.Struct)` instead.
      Returns GML2 CLOB object for the oracle.sql.STRUCT Geometry Object.
      Parameters:
      `geom` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometryCLOB

          public static CLOB to_GMLGeometryCLOB(java.sql.Struct geom)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                java.lang.Exception

      Deprecated. Use `to_GMLGeometryCLOBJS(java.sql.Struct)` instead.
      Returns GML2 CLOB object for the java.sql.Struct Geometry Object.
      Parameters:
      `geom` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometryCLOB

          public static CLOB to_GMLGeometryCLOB(STRUCT geom,
                                                NUMBER coordOrder)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                java.lang.Exception

      Deprecated. Use `to_GMLGeometryCLOBJS(java.sql.Struct, NUMBER)` instead.
      Returns GML2 CLOB object for the oracle.sql.STRUCT Geometry Object.
      Parameters:
      `geom` -

      `coordOrder` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometryCLOB

          public static CLOB to_GMLGeometryCLOB(java.sql.Struct geom,
                                                NUMBER coordOrder)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                java.lang.Exception

      Deprecated. Use `to_GMLGeometryCLOBJS(java.sql.Struct, NUMBER)` instead.
      Returns GML2 CLOB object for the java.sql.Struct Geometry Object.
      Parameters:
      `geom` -

      `coordOrder` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometryCLOB

          public static CLOB to_GMLGeometryCLOB(STRUCT geom,
                                                java.lang.String srsNameSpace,
                                                java.lang.String srsAlias,
                                                NUMBER coordOrder)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                java.lang.Exception

      Deprecated. Use `to_GMLGeometryCLOBJS(java.sql.Struct, String, String, NUMBER)` instead.
      Returns GML2 CLOB object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      `coordOrder` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometryCLOB

          public static CLOB to_GMLGeometryCLOB(java.sql.Struct geom,
                                                java.lang.String srsNameSpace,
                                                java.lang.String srsAlias,
                                                NUMBER coordOrder)
                                         throws java.sql.SQLException,
                                                java.io.IOException,
                                                java.lang.Exception

      Deprecated. Use `to_GMLGeometryCLOBJS(java.sql.Struct, String, String, NUMBER)` instead.
      Returns GML2 CLOB object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      `coordOrder` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(java.sql.Struct geom,
                                                        int coordOrder)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException

      Returns GML2 String object for the java.sql.Struct Geometry Object. is_srsname_in_urn_form is NULL.
      Parameters:
      `geom` -

      `coordOrder` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(STRUCT geom,
                                                        int coordOrder)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException

      Deprecated. Use `to_GMLGeometry(java.sql.Struct, int)` instead.
      Returns GML2 String object for the oracle.sql.STRUCT Geometry Object. is_srsname_in_urn_form is NULL.
      Parameters:
      `geom` -

      `coordOrder` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(java.sql.Struct geom,
                                                        java.lang.String is_srsname_in_urn_form,
                                                        int coordOrder)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException

      Returns GML2 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `coordOrder` -

      `is_srsname_in_urn_form` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(STRUCT geom,
                                                        java.lang.String is_srsname_in_urn_form,
                                                        int coordOrder)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException

      Deprecated. Use `to_GMLGeometry(java.sql.Struct, String, int)` instead.
      Returns GML2 String object for the oracle.sql.STRUCT Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `coordOrder` -

      `is_srsname_in_urn_form` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(java.sql.Struct geom,
                                                        java.lang.String srsNameSpace,
                                                        java.lang.String srsAlias,
                                                        java.lang.String is_srsname_in_urn_form,
                                                        int coordOrder)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Returns GML2 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(STRUCT geom,
                                                        java.lang.String srsNameSpace,
                                                        java.lang.String srsAlias,
                                                        java.lang.String is_srsname_in_urn_form,
                                                        int coordOrder)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Deprecated. Use `to_GMLGeometry(java.sql.Struct, String, String, String, int)` instead.
      Returns GML2 String object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(java.sql.Struct geom,
                                                        java.lang.String srsNameSpace,
                                                        java.lang.String srsAlias,
                                                        java.lang.String is_srsname_in_urn_form,
                                                        int coordOrder,
                                                        java.sql.Connection conn)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Returns GML2 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(STRUCT geom,
                                                        java.lang.String srsNameSpace,
                                                        java.lang.String srsAlias,
                                                        java.lang.String is_srsname_in_urn_form,
                                                        int coordOrder,
                                                        java.sql.Connection conn)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Deprecated. Use `to_GMLGeometry(java.sql.Struct, String, String, String, int, Connection)` instead.
      Returns GML2 String object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      `conn` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(java.sql.Struct geom,
                                                        java.lang.String is_srsname_in_urn_form,
                                                        int coordOrder,
                                                        java.sql.Connection conn)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException

      Returns GML2 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `coordOrder` -

      `is_srsname_in_urn_form` -

      `conn` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GMLGeometry

          public static java.lang.String to_GMLGeometry(STRUCT geom,
                                                        java.lang.String is_srsname_in_urn_form,
                                                        int coordOrder,
                                                        java.sql.Connection conn)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException

      Deprecated. Use `to_GMLGeometry(java.sql.Struct, String, int, Connection)` instead.
      Returns GML2 String object for the oracle.sql.STRUCT Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `coordOrder` -

      `is_srsname_in_urn_form` -

      `conn` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GMLGeometryCLOBJS

          public static OracleClob to_GMLGeometryCLOBJS(java.sql.Struct geom)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Returns GML2 OracleClob object for the java.sql.Struct Geometry Object.
      Parameters:
      `geom` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometryCLOBJS

          public static OracleClob to_GMLGeometryCLOBJS(java.sql.Struct geom,
                                                        NUMBER coordOrder)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Returns GML2 OracleClob object for the java.sql.Struct Geometry Object.
      Parameters:
      `geom` -

      `coordOrder` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GMLGeometryCLOBJS

          public static OracleClob to_GMLGeometryCLOBJS(java.sql.Struct geom,
                                                        java.lang.String srsNameSpace,
                                                        java.lang.String srsAlias)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Returns GML2 OracleClob object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GMLGeometryCLOBJS

          public static OracleClob to_GMLGeometryCLOBJS(java.sql.Struct geom,
                                                        java.lang.String srsNameSpace,
                                                        java.lang.String srsAlias,
                                                        NUMBER coordOrder)
                                                 throws java.sql.SQLException,
                                                        java.io.IOException,
                                                        java.lang.Exception

      Returns GML2 OracleClob object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      `coordOrder` -

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

- [Prev Class](GML.md)
- [Next Class](GML3.md)

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
