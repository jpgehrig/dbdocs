Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](MetadataModificationException.md)
- [Next Class](MetadataProvider.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.olapi.metadata

## Interface MetadataObject

- All Known Implementing Classes:
  [AttributeMap](mapping/AttributeMap.md), [AW](deployment/AW.md), [AWAttributeOrganization](deployment/AWAttributeOrganization.md), [AWCubeOrganization](deployment/AWCubeOrganization.md), [AWPrimaryDimensionOrganization](deployment/AWPrimaryDimensionOrganization.md), [BaseMetadataObject](BaseMetadataObject.md), [CubeDimensionalityMap](mapping/CubeDimensionalityMap.md), [CubeMap](mapping/CubeMap.md), [CubeOrganization](deployment/CubeOrganization.md), [DimensionMap](mapping/DimensionMap.md), [FundamentalMetadataObject](../data/source/FundamentalMetadataObject.md), [HierarchyLevelMap](mapping/HierarchyLevelMap.md), [MdmAssignment](mdm/MdmAssignment.md), [MdmAttribute](mdm/MdmAttribute.md), [MdmBaseAttribute](mdm/MdmBaseAttribute.md), [MdmBaseMeasure](mdm/MdmBaseMeasure.md), [MdmColumn](mdm/MdmColumn.md), [MdmCube](mdm/MdmCube.md), [MdmCustomMember](mdm/MdmCustomMember.md), [MdmDatabaseSchema](mdm/MdmDatabaseSchema.md), [MdmDerivedAttribute](mdm/MdmDerivedAttribute.md), [MdmDerivedMeasure](mdm/MdmDerivedMeasure.md), [MdmDescription](mdm/MdmDescription.md), [MdmDimension](mdm/MdmDimension.md), [MdmDimensionality](mdm/MdmDimensionality.md), [MdmDimensionCalculationModel](mdm/MdmDimensionCalculationModel.md), [MdmDimensionedObject](mdm/MdmDimensionedObject.md), [MdmDimensionLevel](mdm/MdmDimensionLevel.md), [MdmHierarchy](mdm/MdmHierarchy.md), [MdmHierarchyLevel](mdm/MdmHierarchyLevel.md), [MdmLevel](mdm/MdmLevel.md), [MdmLevelHierarchy](mdm/MdmLevelHierarchy.md), [MdmMeasure](mdm/MdmMeasure.md), [MdmMeasureDimension](mdm/MdmMeasureDimension.md), [MdmMetadataProperty](mdm/MdmMetadataProperty.md), [MdmModel](mdm/MdmModel.md), [MdmMultiValuedAttribute](mdm/MdmMultiValuedAttribute.md), [MdmMultiValuedDerivedAttribute](mdm/MdmMultiValuedDerivedAttribute.md), [MdmNamedBuildProcess](mdm/MdmNamedBuildProcess.md), [MdmObject](mdm/MdmObject.md), [MdmOrganizationalSchema](mdm/MdmOrganizationalSchema.md), [MdmPrimaryDimension](mdm/MdmPrimaryDimension.md), [MdmRootSchema](mdm/MdmRootSchema.md), [MdmSchema](mdm/MdmSchema.md), [MdmSingleValuedAttribute](mdm/MdmSingleValuedAttribute.md), [MdmSource](mdm/MdmSource.md), [MdmStandardDimension](mdm/MdmStandardDimension.md), [MdmStandardMember](mdm/MdmStandardMember.md), [MdmSubDimension](mdm/MdmSubDimension.md), [MdmTable](mdm/MdmTable.md), [MdmTimeDimension](mdm/MdmTimeDimension.md), [MdmTimeMember](mdm/MdmTimeMember.md), [MdmValueHierarchy](mdm/MdmValueHierarchy.md), [MeasureMap](mapping/MeasureMap.md), [MemberListMap](mapping/MemberListMap.md), [MVCreationOptions](deployment/MVCreationOptions.md), [ObjectMap](mapping/ObjectMap.md), [PrimaryDimensionOrganization](deployment/PrimaryDimensionOrganization.md), [PublicMetadataObject](PublicMetadataObject.md), [RolapCubeOrganization](deployment/RolapCubeOrganization.md), [RolapPrimaryDimensionOrganization](deployment/RolapPrimaryDimensionOrganization.md), [SecondaryPartitionLevel](deployment/SecondaryPartitionLevel.md), [SolvedHierarchyMap](mapping/SolvedHierarchyMap.md), [SolvedValueHierarchyMap](mapping/SolvedValueHierarchyMap.md), [ValueMap](mapping/ValueMap.md)

  ------------------------------------------------------------------------



      public interface MetadataObject

  An interface that is implemented by most of the Oracle OLAP metadata objects. A `MetadataObject` has a unique identifier (ID) that persists from one `MetadataProvider` instance to another. Therefore, an application can store the ID for a `MetadataObject` in one session, and then it can use it in a later session. However, if the name or the owner of a metadata object changes, then the ID changes as well and the stored ID is no longer valid.
  This interface is also implemented by the `oracle.olapi.data.source.FundamentalMetadataObject` class. Instances of that class represent fundamental operations such as addition and OLAP Java API fundamental data types such as Integer.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                               |
    |--------------------|----------------------------------------------------------------------|
    | `java.lang.String` | `getID``()`<br>Gets the unique identifier for this `MetadataObject`. |

<!-- -->

- - ### Method Detail

    - #### getID

          java.lang.String getID()

      Gets the unique identifier for this `MetadataObject`.
      Returns:
      A `String` that uniquely identifies this `MetadataObject`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MetadataModificationException.md)
- [Next Class](MetadataProvider.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
