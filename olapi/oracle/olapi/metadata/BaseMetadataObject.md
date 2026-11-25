Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- Prev Class
- [Next Class](BaseMetadataProvider.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.olapi.metadata

## Class BaseMetadataObject

- java.lang.Object

- - oracle.olapi.metadata.BaseMetadataObject

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [AW](deployment/AW.md), [MdmDescription](mdm/MdmDescription.md), [PublicMetadataObject](PublicMetadataObject.md)

  ------------------------------------------------------------------------



      public abstract class BaseMetadataObject
      extends java.lang.Object
      implements MetadataObject

  The abstract base class for Oracle OLAP metadata objects. A `BaseMetadataObject` has a unique identifier (ID). It can also have a name and an owner. Some `BaseMetadataObject` objects are contained by another `BaseMetadataObject`. For example, an `MdmLevelHierarchy` is contained by an `MdmPrimaryDimension`.
  The owner of most metadata objects is an `MdmDatabaseSchema`. Exceptions are the `MdmRootSchema` and `MdmMeasureDimension`, which are owned by the `MdmRootSchema`.

  The unique identifier has the form *objectName*, *ownerName.objectName*, or *ownerName.containerName.objectName*. For example, the `MdmDatabaseSchema` for the user GLOBAL has the unique identifier `GLOBAL`. For an `MdmPrimaryDimension` named `PRODUCT_AWJ` that was created by the `GLOBAL` database schema, the ID is `GLOBAL.PRODUCT_AWJ`. For an `MdmLevelHierarchy` named `PRODUCT_PRIMARY` that was created by the `PRODUCT_AWJ` dimension, the ID is `GLOBAL.PRODUCT_AWJ.PRODUCT_PRIMARY`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                                                              |
    |---------------------------------|---------------------------------------------------------------------------------------------------------------------|
    | `BaseMetadataObject`            | `getContainedByObject``()`<br>Gets the `BaseMetadataObject` that is the container of this `BaseMetadataObject`.     |
    | `java.lang.String`              | `getID``()`<br>Gets the unique identifier for the `BaseMetadataObject`.                                             |
    | `java.lang.String`              | `getName``()`<br>Gets the name of the `BaseMetadataObject`.                                                         |
    | `java.lang.String`              | `getNewName``()`<br>Gets the new name specified for the `BaseMetadataObject` by the `setName` method of the object. |
    | [`MdmSchema`](mdm/MdmSchema.md) | `getOwner``()`<br>Gets the `MdmSchema` that owns the `BaseMetadataObject`.                                          |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getID

          public java.lang.String getID()

      Gets the unique identifier for the `BaseMetadataObject`.
      Specified by:
      [`getID`](MetadataObject.md) in interface [`MetadataObject`](MetadataObject.md)

      Returns:
      A `String` that uniquely identifies the `BaseMetadataObject`.

    <!-- -->

    - #### getName

          public java.lang.String getName()
                                   throws oracle.express.mdm.MetadataNotFoundException

      Gets the name of the `BaseMetadataObject`.
      Returns:
      A `String` that contains the name of the `BaseMetadataObject`, or an empty string if the `BaseMetadataObject` has no name.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException` - Indicates that the requested metadata object does not exist or is not available to the `MdmMetadataProvider`.

    <!-- -->

    - #### getNewName

          public final java.lang.String getNewName()

      Gets the new name specified for the `BaseMetadataObject` by the `setName` method of the object. The new name does not take effect until after you have committed the root transaction that contains the name change.
      If you have changed the name of the object with the `setName` method of the object, but you have not committed the root transaction that contains the name change, then this method returns the name that this `MdmObject` will have after you have committed the root transaction. If you have not changed the name of this object since you last committed the root transaction, this method returns `null`.

      Returns:
      The name that this object will have after you commit the current root transaction, or `null` if you have not specified a new name by calling the `setName` method.

    <!-- -->

    - #### getContainedByObject

          public final BaseMetadataObject getContainedByObject()

      Gets the `BaseMetadataObject` that is the container of this `BaseMetadataObject`. A top-level object does not have a container object. Top-level objects contain objects that they create. Those contained objects contain objects that they create. For example, an `MdmStandardDimension` is a top-level object. It can create an `MdmLevelHierarchy`. The `MdmLevelHierarchy` can create an `MdmHierarchyLevel`. The `MdmHierarchyLevel` is contained by the `MdmLevelHierarchy`, which is contained by the `MdmStandardDimension`.
      For information on top-level objects, see [`MdmDatabaseSchema`](mdm/MdmDatabaseSchema.md).

      Returns:
      The `BaseMetadataObject` that contains this metadata object.

    <!-- -->

    - #### getOwner

          public MdmSchema getOwner()

      Gets the `MdmSchema` that owns the `BaseMetadataObject`.
      Returns:
      The `MdmSchema` that owns the `BaseMetadataObject`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- Prev Class
- [Next Class](BaseMetadataProvider.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
