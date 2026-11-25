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

- [Prev Class](NFEModelMetadata.md)
- [Next Class](NFEModelObjectFactory.md)

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

## Interface NFEModelObject

- All Known Implementing Classes:
  [NFEBasicFeature](feature/NFEBasicFeature.md), [NFEBasicFeatureElement](feature/NFEBasicFeatureElement.md), [NFEBasicLink](network/NFEBasicLink.md), [NFEBasicModelObject](NFEBasicModelObject.md), [NFEBasicNode](network/NFEBasicNode.md), [NFEFeature](feature/NFEFeature.md), [NFEFeatureElement](feature/NFEFeatureElement.md), [NFELink](network/NFELink.md), [NFENetworkElement](network/NFENetworkElement.md), [NFENode](network/NFENode.md), [NFERuleInstance](rule/NFERuleInstance.md), [NFERuleInstanceRelation](rule/NFERuleInstanceRelation.md)

  ------------------------------------------------------------------------



      public interface NFEModelObject

  Base interface for any object contained directly or indirectly in an NFE Model

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                    |
    |-------------------|------------------------------------------------------------------------------------------|
    | `static byte`     | `EFLAG_EXISTING`<br>If this flag is on, it means the object was loaded from the database |
    | `static byte`     | `EFLAG_REMOVED`<br>If this flag is on, it means the object was removed from the model    |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                             |
    |-------------------|--------------------------------------------------------------------|
    | `void`            | `addEditionFlag``(byte flag)`<br>Turns on a single flag            |
    | `boolean`         | `containsEditionFlag``(byte flag)`<br>Tells whether the flag is on |
    | `byte`            | `getEditionFlags``()`<br>Gets all the active flags                 |
    | `void`            | `removeEditionFlag``(byte flag)`<br>Sets the given flags off       |
    | `void`            | `setEditionFlags``(byte flags)`<br>Sets the given flags on         |

<!-- -->

- - ### Field Detail

    - #### EFLAG_EXISTING

          static final byte EFLAG_EXISTING

      If this flag is on, it means the object was loaded from the database
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### EFLAG_REMOVED

          static final byte EFLAG_REMOVED

      If this flag is on, it means the object was removed from the model
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### setEditionFlags

          void setEditionFlags(byte flags)

      Sets the given flags on
      Parameters:
      `flags` - a mask with the flags to turn on

    <!-- -->

    - #### getEditionFlags

          byte getEditionFlags()

      Gets all the active flags
      Returns:
      a byte with the active flags on

    <!-- -->

    - #### addEditionFlag

          void addEditionFlag(byte flag)

      Turns on a single flag
      Parameters:
      `flag` - a flag

    <!-- -->

    - #### removeEditionFlag

          void removeEditionFlag(byte flag)

      Sets the given flags off
      Parameters:
      `flag` - a bit mask

    <!-- -->

    - #### containsEditionFlag

          boolean containsEditionFlag(byte flag)

      Tells whether the flag is on
      Parameters:
      `flag` - a bit mask

      Returns:
      true if the flag(s) is on

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

- [Prev Class](NFEModelMetadata.md)
- [Next Class](NFEModelObjectFactory.md)

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
