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

- **[Prev Class](DOMImplementationList.md)**
- **[Next Class](DOMLocator.md)**

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

## **Interface DOMImplementationSource**

-

  ------------------------------------------------------------------------

  **
  **

      public interface DOMImplementationSource

  **This interface permits a DOM implementer to supply one or more implementations, based upon requested features and versions, as specified in . Each implemented `DOMImplementationSource` object is listed in the binding-specific list of available sources so that its `DOMImplementation` objects are made available.**
  **See also the [Document Object Model (DOM) Level 3 Core Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107).**

  **Since:**
  **DOM Level 3**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                                           |
    |-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`DOMImplementation`](DOMImplementation.md)         | `getDOMImplementation``(java.lang.String features)`<br>A method to request the first DOM implementation that supports the specified features.                                    |
    | [`DOMImplementationList`](DOMImplementationList.md) | `getDOMImplementationList``(java.lang.String features)`<br>A method to request a list of DOM implementations that support the specified features and versions, as specified in . |

<!-- -->

- - ### Method Detail

    - #### getDOMImplementation

          DOMImplementation getDOMImplementation(java.lang.String features)

      A method to request the first DOM implementation that supports the specified features.
      Parameters:
      `features` - A string that specifies which features and versions are required. This is a space separated list in which each feature is specified by its name optionally followed by a space and a version number. This method returns the first item of the list returned by `getDOMImplementationList`. As an example, the string `"XML 3.0 Traversal +Events 2.0"` will request a DOM implementation that supports the module "XML" for its 3.0 version, a module that support of the "Traversal" module for any version, and the module "Events" for its 2.0 version. The module "Events" must be accessible using the method `Node.getFeature()` and `DOMImplementation.getFeature()`.

      Returns:
      The first DOM implementation that support the desired features, or `null` if this source has none.

    <!-- -->

    - #### getDOMImplementationList

          DOMImplementationList getDOMImplementationList(java.lang.String features)

      A method to request a list of DOM implementations that support the specified features and versions, as specified in .
      Parameters:
      `features` - A string that specifies which features and versions are required. This is a space separated list in which each feature is specified by its name optionally followed by a space and a version number. This is something like: "XML 3.0 Traversal +Events 2.0"

      Returns:
      A list of DOM implementations that support the desired features.

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

- **[Prev Class](DOMImplementationList.md)**
- **[Next Class](DOMLocator.md)**

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
