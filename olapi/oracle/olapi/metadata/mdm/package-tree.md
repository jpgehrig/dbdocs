Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev](../mapping/package-tree.md)
-

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

# Hierarchy For Package oracle.olapi.metadata.mdm

Package Hierarchies:

- [All Packages](../../../../overview-tree.md)

## Class Hierarchy

- java.lang.Object
  - oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md) (implements oracle.olapi.metadata.[MetadataObject](../MetadataObject.md))
    - oracle.olapi.metadata.mdm.[MdmDescription](MdmDescription.md)
    - oracle.olapi.metadata.[PublicMetadataObject](../PublicMetadataObject.md)
      - oracle.olapi.metadata.mdm.[MdmMetadataProperty](MdmMetadataProperty.md)
      - oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)
        - oracle.olapi.metadata.mdm.[MdmAssignment](MdmAssignment.md)
        - oracle.olapi.metadata.mdm.[MdmCustomMember](MdmCustomMember.md)
        - oracle.olapi.metadata.mdm.[MdmDimensionality](MdmDimensionality.md) (implements oracle.olapi.metadata.mdm.[MdmViewColumnOwner](MdmViewColumnOwner.md))
        - oracle.olapi.metadata.mdm.[MdmModel](MdmModel.md) (implements oracle.olapi.data.source.[Model](../../data/source/Model.md))
          - oracle.olapi.metadata.mdm.[MdmDimensionCalculationModel](MdmDimensionCalculationModel.md)
        - oracle.olapi.metadata.mdm.[MdmNamedBuildProcess](MdmNamedBuildProcess.md)
        - oracle.olapi.metadata.mdm.[MdmSchema](MdmSchema.md)
          - oracle.olapi.metadata.mdm.[MdmDatabaseSchema](MdmDatabaseSchema.md)
          - oracle.olapi.metadata.mdm.[MdmOrganizationalSchema](MdmOrganizationalSchema.md)
          - oracle.olapi.metadata.mdm.[MdmRootSchema](MdmRootSchema.md)
        - oracle.olapi.metadata.mdm.[MdmSource](MdmSource.md)
          - oracle.olapi.metadata.mdm.[MdmColumn](MdmColumn.md) (implements oracle.olapi.metadata.mdm.[MdmQueryColumn](MdmQueryColumn.md))
          - oracle.olapi.metadata.mdm.[MdmDimension](MdmDimension.md)
            - oracle.olapi.metadata.mdm.[MdmPrimaryDimension](MdmPrimaryDimension.md) (implements oracle.olapi.syntax.[Buildable](../../syntax/Buildable.md), oracle.olapi.metadata.mdm.[MdmMemberListMapOwner](MdmMemberListMapOwner.md), oracle.olapi.metadata.mdm.[MdmQuery](MdmQuery.md), oracle.olapi.metadata.mdm.[MdmViewColumnOwner](MdmViewColumnOwner.md))
              - oracle.olapi.metadata.mdm.[MdmMeasureDimension](MdmMeasureDimension.md)
              - oracle.olapi.metadata.mdm.[MdmStandardDimension](MdmStandardDimension.md)
              - oracle.olapi.metadata.mdm.[MdmTimeDimension](MdmTimeDimension.md)
            - oracle.olapi.metadata.mdm.[MdmSubDimension](MdmSubDimension.md)
              - oracle.olapi.metadata.mdm.[MdmDimensionLevel](MdmDimensionLevel.md) (implements oracle.olapi.metadata.mdm.[MdmMemberListMapOwner](MdmMemberListMapOwner.md), oracle.olapi.metadata.mdm.[MdmViewColumnOwner](MdmViewColumnOwner.md))
              - oracle.olapi.metadata.mdm.[MdmHierarchy](MdmHierarchy.md) (implements oracle.olapi.metadata.mdm.[MdmQuery](MdmQuery.md), oracle.olapi.metadata.mdm.[MdmViewColumnOwner](MdmViewColumnOwner.md))
                - oracle.olapi.metadata.mdm.[MdmLevelHierarchy](MdmLevelHierarchy.md)
                - oracle.olapi.metadata.mdm.[MdmValueHierarchy](MdmValueHierarchy.md)
              - oracle.olapi.metadata.mdm.[MdmHierarchyLevel](MdmHierarchyLevel.md)
                - oracle.olapi.metadata.mdm.[MdmLevel](MdmLevel.md)
          - oracle.olapi.metadata.mdm.[MdmDimensionedObject](MdmDimensionedObject.md)
            - oracle.olapi.metadata.mdm.[MdmAttribute](MdmAttribute.md) (implements oracle.olapi.metadata.mdm.[MdmQueryColumn](MdmQueryColumn.md))
              - oracle.olapi.metadata.mdm.[MdmMultiValuedAttribute](MdmMultiValuedAttribute.md)
                - oracle.olapi.metadata.mdm.[MdmMultiValuedDerivedAttribute](MdmMultiValuedDerivedAttribute.md)
              - oracle.olapi.metadata.mdm.[MdmSingleValuedAttribute](MdmSingleValuedAttribute.md)
                - oracle.olapi.metadata.mdm.[MdmBaseAttribute](MdmBaseAttribute.md) (implements oracle.olapi.metadata.mdm.[MdmViewColumnOwner](MdmViewColumnOwner.md))
                - oracle.olapi.metadata.mdm.[MdmDerivedAttribute](MdmDerivedAttribute.md)
            - oracle.olapi.metadata.mdm.[MdmCube](MdmCube.md) (implements oracle.olapi.syntax.[Buildable](../../syntax/Buildable.md), oracle.olapi.metadata.mdm.[MdmQuery](MdmQuery.md))
            - oracle.olapi.metadata.mdm.[MdmMeasure](MdmMeasure.md) (implements oracle.olapi.metadata.mdm.[MdmMember](MdmMember.md), oracle.olapi.metadata.mdm.[MdmQueryColumn](MdmQueryColumn.md), oracle.olapi.metadata.mdm.[MdmViewColumnOwner](MdmViewColumnOwner.md))
              - oracle.olapi.metadata.mdm.[MdmBaseMeasure](MdmBaseMeasure.md)
              - oracle.olapi.metadata.mdm.[MdmDerivedMeasure](MdmDerivedMeasure.md)
          - oracle.olapi.metadata.mdm.[MdmStandardMember](MdmStandardMember.md) (implements oracle.olapi.metadata.mdm.[MdmMember](MdmMember.md))
          - oracle.olapi.metadata.mdm.[MdmTable](MdmTable.md) (implements oracle.olapi.metadata.mdm.[MdmQuery](MdmQuery.md))
          - oracle.olapi.metadata.mdm.[MdmTimeMember](MdmTimeMember.md) (implements oracle.olapi.metadata.mdm.[MdmMember](MdmMember.md))
  - oracle.olapi.metadata.[BaseMetadataProvider](../BaseMetadataProvider.md)
    - oracle.olapi.metadata.mdm.[MdmMetadataProvider](MdmMetadataProvider.md) (implements oracle.olapi.metadata.[MetadataProvider](../MetadataProvider.md))
  - oracle.olapi.metadata.mdm.[MdmBaseObjectVisitor](MdmBaseObjectVisitor.md) (implements oracle.olapi.metadata.mdm.[Mdm11_2_ObjectVisitor](Mdm11_2_ObjectVisitor.md))
  - oracle.olapi.metadata.mdm.[MdmDescriptionType](MdmDescriptionType.md)
  - oracle.olapi.metadata.mdm.[MdmDimensionMemberInfo](MdmDimensionMemberInfo.md)
  - oracle.olapi.metadata.mdm.[MdmViewColumn](MdmViewColumn.md) (implements oracle.olapi.metadata.mdm.[MdmQueryColumn](MdmQueryColumn.md))
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - java.lang.RuntimeException
        - oracle.olapi.metadata.mdm.[MdmInvalidValueException](MdmInvalidValueException.md)
- oracle.olapi.metadata.mdm.[MdmAttributeModel](MdmAttributeModel.md)
- oracle.olapi.metadata.mdm.[MdmMeasureModel](MdmMeasureModel.md)

## Interface Hierarchy

- oracle.olapi.metadata.mdm.[MdmMember](MdmMember.md)
- oracle.olapi.metadata.mdm.[MdmMemberListMapOwner](MdmMemberListMapOwner.md)
- oracle.olapi.metadata.mdm.[MdmObjectVisitor](MdmObjectVisitor.md)
  - oracle.olapi.metadata.mdm.[Mdm10_1_0_3_ObjectVisitor](Mdm10_1_0_3_ObjectVisitor.md)
    - oracle.olapi.metadata.mdm.[Mdm11_ObjectVisitor](Mdm11_ObjectVisitor.md)
      - oracle.olapi.metadata.mdm.[Mdm11_2_ObjectVisitor](Mdm11_2_ObjectVisitor.md)
- oracle.olapi.metadata.mdm.[MdmQuery](MdmQuery.md)
- oracle.olapi.metadata.mdm.[MdmQueryColumn](MdmQueryColumn.md)
- oracle.olapi.metadata.mdm.[MdmViewColumnOwner](MdmViewColumnOwner.md)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev](../mapping/package-tree.md)
-

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)
