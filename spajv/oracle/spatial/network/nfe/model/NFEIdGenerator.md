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

- [Prev Class](NFEGeometryDescriptor.md)
- [Next Class](NFEIdManager.md)

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

## Interface NFEIdGenerator

- All Known Implementing Classes:
  [NFEDBSequenceIdGenerator](NFEDBSequenceIdGenerator.md)

  ------------------------------------------------------------------------



      public interface NFEIdGenerator

  Implementations of this interface must provide ID's for a given entity. For example, an instance of NFEIdGenerator my be used to retrieve new IDs for NFEFeatureClass instances. This interfaces hides the complexities of how new IDs are generated. It does not matter if a database sequence is used or if the ID is based on a counter in memory.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                       |
    |-------------------|----------------------------------------------------------------------------------------------|
    | `int`             | `getIdBufferSize``()`<br>Returns the size of the ID buffer.                                  |
    | `long`            | `getNextId``()`<br>Gets the next ID                                                          |
    | `void`            | `setIdBufferSize``(int size)`<br>Sets the size of the ID buffer size used by this generator. |

<!-- -->

- - ### Method Detail

    - #### getNextId

          long getNextId()

      Gets the next ID
      Returns:
      a new ID

    <!-- -->

    - #### setIdBufferSize

          void setIdBufferSize(int size)

      Sets the size of the ID buffer size used by this generator. There is not guaranteed that the implementation actually uses a buffer.
      Parameters:
      `size` - the number of IDs that can contain the buffer

    <!-- -->

    - #### getIdBufferSize

          int getIdBufferSize()

      Returns the size of the ID buffer. The size is the number of IDs that the buffer can hold or that are reserved.
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

- [Prev Class](NFEGeometryDescriptor.md)
- [Next Class](NFEIdManager.md)

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
