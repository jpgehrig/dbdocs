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

- **[Prev Class](LSInput.md)**
- **[Next Class](LSOutput.md)**

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

**org.w3c.dom.ls**

## **Interface LSLoadEvent**

- **All Superinterfaces:**
  **[Event](../events/Event.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface LSLoadEvent
      extends Event

  **This interface represents a load event object that signals the completion of a document load.**
  **See also the [Document Object Model (DOM) Level 3 Load and Save Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-LS-20031107).**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface org.w3c.dom.events.[Event](../events/Event.md)**

      **[`AT_TARGET`](../events/Event.md)`, `[`BUBBLING_PHASE`](../events/Event.md)`, `[`CAPTURING_PHASE`](../events/Event.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type            | Method and Description                                      |
    |------------------------------|-------------------------------------------------------------|
    | [`LSInput`](LSInput.md)      | `getInput``()`<br>The input source that was parsed.         |
    | [`Document`](../Document.md) | `getNewDocument``()`<br>The document that finished loading. |

    - ### Methods inherited from interface org.w3c.dom.events.[Event](../events/Event.md)

      [`getBubbles`](../events/Event.md)`, `[`getCancelable`](../events/Event.md)`, `[`getCurrentTarget`](../events/Event.md)`, `[`getEventPhase`](../events/Event.md)`, `[`getTarget`](../events/Event.md)`, `[`getTimeStamp`](../events/Event.md)`, `[`getType`](../events/Event.md)`, `[`initEvent`](../events/Event.md)`, `[`preventDefault`](../events/Event.md)`, `[`stopPropagation`](../events/Event.md)

<!-- -->

- - ### Method Detail

    - #### getNewDocument

          Document getNewDocument()

      The document that finished loading.

    <!-- -->

    - #### getInput

          LSInput getInput()

      The input source that was parsed.

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

- **[Prev Class](LSInput.md)**
- **[Next Class](LSOutput.md)**

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

**[Copyright](http://www.w3.org/Consortium/Legal/ipr-notice#Copyright) ©2004 [W3C](http://www.w3.org/)® ([MIT](http://www.csail.mit.edu/), [ERCIM](http://www.ercim.org/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/ipr-notice#Legal_Disclaimer), [trademark](http://www.w3.org/Consortium/Legal/ipr-notice#W3C_Trademarks), [document use](http://www.w3.org/Consortium/Legal/copyright-documents) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software) rules apply. The latest version is at <http://www.w3.org/TR/DOM-Level-3-LS>.**
