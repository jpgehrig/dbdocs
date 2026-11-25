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

- [Prev Class](WKBasis.md)
- [Next Class](WKT.md)

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

## Interface WKInputStream

-

  ------------------------------------------------------------------------



      public interface WKInputStream

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type           | Method and Description                                                  |
    |-----------------------------|-------------------------------------------------------------------------|
    | `int`                       | `getDimensions``()`                                                     |
    | `int`                       | `readByte``()`                                                          |
    | [`ByteOrder`](ByteOrder.md) | `readByteOrder``()`                                                     |
    | `double`                    | `readDouble``(`[`ByteOrder`](ByteOrder.md)` byteOrder)`                 |
    | `void`                      | `readEndList``()`                                                       |
    | `void`                      | `readEndListOrSeparator``()`                                            |
    | `int`                       | `readInnerLabel``()`                                                    |
    | `int`                       | `readLabel``(`[`ByteOrder`](ByteOrder.md)` byteOrder, int outerLabel)`  |
    | `void`                      | `readSeparator``()`                                                     |
    | `void`                      | `readStartList``()`                                                     |
    | `int`                       | `readStartList``(`[`ByteOrder`](ByteOrder.md)` byteOrder)`              |

<!-- -->

- - ### Method Detail

    - #### readDouble

          double readDouble(ByteOrder byteOrder)

    <!-- -->

    - #### readLabel

          int readLabel(ByteOrder byteOrder,
                        int outerLabel)

    <!-- -->

    - #### readInnerLabel

          int readInnerLabel()

    <!-- -->

    - #### readStartList

          void readStartList()

    <!-- -->

    - #### readStartList

          int readStartList(ByteOrder byteOrder)

    <!-- -->

    - #### readByte

          int readByte()
                throws GeometryExceptionWithContext

      Throws:
      [`GeometryExceptionWithContext`](GeometryExceptionWithContext.md)

    <!-- -->

    - #### readEndList

          void readEndList()

    <!-- -->

    - #### readEndListOrSeparator

          void readEndListOrSeparator()

    <!-- -->

    - #### readSeparator

          void readSeparator()

    <!-- -->

    - #### readByteOrder

          ByteOrder readByteOrder()
                           throws GeometryExceptionWithContext

      Throws:
      [`GeometryExceptionWithContext`](GeometryExceptionWithContext.md)

    <!-- -->

    - #### getDimensions

          int getDimensions()

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

- [Prev Class](WKBasis.md)
- [Next Class](WKT.md)

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
