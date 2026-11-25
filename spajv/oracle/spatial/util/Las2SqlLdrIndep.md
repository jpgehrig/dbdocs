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

- [Prev Class](Las2SqlLdr.PointData.SinglePoint.md)
- [Next Class](LASImportExport.md)

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

## Class Las2SqlLdrIndep

- java.lang.Object

- - oracle.spatial.util.Las2SqlLdrIndep

<!-- -->

-

  ------------------------------------------------------------------------



      public class Las2SqlLdrIndep
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `Las2SqlLdrIndep``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                     |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`     | `loadLasIntoBlockTable``(int objId, java.lang.String blockTable, java.lang.String blkIdSequence, java.lang.String lasFile, int blockSize, int numPtsInMem, java.sql.Connection conn, int commitInterval)`  |
    | `static void`     | `loadLasIntoBlockTable``(int objId, java.lang.String blockTable, java.lang.String blkIdSequence, java.lang.String lasFile, int blockSize, int numPtsInMem, int commitInterval)`                            |
    | `static void`     | `main``(java.lang.String[] args)`                                                                                                                                                                          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Las2SqlLdrIndep

          public Las2SqlLdrIndep()

  <!-- -->

  - ### Method Detail

    - #### main

          public static void main(java.lang.String[] args)
                           throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### loadLasIntoBlockTable

          public static void loadLasIntoBlockTable(int objId,
                                                   java.lang.String blockTable,
                                                   java.lang.String blkIdSequence,
                                                   java.lang.String lasFile,
                                                   int blockSize,
                                                   int numPtsInMem,
                                                   java.sql.Connection conn,
                                                   int commitInterval)

    <!-- -->

    - #### loadLasIntoBlockTable

          public static void loadLasIntoBlockTable(int objId,
                                                   java.lang.String blockTable,
                                                   java.lang.String blkIdSequence,
                                                   java.lang.String lasFile,
                                                   int blockSize,
                                                   int numPtsInMem,
                                                   int commitInterval)

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

- [Prev Class](Las2SqlLdr.PointData.SinglePoint.md)
- [Next Class](LASImportExport.md)

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
