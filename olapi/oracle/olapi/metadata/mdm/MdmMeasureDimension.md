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

- [Prev Class](MdmMeasure.md)
- [Next Class](MdmMeasureModel.md)

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

## Class MdmMeasureDimension

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimension](MdmDimension.md)

          - - [oracle.olapi.metadata.mdm.MdmPrimaryDimension](MdmPrimaryDimension.md)

            - - oracle.olapi.metadata.mdm.MdmMeasureDimension

<!-- -->

- All Implemented Interfaces:
  [MdmMemberListMapOwner](MdmMemberListMapOwner.md), [MdmQuery](MdmQuery.md), [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md), [Buildable](../../syntax/Buildable.md)

  ------------------------------------------------------------------------



      public final class MdmMeasureDimension
      extends MdmPrimaryDimension

  An `MdmPrimaryDimension` with members that are `MdmMeasure` objects. The `MdmRootSchema` of an `MdmMetadataProvider` has one persistent `MdmMeasureDimension`, which you can get by calling the `getMeasureDimension` method of the `MdmRootSchema`.
  With a `createCustomMeasure` method, you can create a transient custom measure that is not visible outside of your current session. You can create a custom measure in a child `Transaction`, commit the child `Transaction`, and then use the custom measure in a query.

  The precedence of a custom measure affects the order in which Oracle OLAP calculates values and assigns the values to the measure. Oracle OLAP evaluates the measure with the highest precedence value first, and then the measure with the next highest precedence value, and so on. If the value for one custom measure depends on the calculated value of another custom measure, then the measure with the dependent value should have a lower precedence.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type             | Method and Description                                                                                                                                                                                                                      |
    |-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`            | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmMeasureDimension` method of the `MdmObjectVisitor` and passes that method the `MdmMeasureDimension` and an `Object`. |
    | `void`                        | `addMeasure``(`[`MdmMeasure`](MdmMeasure.md)` measure)`<br>Adds an `MdmMeasure` to the `MdmMeasureDimension`.                                                                                                                               |
    | [`MdmMeasure`](MdmMeasure.md) | `createCustomMeasure``(java.lang.String name, `[`MdmSchema`](MdmSchema.md)` schema, `[`Source`](../../data/source/Source.md)` source, int precedence)`<br>Creates a custom `MdmMeasure` for the specified `MdmSchema`.                      |
    | [`MdmMeasure`](MdmMeasure.md) | `createCustomMeasure``(java.lang.String name, `[`Source`](../../data/source/Source.md)` source, int precedence)`<br>Creates a custom `MdmMeasure`.                                                                                          |
    | [`MdmCube`](MdmCube.md)       | `getCube``()`<br>Gets the `MdmCube` that is associated with this `MdmMeasureDimension`.                                                                                                                                                     |
    | `java.util.List`              | `getMeasures``()`<br>Gets a `List` that contains the `MdmMeasure` objects that are the members of the `MdmMeasureDimension`.                                                                                                                |
    | `void`                        | `removeMeasure``(`[`MdmMeasure`](MdmMeasure.md)` measure)`<br>Removes an `MdmMeasure` from the `MdmMeasureDimension`.                                                                                                                       |

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

      Calls the `visitMdmMeasureDimension` method of the `MdmObjectVisitor` and passes that method the `MdmMeasureDimension` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmMeasureDimension` method.

    <!-- -->

    - #### getMeasures

          public final java.util.List getMeasures()

      Gets a `List` that contains the `MdmMeasure` objects that are the members of the `MdmMeasureDimension`.
      Returns:
      A `List` containing all the `MdmMeasure` objects of the `MdmMeasureDimension`.

    <!-- -->

    - #### addMeasure

          public void addMeasure(MdmMeasure measure)

      Adds an `MdmMeasure` to the `MdmMeasureDimension`.
      Parameters:
      `measure` - The `MdmMeasure` to add to the `MdmMeasureDimension`.

    <!-- -->

    - #### removeMeasure

          public void removeMeasure(MdmMeasure measure)

      Removes an `MdmMeasure` from the `MdmMeasureDimension`.
      Parameters:
      `measure` - The `MdmMeasure` to remove.

    <!-- -->

    - #### createCustomMeasure

          public MdmMeasure createCustomMeasure(java.lang.String name,
                                                Source source,
                                                int precedence)

      Creates a custom `MdmMeasure`.
      Parameters:
      `name` - A `String` that contains a name for the custom `MdmMeasure`.

      `source` - A `Source` that specifies the values of the custom measure.

      `precedence` - An integer that specifies the precedence for the `MdmMeasure`.

    <!-- -->

    - #### createCustomMeasure

          public MdmMeasure createCustomMeasure(java.lang.String name,
                                                MdmSchema schema,
                                                Source source,
                                                int precedence)

      Creates a custom `MdmMeasure` for the specified `MdmSchema`.
      Parameters:
      `name` - A `String` that contains a name for the custom `MdmMeasure`.

      `schema` - The `MdmSchema` to which you want the custom measure to belong.

      `source` - A `Source` that specifies the values of the custom measure.

      `precedence` - An integer that specifies the precedence for the `MdmMeasure`.

    <!-- -->

    - #### getCube

          public final MdmCube getCube()

      Gets the `MdmCube` that is associated with this `MdmMeasureDimension`.
      Returns:
      The `MdmCube` associated with this `MdmMeasureDimension`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmMeasure.md)
- [Next Class](MdmMeasureModel.md)

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
