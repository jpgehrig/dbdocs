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

- [Prev Class](MeasureMap.md)
- [Next Class](ObjectMap.md)

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

oracle.olapi.metadata.mapping

## Class MemberListMap

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mapping.ObjectMap](ObjectMap.md)

      - - [oracle.olapi.metadata.mapping.DimensionMap](DimensionMap.md)

        - - oracle.olapi.metadata.mapping.MemberListMap

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class MemberListMap
      extends DimensionMap

  A `DimensionMap` that maps an `MdmPrimaryDimension` or an `MdmDimensionLevel` to a data source, such as a column in a relational table. You get a `MemberListMap` by calling the `findOrCreateMemberListMap` method of the `MdmPrimaryDimension` or `MdmDimensionLevel`. If you use a `MemberListMap` to map an `MdmPrimaryDimension` or an `MdmDimensionLevel`, then you should not also use a `HierarchyLevelMap` to map an `MdmHierarchyLevel` to the same data source.

<!-- -->

- - ### Method Summary

    - ### Methods inherited from class oracle.olapi.metadata.mapping.[DimensionMap](DimensionMap.md)

      [`addAttributeMap`](DimensionMap.md)`, `[`findOrCreateAttributeMap`](DimensionMap.md)`, `[`findOrCreateAttributeMap`](DimensionMap.md)`, `[`getAttributeMaps`](DimensionMap.md)`, `[`getDimension`](DimensionMap.md)`, `[`getFromClause`](DimensionMap.md)`, `[`getKeyExpression`](DimensionMap.md)`, `[`getQuery`](DimensionMap.md)`, `[`getWhereClause`](DimensionMap.md)`, `[`removeAttributeMap`](DimensionMap.md)`, `[`setDimension`](DimensionMap.md)`, `[`setFromClause`](DimensionMap.md)`, `[`setKeyExpression`](DimensionMap.md)`, `[`setQuery`](DimensionMap.md)`, `[`setWhereClause`](DimensionMap.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mapping.[ObjectMap](ObjectMap.md)

      [`getName`](ObjectMap.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MeasureMap.md)
- [Next Class](ObjectMap.md)

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
