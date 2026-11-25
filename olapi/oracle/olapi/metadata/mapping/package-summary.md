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

- [Prev Package](../deployment/package-summary.md)
- [Next Package](../mdm/package-summary.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

# Package oracle.olapi.metadata.mapping

Contains classes that map the `MdmObject` objects of a logical OLAP metadata model to physical storage structures in an Oracle Database instance.

See: Description

- **Class Summary**

  | Class                                                 | Description                                                                                                                             |
  |-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
  | [AttributeMap](AttributeMap.md)                       | A `ValueMap` that maps an `MdmAttribute` for an `MdmDimension` to an `Expression`.                                                      |
  | [CubeDimensionalityMap](CubeDimensionalityMap.md)     | Associates a `CubeMap` with `MdmDimension` and `MdmDimensionality` objects.                                                             |
  | [CubeMap](CubeMap.md)                                 | An `ObjectMap` that maps an `MdmCube` to an `Expression`.                                                                               |
  | [DimensionMap](DimensionMap.md)                       | The abstract base class for an object that maps an `MdmDimension` to a relational data source.                                          |
  | [HierarchyLevelMap](HierarchyLevelMap.md)             | A `DimensionMap` that maps an `MdmHierarchyLevel` to a data source.                                                                     |
  | [MeasureMap](MeasureMap.md)                           | A `ValueMap` that maps an `MdmMeasure` to an `Expression`.                                                                              |
  | [MemberListMap](MemberListMap.md)                     | A `DimensionMap` that maps an `MdmPrimaryDimension` or an `MdmDimensionLevel` to a data source, such as a column in a relational table. |
  | [ObjectMap](ObjectMap.md)                             | The base class for an object that maps an `MdmObject` to physical storage structures.                                                   |
  | [SolvedHierarchyMap](SolvedHierarchyMap.md)           | A `DimensionMap` that maps an `MdmHierarchy` to a data source.                                                                          |
  | [SolvedValueHierarchyMap](SolvedValueHierarchyMap.md) | A `SolvedHierarchyMap` for an `MdmValueHierarchy`.                                                                                      |
  | [ValueMap](ValueMap.md)                               | An abstract `ObjectMap` that maps an `MdmDimensionedObject` to relational source data.                                                  |

## Package oracle.olapi.metadata.mapping Description

Contains classes that map the `MdmObject` objects of a logical OLAP metadata model to physical storage structures in an Oracle Database instance.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Package](../deployment/package-summary.md)
- [Next Package](../mdm/package-summary.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)
