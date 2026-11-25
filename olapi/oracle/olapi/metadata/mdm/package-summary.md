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

- [Prev Package](../mapping/package-summary.md)
- [Next Package](../../resource/package-summary.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

# Package oracle.olapi.metadata.mdm

Contains classes that represent data supporting the multidimensional model (MDM) for metadata.

See: Description

- **Interface Summary**

  | Interface                                                 | Description                                                                                                                                                    |
  |-----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [Mdm10_1_0_3_ObjectVisitor](Mdm10_1_0_3_ObjectVisitor.md) | An `MdmObjectVisitor` that has methods for visiting classes that are added to the OLAP API in release 10.1.0.3 of Oracle Database.                             |
  | [Mdm11_2_ObjectVisitor](Mdm11_2_ObjectVisitor.md)         | An extension of the `MdmObject` visitor interfaces that has methods for visiting classes that the Oracle OLAP Java API adds in Oracle 11*g*, Release 2 (11.2). |
  | [Mdm11_ObjectVisitor](Mdm11_ObjectVisitor.md)             | An extension of the `MdmObject` visitor interfaces that has methods for visiting classes that the Oracle OLAP Java API adds in Oracle 11*g*, Release 1 (11.1). |
  | [MdmMember](MdmMember.md)                                 | An interface for a custom member of an `MdmPrimaryDimension`.                                                                                                  |
  | [MdmMemberListMapOwner](MdmMemberListMapOwner.md)         | An interface for an object that owns a `MemberListMap`.                                                                                                        |
  | [MdmObjectVisitor](MdmObjectVisitor.md)                   | A visitor object that can execute operations on some of the classes in the `MdmObject` class hierarchy.                                                        |
  | [MdmQuery](MdmQuery.md)                                   | An interface for MDM objects that can have an associated `Query` object.                                                                                       |
  | [MdmQueryColumn](MdmQueryColumn.md)                       | An interface for an object that represents a column of a table or view that is associated with an `MdmQuery`.                                                  |
  | [MdmViewColumnOwner](MdmViewColumnOwner.md)               | A marker interface for objects that can have an associated `MdmViewColumn`.                                                                                    |

- **Class Summary**

  | Class                                                               | Description                                                                                                                                                                                          |
  |---------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [MdmAssignment](MdmAssignment.md)                                   | An object that represents an expression, the value of which is assigned as a measure value for a dimension member as specified by an `MdmModel`.                                                     |
  | [MdmAttribute](MdmAttribute.md)                                     | The abstract base class for an `MdmDimensionedObject` that represents one or more characteristic of the members of an `MdmDimension`.                                                                |
  | [MdmAttributeModel](MdmAttributeModel.md)                           | An `MdmDimensionedObjectModel` that represents an `MdmAttribute`.                                                                                                                                    |
  | [MdmBaseAttribute](MdmBaseAttribute.md)                             | An `MdmSingleValuedAttribute` that is typically mapped to one or more columns of a relational table in the database.                                                                                 |
  | [MdmBaseMeasure](MdmBaseMeasure.md)                                 | An `MdmMeasure` that is mapped to a persistent physical storage structure.                                                                                                                           |
  | [MdmBaseObjectVisitor](MdmBaseObjectVisitor.md)                     | An implementation of the `MdmObjectVisitor` interface that adds methods for visiting more classes in the `MdmObject` class hierarchy.                                                                |
  | [MdmColumn](MdmColumn.md)                                           | An `MdmSource` that represents a column of a table in a relational database.                                                                                                                         |
  | [MdmCube](MdmCube.md)                                               | An `MdmDimensionedObject` that represents a logical organization of `MdmMeasure` objects that have the same dimensionality.                                                                          |
  | [MdmCustomMember](MdmCustomMember.md)                               | An object that represents a custom member of an `MdmPrimaryDimension`.                                                                                                                               |
  | [MdmDatabaseSchema](MdmDatabaseSchema.md)                           | An `MdmSchema` that represents a relational database schema.                                                                                                                                         |
  | [MdmDerivedAttribute](MdmDerivedAttribute.md)                       | An `MdmSingleValuedAttribute` that has values that Oracle OLAP automatically generates, such as the parent attribute for an `MdmHierarchy` and the level depth attribute for an `MdmLevelHierarchy`. |
  | [MdmDerivedMeasure](MdmDerivedMeasure.md)                           | An `MdmMeasure` that has values that Oracle OLAP derives from an `Expression`.                                                                                                                       |
  | [MdmDescription](MdmDescription.md)                                 | A `BaseMetadataObject` that represents a description for an `MdmObject`.                                                                                                                             |
  | [MdmDescriptionType](MdmDescriptionType.md)                         | Represents a type of description for an `MdmDescription`.                                                                                                                                            |
  | [MdmDimension](MdmDimension.md)                                     | An `MdmSource` that represents an OLAP dimension.                                                                                                                                                    |
  | [MdmDimensionality](MdmDimensionality.md)                           | An `MdmObject` that associates an `MdmPrimaryDimension` with an `MdmDimensionedObject`.                                                                                                              |
  | [MdmDimensionCalculationModel](MdmDimensionCalculationModel.md)     | An `MdmModel` that is associated with an `MdmPrimaryDimension`.                                                                                                                                      |
  | [MdmDimensionedObject](MdmDimensionedObject.md)                     | An `MdmSource` that represents a set of data that is organized by one or more `MdmDimension` objects.                                                                                                |
  | [MdmDimensionLevel](MdmDimensionLevel.md)                           | A component of an `MdmPrimaryDimension` that represents a subset of members of the dimension.                                                                                                        |
  | [MdmDimensionMemberInfo](MdmDimensionMemberInfo.md)                 | Provides information about a member of an `MdmHierarchy`.                                                                                                                                            |
  | [MdmHierarchy](MdmHierarchy.md)                                     | An `MdmSubDimension` that represents members of an Oracle OLAP dimension that are organized either hierarchically or nonhierarchically.                                                              |
  | [MdmHierarchyLevel](MdmHierarchyLevel.md)                           | An `MdmSubDimension` whose members comprise one level of an `MdmLevelHierarchy`.                                                                                                                     |
  | [MdmLevel](MdmLevel.md)                                             | Deprecated<br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmHierarchyLevel`](MdmHierarchyLevel.md).                                                                                           |
  | [MdmLevelHierarchy](MdmLevelHierarchy.md)                           | An `MdmHierarchy` that represents members of an Oracle OLAP dimension that are organized either nonhierarchically or hierarchically by levels.                                                       |
  | [MdmMeasure](MdmMeasure.md)                                         | An `MdmDimensionedObject` that represents a set of data to use in analytical processing.                                                                                                             |
  | [MdmMeasureDimension](MdmMeasureDimension.md)                       | An `MdmPrimaryDimension` with members that are `MdmMeasure` objects.                                                                                                                                 |
  | [MdmMeasureModel](MdmMeasureModel.md)                               | An `MdmDimensionedObjectModel` that represents an `MdmMeasure`.                                                                                                                                      |
  | [MdmMetadataProperty](MdmMetadataProperty.md)                       |                                                                                                                                                                                                      |
  | [MdmMetadataProvider](MdmMetadataProvider.md)                       | An object that gives access to Oracle OLAP metadata objects.                                                                                                                                         |
  | [MdmModel](MdmModel.md)                                             | A `Model` that assigns values for `MdmDimension` members.                                                                                                                                            |
  | [MdmMultiValuedAttribute](MdmMultiValuedAttribute.md)               | An abstract base class for `MdmAttribute` objects that can relate more than a single value to a value of an associated `MdmPrimaryDimension`.                                                        |
  | [MdmMultiValuedDerivedAttribute](MdmMultiValuedDerivedAttribute.md) | An `MdmMultiValuedAttribute` that can relate more than a single derived value for a value of an associated `MdmPrimaryDimension`.                                                                    |
  | [MdmNamedBuildProcess](MdmNamedBuildProcess.md)                     | An `MdmObject` that represents a named `oracle.olapi.syntax.BuildProcess` for an `MdmDatabaseSchema`.                                                                                                |
  | [MdmObject](MdmObject.md)                                           | An object that describes a particular set of data, such as a measure of product unit prices or a dimension of time values.                                                                           |
  | [MdmOrganizationalSchema](MdmOrganizationalSchema.md)               | An `MdmSchema` that organizes `MdmCube` and other `MdmObject` objects, including other `MdmOrganizationalSchema` objects, that are related by informational content.                                 |
  | [MdmPrimaryDimension](MdmPrimaryDimension.md)                       | The base class for objects that represent an Oracle OLAP dimension.                                                                                                                                  |
  | [MdmRootSchema](MdmRootSchema.md)                                   | The top-level `MdmSchema` of a `MdmMetadataProvider`.                                                                                                                                                |
  | [MdmSchema](MdmSchema.md)                                           | A container for `MdmCube`, `MdmPrimaryDimension`, `MdmTable`, and other metadata objects.                                                                                                            |
  | [MdmSingleValuedAttribute](MdmSingleValuedAttribute.md)             | An abstract base class for `MdmAttribute` objects that relate a single value to a value of an associated `MdmPrimaryDimension`.                                                                      |
  | [MdmSource](MdmSource.md)                                           | An `MdmObject` that represents a measure, dimension, or other set of data (such as an attribute).                                                                                                    |
  | [MdmStandardDimension](MdmStandardDimension.md)                     | An `MdmPrimaryDimension` that represents most types of metadata for Oracle OLAP dimensions, such as dimensions for products, customers, distribution channels, and so on.                            |
  | [MdmStandardMember](MdmStandardMember.md)                           | An object that represents a custom member of an `MdmStandardDimension`.                                                                                                                              |
  | [MdmSubDimension](MdmSubDimension.md)                               | A component of an `MdmPrimaryDimension`.                                                                                                                                                             |
  | [MdmTable](MdmTable.md)                                             | An `MdmSource` that represents a table in a relational database.                                                                                                                                     |
  | [MdmTimeDimension](MdmTimeDimension.md)                             | An `MdmPrimaryDimension` that represents an Oracle OLAP dimension of time periods.                                                                                                                   |
  | [MdmTimeMember](MdmTimeMember.md)                                   | An object that represents a custom member of an `MdmTimeDimension`.                                                                                                                                  |
  | [MdmValueHierarchy](MdmValueHierarchy.md)                           | An `MdmHierarchy` that represents members of an Oracle OLAP dimension that are organized hierarchically by values rather than by levels.                                                             |
  | [MdmViewColumn](MdmViewColumn.md)                                   | An object that represents a column in a view in an Oracle Database.                                                                                                                                  |

- **Exception Summary**

  | Exception                                               | Description                                                                                   |
  |---------------------------------------------------------|-----------------------------------------------------------------------------------------------|
  | [MdmInvalidValueException](MdmInvalidValueException.md) | Indicates that the value specified by the operation that generated this exception is invalid. |

## Package oracle.olapi.metadata.mdm Description

Contains classes that represent data supporting the multidimensional model (MDM) for metadata.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Package](../mapping/package-summary.md)
- [Next Package](../../resource/package-summary.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)
