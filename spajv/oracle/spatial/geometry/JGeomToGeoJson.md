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

- [Prev Class](JGeometry.Point.md)
- [Next Class](JPoint2DD.md)

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

oracle.spatial.geometry

## Class JGeomToGeoJson

- java.lang.Object

- - oracle.spatial.geometry.JGeomToGeoJson

<!-- -->

-

  ------------------------------------------------------------------------



      public class JGeomToGeoJson
      extends java.lang.Object

  Provides convenient methods to generate JSON fragments. This class is meant for the API internal use only.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description             |
    |---------------------------|-----------------------------------|
    | `static java.lang.String` | `EMPTY_STR`                       |
    | `static java.lang.String` | `F_FEAT_GEOMETRY`                 |
    | `static java.lang.String` | `F_FEAT_ID`                       |
    | `static java.lang.String` | `F_FEAT_PROPS`                    |
    | `static java.lang.String` | `F_FEAT_TYPE`                     |
    | `static java.lang.String` | `F_FEATCOLL_ATTR_NAMES`           |
    | `static java.lang.String` | `F_FEATCOLL_ATTR_TYPES`           |
    | `static java.lang.String` | `F_FEATCOLL_BBOX`                 |
    | `static java.lang.String` | `F_FEATCOLL_CR`                   |
    | `static java.lang.String` | `F_FEATCOLL_FEATURES`             |
    | `static java.lang.String` | `F_FEATCOLL_GEODETIC`             |
    | `static java.lang.String` | `F_FEATCOLL_NAME`                 |
    | `static java.lang.String` | `F_FEATCOLL_SRS`                  |
    | `static java.lang.String` | `F_FEATCOLL_TYPE`                 |
    | `static java.lang.String` | `F_GEOM_COORDS`                   |
    | `static java.lang.String` | `F_GEOM_TYPE`                     |
    | `static java.lang.String` | `V_FEAT_TYPE_FEAT`                |
    | `static java.lang.String` | `V_FEATCOLL_TYPE`                 |
    | `static java.lang.String` | `V_GEOM_TYPE_GEOMETRYCOLLECTION`  |
    | `static java.lang.String` | `V_GEOM_TYPE_LINE`                |
    | `static java.lang.String` | `V_GEOM_TYPE_MULTILINE`           |
    | `static java.lang.String` | `V_GEOM_TYPE_MULTIPOINT`          |
    | `static java.lang.String` | `V_GEOM_TYPE_MULTIPOLYGON`        |
    | `static java.lang.String` | `V_GEOM_TYPE_POINT`               |
    | `static java.lang.String` | `V_GEOM_TYPE_POLYGON`             |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `JGeomToGeoJson``()`        |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                | Method and Description                                                                                                                                                                                                                                                                                 |
    |----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`                    | `asComplexValue``(java.util.Map<java.lang.String,java.lang.Object> properties, java.lang.StringBuilder res)`                                                                                                                                                                                           |
    | `static void`                    | `asComplexValue``(java.util.Map<java.lang.String,java.lang.Object> properties, java.lang.StringBuilder res, java.text.DecimalFormat decimalFormat)`                                                                                                                                                    |
    | `static void`                    | `asFieldName``(java.lang.String fieldName, java.lang.StringBuilder res)`                                                                                                                                                                                                                               |
    | `static java.lang.String`        | `asGeometry``(`[`JGeometry`](JGeometry.md)` geom)`                                                                                                                                                                                                                                                     |
    | `static void`                    | `asGeometry``(`[`JGeometry`](JGeometry.md)`[] geoms, java.lang.StringBuilder res)`                                                                                                                                                                                                                     |
    | `static void`                    | `asGeometry``(`[`JGeometry`](JGeometry.md)` geom, java.lang.StringBuilder res)`<br>Delegates to asGeometry with a null decimalFormat (which will then use the defaultDecimalFormat)                                                                                                                    |
    | `static void`                    | `asGeometry``(`[`JGeometry`](JGeometry.md)` geom, java.lang.StringBuilder res, java.text.DecimalFormat decimalFormat)`                                                                                                                                                                                 |
    | `static void`                    | `asNameValue``(java.lang.String name, java.lang.Object value, java.lang.StringBuilder res)`                                                                                                                                                                                                            |
    | `static void`                    | `asNameValue``(java.lang.String name, java.lang.Object value, java.lang.StringBuilder res, java.text.DecimalFormat decimalFormat)`                                                                                                                                                                     |
    | `static void`                    | `asNameValueList``(java.util.Map<java.lang.String,java.lang.Object> nameValueMap, java.lang.StringBuilder res)`                                                                                                                                                                                        |
    | `static void`                    | `asNameValueList``(java.util.Map<java.lang.String,java.lang.Object> nameValueMap, java.lang.StringBuilder res, java.text.DecimalFormat decimalFormat)`                                                                                                                                                 |
    | `static void`                    | `asSimpleValue``(java.lang.Object value, java.lang.StringBuilder res)`<br>Appends value to res.                                                                                                                                                                                                        |
    | `static void`                    | `asSimpleValue``(java.lang.Object value, java.lang.StringBuilder res, java.text.DecimalFormat decimalFormat)`<br>Note decimal formatting differs from most other methods in this class.                                                                                                                |
    | `static void`                    | `asText``(java.lang.String str, java.lang.StringBuilder res)`                                                                                                                                                                                                                                          |
    | `static java.text.DecimalFormat` | `decimalFormat``(java.util.Locale locale, java.lang.String pattern, int maxFractionDigits)`                                                                                                                                                                                                            |
    | `static java.lang.String`        | `genFeature``(java.lang.String id, `[`JGeometry`](JGeometry.md)` geom, java.util.Map<java.lang.String,java.lang.Object> properties)`                                                                                                                                                                   |
    | `static void`                    | `genFeature``(java.lang.String id, `[`JGeometry`](JGeometry.md)` geom, java.util.Map<java.lang.String,java.lang.Object> properties, java.lang.StringBuilder res)`                                                                                                                                      |
    | `static java.lang.String`        | `genFeatureCollectionHeader``(java.lang.String collName, int srid, boolean geodetic, double[] mbr, java.util.Map<java.lang.String,java.lang.String> attrs)`                                                                                                                                            |
    | `static void`                    | `genFeatureCollectionHeader``(java.lang.String collName, int srid, boolean geodetic, double[] mbr, java.util.Map<java.lang.String,java.lang.String> attrs, java.lang.StringBuilder res)`<br>Calls genFeatureCollectionHeader with a null decimalFormat (which will thus use the defaultDecimalFormat). |
    | `static void`                    | `genFeatureCollectionHeader``(java.lang.String collName, int srid, boolean geodetic, double[] mbr, java.util.Map<java.lang.String,java.lang.String> attrs, java.lang.StringBuilder res, java.text.DecimalFormat decimalFormat)`                                                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### EMPTY_STR

          public static final java.lang.String EMPTY_STR

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEATCOLL_TYPE

          public static final java.lang.String F_FEATCOLL_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEATCOLL_NAME

          public static final java.lang.String F_FEATCOLL_NAME

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEATCOLL_CR

          public static final java.lang.String F_FEATCOLL_CR

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEATCOLL_SRS

          public static final java.lang.String F_FEATCOLL_SRS

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEATCOLL_GEODETIC

          public static final java.lang.String F_FEATCOLL_GEODETIC

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEATCOLL_BBOX

          public static final java.lang.String F_FEATCOLL_BBOX

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEATCOLL_ATTR_NAMES

          public static final java.lang.String F_FEATCOLL_ATTR_NAMES

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEATCOLL_ATTR_TYPES

          public static final java.lang.String F_FEATCOLL_ATTR_TYPES

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEATCOLL_FEATURES

          public static final java.lang.String F_FEATCOLL_FEATURES

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEAT_TYPE

          public static final java.lang.String F_FEAT_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEAT_ID

          public static final java.lang.String F_FEAT_ID

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEAT_GEOMETRY

          public static final java.lang.String F_FEAT_GEOMETRY

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_FEAT_PROPS

          public static final java.lang.String F_FEAT_PROPS

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_GEOM_TYPE

          public static final java.lang.String F_GEOM_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### F_GEOM_COORDS

          public static final java.lang.String F_GEOM_COORDS

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### V_FEATCOLL_TYPE

          public static final java.lang.String V_FEATCOLL_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### V_FEAT_TYPE_FEAT

          public static final java.lang.String V_FEAT_TYPE_FEAT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### V_GEOM_TYPE_POINT

          public static final java.lang.String V_GEOM_TYPE_POINT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### V_GEOM_TYPE_MULTIPOINT

          public static final java.lang.String V_GEOM_TYPE_MULTIPOINT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### V_GEOM_TYPE_LINE

          public static final java.lang.String V_GEOM_TYPE_LINE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### V_GEOM_TYPE_MULTILINE

          public static final java.lang.String V_GEOM_TYPE_MULTILINE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### V_GEOM_TYPE_POLYGON

          public static final java.lang.String V_GEOM_TYPE_POLYGON

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### V_GEOM_TYPE_MULTIPOLYGON

          public static final java.lang.String V_GEOM_TYPE_MULTIPOLYGON

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### V_GEOM_TYPE_GEOMETRYCOLLECTION

          public static final java.lang.String V_GEOM_TYPE_GEOMETRYCOLLECTION

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### JGeomToGeoJson

          public JGeomToGeoJson()

  <!-- -->

  - ### Method Detail

    - #### genFeatureCollectionHeader

          public static java.lang.String genFeatureCollectionHeader(java.lang.String collName,
                                                                    int srid,
                                                                    boolean geodetic,
                                                                    double[] mbr,
                                                                    java.util.Map<java.lang.String,java.lang.String> attrs)

    <!-- -->

    - #### genFeatureCollectionHeader

          public static void genFeatureCollectionHeader(java.lang.String collName,
                                                        int srid,
                                                        boolean geodetic,
                                                        double[] mbr,
                                                        java.util.Map<java.lang.String,java.lang.String> attrs,
                                                        java.lang.StringBuilder res)

      Calls genFeatureCollectionHeader with a null decimalFormat (which will thus use the defaultDecimalFormat).
      Parameters:
      `collName` -

      `srid` -

      `geodetic` -

      `mbr` -

      `attrs` -

      `res` -

    <!-- -->

    - #### genFeatureCollectionHeader

          public static void genFeatureCollectionHeader(java.lang.String collName,
                                                        int srid,
                                                        boolean geodetic,
                                                        double[] mbr,
                                                        java.util.Map<java.lang.String,java.lang.String> attrs,
                                                        java.lang.StringBuilder res,
                                                        java.text.DecimalFormat decimalFormat)

    <!-- -->

    - #### genFeature

          public static void genFeature(java.lang.String id,
                                        JGeometry geom,
                                        java.util.Map<java.lang.String,java.lang.Object> properties,
                                        java.lang.StringBuilder res)

    <!-- -->

    - #### genFeature

          public static java.lang.String genFeature(java.lang.String id,
                                                    JGeometry geom,
                                                    java.util.Map<java.lang.String,java.lang.Object> properties)

    <!-- -->

    - #### asGeometry

          public static void asGeometry(JGeometry geom,
                                        java.lang.StringBuilder res)

      Delegates to asGeometry with a null decimalFormat (which will then use the defaultDecimalFormat)
      Parameters:
      `geom` -

      `res` -

    <!-- -->

    - #### asGeometry

          public static void asGeometry(JGeometry geom,
                                        java.lang.StringBuilder res,
                                        java.text.DecimalFormat decimalFormat)

    <!-- -->

    - #### asGeometry

          public static void asGeometry(JGeometry[] geoms,
                                        java.lang.StringBuilder res)

    <!-- -->

    - #### asGeometry

          public static java.lang.String asGeometry(JGeometry geom)

    <!-- -->

    - #### asComplexValue

          public static void asComplexValue(java.util.Map<java.lang.String,java.lang.Object> properties,
                                            java.lang.StringBuilder res)

    <!-- -->

    - #### asComplexValue

          public static void asComplexValue(java.util.Map<java.lang.String,java.lang.Object> properties,
                                            java.lang.StringBuilder res,
                                            java.text.DecimalFormat decimalFormat)

    <!-- -->

    - #### asNameValueList

          public static void asNameValueList(java.util.Map<java.lang.String,java.lang.Object> nameValueMap,
                                             java.lang.StringBuilder res)

    <!-- -->

    - #### asNameValueList

          public static void asNameValueList(java.util.Map<java.lang.String,java.lang.Object> nameValueMap,
                                             java.lang.StringBuilder res,
                                             java.text.DecimalFormat decimalFormat)

    <!-- -->

    - #### asNameValue

          public static void asNameValue(java.lang.String name,
                                         java.lang.Object value,
                                         java.lang.StringBuilder res)

    <!-- -->

    - #### asNameValue

          public static void asNameValue(java.lang.String name,
                                         java.lang.Object value,
                                         java.lang.StringBuilder res,
                                         java.text.DecimalFormat decimalFormat)

    <!-- -->

    - #### asText

          public static void asText(java.lang.String str,
                                    java.lang.StringBuilder res)

    <!-- -->

    - #### asFieldName

          public static void asFieldName(java.lang.String fieldName,
                                         java.lang.StringBuilder res)

    <!-- -->

    - #### asSimpleValue

          public static void asSimpleValue(java.lang.Object value,
                                           java.lang.StringBuilder res)

      Appends value to res. Passes a decimalFormat of null to .
      Parameters:
      `value` -

      `res` -

    <!-- -->

    - #### asSimpleValue

          public static void asSimpleValue(java.lang.Object value,
                                           java.lang.StringBuilder res,
                                           java.text.DecimalFormat decimalFormat)

      Note decimal formatting differs from most other methods in this class. Arrays of primitives are always output using toString(). If the specified decimalFormat is null, then Number or Boolean objects use toString() instead of the defaultDecimalFormat.
      Parameters:
      `value` - the value (or array) to output

      `res` - where the resulting string is appended

      `decimalFormat` - can be null, in which case Number or Boolean is formatted using toString( instead of using the default decimalFormat.

    <!-- -->

    - #### decimalFormat

          public static java.text.DecimalFormat decimalFormat(java.util.Locale locale,
                                                              java.lang.String pattern,
                                                              int maxFractionDigits)

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

- [Prev Class](JGeometry.Point.md)
- [Next Class](JPoint2DD.md)

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
