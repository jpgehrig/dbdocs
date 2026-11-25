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

- [Prev Class](JDBCExtensionInterface.md)
- [Next Class](KML.md)

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

## Class JDBCUtil

- java.lang.Object

- - oracle.spatial.util.JDBCUtil

<!-- -->

-

  ------------------------------------------------------------------------



      public class JDBCUtil
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `JDBCUtil``()`              |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                           |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static STRUCT`   | `getOracleSTRUCT``(java.lang.Object o)`<br>Returns oracle.sql.STRUCT while running within WLS or any J2EE container such as OC4J, JBoss etc.                     |
    | `static STRUCT`   | `getOracleSTRUCT``(java.sql.ResultSet rs, int columnIndex)`<br>Returns oracle.sql.STRUCT while running within WLS or any J2EE container such as OC4J, JBoss etc. |
    | `static ARRAY`    | `safeCastARRAY``(java.lang.Object o)`<br>Returns oracle.sql.ARRAY while running within WLS or any J2EE container such as OC4J, JBoss etc.                        |
    | `static ARRAY`    | `safeCastARRAY``(java.sql.ResultSet rs, int columnIndex)`<br>Returns oracle.sql.ARRAY while running within WLS or any J2EE container such as OC4J, JBoss etc.    |
    | `static BLOB`     | `safeCastBLOB``(java.sql.Blob blob)`<br>Returns oracle.sql.BLOB while running within WLS or any J2EE container such as OC4J, JBoss etc.                          |
    | `static BLOB`     | `safeCastBLOB``(java.sql.ResultSet rs, int columnIndex)`<br>Returns oracle.sql.BLOB while running within WLS or any J2EE container such as OC4J, JBoss etc.      |
    | `static CLOB`     | `safeCastCLOB``(java.sql.Clob clob)`<br>Returns oracle.sql.CLOB while running within WLS or any J2EE container such as OC4J, JBoss etc.                          |
    | `static CLOB`     | `safeCastCLOB``(java.sql.ResultSet rs, int columnIndex)`<br>Returns oracle.sql.CLOB while running within WLS or any J2EE container such as OC4J, JBoss etc.      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### JDBCUtil

          public JDBCUtil()

  <!-- -->

  - ### Method Detail

    - #### getOracleSTRUCT

          public static STRUCT getOracleSTRUCT(java.sql.ResultSet rs,
                                               int columnIndex)
                                        throws java.lang.Exception

      Returns oracle.sql.STRUCT while running within WLS or any J2EE container such as OC4J, JBoss etc.
      Parameters:
      `rs` - ResultSet

      `columnIndex` - Index of the column

      Returns:
      STRUCT

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getOracleSTRUCT

          public static STRUCT getOracleSTRUCT(java.lang.Object o)
                                        throws java.lang.Exception

      Returns oracle.sql.STRUCT while running within WLS or any J2EE container such as OC4J, JBoss etc.
      Parameters:
      `o` - object in a result set

      Returns:
      STRUCT

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### safeCastCLOB

          public static CLOB safeCastCLOB(java.sql.ResultSet rs,
                                          int columnIndex)
                                   throws java.lang.Exception

      Returns oracle.sql.CLOB while running within WLS or any J2EE container such as OC4J, JBoss etc.
      Parameters:
      `rs` -

      `columnIndex` -

      Returns:
      CLOB

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### safeCastCLOB

          public static CLOB safeCastCLOB(java.sql.Clob clob)
                                   throws java.lang.Exception

      Returns oracle.sql.CLOB while running within WLS or any J2EE container such as OC4J, JBoss etc.
      Parameters:
      `clob` - clob in a result set

      Returns:
      CLOB

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### safeCastBLOB

          public static BLOB safeCastBLOB(java.sql.ResultSet rs,
                                          int columnIndex)
                                   throws java.lang.Exception

      Returns oracle.sql.BLOB while running within WLS or any J2EE container such as OC4J, JBoss etc.
      Parameters:
      `rs` -

      `columnIndex` -

      Returns:
      BLOB

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### safeCastBLOB

          public static BLOB safeCastBLOB(java.sql.Blob blob)
                                   throws java.lang.Exception

      Returns oracle.sql.BLOB while running within WLS or any J2EE container such as OC4J, JBoss etc.
      Parameters:
      `blob` - blob in a result set

      Returns:
      BLOB

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### safeCastARRAY

          public static ARRAY safeCastARRAY(java.sql.ResultSet rs,
                                            int columnIndex)
                                     throws java.lang.Exception

      Returns oracle.sql.ARRAY while running within WLS or any J2EE container such as OC4J, JBoss etc.
      Parameters:
      `rs` -

      `columnIndex` -

      Returns:
      ARRAY

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### safeCastARRAY

          public static ARRAY safeCastARRAY(java.lang.Object o)
                                     throws java.lang.Exception

      Returns oracle.sql.ARRAY while running within WLS or any J2EE container such as OC4J, JBoss etc.
      Parameters:
      `o` - oracle.sql.ARRAY object in a result set

      Returns:
      ARRAY

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

- [Prev Class](JDBCExtensionInterface.md)
- [Next Class](KML.md)

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
