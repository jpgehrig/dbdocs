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

- [Prev Class](MdmDimension.md)
- [Next Class](MdmDimensionCalculationModel.md)

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

## Class MdmDimensionality

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - oracle.olapi.metadata.mdm.MdmDimensionality

<!-- -->

- All Implemented Interfaces:
  [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmDimensionality
      extends MdmObject
      implements MdmViewColumnOwner

  An `MdmObject` that associates an `MdmPrimaryDimension` with an `MdmDimensionedObject`. You can get the `MdmDimensionality` objects with the `getDimensionality` method of the `MdmDimensionedObject`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                                                                                                                                   |
    |-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                  | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmDimensionality` method of the `MdmObjectVisitor` and passes that method this `MdmDimensionality` and an `Object`. |
    | [`MdmDimension`](MdmDimension.md)   | `getDimension``()`<br>Gets the `MdmPrimaryDimension` that is associated with this `MdmDimensionality`.                                                                                                                                   |
    | `java.lang.String`                  | `getETAttrPrefix``()`<br>Gets the ET attribute prefix of this `MdmDimensionality`.                                                                                                                                                       |
    | [`MdmViewColumn`](MdmViewColumn.md) | `getETColumn``()`<br>Gets the `MdmViewColumn` that represents the ET (Embedded Totals) values for this `MdmDimensionality`.                                                                                                              |
    | `void`                              | `setDimension``(`[`MdmDimension`](MdmDimension.md)` value)`<br>Specifies the `MdmPrimaryDimension` to associate with this `MdmDimensionality`.                                                                                           |
    | `void`                              | `setETAttrPrefix``(java.lang.String value)`<br>Specifies a prefix for the name of the column for an attribute of a dimension in the materialized view of a cube.                                                                         |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)

      [`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getDimension

          public MdmDimension getDimension()
                                    throws oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmPrimaryDimension` that is associated with this `MdmDimensionality`.
      Returns:
      The `MdmPrimaryDimension` associated with this `MdmDimensionality`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException` - Indicates that the requested metadata object does not exist or is not available to the `MdmMetadataProvider`.

    <!-- -->

    - #### setDimension

          public void setDimension(MdmDimension value)

      Specifies the `MdmPrimaryDimension` to associate with this `MdmDimensionality`.
      Parameters:
      `value` - The `MdmPrimaryDimension` to associate with this `MdmDimensionality`.

    <!-- -->

    - #### getETAttrPrefix

          public java.lang.String getETAttrPrefix()
                                           throws oracle.express.mdm.MetadataNotFoundException

      Gets the ET attribute prefix of this `MdmDimensionality`.
      Returns:
      A `String` that is the prefix that Oracle OLAP adds to the name of the column for an attribute of a dimension in the materialized view for a cube.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException` - Indicates that the requested metadata object does not exist or is not available to the `MdmMetadataProvider`.

    <!-- -->

    - #### setETAttrPrefix

          public void setETAttrPrefix(java.lang.String value)

      Specifies a prefix for the name of the column for an attribute of a dimension in the materialized view of a cube. When Oracle OLAP creates a materialized view for a cube, it creates columns for the attributes of the dimensions of the cubes. For the name of a column, it uses the name of the attribute column from the ET view of the dimension and adds a default prefix to the name. The ET attribute prefix provides a unique name for the column so that the name does not conflict with that of a column for an attribute of the same name that is owned by for another dimension. For example, each dimension of a cube might have an attribute named LONG_DESCRIPTION.
      Oracle OLAP automatically assigns an ET attribute prefix for the column names for the attributes of a dimension in the materialized view for a cube. You can use this method to assign your own prefix for the column names.

      Parameters:
      `value` - A `String` that contains the prefix for Oracle OLAP to add to the name of the column for an attribute of a dimension in a materialized view for a cube.

    <!-- -->

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmDimensionality` method of the `MdmObjectVisitor` and passes that method this `MdmDimensionality` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor` that implements the `Mdm11_2_ObjectVisitor` interface. .

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmDimensionality` method.

    <!-- -->

    - #### getETColumn

          public final MdmViewColumn getETColumn()

      Gets the `MdmViewColumn` that represents the ET (Embedded Totals) values for this `MdmDimensionality`.
      Returns:
      The `MdmViewColumn` that represents the ET column for this `MdmDimensionality`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmDimension.md)
- [Next Class](MdmDimensionCalculationModel.md)

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
