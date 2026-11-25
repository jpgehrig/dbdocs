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

- [Prev Class](MdmDescriptionType.md)
- [Next Class](MdmDimensionality.md)

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

## Class MdmDimension

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - oracle.olapi.metadata.mdm.MdmDimension

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [MdmPrimaryDimension](MdmPrimaryDimension.md), [MdmSubDimension](MdmSubDimension.md)

  ------------------------------------------------------------------------



      public abstract class MdmDimension
      extends MdmSource

  An `MdmSource` that represents an OLAP dimension. A dimension organizes and specifies the data in an OLAP measure. This abstract class has two subclasses, `MdmPrimaryDimension` and `MdmSubDimension`.
  An `MdmPrimaryDimension` has information about the type of data that its components represent. The components of an `MdmPrimaryDimension` are `MdmSubDimension` objects, which represent organizations of the members of the dimension. Concrete subclasses of `MdmSubDimension` represent dimensions organized hierarchically or nonhierarchically.

  You initially get `MdmPrimaryDimension` objects from an instance of an `MdmSchema` or an `MdmMeasure`. The `getDimensions` methods of those objects return lists of `MdmPrimaryDimension` objects.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                                                                                                                 |
    |--------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract java.util.List`                        | `getAttributes``()`<br>Gets a `List` of `MdmAttribute` objects for this `MdmDimension`.                                                                                                                |
    | `int`                                            | `getCardinality``()`<br>Gets the estimated number of members (the cardinality) of this `MdmDimension`.                                                                                                 |
    | [`OrderByClause`](../../syntax/OrderByClause.md) | `getCustomOrder``()`<br>Gets the `OrderByClause` that indicates an order for a set of related members of this `MdmDimension`.                                                                          |
    | `java.lang.String`                               | `getPluralDescription``()`<br>Gets the long plural description of this `MdmDimension`.                                                                                                                 |
    | [`MdmPrimaryDimension`](MdmPrimaryDimension.md)  | `getPrimaryDimension``()`<br>Gets the `MdmPrimaryDimension` for a concrete subclass of this `MdmDimension`.                                                                                            |
    | `java.lang.String`                               | `getShortPluralDescription``()`<br>Gets the short plural description of this `MdmDimension`.                                                                                                           |
    | `abstract void`                                  | `removeAttribute``(`[`MdmAttribute`](MdmAttribute.md)` attr)`<br>Removes the specified `MdmAttribute` from the attributes of this `MdmDimension`.                                                      |
    | `void`                                           | `setCardinality``(int newCardinality)`<br>Sets the cardinality (estimated number of members) of this `MdmDimension`.                                                                                   |
    | `void`                                           | `setCustomOrder``(`[`OrderByClause`](../../syntax/OrderByClause.md)` input)`<br>Specifies an `OrderByClause` for this `MdmDimension`, which indicates an order for a set of related dimension members. |
    | `void`                                           | `setPluralDescription``(java.lang.String value)`<br>Sets the long plural description for this `MdmDimension`.                                                                                          |
    | `void`                                           | `setShortPluralDescription``(java.lang.String value)`<br>Sets the short plural description for this `MdmDimension`.                                                                                    |

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

    - #### getAttributes

          public abstract java.util.List getAttributes()

      Gets a `List` of `MdmAttribute` objects for this `MdmDimension`.
      Returns:
      A `List` of the `MdmAttribute` objects for this `MdmDimension`.

      See Also:
      [`MdmAttribute`](MdmAttribute.md)

    <!-- -->

    - #### getPrimaryDimension

          public final MdmPrimaryDimension getPrimaryDimension()

      Gets the `MdmPrimaryDimension` for a concrete subclass of this `MdmDimension`. For an `MdmSubDimension`, this method returns the `MdmPrimaryDimension` of which the `MdmSubDimension` is a component. For an `MdmPrimaryDimension`, this method returns the same `MdmPrimaryDimension` object.
      Returns:
      The `MdmPrimaryDimension` for an `MdmSubDimension` or itself for an `MdmPrimaryDimension`.

    <!-- -->

    - #### getPluralDescription

          public java.lang.String getPluralDescription()
                                                throws oracle.express.mdm.MetadataNotFoundException

      Gets the long plural description of this `MdmDimension`. You can use this description for display in a graphical user interface when the plural of the name is required.
      Returns:
      A `String` containing the long plural description of this `MdmDimension`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getShortPluralDescription

          public java.lang.String getShortPluralDescription()
                                                     throws oracle.express.mdm.MetadataNotFoundException

      Gets the short plural description of this `MdmDimension`. You can use this description for display in a graphical user interface when the plural of the name is required.
      Returns:
      A `String` containing the short plural description of this `MdmDimension`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getCardinality

          public int getCardinality()
                             throws oracle.express.mdm.MetadataNotFoundException

      Gets the estimated number of members (the cardinality) of this `MdmDimension`. You can use this estimate as a factor in determining a display algorithm or other potentially performance-intensive operation, or in determining how long some other operation might take.
      If no cardinality is specified for the `MdmDimension`, this method returns `-1`, which indicates that Oracle OLAP has no estimated value for the number of members in this `MdmDimension`.

      Returns:
      The estimated number of members in this `MdmDimension`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### setPluralDescription

          public void setPluralDescription(java.lang.String value)

      Sets the long plural description for this `MdmDimension`.
      Parameters:
      `value` - A `String` containing the long plural description that you want this `MdmDimension` to have.

    <!-- -->

    - #### setShortPluralDescription

          public void setShortPluralDescription(java.lang.String value)

      Sets the short plural description for this `MdmDimension`.
      Parameters:
      `value` - A `String` containing the short plural description that you want this `MdmDimension` to have.

    <!-- -->

    - #### setCardinality

          public void setCardinality(int newCardinality)

      Sets the cardinality (estimated number of members) of this `MdmDimension`. Specify a cardinality of -1 to indicate that no assumptions can be made about the number of members in this `MdmDimension`.
      Parameters:
      `newCardinality` - The estimated number of members in this `MdmDimension`.

    <!-- -->

    - #### removeAttribute

          public abstract void removeAttribute(MdmAttribute attr)

      Removes the specified `MdmAttribute` from the attributes of this `MdmDimension`.
      Parameters:
      `attr` - The `MdmAttribute` to remove from this `MdmDimension`.

    <!-- -->

    - #### getCustomOrder

          public final OrderByClause getCustomOrder()

      Gets the `OrderByClause` that indicates an order for a set of related members of this `MdmDimension`.
      Returns:
      An `OrderByClause` that indicates an order for a set of the dimension members.

    <!-- -->

    - #### setCustomOrder

          public final void setCustomOrder(OrderByClause input)

      Specifies an `OrderByClause` for this `MdmDimension`, which indicates an order for a set of related dimension members.
      Parameters:
      `input` - An `OrderByClause` that indicates an order for a set of dimension members.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmDescriptionType.md)
- [Next Class](MdmDimensionality.md)

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
