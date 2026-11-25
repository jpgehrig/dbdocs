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

- [Prev Class](ByteOrderBigEndian.md)
- [Next Class](ClipPcFlatCells.md)

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

## Class ByteOrderLittleEndian

- java.lang.Object

- - [oracle.spatial.util.ByteOrder](ByteOrder.md)

  - - oracle.spatial.util.ByteOrderLittleEndian

<!-- -->

-

  ------------------------------------------------------------------------



      public class ByteOrderLittleEndian
      extends ByteOrder

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.spatial.util.[ByteOrder](ByteOrder.md)

      [`BIG_ENDIAN`](ByteOrder.md)`, `[`LITTLE_ENDIAN`](ByteOrder.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                       |
    |-------------------|--------------------------------------------------------------|
    | `double`          | `readDouble``(java.io.DataInputStream in)`                   |
    | `int`             | `readUInt32``(java.io.DataInputStream in)`                   |
    | `void`            | `writeDouble``(java.io.DataOutputStream out, double value)`  |
    | `void`            | `writeUInt32``(java.io.DataOutputStream out, int value)`     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### writeDouble

          public void writeDouble(java.io.DataOutputStream out,
                                  double value)

      Specified by:
      [`writeDouble`](ByteOrder.md) in class [`ByteOrder`](ByteOrder.md)

    <!-- -->

    - #### readDouble

          public double readDouble(java.io.DataInputStream in)

      Specified by:
      [`readDouble`](ByteOrder.md) in class [`ByteOrder`](ByteOrder.md)

    <!-- -->

    - #### writeUInt32

          public void writeUInt32(java.io.DataOutputStream out,
                                  int value)

      Specified by:
      [`writeUInt32`](ByteOrder.md) in class [`ByteOrder`](ByteOrder.md)

    <!-- -->

    - #### readUInt32

          public int readUInt32(java.io.DataInputStream in)

      Specified by:
      [`readUInt32`](ByteOrder.md) in class [`ByteOrder`](ByteOrder.md)

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

- [Prev Class](ByteOrderBigEndian.md)
- [Next Class](ClipPcFlatCells.md)

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
