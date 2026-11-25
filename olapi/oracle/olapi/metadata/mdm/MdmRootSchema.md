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

- [Prev Class](MdmQueryColumn.md)
- [Next Class](MdmSchema.md)

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

## Class MdmRootSchema

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSchema](MdmSchema.md)

        - - oracle.olapi.metadata.mdm.MdmRootSchema

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmRootSchema
      extends MdmSchema

  The top-level `MdmSchema` of a `MdmMetadataProvider`. An application gets the `MdmRootSchema` by calling the [`getRootSchema`](MdmMetadataProvider.md) method of the `MdmMetadataProvider`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                                                                           |
    |-----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                              | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmRootSchema` method of the `MdmObjectVisitor` and passes that method this `MdmRootSchema` and an `Object`. |
    | `void`                                                          | `addDatabaseSchema``(`[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` subschema)`<br>Adds the specified `MdmDatabaseSchema` to this `MdmRootSchema`.                                                                                |
    | `void`                                                          | `addSubSchema``(`[`MdmSchema`](MdmSchema.md)` subschema)`<br>Adds the specified `MdmSchema` to this `MdmRootSchema`.                                                                                                             |
    | `java.util.List`                                                | `getCubes``()`<br>Gets the `MdmCube` objects that the `MdmRootSchema` contains.                                                                                                                                                  |
    | [`MdmDatabaseSchema`](MdmDatabaseSchema.md)                     | `getDatabaseSchema``(java.lang.String name)`<br>Gets the specified `MdmDatabaseSchema` contained by this `MdmRootSchema`.                                                                                                        |
    | `java.util.List<`[`MdmDatabaseSchema`](MdmDatabaseSchema.md)`>` | `getDatabaseSchemas``()`<br>Gets the `MdmDatabaseSchema` objects that this `MdmRootSchema` contains.                                                                                                                             |
    | `java.util.List`                                                | `getDimensions``()`<br>Gets the `MdmDimension` objects that the `MdmRootSchema` contains.                                                                                                                                        |
    | `java.util.List`                                                | `getMeasures``()`<br>Gets the `MdmMeasure` objects that the `MdmRootSchema` contains.                                                                                                                                            |
    | [`MdmSchema`](MdmSchema.md)                                     | `getOwner``()`<br>Gets this `MdmRootSchema` because it is the top-level `MdmSchema`.                                                                                                                                             |
    | `void`                                                          | `removeDatabaseSchema``(`[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` subschema)`<br>Removes the specified `MdmDatabaseSchema` from this `MdmRootSchema`.                                                                        |
    | `void`                                                          | `removeSubSchema``(`[`MdmSchema`](MdmSchema.md)` subschema)`<br>Removes the specified `MdmSchema` from this `MdmRootSchema`.                                                                                                     |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSchema](MdmSchema.md)

      [`addCube`](MdmSchema.md)`, `[`addDimension`](MdmSchema.md)`, `[`addMeasure`](MdmSchema.md)`, `[`getMeasureDimension`](MdmSchema.md)`, `[`getOuterSchema`](MdmSchema.md)`, `[`getSubSchemas`](MdmSchema.md)`, `[`removeCube`](MdmSchema.md)`, `[`removeDimension`](MdmSchema.md)`, `[`removeMeasure`](MdmSchema.md)

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

      Calls the `visitMdmRootSchema` method of the `MdmObjectVisitor` and passes that method this `MdmRootSchema` and an `Object`.
      Overrides:
      [`acceptVisitor`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor` that implements the `Mdm11_ObjectVisitor` interface.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmMeasure` method.

    <!-- -->

    - #### addDatabaseSchema

          public final void addDatabaseSchema(MdmDatabaseSchema subschema)

      Adds the specified `MdmDatabaseSchema` to this `MdmRootSchema`.
      Parameters:
      `subschema` - The `MdmDatabaseSchema` to add to this `MdmRootSchema`.

    <!-- -->

    - #### addSubSchema

          public final void addSubSchema(MdmSchema subschema)

      Adds the specified `MdmSchema` to this `MdmRootSchema`. The `MdmSchema` must be an instance of an `MdmDatabaseSchema`.
      Overrides:
      [`addSubSchema`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Parameters:
      `subschema` - The `MdmSchema` to add to this `MdmRootSchema`.

    <!-- -->

    - #### removeDatabaseSchema

          public final void removeDatabaseSchema(MdmDatabaseSchema subschema)

      Removes the specified `MdmDatabaseSchema` from this `MdmRootSchema`.
      Parameters:
      `subschema` - The `MdmDatabaseSchema` to remove from this `MdmRootSchema`.

    <!-- -->

    - #### removeSubSchema

          public final void removeSubSchema(MdmSchema subschema)

      Removes the specified `MdmSchema` from this `MdmRootSchema`. The `MdmSchema` must be an instance of an `MdmDatabaseSchema`.
      Overrides:
      [`removeSubSchema`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Parameters:
      `subschema` - The `MdmSchema` to remove from this `MdmRootSchema`.

    <!-- -->

    - #### getDatabaseSchemas

          public final java.util.List<MdmDatabaseSchema> getDatabaseSchemas()

      Gets the `MdmDatabaseSchema` objects that this `MdmRootSchema` contains.
      Returns:
      A `List` of the `MdmDatabaseSchema` objects that this `MdmRootSchema` contains.

    <!-- -->

    - #### getDatabaseSchema

          public final MdmDatabaseSchema getDatabaseSchema(java.lang.String name)

      Gets the specified `MdmDatabaseSchema` contained by this `MdmRootSchema`.
      Returns:
      The specified `MdmDatabaseSchema`.

    <!-- -->

    - #### getOwner

          public final MdmSchema getOwner()

      Gets this `MdmRootSchema` because it is the top-level `MdmSchema`.
      Overrides:
      [`getOwner`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      This `MdmRootSchema`.

    <!-- -->

    - #### getMeasures

          public java.util.List getMeasures()

      Gets the `MdmMeasure` objects that the `MdmRootSchema` contains.
      Overrides:
      [`getMeasures`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Returns:
      A `List` of `MdmMeasure` objects that the `MdmRootSchema` contains.

    <!-- -->

    - #### getDimensions

          public java.util.List getDimensions()

      Gets the `MdmDimension` objects that the `MdmRootSchema` contains.
      Overrides:
      [`getDimensions`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Returns:
      A `List` of `MdmDimension` objects that the `MdmRootSchema` contains.

    <!-- -->

    - #### getCubes

          public java.util.List getCubes()

      Gets the `MdmCube` objects that the `MdmRootSchema` contains.
      Overrides:
      [`getCubes`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Returns:
      A `List` of `MdmCube` objects that the `MdmRootSchema` contains.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmQueryColumn.md)
- [Next Class](MdmSchema.md)

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
