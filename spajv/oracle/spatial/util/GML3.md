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

- [Prev Class](GML2.md)
- [Next Class](GML3.GMLVersion.md)

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

## Class GML3

- java.lang.Object

- - oracle.spatial.util.GML3

<!-- -->

-

  ------------------------------------------------------------------------



      public class GML3
      extends java.lang.Object

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                    |
    |-------------------|------------------------------------------|
    | `static class `   | [`GML3.GMLVersion`](GML3.GMLVersion.md)  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `GML3``()`                  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type         | Method and Description                                                                                                                                                                                                                                                                                                                                                               |
    |---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`             | `setConnection``(java.sql.Connection conn)`                                                                                                                                                                                                                                                                                                                                          |
    | `void`                    | `setGmlVersion``(`[`GML3.GMLVersion`](GML3.GMLVersion.md)` gmlVersion)`<br>Set the version of GML to generate.                                                                                                                                                                                                                                                                       |
    | `static void`             | `setsrsAlias``(java.lang.String srsAlias)`                                                                                                                                                                                                                                                                                                                                           |
    | `static void`             | `setsrsNameSpace``(java.lang.String srsNameSpace)`                                                                                                                                                                                                                                                                                                                                   |
    | `static java.lang.String` | `to_GML3_2Geometry``(java.sql.Struct geom)`<br>Returns GML3.2.1 String object for the java.sql.Struct Geometry Object.                                                                                                                                                                                                                                                               |
    | `static java.lang.String` | `to_GML3_2Geometry``(STRUCT geom)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct)` instead.                                                                                                                                                                                                                                                                                |
    | `static java.lang.String` | `to_GML3_2Geometry``(java.sql.Struct geom, java.lang.String is_srsname_in_urn_form)`<br>Returns GML3.2.1 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.                                                                                                                                                                                      |
    | `static java.lang.String` | `to_GML3_2Geometry``(STRUCT geom, java.lang.String is_srsname_in_urn_form)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String)` instead.                                                                                                                                                                                                                               |
    | `static java.lang.String` | `to_GML3_2Geometry``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String, String)` instead.                                                                                                                                                                                                      |
    | `static java.lang.String` | `to_GML3_2Geometry``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form)`<br>Returns GML3.2.1 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.                                                                                             |
    | `static java.lang.String` | `to_GML3_2Geometry``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String, String, String)` instead.                                                                                                                                                     |
    | `static CLOB`             | `to_GML3_2GeometryCLOB``(java.sql.Struct geom, NUMBER coordOrder)`<br>Deprecated. <br>Use `to_GML3GeometryCLOBJS(java.sql.Struct, NUMBER)` instead.                                                                                                                                                                                                                                  |
    | `static CLOB`             | `to_GML3_2GeometryCLOB``(STRUCT geom, NUMBER coordOrder)`<br>Deprecated. <br>Use `to_GML3_2GeometryCLOBJS(java.sql.Struct, NUMBER)` instead.                                                                                                                                                                                                                                         |
    | `static CLOB`             | `to_GML3_2GeometryCLOB``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Deprecated. <br>Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String)` instead.                                                                                                                                                                                   |
    | `static CLOB`             | `to_GML3_2GeometryCLOB``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, NUMBER coordOrder)`<br>Deprecated. <br>Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String, NUMBER)` instead.                                                                                                                                                        |
    | `static CLOB`             | `to_GML3_2GeometryCLOB``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias, NUMBER coordOrder)`<br>Deprecated. <br>Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String, NUMBER)` instead.                                                                                                                                                                 |
    | `static OracleClob`       | `to_GML3_2GeometryCLOBJS``(java.sql.Struct geom)`<br>Returns GML3.2.1 OracleClob object for the java.sql.Struct Geometry Object.                                                                                                                                                                                                                                                     |
    | `static OracleClob`       | `to_GML3_2GeometryCLOBJS``(java.sql.Struct geom, NUMBER coordOrder)`<br>Returns GML3.2.1 OracleClob object for the java.sql.Struct Geometry Object with coordOrder.                                                                                                                                                                                                                  |
    | `static OracleClob`       | `to_GML3_2GeometryCLOBJS``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Returns GML3.2.1 OracleClob object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.                                                                                                                                                            |
    | `static OracleClob`       | `to_GML3_2GeometryCLOBJS``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, NUMBER coordOrder)`<br>Returns GML3.2.1 OracleClob object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.                                                                                                                                         |
    | `static java.lang.String` | `to_GML3Geometry``(`[`JGeometry`](../geometry/JGeometry.md)` theGeom, `[`GML3.GMLVersion`](GML3.GMLVersion.md)` version)`                                                                                                                                                                                                                                                            |
    | `static java.lang.String` | `to_GML3Geometry``(`[`JGeometry`](../geometry/JGeometry.md)` theGeom, java.lang.String is_srsname_in_urn_form, `[`GML3.GMLVersion`](GML3.GMLVersion.md)` gmlVersion)`                                                                                                                                                                                                                |
    | `static java.lang.String` | `to_GML3Geometry``(java.sql.Struct geom)`<br>Returns GML311 String object for the java.sql.Struct Geometry Object.                                                                                                                                                                                                                                                                   |
    | `static java.lang.String` | `to_GML3Geometry``(STRUCT geom)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct)` instead.                                                                                                                                                                                                                                                                                  |
    | `static java.lang.String` | `to_GML3Geometry``(java.sql.Struct geom, int coordOrder)`<br>Returns GML311 String object for the java.sql.Struct Geometry Object.                                                                                                                                                                                                                                                   |
    | `static java.lang.String` | `to_GML3Geometry``(STRUCT geom, int coordOrder)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, int)` instead.                                                                                                                                                                                                                                                             |
    | `static java.lang.String` | `to_GML3Geometry``(java.sql.Struct geom, java.lang.String is_srsname_in_urn_form)`<br>Returns GML311 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.                                                                                                                                                                                          |
    | `static java.lang.String` | `to_GML3Geometry``(STRUCT geom, java.lang.String is_srsname_in_urn_form)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String)` instead.                                                                                                                                                                                                                                 |
    | `static java.lang.String` | `to_GML3Geometry``(java.sql.Struct geom, java.lang.String is_srsname_in_urn_form, int coordOrder)`<br>Returns GML311 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.                                                                                                                                                                          |
    | `static java.lang.String` | `to_GML3Geometry``(STRUCT geom, java.lang.String is_srsname_in_urn_form, int coordOrder)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String, int)` instead.                                                                                                                                                                                                            |
    | `static java.lang.String` | `to_GML3Geometry``(java.sql.Struct geom, java.lang.String is_srsname_in_urn_form, int coordOrder, java.sql.Connection conn)`<br>Returns GML311 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.                                                                                                                                                |
    | `static java.lang.String` | `to_GML3Geometry``(STRUCT geom, java.lang.String is_srsname_in_urn_form, int coordOrder, java.sql.Connection conn)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String, int, Connection)` instead.                                                                                                                                                                      |
    | `static java.lang.String` | `to_GML3Geometry``(java.sql.Struct geom, java.lang.String is_srsname_in_urn_form, int coordOrder, `[`GML3.GMLVersion`](GML3.GMLVersion.md)` gmlversion)`<br>Returns GML311 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.                                                                                                                    |
    | `static java.lang.String` | `to_GML3Geometry``(STRUCT geom, java.lang.String is_srsname_in_urn_form, int coordOrder, `[`GML3.GMLVersion`](GML3.GMLVersion.md)` gmlVersion)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String, int)` instead.                                                                                                                                                      |
    | `static java.lang.String` | `to_GML3Geometry``(java.sql.Struct geom, java.lang.String is_srsname_in_urn_form, int coordOrder, `[`GML3.GMLVersion`](GML3.GMLVersion.md)` gmlVersion, java.sql.Connection conn)`<br>Returns GML311 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.                                                                                          |
    | `static java.lang.String` | `to_GML3Geometry``(STRUCT geom, java.lang.String is_srsname_in_urn_form, int coordOrder, `[`GML3.GMLVersion`](GML3.GMLVersion.md)` gmlVersion, java.sql.Connection conn)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String, int, Connection)` instead.                                                                                                                |
    | `static java.lang.String` | `to_GML3Geometry``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Returns GML311 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.                                                                                                                                                                          |
    | `static java.lang.String` | `to_GML3Geometry``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String, String)` instead.                                                                                                                                                                                                        |
    | `static java.lang.String` | `to_GML3Geometry``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form)`<br>Returns GML311 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.                                                                                                 |
    | `static java.lang.String` | `to_GML3Geometry``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String, String, String)` instead.                                                                                                                                                       |
    | `static java.lang.String` | `to_GML3Geometry``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form, int coordOrder)`<br>Returns GML311 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.                                                                                 |
    | `static java.lang.String` | `to_GML3Geometry``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form, int coordOrder)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String, String, String, int)` instead.                                                                                                                                  |
    | `static java.lang.String` | `to_GML3Geometry``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form, int coordOrder, java.sql.Connection conn)`<br>Returns GML311 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.                                                       |
    | `static java.lang.String` | `to_GML3Geometry``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form, int coordOrder, java.sql.Connection conn)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String, String, String, int, Connection)` instead.                                                                                            |
    | `static java.lang.String` | `to_GML3Geometry``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form, int coordOrder, `[`GML3.GMLVersion`](GML3.GMLVersion.md)` gmlVersion, java.sql.Connection conn)`<br>Returns GML311 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form. |
    | `static java.lang.String` | `to_GML3Geometry``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias, java.lang.String is_srsname_in_urn_form, int coordOrder, `[`GML3.GMLVersion`](GML3.GMLVersion.md)` gmlVersion, java.sql.Connection conn)`<br>Deprecated. <br>Use `to_GML3Geometry(java.sql.Struct, String, String, String, int, Connection)` instead.                                      |
    | `static CLOB`             | `to_GML3GeometryCLOB``(java.sql.Struct geom)`<br>Deprecated. <br>Use `to_GML3GeometryCLOBJS(java.sql.Struct)` instead.                                                                                                                                                                                                                                                               |
    | `static CLOB`             | `to_GML3GeometryCLOB``(STRUCT geom)`<br>Deprecated. <br>Use `to_GML3GeometryCLOBJS(java.sql.Struct)` instead.                                                                                                                                                                                                                                                                        |
    | `static CLOB`             | `to_GML3GeometryCLOB``(java.sql.Struct geom, NUMBER coordOrder)`<br>Deprecated. <br>Use `to_GML3GeometryCLOBJS(java.sql.Struct, NUMBER)` instead.                                                                                                                                                                                                                                    |
    | `static CLOB`             | `to_GML3GeometryCLOB``(STRUCT geom, NUMBER coordOrder)`<br>Deprecated. <br>Use `to_GML3GeometryCLOBJS(java.sql.Struct, NUMBER)` instead.                                                                                                                                                                                                                                             |
    | `static CLOB`             | `to_GML3GeometryCLOB``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Deprecated. <br>Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String)` instead.                                                                                                                                                                                     |
    | `static CLOB`             | `to_GML3GeometryCLOB``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Deprecated. <br>Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String)` instead.                                                                                                                                                                                              |
    | `static CLOB`             | `to_GML3GeometryCLOB``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, NUMBER coordOrder)`<br>Deprecated. <br>Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String, NUMBER)` instead.                                                                                                                                                          |
    | `static CLOB`             | `to_GML3GeometryCLOB``(STRUCT geom, java.lang.String srsNameSpace, java.lang.String srsAlias, NUMBER coordOrder)`<br>Deprecated. <br>Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String, NUMBER)` instead.                                                                                                                                                                   |
    | `static OracleClob`       | `to_GML3GeometryCLOBJS``(java.sql.Struct geom)`<br>Returns GML311 OracleClob object for the java.sql.Struct Geometry Object.                                                                                                                                                                                                                                                         |
    | `static OracleClob`       | `to_GML3GeometryCLOBJS``(java.sql.Struct geom, NUMBER coordOrder)`<br>Returns GML311 OracleClob object for the java.sql.Struct Geometry Object with coordOrder.                                                                                                                                                                                                                      |
    | `static OracleClob`       | `to_GML3GeometryCLOBJS``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias)`<br>Returns GML311 OracleClob object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.                                                                                                                                                                |
    | `static OracleClob`       | `to_GML3GeometryCLOBJS``(java.sql.Struct geom, java.lang.String srsNameSpace, java.lang.String srsAlias, NUMBER coordOrder)`<br>Returns GML311 OracleClob object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.                                                                                                                                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GML3

          public GML3()

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

    - #### setGmlVersion

          public void setGmlVersion(GML3.GMLVersion gmlVersion)

      Set the version of GML to generate.
      Parameters:
      `gmlVersion` - An instance of [`GML3.GMLVersion`](GML3.GMLVersion.md) enumerator.

    <!-- -->

    - #### to_GML3GeometryCLOB

          public static CLOB to_GML3GeometryCLOB(STRUCT geom,
                                                 java.lang.String srsNameSpace,
                                                 java.lang.String srsAlias)
                                          throws java.sql.SQLException,
                                                 java.io.IOException,
                                                 java.lang.Exception

      Deprecated. Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String)` instead.
      Returns GML311 CLOB object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3GeometryCLOB

          public static CLOB to_GML3GeometryCLOB(java.sql.Struct geom,
                                                 java.lang.String srsNameSpace,
                                                 java.lang.String srsAlias)
                                          throws java.sql.SQLException,
                                                 java.io.IOException,
                                                 java.lang.Exception

      Deprecated. Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String)` instead.
      Returns GML311 CLOB object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(java.sql.Struct geom,
                                                         java.lang.String srsNameSpace,
                                                         java.lang.String srsAlias)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Returns GML311 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(STRUCT geom,
                                                         java.lang.String srsNameSpace,
                                                         java.lang.String srsAlias)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String, String)` instead.
      Returns GML311 String object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(java.sql.Struct geom,
                                                         java.lang.String srsNameSpace,
                                                         java.lang.String srsAlias,
                                                         java.lang.String is_srsname_in_urn_form)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Returns GML311 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
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

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(STRUCT geom,
                                                         java.lang.String srsNameSpace,
                                                         java.lang.String srsAlias,
                                                         java.lang.String is_srsname_in_urn_form)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String, String, String)` instead.
      Returns GML311 String object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
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

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(java.sql.Struct geom)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Returns GML311 String object for the java.sql.Struct Geometry Object. is_srsname_in_urn_form is NULL.
      Parameters:
      `geom` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(STRUCT geom)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Deprecated. Use `to_GML3Geometry(java.sql.Struct)` instead.
      Returns GML311 String object for the oracle.sql.STRUCT Geometry Object. is_srsname_in_urn_form is NULL.
      Parameters:
      `geom` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(java.sql.Struct geom,
                                                         java.lang.String is_srsname_in_urn_form)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Returns GML311 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(STRUCT geom,
                                                         java.lang.String is_srsname_in_urn_form)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String)` instead.
      Returns GML311 String object for the oracle.sql.STRUCT Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3_2Geometry

          public static java.lang.String to_GML3_2Geometry(java.sql.Struct geom,
                                                           java.lang.String is_srsname_in_urn_form)
                                                    throws java.sql.SQLException,
                                                           java.io.IOException

      Returns GML3.2.1 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3_2Geometry

          public static java.lang.String to_GML3_2Geometry(java.sql.Struct geom)
                                                    throws java.sql.SQLException,
                                                           java.io.IOException

      Returns GML3.2.1 String object for the java.sql.Struct Geometry Object. is_srsname_in_urn_form is NULL.
      Parameters:
      `geom` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3_2GeometryCLOB

          public static CLOB to_GML3_2GeometryCLOB(java.sql.Struct geom,
                                                   java.lang.String srsNameSpace,
                                                   java.lang.String srsAlias)
                                            throws java.sql.SQLException,
                                                   java.io.IOException,
                                                   java.lang.Exception

      Deprecated. Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String)` instead.
      Returns GML3.2.1 CLOB object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3_2Geometry

          public static java.lang.String to_GML3_2Geometry(java.sql.Struct geom,
                                                           java.lang.String srsNameSpace,
                                                           java.lang.String srsAlias,
                                                           java.lang.String is_srsname_in_urn_form)
                                                    throws java.sql.SQLException,
                                                           java.io.IOException,
                                                           java.lang.Exception

      Returns GML3.2.1 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
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

    - #### to_GML3_2Geometry

          public static java.lang.String to_GML3_2Geometry(STRUCT geom,
                                                           java.lang.String srsNameSpace,
                                                           java.lang.String srsAlias,
                                                           java.lang.String is_srsname_in_urn_form)
                                                    throws java.sql.SQLException,
                                                           java.io.IOException,
                                                           java.lang.Exception

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String, String, String)` instead.
      Returns GML3.2.1 String object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
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

    - #### to_GML3_2Geometry

          public static java.lang.String to_GML3_2Geometry(STRUCT geom,
                                                           java.lang.String srsNameSpace,
                                                           java.lang.String srsAlias)
                                                    throws java.sql.SQLException,
                                                           java.io.IOException,
                                                           java.lang.Exception

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String, String)` instead.
      Returns GML3.2.1 String object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3_2Geometry

          public static java.lang.String to_GML3_2Geometry(STRUCT geom)
                                                    throws java.sql.SQLException,
                                                           java.io.IOException

      Deprecated. Use `to_GML3Geometry(java.sql.Struct)` instead.
      Returns GML3.2.1 String object for the oracle.sql.STRUCT Geometry Object. is_srsname_in_urn_form is NULL.
      Parameters:
      `geom` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3_2Geometry

          public static java.lang.String to_GML3_2Geometry(STRUCT geom,
                                                           java.lang.String is_srsname_in_urn_form)
                                                    throws java.sql.SQLException,
                                                           java.io.IOException

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String)` instead.
      Returns GML3.2.1 String object for the oracle.sql.STRUCT Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3GeometryCLOB

          public static CLOB to_GML3GeometryCLOB(STRUCT geom)
                                          throws java.sql.SQLException,
                                                 java.io.IOException,
                                                 java.lang.Exception

      Deprecated. Use `to_GML3GeometryCLOBJS(java.sql.Struct)` instead.
      Returns GML311 CLOB object for the oracle.sql.STRUCT Geometry Object.
      Parameters:
      `geom` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GML3GeometryCLOB

          public static CLOB to_GML3GeometryCLOB(java.sql.Struct geom)
                                          throws java.sql.SQLException,
                                                 java.io.IOException,
                                                 java.lang.Exception

      Deprecated. Use `to_GML3GeometryCLOBJS(java.sql.Struct)` instead.
      Returns GML311 CLOB object for the java.sql.Struct Geometry Object.
      Parameters:
      `geom` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(JGeometry theGeom,
                                                         GML3.GMLVersion version)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(JGeometry theGeom,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         GML3.GMLVersion gmlVersion)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3GeometryCLOB

          public static CLOB to_GML3GeometryCLOB(STRUCT geom,
                                                 NUMBER coordOrder)
                                          throws java.sql.SQLException,
                                                 java.io.IOException,
                                                 java.lang.Exception

      Deprecated. Use `to_GML3GeometryCLOBJS(java.sql.Struct, NUMBER)` instead.
      Returns GML311 CLOB object for the oracle.sql.STRUCT Geometry Object with coordOrder.
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

    - #### to_GML3GeometryCLOB

          public static CLOB to_GML3GeometryCLOB(java.sql.Struct geom,
                                                 NUMBER coordOrder)
                                          throws java.sql.SQLException,
                                                 java.io.IOException,
                                                 java.lang.Exception

      Deprecated. Use `to_GML3GeometryCLOBJS(java.sql.Struct, NUMBER)` instead.
      Returns GML311 CLOB object for the java.sql.Struct Geometry Object with coordOrder.
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

    - #### to_GML3GeometryCLOB

          public static CLOB to_GML3GeometryCLOB(STRUCT geom,
                                                 java.lang.String srsNameSpace,
                                                 java.lang.String srsAlias,
                                                 NUMBER coordOrder)
                                          throws java.sql.SQLException,
                                                 java.io.IOException,
                                                 java.lang.Exception

      Deprecated. Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String, NUMBER)` instead.
      Returns GML311 CLOB object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3GeometryCLOB

          public static CLOB to_GML3GeometryCLOB(java.sql.Struct geom,
                                                 java.lang.String srsNameSpace,
                                                 java.lang.String srsAlias,
                                                 NUMBER coordOrder)
                                          throws java.sql.SQLException,
                                                 java.io.IOException,
                                                 java.lang.Exception

      Deprecated. Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String, NUMBER)` instead.
      Returns GML311 CLOB object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3_2GeometryCLOB

          public static CLOB to_GML3_2GeometryCLOB(STRUCT geom,
                                                   NUMBER coordOrder)
                                            throws java.sql.SQLException,
                                                   java.io.IOException,
                                                   java.lang.Exception

      Deprecated. Use `to_GML3_2GeometryCLOBJS(java.sql.Struct, NUMBER)` instead.
      Returns GML3.2.1 CLOB object for the oracle.sql.STRUCT Geometry Object with coordOrder.
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

    - #### to_GML3_2GeometryCLOB

          public static CLOB to_GML3_2GeometryCLOB(STRUCT geom,
                                                   java.lang.String srsNameSpace,
                                                   java.lang.String srsAlias,
                                                   NUMBER coordOrder)
                                            throws java.sql.SQLException,
                                                   java.io.IOException,
                                                   java.lang.Exception

      Deprecated. Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String, NUMBER)` instead.
      Returns GML3.2.1 CLOB object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3_2GeometryCLOB

          public static CLOB to_GML3_2GeometryCLOB(java.sql.Struct geom,
                                                   NUMBER coordOrder)
                                            throws java.sql.SQLException,
                                                   java.io.IOException,
                                                   java.lang.Exception

      Deprecated. Use `to_GML3GeometryCLOBJS(java.sql.Struct, NUMBER)` instead.
      Returns GML3.2.1 CLOB object for the java.sql.Struct Geometry Object with coordOrder.
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

    - #### to_GML3_2GeometryCLOB

          public static CLOB to_GML3_2GeometryCLOB(java.sql.Struct geom,
                                                   java.lang.String srsNameSpace,
                                                   java.lang.String srsAlias,
                                                   NUMBER coordOrder)
                                            throws java.sql.SQLException,
                                                   java.io.IOException,
                                                   java.lang.Exception

      Deprecated. Use `to_GML3GeometryCLOBJS(java.sql.Struct, String, String, NUMBER)` instead.
      Returns GML3.2.1 CLOB object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(java.sql.Struct geom,
                                                         int coordOrder)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Returns GML311 String object for the java.sql.Struct Geometry Object. is_srsname_in_urn_form is NULL.
      Parameters:
      `geom` -

      `coordOrder` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(STRUCT geom,
                                                         int coordOrder)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, int)` instead.
      Returns GML311 String object for the oracle.sql.STRUCT Geometry Object. is_srsname_in_urn_form is NULL.
      Parameters:
      `geom` -

      `coordOrder` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(java.sql.Struct geom,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Returns GML311 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(java.sql.Struct geom,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder,
                                                         GML3.GMLVersion gmlversion)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Returns GML311 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(STRUCT geom,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String, int)` instead.
      Returns GML311 String object for the oracle.sql.STRUCT Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(STRUCT geom,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder,
                                                         GML3.GMLVersion gmlVersion)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String, int)` instead.
      Returns GML String object for the oracle.sql.STRUCT Geometry Object by checking srsname in URN form. The version of the GML to be generated is determined by the gmlVersion parameter
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      `gmlVersion` - if null GML 3.1.1 is generated

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(java.sql.Struct geom,
                                                         java.lang.String srsNameSpace,
                                                         java.lang.String srsAlias,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Returns GML311 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
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

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(STRUCT geom,
                                                         java.lang.String srsNameSpace,
                                                         java.lang.String srsAlias,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String, String, String, int)` instead.
      Returns GML311 String object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
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

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(java.sql.Struct geom,
                                                         java.lang.String srsNameSpace,
                                                         java.lang.String srsAlias,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder,
                                                         java.sql.Connection conn)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Returns GML311 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
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

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(java.sql.Struct geom,
                                                         java.lang.String srsNameSpace,
                                                         java.lang.String srsAlias,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder,
                                                         GML3.GMLVersion gmlVersion,
                                                         java.sql.Connection conn)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Returns GML311 String object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form. This is necessary for WFS 2.0 to use GML 3.2.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      `gmlVersion` -

      `conn` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(STRUCT geom,
                                                         java.lang.String srsNameSpace,
                                                         java.lang.String srsAlias,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder,
                                                         java.sql.Connection conn)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String, String, String, int, Connection)` instead.
      Returns GML311 String object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form.
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

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(STRUCT geom,
                                                         java.lang.String srsNameSpace,
                                                         java.lang.String srsAlias,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder,
                                                         GML3.GMLVersion gmlVersion,
                                                         java.sql.Connection conn)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String, String, String, int, Connection)` instead.
      Returns GML311 String object for the oracle.sql.STRUCT Geometry Object with srsNameSpace and srsAlias by checking srsname in URN form. This is necessary for WFS 2.0 to use GML 3.2.
      Parameters:
      `geom` -

      `srsNameSpace` -

      `srsAlias` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      `gmlVersion` -

      `conn` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(java.sql.Struct geom,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder,
                                                         java.sql.Connection conn)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Returns GML311 String object for the java.sql.Struct Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      `conn` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(java.sql.Struct geom,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder,
                                                         GML3.GMLVersion gmlVersion,
                                                         java.sql.Connection conn)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Returns GML311 String object for the java.sql.Struct Geometry Object by checking srsname in URN form. This is necessary for WFS 2.0 to use GML 3.2.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      `gmlVersion` -

      `conn` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(STRUCT geom,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder,
                                                         java.sql.Connection conn)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String, int, Connection)` instead.
      Returns GML311 String object for the oracle.sql.STRUCT Geometry Object by checking srsname in URN form.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      `conn` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3Geometry

          public static java.lang.String to_GML3Geometry(STRUCT geom,
                                                         java.lang.String is_srsname_in_urn_form,
                                                         int coordOrder,
                                                         GML3.GMLVersion gmlVersion,
                                                         java.sql.Connection conn)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException

      Deprecated. Use `to_GML3Geometry(java.sql.Struct, String, int, Connection)` instead.
      Returns GML311 String object for the oracle.sql.STRUCT Geometry Object by checking srsname in URN form. This is necessary for WFS 2.0 to use GML 3.2.
      Parameters:
      `geom` -

      `is_srsname_in_urn_form` -

      `coordOrder` -

      `gmlVersion` -

      `conn` -

      Returns:
      String

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### to_GML3GeometryCLOBJS

          public static OracleClob to_GML3GeometryCLOBJS(java.sql.Struct geom)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Returns GML311 OracleClob object for the java.sql.Struct Geometry Object.
      Parameters:
      `geom` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GML3GeometryCLOBJS

          public static OracleClob to_GML3GeometryCLOBJS(java.sql.Struct geom,
                                                         NUMBER coordOrder)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Returns GML311 OracleClob object for the java.sql.Struct Geometry Object with coordOrder.
      Parameters:
      `geom` -

      `coordOrder` -

      Returns:
      OracleClob

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GML3GeometryCLOBJS

          public static OracleClob to_GML3GeometryCLOBJS(java.sql.Struct geom,
                                                         java.lang.String srsNameSpace,
                                                         java.lang.String srsAlias)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Returns GML311 OracleClob object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3GeometryCLOBJS

          public static OracleClob to_GML3GeometryCLOBJS(java.sql.Struct geom,
                                                         java.lang.String srsNameSpace,
                                                         java.lang.String srsAlias,
                                                         NUMBER coordOrder)
                                                  throws java.sql.SQLException,
                                                         java.io.IOException,
                                                         java.lang.Exception

      Returns GML311 OracleClob object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3_2GeometryCLOBJS

          public static OracleClob to_GML3_2GeometryCLOBJS(java.sql.Struct geom)
                                                    throws java.sql.SQLException,
                                                           java.io.IOException,
                                                           java.lang.Exception

      Returns GML3.2.1 OracleClob object for the java.sql.Struct Geometry Object.
      Parameters:
      `geom` -

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GML3_2GeometryCLOBJS

          public static OracleClob to_GML3_2GeometryCLOBJS(java.sql.Struct geom,
                                                           java.lang.String srsNameSpace,
                                                           java.lang.String srsAlias)
                                                    throws java.sql.SQLException,
                                                           java.io.IOException,
                                                           java.lang.Exception

      Returns GML3.2.1 OracleClob object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
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

    - #### to_GML3_2GeometryCLOBJS

          public static OracleClob to_GML3_2GeometryCLOBJS(java.sql.Struct geom,
                                                           NUMBER coordOrder)
                                                    throws java.sql.SQLException,
                                                           java.io.IOException,
                                                           java.lang.Exception

      Returns GML3.2.1 OracleClob object for the java.sql.Struct Geometry Object with coordOrder.
      Parameters:
      `geom` -

      `coordOrder` -

      Returns:
      OracleClob

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### to_GML3_2GeometryCLOBJS

          public static OracleClob to_GML3_2GeometryCLOBJS(java.sql.Struct geom,
                                                           java.lang.String srsNameSpace,
                                                           java.lang.String srsAlias,
                                                           NUMBER coordOrder)
                                                    throws java.sql.SQLException,
                                                           java.io.IOException,
                                                           java.lang.Exception

      Returns GML3.2.1 OracleClob object for the java.sql.Struct Geometry Object with srsNameSpace and srsAlias.
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

- [Prev Class](GML2.md)
- [Next Class](GML3.GMLVersion.md)

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
