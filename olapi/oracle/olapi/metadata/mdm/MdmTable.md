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

- [Prev Class](MdmSubDimension.md)
- [Next Class](MdmTimeDimension.md)

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

## Class MdmTable

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - oracle.olapi.metadata.mdm.MdmTable

<!-- -->

- All Implemented Interfaces:
  [MdmQuery](MdmQuery.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmTable
      extends MdmSource
      implements MdmQuery

  An `MdmSource` that represents a table in a relational database. You get an `MdmTable` by calling the `getTopLevelObject` method of an `MdmDatabaseSchema`. For example, the following code gets the `MdmTable` for the UNITS_FACT relational table.
       MdmTable unitsTable = null;
       Query cubeQuery = null;
       String tablename="UNITS_FACT";

       try
       {
         unitsTable = (MdmTable)
                       mdmDBSchema.getTopLevelObject(tableName);
         cubeQuery = unitsTable.getQuery();
       }
       catch (Exception ex)
       {
         println("Could not get the " + tableName + " table. " + ex);
       }

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                         | Method and Description                                                                                                                                                                                                 |
    |-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                        | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmTable` method of the `MdmObjectVisitor` and passes that method this `MdmTable` and an `Object`. |
    | `void`                                                    | `addColumn``(`[`MdmColumn`](MdmColumn.md)` value)`<br>Adds an `MdmColumn` to the `List` of `MdmColumn` objects that are associated with this `MdmTable`.                                                               |
    | `java.util.List<`[`MdmColumn`](MdmColumn.md)`>`           | `getColumns``()`<br>Gets the `MdmColumn` objects that are associated with this `MdmTable`.                                                                                                                             |
    | [`MdmDatabaseSchema`](MdmDatabaseSchema.md)               | `getOwner``()`<br>Gets the `MdmDatabaseSchema` that owns this `MdmTable`.                                                                                                                                              |
    | [`Query`](../../syntax/Query.md)                          | `getQuery``()`<br>Gets the `Query` that is associated with this `MdmTable`.                                                                                                                                            |
    | [`MdmQueryColumn`](MdmQueryColumn.md)                     | `getQueryColumn``(java.lang.String name)`<br>Gets the specified `MdmQueryColumn`.                                                                                                                                      |
    | `java.util.List<`[`MdmQueryColumn`](MdmQueryColumn.md)`>` | `getQueryColumns``()`<br>Gets the `MdmQueryColumn` objects that are associated with this `MdmTable`.                                                                                                                   |
    | `java.lang.String`                                        | `getQueryName``()`<br>Gets the identifier of this `MdmTable`.                                                                                                                                                          |
    | `void`                                                    | `removeColumn``(`[`MdmColumn`](MdmColumn.md)` value)`<br>Removes an `MdmColumn` from the `List` of `MdmColumn` objects that are associated with this `MdmTable`.                                                       |
    | `void`                                                    | `setOwner``(`[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` owner)`<br>Specifies an `MdmDatabaseSchema` as the owner of this `MdmTable`.                                                                                 |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSource](MdmSource.md)

      [`getDataType`](MdmSource.md)`, `[`getSource`](MdmSource.md)`, `[`getType`](MdmSource.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)

      [`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmTable` method of the `MdmObjectVisitor` and passes that method this `MdmTable` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor` that implements the `Mdm11_ObjectVisitor` interface.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmTable` method.

    <!-- -->

    - #### getColumns

          public final java.util.List<MdmColumn> getColumns()

      Gets the `MdmColumn` objects that are associated with this `MdmTable`.
      Returns:
      A `List` of the `MdmColumn` objects associated with this `MdmTable`.

    <!-- -->

    - #### addColumn

          public void addColumn(MdmColumn value)

      Adds an `MdmColumn` to the `List` of `MdmColumn` objects that are associated with this `MdmTable`.
      Parameters:
      `value` - The `MdmColumn` to add to this `MdmTable`.

    <!-- -->

    - #### removeColumn

          public void removeColumn(MdmColumn value)

      Removes an `MdmColumn` from the `List` of `MdmColumn` objects that are associated with this `MdmTable`.
      Parameters:
      `value` - The `MdmColumn` to remove from this `MdmTable`.

    <!-- -->

    - #### getOwner

          public final MdmDatabaseSchema getOwner()

      Gets the `MdmDatabaseSchema` that owns this `MdmTable`.
      Overrides:
      [`getOwner`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      The `MdmDatabaseSchema` that owns this `MdmTable`.

    <!-- -->

    - #### setOwner

          public final void setOwner(MdmDatabaseSchema owner)

      Specifies an `MdmDatabaseSchema` as the owner of this `MdmTable`.
      Parameters:
      `owner` - The `MdmDatabaseSchema` to specify as the owner of this `MdmTable`.

    <!-- -->

    - #### getQuery

          public final Query getQuery()

      Gets the `Query` that is associated with this `MdmTable`.
      Specified by:
      [`getQuery`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Returns:
      The `Query` associated with this `MdmTable`.

    <!-- -->

    - #### getQueryColumns

          public final java.util.List<MdmQueryColumn> getQueryColumns()

      Gets the `MdmQueryColumn` objects that are associated with this `MdmTable`. The `MdmQueryColumn` objects for an `MdmTable` are instances of `MdmColumn`, so the `List` returned by this method has the same objects as the `List` returned by the `getColumns` method.
      Specified by:
      [`getQueryColumns`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Returns:
      A `List` of the `MdmQueryColumn` objects associated with this `MdmTable`.

    <!-- -->

    - #### getQueryName

          public final java.lang.String getQueryName()

      Gets the identifier of this `MdmTable`.
      Specified by:
      [`getQueryName`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Returns:
      A `String` that contains the identifier of this `MdmTable`.

    <!-- -->

    - #### getQueryColumn

          public MdmQueryColumn getQueryColumn(java.lang.String name)

      Gets the specified `MdmQueryColumn`.
      Specified by:
      [`getQueryColumn`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Parameters:
      `name` - A `String` that contains the name of an `MdmQueryColumn`.

      Returns:
      The `MdmQueryColumn` that has the specified name.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmSubDimension.md)
- [Next Class](MdmTimeDimension.md)

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
