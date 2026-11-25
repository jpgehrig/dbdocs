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

- [Prev Class](CubeMap.md)
- [Next Class](HierarchyLevelMap.md)

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

## Class DimensionMap

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mapping.ObjectMap](ObjectMap.md)

      - - oracle.olapi.metadata.mapping.DimensionMap

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [HierarchyLevelMap](HierarchyLevelMap.md), [MemberListMap](MemberListMap.md), [SolvedHierarchyMap](SolvedHierarchyMap.md)

  ------------------------------------------------------------------------



      public abstract class DimensionMap
      extends ObjectMap

  The abstract base class for an object that maps an `MdmDimension` to a relational data source. The data source is specified by an `Expression` that identifies the key column in the table that contains the dimension members.
  A `DimensionMap` has an associated dimension. A `DimensionMap` can contain one or more `AttributeMap` objects. It has either an associated `Query` or a `FromClause`. It also can have a `Condition` that functions like a `WHERE` clause in a SQL `SELECT` statement.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                          | Method and Description                                                                                                                                                                                                                                                             |
    |--------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                     | `addAttributeMap``(`[`AttributeMap`](AttributeMap.md)` value)`<br>Adds an `AttributeMap` to the `DimensionMap`.                                                                                                                                                                    |
    | [`AttributeMap`](AttributeMap.md)          | `findOrCreateAttributeMap``(`[`MdmBaseAttribute`](../mdm/MdmBaseAttribute.md)` attribute)`<br>Gets the `AttributeMap` for the specified attribute or, if the map does not exist, creates an `AttributeMap` for the attribute.                                                      |
    | [`AttributeMap`](AttributeMap.md)          | `findOrCreateAttributeMap``(`[`MdmBaseAttribute`](../mdm/MdmBaseAttribute.md)` attribute, java.lang.String language)`<br>Gets the `AttributeMap` for the specified attribute and language or, if the map does not exist, creates an `AttributeMap` for the attribute and language. |
    | `java.util.List`                           | `getAttributeMaps``()`<br>Gets the `AttributeMap` objects that are owned by the `DimensionMap`.                                                                                                                                                                                    |
    | [`MdmDimension`](../mdm/MdmDimension.md)   | `getDimension``()`<br>Gets the `MdmDimension` associated with the `DimensionMap`.                                                                                                                                                                                                  |
    | [`FromClause`](../../syntax/FromClause.md) | `getFromClause``()`<br>Gets the `FromClause` associated with the `DimensionMap`.                                                                                                                                                                                                   |
    | [`Expression`](../../syntax/Expression.md) | `getKeyExpression``()`<br>Gets the `Expression` that identifies the primary key column of the relational table for the dimension members.                                                                                                                                          |
    | [`Query`](../../syntax/Query.md)           | `getQuery``()`<br>Gets the `Query` associated with the `DimensionMap`.                                                                                                                                                                                                             |
    | [`Condition`](../../syntax/Condition.md)   | `getWhereClause``()`<br>Gets the `Condition` associated with the `DimensionMap`.                                                                                                                                                                                                   |
    | `void`                                     | `removeAttributeMap``(`[`AttributeMap`](AttributeMap.md)` value)`<br>Removes an `AttributeMap` from the `DimensionMap`.                                                                                                                                                            |
    | `void`                                     | `setDimension``(`[`MdmDimension`](../mdm/MdmDimension.md)` input)`<br>Specifies the `MdmDimension` to associate with the `DimensionMap`.                                                                                                                                           |
    | `void`                                     | `setFromClause``(`[`FromClause`](../../syntax/FromClause.md)` fromClause)`<br>Specifies a `FromClause` to associate with the `DimensionMap`.                                                                                                                                       |
    | `void`                                     | `setKeyExpression``(`[`Expression`](../../syntax/Expression.md)` input)`<br>Specifies the primary key column of the relational table for the dimension members.                                                                                                                    |
    | `void`                                     | `setQuery``(`[`Query`](../../syntax/Query.md)` query)`<br>Specifies a `Query` to associate with this `DimensionMap`.                                                                                                                                                               |
    | `void`                                     | `setWhereClause``(`[`Condition`](../../syntax/Condition.md)` whereClause)`<br>Specifies a `Condition` to associate with this `DimensionMap`.                                                                                                                                       |

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

    - #### setKeyExpression

          public void setKeyExpression(Expression input)

      Specifies the primary key column of the relational table for the dimension members.
      Parameters:
      `input` - An `Expression` that identifies the primary key column for the dimension members.

    <!-- -->

    - #### getKeyExpression

          public Expression getKeyExpression()

      Gets the `Expression` that identifies the primary key column of the relational table for the dimension members.
      Returns:
      An `Expression` that identifies the primary key column for the dimension members.

    <!-- -->

    - #### setDimension

          public void setDimension(MdmDimension input)

      Specifies the `MdmDimension` to associate with the `DimensionMap`.
      Parameters:
      `input` - The `MdmDimension` to associate with the `DimensionMap`.

    <!-- -->

    - #### getDimension

          public MdmDimension getDimension()

      Gets the `MdmDimension` associated with the `DimensionMap`.
      Returns:
      The `MdmDimension` associated with the `DimensionMap`.

    <!-- -->

    - #### setWhereClause

          public void setWhereClause(Condition whereClause)

      Specifies a `Condition` to associate with this `DimensionMap`. The `Condition` functions like a `WHERE` clause in a SQL `SELECT` statement
      Parameters:
      `whereClause` - The `Condition` to associate with this `DimensionMap`.

    <!-- -->

    - #### getWhereClause

          public Condition getWhereClause()

      Gets the `Condition` associated with the `DimensionMap`.
      Returns:
      The `Condition` associated with the `DimensionMap`.

    <!-- -->

    - #### setFromClause

          public void setFromClause(FromClause fromClause)

      Specifies a `FromClause` to associate with the `DimensionMap`. A `DimensionMap` can have a `FromClause` or a `Query`, but not both.
      A `FromClause` specifies tables that Oracle OLAP joins to get the values that it requires for members of an OLAP dimension. For example, the values for an `MdmAttribute` could come from a table other than the table that contains the dimension members. A `FromClause` that specifies only one table is functionally the same as a `Query`.

      A `FromClause` that specifies two or more tables requires a `Condition` that specifies the join conditions for the tables. You specify the `Condition` with the `setWhereClause` method.

      Parameters:
      `fromClause` - The `FromClause` to associate with the `DimensionMap`.

    <!-- -->

    - #### getFromClause

          public FromClause getFromClause()

      Gets the `FromClause` associated with the `DimensionMap`.
      Returns:
      The `FromClause` associated with the `DimensionMap`.

    <!-- -->

    - #### setQuery

          public void setQuery(Query query)

      Specifies a `Query` to associate with this `DimensionMap`. A `DimensionMap` can have a `Query` or a `FromClause`, but not both. The `Query` for a dimension identifies the relational table that contains the data for the dimension.
      Parameters:
      `query` - The `Query` to associate with this `DimensionMap`.

    <!-- -->

    - #### getQuery

          public Query getQuery()

      Gets the `Query` associated with the `DimensionMap`.
      Returns:
      The `Query` associated with the `DimensionMap`.

    <!-- -->

    - #### addAttributeMap

          public void addAttributeMap(AttributeMap value)

      Adds an `AttributeMap` to the `DimensionMap`.
      Parameters:
      `value` - The `AttributeMap` to add.

    <!-- -->

    - #### removeAttributeMap

          public void removeAttributeMap(AttributeMap value)

      Removes an `AttributeMap` from the `DimensionMap`.
      Parameters:
      `value` - The `AttributeMap` to remove.

    <!-- -->

    - #### getAttributeMaps

          public java.util.List getAttributeMaps()

      Gets the `AttributeMap` objects that are owned by the `DimensionMap`.
      Returns:
      A `List` that contains the `AttributeMap` objects owned by the `DimensionMap`.

    <!-- -->

    - #### findOrCreateAttributeMap

          public AttributeMap findOrCreateAttributeMap(MdmBaseAttribute attribute)

      Gets the `AttributeMap` for the specified attribute or, if the map does not exist, creates an `AttributeMap` for the attribute.
      Parameters:
      `attribute` - The `MdmBaseAttribute` for which to get an `AttributeMap`.

      Returns:
      An `AttributeMap` for the specified attribute.

    <!-- -->

    - #### findOrCreateAttributeMap

          public AttributeMap findOrCreateAttributeMap(MdmBaseAttribute attribute,
                                                       java.lang.String language)

      Gets the `AttributeMap` for the specified attribute and language or, if the map does not exist, creates an `AttributeMap` for the attribute and language.
      Parameters:
      `attribute` - The `MdmBaseAttribute` for which to get an `AttributeMap`.

      `language` - A `String` that specifies the language for the attribute.

      Returns:
      An `AttributeMap` for the specified attribute and language.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](CubeMap.md)
- [Next Class](HierarchyLevelMap.md)

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
