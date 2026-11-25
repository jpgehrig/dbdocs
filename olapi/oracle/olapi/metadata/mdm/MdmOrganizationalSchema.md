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

- [Prev Class](MdmObjectVisitor.md)
- [Next Class](MdmPrimaryDimension.md)

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

## Class MdmOrganizationalSchema

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSchema](MdmSchema.md)

        - - oracle.olapi.metadata.mdm.MdmOrganizationalSchema

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmOrganizationalSchema
      extends MdmSchema

  An `MdmSchema` that organizes `MdmCube` and other `MdmObject` objects, including other `MdmOrganizationalSchema` objects, that are related by informational content. An `MdmOrganizationalSchema` is equivalent to a folder or directory that contains associated items. Because `MdmOrganizationalSchema` objects can contain other `MdmOrganizationalSchema` objects, they can be arranged in a nested structure.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                           | Method and Description                                                                                                                                                                                                                               |
    |---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                          | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmOrganizationalSchema` method of the `MdmObjectVisitor` and passes that method this `MdmOrganizationalSchema` and an `Object`. |
    | `void`                                      | `addOrganizationalSchema``(MdmOrganizationalSchema subschema)`<br>Adds the specified `MdmOrganizationalSchema` to this `MdmOrganizationalSchema`.                                                                                                    |
    | `void`                                      | `addSubSchema``(`[`MdmSchema`](MdmSchema.md)` subschema)`<br>Adds the specified `MdmSchema` to this `MdmOrganizationalSchema`.                                                                                                                       |
    | `java.lang.String`                          | `getNamespace``()`<br>Gets the namespace of this `MdmOrganizationalSchema`.                                                                                                                                                                          |
    | `java.util.List`                            | `getOrganizationalSchemas``()`<br>Gets the `MdmOrganizationalSchema` objects that this `MdmOrganizationalSchema` contains.                                                                                                                           |
    | [`MdmDatabaseSchema`](MdmDatabaseSchema.md) | `getOwner``()`<br>Gets the `MdmDatabaseSchema` that owns this `MdmOrganizationalSchema`.                                                                                                                                                             |
    | `java.util.List`                            | `getPersistentLanguages``()`<br>Gets the languages in which descriptions are available of this `MdmOrganizationalSchema` and the objects it contains.                                                                                                |
    | `java.util.List`                            | `getSubSchemas``()`<br>Gets the `MdmSchema` objects that this `MdmOrganizationalSchema` contains.                                                                                                                                                    |
    | `void`                                      | `removeOrganizationalSchema``(MdmOrganizationalSchema subschema)`<br>Removes the specified `MdmOrganizationalSchema` from this `MdmOrganizationalSchema`.                                                                                            |
    | `void`                                      | `removeSubSchema``(`[`MdmSchema`](MdmSchema.md)` subschema)`<br>Removes the specified `MdmSchema` from this `MdmOrganizationalSchema`.                                                                                                               |
    | `void`                                      | `setOwner``(`[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` schema)`<br>Specifies an `MdmDatabaseSchema` as the owner of this `MdmOrganizationalSchema`.                                                                                               |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSchema](MdmSchema.md)

      [`addCube`](MdmSchema.md)`, `[`addDimension`](MdmSchema.md)`, `[`addMeasure`](MdmSchema.md)`, `[`getCubes`](MdmSchema.md)`, `[`getDimensions`](MdmSchema.md)`, `[`getMeasureDimension`](MdmSchema.md)`, `[`getMeasures`](MdmSchema.md)`, `[`getOuterSchema`](MdmSchema.md)`, `[`removeCube`](MdmSchema.md)`, `[`removeDimension`](MdmSchema.md)`, `[`removeMeasure`](MdmSchema.md)

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

      Calls the `visitMdmOrganizationalSchema` method of the `MdmObjectVisitor` and passes that method this `MdmOrganizationalSchema` and an `Object`.
      Overrides:
      [`acceptVisitor`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor` that implements the `Mdm11_ObjectVisitor` interface.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmOrganizationalSchema` method.

    <!-- -->

    - #### addOrganizationalSchema

          public final void addOrganizationalSchema(MdmOrganizationalSchema subschema)

      Adds the specified `MdmOrganizationalSchema` to this `MdmOrganizationalSchema`.
      Parameters:
      `subschema` - The `MdmOrganizationalSchema` to add to this `MdmOrganizationalSchema`.

    <!-- -->

    - #### addSubSchema

          public final void addSubSchema(MdmSchema subschema)

      Adds the specified `MdmSchema` to this `MdmOrganizationalSchema`. The `MdmSchema` must be an instance of an `MdmOrganizationalSchema`.
      Overrides:
      [`addSubSchema`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Parameters:
      `subschema` - The `MdmSchema` to add to this `MdmOrganizationalSchema`.

    <!-- -->

    - #### removeOrganizationalSchema

          public final void removeOrganizationalSchema(MdmOrganizationalSchema subschema)

      Removes the specified `MdmOrganizationalSchema` from this `MdmOrganizationalSchema`.
      Parameters:
      `subschema` - The `MdmOrganizationalSchema` to remove from this `MdmOrganizationalSchema`.

    <!-- -->

    - #### removeSubSchema

          public final void removeSubSchema(MdmSchema subschema)

      Removes the specified `MdmSchema` from this `MdmOrganizationalSchema`. The `MdmSchema` must be an instance of an `MdmOrganizationalSchema`.
      Overrides:
      [`removeSubSchema`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Parameters:
      `subschema` - The `MdmSchema` to remove from this `MdmOrganizationalSchema`.

    <!-- -->

    - #### getOrganizationalSchemas

          public final java.util.List getOrganizationalSchemas()

      Gets the `MdmOrganizationalSchema` objects that this `MdmOrganizationalSchema` contains.
      Returns:
      A `List` of `MdmOrganizationalSchema` objects that this `MdmOrganizationalSchema` contains.

    <!-- -->

    - #### getSubSchemas

          public final java.util.List getSubSchemas()

      Gets the `MdmSchema` objects that this `MdmOrganizationalSchema` contains. The `MdmSchema` objects are instances of `MdmOrganizationalSchema`.
      Overrides:
      [`getSubSchemas`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Returns:
      A `List` of `MdmOrganizationalSchema` objects that this `MdmOrganizationalSchema` contains.

    <!-- -->

    - #### getOwner

          public final MdmDatabaseSchema getOwner()

      Gets the `MdmDatabaseSchema` that owns this `MdmOrganizationalSchema`.
      Overrides:
      [`getOwner`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      The `MdmDatabaseSchema` that owns this `MdmOrganizationalSchema`.

    <!-- -->

    - #### setOwner

          public final void setOwner(MdmDatabaseSchema schema)

      Specifies an `MdmDatabaseSchema` as the owner of this `MdmOrganizationalSchema`.
      Parameters:
      `schema` - The `MdmDatabaseSchema` to own this `MdmOrganizationalSchema`.

    <!-- -->

    - #### getNamespace

          public final java.lang.String getNamespace()

      Gets the namespace of this `MdmOrganizationalSchema`. For information on namespaces, see [Using Namespaces](MdmMetadataProvider.md) in the description of `MdmMetadataProvider`.
      Returns:
      A `String` that contains the namespace of this `MdmOrganizationalSchema`.

    <!-- -->

    - #### getPersistentLanguages

          public java.util.List getPersistentLanguages()

      Gets the languages in which descriptions are available of this `MdmOrganizationalSchema` and the objects it contains.
      Returns:
      A `List` of `String` objects that contain the names of NLS languages.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmObjectVisitor.md)
- [Next Class](MdmPrimaryDimension.md)

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
