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

- [Prev Class](MdmNamedBuildProcess.md)
- [Next Class](MdmObjectVisitor.md)

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

## Class MdmObject

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - oracle.olapi.metadata.mdm.MdmObject

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [MdmAssignment](MdmAssignment.md), [MdmCustomMember](MdmCustomMember.md), [MdmDimensionality](MdmDimensionality.md), [MdmModel](MdmModel.md), [MdmNamedBuildProcess](MdmNamedBuildProcess.md), [MdmSchema](MdmSchema.md), [MdmSource](MdmSource.md)

  ------------------------------------------------------------------------



      public abstract class MdmObject
      extends PublicMetadataObject

  An object that describes a particular set of data, such as a measure of product unit prices or a dimension of time values. This class is the basic implementation of the `MetadataObject` interface.
  An `MdmObject` has only the most fundamental properties, so very few specific data characteristics are associated with it. An `MdmObject` has methods that get or set the following characteristics of the object.

  - Name
  - Descriptions
  - Classifications

  In addition to a name, an `MdmObject` can have other decriptive words or phrases associated with it, such as a plural name or a short or long description. An `MdmObject` can also have one or more classifications. Classifications are assigned and handled by an application.

  See Also:
  [`MetadataObject`](../MetadataObject.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                                       |
    |-------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract java.lang.Object`                     | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls a method of the specified `MdmObjectVisitor` and passes that method this `MdmObject` and an `Object`.              |
    | `void`                                          | `addDescription``(`[`MdmDescription`](MdmDescription.md)` desc)`<br>Adds an `MdmDescription` to the descriptions that are associated with this `MdmObject`.                                                                  |
    | `void`                                          | `addObjectClassification``(java.lang.String classification)`<br>Adds a classification to the `MdmObject`.                                                                                                                    |
    | [`MdmDescription`](MdmDescription.md)           | `findOrCreateDescription``(`[`MdmDescriptionType`](MdmDescriptionType.md)` type, java.lang.String language)`<br>Gets the `MdmDescription` of the specified type and language, if it exists.                                  |
    | `java.lang.String`                              | `getDescription``()`<br>Gets a descriptive phrase for this `MdmObject`.                                                                                                                                                      |
    | `java.lang.String`                              | `getDescription``(`[`MdmDescriptionType`](MdmDescriptionType.md)` type)`<br>Gets a description of the specified type for this `MdmObject` in the default language for the current session.                                   |
    | `java.lang.String`                              | `getDescription``(`[`MdmDescriptionType`](MdmDescriptionType.md)` type, java.lang.String language)`<br>Gets a description of the specified type for this `MdmObject` in the specified.language.                              |
    | `java.util.List`                                | `getDescriptions``()`<br>Gets the `MdmDescription` objects that are associated with this `MdmObject`.                                                                                                                        |
    | [`MdmMetadataProvider`](MdmMetadataProvider.md) | `getMetadataProvider``()`<br>Gets the `MdmMetadataProvider` for this `MdmObject`.                                                                                                                                            |
    | `java.util.List`                                | `getObjectClassifications``()`<br>Gets a list of the classifications of the `MdmObject`.                                                                                                                                     |
    | `java.lang.String`                              | `getShortDescription``()`<br>Gets the short description for this `MdmObject`.                                                                                                                                                |
    | `boolean`                                       | `isClassifiedAs``(java.lang.String classification)`<br>Indicates whether or not the `MdmObject` has the specified classification.                                                                                            |
    | `void`                                          | `removeDescription``(`[`MdmDescription`](MdmDescription.md)` desc)`<br>Removes an `MdmDescription` from the descriptions that are associated with this `MdmObject`.                                                          |
    | `void`                                          | `removeObjectClassification``(java.lang.String classification)`<br>Removes a classification from the `MdmObject`.                                                                                                            |
    | `void`                                          | `setDescription``(`[`MdmDescriptionType`](MdmDescriptionType.md)` type, java.lang.String value)`<br>Specifies a description of the specified type for this `MdmObject` in the default language for the current session.      |
    | `void`                                          | `setDescription``(`[`MdmDescriptionType`](MdmDescriptionType.md)` type, java.lang.String language, java.lang.String value)`<br>Specifies a description of the specified type for this `MdmObject` in the specified language. |
    | `void`                                          | `setDescription``(java.lang.String description)`<br>Specifies a descriptive phrase for this `MdmObject`.                                                                                                                     |
    | `void`                                          | `setName``(java.lang.String name)`<br>Specifies a name for this `MdmObject`.                                                                                                                                                 |
    | `void`                                          | `setShortDescription``(java.lang.String description)`<br>Specifies a short description for this `MdmObject`.                                                                                                                 |

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public abstract java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                         java.lang.Object context)

      Calls a method of the specified `MdmObjectVisitor` and passes that method this `MdmObject` and an `Object`.
      Parameters:
      `visitor` - An `MdmObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by a method of the `MdmObjectVisitor`.

    <!-- -->

    - #### getDescription

          public final java.lang.String getDescription()
                                                throws oracle.express.mdm.MetadataNotFoundException

      Gets a descriptive phrase for this `MdmObject`.
      Returns:
      A descriptive phrase for this `MdmObject`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException` - Indicates that the requested metadata object does not exist or is not available to the `MdmMetadataProvider`.

    <!-- -->

    - #### getMetadataProvider

          public MdmMetadataProvider getMetadataProvider()

      Gets the `MdmMetadataProvider` for this `MdmObject`.
      Returns:
      The `MdmMetadataProvider` for this `MdmObject`.

    <!-- -->

    - #### getShortDescription

          public java.lang.String getShortDescription()
                                               throws oracle.express.mdm.MetadataNotFoundException

      Gets the short description for this `MdmObject`. You can use this description for display in a graphical user interface instead of the return value of the `getName` method.
      Returns:
      A `String` containing the short description of this `MdmObject`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException` - Indicates that the requested metadata object does not exist or is not available to the `MdmMetadataProvider`.

    <!-- -->

    - #### setDescription

          public final void setDescription(java.lang.String description)

      Specifies a descriptive phrase for this `MdmObject`.
      Parameters:
      `description` - A `String` that contains a description for this `MdmObject`.

    <!-- -->

    - #### setName

          public void setName(java.lang.String name)

      Specifies a name for this `MdmObject`. If the `MdmObject` already has a name, the new name does not take effect until the root transaction is committed.
      Parameters:
      `name` - A `String` that contains a name for this `MdmObject`.

    <!-- -->

    - #### setShortDescription

          public void setShortDescription(java.lang.String description)
                                   throws oracle.express.mdm.MetadataNotFoundException

      Specifies a short description for this `MdmObject`. You can use this description for display in a graphical user interface instead of the return value of the `getName` method.
      Parameters:
      `description` - A `String` that contains a short description for this `MdmObject`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException` - Indicates that the requested metadata object does not exist or is not available to the `MdmMetadataProvider`.

    <!-- -->

    - #### getObjectClassifications

          public final java.util.List getObjectClassifications()

      Gets a list of the classifications of the `MdmObject`.
      Returns:
      A `List` of the classifications of the `MdmObject`.

    <!-- -->

    - #### addObjectClassification

          public final void addObjectClassification(java.lang.String classification)

      Adds a classification to the `MdmObject`.
      Parameters:
      `classification` - A `String` that contains the classification to add to the `MdmObject`.

    <!-- -->

    - #### removeObjectClassification

          public final void removeObjectClassification(java.lang.String classification)

      Removes a classification from the `MdmObject`.
      Parameters:
      `classification` - A `String` that contains the classification to remove from the `MdmObject`.

    <!-- -->

    - #### isClassifiedAs

          public final boolean isClassifiedAs(java.lang.String classification)

      Indicates whether or not the `MdmObject` has the specified classification.
      Parameters:
      `classification` - A `String` that contains the classification to compare to that of this `MdmObject`.

      Returns:
      A `boolean` that is `true` if the `MdmObject` has the specified classification or `false` if it does not.

    <!-- -->

    - #### getDescription

          public final java.lang.String getDescription(MdmDescriptionType type)

      Gets a description of the specified type for this `MdmObject` in the default language for the current session.
      Parameters:
      `type` - An `MdmDescriptionType` that specifies the type of description, such as name or long description.

      Returns:
      A `String` that contains the descriptive value of the `MdmDescription` associated with the specified `MdmDescriptionType`.

    <!-- -->

    - #### getDescription

          public final java.lang.String getDescription(MdmDescriptionType type,
                                                       java.lang.String language)

      Gets a description of the specified type for this `MdmObject` in the specified.language.
      Parameters:
      `type` - An `MdmDescriptionType` that specifies the type of description, such as short name or plural description.

      `language` - A `String` that specifies the language for the description.

      Returns:
      A `String` that contains the descriptive value of the `MdmDescription` associated with the specified `MdmDescriptionType`.

    <!-- -->

    - #### setDescription

          public final void setDescription(MdmDescriptionType type,
                                           java.lang.String value)

      Specifies a description of the specified type for this `MdmObject` in the default language for the current session.
      Parameters:
      `type` - An `MdmDescriptionType` that specifies the type of description, such as name or long description.

      `value` - A `String` that contains the description for this `MdmObject`.

    <!-- -->

    - #### setDescription

          public final void setDescription(MdmDescriptionType type,
                                           java.lang.String language,
                                           java.lang.String value)

      Specifies a description of the specified type for this `MdmObject` in the specified language.
      Parameters:
      `type` - An `MdmDescriptionType` that specifies the type of description, such as name or long description.

      `language` - A `String` that specifies the language for the description.

      `value` - A `String` that contains the description for this `MdmObject`.

    <!-- -->

    - #### findOrCreateDescription

          public MdmDescription findOrCreateDescription(MdmDescriptionType type,
                                                        java.lang.String language)

      Gets the `MdmDescription` of the specified type and language, if it exists. Otherwise, creates an `MdmDescription` of the specified type and language.
      Parameters:
      `type` - An `MdmDescriptionType` that specifies the type of description, such as name or long description.

      `language` - A `String` that specifies the language for the description.

      Returns:
      An `MdmDescription` of specified type and language with the specified value.

    <!-- -->

    - #### getDescriptions

          public final java.util.List getDescriptions()

      Gets the `MdmDescription` objects that are associated with this `MdmObject`.
      Returns:
      A `List` of the `MdmDescription` objects associated with this `MdmObject`.

    <!-- -->

    - #### addDescription

          public final void addDescription(MdmDescription desc)

      Adds an `MdmDescription` to the descriptions that are associated with this `MdmObject`.
      Parameters:
      `desc` - The `MdmDescription` to add to this `MdmObject`.

    <!-- -->

    - #### removeDescription

          public final void removeDescription(MdmDescription desc)

      Removes an `MdmDescription` from the descriptions that are associated with this `MdmObject`.
      Parameters:
      `desc` - The `MdmDescription` to remove from this `MdmObject`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmNamedBuildProcess.md)
- [Next Class](MdmObjectVisitor.md)

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
