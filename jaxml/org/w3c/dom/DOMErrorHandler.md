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

- **[Prev Class](DOMError.md)**
- **[Next Class](DOMException.md)**

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

## **Interface DOMErrorHandler**

-

  ------------------------------------------------------------------------

  **
  **

      public interface DOMErrorHandler

  **`DOMErrorHandler` is a callback interface that the DOM implementation can call when reporting errors that happens while processing XML data, or when doing some other processing (e.g. validating a document). A `DOMErrorHandler` object can be attached to a `Document` using the "error-handler" on the `DOMConfiguration` interface. If more than one error needs to be reported during an operation, the sequence and numbers of the errors passed to the error handler are implementation dependent.**
  **The application that is using the DOM implementation is expected to implement this interface.**

  **See also the [Document Object Model (DOM) Level 3 Core Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107).**

  **Since:**
  **DOM Level 3**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                 |
    |-------------------|------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `handleError``(`[`DOMError`](DOMError.md)` error)`<br>This method is called on the error handler when an error occurs. |

<!-- -->

- - ### Method Detail

    - #### handleError

          boolean handleError(DOMError error)

      This method is called on the error handler when an error occurs.
      If an exception is thrown from this method, it is considered to be equivalent of returning `true`.
      Parameters:
      `error` - The error object that describes the error. This object may be reused by the DOM implementation across multiple calls to the `handleError` method.

      Returns:
      If the `handleError` method returns `false`, the DOM implementation should stop the current processing when possible. If the method returns `true`, the processing may continue depending on `DOMError.severity`.

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

- **[Prev Class](DOMError.md)**
- **[Next Class](DOMException.md)**

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
