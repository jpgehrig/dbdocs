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

- [Prev Class](SdoPointInPolygon.md)
- [Next Class](ShapefileFeatureJGeom.md)

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

## Class SegY2SqlLdr

- java.lang.Object

- - oracle.spatial.util.SegY2SqlLdr

<!-- -->

-

  ------------------------------------------------------------------------



      public class SegY2SqlLdr
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `SegY2SqlLdr``()`           |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                  |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`     | `main``(java.lang.String[] args)`                                                                                                                                                       |
    | `static void`     | `readFile``(java.io.DataInputStream dis, java.io.BufferedOutputStream csvOutSamples, java.io.BufferedOutputStream csvOutTraces, java.io.PrintStream txtOutInfo, long maxNumTraces)`     |
    | `static void`     | `readFile``(java.lang.String sourceLasFile, java.io.BufferedOutputStream csvOutSamples, java.io.BufferedOutputStream csvOutTraces, java.io.PrintStream txtOutInfo, long maxNumTraces)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SegY2SqlLdr

          public SegY2SqlLdr()

  <!-- -->

  - ### Method Detail

    - #### readFile

          public static void readFile(java.io.DataInputStream dis,
                                      java.io.BufferedOutputStream csvOutSamples,
                                      java.io.BufferedOutputStream csvOutTraces,
                                      java.io.PrintStream txtOutInfo,
                                      long maxNumTraces)
                               throws java.io.IOException

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### readFile

          public static void readFile(java.lang.String sourceLasFile,
                                      java.io.BufferedOutputStream csvOutSamples,
                                      java.io.BufferedOutputStream csvOutTraces,
                                      java.io.PrintStream txtOutInfo,
                                      long maxNumTraces)

    <!-- -->

    - #### main

          public static void main(java.lang.String[] args)
                           throws java.io.FileNotFoundException

      Throws:
      `java.io.FileNotFoundException`

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

- [Prev Class](SdoPointInPolygon.md)
- [Next Class](ShapefileFeatureJGeom.md)

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
