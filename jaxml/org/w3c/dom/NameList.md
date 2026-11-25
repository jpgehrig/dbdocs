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

- **[Prev Class](NamedNodeMap.md)**
- **[Next Class](Node.md)**

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

**org.w3c.dom**

## **Interface NameList**

-

  ------------------------------------------------------------------------

  **
  **

      public interface NameList

  **The `NameList` interface provides the abstraction of an ordered collection of parallel pairs of name and namespace values (which could be null values), without defining or constraining how this collection is implemented. The items in the `NameList` are accessible via an integral index, starting from 0.**
  **See also the [Document Object Model (DOM) Level 3 Core Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107).**

  **Since:**
  **DOM Level 3**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                 |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`          | `contains``(java.lang.String name)`<br>Test if a name is part of this `NameList`.                                                      |
    | `boolean`          | `containsNS``(java.lang.String namespaceURI, java.lang.String name)`<br>Test if the pair namespaceURI/name is part of this `NameList`. |
    | `int`              | `getLength``()`<br>The number of pairs (name and namespaceURI) in the list.                                                            |
    | `java.lang.String` | `getName``(int index)`<br>Returns the `index`th name item in the collection.                                                           |
    | `java.lang.String` | `getNamespaceURI``(int index)`<br>Returns the `index`th namespaceURI item in the collection.                                           |

<!-- -->

- - ### Method Detail

    - #### getName

          java.lang.String getName(int index)

      Returns the `index`th name item in the collection.
      Parameters:
      `index` - Index into the collection.

      Returns:
      The name at the `index`th position in the `NameList`, or `null` if there is no name for the specified index or if the index is out of range.

    <!-- -->

    - #### getNamespaceURI

          java.lang.String getNamespaceURI(int index)

      Returns the `index`th namespaceURI item in the collection.
      Parameters:
      `index` - Index into the collection.

      Returns:
      The namespace URI at the `index`th position in the `NameList`, or `null` if there is no name for the specified index or if the index is out of range.

    <!-- -->

    - #### getLength

          int getLength()

      The number of pairs (name and namespaceURI) in the list. The range of valid child node indices is 0 to `length-1` inclusive.

    <!-- -->

    - #### contains

          boolean contains(java.lang.String name)

      Test if a name is part of this `NameList`.
      Parameters:
      `name` - The name to look for.

      Returns:
      `true` if the name has been found, `false` otherwise.

    <!-- -->

    - #### containsNS

          boolean containsNS(java.lang.String namespaceURI,
                             java.lang.String name)

      Test if the pair namespaceURI/name is part of this `NameList`.
      Parameters:
      `namespaceURI` - The namespace URI to look for.

      `name` - The name to look for.

      Returns:
      `true` if the pair namespaceURI/name has been found, `false` otherwise.

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

- **[Prev Class](NamedNodeMap.md)**
- **[Next Class](Node.md)**

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

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
