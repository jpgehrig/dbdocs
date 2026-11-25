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

- [Prev Class](NFEBasicPredefinedConnectedPoint.md)
- [Next Class](NFECatalogValue.md)

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

## Interface NFECatalog

- All Known Implementing Classes:
  [NFEBasicCatalog](NFEBasicCatalog.md)

  ------------------------------------------------------------------------



      public interface NFECatalog

  A set of predefined values that can be assigned to a feature layer's attribute

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                 | Method and Description                                                                                             |
    |-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                         | `addCatalogValue``(`[`NFECatalogValue`](NFECatalogValue.md)` catalogValue)`<br>Adds a value to the catalog         |
    | `NFECatalog`                                                      | `createCopy``()`<br>Returns object copy.                                                                           |
    | [`NFEAttributeType`](NFEAttributeType.md)                         | `getAttributeType``()`<br>Gets the catalog's type.                                                                 |
    | `java.lang.Object[]`                                              | `getCatalogSimpleValues``()`<br>Gets the actual values (that is, not holders) defined in the catalog               |
    | `java.util.Collection<`[`NFECatalogValue`](NFECatalogValue.md)`>` | `getCatalogValues``()`<br>Gets all the values defined in the catalog                                               |
    | `long`                                                            | `getId``()`<br>Gets the catalog ID                                                                                 |
    | `java.lang.String`                                                | `getName``()`<br>Gets the catalog's name                                                                           |
    | `boolean`                                                         | `removeCatalogValue``(`[`NFECatalogValue`](NFECatalogValue.md)` catalogValue)`<br>Removes a value from the catalog |
    | `void`                                                            | `setAttributeType``(`[`NFEAttributeType`](NFEAttributeType.md)` attributeType)`<br>Sets the catalog's type.        |
    | `void`                                                            | `setId``(long id)`<br>Sets the catalog ID                                                                          |
    | `void`                                                            | `setName``(java.lang.String name)`<br>Sets the catalog's name                                                      |

<!-- -->

- - ### Method Detail

    - #### getId

          long getId()

      Gets the catalog ID
      Returns:
      the catalog ID

    <!-- -->

    - #### setId

          void setId(long id)

      Sets the catalog ID
      Parameters:
      `id` - the catalog ID

    <!-- -->

    - #### getName

          java.lang.String getName()

      Gets the catalog's name
      Returns:
      the catalog's name

    <!-- -->

    - #### setName

          void setName(java.lang.String name)

      Sets the catalog's name
      Parameters:
      `name` - the catalog's name

    <!-- -->

    - #### getAttributeType

          NFEAttributeType getAttributeType()

      Gets the catalog's type. This is the type of the values stored at the catalog
      Returns:
      an attribute type value

    <!-- -->

    - #### setAttributeType

          void setAttributeType(NFEAttributeType attributeType)

      Sets the catalog's type. This is the type of the values stored at the catalog
      Parameters:
      `attributeType` - an attribute type value

    <!-- -->

    - #### getCatalogValues

          java.util.Collection<NFECatalogValue> getCatalogValues()

      Gets all the values defined in the catalog
      Returns:
      a collection containing all values of the catalog

    <!-- -->

    - #### addCatalogValue

          boolean addCatalogValue(NFECatalogValue catalogValue)

      Adds a value to the catalog
      Parameters:

      `catalogValue` - a catalog value holder. The value type must match the catalog type

      Returns:

    <!-- -->

    - #### removeCatalogValue

          boolean removeCatalogValue(NFECatalogValue catalogValue)

      Removes a value from the catalog
      Parameters:
      `catalogValue` - a catalog value holder

      Returns:
      true if the value was removed

    <!-- -->

    - #### getCatalogSimpleValues

          java.lang.Object[] getCatalogSimpleValues()

      Gets the actual values (that is, not holders) defined in the catalog
      Returns:
      an array of values as objects

    <!-- -->

    - #### createCopy

          NFECatalog createCopy()

      Returns object copy.
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

- [Prev Class](NFEBasicPredefinedConnectedPoint.md)
- [Next Class](NFECatalogValue.md)

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
