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

- [Prev Class](MdmAssignment.md)
- [Next Class](MdmAttributeModel.md)

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

## Class MdmAttribute

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimensionedObject](MdmDimensionedObject.md)

          - - oracle.olapi.metadata.mdm.MdmAttribute

<!-- -->

- All Implemented Interfaces:
  [MdmQueryColumn](MdmQueryColumn.md), [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [MdmMultiValuedAttribute](MdmMultiValuedAttribute.md), [MdmSingleValuedAttribute](MdmSingleValuedAttribute.md)

  ------------------------------------------------------------------------



      public abstract class MdmAttribute
      extends MdmDimensionedObject
      implements MdmQueryColumn

  The abstract base class for an `MdmDimensionedObject` that represents one or more characteristic of the members of an `MdmDimension`. An `MdmAttribute` relates one member of the `MdmDimension` to one or more values. For example, the end date `MdmAttribute` of an `MdmTimeDimension` relates an end date to each member of an `MdmTimeDimension`. The data type of an `MdmAttribute` can be any of the OLAP Java API data types. A value of `MdmAttribute` can be a boolean, a `Date`, a number, a `String`, an `MdmSource`, or other kinds of objects.
  An `MdmAttribute` is an `MdmDimensionedObject` because it has elements that are organized by an `MdmDimension`. For example, the end date `MdmAttribute` has one element (with a value that specifies a date) for each member of the `MdmTimeDimension` associated with it.

  An application finds an existing attribute or creates a new one by using the appropriate method of the `MdmPrimaryDimension` that dimensions it. For example, the `findOrCreateBaseAttribute` method of an `MdmPrimaryDimension` gets an existing `MdmBaseAttribute` or creates a new one. An application can also get attributes of a dimension or level by using methods such as `getShortValueDescriptionAttribute` of an `MdmPrimaryDimension` and `getLevelAttribute` of an `MdmLevelHierarchy`.

  Sometimes, not all of the members of an `MdmDimension` relate to the values of an `MdmAttribute`. For example, an `MdmLevelHierarchy` that represents a dimension of product items might have an attribute at the lowest level that relates a color to the items. The color attribute does not apply to members at higher levels of the hierarchy. If an `MdmAttribute` does not apply to a member of an `MdmDimension`, then the attribute value for that member is `null`.

  Some `MdmAttribute` objects provide a relation that is one-to-many, rather than one-to-one. Therefore, a member in an `MdmDimension` might map to a whole set of `MdmAttribute` elements. For example, the `MdmAttribute` that is the ancestors attribute of an `MdmHierarchy` relates each member of the `MdmHierarchy` to the set of the `MdmHierarchy` members that are the ancestors of it.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                       | Method and Description                                                                                                                                                                                                           |
    |---------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`BaseMetadataObject`](../BaseMetadataObject.md)        | `getColumnObject``()`<br>Gets the Column                                                                                                                                                                                         |
    | [`MdmDescriptionType`](MdmDescriptionType.md)           | `getDescriptionType``()`<br>Gets the `MdmDescriptionType` associated with the `MdmAttribute`.                                                                                                                                    |
    | `java.util.List`                                        | `getDimensionality``()`<br>Gets a `List` of the `MdmPrimaryDimension` objects associated with the `MdmAttribute`.                                                                                                                |
    | [`MdmPrimaryDimension`](MdmPrimaryDimension.md)         | `getPrimaryDimension``()`<br>Gets the `MdmPrimaryDimension` associated with the `MdmAttribute`.                                                                                                                                  |
    | `abstract `[`SQLDataType`](../../syntax/SQLDataType.md) | `getSQLDataType``()`<br>Gets the SQL data type for the `MdmAttribute`.                                                                                                                                                           |
    | [`MdmPrimaryDimension`](MdmPrimaryDimension.md)         | `getTargetDimension``()`<br>Gets the `MdmPrimaryDimension` associated with the `MdmAttribute`.                                                                                                                                   |
    | [`MetadataObject`](../MetadataObject.md)                | `getType``()`<br>Gets the OLAP Java API data type for the `MdmAttribute`.                                                                                                                                                        |
    | `boolean`                                               | `isVisibleForAll``()`<br>Indicates whether a column for the `MdmAttribute` appears in the OLAP (ET) views for all of the hierarchies of the `MdmPrimaryDimension` that contains the `MdmAttribute`.                              |
    | `void`                                                  | `setDescriptionType``(`[`MdmDescriptionType`](MdmDescriptionType.md)` input)`<br>Specifies an `MdmDescriptionType` to associate with the `MdmAttribute`.                                                                         |
    | `void`                                                  | `setIsVisibleForAll``(boolean input)`<br>Specifies whether Oracle OLAP includes a column for the `MdmAttribute` in the OLAP (ET) views for all of the hierarchies of the `MdmPrimaryDimension` that contains the `MdmAttribute`. |
    | `void`                                                  | `setPrimaryDimension``(`[`MdmPrimaryDimension`](MdmPrimaryDimension.md)` primaryDimension)`<br>Specifies the `MdmPrimaryDimension` to associate with the `MdmAttribute`.                                                         |
    | `void`                                                  | `setTargetDimension``(`[`MdmPrimaryDimension`](MdmPrimaryDimension.md)` input)`<br>Specifies an `MdmPrimaryDimension` to associate with the `MdmAttribute`.                                                                      |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmDimensionedObject](MdmDimensionedObject.md)

      [`addDimension`](MdmDimensionedObject.md)`, `[`addDimensionality`](MdmDimensionedObject.md)`, `[`getDimensions`](MdmDimensionedObject.md)`, `[`isBooleanValued`](MdmDimensionedObject.md)`, `[`removeDimensionality`](MdmDimensionedObject.md)`, `[`setBooleanValued`](MdmDimensionedObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSource](MdmSource.md)

      [`getDataType`](MdmSource.md)`, `[`getSource`](MdmSource.md)

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

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[MdmQueryColumn](MdmQueryColumn.md)

      [`getName`](MdmQueryColumn.md)

<!-- -->

- - ### Method Detail

    - #### getTargetDimension

          public final MdmPrimaryDimension getTargetDimension()

      Gets the `MdmPrimaryDimension` associated with the `MdmAttribute`.
      Returns:
      The `MdmPrimaryDimension` associated with the `MdmAttribute`.

    <!-- -->

    - #### setTargetDimension

          public final void setTargetDimension(MdmPrimaryDimension input)

      Specifies an `MdmPrimaryDimension` to associate with the `MdmAttribute`.
      Parameters:
      `input` - The `MdmPrimaryDimension` to associate with the `MdmAttribute`.

    <!-- -->

    - #### getDescriptionType

          public final MdmDescriptionType getDescriptionType()

      Gets the `MdmDescriptionType` associated with the `MdmAttribute`.
      Returns:
      The `MdmDescriptionType` associated with the `MdmAttribute`.

    <!-- -->

    - #### setDescriptionType

          public final void setDescriptionType(MdmDescriptionType input)

      Specifies an `MdmDescriptionType` to associate with the `MdmAttribute`.
      Parameters:
      `input` - The `MdmDescriptionType` to associate with the `>MdmAttribute`.

    <!-- -->

    - #### isVisibleForAll

          public final boolean isVisibleForAll()

      Indicates whether a column for the `MdmAttribute` appears in the OLAP (ET) views for all of the hierarchies of the `MdmPrimaryDimension` that contains the `MdmAttribute`.
      Returns:
      A `boolean` that is `true` if a column for the attribute appears in the OLAP views for all of the hierarchies of the dimension or `false` if it does not.

    <!-- -->

    - #### setIsVisibleForAll

          public final void setIsVisibleForAll(boolean input)

      Specifies whether Oracle OLAP includes a column for the `MdmAttribute` in the OLAP (ET) views for all of the hierarchies of the `MdmPrimaryDimension` that contains the `MdmAttribute`.
      Parameters:
      `input` - A `boolean` that is `true` to have Oracle OLAP include a column for the attribute in the OLAP view of each of the hierarchies of the dimension or `false` to not do so.

    <!-- -->

    - #### setPrimaryDimension

          public final void setPrimaryDimension(MdmPrimaryDimension primaryDimension)

      Specifies the `MdmPrimaryDimension` to associate with the `MdmAttribute`.
      Parameters:
      `primaryDimension` - The `MdmPrimaryDimension` to associate with the `MdmAttribute`.

    <!-- -->

    - #### getDimensionality

          public final java.util.List getDimensionality()

      Gets a `List` of the `MdmPrimaryDimension` objects associated with the `MdmAttribute`.
      Overrides:
      [`getDimensionality`](MdmDimensionedObject.md) in class [`MdmDimensionedObject`](MdmDimensionedObject.md)

      Returns:
      A `List` of the `MdmPrimaryDimension` objects associated with the `MdmAttribute`.

    <!-- -->

    - #### getPrimaryDimension

          public final MdmPrimaryDimension getPrimaryDimension()

      Gets the `MdmPrimaryDimension` associated with the `MdmAttribute`.
      Returns:
      The `MdmPrimaryDimension` associated with the `MdmAttribute`.

    <!-- -->

    - #### getType

          public final MetadataObject getType()

      Gets the OLAP Java API data type for the `MdmAttribute`.
      Specified by:
      [`getType`](MdmSource.md) in class [`MdmSource`](MdmSource.md)

      Returns:
      A `MetadataObject` that represents the OLAP Java API data type.

    <!-- -->

    - #### getSQLDataType

          public abstract SQLDataType getSQLDataType()

      Gets the SQL data type for the `MdmAttribute`.
      Specified by:
      [`getSQLDataType`](MdmQueryColumn.md) in interface [`MdmQueryColumn`](MdmQueryColumn.md)

      Returns:
      A `SQLDataType` that represents the SQL data type.

    <!-- -->

    - #### getColumnObject

          public BaseMetadataObject getColumnObject()

      Gets the Column
      Specified by:
      [`getColumnObject`](MdmQueryColumn.md) in interface [`MdmQueryColumn`](MdmQueryColumn.md)

      Returns:
      A `BaseMetadataObject` that represents the column

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmAssignment.md)
- [Next Class](MdmAttributeModel.md)

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
