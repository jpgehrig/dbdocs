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

- [Prev Class](NFECatalog.md)
- [Next Class](NFEFeature.md)

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

## Class NFECatalogValue

- java.lang.Object

- - oracle.spatial.network.nfe.model.feature.NFECatalogValue

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFECatalogValue
      extends java.lang.Object

  It is a tuple of an ID and a value

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFECatalogValue``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                        |
    |--------------------|---------------------------------------------------------------|
    | `NFECatalogValue`  | `createCopy``()`<br>Returns object copy.                      |
    | `long`             | `getId``()`<br>Gets the value ID                              |
    | `java.lang.Object` | `getValue``()`<br>Gets the actual value                       |
    | `void`             | `setId``(long id)`<br>Sets the value ID                       |
    | `void`             | `setValue``(java.lang.Object value)`<br>Sets the actual value |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFECatalogValue

          public NFECatalogValue()

  <!-- -->

  - ### Method Detail

    - #### getId

          public long getId()

      Gets the value ID
      Returns:
      the value ID

    <!-- -->

    - #### setId

          public void setId(long id)

      Sets the value ID
      Parameters:
      `id` - the value ID

    <!-- -->

    - #### getValue

          public java.lang.Object getValue()

      Gets the actual value
      Returns:
      an Object subclass instance

    <!-- -->

    - #### setValue

          public void setValue(java.lang.Object value)

      Sets the actual value
      Parameters:
      `value` - an Object subclass instance

    <!-- -->

    - #### createCopy

          public NFECatalogValue createCopy()

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

- [Prev Class](NFECatalog.md)
- [Next Class](NFEFeature.md)

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
