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

- [Prev Class](MdmBaseObjectVisitor.md)
- [Next Class](MdmCube.md)

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

## Class MdmColumn

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - oracle.olapi.metadata.mdm.MdmColumn

<!-- -->

- All Implemented Interfaces:
  [MdmQueryColumn](MdmQueryColumn.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmColumn
      extends MdmSource
      implements MdmQueryColumn

  An `MdmSource` that represents a column of a table in a relational database. Some of the methods of `MdmTable` return `MdmColumn` objects.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                                                                                                                                   |
    |--------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                               | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmColumn` method of the `MdmObjectVisitor` and passes that method this `MdmColumn` and an `Object`. |
    | [`BaseMetadataObject`](../BaseMetadataObject.md) | `getColumnObject``()`<br>Gets this `MdmColumn` as a `BaseMetadataObject`.                                                                                                                                                |
    | [`SQLDataType`](../../syntax/SQLDataType.md)     | `getSQLDataType``()`<br>Gets the `SQLDataType` that is associated with this `MdmColumn`.                                                                                                                                 |
    | [`MdmTable`](MdmTable.md)                        | `getTable``()`<br>Gets the `MdmTable` that is associated with this `MdmColumn`.                                                                                                                                          |
    | [`MetadataObject`](../MetadataObject.md)         | `getType``()`<br>Gets the data type of this `MdmColumn`.                                                                                                                                                                 |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSource](MdmSource.md)

      [`getDataType`](MdmSource.md)`, `[`getSource`](MdmSource.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)

      [`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

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

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmColumn` method of the `MdmObjectVisitor` and passes that method this `MdmColumn` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor` that is an instance of `Mdm11_ObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmColumn` method.

    <!-- -->

    - #### getTable

          public final MdmTable getTable()

      Gets the `MdmTable` that is associated with this `MdmColumn`.
      Returns:
      The `MdmTable` that owns this `MdmColumn`.

    <!-- -->

    - #### getSQLDataType

          public final SQLDataType getSQLDataType()

      Gets the `SQLDataType` that is associated with this `MdmColumn`.
      Specified by:
      [`getSQLDataType`](MdmQueryColumn.md) in interface [`MdmQueryColumn`](MdmQueryColumn.md)

      Returns:
      The `SQLDataType` of this `MdmColumn`.

    <!-- -->

    - #### getColumnObject

          public final BaseMetadataObject getColumnObject()

      Gets this `MdmColumn` as a `BaseMetadataObject`.
      Specified by:
      [`getColumnObject`](MdmQueryColumn.md) in interface [`MdmQueryColumn`](MdmQueryColumn.md)

      Returns:
      This `MdmColumn` as a `BaseMetadataObject`.

    <!-- -->

    - #### getType

          public final MetadataObject getType()

      Gets the data type of this `MdmColumn`.
      Specified by:
      [`getType`](MdmSource.md) in class [`MdmSource`](MdmSource.md)

      Returns:
      The data type of this `MdmColumn`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmBaseObjectVisitor.md)
- [Next Class](MdmCube.md)

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
