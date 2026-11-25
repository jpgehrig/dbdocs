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

- [Prev Class](NFEIdGenerator.md)
- [Next Class](NFEMetadata.md)

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

## Interface NFEIdManager

- All Known Implementing Classes:
  [NFEDBSequenceIdManager](NFEDBSequenceIdManager.md)

  ------------------------------------------------------------------------



      public interface NFEIdManager

  This interface acts as a holder and manager of different ID generators used for different entities related to an NFEModel. An implementation of this class will relate NFEIdGenerator instances to specific entities and will encapsulate calls to those NFEIdGenerator instances.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                 |
    |---------------------------|-----------------------------------------------------------------------|
    | `static java.lang.String` | `ENTITY_ATTRIBUTE_CONSTRAINT`<br>Represents an NFEAttributeConstraint |
    | `static java.lang.String` | `ENTITY_CARDINALITY_RULE`<br>Represents an NFECardinalityRule         |
    | `static java.lang.String` | `ENTITY_CATALOG`<br>Represents an NFECatalog                          |
    | `static java.lang.String` | `ENTITY_CATALOG_VALUE`<br>Represents an NFECatalogValue               |
    | `static java.lang.String` | `ENTITY_FEATURE_CLASS`<br>Represents an NFEFeatureClass               |
    | `static java.lang.String` | `ENTITY_LINE_LINE_RULE`<br>Represents an NFELineLineRule              |
    | `static java.lang.String` | `ENTITY_LINE_POINT_RULE`<br>Represents an NFELinePointRule            |
    | `static java.lang.String` | `ENTITY_LINK`<br>Represents an NFELink                                |
    | `static java.lang.String` | `ENTITY_NODE`<br>Represents an NFENode                                |
    | `static java.lang.String` | `ENTITY_PREDEF_CONN_POINT`<br>Represents an NFEDefaultConnectedPoint  |
    | `static java.lang.String` | `ENTITY_RULE_INSTANCE`<br>Represents an NFERuleInstance               |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

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

<!-- -->

- - ### Field Detail

    - #### ENTITY_NODE

          static final java.lang.String ENTITY_NODE

      Represents an NFENode
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### ENTITY_LINK

          static final java.lang.String ENTITY_LINK

      Represents an NFELink
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### ENTITY_FEATURE_CLASS

          static final java.lang.String ENTITY_FEATURE_CLASS

      Represents an NFEFeatureClass
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### ENTITY_CATALOG

          static final java.lang.String ENTITY_CATALOG

      Represents an NFECatalog
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### ENTITY_CATALOG_VALUE

          static final java.lang.String ENTITY_CATALOG_VALUE

      Represents an NFECatalogValue
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### ENTITY_ATTRIBUTE_CONSTRAINT

          static final java.lang.String ENTITY_ATTRIBUTE_CONSTRAINT

      Represents an NFEAttributeConstraint
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### ENTITY_PREDEF_CONN_POINT

          static final java.lang.String ENTITY_PREDEF_CONN_POINT

      Represents an NFEDefaultConnectedPoint
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### ENTITY_LINE_POINT_RULE

          static final java.lang.String ENTITY_LINE_POINT_RULE

      Represents an NFELinePointRule
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### ENTITY_LINE_LINE_RULE

          static final java.lang.String ENTITY_LINE_LINE_RULE

      Represents an NFELineLineRule
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### ENTITY_CARDINALITY_RULE

          static final java.lang.String ENTITY_CARDINALITY_RULE

      Represents an NFECardinalityRule
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### ENTITY_RULE_INSTANCE

          static final java.lang.String ENTITY_RULE_INSTANCE

      Represents an NFERuleInstance
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### setModel

          void setModel(NFEModel model)

      Sets the current NFEModel instance. This is typically set automatically when a new NFEModel instance is initialized.
      Parameters:
      `model` - an NFEModel instance

    <!-- -->

    - #### getModel

          NFEModel getModel()

      Gets the current NFEModel instance
      Returns:
      the assigned NFEModel instance

    <!-- -->

    - #### setIdGenerator

          void setIdGenerator(java.lang.String entityName,
                              NFEIdGenerator idGen)

      Associates an NFEIdGenerator instance to the given entity. The NFEIdGenerator instance will be used to create new ID's for the entity.
      Parameters:
      `entityName` - an entity name. See the field summary for supported entity names.

      `idGen` - an NFEIdGenerator instance

    <!-- -->

    - #### getIdGenerator

          NFEIdGenerator getIdGenerator(java.lang.String entityName)

      Gets the NFEIdGenerator currently used for generating ID's for the given entity
      Parameters:
      `entityName` - an entity name.

      Returns:
      an NFEIdGenerator instance or null if the entity is not related to any ID generator

    <!-- -->

    - #### getNextId

          long getNextId(java.lang.String entityName)

      Gets the next ID for the given entity name. It is equivalent to get the ID generator for the entity and call NFEIdGenerator.getNextId()
      Parameters:
      `entityName` - an entity name

      Returns:
      a valid ID if the entity is related to an ID generator

    <!-- -->

    - #### getNextNodeId

          long getNextNodeId()

      Gets the next node ID. This is a shorthand for getNextId( NFEIdManager.ENTITY_NODE )
      Returns:
      a node ID

    <!-- -->

    - #### getNextLinkId

          long getNextLinkId()

      Gets the next link ID. This is a shorthand for getNextId( NFEIdManager.ENTITY_LINK )
      Returns:
      a link ID

    <!-- -->

    - #### getNextFeatureId

          long getNextFeatureId(long featureLayerId)

      Gets the next feature ID for the Feature Layer identified by the given featureLayerId
      Parameters:
      `featureLayerId` - an existing Feature Layer ID

      Returns:
      a feature ID

    <!-- -->

    - #### getNextFeatureElementSequence

          long getNextFeatureElementSequence(long featureLayerId)

      Gets the next feature element sequence for the Feature Layer identified by the given featureLayerId. Note that the sequence is used as the ID of a feature element. A feature may contain feature element with no necessarily consecutive sequences.
      Parameters:
      `featureLayerId` - featureLayerId an existing Feature Layer ID

      Returns:
      a feature element sequence.

    <!-- -->

    - #### setIdBufferSize

          void setIdBufferSize(int size)

      Sets the ID buffer size used by all the ID generators managed
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

- [Prev Class](NFEIdGenerator.md)
- [Next Class](NFEMetadata.md)

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
