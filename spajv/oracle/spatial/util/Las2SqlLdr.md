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

- [Prev Class](KML2.md)
- [Next Class](Las2SqlLdr.LasFileStream.md)

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

## Class Las2SqlLdr

- java.lang.Object

- - oracle.spatial.util.Las2SqlLdr

<!-- -->

-

  ------------------------------------------------------------------------



      public class Las2SqlLdr
      extends java.lang.Object

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                      |
    |-------------------|------------------------------------------------------------|
    | `static class `   | [`Las2SqlLdr.LasFileStream`](Las2SqlLdr.LasFileStream.md)  |
    | `static class `   | [`Las2SqlLdr.PointData`](Las2SqlLdr.PointData.md)          |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `Las2SqlLdr``()`            |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                               |
    |-------------------|------------------------------------------------------------------------------------------------------|
    | `static int`      | `getPyramidLevel``(long counter)`                                                                    |
    | `static long`     | `hilbert_xy2d``(long n, long x, long y)`                                                             |
    | `static void`     | `main``(java.lang.String[] args)`                                                                    |
    | `static long`     | `mortonEncode2D``(int x, int y)`                                                                     |
    | `static long`     | `mortonExpand``(int a)`                                                                              |
    | `static void`     | `readFile``(java.io.DataInputStream dis, int[] attributes, java.io.BufferedOutputStream csvOut)`     |
    | `static void`     | `readFile``(java.lang.String sourceLasFile, int[] attributes, java.io.BufferedOutputStream csvOut)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Las2SqlLdr

          public Las2SqlLdr()

  <!-- -->

  - ### Method Detail

    - #### hilbert_xy2d

          public static long hilbert_xy2d(long n,
                                          long x,
                                          long y)

    <!-- -->

    - #### mortonExpand

          public static long mortonExpand(int a)

    <!-- -->

    - #### mortonEncode2D

          public static long mortonEncode2D(int x,
                                            int y)

    <!-- -->

    - #### readFile

          public static void readFile(java.io.DataInputStream dis,
                                      int[] attributes,
                                      java.io.BufferedOutputStream csvOut)
                               throws java.io.IOException

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### getPyramidLevel

          public static int getPyramidLevel(long counter)

    <!-- -->

    - #### readFile

          public static void readFile(java.lang.String sourceLasFile,
                                      int[] attributes,
                                      java.io.BufferedOutputStream csvOut)

    <!-- -->

    - #### main

          public static void main(java.lang.String[] args)

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

- [Prev Class](KML2.md)
- [Next Class](Las2SqlLdr.LasFileStream.md)

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
