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

- [Prev Class](ObjectMap.md)
- [Next Class](SolvedValueHierarchyMap.md)

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

## Class SolvedHierarchyMap

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mapping.ObjectMap](ObjectMap.md)

      - - [oracle.olapi.metadata.mapping.DimensionMap](DimensionMap.md)

        - - oracle.olapi.metadata.mapping.SolvedHierarchyMap

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [SolvedValueHierarchyMap](SolvedValueHierarchyMap.md)

  ------------------------------------------------------------------------



      public abstract class SolvedHierarchyMap
      extends DimensionMap

  A `DimensionMap` that maps an `MdmHierarchy` to a data source.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                          | Method and Description                                                                                                                                                                      |
    |--------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Expression`](../../syntax/Expression.md) | `getParentKeyExpression``()`<br>Gets the `Expression` that identifies the column of the relational table that identifies the parents of the members of the hierarchy.                       |
    | `void`                                     | `setParentKeyExpression``(`[`Expression`](../../syntax/Expression.md)` input)`<br>Specifies the column of the relational table that identifies the parents of the members of the hierarchy. |

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

<!-- -->

- - ### Method Detail

    - #### setParentKeyExpression

          public final void setParentKeyExpression(Expression input)

      Specifies the column of the relational table that identifies the parents of the members of the hierarchy.
      Parameters:
      `input` - An `Expression` that identifies the column that contains the parents of the hierarchy members.

    <!-- -->

    - #### getParentKeyExpression

          public final Expression getParentKeyExpression()

      Gets the `Expression` that identifies the column of the relational table that identifies the parents of the members of the hierarchy.
      Returns:
      An `Expression` that identifies the column that contains the parents of the hierarchy members.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](ObjectMap.md)
- [Next Class](SolvedValueHierarchyMap.md)

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
