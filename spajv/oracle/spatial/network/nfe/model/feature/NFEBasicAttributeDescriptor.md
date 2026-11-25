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

- [Prev Class](NFEBasicAttributeConstraint.md)
- [Next Class](NFEBasicCatalog.md)

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

## Class NFEBasicAttributeDescriptor

- java.lang.Object

- - oracle.spatial.network.nfe.model.feature.NFEBasicAttributeDescriptor

<!-- -->

- All Implemented Interfaces:
  [NFEAttributeDescriptor](NFEAttributeDescriptor.md)

  ------------------------------------------------------------------------



      public class NFEBasicAttributeDescriptor
      extends java.lang.Object
      implements NFEAttributeDescriptor

  The default implementation of [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description        |
    |------------------------------------|
    | `NFEBasicAttributeDescriptor``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                     | Method and Description                                                                                   |
    |-------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
    | [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md) | `createCopy``()`<br>Returns object copy.                                                                 |
    | [`NFECatalog`](NFECatalog.md)                         | `getCatalog``()`<br>Gets the catalog associated to this attribute (if any)                               |
    | `int`                                                 | `getCategory``()`<br>Gets the attribute category value                                                   |
    | `int`                                                 | `getLength``()`<br>Gets the maximum length the attribute can be if it is a VARCHAR type                  |
    | `java.lang.String`                                    | `getName``()`<br>Gets the attribute name                                                                 |
    | [`NFEAttributeType`](NFEAttributeType.md)             | `getType``()`<br>Gets the attribute type identifier                                                      |
    | `java.lang.Class<?>`                                  | `getTypeClass``()`<br>Gets the attribute type as a Java Class                                            |
    | `void`                                                | `setCatalog``(`[`NFECatalog`](NFECatalog.md)` catalog)`<br>Sets the catalog associated to this attribute |
    | `void`                                                | `setCategory``(int category)`<br>Sets the attribute category value                                       |
    | `void`                                                | `setLength``(int length)`<br>Sets the maximum length the attribute can be if it is a VARCHAR type        |
    | `void`                                                | `setName``(java.lang.String name)`<br>Sets the attribute name                                            |
    | `void`                                                | `setType``(`[`NFEAttributeType`](NFEAttributeType.md)` type)`<br>Sets the attribute type identifier      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicAttributeDescriptor

          public NFEBasicAttributeDescriptor()

  <!-- -->

  - ### Method Detail

    - #### getName

          public java.lang.String getName()

      Description copied from interface: [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)
      Gets the attribute name
      Specified by:
      [`getName`](NFEAttributeDescriptor.md) in interface [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

      Returns:
      an attribute name

    <!-- -->

    - #### setName

          public void setName(java.lang.String name)

      Description copied from interface: [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)
      Sets the attribute name
      Specified by:
      [`setName`](NFEAttributeDescriptor.md) in interface [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

      Parameters:
      `name` - an attribute name

    <!-- -->

    - #### getTypeClass

          public java.lang.Class<?> getTypeClass()

      Description copied from interface: [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)
      Gets the attribute type as a Java Class
      Specified by:
      [`getTypeClass`](NFEAttributeDescriptor.md) in interface [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

      Returns:
      the Java type representing the attribute type

    <!-- -->

    - #### getType

          public NFEAttributeType getType()

      Description copied from interface: [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)
      Gets the attribute type identifier
      Specified by:
      [`getType`](NFEAttributeDescriptor.md) in interface [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

      Returns:
      an attribute type value

    <!-- -->

    - #### setType

          public void setType(NFEAttributeType type)

      Description copied from interface: [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)
      Sets the attribute type identifier
      Specified by:
      [`setType`](NFEAttributeDescriptor.md) in interface [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

      Parameters:
      `type` - an attribute type value

    <!-- -->

    - #### getLength

          public int getLength()

      Description copied from interface: [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)
      Gets the maximum length the attribute can be if it is a VARCHAR type
      Specified by:
      [`getLength`](NFEAttributeDescriptor.md) in interface [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

      Returns:
      a string attribute maximum length

    <!-- -->

    - #### setLength

          public void setLength(int length)

      Description copied from interface: [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)
      Sets the maximum length the attribute can be if it is a VARCHAR type
      Specified by:
      [`setLength`](NFEAttributeDescriptor.md) in interface [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

      Parameters:
      `length` - a string attribute maximum length

    <!-- -->

    - #### getCategory

          public int getCategory()

      Description copied from interface: [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)
      Gets the attribute category value
      Specified by:
      [`getCategory`](NFEAttributeDescriptor.md) in interface [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

      Returns:
      an attribute category value

    <!-- -->

    - #### setCategory

          public void setCategory(int category)

      Description copied from interface: [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)
      Sets the attribute category value
      Specified by:
      [`setCategory`](NFEAttributeDescriptor.md) in interface [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

      Parameters:
      `category` - an attribute category value

    <!-- -->

    - #### getCatalog

          public NFECatalog getCatalog()

      Description copied from interface: [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)
      Gets the catalog associated to this attribute (if any)
      Specified by:
      [`getCatalog`](NFEAttributeDescriptor.md) in interface [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

      Returns:
      An NFECatalog instance or null if the attribute is not associated to a catalog

    <!-- -->

    - #### setCatalog

          public void setCatalog(NFECatalog catalog)

      Description copied from interface: [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)
      Sets the catalog associated to this attribute
      Specified by:
      [`setCatalog`](NFEAttributeDescriptor.md) in interface [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

      Parameters:
      `catalog` - a catalog instance

    <!-- -->

    - #### createCopy

          public NFEAttributeDescriptor createCopy()

      Description copied from interface: [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)
      Returns object copy.
      Specified by:
      [`createCopy`](NFEAttributeDescriptor.md) in interface [`NFEAttributeDescriptor`](NFEAttributeDescriptor.md)

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

- [Prev Class](NFEBasicAttributeConstraint.md)
- [Next Class](NFEBasicCatalog.md)

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
