Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LRUCachingHandler.md)
- [Next Class](MaxCostConstraint.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.network.lod

## Class Matrix\<E\>

- java.lang.Object

- - oracle.spatial.network.lod.Matrix\<E\>

<!-- -->

-

  ------------------------------------------------------------------------



      public class Matrix<E>
      extends java.lang.Object

  A simple double array matrix implementation.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------|
    | `Matrix``(int rows, int cols, java.lang.Class<E> clazz)`<br>Constructs an empty matrix with the specified dimensions. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                 |
    |-------------------|----------------------------------------------------------------------------------------|
    | `E`               | `get``(int row, int col)`<br>Returns the element at the specified row and column.      |
    | `E[]`             | `getColumn``(int col)`                                                                 |
    | `int`             | `getColumnDimension``()`<br>Returns the column dimension.                              |
    | `E[]`             | `getRow``(int row)`                                                                    |
    | `int`             | `getRowDimension``()`<br>Returns the row dimension.                                    |
    | `void`            | `set``(int row, int col, E elem)`<br>Sets the element at the specified row and column. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Matrix

          public Matrix(int rows,
                        int cols,
                        java.lang.Class<E> clazz)

      Constructs an empty matrix with the specified dimensions.
      Parameters:
      `rows` - row dimension

      `cols` - column dimension

  <!-- -->

  - ### Method Detail

    - #### getColumnDimension

          public int getColumnDimension()

      Returns the column dimension.
      Returns:

    <!-- -->

    - #### getRowDimension

          public int getRowDimension()

      Returns the row dimension.
      Returns:

    <!-- -->

    - #### get

          public E get(int row,
                       int col)

      Returns the element at the specified row and column.
      Parameters:

      `row` - row of the element

      `col` - column of the element

      Returns:

    <!-- -->

    - #### set

          public void set(int row,
                          int col,
                          E elem)

      Sets the element at the specified row and column.
      Parameters:
      `row` - row of the element

      `col` - column of the element

      `elem` - element

    <!-- -->

    - #### getRow

          public E[] getRow(int row)

    <!-- -->

    - #### getColumn

          public E[] getColumn(int col)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LRUCachingHandler.md)
- [Next Class](MaxCostConstraint.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
