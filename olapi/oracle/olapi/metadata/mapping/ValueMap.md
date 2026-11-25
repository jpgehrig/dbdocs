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

- [Prev Class](SolvedValueHierarchyMap.md)
- Next Class

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

## Class ValueMap

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mapping.ObjectMap](ObjectMap.md)

      - - oracle.olapi.metadata.mapping.ValueMap

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [AttributeMap](AttributeMap.md), [CubeDimensionalityMap](CubeDimensionalityMap.md), [MeasureMap](MeasureMap.md)

  ------------------------------------------------------------------------



      public abstract class ValueMap
      extends ObjectMap

  An abstract `ObjectMap` that maps an `MdmDimensionedObject` to relational source data. You use a `CubeMap` or a `DimensionMap` to create a `ValueMap`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                          | Method and Description                                                                                                                                                               |
    |--------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Expression`](../../syntax/Expression.md) | `getExpression``()`<br>Gets an `Expression` that identifies the relational source data for the values of the metadata object.                                                        |
    | `java.lang.String`                         | `getName``()`<br>Gets the name of the `ValueMap`.                                                                                                                                    |
    | `void`                                     | `setExpression``(`[`Expression`](../../syntax/Expression.md)` input)`<br>Specifies an `Expression` that identifies the relational source data for the values of the metadata object. |
    | `void`                                     | `setName``(java.lang.String name)`<br>Specifies a name for the `ValueMap`.                                                                                                           |

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### setExpression

          public void setExpression(Expression input)

      Specifies an `Expression` that identifies the relational source data for the values of the metadata object.
      Parameters:
      `input` - An `Expression` that identifies the relational source of the data for the metadata object.

    <!-- -->

    - #### getExpression

          public Expression getExpression()

      Gets an `Expression` that identifies the relational source data for the values of the metadata object.
      Returns:
      An `Expression` that identifies the relational source of the data for the metadata object.

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Gets the name of the `ValueMap`.
      Overrides:
      [`getName`](ObjectMap.md) in class [`ObjectMap`](ObjectMap.md)

      Returns:
      A `String` that contains the name of the `ValueMap`.

    <!-- -->

    - #### setName

          public void setName(java.lang.String name)

      Specifies a name for the `ValueMap`.
      Parameters:
      `name` - A `String` that contains a name for the `ValueMap`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](SolvedValueHierarchyMap.md)
- Next Class

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
