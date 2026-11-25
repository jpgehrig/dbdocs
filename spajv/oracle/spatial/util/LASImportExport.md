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

- [Prev Class](Las2SqlLdrIndep.md)
- [Next Class](Logger.md)

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

## Class LASImportExport

- java.lang.Object

- - oracle.spatial.util.LASImportExport

<!-- -->

-

  ------------------------------------------------------------------------



      public class LASImportExport
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `LASImportExport``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                        |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`     | `exportLAS``(java.lang.String sourceTable, java.lang.String targetLasFile)`                                                                                   |
    | `static void`     | `importLAS``(java.lang.String sourceLasFile, java.lang.String sourceLasFileId, java.lang.String targetTable, java.sql.Connection conn)`                       |
    | `static void`     | `importLAS``(java.lang.String sourceLasDir, java.lang.String sourceLasFile, java.lang.String sourceLasFileId, java.lang.String targetTable, int addColumns)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LASImportExport

          public LASImportExport()

  <!-- -->

  - ### Method Detail

    - #### importLAS

          public static void importLAS(java.lang.String sourceLasDir,
                                       java.lang.String sourceLasFile,
                                       java.lang.String sourceLasFileId,
                                       java.lang.String targetTable,
                                       int addColumns)
                                throws java.sql.SQLException,
                                       java.io.IOException

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### importLAS

          public static void importLAS(java.lang.String sourceLasFile,
                                       java.lang.String sourceLasFileId,
                                       java.lang.String targetTable,
                                       java.sql.Connection conn)
                                throws java.sql.SQLException,
                                       java.io.IOException

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### exportLAS

          public static void exportLAS(java.lang.String sourceTable,
                                       java.lang.String targetLasFile)
                                throws java.sql.SQLException,
                                       java.io.IOException

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

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

- [Prev Class](Las2SqlLdrIndep.md)
- [Next Class](Logger.md)

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
