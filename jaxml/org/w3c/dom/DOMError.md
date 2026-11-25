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

- **[Prev Class](DOMConfiguration.md)**
- **[Next Class](DOMErrorHandler.md)**

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

## **Interface DOMError**

- **All Known Implementing Classes:**
  **[XMLError](../../../oracle/xml/parser/v2/XMLError.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DOMError

  **`DOMError` is an interface that describes an error.**
  **See also the [Document Object Model (DOM) Level 3 Core Specification](http://www.w3.org/TR/2003/WD-DOM-Level-3-Core-20030226).**

  **Since:**
  **DOM Level 3**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                          |
    |-------------------|------------------------------------------------------------------------------------------------|
    | `static short`    | `SEVERITY_ERROR`<br>The severity of the error described by the `DOMError` is error             |
    | `static short`    | `SEVERITY_FATAL_ERROR`<br>The severity of the error described by the `DOMError` is fatal error |
    | `static short`    | `SEVERITY_WARNING`<br>The severity of the error described by the `DOMError` is warning         |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type             | Method and Description                                                                                                                                        |
    |-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`DOMLocator`](DOMLocator.md) | `getLocation``()`<br>The location of the error.                                                                                                               |
    | `java.lang.String`            | `getMessage``()`<br>An implementation specific string describing the error that occured.                                                                      |
    | `java.lang.Object`            | `getRelatedData``()`<br>The related `DOMError.type` dependent data if any.                                                                                    |
    | `java.lang.Object`            | `getRelatedException``()`<br>The related platform dependent exception if any.exception is a reserved word, we need to rename it.Change to "relatedException". |
    | `short`                       | `getSeverity``()`<br>The severity of the error, either `SEVERITY_WARNING`, `SEVERITY_ERROR`, or `SEVERITY_FATAL_ERROR`.                                       |
    | `java.lang.String`            | `getType``()`<br>A `DOMString` indicating which related data is expected in `relatedData`.                                                                    |

<!-- -->

- - ### Field Detail

    - #### SEVERITY_WARNING

          static final short SEVERITY_WARNING

      The severity of the error described by the `DOMError` is warning
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SEVERITY_ERROR

          static final short SEVERITY_ERROR

      The severity of the error described by the `DOMError` is error
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SEVERITY_FATAL_ERROR

          static final short SEVERITY_FATAL_ERROR

      The severity of the error described by the `DOMError` is fatal error
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getSeverity

          short getSeverity()

      The severity of the error, either `SEVERITY_WARNING`, `SEVERITY_ERROR`, or `SEVERITY_FATAL_ERROR`.

    <!-- -->

    - #### getMessage

          java.lang.String getMessage()

      An implementation specific string describing the error that occured.

    <!-- -->

    - #### getType

          java.lang.String getType()

      A `DOMString` indicating which related data is expected in `relatedData`. Users should refer to the specification of the error in order to find its `DOMString` type and `relatedData` definitions if any.
      **Note:** As an example, \[[DOM Level 3 Load and Save](http://www.w3.org/TR/DOM-Level-3-LS)\] does not keep the \[baseURI\] property defined on a Processing Instruction information item. Therefore, the `DOMBuilder` generates a `SEVERITY_WARNING` with `type` `"infoset-baseURI"` and the lost \[baseURI\] property represented as a `DOMString` in the `relatedData` attribute.

    <!-- -->

    - #### getRelatedException

          java.lang.Object getRelatedException()

      The related platform dependent exception if any.exception is a reserved word, we need to rename it.Change to "relatedException". (F2F 26 Sep 2001)

    <!-- -->

    - #### getRelatedData

          java.lang.Object getRelatedData()

      The related `DOMError.type` dependent data if any.

    <!-- -->

    - #### getLocation

          DOMLocator getLocation()

      The location of the error.

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

- **[Prev Class](DOMConfiguration.md)**
- **[Next Class](DOMErrorHandler.md)**

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
