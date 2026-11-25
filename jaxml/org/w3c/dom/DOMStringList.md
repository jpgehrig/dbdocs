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

- **[Prev Class](DOMLocator.md)**
- **[Next Class](Element.md)**

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

## **Interface DOMStringList**

-

  ------------------------------------------------------------------------

  **
  **

      public interface DOMStringList

  **The `DOMStringList` interface provides the abstraction of an ordered collection of `DOMString` values, without defining or constraining how this collection is implemented. The items in the `DOMStringList` are accessible via an integral index, starting from 0.**
  **See also the [Document Object Model (DOM) Level 3 Core Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107).**

  **Since:**
  **DOM Level 3**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                  |
    |--------------------|-----------------------------------------------------------------------------------------|
    | `boolean`          | `contains``(java.lang.String str)`<br>Test if a string is part of this `DOMStringList`. |
    | `int`              | `getLength``()`<br>The number of `DOMString`s in the list.                              |
    | `java.lang.String` | `item``(int index)`<br>Returns the `index`th item in the collection.                    |

<!-- -->

- - ### Method Detail

    - #### item

          java.lang.String item(int index)

      Returns the `index`th item in the collection. If `index` is greater than or equal to the number of `DOMString`s in the list, this returns `null`.
      Parameters:
      `index` - Index into the collection.

      Returns:
      The `DOMString` at the `index`th position in the `DOMStringList`, or `null` if that is not a valid index.

    <!-- -->

    - #### getLength

          int getLength()

      The number of `DOMString`s in the list. The range of valid child node indices is 0 to `length-1` inclusive.

    <!-- -->

    - #### contains

          boolean contains(java.lang.String str)

      Test if a string is part of this `DOMStringList`.
      Parameters:
      `str` - The string to look for.

      Returns:
      `true` if the string has been found, `false` otherwise.

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

- **[Prev Class](DOMLocator.md)**
- **[Next Class](Element.md)**

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
