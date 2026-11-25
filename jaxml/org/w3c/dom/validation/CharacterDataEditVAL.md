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
- **[Next Class](DocumentEditVAL.md)**

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

## **Interface CharacterDataEditVAL**

- **All Superinterfaces:**
  **[NodeEditVAL](NodeEditVAL.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[XMLCDATA](../../../../oracle/xml/parser/v2/XMLCDATA.md), [XMLComment](../../../../oracle/xml/parser/v2/XMLComment.md), [XMLDeclPI](../../../../oracle/xml/parser/v2/XMLDeclPI.md), [XMLPI](../../../../oracle/xml/parser/v2/XMLPI.md), [XMLText](../../../../oracle/xml/parser/v2/XMLText.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface CharacterDataEditVAL
      extends NodeEditVAL

  **This interface extends the `NodeEditVAL` interface with additional methods for document editing. An object implementing this interface must also implement `CharacterData` interface.**
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

    | Modifier and Type | Method and Description                                                                                 |
    |-------------------|--------------------------------------------------------------------------------------------------------|
    | `short`           | `canAppendData``(java.lang.String arg)`<br>Determines if data can be appended.                         |
    | `short`           | `canDeleteData``(int offset, int count)`<br>Determines if data can be deleted.                         |
    | `short`           | `canInsertData``(int offset, java.lang.String arg)`<br>Determines if data can be inserted.             |
    | `short`           | `canReplaceData``(int offset, int count, java.lang.String arg)`<br>Determines if data can be replaced. |
    | `short`           | `canSetData``(java.lang.String arg)`<br>Determines if data can be set.                                 |
    | `short`           | `isWhitespaceOnly``()`<br>Determines if data is only whitespace.                                       |

    - ### Methods inherited from interface org.w3c.dom.validation.[NodeEditVAL](NodeEditVAL.md)

      [`canAppendChild`](NodeEditVAL.md)`, `[`canInsertBefore`](NodeEditVAL.md)`, `[`canRemoveChild`](NodeEditVAL.md)`, `[`canReplaceChild`](NodeEditVAL.md)`, `[`getDefaultValue`](NodeEditVAL.md)`, `[`getEnumeratedValues`](NodeEditVAL.md)`, `[`nodeValidity`](NodeEditVAL.md)

<!-- -->

- - ### Method Detail

    - #### isWhitespaceOnly

          short isWhitespaceOnly()

      Determines if data is only whitespace.
      Returns:
      A validation state constant.

    <!-- -->

    - #### canSetData

          short canSetData(java.lang.String arg)

      Determines if data can be set.
      Parameters:
      `arg` - Argument to be set.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canAppendData

          short canAppendData(java.lang.String arg)

      Determines if data can be appended.
      Parameters:
      `arg` - Data to be appended.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canReplaceData

          short canReplaceData(int offset,
                               int count,
                               java.lang.String arg)
                        throws DOMException

      Determines if data can be replaced.
      Parameters:
      `offset` - Offset.

      `count` - Replacement.

      `arg` - Argument to be set.

      Returns:
      A validation state constant.

      Throws:
      [`DOMException`](../DOMException.md) - INDEX_SIZE_ERR: Raised if the specified offset is negative or greater than the number of 16-bit units in data, or if the specified count is negative.

    <!-- -->

    - #### canInsertData

          short canInsertData(int offset,
                              java.lang.String arg)
                       throws DOMException

      Determines if data can be inserted.
      Parameters:
      `offset` - Offset.

      `arg` - Argument to be set.

      Returns:
      A validation state constant.

      Throws:
      [`DOMException`](../DOMException.md) - INDEX_SIZE_ERR: Raised if the specified offset is negative or greater than the number of 16-bit units in data.

    <!-- -->

    - #### canDeleteData

          short canDeleteData(int offset,
                              int count)
                       throws DOMException

      Determines if data can be deleted.
      Parameters:
      `offset` - Offset.

      `count` - Number of 16-bit units to delete.

      Returns:
      A validation state constant.

      Throws:
      [`DOMException`](../DOMException.md) - INDEX_SIZE_ERR: Raised if the specified offset is negative or greater than the number of 16-bit units in data, or if the specified count is negative.

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
- **[Next Class](DocumentEditVAL.md)**

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
