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

- [Prev Class](NFEAttributeConstraint.md)
- [Next Class](NFEAttributeType.md)

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

## Interface NFEAttributeDescriptor

- All Known Implementing Classes:
  [NFEBasicAttributeDescriptor](NFEBasicAttributeDescriptor.md)

  ------------------------------------------------------------------------



      public interface NFEAttributeDescriptor

  Used to describe an attribute definition of a Feature Layer. Basically, it contains attribute metadata.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                         | Method and Description                                                                                   |
    |-------------------------------------------|----------------------------------------------------------------------------------------------------------|
    | `NFEAttributeDescriptor`                  | `createCopy``()`<br>Returns object copy.                                                                 |
    | [`NFECatalog`](NFECatalog.md)             | `getCatalog``()`<br>Gets the catalog associated to this attribute (if any)                               |
    | `int`                                     | `getCategory``()`<br>Gets the attribute category value                                                   |
    | `int`                                     | `getLength``()`<br>Gets the maximum length the attribute can be if it is a VARCHAR type                  |
    | `java.lang.String`                        | `getName``()`<br>Gets the attribute name                                                                 |
    | [`NFEAttributeType`](NFEAttributeType.md) | `getType``()`<br>Gets the attribute type identifier                                                      |
    | `java.lang.Class<?>`                      | `getTypeClass``()`<br>Gets the attribute type as a Java Class                                            |
    | `void`                                    | `setCatalog``(`[`NFECatalog`](NFECatalog.md)` catalog)`<br>Sets the catalog associated to this attribute |
    | `void`                                    | `setCategory``(int category)`<br>Sets the attribute category value                                       |
    | `void`                                    | `setLength``(int length)`<br>Sets the maximum length the attribute can be if it is a VARCHAR type        |
    | `void`                                    | `setName``(java.lang.String attrName)`<br>Sets the attribute name                                        |
    | `void`                                    | `setType``(`[`NFEAttributeType`](NFEAttributeType.md)` type)`<br>Sets the attribute type identifier      |

<!-- -->

- - ### Method Detail

    - #### getName

          java.lang.String getName()

      Gets the attribute name
      Returns:
      an attribute name

    <!-- -->

    - #### setName

          void setName(java.lang.String attrName)

      Sets the attribute name
      Parameters:
      `attrName` - an attribute name

    <!-- -->

    - #### getTypeClass

          java.lang.Class<?> getTypeClass()

      Gets the attribute type as a Java Class
      Returns:
      the Java type representing the attribute type

    <!-- -->

    - #### getType

          NFEAttributeType getType()

      Gets the attribute type identifier
      Returns:
      an attribute type value

    <!-- -->

    - #### setType

          void setType(NFEAttributeType type)

      Sets the attribute type identifier
      Parameters:
      `type` - an attribute type value

    <!-- -->

    - #### getLength

          int getLength()

      Gets the maximum length the attribute can be if it is a VARCHAR type
      Returns:
      a string attribute maximum length

    <!-- -->

    - #### setLength

          void setLength(int length)

      Sets the maximum length the attribute can be if it is a VARCHAR type
      Parameters:
      `length` - a string attribute maximum length

    <!-- -->

    - #### getCategory

          int getCategory()

      Gets the attribute category value
      Returns:
      an attribute category value

    <!-- -->

    - #### setCategory

          void setCategory(int category)

      Sets the attribute category value
      Parameters:
      `category` - an attribute category value

    <!-- -->

    - #### getCatalog

          NFECatalog getCatalog()

      Gets the catalog associated to this attribute (if any)
      Returns:
      An NFECatalog instance or null if the attribute is not associated to a catalog

    <!-- -->

    - #### setCatalog

          void setCatalog(NFECatalog catalog)

      Sets the catalog associated to this attribute
      Parameters:
      `catalog` - a catalog instance

    <!-- -->

    - #### createCopy

          NFEAttributeDescriptor createCopy()

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

- [Prev Class](NFEAttributeConstraint.md)
- [Next Class](NFEAttributeType.md)

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
