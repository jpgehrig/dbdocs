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

- Prev Class
- [Next Class](AWAttributeOrganization.md)

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

oracle.olapi.metadata.deployment

## Class AW

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - oracle.olapi.metadata.deployment.AW

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class AW
      extends BaseMetadataObject

  A metadata object that represents an Oracle OLAP analytic workspace. An `AW` is owned by an `MdmDatabaseSchema`. An application creates or gets an `AW` by calling the [`findOrCreateAW`](../mdm/MdmDatabaseSchema.md) method of an `MdmDatabaseSchema`. An `AW` is a top-level object that has associated `MdmCube` and `MdmPrimaryDimension` objects. It also has a tablespace.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                  | Method and Description                                                                                                                                                                   |
    |----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.List`                                   | `getCubes``()`<br>Gets the `MdmCube` objects that are associated with this `AW`.                                                                                                         |
    | `java.util.List`                                   | `getDimensions``()`<br>Gets the `MdmPrimaryDimension` objects that are associated with this `AW`.                                                                                        |
    | `java.lang.String`                                 | `getName``()`<br>Gets the name of this `AW`.                                                                                                                                             |
    | [`MdmDatabaseSchema`](../mdm/MdmDatabaseSchema.md) | `getOwner``()`<br>Gets the `MdmDatabaseSchema` that owns this `AW`.                                                                                                                      |
    | `java.util.List`                                   | `getPersistentLanguages``()`<br>Gets a list that has the names of the languages in which this `AW` has descriptions of the `MdmCube` and `MdmPrimaryDimension` objects that it contains. |
    | `java.lang.String`                                 | `getTablespace``()`<br>Gets the name of the tablespace that contains this `AW`.                                                                                                          |
    | `java.lang.String`                                 | `getVersion``()`<br>Gets the version of this `AW`.                                                                                                                                       |
    | `void`                                             | `setOwner``(`[`MdmDatabaseSchema`](../mdm/MdmDatabaseSchema.md)` owner)`<br>Specifies an owner for this `AW`.                                                                            |
    | `void`                                             | `setTablespace``(java.lang.String name)`<br>Specifies a tablespace to contain this `AW`.                                                                                                 |

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getName

          public final java.lang.String getName()

      Gets the name of this `AW`.
      Overrides:
      [`getName`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      A `String` that contains the name of the analytic workspace object.

    <!-- -->

    - #### getOwner

          public final MdmDatabaseSchema getOwner()

      Gets the `MdmDatabaseSchema` that owns this `AW`.
      Overrides:
      [`getOwner`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      The `MdmDatabaseSchema` that owns this `AW`.

    <!-- -->

    - #### setOwner

          public final void setOwner(MdmDatabaseSchema owner)

      Specifies an owner for this `AW`. Use this method to transfer ownership of an analytic workspace from one `MdmDatabaseSchema` to another.
      Parameters:
      `owner` - The `MdmDatabaseSchema` to be the owner of this `AW`.

    <!-- -->

    - #### getTablespace

          public final java.lang.String getTablespace()

      Gets the name of the tablespace that contains this `AW`.
      Returns:
      A `String` that contains the name of the tablespace that contains this `AW`.

    <!-- -->

    - #### setTablespace

          public final void setTablespace(java.lang.String name)

      Specifies a tablespace to contain this `AW`.
      Parameters:
      `name` - A `String` that contains the name of the tablespace for the `AW`.

    <!-- -->

    - #### getDimensions

          public final java.util.List getDimensions()

      Gets the `MdmPrimaryDimension` objects that are associated with this `AW`.
      Returns:
      A `List` of the `MdmPrimaryDimension` objects of this `AW`.

    <!-- -->

    - #### getCubes

          public final java.util.List getCubes()

      Gets the `MdmCube` objects that are associated with this `AW`.
      Returns:
      A `List` of the `MdmCube` objects of this `AW`.

    <!-- -->

    - #### getPersistentLanguages

          public java.util.List getPersistentLanguages()

      Gets a list that has the names of the languages in which this `AW` has descriptions of the `MdmCube` and `MdmPrimaryDimension` objects that it contains. For the `MdmPrimaryDimension` objects, the list also includes the languages for the `AttributeMap` objects that are contained by a `DimensionMap` that is owned directly or indirectly by an `MdmPrimaryDimension`.
      Returns:
      A `List` that contains the NLS names of languages.

    <!-- -->

    - #### getVersion

          public final java.lang.String getVersion()

      Gets the version of this `AW`.
      Returns:
      A `String` that contains the version of the analytic workspace object.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- Prev Class
- [Next Class](AWAttributeOrganization.md)

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
