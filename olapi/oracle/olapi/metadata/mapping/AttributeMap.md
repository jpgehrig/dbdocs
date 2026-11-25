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

- Prev Class
- [Next Class](CubeDimensionalityMap.md)

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

## Class AttributeMap

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mapping.ObjectMap](ObjectMap.md)

      - - [oracle.olapi.metadata.mapping.ValueMap](ValueMap.md)

        - - oracle.olapi.metadata.mapping.AttributeMap

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class AttributeMap
      extends ValueMap

  A `ValueMap` that maps an `MdmAttribute` for an `MdmDimension` to an `Expression`. An application creates an `AttributeMap` with the [`findOrCreateAttributeMap`](DimensionMap.md) method of a `DimensionMap`. An application that supports multiple languages must provide a separate `AttributeMap` for each language.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                                                           |
    |--------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MdmBaseAttribute`](../mdm/MdmBaseAttribute.md) | `getAttribute``()`<br>Gets the `MdmAttribute` associated with the `AttributeMap`.                                                                |
    | [`DimensionMap`](DimensionMap.md)                | `getDimensionMap``()`<br>Gets the `DimensionMap` that is the owner of this `AttributeMap`.                                                       |
    | `java.lang.String`                               | `getLanguage``()`<br>Gets the language that is associated with this `AttributeMap`.                                                              |
    | `void`                                           | `setAttribute``(`[`MdmBaseAttribute`](../mdm/MdmBaseAttribute.md)` input)`<br>Specifies the `MdmAttribute` to associate with the `AttributeMap`. |
    | `void`                                           | `setLanguage``(java.lang.String input)`<br>Specifies the language to associate with this `AttributeMap`.                                         |

    - ### Methods inherited from class oracle.olapi.metadata.mapping.[ValueMap](ValueMap.md)

      [`getExpression`](ValueMap.md)`, `[`getName`](ValueMap.md)`, `[`setExpression`](ValueMap.md)`, `[`setName`](ValueMap.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### setAttribute

          public void setAttribute(MdmBaseAttribute input)

      Specifies the `MdmAttribute` to associate with the `AttributeMap`.
      Parameters:
      `input` - The `MdmAttribute` to associate with the `AttributeMap`.

    <!-- -->

    - #### getAttribute

          public MdmBaseAttribute getAttribute()

      Gets the `MdmAttribute` associated with the `AttributeMap`.
      Returns:
      The `MdmAttribute` associated with the `AttributeMap`.

    <!-- -->

    - #### getDimensionMap

          public DimensionMap getDimensionMap()

      Gets the `DimensionMap` that is the owner of this `AttributeMap`.
      Returns:
      The `DimensionMap` that owns this `AttributeMap`.

    <!-- -->

    - #### setLanguage

          public void setLanguage(java.lang.String input)

      Specifies the language to associate with this `AttributeMap`.
      Parameters:
      `input` - A `String` that contains the identifier of the language to associate with this `AttributeMap`.

    <!-- -->

    - #### getLanguage

          public java.lang.String getLanguage()

      Gets the language that is associated with this `AttributeMap`.
      Returns:
      A `String` that contains the identifier of the language associated with this `AttributeMap`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- Prev Class
- [Next Class](CubeDimensionalityMap.md)

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
