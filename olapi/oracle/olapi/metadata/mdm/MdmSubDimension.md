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

- [Prev Class](MdmStandardMember.md)
- [Next Class](MdmTable.md)

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

## Class MdmSubDimension

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimension](MdmDimension.md)

          - - oracle.olapi.metadata.mdm.MdmSubDimension

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [MdmDimensionLevel](MdmDimensionLevel.md), [MdmHierarchy](MdmHierarchy.md), [MdmHierarchyLevel](MdmHierarchyLevel.md)

  ------------------------------------------------------------------------



      public abstract class MdmSubDimension
      extends MdmDimension

  A component of an `MdmPrimaryDimension`. The type of the members of an `MdmSubDimension` is specified by the `MdmPrimaryDimension`. With the `getPrimaryDimension` method, an application can get the `MdmPrimaryDimension` for an `MdmSubDimension`.
  The subclasses of `MdmSubDimension` represent hierarchical or nonhierarchical organizations of the members of the dimension. The following are the subclasses of `MdmSubDimension`.

  - `MdmDimensionLevel`, which is an arbitrary subset of members of the `MdmPrimaryDimension`. A dimension member can be in at most one `MdmDimensionLevel`.
  - `MdmHierarchy`, which is an abstract class that represents a hierarchical organization of the members of the dimension. The concrete subclass `MdmLevelHierarchy` represents a hierarchy that has levels. Each level is represented by an `MdmHierarchyLevel`. The parents and children in the hierarchy belong to different levels. The concrete subclass `MdmValueHierarchy` represents a hierarchy that does not have levels.
  - `MdmHierarchyLevel`, which represents members of one level of an `MdmLevelHierarchy`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                        |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `addAttribute``(`[`MdmAttribute`](MdmAttribute.md)` attr)`<br>Adds an `MdmAttribute` to the `MdmSubDimension`.                                |
    | `java.util.List`  | `getAttributes``()`<br>Gets the `MdmAttribute` objects that have been explicitly added to the `MdmSubDimension` by the `addAttribute` method. |
    | `void`            | `removeAttribute``(`[`MdmAttribute`](MdmAttribute.md)` attr)`<br>Removes an `MdmAttribute` from the `MdmSubDimension`.                        |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmDimension](MdmDimension.md)

      [`getCardinality`](MdmDimension.md)`, `[`getCustomOrder`](MdmDimension.md)`, `[`getPluralDescription`](MdmDimension.md)`, `[`getPrimaryDimension`](MdmDimension.md)`, `[`getShortPluralDescription`](MdmDimension.md)`, `[`setCardinality`](MdmDimension.md)`, `[`setCustomOrder`](MdmDimension.md)`, `[`setPluralDescription`](MdmDimension.md)`, `[`setShortPluralDescription`](MdmDimension.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSource](MdmSource.md)

      [`getDataType`](MdmSource.md)`, `[`getSource`](MdmSource.md)`, `[`getType`](MdmSource.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)

      [`acceptVisitor`](MdmObject.md)`, `[`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getAttributes

          public final java.util.List getAttributes()

      Gets the `MdmAttribute` objects that have been explicitly added to the `MdmSubDimension` by the `addAttribute` method.
      Specified by:
      [`getAttributes`](MdmDimension.md) in class [`MdmDimension`](MdmDimension.md)

      Returns:
      A `List` of the `MdmAttribute` objects of the `MdmSubDimension`.

      See Also:
      [`MdmAttribute`](MdmAttribute.md)

    <!-- -->

    - #### addAttribute

          public final void addAttribute(MdmAttribute attr)

      Adds an `MdmAttribute` to the `MdmSubDimension`.
      Parameters:
      `attr` - The `MdmAttribute` to add to the `MdmSubDimension`.

    <!-- -->

    - #### removeAttribute

          public final void removeAttribute(MdmAttribute attr)

      Removes an `MdmAttribute` from the `MdmSubDimension`.
      Specified by:
      [`removeAttribute`](MdmDimension.md) in class [`MdmDimension`](MdmDimension.md)

      Parameters:
      `attr` - The `MdmAttribute` to remove from the `MdmSubDimension`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmStandardMember.md)
- [Next Class](MdmTable.md)

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
