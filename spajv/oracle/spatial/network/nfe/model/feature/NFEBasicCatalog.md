Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEBasicAttributeDescriptor.md)
- [Next Class](NFEBasicFeature.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.feature

## Class NFEBasicCatalog

- java.lang.Object

- - oracle.spatial.network.nfe.model.feature.NFEBasicCatalog

<!-- -->

- All Implemented Interfaces:
  [NFECatalog](NFECatalog.md)

  ------------------------------------------------------------------------



      public class NFEBasicCatalog
      extends java.lang.Object
      implements NFECatalog

  The default implementation of [`NFECatalog`](NFECatalog.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEBasicCatalog``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                 | Method and Description                                                                                             |
    |-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                         | `addCatalogValue``(`[`NFECatalogValue`](NFECatalogValue.md)` catalogValue)`<br>Adds a value to the catalog         |
    | [`NFECatalog`](NFECatalog.md)                                     | `createCopy``()`<br>Returns object copy.                                                                           |
    | [`NFEAttributeType`](NFEAttributeType.md)                         | `getAttributeType``()`<br>Gets the catalog's type.                                                                 |
    | `java.lang.Object[]`                                              | `getCatalogSimpleValues``()`<br>Gets the actual values (that is, not holders) defined in the catalog               |
    | `java.util.Collection<`[`NFECatalogValue`](NFECatalogValue.md)`>` | `getCatalogValues``()`<br>Gets all the values defined in the catalog                                               |
    | `long`                                                            | `getId``()`<br>Gets the catalog ID                                                                                 |
    | `java.lang.String`                                                | `getName``()`<br>Gets the catalog's name                                                                           |
    | `boolean`                                                         | `removeCatalogValue``(`[`NFECatalogValue`](NFECatalogValue.md)` catalogValue)`<br>Removes a value from the catalog |
    | `void`                                                            | `setAttributeType``(`[`NFEAttributeType`](NFEAttributeType.md)` attributeType)`<br>Sets the catalog's type.        |
    | `void`                                                            | `setId``(long id)`<br>Sets the catalog ID                                                                          |
    | `void`                                                            | `setName``(java.lang.String name)`<br>Sets the catalog's name                                                      |
    | `java.lang.String`                                                | `toString``()`                                                                                                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicCatalog

          public NFEBasicCatalog()

  <!-- -->

  - ### Method Detail

    - #### getId

          public long getId()

      Description copied from interface: [`NFECatalog`](NFECatalog.md)
      Gets the catalog ID
      Specified by:
      [`getId`](NFECatalog.md) in interface [`NFECatalog`](NFECatalog.md)

      Returns:
      the catalog ID

    <!-- -->

    - #### setId

          public void setId(long id)

      Description copied from interface: [`NFECatalog`](NFECatalog.md)
      Sets the catalog ID
      Specified by:
      [`setId`](NFECatalog.md) in interface [`NFECatalog`](NFECatalog.md)

      Parameters:
      `id` - the catalog ID

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Description copied from interface: [`NFECatalog`](NFECatalog.md)
      Gets the catalog's name
      Specified by:
      [`getName`](NFECatalog.md) in interface [`NFECatalog`](NFECatalog.md)

      Returns:
      the catalog's name

    <!-- -->

    - #### setName

          public void setName(java.lang.String name)

      Description copied from interface: [`NFECatalog`](NFECatalog.md)
      Sets the catalog's name
      Specified by:
      [`setName`](NFECatalog.md) in interface [`NFECatalog`](NFECatalog.md)

      Parameters:
      `name` - the catalog's name

    <!-- -->

    - #### getAttributeType

          public NFEAttributeType getAttributeType()

      Description copied from interface: [`NFECatalog`](NFECatalog.md)
      Gets the catalog's type. This is the type of the values stored at the catalog
      Specified by:
      [`getAttributeType`](NFECatalog.md) in interface [`NFECatalog`](NFECatalog.md)

      Returns:
      an attribute type value

    <!-- -->

    - #### setAttributeType

          public void setAttributeType(NFEAttributeType attributeType)

      Description copied from interface: [`NFECatalog`](NFECatalog.md)
      Sets the catalog's type. This is the type of the values stored at the catalog
      Specified by:
      [`setAttributeType`](NFECatalog.md) in interface [`NFECatalog`](NFECatalog.md)

      Parameters:
      `attributeType` - an attribute type value

    <!-- -->

    - #### getCatalogValues

          public java.util.Collection<NFECatalogValue> getCatalogValues()

      Description copied from interface: [`NFECatalog`](NFECatalog.md)
      Gets all the values defined in the catalog
      Specified by:
      [`getCatalogValues`](NFECatalog.md) in interface [`NFECatalog`](NFECatalog.md)

      Returns:
      a collection containing all values of the catalog

    <!-- -->

    - #### addCatalogValue

          public boolean addCatalogValue(NFECatalogValue catalogValue)

      Description copied from interface: [`NFECatalog`](NFECatalog.md)
      Adds a value to the catalog
      Specified by:

      [`addCatalogValue`](NFECatalog.md) in interface [`NFECatalog`](NFECatalog.md)

      Parameters:

      `catalogValue` - a catalog value holder. The value type must match the catalog type

      Returns:

    <!-- -->

    - #### removeCatalogValue

          public boolean removeCatalogValue(NFECatalogValue catalogValue)

      Description copied from interface: [`NFECatalog`](NFECatalog.md)
      Removes a value from the catalog
      Specified by:
      [`removeCatalogValue`](NFECatalog.md) in interface [`NFECatalog`](NFECatalog.md)

      Parameters:
      `catalogValue` - a catalog value holder

      Returns:
      true if the value was removed

    <!-- -->

    - #### getCatalogSimpleValues

          public java.lang.Object[] getCatalogSimpleValues()

      Description copied from interface: [`NFECatalog`](NFECatalog.md)
      Gets the actual values (that is, not holders) defined in the catalog
      Specified by:
      [`getCatalogSimpleValues`](NFECatalog.md) in interface [`NFECatalog`](NFECatalog.md)

      Returns:
      an array of values as objects

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### createCopy

          public NFECatalog createCopy()

      Description copied from interface: [`NFECatalog`](NFECatalog.md)
      Returns object copy.
      Specified by:
      [`createCopy`](NFECatalog.md) in interface [`NFECatalog`](NFECatalog.md)

      Returns:
      object copy

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEBasicAttributeDescriptor.md)
- [Next Class](NFEBasicFeature.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
