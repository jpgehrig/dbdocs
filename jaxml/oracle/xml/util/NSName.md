Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **[Next Class](Queue.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**oracle.xml.util**

## **Interface NSName**

- **All Known Subinterfaces:**
  **[NSName](../parser/v2/NSName.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[XMLAttr](../parser/v2/XMLAttr.md), [XMLDocument](../parser/v2/XMLDocument.md), [XMLDocumentFragment](../parser/v2/XMLDocumentFragment.md), [XMLElement](../parser/v2/XMLElement.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface NSName

  **This interface provides Namespace support for Element and Attr names**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                               |
    |--------------------|--------------------------------------------------------------------------------------|
    | `java.lang.String` | `getExpandedName``()`<br>Get the fully resolved name for this name, i.e., uri:ncname |
    | `java.lang.String` | `getLocalName``()`<br>Get the local name for this name                               |
    | `java.lang.String` | `getNamespace``()`<br>Get the resolved Namespace for this name                       |
    | `java.lang.String` | `getPrefix``()`<br>Get the prefix for this name                                      |
    | `java.lang.String` | `getQualifiedName``()`<br>Get the qualified name, i.e., prefix:ncname                |

<!-- -->

- - ### Method Detail

    - #### getQualifiedName

          java.lang.String getQualifiedName()

      Get the qualified name, i.e., prefix:ncname
      Returns:
      The qualified name, i.e., prefix:ncname

    <!-- -->

    - #### getNamespace

          java.lang.String getNamespace()

      Get the resolved Namespace for this name
      Returns:
      The resolved Namespace

    <!-- -->

    - #### getPrefix

          java.lang.String getPrefix()

      Get the prefix for this name
      Returns:
      The prefix

    <!-- -->

    - #### getLocalName

          java.lang.String getLocalName()

      Get the local name for this name
      Returns:
      The local name

    <!-- -->

    - #### getExpandedName

          java.lang.String getExpandedName()

      Get the fully resolved name for this name, i.e., uri:ncname
      Returns:
      The fully resolved name, i.e., uri:ncname

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **[Next Class](Queue.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
