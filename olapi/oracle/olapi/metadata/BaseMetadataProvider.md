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

- [Prev Class](BaseMetadataObject.md)
- [Next Class](DuplicateMetadataIDException.md)

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

## Class BaseMetadataProvider

- java.lang.Object

- - oracle.olapi.metadata.BaseMetadataProvider

<!-- -->

- Direct Known Subclasses:
  [MdmMetadataProvider](mdm/MdmMetadataProvider.md)

  ------------------------------------------------------------------------



      public abstract class BaseMetadataProvider
      extends java.lang.Object

  The base class for an object that gives access to the metadata for a data store. An application creates Oracle OLAP multidimensional model (MDM) metadata with classes in the `oracle.olapi.metadata.mdm` package. The `MdmMetadataProvider` subclass of `BaseMetadataProvider` provides access to Oracle OLAP metadata.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                                                                                   |
    |--------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                           | `flushDeletedObjects``()`<br>Frees the resources in an OLAP Java API client application for any objects that Oracle OLAP has deleted from cached metadata on the client. |
    | `void`                                           | `flushMetadataObjectCache``()`<br>Removes the cached metadata in an OLAP Java API client application for any objects that Oracle OLAP has previously fetched.            |
    | [`DataProvider`](../data/source/DataProvider.md) | `getDataProvider``()`<br>Gets the `DataProvider` that is associated with this `BaseMetadataProvider`.                                                                    |
    | `java.lang.String`                               | `getID``()`<br>Gets the unique object identifier for the `BaseMetadataProvider`.                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### flushDeletedObjects

          public final void flushDeletedObjects()

      Frees the resources in an OLAP Java API client application for any objects that Oracle OLAP has deleted from cached metadata on the client. Oracle OLAP does not free the resources for deleted objects until the applications calls `flushDeletedObjects` or the application exits. Most applications do not need to use this method.

    <!-- -->

    - #### flushMetadataObjectCache

          public final void flushMetadataObjectCache()

      Removes the cached metadata in an OLAP Java API client application for any objects that Oracle OLAP has previously fetched. This allows the OLAP Java API client to pick up any metadata changes made through a different connection on the server.

    <!-- -->

    - #### getDataProvider

          public DataProvider getDataProvider()

      Gets the `DataProvider` that is associated with this `BaseMetadataProvider`. This is the `DataProvider` that was specified when this `BaseMetadataProvider` was created.
      Returns:
      The `DataProvider` that is associated with this `BaseMetadataProvider`.

    <!-- -->

    - #### getID

          public java.lang.String getID()

      Gets the unique object identifier for the `BaseMetadataProvider`. Object identifiers have the form *objectName* or *ownerName.objectName*. For example, the unique identifier for the `MdmDatabaseSchema` for the user GLOBAL is `GLOBAL`. For an `MdmPrimaryDimension` named `PRODUCTS_AWJ`, the ID is `GLOBAL.PRODUCTS_AWJ`. For an `MdmLevelHierarchy` named `PRIMARY`, the ID is `GLOBAL.PRODUCTS_AWJ.PRIMARY`.
      Returns:
      The unique identifier for this `BaseMetadataProvider`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](BaseMetadataObject.md)
- [Next Class](DuplicateMetadataIDException.md)

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
