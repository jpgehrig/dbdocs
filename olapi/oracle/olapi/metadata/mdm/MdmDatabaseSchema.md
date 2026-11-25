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

- [Prev Class](MdmCustomMember.md)
- [Next Class](MdmDerivedAttribute.md)

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

## Class MdmDatabaseSchema

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSchema](MdmSchema.md)

        - - oracle.olapi.metadata.mdm.MdmDatabaseSchema

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmDatabaseSchema
      extends MdmSchema

  An `MdmSchema` that represents a relational database schema. A schema is owned by a database user and has the same name as that user. Each user owns a single schema.
  A schema is a collection of logical structures of data, which are the schema objects. You use an `MdmDatabaseSchema` to create or get, or add or remove, schema objects such as an `AW` or an `MdmCube`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                    | Method and Description                                                                                                                                                                                                                   |
    |----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                                   | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmDatabaseSchema` method of the `MdmObjectVisitor` and passes that method this `MdmDatabaseSchema` and an `Object`. |
    | `void`                                                               | `addAW``(`[`AW`](../deployment/AW.md)` obj)`<br>Adds the specified `AW` to this `MdmDatabaseSchema`.                                                                                                                                     |
    | `void`                                                               | `addNamedBuildProcess``(`[`MdmNamedBuildProcess`](MdmNamedBuildProcess.md)` namedBuildProc)`<br>Adds the specified `MdmNamedBuildProcess` to this `MdmDatabaseSchema`.                                                                   |
    | `void`                                                               | `addOrganizationalSchema``(`[`MdmOrganizationalSchema`](MdmOrganizationalSchema.md)` subschema)`<br>Adds the specified `MdmOrganizationalSchema` to this `MdmDatabaseSchema`.                                                            |
    | `void`                                                               | `addSchemaObject``(`[`BaseMetadataObject`](../BaseMetadataObject.md)` obj)`<br>Adds the specified `BaseMetadataObject` to this `MdmDatabaseSchema`.                                                                                      |
    | `void`                                                               | `addSubSchema``(`[`MdmSchema`](MdmSchema.md)` subschema)`<br>Adds the specified `MdmSchema` to this `MdmDatabaseSchema`.                                                                                                                 |
    | [`AW`](../deployment/AW.md)                                          | `findOrCreateAW``(java.lang.String publicName)`<br>Gets the specified `AW` or, if it does not already exist, creates a new one.                                                                                                          |
    | [`MdmCube`](MdmCube.md)                                              | `findOrCreateCube``(java.lang.String publicName)`<br>Gets the specified `MdmCube` or, if it does not already exist, creates a new one.                                                                                                   |
    | [`MdmCube`](MdmCube.md)                                              | `findOrCreateCube``(java.lang.String publicName, java.lang.String nameSpace)`<br>Gets a 10*g* `MdmCube` or, if that object does not exist, creates a new 11*g* one.                                                                      |
    | [`MdmNamedBuildProcess`](MdmNamedBuildProcess.md)                    | `findOrCreateNamedBuildProcess``(java.lang.String publicName)`<br>Gets the specified `MdmNamedBuildProcess` or, if it does not already exist, creates a new one.                                                                         |
    | [`MdmOrganizationalSchema`](MdmOrganizationalSchema.md)              | `findOrCreateOrganizationalSchema``(java.lang.String publicName)`<br>Gets the specified `MdmOrganizationalSchema` or, if it does not already exist, creates a new `MdmOrganizationalSchema` for this `MdmDatabaseSchema`.                |
    | [`MdmOrganizationalSchema`](MdmOrganizationalSchema.md)              | `findOrCreateOrganizationalSchema``(java.lang.String publicName, java.lang.String nameSpace)`<br>Gets the specified 10*g* measure folder or, if that object does not exist, creates a new 11*g* `MdmOrganizationalSchema`.               |
    | [`MdmStandardDimension`](MdmStandardDimension.md)                    | `findOrCreateStandardDimension``(java.lang.String publicName)`<br>Gets the specified `MdmStandardDimension` or, if it does not already exist, creates a new one.                                                                         |
    | [`MdmStandardDimension`](MdmStandardDimension.md)                    | `findOrCreateStandardDimension``(java.lang.String publicName, java.lang.String nameSpace)`<br>Gets a 10*g* `MdmStandardDimension` or, if that object does not exist, creates a new 11*g* one.                                            |
    | [`MdmTimeDimension`](MdmTimeDimension.md)                            | `findOrCreateTimeDimension``(java.lang.String publicName)`<br>Gets the specified `MdmTimeDimension` or, if it does not already exist, creates a new one.                                                                                 |
    | [`MdmTimeDimension`](MdmTimeDimension.md)                            | `findOrCreateTimeDimension``(java.lang.String publicName, java.lang.String nameSpace)`<br>Gets a 10*g* `MdmTimeDimension` or, if that object does not exist, creates a new 11*g* one.                                                    |
    | `java.util.List<`[`AW`](../deployment/AW.md)`>`                      | `getAWs``()`<br>Gets the `AW` objects that this `MdmDatabaseSchema` contains.                                                                                                                                                            |
    | `java.util.List`                                                     | `getMeasures``()`<br>Gets the `MdmMeasure` objects that the `MdmDatabaseSchema` contains.                                                                                                                                                |
    | `java.util.List`                                                     | `getNamedBuildProcesses``()`<br>Gets the `MdmNamedBuildProcess` objects that this `MdmDatabaseSchema` contains.                                                                                                                          |
    | `java.util.List`                                                     | `getOrganizationalSchemas``()`<br>Gets all of the `MdmOrganizationalSchema` objects that this `MdmDatabaseSchema` contains.                                                                                                              |
    | `MdmDatabaseSchema`                                                  | `getOwner``()`<br>Gets this `MdmDatabaseSchema`.                                                                                                                                                                                         |
    | `java.util.List`                                                     | `getPersistentLanguages``()`<br>Gets the languages in which descriptions are available of this `MdmDatabaseSchema` and the objects owned by it.                                                                                          |
    | `java.util.List<`[`BaseMetadataObject`](../BaseMetadataObject.md)`>` | `getSchemaObjects``()`<br>Gets all of the `BaseMetadataObject` objects that are owned by this `MdmDatabaseSchema`.                                                                                                                       |
    | `java.util.List`                                                     | `getSubSchemas``()`<br>Gets the top-level `MdmOrganizationalSchema` objects that this `MdmDatabaseSchema` contains.                                                                                                                      |
    | [`BaseMetadataObject`](../BaseMetadataObject.md)                     | `getTopLevelObject``(java.lang.String name)`<br>Gets the top-level object that has the specified name.                                                                                                                                   |
    | `void`                                                               | `removeAW``(`[`AW`](../deployment/AW.md)` aw)`<br>Removes the specified `AW` from this `MdmDatabaseSchema`.                                                                                                                              |
    | `void`                                                               | `removeAW``(`[`AW`](../deployment/AW.md)` aw, boolean bRemoveAllSubObjects)`<br>Removes the specified `AW` from this `MdmDatabaseSchema` and possibly all of the objects that are deployed with the `AW`.                                |
    | `void`                                                               | `removeNamedBuildProcess``(`[`MdmNamedBuildProcess`](MdmNamedBuildProcess.md)` namedBuildProc)`<br>Removes the specified `MdmNamedBuildProcess` from this `MdmDatabaseSchema`.                                                           |
    | `void`                                                               | `removeOrganizationalSchema``(`[`MdmOrganizationalSchema`](MdmOrganizationalSchema.md)` subschema)`<br>Removes the specified `MdmOrganizationalSchema` from this `MdmDatabaseSchema`.                                                    |
    | `void`                                                               | `removeSchemaObject``(`[`BaseMetadataObject`](../BaseMetadataObject.md)` obj)`<br>Removes the specified `BaseMetadataObject` from this `MdmDatabaseSchema`.                                                                              |
    | `void`                                                               | `removeSubSchema``(`[`MdmSchema`](MdmSchema.md)` subschema)`<br>Removes the specified `MdmSchema` from this `MdmDatabaseSchema`.                                                                                                         |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSchema](MdmSchema.md)

      [`addCube`](MdmSchema.md)`, `[`addDimension`](MdmSchema.md)`, `[`addMeasure`](MdmSchema.md)`, `[`getCubes`](MdmSchema.md)`, `[`getDimensions`](MdmSchema.md)`, `[`getMeasureDimension`](MdmSchema.md)`, `[`getOuterSchema`](MdmSchema.md)`, `[`removeCube`](MdmSchema.md)`, `[`removeDimension`](MdmSchema.md)`, `[`removeMeasure`](MdmSchema.md)

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

      Calls the `visitMdmDatabaseSchema` method of the `MdmObjectVisitor` and passes that method this `MdmDatabaseSchema` and an `Object`.
      Overrides:
      [`acceptVisitor`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor` that implements the `Mdm11_ObjectVisitor` interface.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmDatabaseSchema` method.

    <!-- -->

    - #### getTopLevelObject

          public BaseMetadataObject getTopLevelObject(java.lang.String name)

      Gets the top-level object that has the specified name. The following objects are top-level objects of an `MdmDatabaseSchema`:
              AW
              MdmCube
              MdmNamedBuildProcess
              MdmOrganizationalSchema
              MdmPrimaryDimension
              MdmTable


      To get an `AW` object, you must include the object type after the object name. The following example gets the `AW` named GLOBAL_AWJ and the `MdmPrimaryDimension` named PRODUCT_AWJ from the `MdmDatabaseSchema` `mdmDBSchema`.

           AW globalAWJ = (AW)mdmDBSchema.getTopLevelObject("GLOBAL_AWJ.AW");
           MdmPrimaryDimension mdmProdDim =
             (MdmPrimaryDimension)mdmDBSchema.getTopLevelObject("PRODUCT_AWJ");


      Parameters:
      `name` - A `String` that contains the name of the object to get.

      Returns:
      The `MdmSource` that has the specified name.

    <!-- -->

    - #### addOrganizationalSchema

          public final void addOrganizationalSchema(MdmOrganizationalSchema subschema)

      Adds the specified `MdmOrganizationalSchema` to this `MdmDatabaseSchema`.
      Parameters:
      `subschema` - The `MdmOrganizationalSchema` to add to this `MdmDatabaseSchema`.

    <!-- -->

    - #### addSubSchema

          public final void addSubSchema(MdmSchema subschema)

      Adds the specified `MdmSchema` to this `MdmDatabaseSchema`. The `MdmSchema` must be an instance of `MdmOrganizationalSchema`.
      Overrides:
      [`addSubSchema`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Parameters:
      `subschema` - The `MdmSchema` to add to this `MdmDatabaseSchema`.

    <!-- -->

    - #### addNamedBuildProcess

          public final void addNamedBuildProcess(MdmNamedBuildProcess namedBuildProc)

      Adds the specified `MdmNamedBuildProcess` to this `MdmDatabaseSchema`.
      Parameters:
      `namedBuildProc` - The `MdmNamedBuildProcess` to add to this `MdmDatabaseSchema`.

    <!-- -->

    - #### removeOrganizationalSchema

          public final void removeOrganizationalSchema(MdmOrganizationalSchema subschema)

      Removes the specified `MdmOrganizationalSchema` from this `MdmDatabaseSchema`.
      Parameters:
      `subschema` - The `MdmOrganizationalSchema` to remove from this `MdmDatabaseSchema`.

    <!-- -->

    - #### removeSubSchema

          public final void removeSubSchema(MdmSchema subschema)

      Removes the specified `MdmSchema` from this `MdmDatabaseSchema`. The `MdmSchema` must be an instance of `MdmOrganizationalSchema`.
      Overrides:
      [`removeSubSchema`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Parameters:
      `subschema` - The `MdmSchema` to remove from this `MdmDatabaseSchema`.

    <!-- -->

    - #### removeNamedBuildProcess

          public final void removeNamedBuildProcess(MdmNamedBuildProcess namedBuildProc)

      Removes the specified `MdmNamedBuildProcess` from this `MdmDatabaseSchema`.
      Parameters:
      `namedBuildProc` - The `MdmNamedBuildProcess` to remove from this `MdmDatabaseSchema`.

    <!-- -->

    - #### getOrganizationalSchemas

          public final java.util.List getOrganizationalSchemas()

      Gets all of the `MdmOrganizationalSchema` objects that this `MdmDatabaseSchema` contains. The list includes `MdmOrganizationalSchema` objects that are subschemas of other `MdmOrganizationalSchema` objects.
      Returns:
      A `List` of all of the `MdmOrganizationalSchema` objects of this `MdmDatabaseSchema`.

    <!-- -->

    - #### getSubSchemas

          public final java.util.List getSubSchemas()

      Gets the top-level `MdmOrganizationalSchema` objects that this `MdmDatabaseSchema` contains. This method does not return any subschemas of an `MdmOrganizationalSchema`.
      Overrides:
      [`getSubSchemas`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Returns:
      A `List` of the top-level `MdmOrganizationalSchema` objects of this `MdmDatabaseSchema`.

    <!-- -->

    - #### getNamedBuildProcesses

          public final java.util.List getNamedBuildProcesses()

      Gets the `MdmNamedBuildProcess` objects that this `MdmDatabaseSchema` contains.
      Returns:
      A `List` of `MdmNamedBuildProcess` objects that this `MdmDatabaseSchema` contains.

    <!-- -->

    - #### getOwner

          public final MdmDatabaseSchema getOwner()

      Gets this `MdmDatabaseSchema`.
      Overrides:
      [`getOwner`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      This `MdmDatabaseSchema`.

    <!-- -->

    - #### addSchemaObject

          public final void addSchemaObject(BaseMetadataObject obj)

      Adds the specified `BaseMetadataObject` to this `MdmDatabaseSchema`.
      Parameters:
      `obj` - The `BaseMetadataObject` to add to this `MdmDatabaseSchema`.

    <!-- -->

    - #### removeSchemaObject

          public final void removeSchemaObject(BaseMetadataObject obj)

      Removes the specified `BaseMetadataObject` from this `MdmDatabaseSchema`.
      Parameters:
      `obj` - The `BaseMetadataObject` to remove from this `MdmDatabaseSchema`.

    <!-- -->

    - #### getSchemaObjects

          public final java.util.List<BaseMetadataObject> getSchemaObjects()

      Gets all of the `BaseMetadataObject` objects that are owned by this `MdmDatabaseSchema`.
      Returns:
      A `List` of the `BaseMetadataObject` objects owned by this `MdmDatabaseSchema`.

    <!-- -->

    - #### findOrCreateOrganizationalSchema

          public MdmOrganizationalSchema findOrCreateOrganizationalSchema(java.lang.String publicName)

      Gets the specified `MdmOrganizationalSchema` or, if it does not already exist, creates a new `MdmOrganizationalSchema` for this `MdmDatabaseSchema`.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmOrganizationalSchema` to get or create.

      Returns:
      The specified `MdmOrganizationalSchema` or a new one with the specified name.

    <!-- -->

    - #### findOrCreateOrganizationalSchema

          public MdmOrganizationalSchema findOrCreateOrganizationalSchema(java.lang.String publicName,
                                                                          java.lang.String nameSpace)

      Gets the specified 10*g* measure folder or, if that object does not exist, creates a new 11*g* `MdmOrganizationalSchema`. The `nameSpace` parameter can be one of the `MdmMetadataProvider` static constant fields or one of the values in the `List` returned by the `getValidNamespaces` method of the `MdmMetadataProvider`.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmOrganizationalSchema` to get or create.

      `nameSpace` - A `String` that contains a valid organizational schema namespace.

      Returns:
      The specified 10*g* measure folder or a new 11*g* `MdmOrganizationalSchema`.

    <!-- -->

    - #### findOrCreateAW

          public AW findOrCreateAW(java.lang.String publicName)

      Gets the specified `AW` or, if it does not already exist, creates a new one.
      Parameters:
      `publicName` - A `String` that contains the name of the `AW` to get or create.

      Returns:
      The specified `AW` or a new one.

    <!-- -->

    - #### findOrCreateStandardDimension

          public MdmStandardDimension findOrCreateStandardDimension(java.lang.String publicName)

      Gets the specified `MdmStandardDimension` or, if it does not already exist, creates a new one.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmStandardDimension` to get or create.

      Returns:
      The specified `MdmStandardDimension` or a new one.

    <!-- -->

    - #### findOrCreateStandardDimension

          public MdmStandardDimension findOrCreateStandardDimension(java.lang.String publicName,
                                                                    java.lang.String nameSpace)

      Gets a 10*g* `MdmStandardDimension` or, if that object does not exist, creates a new 11*g* one. The `nameSpace` parameter can be one of the `MdmMetadataProvider` static constant fields or one of the values in the `List` returned by the `getValidNamespaces` method of the `MdmMetadataProvider`.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmStandardDimension` to get or create.

      `nameSpace` - A `String` that contains a valid dimension namespace.

      Returns:
      The specified 10*g* `MdmStandardDimension` or a new 11*g* one.

    <!-- -->

    - #### findOrCreateTimeDimension

          public MdmTimeDimension findOrCreateTimeDimension(java.lang.String publicName)

      Gets the specified `MdmTimeDimension` or, if it does not already exist, creates a new one.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmTimeDimension` to get or create.

      Returns:
      The specified `MdmTimeDimension` or a new one.

    <!-- -->

    - #### findOrCreateTimeDimension

          public MdmTimeDimension findOrCreateTimeDimension(java.lang.String publicName,
                                                            java.lang.String nameSpace)

      Gets a 10*g* `MdmTimeDimension` or, if that object does not exist, creates a new 11*g* one. The namespace can be one of the `MdmMetadataProvider` static constant fields or one of the values in the `List` returned by the `getValidNamespaces` method of an `MdmMetadataProvider`.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmTimeDimension` to get or create.

      `nameSpace` - A `String` that contains a valid dimension namespace.

      Returns:
      The specified 10*g* `MdmTimeDimension` or a new 11*g* one.

    <!-- -->

    - #### findOrCreateCube

          public MdmCube findOrCreateCube(java.lang.String publicName)

      Gets the specified `MdmCube` or, if it does not already exist, creates a new one.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmCube` to get or create.

      Returns:
      The specified `MdmCube` or a new one.

    <!-- -->

    - #### findOrCreateCube

          public MdmCube findOrCreateCube(java.lang.String publicName,
                                          java.lang.String nameSpace)

      Gets a 10*g* `MdmCube` or, if that object does not exist, creates a new 11*g* one. The `nameSpace` parameter can be one of the `MdmMetadataProvider` static constant fields or one of the values in the `List` returned by the `getValidNamespaces` method of the `MdmMetadataProvider`.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmCube` to get or create.

      `nameSpace` - A `String` that contains a valid cube namespace.

      Returns:
      The specified 10*g* `MdmCube` or a new 11*g* one.

    <!-- -->

    - #### findOrCreateNamedBuildProcess

          public MdmNamedBuildProcess findOrCreateNamedBuildProcess(java.lang.String publicName)

      Gets the specified `MdmNamedBuildProcess` or, if it does not already exist, creates a new one.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmNamedBuildProcess` to get or create.

      Returns:
      The specified `MdmNamedBuildProcess` or a new one.

    <!-- -->

    - #### getAWs

          public final java.util.List<AW> getAWs()

      Gets the `AW` objects that this `MdmDatabaseSchema` contains.
      Returns:
      A `List` of the `AW` objects of this `MdmDatabaseSchema`.

    <!-- -->

    - #### addAW

          public final void addAW(AW obj)

      Adds the specified `AW` to this `MdmDatabaseSchema`.
      Parameters:
      `obj` - The `AW` to add to this `MdmDatabaseSchema`.

    <!-- -->

    - #### removeAW

          public final void removeAW(AW aw)

      Removes the specified `AW` from this `MdmDatabaseSchema`.
      Parameters:
      `aw` - The `AW` to remove from this `MdmDatabaseSchema`.

    <!-- -->

    - #### removeAW

          public final void removeAW(AW aw,
                                     boolean bRemoveAllSubObjects)

      Removes the specified `AW` from this `MdmDatabaseSchema` and possibly all of the objects that are deployed with the `AW`.
      Parameters:
      `aw` - The `AW` to remove from this `MdmDatabaseSchema`.

      `bRemoveAllSubObjects` - A `boolean` that if `true` specifies removing all of the objects that are deployed with the `AW`. If `false`, the parameter specifies removing the `AW` but not removing the objects deployed with it.

    <!-- -->

    - #### getMeasures

          public java.util.List getMeasures()

      Gets the `MdmMeasure` objects that the `MdmDatabaseSchema` contains.
      Overrides:
      [`getMeasures`](MdmSchema.md) in class [`MdmSchema`](MdmSchema.md)

      Returns:
      A `List` of `MdmMeasure` objects that the `MdmDatabaseSchema` contains.

    <!-- -->

    - #### getPersistentLanguages

          public java.util.List getPersistentLanguages()

      Gets the languages in which descriptions are available of this `MdmDatabaseSchema` and the objects owned by it. The languages include those available for `AttributeMap` objects that are contained by `DimensionMap` objects that are contained directly or indirectly by the `MdmPrimaryDimension` objects of the `MdmDatabaseSchema`.
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

- [Prev Class](MdmCustomMember.md)
- [Next Class](MdmDerivedAttribute.md)

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
