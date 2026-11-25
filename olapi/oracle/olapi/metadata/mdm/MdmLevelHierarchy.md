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

- [Prev Class](MdmLevel.md)
- [Next Class](MdmMeasure.md)

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

## Class MdmLevelHierarchy

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimension](MdmDimension.md)

          - - [oracle.olapi.metadata.mdm.MdmSubDimension](MdmSubDimension.md)

            - - [oracle.olapi.metadata.mdm.MdmHierarchy](MdmHierarchy.md)

              - - oracle.olapi.metadata.mdm.MdmLevelHierarchy

<!-- -->

- All Implemented Interfaces:
  [MdmQuery](MdmQuery.md), [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class MdmLevelHierarchy
      extends MdmHierarchy

  An `MdmHierarchy` that represents members of an Oracle OLAP dimension that are organized either nonhierarchically or hierarchically by levels. An application creates an `MdmLevelHierarchy` with the [`findOrCreateLevelHierarchy`](MdmPrimaryDimension.md) method of an `MdmPrimaryDimension`.
  An `MdmLevelHierarchy` has component `MdmHierarchyLevel` objects. A nonhierarchical `MdmLevelHierarchy` has only one `MdmHierarchyLevel` component, and a hierarchical `MdmLevelHierarchy` has more than one `MdmHierarchyLevel` components. An `MdmLevelHierarchy` can have up to 31 component `MdmHierarchyLevel` objects.

  The hierarchical organization is defined by parent-child relationships between the members of the `MdmHierarchyLevel` components. `MdmAttribute` objects record the parent-child relationships among the members of an `MdmLevelHierarchy` You use the `getParentAttribute` and `getAncestorsAttribute` methods to get the `MdmAttribute` objects that relate parents to children and ancestors to descendents, respectively.

  The `MdmLevelHierarchy` has all of the members of its `MdmHierarchyLevel` components. Each of its component `MdmHierarchyLevel` objects has the members of the hierarchy for that level. For example, an `MdmLevelHierarchy` for a calendar year time hierarchy might have parent-child relationships organized at year, quarter, month, and day levels. The `MdmLevelHierarchy` would have the members at every level. It would also have four component `MdmHierarchyLevel` objects, one for each level.

  To map the levels of an `MdmLevelHierarchy` to data sources, you can either use `MemberListMap` objects to map the `MdmDimensionLevel` objects or you can use `HierarchyLevelMap` objects to map the `MdmHierarchyLevel` objects.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                                                                                                                                                                                                                     |
    |-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                              | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmLevelHierarchy` method of the specified `MdmObjectVisitor` and passes that method the `MdmLevelHierarchy` and the specified `context` object.                                                                                                       |
    | `void`                                                          | `addHierarchyLevel``(`[`MdmHierarchyLevel`](MdmHierarchyLevel.md)` level)`<br>Appends an `MdmHierarchyLevel` to the ordered list of hierarchy levels that are associated with this `MdmLevelHierarchy`.                                                                                                                                                                    |
    | `void`                                                          | `addHierarchyLevel``(`[`MdmHierarchyLevel`](MdmHierarchyLevel.md)` level, int levelNumber)`<br>Adds an `MdmHierarchyLevel` at the specified position in the ordered list of hierarchy levels that are associated with this When the `findOrCreateHierarchyLevel` method creates a new `MdmHierarchyLevel`, it adds the new hierarchy level to the end of the ordered list. |
    | [`MdmHierarchyLevel`](MdmHierarchyLevel.md)                     | `findOrCreateHierarchyLevel``(`[`MdmDimensionLevel`](MdmDimensionLevel.md)` dimLevel)`<br>Gets the specified `MdmHierarchyLevel` or, if it does not already exist, creates a new one for this `MdmLevelHierarchy`.                                                                                                                                                         |
    | [`MdmDimensionMemberInfo`](MdmDimensionMemberInfo.md)           | `getDefaultMember``()`<br>Gets the `MdmDimensionMemberInfo` that specifies the default member of the `MdmLevelHierarchy`.                                                                                                                                                                                                                                                  |
    | `java.util.List<`[`MdmHierarchyLevel`](MdmHierarchyLevel.md)`>` | `getHierarchyLevels``()`<br>Gets the `MdmHierarchyLevel` components of the `MdmLevelHierarchy`.                                                                                                                                                                                                                                                                            |
    | [`MdmAttribute`](MdmAttribute.md)                               | `getLevelAttribute``()`<br>Gets the `MdmAttribute` that relates the members of a component `MdmHierarchyLevel` to a level in the hierarchy.                                                                                                                                                                                                                                |
    | [`MdmAttribute`](MdmAttribute.md)                               | `getLevelDepthAttribute``()`<br>Gets the `MdmAttribute` that relates the members of a component `MdmHierarchyLevel` to the depth of a level in the hierarchy.                                                                                                                                                                                                              |
    | `java.util.List`                                                | `getLevels``()`<br>Gets the `MdmHierarchyLevel` components of the `MdmLevelHierarchy`.                                                                                                                                                                                                                                                                                     |
    | [`MdmQueryColumn`](MdmQueryColumn.md)                           | `getQueryColumn``(java.lang.String name)`<br>Gets the specified `MdmQueryColumn`.                                                                                                                                                                                                                                                                                          |
    | `java.util.List<`[`MdmQueryColumn`](MdmQueryColumn.md)`>`       | `getQueryColumns``()`<br>Gets the `MdmQueryColumn` objects that are associated with this `MdmLevelHierarchy`.                                                                                                                                                                                                                                                              |
    | `boolean`                                                       | `isRagged``()`<br>Indicates whether the hierarchy is ragged, which means that not all of the leaf members are at the same level.                                                                                                                                                                                                                                           |
    | `boolean`                                                       | `isSkipLevel``()`<br>Indicates whether this `MdmLevelHierarchy` is a skip-level hierarchy.                                                                                                                                                                                                                                                                                 |
    | `boolean`                                                       | `isSnowflake``()`                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                          | `removeHierarchyLevel``(`[`MdmHierarchyLevel`](MdmHierarchyLevel.md)` level)`<br>Removes the specified `MdmHierarchyLevel` from this `MdmLevelHierarchy`.                                                                                                                                                                                                                  |
    | `void`                                                          | `removeLevel``(`[`MdmLevel`](MdmLevel.md)` level)`<br>Removes the specified `MdmLevel` from this `MdmLevelHierarchy`.                                                                                                                                                                                                                                                      |
    | `void`                                                          | `setDefaultMember``(`[`MdmDimensionMemberInfo`](MdmDimensionMemberInfo.md)` defaultMember)`<br>Specifies a default member for the `MdmLevelHierarchy`.                                                                                                                                                                                                                     |
    | `void`                                                          | `setIsRagged``(boolean input)`<br>Specifies that the hierarchy is ragged or not ragged.                                                                                                                                                                                                                                                                                    |
    | `void`                                                          | `setIsSkipLevel``(boolean input)`<br>Specifies whether this `MdmLevelHierarchy` is a skip-level hierarchy.                                                                                                                                                                                                                                                                 |
    | `void`                                                          | `setSnowflake``(boolean isSnowflake)`                                                                                                                                                                                                                                                                                                                                      |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmHierarchy](MdmHierarchy.md)

      [`getAncestorsAttribute`](MdmHierarchy.md)`, `[`getETDepthColumn`](MdmHierarchy.md)`, `[`getETParentColumn`](MdmHierarchy.md)`, `[`getETViewName`](MdmHierarchy.md)`, `[`getParentAttribute`](MdmHierarchy.md)`, `[`getQuery`](MdmHierarchy.md)`, `[`getQueryName`](MdmHierarchy.md)`, `[`isDefaultHierarchy`](MdmHierarchy.md)`, `[`setETViewName`](MdmHierarchy.md)

    <!-- -->

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

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmLevelHierarchy` method of the specified `MdmObjectVisitor` and passes that method the `MdmLevelHierarchy` and the specified `context` object.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmLevelHierarchy` method.

    <!-- -->

    - #### getLevelAttribute

          public final MdmAttribute getLevelAttribute()

      Gets the `MdmAttribute` that relates the members of a component `MdmHierarchyLevel` to a level in the hierarchy.
      Returns:
      The `MdmAttribute` that relates the members of the `MdmHierarchyLevel` components of this `MdmLevelHierarchy` to a level in the hierarchy.

    <!-- -->

    - #### getLevelDepthAttribute

          public final MdmAttribute getLevelDepthAttribute()

      Gets the `MdmAttribute` that relates the members of a component `MdmHierarchyLevel` to the depth of a level in the hierarchy. For example, an `MdmLevelHierarchy` that represents a hierarchy that has four levels would have four component `MdmHierarchyLevel` objects. The members of the `MdmHierarchyLevel` for the top level of the hierarchy have a level depth of 1, the members of the `MdmHierarchyLevel` that are the children of the level 1 members have a level depth of 2, and so on.
      Returns:
      The `MdmAttribute` that relates the members of the `MdmHierarchyLevel` components of this `MdmLevelHierarchy` to the depth of their level in the hierarchy.

    <!-- -->

    - #### getLevels

          public final java.util.List getLevels()

      Gets the `MdmHierarchyLevel` components of the `MdmLevelHierarchy`. This method provides compatibility with earlier versions of the Oracle OLAP Java API. In those earlier versions, this method returned a `List` of `MdmLevel` objects. The `MdmLevel` class is now a subclass of `MdmHierarchyLevel` and is deprecated.
      Returns:
      A `List` that contains the `MdmHierarchyLevel` components of the `MdmLevelHierarchy`.

    <!-- -->

    - #### getHierarchyLevels

          public final java.util.List<MdmHierarchyLevel> getHierarchyLevels()

      Gets the `MdmHierarchyLevel` components of the `MdmLevelHierarchy`.
      Returns:
      A `List` that contains the `MdmHierarchyLevel` components of the `MdmLevelHierarchy`.

    <!-- -->

    - #### getDefaultMember

          public MdmDimensionMemberInfo getDefaultMember()
                                                  throws oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmDimensionMemberInfo` that specifies the default member of the `MdmLevelHierarchy`. From the `MdmDimensionMemberInfo` you can get the value of the default member by calling the `getLocalValue` or `getUniqueValue` method.
      Specified by:
      [`getDefaultMember`](MdmHierarchy.md) in class [`MdmHierarchy`](MdmHierarchy.md)

      Returns:
      An `MdmDimensionMemberInfo` that has the default member of the `MdmLevelHierarchy`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### setDefaultMember

          public void setDefaultMember(MdmDimensionMemberInfo defaultMember)
                                throws oracle.express.mdm.MetadataNotFoundException,
                                       MdmInvalidValueException

      Specifies a default member for the `MdmLevelHierarchy`.
      Specified by:
      [`setDefaultMember`](MdmHierarchy.md) in class [`MdmHierarchy`](MdmHierarchy.md)

      Parameters:
      `defaultMember` - An `MdmDimensionMemberInfo` that has the value to specify as the default member of the `MdmLevelHierarchy`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

      [`MdmInvalidValueException`](MdmInvalidValueException.md)

    <!-- -->

    - #### addHierarchyLevel

          public void addHierarchyLevel(MdmHierarchyLevel level,
                                        int levelNumber)

      Adds an `MdmHierarchyLevel` at the specified position in the ordered list of hierarchy levels that are associated with this When the `findOrCreateHierarchyLevel` method creates a new `MdmHierarchyLevel`, it adds the new hierarchy level to the end of the ordered list. To place a `MdmHierarchyLevel` in a different position in the list, you must remove it and add it back in the desired position. For example, the following code moves an `MdmHierarchyLevel` to the specified position in the list. The example creates three `MdmHierarchyLevel` objects. It removes the second `MdmHierarchyLevel` and then adds it back at the beginning of the list, which is position 0 (zero). In the example, `mdmDLevelFee`, `mdmDLevelFie`, and `mdmDLevelFoe` are `MdmDimensionLevel` objects.
           MdmHierarchyLevel mdmHLevelFee =
                            mdmLevelHierarchy.findOrCreateHierarchyLevel(mdmDLevelFee);
           MdmHierarchyLevel mdmHLevelFie =
                            mdmLevelHierarchy.findOrCreateHierarchyLevel(mdmDLevelFie);
           MdmHierarchyLevel mdmHLevelFoe =
                            mdmLevelHierarchy.findOrCreateHierarchyLevel(mdmDLevelFoe);

           mdmLevelHierarchy.removeHierarchyLevel(mdmHLevelFie);
           mdmLevelHierarchy.addHierarchyLevel(mdmHLevelFie, 0);

      Parameters:
      `level` - The `MdmHierarchyLevel` to add to the list.

      `levelNumber` - The position in the hierarchy for the level.

    <!-- -->

    - #### addHierarchyLevel

          public void addHierarchyLevel(MdmHierarchyLevel level)

      Appends an `MdmHierarchyLevel` to the ordered list of hierarchy levels that are associated with this `MdmLevelHierarchy`. `MdmLevelHierarchy`. When the `findOrCreateHierarchyLevel` method creates a new `MdmHierarchyLevel`, it adds the new hierarchy level to the end of the ordered list. To place a `MdmHierarchyLevel` in a different position in the list, you must remove it and add it back in the desired position. For example, the following code positions a new `MdmHierarchyLevel` before a previously existing `MdmHierarchyLevel`. To do so, it removes the existing `MdmHierarchyLevel`, creates the new `MdmHierarchyLevel`, and then adds the previously existing `MdmHierarchyLevel` to the end of the list. In the example, `mdmDLevelFoo` and `mdmDLevelBar` are `MdmDimensionLevel` objects.
           MdmHierarchyLevel mdmHLevelFoo =
                             mdmLevelHierarchy.findOrCreateHierarchyLevel(mdmDLevelFoo);
           MdmHierarchyLevel mdmHLevelBar =
                             mdmLevelHierarchy.findOrCreateHierarchyLevel(mdmDLevelBar);
           mdmLevelHierarchy.removeHierarchyLevel(mdmHLevelFoo);
           mdmLevelHierarchy.addHierarchyLevel(mdmHLevelFoo);

      Parameters:
      `level` - The `MdmHierarchyLevel` to append to the list.

    <!-- -->

    - #### removeLevel

          public void removeLevel(MdmLevel level)

      Removes the specified `MdmLevel` from this `MdmLevelHierarchy`.
      Parameters:
      `level` - The `MdmLevel` to remove as a component of the hierarchy.

    <!-- -->

    - #### removeHierarchyLevel

          public void removeHierarchyLevel(MdmHierarchyLevel level)

      Removes the specified `MdmHierarchyLevel` from this `MdmLevelHierarchy`.
      Parameters:
      `level` - The `MdmHierarchyLevel` to remove as a component of the hierarchy.

    <!-- -->

    - #### isSkipLevel

          public final boolean isSkipLevel()

      Indicates whether this `MdmLevelHierarchy` is a skip-level hierarchy. A skip-level hierarchy contains at least one member whose parents are more than one level above it.
      Returns:
      A `boolean` that is `true` if the hierarchy is a skip-level hierarchy or `false` if it is not.

    <!-- -->

    - #### setIsSkipLevel

          public final void setIsSkipLevel(boolean input)

      Specifies whether this `MdmLevelHierarchy` is a skip-level hierarchy. A skip-level hierarchy contains at least one member whose parents are more than one level above it, creating a hole in the hierarchy. An example of a skip-level hierarchy is City-State-Country, where at least one city has a country as its parent (for example, Washington D.C. in the United States).
      Parameters:
      `input` - A `boolean` that is `true` if the hierarchy is a skip-level hierarchy or `false` if it is not.

    <!-- -->

    - #### isRagged

          public final boolean isRagged()

      Indicates whether the hierarchy is ragged, which means that not all of the leaf members are at the same level. Leaf members are those that have no children.
      Returns:
      A `boolean` that is `true` if the hierarchy is ragged or `false` if it is not.

    <!-- -->

    - #### setIsRagged

          public final void setIsRagged(boolean input)

      Specifies that the hierarchy is ragged or not ragged. A ragged hierachy is one in which not all of the leaf members are at the same level. Leaf members are those that have no children.
      Parameters:
      `input` - A `boolean` that is `true` if the hierarchy is ragged or `false` if it is not.

    <!-- -->

    - #### isSnowflake

          public final boolean isSnowflake()

    <!-- -->

    - #### setSnowflake

          public final void setSnowflake(boolean isSnowflake)

    <!-- -->

    - #### getQueryColumns

          public final java.util.List<MdmQueryColumn> getQueryColumns()

      Gets the `MdmQueryColumn` objects that are associated with this `MdmLevelHierarchy`.
      Specified by:
      [`getQueryColumns`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Overrides:
      [`getQueryColumns`](MdmHierarchy.md) in class [`MdmHierarchy`](MdmHierarchy.md)

      Returns:
      A `List` of the `MdmQueryColumn` objects associated with this `MdmLevelHierarchy`.

    <!-- -->

    - #### getQueryColumn

          public MdmQueryColumn getQueryColumn(java.lang.String name)

      Gets the specified `MdmQueryColumn`.
      Specified by:
      [`getQueryColumn`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Overrides:
      [`getQueryColumn`](MdmHierarchy.md) in class [`MdmHierarchy`](MdmHierarchy.md)

      Parameters:
      `name` - A `String` that contains the name of an `MdmQueryColumn`.

      Returns:
      The `MdmQueryColumn` that has the specified name.

    <!-- -->

    - #### findOrCreateHierarchyLevel

          public MdmHierarchyLevel findOrCreateHierarchyLevel(MdmDimensionLevel dimLevel)

      Gets the specified `MdmHierarchyLevel` or, if it does not already exist, creates a new one for this `MdmLevelHierarchy`. An `MdmHierarchyLevel` has an associated `MdmDimensionLevel`.
      If this method creates a new `MdmHierarchyLevel`, then it appends the new `MdmHierarchyLevel` to the list of `MdmHierarchyLevel` objects that are owned by this `MdmLevelHierarchy`. For information on changing the position of an `MdmHierarchyLevel` in the list, see the `addHierarchyLevel` methods.

      Parameters:
      `dimLevel` - An existing `MdmDimensionLevel` to associate with a new `MdmHierarchyLevel` or that is associated with an existing `MdmHierarchyLevel`.

      Returns:
      The specified `MdmHierarchyLevel` or a new one.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmLevel.md)
- [Next Class](MdmMeasure.md)

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
