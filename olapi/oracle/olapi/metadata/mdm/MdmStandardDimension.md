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

- [Prev Class](MdmSource.md)
- [Next Class](MdmStandardMember.md)

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

## Class MdmStandardDimension

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimension](MdmDimension.md)

          - - [oracle.olapi.metadata.mdm.MdmPrimaryDimension](MdmPrimaryDimension.md)

            - - oracle.olapi.metadata.mdm.MdmStandardDimension

<!-- -->

- All Implemented Interfaces:
  [MdmMemberListMapOwner](MdmMemberListMapOwner.md), [MdmQuery](MdmQuery.md), [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md), [Buildable](../../syntax/Buildable.md)

  ------------------------------------------------------------------------



      public final class MdmStandardDimension
      extends MdmPrimaryDimension

  An `MdmPrimaryDimension` that represents most types of metadata for Oracle OLAP dimensions, such as dimensions for products, customers, distribution channels, and so on. An application creates an `MdmStandardDimension` by calling the [`findOrCreateStandardDimension`](MdmDatabaseSchema.md) method of an `MdmDatabaseSchema`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                           | Method and Description                                                                                                                                                                                                                                                                                                    |
    |---------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                          | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmStandardDimension` method of the `MdmObjectVisitor` and passes that method the `MdmStandardDimension` and an `Object`.                                                                             |
    | `void`                                      | `addCustomMember``(`[`MdmStandardMember`](MdmStandardMember.md)` customMember)`<br>Adds a custom member to the `MdmStandardDimension`.                                                                                                                                                                                    |
    | [`MdmStandardMember`](MdmStandardMember.md) | `createCustomMember``(java.lang.String name, `[`MdmLevel`](MdmLevel.md)` level, java.lang.String parent, `[`MdmLevel`](MdmLevel.md)` parentLevel, `[`Source`](../../data/source/Source.md)` source, int precedence)`<br>Creates a custom dimension member with the specified parent level for the `MdmStandardDimension`. |
    | [`MdmStandardMember`](MdmStandardMember.md) | `createCustomMember``(java.lang.String name, `[`MdmLevel`](MdmLevel.md)` level, java.lang.String parent, `[`Source`](../../data/source/Source.md)` source, int precedence)`<br>Creates a custom dimension member for the `MdmStandardDimension`.                                                                          |
    | [`MdmStandardMember`](MdmStandardMember.md) | `createCustomMember``(java.lang.String name, `[`MdmValueHierarchy`](MdmValueHierarchy.md)` valueHier, `[`Source`](../../data/source/Source.md)` source, int precedence)`<br>Creates a custom dimension member for an `MdmValueHierarchy` component of the `MdmStandardDimension`.                                         |
    | `java.util.List`                            | `getCustomMembers``()`<br>Gets the custom members of the `MdmStandardDimension`.                                                                                                                                                                                                                                          |
    | `void`                                      | `removeCustomMember``(`[`MdmStandardMember`](MdmStandardMember.md)` customMember)`<br>Removes a custom member from the `MdmStandardDimension`.                                                                                                                                                                            |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmPrimaryDimension](MdmPrimaryDimension.md)

      [`addDimensionLevel`](MdmPrimaryDimension.md)`, `[`addHierarchy`](MdmPrimaryDimension.md)`, `[`addModel`](MdmPrimaryDimension.md)`, `[`findOrCreateAWPrimaryDimensionOrganization`](MdmPrimaryDimension.md)`, `[`findOrCreateBaseAttribute`](MdmPrimaryDimension.md)`, `[`findOrCreateDimCalcModel`](MdmPrimaryDimension.md)`, `[`findOrCreateDimensionLevel`](MdmPrimaryDimension.md)`, `[`findOrCreateLevelHierarchy`](MdmPrimaryDimension.md)`, `[`findOrCreateMdmCustomMember`](MdmPrimaryDimension.md)`, `[`findOrCreateMemberListMap`](MdmPrimaryDimension.md)`, `[`findOrCreateRolapPrimaryDimensionOrganization`](MdmPrimaryDimension.md)`, `[`findOrCreateValueHierarchy`](MdmPrimaryDimension.md)`, `[`getAncestorsAttribute`](MdmPrimaryDimension.md)`, `[`getAttributes`](MdmPrimaryDimension.md)`, `[`getDefaultCalcModel`](MdmPrimaryDimension.md)`, `[`getDefaultHierarchy`](MdmPrimaryDimension.md)`, `[`getDimensionLevels`](MdmPrimaryDimension.md)`, `[`getETDimensionOrderColumn`](MdmPrimaryDimension.md)`, `[`getETHierarchyOrderColumn`](MdmPrimaryDimension.md)`, `[`getETKeyColumn`](MdmPrimaryDimension.md)`, `[`getETLevelNameColumn`](MdmPrimaryDimension.md)`, `[`getETLocalValueColumn`](MdmPrimaryDimension.md)`, `[`getETMemberTypeColumn`](MdmPrimaryDimension.md)`, `[`getETViewName`](MdmPrimaryDimension.md)`, `[`getHierarchies`](MdmPrimaryDimension.md)`, `[`getHierarchy`](MdmPrimaryDimension.md)`, `[`getHierarchyAttribute`](MdmPrimaryDimension.md)`, `[`getIsCustomMemberAttribute`](MdmPrimaryDimension.md)`, `[`getLevelAttribute`](MdmPrimaryDimension.md)`, `[`getLevelDepthAttribute`](MdmPrimaryDimension.md)`, `[`getLocalValueAttribute`](MdmPrimaryDimension.md)`, `[`getMdmCustomMembers`](MdmPrimaryDimension.md)`, `[`getMemberListMap`](MdmPrimaryDimension.md)`, `[`getModels`](MdmPrimaryDimension.md)`, `[`getNamespace`](MdmPrimaryDimension.md)`, `[`getOrganization`](MdmPrimaryDimension.md)`, `[`getOwner`](MdmPrimaryDimension.md)`, `[`getParentAttribute`](MdmPrimaryDimension.md)`, `[`getPersistentLanguages`](MdmPrimaryDimension.md)`, `[`getQuery`](MdmPrimaryDimension.md)`, `[`getQueryColumn`](MdmPrimaryDimension.md)`, `[`getQueryColumns`](MdmPrimaryDimension.md)`, `[`getQueryName`](MdmPrimaryDimension.md)`, `[`getShortValueDescriptionAttribute`](MdmPrimaryDimension.md)`, `[`getType`](MdmPrimaryDimension.md)`, `[`getValueDescriptionAttribute`](MdmPrimaryDimension.md)`, `[`getValueLineageAttribute`](MdmPrimaryDimension.md)`, `[`getValueSeparationString`](MdmPrimaryDimension.md)`, `[`removeAttribute`](MdmPrimaryDimension.md)`, `[`removeDimensionLevel`](MdmPrimaryDimension.md)`, `[`removeHierarchy`](MdmPrimaryDimension.md)`, `[`removeMdmCustomMember`](MdmPrimaryDimension.md)`, `[`removeModel`](MdmPrimaryDimension.md)`, `[`setDefaultCalcModel`](MdmPrimaryDimension.md)`, `[`setDefaultHierarchy`](MdmPrimaryDimension.md)`, `[`setETViewName`](MdmPrimaryDimension.md)`, `[`setMemberListMap`](MdmPrimaryDimension.md)`, `[`setOwner`](MdmPrimaryDimension.md)`, `[`setShortValueDescriptionAttribute`](MdmPrimaryDimension.md)`, `[`setValueDescriptionAttribute`](MdmPrimaryDimension.md)`, `[`setValueSeparationString`](MdmPrimaryDimension.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmDimension](MdmDimension.md)

      [`getCardinality`](MdmDimension.md)`, `[`getCustomOrder`](MdmDimension.md)`, `[`getPluralDescription`](MdmDimension.md)`, `[`getPrimaryDimension`](MdmDimension.md)`, `[`getShortPluralDescription`](MdmDimension.md)`, `[`setCardinality`](MdmDimension.md)`, `[`setCustomOrder`](MdmDimension.md)`, `[`setPluralDescription`](MdmDimension.md)`, `[`setShortPluralDescription`](MdmDimension.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSource](MdmSource.md)

      [`getDataType`](MdmSource.md)`, `[`getSource`](MdmSource.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)

      [`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmStandardDimension` method of the `MdmObjectVisitor` and passes that method the `MdmStandardDimension` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmStandardDimension` method.

    <!-- -->

    - #### createCustomMember

          public MdmStandardMember createCustomMember(java.lang.String name,
                                                      MdmLevel level,
                                                      java.lang.String parent,
                                                      Source source,
                                                      int precedence)

      Creates a custom dimension member for the `MdmStandardDimension`. For example, the following code creates a custom member of the Product dimension at the `ITEM` level. In the example, `calc1` defines a calculation that produces the measure value for the dimension member for a measure dimensioned by the dimension.
           MdmStandardMember myProdMember = mdmProdStdDim.createCustomMember(
                                                                      "EXE and STD",
                                                                      mdmItemLevel,
                                                                      "LTPC",
                                                                      calc1,
                                                                      10);

      Parameters:
      `name` - A `String` that contains the local value for the member.

      `level` - The `MdmLevel` to which you want the member to belong.

      `parent` - A `String` that contains the local value of the parent of the member. The parent must be a member of the level that is one level above the level to which the custom member belongs.

      `source` - A `Source` that specifies the value of the custom member; this value is the measure value that is specified by the custom member for an `MdmMeasure` that is dimensioned by the `MdmStandardDimension`.

      `precedence` - An integer that specifies the precedence for the custom member.

      Returns:
      An `MdmStandardMember` that is a custom member of the dimension.

      See Also:
      [`FundamentalMetadataProvider`](../../data/source/FundamentalMetadataProvider.md)

    <!-- -->

    - #### createCustomMember

          public MdmStandardMember createCustomMember(java.lang.String name,
                                                      MdmLevel level,
                                                      java.lang.String parent,
                                                      MdmLevel parentLevel,
                                                      Source source,
                                                      int precedence)

      Creates a custom dimension member with the specified parent level for the `MdmStandardDimension`.
      Parameters:
      `name` - A `String` that contains the local value for the member.

      `level` - The `MdmLevel` to which you want the member to belong.

      `parent` - A `String` that contains the local value of the parent of the member.

      `parentLevel` - The `MdmLevel` to which the parent of the member belongs.

      `source` - A `Source` that specifies the value of the custom member; this value is the measure value that is specified by the custom member for an `MdmMeasure` that is dimensioned by the `MdmStandardDimension`.

      `precedence` - An integer that specifies the precedence for the custom member.

      Returns:
      An `MdmStandardMember` that is a custom member of the dimension.

    <!-- -->

    - #### createCustomMember

          public MdmStandardMember createCustomMember(java.lang.String name,
                                                      MdmValueHierarchy valueHier,
                                                      Source source,
                                                      int precedence)

      Creates a custom dimension member for an `MdmValueHierarchy` component of the `MdmStandardDimension`.
      Parameters:
      `name` - A `String` that contains the local value for the member.

      `valueHier` - The `MdmValueHierarchy` to which you want the member to belong.

      `source` - A `Source` that specifies the value of the custom member; this value is the measure value that is specified by the custom member for an `MdmMeasure` that is dimensioned by the `MdmStandardDimension`.

      `precedence` - An integer that specifies the precedence for the custom member.

      Returns:
      An `MdmStandardMember` that is a custom member of the dimension.

    <!-- -->

    - #### getCustomMembers

          public final java.util.List getCustomMembers()

      Gets the custom members of the `MdmStandardDimension`.
      Returns:
      A `List` that contains the `MdmStandardMember` objects that are the custom members of the `MdmStandardDimension`.

    <!-- -->

    - #### addCustomMember

          public final void addCustomMember(MdmStandardMember customMember)

      Adds a custom member to the `MdmStandardDimension`. Use this method to add a custom member that you create with the constructor of the `MdmStandardMember` class.
      Parameters:
      `customMember` - The custom `MdmStandardMember` to add to the `MdmStandardDimension`.

    <!-- -->

    - #### removeCustomMember

          public final void removeCustomMember(MdmStandardMember customMember)

      Removes a custom member from the `MdmStandardDimension`.
      Parameters:
      `customMember` - The custom `MdmStandardMember` to remove from the `MdmStandardDimension`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmSource.md)
- [Next Class](MdmStandardMember.md)

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
