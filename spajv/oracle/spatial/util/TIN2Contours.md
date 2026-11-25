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

- [Prev Class](StAXGML.md)
- [Next Class](Util.md)

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

## Class TIN2Contours

- java.lang.Object

- - oracle.spatial.util.TIN2Contours

<!-- -->

-

  ------------------------------------------------------------------------



      public class TIN2Contours
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `TIN2Contours``()`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                       |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`     | `generateContours``(STRUCT tin, java.lang.String tinBlockTableName, long tinObjId, double[] elevations, STRUCT region, java.lang.String contourTableName)`                                                   |
    | `static void`     | `generateContours``(STRUCT tin, java.lang.String tinBlockTableName, NUMBER tinObjId, NUMBER elevationMin, NUMBER elevationInterval, NUMBER elevationMax, STRUCT region, java.lang.String contourTableName)`  |
    | `static void`     | `generateContours``(STRUCT tin, java.lang.String tinBlockTableName, NUMBER tinObjId, SdoNumberArray elevations, STRUCT region, java.lang.String contourTableName)`                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TIN2Contours

          public TIN2Contours()

  <!-- -->

  - ### Method Detail

    - #### generateContours

          public static void generateContours(STRUCT tin,
                                              java.lang.String tinBlockTableName,
                                              long tinObjId,
                                              double[] elevations,
                                              STRUCT region,
                                              java.lang.String contourTableName)
                                       throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### generateContours

          public static void generateContours(STRUCT tin,
                                              java.lang.String tinBlockTableName,
                                              NUMBER tinObjId,
                                              SdoNumberArray elevations,
                                              STRUCT region,
                                              java.lang.String contourTableName)
                                       throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### generateContours

          public static void generateContours(STRUCT tin,
                                              java.lang.String tinBlockTableName,
                                              NUMBER tinObjId,
                                              NUMBER elevationMin,
                                              NUMBER elevationInterval,
                                              NUMBER elevationMax,
                                              STRUCT region,
                                              java.lang.String contourTableName)
                                       throws java.sql.SQLException

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

- [Prev Class](StAXGML.md)
- [Next Class](Util.md)

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
