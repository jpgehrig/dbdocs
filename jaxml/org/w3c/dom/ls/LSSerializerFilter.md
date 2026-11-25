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

- **[Prev Class](LSSerializer.md)**
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

**org.w3c.dom.ls**

## **Interface LSSerializerFilter**

- **All Superinterfaces:**
  **[NodeFilter](../traversal/NodeFilter.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface LSSerializerFilter
      extends NodeFilter

  **`LSSerializerFilter`s provide applications the ability to examine nodes as they are being serialized and decide what nodes should be serialized or not. The `LSSerializerFilter` interface is based on the `NodeFilter` interface defined in \[[DOM Level 2 Traversal and Range](http://www.w3.org/TR/2000/REC-DOM-Level-2-Traversal-Range-20001113)\] .**
  **`Document`, `DocumentType`, `DocumentFragment`, `Notation`, and `Entity` nodes are not passed to the filter.**

  **When serializing an `Element`, the element is passed to the filter before any of its attributes are passed to the filter. Namespace declaration attributes, and default attributes (except in the case when " discard-default-content" is set to `false`), are never passed to the filter.**

  **The result of any attempt to modify a node passed to a `LSSerializerFilter` is implementation dependent.**

  **See also the [Document Object Model (DOM) Level 3 Load and Save Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-LS-20031107).**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface org.w3c.dom.traversal.[NodeFilter](../traversal/NodeFilter.md)**

      **[`FILTER_ACCEPT`](../traversal/NodeFilter.md)`, `[`FILTER_REJECT`](../traversal/NodeFilter.md)`, `[`FILTER_SKIP`](../traversal/NodeFilter.md)`, `[`SHOW_ALL`](../traversal/NodeFilter.md)`, `[`SHOW_ATTRIBUTE`](../traversal/NodeFilter.md)`, `[`SHOW_CDATA_SECTION`](../traversal/NodeFilter.md)`, `[`SHOW_COMMENT`](../traversal/NodeFilter.md)`, `[`SHOW_DOCUMENT`](../traversal/NodeFilter.md)`, `[`SHOW_DOCUMENT_FRAGMENT`](../traversal/NodeFilter.md)`, `[`SHOW_DOCUMENT_TYPE`](../traversal/NodeFilter.md)`, `[`SHOW_ELEMENT`](../traversal/NodeFilter.md)`, `[`SHOW_ENTITY`](../traversal/NodeFilter.md)`, `[`SHOW_ENTITY_REFERENCE`](../traversal/NodeFilter.md)`, `[`SHOW_NOTATION`](../traversal/NodeFilter.md)`, `[`SHOW_PROCESSING_INSTRUCTION`](../traversal/NodeFilter.md)`, `[`SHOW_TEXT`](../traversal/NodeFilter.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                     |
    |-------------------|--------------------------------------------------------------------------------------------|
    | `int`             | `getWhatToShow``()`<br>Tells the `LSSerializer` what types of nodes to show to the filter. |

    - ### Methods inherited from interface org.w3c.dom.traversal.[NodeFilter](../traversal/NodeFilter.md)

      [`acceptNode`](../traversal/NodeFilter.md)

<!-- -->

- - ### Method Detail

    - #### getWhatToShow

          int getWhatToShow()

      Tells the `LSSerializer` what types of nodes to show to the filter. See `NodeFilter` for definition of the constants. The constants `SHOW_DOCUMENT`, `SHOW_DOCUMENT_TYPE`, `SHOW_DOCUMENT_FRAGMENT`, `SHOW_NOTATION`, and `SHOW_ENTITY` are meaningless here, such nodes will never be passed to a `LSSerializerFilter`.
      The constants used here are defined in \[[DOM Level 2 Traversal and Range](http://www.w3.org/TR/2000/REC-DOM-Level-2-Traversal-Range-20001113)\] .

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

- **[Prev Class](LSSerializer.md)**
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

**[Copyright](http://www.w3.org/Consortium/Legal/ipr-notice#Copyright) ©2004 [W3C](http://www.w3.org/)® ([MIT](http://www.csail.mit.edu/), [ERCIM](http://www.ercim.org/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/ipr-notice#Legal_Disclaimer), [trademark](http://www.w3.org/Consortium/Legal/ipr-notice#W3C_Trademarks), [document use](http://www.w3.org/Consortium/Legal/copyright-documents) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software) rules apply. The latest version is at <http://www.w3.org/TR/DOM-Level-3-LS>.**
