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

- **[Prev Class](CharacterDataEditVAL.md)**
- **[Next Class](ElementEditVAL.md)**

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

**org.w3c.dom.validation**

## **Interface DocumentEditVAL**

- **All Superinterfaces:**
  **[NodeEditVAL](NodeEditVAL.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[XMLDocument](../../../../oracle/xml/parser/v2/XMLDocument.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DocumentEditVAL
      extends NodeEditVAL

  **This interface extends the `NodeEditVAL` interface with additional methods for document editing. An object implementing this interface must also implement the `Document` interface.**
  **See also the [Document Object Model (DOM) Level 3 Validation Specification](https://www.w3.org/TR/DOM-Level-3-Val/validation.html).**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface org.w3c.dom.validation.[NodeEditVAL](NodeEditVAL.md)**

      **[`VAL_FALSE`](NodeEditVAL.md)`, `[`VAL_INCOMPLETE`](NodeEditVAL.md)`, `[`VAL_NS_WF`](NodeEditVAL.md)`, `[`VAL_SCHEMA`](NodeEditVAL.md)`, `[`VAL_TRUE`](NodeEditVAL.md)`, `[`VAL_UNKNOWN`](NodeEditVAL.md)`, `[`VAL_WF`](NodeEditVAL.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type            | Method and Description                                                                                                                                                   |
    |------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `short`                      | `getContinuousValidityChecking``()`<br>An attribute specifying whether the validity of the document is continuously enforced.                                            |
    | [`NameList`](../NameList.md) | `getDefinedElements``(java.lang.String namespaceURI)`<br>Returns list of all element information item names of global declaration, belonging to the specified namespace. |
    | `void`                       | `setContinuousValidityChecking``(short continuousValidityChecking)`<br>An attribute specifying whether the validity of the document is continuously enforced.            |
    | `short`                      | `validateDocument``()`<br>Validates the document against the schema, e.g., a DTD or an XML Schema or another.                                                            |

    - ### Methods inherited from interface org.w3c.dom.validation.[NodeEditVAL](NodeEditVAL.md)

      [`canAppendChild`](NodeEditVAL.md)`, `[`canInsertBefore`](NodeEditVAL.md)`, `[`canRemoveChild`](NodeEditVAL.md)`, `[`canReplaceChild`](NodeEditVAL.md)`, `[`getDefaultValue`](NodeEditVAL.md)`, `[`getEnumeratedValues`](NodeEditVAL.md)`, `[`nodeValidity`](NodeEditVAL.md)

<!-- -->

- - ### Method Detail

    - #### getContinuousValidityChecking

          short getContinuousValidityChecking()

      An attribute specifying whether the validity of the document is continuously enforced. When the attribute is set to `true` , the implementation may raise certain exceptions, depending on the situation (see the following). This attribute is `false` by default.

    <!-- -->

    - #### setContinuousValidityChecking

          void setContinuousValidityChecking(short continuousValidityChecking)
                                      throws DOMException,
                                             ExceptionVAL,
                                             DOMException

      An attribute specifying whether the validity of the document is continuously enforced. When the attribute is set to `true` , the implementation may raise certain exceptions, depending on the situation (see the following). This attribute is `false` by default.
      Throws:
      [`DOMException`](../DOMException.md) - NOT_SUPPORTED_ERR: Raised if the implementation does not support setting this attribute to `true`.

      [`ExceptionVAL`](ExceptionVAL.md) - NO_SCHEMA_AVAILABLE_ERR: Raised if this attribute is set to `true` and a schema is unavailable.

      [`DOMException`](../DOMException.md) - VALIDATION_ERR: Raised if an operation makes this document not compliant with the `VAL_INCOMPLETE` validity type or the document is invalid, and this attribute is set to `true` .

    <!-- -->

    - #### getDefinedElements

          NameList getDefinedElements(java.lang.String namespaceURI)

      Returns list of all element information item names of global declaration, belonging to the specified namespace.
      Parameters:
      `namespaceURI` - `namespaceURI` of namespace. For DTDs, this is `null`.

      Returns:
      List of all element information item names belonging to the specified namespace or `null` if no schema is available.

    <!-- -->

    - #### validateDocument

          short validateDocument()

      Validates the document against the schema, e.g., a DTD or an XML Schema or another. This method's behavior is implementation- dependent; and the any attempt to modify any part of the document while validating results in implementation-dependent behavior. In addition, the validation operation itself cannot modify the document, e.g., for default attributes. This method makes use of the passed-in error handler, as described in the \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] `DOMConfiguration` interface, with all errors being `SEVERITY_ERROR` as defined in the `DOMError` interface.
      Returns:
      A validation state constant.

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

- **[Prev Class](CharacterDataEditVAL.md)**
- **[Next Class](ElementEditVAL.md)**

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

**[Copyright](http://www.w3.org/Consortium/Legal/ipr-notice#Copyright) ©2004 [W3C](http://www.w3.org/)® ([MIT](http://www.csail.mit.edu/), [ERCIM](http://www.ercim.org/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/ipr-notice#Legal_Disclaimer), [trademark](http://www.w3.org/Consortium/Legal/ipr-notice#W3C_Trademarks), [document use](http://www.w3.org/Consortium/Legal/copyright-documents) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software) rules apply. The latest version is at [http://www.w3.org/TR/DOM-Level-3-Val](http://www.w3.org/TR/DOM-Level-3-Val/).**
