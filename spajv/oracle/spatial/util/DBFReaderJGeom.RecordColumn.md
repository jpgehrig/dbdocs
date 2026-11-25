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

- [Prev Class](DBFReaderJGeom.NumericColumn.md)
- [Next Class](DBMS.md)

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

## Class DBFReaderJGeom.RecordColumn

- java.lang.Object

- - oracle.spatial.util.DBFReaderJGeom.RecordColumn

<!-- -->

- Direct Known Subclasses:
  [DBFReaderJGeom.CharacterColumn](DBFReaderJGeom.CharacterColumn.md), [DBFReaderJGeom.DateColumn](DBFReaderJGeom.DateColumn.md), [DBFReaderJGeom.LogicalColumn](DBFReaderJGeom.LogicalColumn.md), [DBFReaderJGeom.NumericColumn](DBFReaderJGeom.NumericColumn.md)

  <!-- -->

  Enclosing class:
  [DBFReaderJGeom](DBFReaderJGeom.md)

  ------------------------------------------------------------------------



      public abstract static class DBFReaderJGeom.RecordColumn
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description    |
    |--------------------------------|
    | `RecordColumn``(byte[] name)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description  |
    |-------------------|-------------------------|
    | `void`            | `addValue``(byte[] v)`  |
    | `int`             | `getDecimalDigits``()`  |
    | `int`             | `getLength``()`         |
    | `byte[]`          | `getName``()`           |
    | `int`             | `getNumValues``()`      |
    | `byte`            | `getType``()`           |
    | `byte[]`          | `getValue``(int num)`   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### RecordColumn

          public RecordColumn(byte[] name)

  <!-- -->

  - ### Method Detail

    - #### addValue

          public void addValue(byte[] v)

    <!-- -->

    - #### getValue

          public byte[] getValue(int num)

    <!-- -->

    - #### getName

          public byte[] getName()

    <!-- -->

    - #### getNumValues

          public int getNumValues()

    <!-- -->

    - #### getType

          public byte getType()

    <!-- -->

    - #### getLength

          public int getLength()

    <!-- -->

    - #### getDecimalDigits

          public int getDecimalDigits()

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

- [Prev Class](DBFReaderJGeom.NumericColumn.md)
- [Next Class](DBMS.md)

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
