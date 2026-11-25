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

- **[Prev Class](ExceptionVAL.md)**
- **Next Class**

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

## **Interface NodeEditVAL**

- **All Known Subinterfaces:**
  **[CharacterDataEditVAL](CharacterDataEditVAL.md), [DocumentEditVAL](DocumentEditVAL.md), [ElementEditVAL](ElementEditVAL.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[AttrDecl](../../../../oracle/xml/parser/v2/AttrDecl.md), [DTD](../../../../oracle/xml/parser/v2/DTD.md), [ElementDecl](../../../../oracle/xml/parser/v2/ElementDecl.md), [XMLAttr](../../../../oracle/xml/parser/v2/XMLAttr.md), [XMLCDATA](../../../../oracle/xml/parser/v2/XMLCDATA.md), [XMLComment](../../../../oracle/xml/parser/v2/XMLComment.md), [XMLDeclPI](../../../../oracle/xml/parser/v2/XMLDeclPI.md), [XMLDocument](../../../../oracle/xml/parser/v2/XMLDocument.md), [XMLDocumentFragment](../../../../oracle/xml/parser/v2/XMLDocumentFragment.md), [XMLElement](../../../../oracle/xml/parser/v2/XMLElement.md), [XMLEntity](../../../../oracle/xml/parser/v2/XMLEntity.md), [XMLEntityReference](../../../../oracle/xml/parser/v2/XMLEntityReference.md), [XMLNode](../../../../oracle/xml/parser/v2/XMLNode.md), [XMLNotation](../../../../oracle/xml/parser/v2/XMLNotation.md), [XMLNSNode](../../../../oracle/xml/parser/v2/XMLNSNode.md), [XMLPI](../../../../oracle/xml/parser/v2/XMLPI.md), [XMLText](../../../../oracle/xml/parser/v2/XMLText.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface NodeEditVAL

  **This interface is similar to the \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] `Node` interface, with methods for guided document editing.**
  **See also the [Document Object Model (DOM) Level 3 Validation Specification](https://www.w3.org/TR/DOM-Level-3-Val/validation.html).**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                          |
    |-------------------|----------------------------------------------------------------------------------------------------------------|
    | `static short`    | `VAL_FALSE`<br>False if the node is invalid with regards to the operation, or if the operation cannot be done. |
    | `static short`    | `VAL_INCOMPLETE`<br>Check if the node's immediate children are those expected by the content model.            |
    | `static short`    | `VAL_NS_WF`<br>Check if the node is namespace well-formed.                                                     |
    | `static short`    | `VAL_SCHEMA`<br>Check if the node's entire subtree are those expected by the the content model.                |
    | `static short`    | `VAL_TRUE`<br>True if the node is valid with regards to the operation, or if the operation can be done.        |
    | `static short`    | `VAL_UNKNOWN`<br>The validity of the node is unknown.                                                          |
    | `static short`    | `VAL_WF`<br>Check if the node is well-formed.                                                                  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                      | Method and Description                                                                                                                                                                                                                   |
    |----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `short`                                | `canAppendChild``(`[`Node`](../Node.md)` newChild)`<br>Determines whether the `Node.appendChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                               |
    | `short`                                | `canInsertBefore``(`[`Node`](../Node.md)` newChild, `[`Node`](../Node.md)` refChild)`<br>Determines whether the `Node.insertBefore` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.            |
    | `short`                                | `canRemoveChild``(`[`Node`](../Node.md)` oldChild)`<br>Determines whether the `Node.removeChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                               |
    | `short`                                | `canReplaceChild``(`[`Node`](../Node.md)` newChild, `[`Node`](../Node.md)` oldChild)`<br>Determines whether the `Node.replaceChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.            |
    | `java.lang.String`                     | `getDefaultValue``()`<br>The default value specified in an attribute or an element declaration or `null` if unspecified.                                                                                                                 |
    | [`DOMStringList`](../DOMStringList.md) | `getEnumeratedValues``()`<br>A `DOMStringList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of distinct values for an attribute or an element declaration or `null` if unspecified. |
    | `short`                                | `nodeValidity``(short wFValidityCheckLevel)`<br>Determines if the node is valid relative to the validation type specified in `valType`.                                                                                                  |

<!-- -->

- - ### Field Detail

    - #### VAL_WF

          static final short VAL_WF

      Check if the node is well-formed.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VAL_NS_WF

          static final short VAL_NS_WF

      Check if the node is namespace well-formed.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VAL_INCOMPLETE

          static final short VAL_INCOMPLETE

      Check if the node's immediate children are those expected by the content model. This node's trailing required children could be missing. It includes `VAL_NS_WF`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VAL_SCHEMA

          static final short VAL_SCHEMA

      Check if the node's entire subtree are those expected by the the content model. It includes `VAL_NS_WF`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VAL_TRUE

          static final short VAL_TRUE

      True if the node is valid with regards to the operation, or if the operation can be done.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VAL_FALSE

          static final short VAL_FALSE

      False if the node is invalid with regards to the operation, or if the operation cannot be done.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### VAL_UNKNOWN

          static final short VAL_UNKNOWN

      The validity of the node is unknown.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getDefaultValue

          java.lang.String getDefaultValue()

      The default value specified in an attribute or an element declaration or `null` if unspecified. Elena wanted mention of XML Schema's canonical lexical representation here. Why?

    <!-- -->

    - #### getEnumeratedValues

          DOMStringList getEnumeratedValues()

      A `DOMStringList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of distinct values for an attribute or an element declaration or `null` if unspecified. Elena wanted mention of XML Schema's canonical lexical representation here. Why?

    <!-- -->

    - #### canInsertBefore

          short canInsertBefore(Node newChild,
                                Node refChild)

      Determines whether the `Node.insertBefore` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.
      Parameters:
      `newChild` - `Node` to be inserted.

      `refChild` - Reference `Node`.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canRemoveChild

          short canRemoveChild(Node oldChild)

      Determines whether the `Node.removeChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.
      Parameters:
      `oldChild` - `Node` to be removed.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canReplaceChild

          short canReplaceChild(Node newChild,
                                Node oldChild)

      Determines whether the `Node.replaceChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.
      Parameters:
      `newChild` - New `Node`.

      `oldChild` - `Node` to be replaced.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canAppendChild

          short canAppendChild(Node newChild)

      Determines whether the `Node.appendChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.
      Parameters:
      `newChild` - `Node` to be appended.

      Returns:
      A validation state constant.

    <!-- -->

    - #### nodeValidity

          short nodeValidity(short wFValidityCheckLevel)

      Determines if the node is valid relative to the validation type specified in `valType`. This operation doesn't normalize before checking if it is valid. To do so, one would need to explicitly call a normalize method. The difference between this method and the `validateDocument` method on the `DocumentVAL` interface is that `validateDocument` only checks to determine whether the entire document is valid.
      Parameters:
      `wFValidityCheckLevel` - Flag to tell at what level validity and well-formedness checking is done.

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

- **[Prev Class](ExceptionVAL.md)**
- **Next Class**

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
