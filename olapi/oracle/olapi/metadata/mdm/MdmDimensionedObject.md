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

- [Prev Class](MdmDimensionCalculationModel.md)
- [Next Class](MdmDimensionLevel.md)

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

oracle.olapi.metadata.mdm

## Class MdmDimensionedObject

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - oracle.olapi.metadata.mdm.MdmDimensionedObject

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [MdmAttribute](MdmAttribute.md), [MdmCube](MdmCube.md), [MdmMeasure](MdmMeasure.md)

  ------------------------------------------------------------------------



      public abstract class MdmDimensionedObject
      extends MdmSource

  An `MdmSource` that represents a set of data that is organized by one or more `MdmDimension` objects.
  The structure of the data that is represented by an `MdmDimensionedObject` is similar to that of a multidimensional array. Like the dimensions of an array, the `MdmDimension` objects that organize an `MdmDimensionedObject` provide the indexes for identifying individual cells. For example, suppose you have an `MdmMeasure` (a subclass of `MdmDimensionedObject`) that represents sales data, and the data is organized by product, time, and customer. You can think of the data as occupying a three-dimensional array with the product, time, and customer dimensions providing the organizational structure. The values of these three dimensions are indexes for identifying each particular cell in the array, which contains a single sales value. You must specify a value for each dimension in order to identify a value in the array. In relational terms, the `MdmDimension` objects can be thought of as a compound (that is, composite) primary key for the `MdmMeasure`.

  Another subclass of `MdmDimensionedObject` is `MdmAttribute`, which provides a mapping from the members of an `MdmDimension` to values that represent characteristics of the members, such as their color or their gender. For an `MdmAttribute`, the data is organized by the `MdmDimension` for which it holds characteristics, just as the data for an `MdmMeasure` is organized by its `MdmDimension` objects.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                           | Method and Description                                                                                                                                                                                         |
    |---------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MdmDimensionality`](MdmDimensionality.md) | `addDimension``(`[`MdmDimension`](MdmDimension.md)` dimension)`<br>Adds an `MdmDimension` to the dimensions by which this `MdmDimensionedObject` is dimensioned.                                               |
    | `void`                                      | `addDimensionality``(`[`MdmDimensionality`](MdmDimensionality.md)` value)`<br>Adds an `MdmDimensionality` to the list of dimensionality objects that are associated which this `MdmDimensionedObject`.         |
    | `java.util.List`                            | `getDimensionality``()`<br>Gets the `MdmDimensionality` objects for this `MdmDimensionedObject`.                                                                                                               |
    | `java.util.List`                            | `getDimensions``()`<br>Gets the `MdmDimension` objects for this `MdmDimensionedObject`.                                                                                                                        |
    | `boolean`                                   | `isBooleanValued``()`<br>Indicates whether this `MdmDimensionedObject` has `boolean` values.                                                                                                                   |
    | `void`                                      | `removeDimensionality``(`[`MdmDimensionality`](MdmDimensionality.md)` value)`<br>Removes an `MdmDimensionality` from the list of dimensionality objects that are associated which this `MdmDimensionedObject`. |
    | `void`                                      | `setBooleanValued``(boolean input)`<br>Specifies whether this `MdmDimensionedObject` has `boolean` values.                                                                                                     |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSource](MdmSource.md)

      [`getDataType`](MdmSource.md)`, `[`getSource`](MdmSource.md)`, `[`getType`](MdmSource.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)

      [`acceptVisitor`](MdmObject.md)`, `[`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### addDimension

          public final MdmDimensionality addDimension(MdmDimension dimension)

      Adds an `MdmDimension` to the dimensions by which this `MdmDimensionedObject` is dimensioned.
      Parameters:
      `dimension` - The `MdmDimension` to add to this `MdmDimensionedObject`.

    <!-- -->

    - #### getDimensions

          public final java.util.List getDimensions()

      Gets the `MdmDimension` objects for this `MdmDimensionedObject`.
      Returns:
      A `List` that contains the `MdmDimension` objects for this `MdmDimensionedObject`.

    <!-- -->

    - #### getDimensionality

          public java.util.List getDimensionality()

      Gets the `MdmDimensionality` objects for this `MdmDimensionedObject`.
      Returns:
      A `List` that contains the `MdmDimensionality` objects for this `MdmDimensionedObject`.

    <!-- -->

    - #### addDimensionality

          public void addDimensionality(MdmDimensionality value)

      Adds an `MdmDimensionality` to the list of dimensionality objects that are associated which this `MdmDimensionedObject`.
      Parameters:
      `value` - The `MdmDimensionality` to add to this `MdmDimensionedObject`.

    <!-- -->

    - #### removeDimensionality

          public void removeDimensionality(MdmDimensionality value)

      Removes an `MdmDimensionality` from the list of dimensionality objects that are associated which this `MdmDimensionedObject`.
      Parameters:
      `value` - The `MdmDimensionality` to remove from this `MdmDimensionedObject`.

    <!-- -->

    - #### isBooleanValued

          public final boolean isBooleanValued()

      Indicates whether this `MdmDimensionedObject` has `boolean` values.
      Returns:
      A `boolean` that is `true` if this `MdmDimensionedObject` has `boolean` values or `false` otherwise.

    <!-- -->

    - #### setBooleanValued

          public final void setBooleanValued(boolean input)

      Specifies whether this `MdmDimensionedObject` has `boolean` values.
      Parameters:
      `input` - A `boolean` that is `true` if this `MdmDimensionedObject` has `boolean` values or `false` otherwise.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmDimensionCalculationModel.md)
- [Next Class](MdmDimensionLevel.md)

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
