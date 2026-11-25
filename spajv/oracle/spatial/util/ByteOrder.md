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

- [Prev Class](AdapterShapefileJGeom.md)
- [Next Class](ByteOrderBigEndian.md)

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

## Class ByteOrder

- java.lang.Object

- - oracle.spatial.util.ByteOrder

<!-- -->

- Direct Known Subclasses:
  [ByteOrderBigEndian](ByteOrderBigEndian.md), [ByteOrderLittleEndian](ByteOrderLittleEndian.md)

  ------------------------------------------------------------------------



      public abstract class ByteOrder
      extends java.lang.Object

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type  | Field and Description |
    |--------------------|-----------------------|
    | `static ByteOrder` | `BIG_ENDIAN`          |
    | `static ByteOrder` | `LITTLE_ENDIAN`       |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `ByteOrder``()`             |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                       |
    |-------------------|--------------------------------------------------------------|
    | `abstract double` | `readDouble``(java.io.DataInputStream in)`                   |
    | `abstract int`    | `readUInt32``(java.io.DataInputStream in)`                   |
    | `abstract void`   | `writeDouble``(java.io.DataOutputStream out, double value)`  |
    | `abstract void`   | `writeUInt32``(java.io.DataOutputStream out, int value)`     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### BIG_ENDIAN

          public static final ByteOrder BIG_ENDIAN

    <!-- -->

    - #### LITTLE_ENDIAN

          public static final ByteOrder LITTLE_ENDIAN

  <!-- -->

  - ### Constructor Detail

    - #### ByteOrder

          public ByteOrder()

  <!-- -->

  - ### Method Detail

    - #### writeDouble

          public abstract void writeDouble(java.io.DataOutputStream out,
                                           double value)

    <!-- -->

    - #### readDouble

          public abstract double readDouble(java.io.DataInputStream in)

    <!-- -->

    - #### writeUInt32

          public abstract void writeUInt32(java.io.DataOutputStream out,
                                           int value)

    <!-- -->

    - #### readUInt32

          public abstract int readUInt32(java.io.DataInputStream in)

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

- [Prev Class](AdapterShapefileJGeom.md)
- [Next Class](ByteOrderBigEndian.md)

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
