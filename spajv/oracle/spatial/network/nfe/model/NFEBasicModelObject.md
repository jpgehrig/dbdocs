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

- [Prev Class](NFEBasicModel.md)
- [Next Class](NFEBasicModelObjectFactory.md)

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

## Class NFEBasicModelObject

- java.lang.Object

- - oracle.spatial.network.nfe.model.NFEBasicModelObject

<!-- -->

- All Implemented Interfaces:
  [NFEModelObject](NFEModelObject.md)

  <!-- -->

  Direct Known Subclasses:
  [NFEFeature](feature/NFEFeature.md), [NFEFeatureElement](feature/NFEFeatureElement.md), [NFENetworkElement](network/NFENetworkElement.md), [NFERuleInstance](rule/NFERuleInstance.md), [NFERuleInstanceRelation](rule/NFERuleInstanceRelation.md)

  ------------------------------------------------------------------------



      public class NFEBasicModelObject
      extends java.lang.Object
      implements NFEModelObject

  The simplest implementation of NFEModelObject

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.[NFEModelObject](NFEModelObject.md)

      [`EFLAG_EXISTING`](NFEModelObject.md)`, `[`EFLAG_REMOVED`](NFEModelObject.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEBasicModelObject``()`   |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                             |
    |-------------------|--------------------------------------------------------------------|
    | `void`            | `addEditionFlag``(byte flag)`<br>Turns on a single flag            |
    | `boolean`         | `containsEditionFlag``(byte flag)`<br>Tells whether the flag is on |
    | `byte`            | `getEditionFlags``()`<br>Gets all the active flags                 |
    | `void`            | `removeEditionFlag``(byte flag)`<br>Sets the given flags off       |
    | `void`            | `setEditionFlags``(byte flags)`<br>Sets the given flags on         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicModelObject

          public NFEBasicModelObject()

  <!-- -->

  - ### Method Detail

    - #### setEditionFlags

          public void setEditionFlags(byte flags)

      Description copied from interface: [`NFEModelObject`](NFEModelObject.md)
      Sets the given flags on
      Specified by:
      [`setEditionFlags`](NFEModelObject.md) in interface [`NFEModelObject`](NFEModelObject.md)

      Parameters:
      `flags` - a mask with the flags to turn on

    <!-- -->

    - #### getEditionFlags

          public byte getEditionFlags()

      Description copied from interface: [`NFEModelObject`](NFEModelObject.md)
      Gets all the active flags
      Specified by:
      [`getEditionFlags`](NFEModelObject.md) in interface [`NFEModelObject`](NFEModelObject.md)

      Returns:
      a byte with the active flags on

    <!-- -->

    - #### addEditionFlag

          public void addEditionFlag(byte flag)

      Description copied from interface: [`NFEModelObject`](NFEModelObject.md)
      Turns on a single flag
      Specified by:
      [`addEditionFlag`](NFEModelObject.md) in interface [`NFEModelObject`](NFEModelObject.md)

      Parameters:
      `flag` - a flag

    <!-- -->

    - #### removeEditionFlag

          public void removeEditionFlag(byte flag)

      Description copied from interface: [`NFEModelObject`](NFEModelObject.md)
      Sets the given flags off
      Specified by:
      [`removeEditionFlag`](NFEModelObject.md) in interface [`NFEModelObject`](NFEModelObject.md)

      Parameters:
      `flag` - a bit mask

    <!-- -->

    - #### containsEditionFlag

          public boolean containsEditionFlag(byte flag)

      Description copied from interface: [`NFEModelObject`](NFEModelObject.md)
      Tells whether the flag is on
      Specified by:
      [`containsEditionFlag`](NFEModelObject.md) in interface [`NFEModelObject`](NFEModelObject.md)

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

- [Prev Class](NFEBasicModel.md)
- [Next Class](NFEBasicModelObjectFactory.md)

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
