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

- [Prev Class](MdmTable.md)
- [Next Class](MdmTimeMember.md)

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

## Class MdmTimeDimension

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimension](MdmDimension.md)

          - - [oracle.olapi.metadata.mdm.MdmPrimaryDimension](MdmPrimaryDimension.md)

            - - oracle.olapi.metadata.mdm.MdmTimeDimension

<!-- -->

- All Implemented Interfaces:
  [MdmMemberListMapOwner](MdmMemberListMapOwner.md), [MdmQuery](MdmQuery.md), [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md), [Buildable](../../syntax/Buildable.md)

  ------------------------------------------------------------------------



      public final class MdmTimeDimension
      extends MdmPrimaryDimension

  An `MdmPrimaryDimension` that represents an Oracle OLAP dimension of time periods. An application creates an `MdmTimeDimension` by calling the [`findOrCreateTimeDimension`](MdmDatabaseSchema.md) method of an `MdmDatabaseSchema`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                                                                                                                                                                                                                                                                 |
    |-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                  | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmTimeDimension` method of the `MdmObjectVisitor` and passes that method the `MdmTimeDimension` and the `Object`.                                                                                                                                 |
    | `void`                              | `addCustomMember``(`[`MdmTimeMember`](MdmTimeMember.md)` customMember)`<br>Adds a custom member to the `MdmTimeDimension`.                                                                                                                                                                                                                                             |
    | [`MdmTimeMember`](MdmTimeMember.md) | `createCustomMember``(java.lang.String name, `[`MdmLevel`](MdmLevel.md)` level, java.lang.String parent, java.util.Date endDate, int timeSpan, `[`Source`](../../data/source/Source.md)` source, int precedence)`<br>Creates a custom dimension member with the specified parent for the `MdmTimeDimension`.                                                           |
    | [`MdmTimeMember`](MdmTimeMember.md) | `createCustomMember``(java.lang.String name, `[`MdmLevel`](MdmLevel.md)` level, java.lang.String parent, `[`MdmLevel`](MdmLevel.md)` parentLevel, java.util.Date endDate, int timeSpan, `[`Source`](../../data/source/Source.md)` source, int precedence)`<br>Creates a custom dimension member with the specified parent and parent level for the `MdmTimeDimension`. |
    | [`MdmTimeMember`](MdmTimeMember.md) | `createCustomMember``(java.lang.String name, `[`MdmValueHierarchy`](MdmValueHierarchy.md)` valueHier, java.util.Date endDate, int timeSpan, `[`Source`](../../data/source/Source.md)` source, int precedence)`<br>Creates a custom dimension member for the `MdmTimeDimension`.                                                                                        |
    | `java.util.List`                    | `getCustomMembers``()`<br>Gets the custom members of the `MdmTimeDimension`.                                                                                                                                                                                                                                                                                           |
    | [`MdmAttribute`](MdmAttribute.md)   | `getEndDateAttribute``()`<br>Gets an `MdmAttribute` that relates each member of the `MdmSubDimension` components of the `MdmTimeDimension` to the end date of the time period that the member represents.                                                                                                                                                              |
    | [`MdmAttribute`](MdmAttribute.md)   | `getStartDateAttribute``()`<br>Gets an `MdmAttribute` that relates each member of the `MdmSubDimension` components of the `MdmTimeDimension` to the start date of the time period that the member represents.                                                                                                                                                          |
    | [`MdmAttribute`](MdmAttribute.md)   | `getTimeSpanAttribute``()`<br>Gets an `MdmAttribute` that relates each member of the `MdmSubDimension` components of the `MdmTimeDimension` to the time span of the time period that the member represents.                                                                                                                                                            |
    | `void`                              | `removeCustomMember``(`[`MdmTimeMember`](MdmTimeMember.md)` customMember)`<br>Removes a custom member from the `MdmTimeDimension`.                                                                                                                                                                                                                                     |
    | `void`                              | `setEndDateAttribute``(`[`MdmAttribute`](MdmAttribute.md)` endDateAttr)`<br>Specifies an `MdmAttribute` as the end date attribute for the dimension.                                                                                                                                                                                                                   |
    | `void`                              | `setStartDateAttribute``(`[`MdmAttribute`](MdmAttribute.md)` startDateAttr)`<br>Specifies an `MdmAttribute` as the start date attribute for the dimension.                                                                                                                                                                                                             |
    | `void`                              | `setTimeSpanAttribute``(`[`MdmAttribute`](MdmAttribute.md)` timeSpanAttr)`<br>Specifies an `MdmAttribute` as the time span attribute for the dimension.                                                                                                                                                                                                                |

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

      Calls the `visitMdmTimeDimension` method of the `MdmObjectVisitor` and passes that method the `MdmTimeDimension` and the `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `MdmObjectVisitor`.

    <!-- -->

    - #### getStartDateAttribute

          public final MdmAttribute getStartDateAttribute()

      Gets an `MdmAttribute` that relates each member of the `MdmSubDimension` components of the `MdmTimeDimension` to the start date of the time period that the member represents.
      Returns:
      An `MdmAttribute` that relates each member of the `MdmSubDimension` components of the `MdmTimeDimension` to the start date of the time period that the member represents.

    <!-- -->

    - #### getEndDateAttribute

          public final MdmAttribute getEndDateAttribute()

      Gets an `MdmAttribute` that relates each member of the `MdmSubDimension` components of the `MdmTimeDimension` to the end date of the time period that the member represents.
      Returns:
      An `MdmAttribute` that relates each member of the `MdmSubDimension` components of the `MdmTimeDimension` to the end date of the time period that the member represents.

    <!-- -->

    - #### getTimeSpanAttribute

          public final MdmAttribute getTimeSpanAttribute()

      Gets an `MdmAttribute` that relates each member of the `MdmSubDimension` components of the `MdmTimeDimension` to the time span of the time period that the member represents.
      Returns:
      An `MdmAttribute` that relates each member of the `MdmSubDimension` components of the `MdmTimeDimension` to the time span of the time period that the member represents.

    <!-- -->

    - #### setStartDateAttribute

          public void setStartDateAttribute(MdmAttribute startDateAttr)

      Specifies an `MdmAttribute` as the start date attribute for the dimension.
      Parameters:
      `startDateAttr` - An `MdmAttribute` that has start date values for members of the dimension.

    <!-- -->

    - #### setEndDateAttribute

          public void setEndDateAttribute(MdmAttribute endDateAttr)

      Specifies an `MdmAttribute` as the end date attribute for the dimension.
      Parameters:
      `endDateAttr` - An `MdmAttribute` that has end date values for members of the dimension.

    <!-- -->

    - #### setTimeSpanAttribute

          public void setTimeSpanAttribute(MdmAttribute timeSpanAttr)

      Specifies an `MdmAttribute` as the time span attribute for the dimension.
      Parameters:
      `timeSpanAttr` - An `MdmAttribute` that has time span values for members of the dimension.

    <!-- -->

    - #### createCustomMember

          public MdmTimeMember createCustomMember(java.lang.String name,
                                                  MdmLevel level,
                                                  java.lang.String parent,
                                                  java.util.Date endDate,
                                                  int timeSpan,
                                                  Source source,
                                                  int precedence)

      Creates a custom dimension member with the specified parent for the `MdmTimeDimension`.
      Parameters:
      `name` - A `String` that contains the local value for the member.

      `level` - The `MdmLevel` to which you want the member to belong.

      `parent` - A `String` that contains the local value of the parent of the member. The parent must be a member of the level that is one level above the level to which the custom member belongs.

      `endDate` - A `Date` that specifies the end date for the member.

      `timeSpan` - An integer that specifies the time span for the member.

      `source` - A `Source` that specifies the value of the custom member; this value is the measure value that is specified by the custom member for an `MdmMeasure` that is dimensioned by the `MdmTimeDimension`.

      `precedence` - An integer that specifies the precedence for the custom member.

      Returns:
      An `MdmTimeMember` that is a custom member of the dimension.

    <!-- -->

    - #### createCustomMember

          public MdmTimeMember createCustomMember(java.lang.String name,
                                                  MdmLevel level,
                                                  java.lang.String parent,
                                                  MdmLevel parentLevel,
                                                  java.util.Date endDate,
                                                  int timeSpan,
                                                  Source source,
                                                  int precedence)

      Creates a custom dimension member with the specified parent and parent level for the `MdmTimeDimension`.
      Parameters:
      `name` - A `String` that contains the local value for the member.

      `level` - The `MdmLevel` to which you want the member to belong.

      `parent` - A `String` that contains the local value of the parent of the member.

      `parentLevel` - The `MdmLevel` to which the parent of the member belongs.

      `endDate` - A `Date` that specifies the end date for the member.

      `timeSpan` - An integer that specifies the time span for the member.

      `source` - A `Source` that specifies the value of the custom member; the value is the measure value that is specified by the custom member for an `MdmMeasure` that is dimensioned by the `MdmTimeDimension`.

      `precedence` - An integer that specifies the precedence for the custom member.

      Returns:
      An `MdmTimeMember` that is a custom member of the dimension.

    <!-- -->

    - #### createCustomMember

          public MdmTimeMember createCustomMember(java.lang.String name,
                                                  MdmValueHierarchy valueHier,
                                                  java.util.Date endDate,
                                                  int timeSpan,
                                                  Source source,
                                                  int precedence)

      Creates a custom dimension member for the `MdmTimeDimension`.
      Parameters:
      `name` - A `String` that contains the local value for the member.

      `valueHier` - The `MdmValueHierarchy` to which you want the member to belong.

      `endDate` - A `Date` that specifies the end date for the member.

      `timeSpan` - An integer that specifies the time span for the member.

      `source` - A `Source` that specifies the value of the custom member; this value is the measure value that is specified by the custom member for an `MdmMeasure` that is dimensioned by the `MdmTimeDimension`.

      `precedence` - An integer that specifies the precedence for the custom member.

      Returns:
      An `MdmTimeMember` that is a custom member of the dimension.

    <!-- -->

    - #### getCustomMembers

          public final java.util.List getCustomMembers()

      Gets the custom members of the `MdmTimeDimension`.
      Returns:
      A `List` that contains the `MdmTimeMember` objects that are the custom members of the `MdmTimeDimension`.

    <!-- -->

    - #### addCustomMember

          public final void addCustomMember(MdmTimeMember customMember)

      Adds a custom member to the `MdmTimeDimension`. Use this method to add a custom member that you create with the constructor of the `MdmTimeMember` class.
      Parameters:
      `customMember` - The custom `MdmTimedMember` to add to the `MdmTimeDimension`.

    <!-- -->

    - #### removeCustomMember

          public final void removeCustomMember(MdmTimeMember customMember)

      Removes a custom member from the `MdmTimeDimension`.
      Parameters:
      `customMember` - The custom `MdmTimedMember` to remove from the `MdmTimeDimension`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmTable.md)
- [Next Class](MdmTimeMember.md)

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
