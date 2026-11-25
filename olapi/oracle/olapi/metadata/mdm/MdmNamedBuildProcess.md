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

- [Prev Class](MdmMultiValuedDerivedAttribute.md)
- [Next Class](MdmObject.md)

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

## Class MdmNamedBuildProcess

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - oracle.olapi.metadata.mdm.MdmNamedBuildProcess

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmNamedBuildProcess
      extends MdmObject

  An `MdmObject` that represents a named `oracle.olapi.syntax.BuildProcess` for an `MdmDatabaseSchema`. An application gets an existing `MdmNamedBuildProcess` or creates a new one by calling the [`findOrCreateNamedBuildProcess`](MdmDatabaseSchema.md) method of the `MdmDatabaseSchema`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                              | Method and Description                                                                                                                                                                                                                                   |
    |------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                             | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmNamedBuildProcess` method of the specified `MdmObjectVisitor` and passes that method this `MdmNamedBuildProcess` and an `Object`. |
    | [`BuildProcess`](../../syntax/BuildProcess.md) | `getBuildProcess``()`<br>Gets the `BuildProcess` associated with this `MdmNamedBuildProcess`.                                                                                                                                                            |
    | [`MdmDatabaseSchema`](MdmDatabaseSchema.md)    | `getOwner``()`<br>Gets the `MdmDatabaseSchema` that owns this `MdmNamedBuildProcess`.                                                                                                                                                                    |
    | `java.util.List`                               | `getPersistentLanguages``()`<br>Returns the list of all languages used for descriptions of this `MdmNamedBuildProcess`.                                                                                                                                  |
    | `void`                                         | `setBuildProcess``(`[`BuildProcess`](../../syntax/BuildProcess.md)` input)`<br>Specifies a `BuildProcess` to associate with this `MdmNamedBuildProcess`.                                                                                                 |
    | `void`                                         | `setOwner``(`[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` owner)`<br>Specifies an `MdmDatabaseSchema` as the owner of this `MdmNamedBuildProcess`.                                                                                                       |

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

      Calls the `visitMdmNamedBuildProcess` method of the specified `MdmObjectVisitor` and passes that method this `MdmNamedBuildProcess` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `Mdm11_ObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `MdmNamedBuildProcess` method.

    <!-- -->

    - #### getBuildProcess

          public final BuildProcess getBuildProcess()

      Gets the `BuildProcess` associated with this `MdmNamedBuildProcess`.
      Returns:
      The `BuildProcess` associated with this `MdmNamedBuildProcess`.

    <!-- -->

    - #### setBuildProcess

          public final void setBuildProcess(BuildProcess input)

      Specifies a `BuildProcess` to associate with this `MdmNamedBuildProcess`.
      Parameters:
      `input` - The `BuildProcess` to associate with this `MdmNamedBuildProcess`.

    <!-- -->

    - #### getOwner

          public final MdmDatabaseSchema getOwner()

      Gets the `MdmDatabaseSchema` that owns this `MdmNamedBuildProcess`.
      Overrides:
      [`getOwner`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      The `BuildProcess` that owns this `MdmNamedBuildProcess`.

    <!-- -->

    - #### setOwner

          public final void setOwner(MdmDatabaseSchema owner)

      Specifies an `MdmDatabaseSchema` as the owner of this `MdmNamedBuildProcess`.
      Parameters:
      `owner` - The `MdmDatabaseSchema` to own this `MdmNamedBuildProcess`.

    <!-- -->

    - #### getPersistentLanguages

          public java.util.List getPersistentLanguages()

      Returns the list of all languages used for descriptions of this `MdmNamedBuildProcess`.
      Returns:
      List of Strings representing NLS Languages.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmMultiValuedDerivedAttribute.md)
- [Next Class](MdmObject.md)

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
