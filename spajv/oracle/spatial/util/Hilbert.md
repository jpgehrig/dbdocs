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

- [Prev Class](GroupingLOD1Generalization.md)
- [Next Class](JDBCAdapter.md)

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

## Class Hilbert

- java.lang.Object

- - oracle.spatial.util.Hilbert

<!-- -->

-

  ------------------------------------------------------------------------



      public class Hilbert
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `Hilbert``()`               |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                       |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`     | `addToBlocksFromInputTable``(long objId, java.lang.String inputTableName, java.lang.String blockTableName, int blockSize)`                                                   |
    | `static void`     | `confirmLhvColumn``(java.sql.Connection conn, java.lang.String blockTableName)`                                                                                              |
    | `static void`     | `generateBlocksFromInputTable``(long objId, long srid, java.lang.String inputTableName, java.lang.String blockTableName, int blockSize, double pcTol, int pcTotDimensions)`  |
    | `static long[]`   | `hilbert_d2xy``(long n, long d)`                                                                                                                                             |
    | `static long`     | `hilbert_xy2d``(long n, long x, long y)`                                                                                                                                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Hilbert

          public Hilbert()

  <!-- -->

  - ### Method Detail

    - #### hilbert_xy2d

          public static long hilbert_xy2d(long n,
                                          long x,
                                          long y)

    <!-- -->

    - #### hilbert_d2xy

          public static long[] hilbert_d2xy(long n,
                                            long d)

    <!-- -->

    - #### addToBlocksFromInputTable

          public static void addToBlocksFromInputTable(long objId,
                                                       java.lang.String inputTableName,
                                                       java.lang.String blockTableName,
                                                       int blockSize)
                                                throws java.io.IOException,
                                                       java.sql.SQLException

      Throws:
      `java.io.IOException`

      `java.sql.SQLException`

    <!-- -->

    - #### confirmLhvColumn

          public static void confirmLhvColumn(java.sql.Connection conn,
                                              java.lang.String blockTableName)
                                       throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### generateBlocksFromInputTable

          public static void generateBlocksFromInputTable(long objId,
                                                          long srid,
                                                          java.lang.String inputTableName,
                                                          java.lang.String blockTableName,
                                                          int blockSize,
                                                          double pcTol,
                                                          int pcTotDimensions)
                                                   throws java.io.IOException,
                                                          java.sql.SQLException

      Throws:
      `java.io.IOException`

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

- [Prev Class](GroupingLOD1Generalization.md)
- [Next Class](JDBCAdapter.md)

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
