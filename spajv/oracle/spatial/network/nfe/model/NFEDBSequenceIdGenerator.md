Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEBasicModelObjectFactory.md)
- [Next Class](NFEDBSequenceIdManager.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model

## Class NFEDBSequenceIdGenerator

- java.lang.Object

- - oracle.spatial.network.nfe.model.NFEDBSequenceIdGenerator

<!-- -->

- All Implemented Interfaces:
  [NFEIdGenerator](NFEIdGenerator.md)

  ------------------------------------------------------------------------



      public class NFEDBSequenceIdGenerator
      extends java.lang.Object
      implements NFEIdGenerator

  An implementation of NFEIdGeneratiom that uses a database sequence to generate id's

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                            |
    |----------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEDBSequenceIdGenerator``(java.lang.String sequenceName, `[`NFEDataSource`](../io/NFEDataSource.md)` dataSource, int idBufferSize)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                               |
    |-------------------|------------------------------------------------------------------------------------------------------|
    | `int`             | `getIdBufferSize``()`<br>Returns the size of the ID buffer.                                          |
    | `long`            | `getNextId``()`<br>Gets the next ID                                                                  |
    | `void`            | `setIdBufferSize``(int idBufferSize)`<br>Sets the size of the ID buffer size used by this generator. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEDBSequenceIdGenerator

          public NFEDBSequenceIdGenerator(java.lang.String sequenceName,
                                          NFEDataSource dataSource,
                                          int idBufferSize)

  <!-- -->

  - ### Method Detail

    - #### getNextId

          public long getNextId()

      Description copied from interface: [`NFEIdGenerator`](NFEIdGenerator.md)
      Gets the next ID
      Specified by:
      [`getNextId`](NFEIdGenerator.md) in interface [`NFEIdGenerator`](NFEIdGenerator.md)

      Returns:
      a new ID

    <!-- -->

    - #### setIdBufferSize

          public void setIdBufferSize(int idBufferSize)

      Description copied from interface: [`NFEIdGenerator`](NFEIdGenerator.md)
      Sets the size of the ID buffer size used by this generator. There is not guaranteed that the implementation actually uses a buffer.
      Specified by:
      [`setIdBufferSize`](NFEIdGenerator.md) in interface [`NFEIdGenerator`](NFEIdGenerator.md)

      Parameters:
      `idBufferSize` - the number of IDs that can contain the buffer

    <!-- -->

    - #### getIdBufferSize

          public int getIdBufferSize()

      Description copied from interface: [`NFEIdGenerator`](NFEIdGenerator.md)
      Returns the size of the ID buffer. The size is the number of IDs that the buffer can hold or that are reserved.
      Specified by:
      [`getIdBufferSize`](NFEIdGenerator.md) in interface [`NFEIdGenerator`](NFEIdGenerator.md)

      Returns:
      the size of the ID buffer

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEBasicModelObjectFactory.md)
- [Next Class](NFEDBSequenceIdManager.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
