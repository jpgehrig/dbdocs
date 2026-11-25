Skip navigation links

- [Overview](../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Package](../package-summary.md)
- [Next Package](../mapping/package-summary.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

# Package oracle.olapi.metadata.deployment

Contains classes that specify the deployment of a logical OLAP model as relational OLAP (ROLAP) objects or as analytic workspace (AW) objects.

See: Description

- **Class Summary**

  | Class                                                                     | Description                                                                                                                                                        |
  |---------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AW](AW.md)                                                               | A metadata object that represents an Oracle OLAP analytic workspace.                                                                                               |
  | [AWAttributeOrganization](AWAttributeOrganization.md)                     | A metadata object that represents the organization of an `MdmAttribute` for an `AWPrimaryDimensionOrganization`.                                                   |
  | [AWCubeOrganization](AWCubeOrganization.md)                               | A `CubeOrganization` for an analytic workspace.                                                                                                                    |
  | [AWPrimaryDimensionOrganization](AWPrimaryDimensionOrganization.md)       | A `PrimaryDimensionOrganization` for an analytic workspace.                                                                                                        |
  | [CubeOrganization](CubeOrganization.md)                                   | The base class for a metadata object that represents the organization of an `MdmCube` as an analytic workspace (AW) object or as a relational OLAP (Rolap) object. |
  | [MVCreationOptions](MVCreationOptions.md)                                 | A `BaseMetadataObject` that contains options that Oracle OLAP uses when it creates a materialized view (MV) for an analytic workspace cube or dimension.           |
  | [PrimaryDimensionOrganization](PrimaryDimensionOrganization.md)           | A metadata object that represents the organization of an `MdmPrimaryDimension` as a relational OLAP (Rolap) object or as an analytic workspace (AW) object.        |
  | [RolapCubeOrganization](RolapCubeOrganization.md)                         | A `CubeOrganization` for a relational deployment of an `MdmCube`.                                                                                                  |
  | [RolapPrimaryDimensionOrganization](RolapPrimaryDimensionOrganization.md) | A `PrimaryDimensionOrganization` for a relational deployment of an `MdmPrimaryDimension`.                                                                          |
  | [SecondaryPartitionLevel](SecondaryPartitionLevel.md)                     | A `BaseMetadataObject` that represents a secondary partitioning level for an `AWCubeOrganization`.                                                                 |

- **Exception Summary**

  | Exception                                     | Description                                                         |
  |-----------------------------------------------|---------------------------------------------------------------------|
  | [DeploymentException](DeploymentException.md) | Indicates that the deployment specified for an object is not valid. |

## Package oracle.olapi.metadata.deployment Description

Contains classes that specify the deployment of a logical OLAP model as relational OLAP (ROLAP) objects or as analytic workspace (AW) objects. An application can deploy an instance of an `MdmCube` or an `MdmPrimaryDimension` in either an AW or a Rolap organization.

An application could create two instances of an `MdmCube` and associate one with an AW organization and the other with a Rolap organization. However, all associated metadata objects must have the same type of organization. For example, if an `MdmCube` has an `AWCubeOrganization`, then the `MdmPrimaryDimension` objects that dimension the `MdmMeasure` objects of the `MdmCube` must have associated `AWPrimaryDimensionOrganization` objects.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Package](../package-summary.md)
- [Next Package](../mapping/package-summary.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)
