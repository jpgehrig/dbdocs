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

- [Prev Class](ParallelPairwiseShortestPaths.md)
- [Next Class](PartitionBlobTranslator.md)

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

## Class PartitionBlob

- java.lang.Object

- - oracle.spatial.network.lod.PartitionBlob

<!-- -->

-

  ------------------------------------------------------------------------



      public class PartitionBlob
      extends java.lang.Object

  An instance of the PartitionBlob represents a row in the partition BLOB table in the database.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                           |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `PartitionBlob``(int partitionId, java.sql.Blob blob, int numberOfInternalNodes, int numberOfExternalNodes, int numberOfInternalLinks, int numberOfBoundaryLinks, int numberOfIncomingLinks, int numberOfOutgoingLinks, boolean isUserDataIncluded)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                   |
    |-------------------|----------------------------------------------------------|
    | `java.sql.Blob`   | `getBlob``()`                                            |
    | `int`             | `getNumberOfBoundaryLinks``()`                           |
    | `int`             | `getNumberOfExternalNodes``()`                           |
    | `int`             | `getNumberOfIncomingLinks``()`                           |
    | `int`             | `getNumberOfInternalLinks``()`                           |
    | `int`             | `getNumberOfInternalNodes``()`                           |
    | `int`             | `getNumberOfOutgoingLinks``()`                           |
    | `int`             | `getPartitionId``()`                                     |
    | `boolean`         | `isIsUserDataIncluded``()`                               |
    | `void`            | `setBlob``(java.sql.Blob blob)`                          |
    | `void`            | `setIsUserDataIncluded``(boolean isUserDataIncluded)`    |
    | `void`            | `setNumberOfBoundaryLinks``(int numberOfBoundaryLinks)`  |
    | `void`            | `setNumberOfExternalNodes``(int numberOfExternalNodes)`  |
    | `void`            | `setNumberOfIncomingLinks``(int numberOfIncomingLinks)`  |
    | `void`            | `setNumberOfInternalLinks``(int numberOfInternalLinks)`  |
    | `void`            | `setNumberOfInternalNodes``(int numberOfInternalNodes)`  |
    | `void`            | `setNumberOfOutgoingLinks``(int numberOfOutgoingLinks)`  |
    | `void`            | `setPartitionId``(int partitionId)`                      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### PartitionBlob

          public PartitionBlob(int partitionId,
                               java.sql.Blob blob,
                               int numberOfInternalNodes,
                               int numberOfExternalNodes,
                               int numberOfInternalLinks,
                               int numberOfBoundaryLinks,
                               int numberOfIncomingLinks,
                               int numberOfOutgoingLinks,
                               boolean isUserDataIncluded)

  <!-- -->

  - ### Method Detail

    - #### setPartitionId

          public void setPartitionId(int partitionId)

    <!-- -->

    - #### getPartitionId

          public int getPartitionId()

    <!-- -->

    - #### setBlob

          public void setBlob(java.sql.Blob blob)

    <!-- -->

    - #### getBlob

          public java.sql.Blob getBlob()

    <!-- -->

    - #### setNumberOfInternalNodes

          public void setNumberOfInternalNodes(int numberOfInternalNodes)

    <!-- -->

    - #### getNumberOfInternalNodes

          public int getNumberOfInternalNodes()

    <!-- -->

    - #### setNumberOfExternalNodes

          public void setNumberOfExternalNodes(int numberOfExternalNodes)

    <!-- -->

    - #### getNumberOfExternalNodes

          public int getNumberOfExternalNodes()

    <!-- -->

    - #### setNumberOfInternalLinks

          public void setNumberOfInternalLinks(int numberOfInternalLinks)

    <!-- -->

    - #### getNumberOfInternalLinks

          public int getNumberOfInternalLinks()

    <!-- -->

    - #### setNumberOfBoundaryLinks

          public void setNumberOfBoundaryLinks(int numberOfBoundaryLinks)

    <!-- -->

    - #### getNumberOfBoundaryLinks

          public int getNumberOfBoundaryLinks()

    <!-- -->

    - #### setNumberOfIncomingLinks

          public void setNumberOfIncomingLinks(int numberOfIncomingLinks)

    <!-- -->

    - #### getNumberOfIncomingLinks

          public int getNumberOfIncomingLinks()

    <!-- -->

    - #### setNumberOfOutgoingLinks

          public void setNumberOfOutgoingLinks(int numberOfOutgoingLinks)

    <!-- -->

    - #### getNumberOfOutgoingLinks

          public int getNumberOfOutgoingLinks()

    <!-- -->

    - #### setIsUserDataIncluded

          public void setIsUserDataIncluded(boolean isUserDataIncluded)

    <!-- -->

    - #### isIsUserDataIncluded

          public boolean isIsUserDataIncluded()

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

- [Prev Class](ParallelPairwiseShortestPaths.md)
- [Next Class](PartitionBlobTranslator.md)

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
