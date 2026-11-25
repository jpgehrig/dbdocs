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

- [Prev Class](MdmHierarchy.md)
- [Next Class](MdmInvalidValueException.md)

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

## Class MdmHierarchyLevel

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimension](MdmDimension.md)

          - - [oracle.olapi.metadata.mdm.MdmSubDimension](MdmSubDimension.md)

            - - oracle.olapi.metadata.mdm.MdmHierarchyLevel

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [MdmLevel](MdmLevel.md)

  ------------------------------------------------------------------------



      public class MdmHierarchyLevel
      extends MdmSubDimension

  An `MdmSubDimension` whose members comprise one level of an `MdmLevelHierarchy`. An application creates an `MdmHierarchyLevel` with the `findOrCreateHierarchyLevel` method of the `MdmLevelHierarchy`. The members of an `MdmHierarchyLevel` are specified by an associated `HierarchyLevelMap`
  If the `MdmLevelHierarchy` has more than one component `MdmHierarchyLevel`, then the `MdmLevelHierarchy` has a hierarchical structure that is specified by parent-child relationships between the members of the `MdmHierarchyLevel` components. Those parent-child relationships are recorded by `MdmAttribute` objects that you can get with the `getParentAttribute` and `getAncestorsAttribute` methods of the `MdmLevelHierarchy`.

  An `MdmHierarchyLevel` is associated with an `MdmDimensionLevel`. The members of the `MdmHierarchyLevel` are a subset of the members of the `MdmDimensionLevel`. The `getType` method of the `MdmDimensionLevel` returns the type of data that the `MdmHierarchyLevel` represents.

  See Also:
  [`HierarchyLevelMap`](../mapping/HierarchyLevelMap.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                                                                                                                                                                                                             |
    |--------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                     | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmHierarchyLevel` method of the specified `MdmObjectVisitor` and passes that method this `MdmHierarchyLevel` and an `Object`. |
    | [`HierarchyLevelMap`](../mapping/HierarchyLevelMap.md) | `findOrCreateHierarchyLevelMap``()`<br>Gets the `HierarchyLevelMap` that is associated with this `MdmHierarchyLevel` or creates a new `HierarchyLevelMap` if one does not already exist.                                                           |
    | [`MdmDimensionLevel`](MdmDimensionLevel.md)            | `getDimensionLevel``()`<br>Gets the `MdmDimensionLevel` associated with this `MdmHierarchyLevel`.                                                                                                                                                  |
    | [`HierarchyLevelMap`](../mapping/HierarchyLevelMap.md) | `getHierarchyLevelMap``()`<br>Gets the `HierarchyLevelMap` associated with this `MdmHierarchyLevel`.                                                                                                                                               |
    | `int`                                                  | `getLevelDepth``()`<br>Gets the depth of this `MdmHierarchyLevel` in the hierarchy of levels of the `MdmHierarchy` of which this level is a component.                                                                                             |
    | [`MdmLevelHierarchy`](MdmLevelHierarchy.md)            | `getLevelHierarchy``()`<br>Gets the `MdmLevelHierarchy` of which this `MdmLevel` is a component.                                                                                                                                                   |
    | `java.lang.String`                                     | `getName``()`<br>Gets the name of this `MdmObject`.                                                                                                                                                                                                |
    | `void`                                                 | `setHierarchyLevelMap``(`[`HierarchyLevelMap`](../mapping/HierarchyLevelMap.md)` value)`<br>Specifies the `HierarchyLevelMap` to associate with this `MdmHierarchyLevel`.                                                                          |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSubDimension](MdmSubDimension.md)

      [`addAttribute`](MdmSubDimension.md)`, `[`getAttributes`](MdmSubDimension.md)`, `[`removeAttribute`](MdmSubDimension.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmDimension](MdmDimension.md)

      [`getCardinality`](MdmDimension.md)`, `[`getCustomOrder`](MdmDimension.md)`, `[`getPluralDescription`](MdmDimension.md)`, `[`getPrimaryDimension`](MdmDimension.md)`, `[`getShortPluralDescription`](MdmDimension.md)`, `[`setCardinality`](MdmDimension.md)`, `[`setCustomOrder`](MdmDimension.md)`, `[`setPluralDescription`](MdmDimension.md)`, `[`setShortPluralDescription`](MdmDimension.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSource](MdmSource.md)

      [`getDataType`](MdmSource.md)`, `[`getSource`](MdmSource.md)`, `[`getType`](MdmSource.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)

      [`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmHierarchyLevel` method of the specified `MdmObjectVisitor` and passes that method this `MdmHierarchyLevel` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `Mdm11_ObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmHierarchyLevel` method.

    <!-- -->

    - #### getLevelHierarchy

          public MdmLevelHierarchy getLevelHierarchy()

      Gets the `MdmLevelHierarchy` of which this `MdmLevel` is a component.
      Returns:
      The `MdmLevelHierarchy` of which this `MdmLevel` is a component.

    <!-- -->

    - #### getName

          public final java.lang.String getName()
                                         throws oracle.express.mdm.MetadataNotFoundException

      Gets the name of this `MdmObject`.
      Overrides:
      [`getName`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      A `String` that contains the name of this `MdmObject`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException` - Indicates that the requested metadata object does not exist or is not available to the `MdmMetadataProvider`.

    <!-- -->

    - #### getLevelDepth

          public int getLevelDepth()

      Gets the depth of this `MdmHierarchyLevel` in the hierarchy of levels of the `MdmHierarchy` of which this level is a component.
      Returns:
      An integer that indicates the level depth of the level in a hierarchy of levels.

    <!-- -->

    - #### getDimensionLevel

          public MdmDimensionLevel getDimensionLevel()

      Gets the `MdmDimensionLevel` associated with this `MdmHierarchyLevel`.
      Returns:
      The `MdmDimensionLevel` associated with this `MdmHierarchyLevel`.

    <!-- -->

    - #### getHierarchyLevelMap

          public final HierarchyLevelMap getHierarchyLevelMap()

      Gets the `HierarchyLevelMap` associated with this `MdmHierarchyLevel`. The `HierarchyLevelMap` maps the members of the `MdmHierarchyLevel` to data in the relational database.
      Returns:
      The `HierarchyLevelMap` for the `MdmLevel`.

    <!-- -->

    - #### findOrCreateHierarchyLevelMap

          public HierarchyLevelMap findOrCreateHierarchyLevelMap()

      Gets the `HierarchyLevelMap` that is associated with this `MdmHierarchyLevel` or creates a new `HierarchyLevelMap` if one does not already exist.
      Returns:
      The `HierarchyLevelMap` associated with this `MdmHierarchyLevel`.

    <!-- -->

    - #### setHierarchyLevelMap

          public void setHierarchyLevelMap(HierarchyLevelMap value)

      Specifies the `HierarchyLevelMap` to associate with this `MdmHierarchyLevel`.
      Parameters:
      `value` - The `HierarchyLevelMap` to associate with this `MdmHierarchyLevel`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmHierarchy.md)
- [Next Class](MdmInvalidValueException.md)

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
