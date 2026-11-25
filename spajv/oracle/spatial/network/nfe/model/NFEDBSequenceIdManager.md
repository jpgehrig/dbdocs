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

- [Prev Class](NFEDBSequenceIdGenerator.md)
- [Next Class](NFEEditionMode.md)

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

## Class NFEDBSequenceIdManager

- java.lang.Object

- - oracle.spatial.network.nfe.model.NFEDBSequenceIdManager

<!-- -->

- All Implemented Interfaces:
  [NFEIdManager](NFEIdManager.md)

  ------------------------------------------------------------------------



      public class NFEDBSequenceIdManager
      extends java.lang.Object
      implements NFEIdManager

  An implementation of NFEIdManager that uses instances of [`NFEDBSequenceIdGenerator`](NFEDBSequenceIdGenerator.md) to generate id's

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.[NFEIdManager](NFEIdManager.md)

      [`ENTITY_ATTRIBUTE_CONSTRAINT`](NFEIdManager.md)`, `[`ENTITY_CARDINALITY_RULE`](NFEIdManager.md)`, `[`ENTITY_CATALOG`](NFEIdManager.md)`, `[`ENTITY_CATALOG_VALUE`](NFEIdManager.md)`, `[`ENTITY_FEATURE_CLASS`](NFEIdManager.md)`, `[`ENTITY_LINE_LINE_RULE`](NFEIdManager.md)`, `[`ENTITY_LINE_POINT_RULE`](NFEIdManager.md)`, `[`ENTITY_LINK`](NFEIdManager.md)`, `[`ENTITY_NODE`](NFEIdManager.md)`, `[`ENTITY_PREDEF_CONN_POINT`](NFEIdManager.md)`, `[`ENTITY_RULE_INSTANCE`](NFEIdManager.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                         |
    |-------------------------------------------------------------------------------------|
    | `NFEDBSequenceIdManager``(`[`NFEDataSource`](../io/NFEDataSource.md)` dataSource)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                     | Method and Description                                                                                                                                         |
    |---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`NFEIdGenerator`](NFEIdGenerator.md) | `getIdGenerator``(java.lang.String entityName)`<br>Gets the NFEIdGenerator currently used for generating ID's for the given entity                             |
    | [`NFEModel`](NFEModel.md)             | `getModel``()`<br>Gets the current NFEModel instance                                                                                                           |
    | `long`                                | `getNextFeatureElementSequence``(long featureLayerId)`<br>Gets the next feature element sequence for the Feature Layer identified by the given featureLayerId. |
    | `long`                                | `getNextFeatureId``(long featureLayerId)`<br>Gets the next feature ID for the Feature Layer identified by the given featureLayerId                             |
    | `long`                                | `getNextId``(java.lang.String entityName)`<br>Gets the next ID for the given entity name.                                                                      |
    | `long`                                | `getNextLinkId``()`<br>Gets the next link ID.                                                                                                                  |
    | `long`                                | `getNextNodeId``()`<br>Gets the next node ID.                                                                                                                  |
    | `void`                                | `setIdBufferSize``(int size)`<br>Sets the ID buffer size used by all the ID generators managed                                                                 |
    | `void`                                | `setIdGenerator``(java.lang.String entityName, `[`NFEIdGenerator`](NFEIdGenerator.md)` idGen)`<br>Associates an NFEIdGenerator instance to the given entity.   |
    | `void`                                | `setModel``(`[`NFEModel`](NFEModel.md)` model)`<br>Sets the current NFEModel instance.                                                                         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEDBSequenceIdManager

          public NFEDBSequenceIdManager(NFEDataSource dataSource)

  <!-- -->

  - ### Method Detail

    - #### setModel

          public void setModel(NFEModel model)

      Description copied from interface: [`NFEIdManager`](NFEIdManager.md)
      Sets the current NFEModel instance. This is typically set automatically when a new NFEModel instance is initialized.
      Specified by:
      [`setModel`](NFEIdManager.md) in interface [`NFEIdManager`](NFEIdManager.md)

      Parameters:
      `model` - an NFEModel instance

    <!-- -->

    - #### getModel

          public NFEModel getModel()

      Description copied from interface: [`NFEIdManager`](NFEIdManager.md)
      Gets the current NFEModel instance
      Specified by:
      [`getModel`](NFEIdManager.md) in interface [`NFEIdManager`](NFEIdManager.md)

      Returns:
      the assigned NFEModel instance

    <!-- -->

    - #### setIdGenerator

          public void setIdGenerator(java.lang.String entityName,
                                     NFEIdGenerator idGen)

      Description copied from interface: [`NFEIdManager`](NFEIdManager.md)
      Associates an NFEIdGenerator instance to the given entity. The NFEIdGenerator instance will be used to create new ID's for the entity.
      Specified by:
      [`setIdGenerator`](NFEIdManager.md) in interface [`NFEIdManager`](NFEIdManager.md)

      Parameters:
      `entityName` - an entity name. See the field summary for supported entity names.

      `idGen` - an NFEIdGenerator instance

    <!-- -->

    - #### getIdGenerator

          public NFEIdGenerator getIdGenerator(java.lang.String entityName)

      Description copied from interface: [`NFEIdManager`](NFEIdManager.md)
      Gets the NFEIdGenerator currently used for generating ID's for the given entity
      Specified by:
      [`getIdGenerator`](NFEIdManager.md) in interface [`NFEIdManager`](NFEIdManager.md)

      Parameters:
      `entityName` - an entity name.

      Returns:
      an NFEIdGenerator instance or null if the entity is not related to any ID generator

    <!-- -->

    - #### getNextId

          public long getNextId(java.lang.String entityName)

      Description copied from interface: [`NFEIdManager`](NFEIdManager.md)
      Gets the next ID for the given entity name. It is equivalent to get the ID generator for the entity and call NFEIdGenerator.getNextId()
      Specified by:
      [`getNextId`](NFEIdManager.md) in interface [`NFEIdManager`](NFEIdManager.md)

      Parameters:
      `entityName` - an entity name

      Returns:
      a valid ID if the entity is related to an ID generator

    <!-- -->

    - #### getNextNodeId

          public long getNextNodeId()

      Description copied from interface: [`NFEIdManager`](NFEIdManager.md)
      Gets the next node ID. This is a shorthand for getNextId( NFEIdManager.ENTITY_NODE )
      Specified by:
      [`getNextNodeId`](NFEIdManager.md) in interface [`NFEIdManager`](NFEIdManager.md)

      Returns:
      a node ID

    <!-- -->

    - #### getNextLinkId

          public long getNextLinkId()

      Description copied from interface: [`NFEIdManager`](NFEIdManager.md)
      Gets the next link ID. This is a shorthand for getNextId( NFEIdManager.ENTITY_LINK )
      Specified by:
      [`getNextLinkId`](NFEIdManager.md) in interface [`NFEIdManager`](NFEIdManager.md)

      Returns:
      a link ID

    <!-- -->

    - #### getNextFeatureId

          public long getNextFeatureId(long featureLayerId)

      Description copied from interface: [`NFEIdManager`](NFEIdManager.md)
      Gets the next feature ID for the Feature Layer identified by the given featureLayerId
      Specified by:
      [`getNextFeatureId`](NFEIdManager.md) in interface [`NFEIdManager`](NFEIdManager.md)

      Parameters:
      `featureLayerId` - an existing Feature Layer ID

      Returns:
      a feature ID

    <!-- -->

    - #### getNextFeatureElementSequence

          public long getNextFeatureElementSequence(long featureLayerId)

      Description copied from interface: [`NFEIdManager`](NFEIdManager.md)
      Gets the next feature element sequence for the Feature Layer identified by the given featureLayerId. Note that the sequence is used as the ID of a feature element. A feature may contain feature element with no necessarily consecutive sequences.
      Specified by:
      [`getNextFeatureElementSequence`](NFEIdManager.md) in interface [`NFEIdManager`](NFEIdManager.md)

      Parameters:
      `featureLayerId` - featureLayerId an existing Feature Layer ID

      Returns:
      a feature element sequence.

    <!-- -->

    - #### setIdBufferSize

          public void setIdBufferSize(int size)

      Description copied from interface: [`NFEIdManager`](NFEIdManager.md)
      Sets the ID buffer size used by all the ID generators managed
      Specified by:
      [`setIdBufferSize`](NFEIdManager.md) in interface [`NFEIdManager`](NFEIdManager.md)

      Parameters:
      `size` - the size of the buffer

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

- [Prev Class](NFEDBSequenceIdGenerator.md)
- [Next Class](NFEEditionMode.md)

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
