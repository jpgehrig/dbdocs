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

- [Prev Class](DataException.md)
- [Next Class](FastJGeometry.md)

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

## Class ElementExtractor

- java.lang.Object

- - oracle.spatial.geometry.ElementExtractor

<!-- -->

-

  ------------------------------------------------------------------------



      public class ElementExtractor
      extends java.lang.Object

  This extractor extracts elements from J3D_Geometry in an iterative fashion Composite surface is expected to be: \< , 1006, N\> N tuples of the form \<, 1003, x\> \<, 2003, x\>\* Composite solid should be of the form: \< , 1008, N\> N solids each of the form \<, 1007,\> specified using 1 outer surface and N inner surfaces \<, 1006, m\> and M tuples of the form \<,1003,\> m times followed by 0 or more inner solids specified as surfaces as: \<, 2006, p\> and p tuples of the form \<,2003,\>
  Multi-x geometry can have multiple of the composite-x and/or simple-x geometry. x is here could be solid, surface, line, point.

  The constructor function's extraction_level parameter can have the following values: LOWER_LEVEL: This returns the elements in the next level of hierarchy (e.g., for a solid, the next Level will be surfaces, for a polygon the next level will be lines etc.); MULTICOMP_TOSIMPLE: This returns the elements of a composite or multi-geometry. For instance, for a composite surface, it returns each surface element as a J3D_GEOMETRY in the "next" call; INNER_OUTER: This returns the inner/outer elements if any. For polygons, it returns the outer first which is followed by inner polygons in subsequent "next" calls. The method ElementExtractor.nextElement() returns J3D_GEOMETRY or null.

  If the 3-D geometry has shortcut (optimized box, rectangle) representation, this extractor expands those geometries to full extent via expandSolid and other routines in this code. Thus, the returned geometries will have explicit coordinates and elemInfo.

  In MULTICOMP_TOSIMPLE extraction level, users can also arrange to extract directly simple geometries from multi or composite geometries by setting the public parameter allow_comp_sub_elements to FALSE. The default value is TRUE, which means users will extract composite geometry first (if exists) from multi geometry.

  Optimized (shortcut) representations are only for axis aligned 3-D geometries.

  Please note that the INNER_OUTER parameter is different than the inner_outer integer array of nextElementmethod.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description     |
    |-------------------|---------------------------|
    | `static int`      | `ETYPE_COMPOSITEPOLYGON`  |
    | `static int`      | `ETYPE_COMPOSITESOLID`    |
    | `static int`      | `ETYPE_COMPOSITESURFACE`  |
    | `static int`      | `ETYPE_COMPOUNDCURVE`     |
    | `static int`      | `ETYPE_COMPOUNDRING`      |
    | `static int`      | `ETYPE_CURVE`             |
    | `static int`      | `ETYPE_POINT`             |
    | `static int`      | `ETYPE_POLYGON`           |
    | `static int`      | `ETYPE_RING`              |
    | `static int`      | `ETYPE_SOLID`             |
    | `static int`      | `ETYPE_SURFACE`           |
    | `static int`      | `ETYPE_UNKNOWN`           |
    | `static int`      | `GTYPE_COLLECTION`        |
    | `static int`      | `GTYPE_CURVE`             |
    | `static int`      | `GTYPE_MULTICURVE`        |
    | `static int`      | `GTYPE_MULTIPOINT`        |
    | `static int`      | `GTYPE_MULTIPOLYGON`      |
    | `static int`      | `GTYPE_MULTISOLID`        |
    | `static int`      | `GTYPE_MULTISURFACE`      |
    | `static int`      | `GTYPE_POINT`             |
    | `static int`      | `GTYPE_POLYGON`           |
    | `static int`      | `GTYPE_SOLID`             |
    | `static int`      | `GTYPE_SURFACE`           |
    | `static int`      | `INNER_OUTER`             |
    | `static int`      | `LOWER_LEVEL`             |
    | `static int`      | `MULTICOMP_TOSIMPLE`      |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                          |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ElementExtractor``(`[`J3D_Geometry`](J3D_Geometry.md)` geom)`                                                                                                       |
    | `ElementExtractor``(`[`J3D_Geometry`](J3D_Geometry.md)` geom, int type)`<br>Constructs an extractor that extracts elements from J3D_Geometry in an iterative fashion |
    | `ElementExtractor``(`[`J3D_Geometry`](J3D_Geometry.md)` geom, int elemStart, int type)`                                                                              |
    | `ElementExtractor``(`[`J3D_Geometry`](J3D_Geometry.md)` geom, int elemStart, int type, boolean allow_comp_sub_elements_param)`                                       |
    | `ElementExtractor``(`[`J3D_Geometry`](J3D_Geometry.md)` geom, int elemStart, int type, int mydim)`                                                                   |
    | `ElementExtractor``(`[`J3D_Geometry`](J3D_Geometry.md)` geom, int elemStart, int type, int mydim, boolean allow_comp_sub_elements_param)`                            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                 | Method and Description                                                          |
    |-----------------------------------|---------------------------------------------------------------------------------|
    | [`J3D_Geometry`](J3D_Geometry.md) | `nextElement``(int[] inner_outer)`<br>Returns the next element of J3D_Geometry. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### MULTICOMP_TOSIMPLE

          public static final int MULTICOMP_TOSIMPLE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### INNER_OUTER

          public static final int INNER_OUTER

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LOWER_LEVEL

          public static final int LOWER_LEVEL

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_POINT

          public static final int GTYPE_POINT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_CURVE

          public static final int GTYPE_CURVE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_SURFACE

          public static final int GTYPE_SURFACE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_POLYGON

          public static final int GTYPE_POLYGON

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_COLLECTION

          public static final int GTYPE_COLLECTION

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_SOLID

          public static final int GTYPE_SOLID

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_MULTIPOINT

          public static final int GTYPE_MULTIPOINT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_MULTICURVE

          public static final int GTYPE_MULTICURVE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_MULTISURFACE

          public static final int GTYPE_MULTISURFACE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_MULTIPOLYGON

          public static final int GTYPE_MULTIPOLYGON

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GTYPE_MULTISOLID

          public static final int GTYPE_MULTISOLID

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_UNKNOWN

          public static final int ETYPE_UNKNOWN

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_POINT

          public static final int ETYPE_POINT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_CURVE

          public static final int ETYPE_CURVE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_RING

          public static final int ETYPE_RING

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_POLYGON

          public static final int ETYPE_POLYGON

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_SURFACE

          public static final int ETYPE_SURFACE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_SOLID

          public static final int ETYPE_SOLID

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_COMPOUNDCURVE

          public static final int ETYPE_COMPOUNDCURVE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_COMPOUNDRING

          public static final int ETYPE_COMPOUNDRING

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_COMPOSITEPOLYGON

          public static final int ETYPE_COMPOSITEPOLYGON

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_COMPOSITESURFACE

          public static final int ETYPE_COMPOSITESURFACE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ETYPE_COMPOSITESOLID

          public static final int ETYPE_COMPOSITESOLID

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### ElementExtractor

          public ElementExtractor(J3D_Geometry geom,
                                  int elemStart,
                                  int type,
                                  boolean allow_comp_sub_elements_param)
                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### ElementExtractor

          public ElementExtractor(J3D_Geometry geom,
                                  int elemStart,
                                  int type)
                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### ElementExtractor

          public ElementExtractor(J3D_Geometry geom,
                                  int type)
                           throws java.lang.Exception

      Constructs an extractor that extracts elements from J3D_Geometry in an iterative fashion
      Parameters:
      `geom` - Geometry

      `type` - MULTICOMP_TOSIMPLE (0), or INNER_OUTER (1) or LOWER_LEVEL (2) This is the constructor function's extraction_level parameter which can have the following values: LOWER_LEVEL (2): This returns the elements in the next level of hierarchy (e.g., for a solid, the next Level will be surfaces, for a polygon the next level will be lines etc.); MULTICOMP_TOSIMPLE (0): This returns the elements of a composite or multi-geometry. For instance, for a composite surface, it returns each surface element as a J3D_GEOMETRY in the "next" call; INNER_OUTER (1): This returns the inner/outer elements if any. For polygons, it returns the outer first which is followed by inner polygons in subsequent "next" calls.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### ElementExtractor

          public ElementExtractor(J3D_Geometry geom,
                                  int elemStart,
                                  int type,
                                  int mydim,
                                  boolean allow_comp_sub_elements_param)
                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### ElementExtractor

          public ElementExtractor(J3D_Geometry geom,
                                  int elemStart,
                                  int type,
                                  int mydim)
                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### ElementExtractor

          public ElementExtractor(J3D_Geometry geom)
                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

  <!-- -->

  - ### Method Detail

    - #### nextElement

          public J3D_Geometry nextElement(int[] inner_outer)
                                   throws java.lang.Exception

      Returns the next element of J3D_Geometry.
      This is the iterator to get next element using the above hierarchy. It takes an input J3D_Geometry and returns the next element in sequence.

      Parameters:
      `inner_outer` - This is a single element integer array. It tells whether the extracted next element geometry is a hole(2) or outer geometry(1).

      Returns:
      J3D_Geometry geometry which is the next element of input 3-D geometry

      Throws:
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

- [Prev Class](DataException.md)
- [Next Class](FastJGeometry.md)

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
