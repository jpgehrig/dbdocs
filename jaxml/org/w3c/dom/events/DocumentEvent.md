Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **[Next Class](Event.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**org.w3c.dom.events**

## **Interface DocumentEvent**

- **All Known Implementing Classes:**
  **[XMLDocument](../../../../oracle/xml/parser/v2/XMLDocument.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DocumentEvent

  **The `DocumentEvent` interface provides a mechanism by which the user can create an Event of a type supported by the implementation. It is expected that the `DocumentEvent` interface will be implemented on the same object which implements the `Document` interface in an implementation which supports the Event model.**
  **See also the [Document Object Model (DOM) Level 2 Events Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Events-20001113).**

  **Since:**
  **DOM Level 2**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type   | Method and Description                       |
    |---------------------|----------------------------------------------|
    | [`Event`](Event.md) | `createEvent``(java.lang.String eventType)`  |

<!-- -->

- - ### Method Detail

    - #### createEvent

          Event createEvent(java.lang.String eventType)
                     throws DOMException

      Parameters:
      `eventType` - The `eventType` parameter specifies the type of `Event` interface to be created. If the `Event` interface specified is supported by the implementation this method will return a new `Event` of the interface type requested. If the `Event` is to be dispatched via the `dispatchEvent` method the appropriate event init method must be called after creation in order to initialize the `Event`'s values. As an example, a user wishing to synthesize some kind of `UIEvent` would call `createEvent` with the parameter "UIEvents". The `initUIEvent` method could then be called on the newly created `UIEvent` to set the specific type of UIEvent to be dispatched and set its context information.The `createEvent` method is used in creating `Event`s when it is either inconvenient or unnecessary for the user to create an `Event` themselves. In cases where the implementation provided `Event` is insufficient, users may supply their own `Event` implementations for use with the `dispatchEvent` method.

      Returns:
      The newly created `Event`

      Throws:
      [`DOMException`](../DOMException.md) - NOT_SUPPORTED_ERR: Raised if the implementation does not support the type of `Event` interface requested

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **Prev Class**
- **[Next Class](Event.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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
