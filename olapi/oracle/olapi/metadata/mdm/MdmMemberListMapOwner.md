Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](MdmMember.md)
- [Next Class](MdmMetadataProperty.md)

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

oracle.olapi.metadata.mdm

## Interface MdmMemberListMapOwner

- All Known Implementing Classes:
  [MdmDimensionLevel](MdmDimensionLevel.md), [MdmMeasureDimension](MdmMeasureDimension.md), [MdmPrimaryDimension](MdmPrimaryDimension.md), [MdmStandardDimension](MdmStandardDimension.md), [MdmTimeDimension](MdmTimeDimension.md)

  ------------------------------------------------------------------------



      public interface MdmMemberListMapOwner

  An interface for an object that owns a `MemberListMap`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                              | Method and Description                                                                                                                                                          |
    |------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MemberListMap`](../mapping/MemberListMap.md) | `findOrCreateMemberListMap``()`<br>Gets the `MemberListMap` associated with the implementation of the interface or creates a new `MemberListMap` if one does not already exist. |
    | [`MemberListMap`](../mapping/MemberListMap.md) | `getMemberListMap``()`<br>Gets the `MemberListMap` associated with the implementation of the interface.                                                                         |

<!-- -->

- - ### Method Detail

    - #### getMemberListMap

          MemberListMap getMemberListMap()

      Gets the `MemberListMap` associated with the implementation of the interface.
      Returns:
      The `MemberListMap` associated with the `MdmMemberListMapOwner`.

    <!-- -->

    - #### findOrCreateMemberListMap

          MemberListMap findOrCreateMemberListMap()

      Gets the `MemberListMap` associated with the implementation of the interface or creates a new `MemberListMap` if one does not already exist.
      Returns:
      The `MemberListMap` associated with the `MdmMemberListMapOwner`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmMember.md)
- [Next Class](MdmMetadataProperty.md)

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
