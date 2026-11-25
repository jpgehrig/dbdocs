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

- [Prev Class](MdmColumn.md)
- [Next Class](MdmCustomMember.md)

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

## Class MdmCube

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimensionedObject](MdmDimensionedObject.md)

          - - oracle.olapi.metadata.mdm.MdmCube

<!-- -->

- All Implemented Interfaces:
  [MdmQuery](MdmQuery.md), [MetadataObject](../MetadataObject.md), [Buildable](../../syntax/Buildable.md)

  ------------------------------------------------------------------------



      public class MdmCube
      extends MdmDimensionedObject
      implements MdmQuery, Buildable

  An `MdmDimensionedObject` that represents a logical organization of `MdmMeasure` objects that have the same dimensionality. To get an existing `MdmCube` or to create a new one, use the [`findOrCreateCube`](MdmDatabaseSchema.md) method of an `MdmDatabaseSchema`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                              | Method and Description                                                                                                                                                                                               |
    |--------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                                             | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmCube` method of the `MdmObjectVisitor` and passes that method this `MdmCube` and an `Object`. |
    | `void`                                                                         | `addCubeMap``(`[`CubeMap`](../mapping/CubeMap.md)` map)`<br>Adds a `CubeMap` to the `List` of `CubeMap` objects associated with this `MdmCube`.                                                                      |
    | `void`                                                                         | `addMeasure``(`[`MdmMeasure`](MdmMeasure.md)` value)`<br>Adds an `MdmMeasure` to the `List` of `MdmMeasure` objects that are contained by this `MdmCube`.                                                            |
    | [`CubeMap`](../mapping/CubeMap.md)                                             | `createCubeMap``()`<br>Creates a `CubeMap` for this `MdmCube`.                                                                                                                                                       |
    | [`AWCubeOrganization`](../deployment/AWCubeOrganization.md)                    | `findOrCreateAWCubeOrganization``(`[`AW`](../deployment/AW.md)` aw)`<br>Gets the `AWCubeOrganization` for the `MdmCube` or creates a new `AWCubeOrganization` if one does not already exist.                         |
    | [`MdmBaseMeasure`](MdmBaseMeasure.md)                                          | `findOrCreateBaseMeasure``(java.lang.String publicName)`<br>Gets the specified `MdmBaseMeasure` or, if it does not already exist, creates a new `MdmBaseMeasure` for this `MdmCube`.                                 |
    | [`CubeMap`](../mapping/CubeMap.md)                                             | `findOrCreateCubeMap``(java.lang.String name)`<br>Gets the specified `CubeMap` or, if it does not already exist, creates a new `CubeMap` for this `MdmCube`.                                                         |
    | [`MdmDerivedMeasure`](MdmDerivedMeasure.md)                                    | `findOrCreateDerivedMeasure``(java.lang.String publicName)`<br>Gets the specified `MdmDerivedMeasure` or, if it does not already exist, creates a new `MdmDerivedMeasure` for this `MdmCube`.                        |
    | [`RolapCubeOrganization`](../deployment/RolapCubeOrganization.md)              | `findOrCreateRolapCubeOrganization``()`<br>Gets the `RolapCubeOrganization` for the `MdmCube` or creates a new `RolapCubeOrganization` if one does not already exist.                                                |
    | `MdmCube`                                                                      | `getAggmapCube``()`                                                                                                                                                                                                  |
    | [`ConsistentSolveSpecification`](../../syntax/ConsistentSolveSpecification.md) | `getConsistentSolveSpecification``()`<br>Gets the `ConsistentSolveSpecification` that is associated with this `MdmCube`.                                                                                             |
    | `java.util.List`                                                               | `getCubeMaps``()`<br>Gets the `CubeMap` objects that are associated with this `MdmCube`.                                                                                                                             |
    | [`MdmMeasure`](MdmMeasure.md)                                                  | `getDefaultMeasure``()`<br>Gets the default measure of the `MdmCube`.                                                                                                                                                |
    | `java.lang.String`                                                             | `getETViewName``()`<br>Gets the name of the ET (embedded totals) view for this `MdmCube`.                                                                                                                            |
    | `java.lang.String`                                                             | `getLoopDomainOverride``()`                                                                                                                                                                                          |
    | [`MdmMeasure`](MdmMeasure.md)                                                  | `getMeasure``(java.lang.String name)`<br>Gets the specified `MdmMeasure` that is associated with this `MdmCube`.                                                                                                     |
    | `java.util.List<`[`MdmMeasure`](MdmMeasure.md)`>`                              | `getMeasures``()`<br>Gets the `MdmMeasure` objects that are associated with this `MdmCube`.                                                                                                                          |
    | `java.lang.String`                                                             | `getNamespace``()`<br>Gets the namespace of a legacy 10*g* object.                                                                                                                                                   |
    | [`CubeOrganization`](../deployment/CubeOrganization.md)                        | `getOrganization``()`<br>Gets the `CubeOrganization` associated with this `MdmCube`.                                                                                                                                 |
    | [`MdmDatabaseSchema`](MdmDatabaseSchema.md)                                    | `getOwner``()`<br>Gets the `MdmDatabaseSchema` that owns this `MdmCube`.                                                                                                                                             |
    | `java.util.List`                                                               | `getPersistentLanguages``()`<br>Gets the languages in which descriptions are available for this `MdmCube` and for the objects contained by it.                                                                       |
    | [`Query`](../../syntax/Query.md)                                               | `getQuery``()`<br>Gets the `Query` that is associated with this `MdmCube`.                                                                                                                                           |
    | [`MdmQueryColumn`](MdmQueryColumn.md)                                          | `getQueryColumn``(java.lang.String name)`<br>Gets the specified `MdmQueryColumn`.                                                                                                                                    |
    | `java.util.List<`[`MdmQueryColumn`](MdmQueryColumn.md)`>`                      | `getQueryColumns``()`<br>Gets the `MdmQueryColumn` objects that are associated with this `MdmCube`.                                                                                                                  |
    | `java.lang.String`                                                             | `getQueryName``()`<br>Gets the identifier of this `MdmCube`.                                                                                                                                                         |
    | [`MetadataObject`](../MetadataObject.md)                                       | `getType``()`<br>Gets the OLAP Java API Value data type.                                                                                                                                                             |
    | `java.lang.String`                                                             | `getViewName``()`<br>Deprecated. <br>As of Oracle 12c, Release 1 (12.1); replaced by `getETViewName`.                                                                                                                |
    | `void`                                                                         | `removeCubeMap``(`[`CubeMap`](../mapping/CubeMap.md)` map)`<br>Removes a `CubeMap` from the `List` of `CubeMap` objects associated with this `MdmCube`.                                                              |
    | `void`                                                                         | `removeMeasure``(`[`MdmMeasure`](MdmMeasure.md)` value)`<br>Removes an `MdmMeasure` from the `List` of `MdmMeasure` objects that are contained by this `MdmCube`.                                                    |
    | `void`                                                                         | `setAggmapCube``(MdmCube cube)`                                                                                                                                                                                      |
    | `void`                                                                         | `setConsistentSolveSpecification``(`[`ConsistentSolveSpecification`](../../syntax/ConsistentSolveSpecification.md)` input)`<br>Specifies a `ConsistentSolveSpecification` to associate with this `MdmCube`.          |
    | `void`                                                                         | `setDefaultMeasure``(`[`MdmMeasure`](MdmMeasure.md)` measure)`<br>Specifies a default measure for the `MdmCube`.                                                                                                     |
    | `void`                                                                         | `setETViewName``(java.lang.String name)`<br>Specifies a name for the ET (embedded totals) view for this `MdmCube`.                                                                                                   |
    | `void`                                                                         | `setLoopDomainOverride``(java.lang.String ld)`                                                                                                                                                                       |
    | `void`                                                                         | `setOwner``(`[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` owner)`<br>Specifies an `MdmDatabaseSchema` as the owner of this `MdmCube`.                                                                                |
    | `void`                                                                         | `setViewName``(java.lang.String name)`<br>Deprecated. <br>As of Oracle 12c, Release 1 (12.1); replaced by `setETViewName`.                                                                                           |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmDimensionedObject](MdmDimensionedObject.md)

      [`addDimension`](MdmDimensionedObject.md)`, `[`addDimensionality`](MdmDimensionedObject.md)`, `[`getDimensionality`](MdmDimensionedObject.md)`, `[`getDimensions`](MdmDimensionedObject.md)`, `[`isBooleanValued`](MdmDimensionedObject.md)`, `[`removeDimensionality`](MdmDimensionedObject.md)`, `[`setBooleanValued`](MdmDimensionedObject.md)

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

      Calls the `visitMdmCube` method of the `MdmObjectVisitor` and passes that method this `MdmCube` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor` that implements the `Mdm11_ObjectVisitor` interface.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmCube` method.

    <!-- -->

    - #### getMeasure

          public final MdmMeasure getMeasure(java.lang.String name)

      Gets the specified `MdmMeasure` that is associated with this `MdmCube`.
      Parameters:
      `name` - A `String` that contains the name of an `MdmMeasure` associated with this `MdmCube`.

      Returns:
      The `MdmMeasure` that has the specified name. If the `MdmMeasure` is not associated with the `MdmCube`, then this method returns `null`.

    <!-- -->

    - #### getMeasures

          public final java.util.List<MdmMeasure> getMeasures()

      Gets the `MdmMeasure` objects that are associated with this `MdmCube`.
      Returns:
      A `List` of the `MdmMeasure` associated with this `MdmCube`.

    <!-- -->

    - #### addMeasure

          public void addMeasure(MdmMeasure value)

      Adds an `MdmMeasure` to the `List` of `MdmMeasure` objects that are contained by this `MdmCube`.
      Parameters:
      `value` - The `MdmMeasure` to add to this `MdmCube`.

    <!-- -->

    - #### removeMeasure

          public void removeMeasure(MdmMeasure value)

      Removes an `MdmMeasure` from the `List` of `MdmMeasure` objects that are contained by this `MdmCube`.
      Parameters:
      `value` - The `MdmMeasure` to remove from this `MdmCube`.

    <!-- -->

    - #### setDefaultMeasure

          public void setDefaultMeasure(MdmMeasure measure)

      Specifies a default measure for the `MdmCube`.
      Parameters:
      `measure` - The `MdmMeasure` to be the default measure for the `MdmCube`.

    <!-- -->

    - #### getDefaultMeasure

          public MdmMeasure getDefaultMeasure()

      Gets the default measure of the `MdmCube`.
      Returns:
      The `MdmMeasure` that is the default measure of the `MdmCube`.

    <!-- -->

    - #### getOwner

          public final MdmDatabaseSchema getOwner()

      Gets the `MdmDatabaseSchema` that owns this `MdmCube`.
      Overrides:
      [`getOwner`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      The `MdmDatabaseSchema` that owns this `MdmCube`.

    <!-- -->

    - #### setOwner

          public final void setOwner(MdmDatabaseSchema owner)

      Specifies an `MdmDatabaseSchema` as the owner of this `MdmCube`.
      Parameters:
      `owner` - The `MdmDatabaseSchema` to specify as the owner of this `MdmCube`.

    <!-- -->

    - #### getNamespace

          public final java.lang.String getNamespace()

      Gets the namespace of a legacy 10*g* object. For information on namespaces, see [Using Namespaces](MdmMetadataProvider.md) in the description of `MdmMetadataProvider`.
      Returns:
      For a legacy 10*g* object, returns a `String` that contains the namespace of the object. For an 11*g* `MdmCube`, returns `null`.

    <!-- -->

    - #### getLoopDomainOverride

          public final java.lang.String getLoopDomainOverride()

    <!-- -->

    - #### setLoopDomainOverride

          public final void setLoopDomainOverride(java.lang.String ld)

    <!-- -->

    - #### getAggmapCube

          public final MdmCube getAggmapCube()

    <!-- -->

    - #### setAggmapCube

          public final void setAggmapCube(MdmCube cube)

    <!-- -->

    - #### getCubeMaps

          public final java.util.List getCubeMaps()

      Gets the `CubeMap` objects that are associated with this `MdmCube`.
      Returns:
      A `List` of the `CubeMap` objects associated with this `MdmCube`.

    <!-- -->

    - #### addCubeMap

          public final void addCubeMap(CubeMap map)

      Adds a `CubeMap` to the `List` of `CubeMap` objects associated with this `MdmCube`.
      Parameters:
      `map` - The `CubeMap` to add to this `MdmCube`.

    <!-- -->

    - #### removeCubeMap

          public final void removeCubeMap(CubeMap map)

      Removes a `CubeMap` from the `List` of `CubeMap` objects associated with this `MdmCube`.
      Parameters:
      `map` - The `CubeMap` to remove from this `MdmCube`.

    <!-- -->

    - #### getOrganization

          public final CubeOrganization getOrganization()

      Gets the `CubeOrganization` associated with this `MdmCube`.
      Returns:
      The `CubeOrganization` for this `MdmCube`.

    <!-- -->

    - #### findOrCreateAWCubeOrganization

          public final AWCubeOrganization findOrCreateAWCubeOrganization(AW aw)

      Gets the `AWCubeOrganization` for the `MdmCube` or creates a new `AWCubeOrganization` if one does not already exist.
      Parameters:
      `aw` - The `AW` object to associate with the `AWCubeOrganization`.

      Returns:
      The new or existing `AWCubeOrganization` for the `MdmCube`.

    <!-- -->

    - #### findOrCreateRolapCubeOrganization

          public final RolapCubeOrganization findOrCreateRolapCubeOrganization()

      Gets the `RolapCubeOrganization` for the `MdmCube` or creates a new `RolapCubeOrganization` if one does not already exist.
      Returns:
      The new or existing `RolapCubeOrganization` for the `MdmCube`.

    <!-- -->

    - #### getConsistentSolveSpecification

          public final ConsistentSolveSpecification getConsistentSolveSpecification()

      Gets the `ConsistentSolveSpecification` that is associated with this `MdmCube`.
      Returns:
      The `ConsistentSolveSpecification` associated with this `MdmCube`.

    <!-- -->

    - #### setConsistentSolveSpecification

          public final void setConsistentSolveSpecification(ConsistentSolveSpecification input)

      Specifies a `ConsistentSolveSpecification` to associate with this `MdmCube`.
      Parameters:
      `input` - The `ConsistentSolveSpecification` to associate with this `MdmCube`.

    <!-- -->

    - #### getViewName

          public final java.lang.String getViewName()

      Deprecated. As of Oracle 12c, Release 1 (12.1); replaced by `getETViewName`.

    <!-- -->

    - #### setViewName

          public final void setViewName(java.lang.String name)

      Deprecated. As of Oracle 12c, Release 1 (12.1); replaced by `setETViewName`.

    <!-- -->

    - #### getETViewName

          public final java.lang.String getETViewName()

      Gets the name of the ET (embedded totals) view for this `MdmCube`.
      Returns:
      A `String` that contains the name of the ET view for the `MdmCube`.

    <!-- -->

    - #### setETViewName

          public final void setETViewName(java.lang.String name)

      Specifies a name for the ET (embedded totals) view for this `MdmCube`. You must commit the root `Transaction` to make the name change permanent.
      Parameters:
      `name` - A `String` that contains a name for the ET view for the `MdmCube`.

    <!-- -->

    - #### getQuery

          public final Query getQuery()

      Gets the `Query` that is associated with this `MdmCube`.
      Specified by:
      [`getQuery`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Returns:
      The `Query` associated with this `MdmCube`.

    <!-- -->

    - #### getQueryColumns

          public final java.util.List<MdmQueryColumn> getQueryColumns()

      Gets the `MdmQueryColumn` objects that are associated with this `MdmCube`.
      Specified by:
      [`getQueryColumns`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Returns:
      A `List` of the `MdmQueryColumn` objects associated with this `MdmCube`.

    <!-- -->

    - #### getQueryName

          public final java.lang.String getQueryName()

      Gets the identifier of this `MdmCube`.
      Specified by:
      [`getQueryName`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Returns:
      A `String` that contains the identifier of this `MdmCube`.

    <!-- -->

    - #### getQueryColumn

          public MdmQueryColumn getQueryColumn(java.lang.String name)

      Gets the specified `MdmQueryColumn`.
      Specified by:
      [`getQueryColumn`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Parameters:
      `name` - A `String` that contains the name of an `MdmQueryColumn`.

      Returns:
      The `MdmQueryColumn` that has the specified name.

    <!-- -->

    - #### getType

          public MetadataObject getType()

      Gets the OLAP Java API Value data type. An `MdmCube` does not have a value, so it does not have a more specific data type.
      Specified by:
      [`getType`](MdmSource.md) in class [`MdmSource`](MdmSource.md)

      Returns:
      A `MetadataObject` that represents the OLAP Java API Value data type.

    <!-- -->

    - #### findOrCreateBaseMeasure

          public MdmBaseMeasure findOrCreateBaseMeasure(java.lang.String publicName)

      Gets the specified `MdmBaseMeasure` or, if it does not already exist, creates a new `MdmBaseMeasure` for this `MdmCube`.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmBaseMeasure` to get or create.

      Returns:
      The specified `MdmBaseMeasure` or a new one with the specified name.

    <!-- -->

    - #### findOrCreateDerivedMeasure

          public MdmDerivedMeasure findOrCreateDerivedMeasure(java.lang.String publicName)

      Gets the specified `MdmDerivedMeasure` or, if it does not already exist, creates a new `MdmDerivedMeasure` for this `MdmCube`.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmDerivedMeasure` to get or create.

      Returns:
      The specified `MdmDerivedMeasure` or a new one with the specified name.

    <!-- -->

    - #### createCubeMap

          public CubeMap createCubeMap()

      Creates a `CubeMap` for this `MdmCube`.
      Returns:
      The `CubeMap` for this `MdmCube`.

    <!-- -->

    - #### findOrCreateCubeMap

          public final CubeMap findOrCreateCubeMap(java.lang.String name)

      Gets the specified `CubeMap` or, if it does not already exist, creates a new `CubeMap` for this `MdmCube`.
      Parameters:
      `name` - A `String` that contains the name of the `CubeMap` to get or create.

      Returns:
      The specified `CubeMap` or a new one with the specified name.

    <!-- -->

    - #### getPersistentLanguages

          public java.util.List getPersistentLanguages()

      Gets the languages in which descriptions are available for this `MdmCube` and for the objects contained by it.
      Returns:
      A `List` of `String` objects that contain the names of NLS languages.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmColumn.md)
- [Next Class](MdmCustomMember.md)

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
