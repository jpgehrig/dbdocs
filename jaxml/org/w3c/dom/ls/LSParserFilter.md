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

- **[Prev Class](LSParser.md)**
- **[Next Class](LSProgressEvent.md)**

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

## **Interface LSParserFilter**

-

  ------------------------------------------------------------------------

  **
  **

      public interface LSParserFilter

  **`LSParserFilter`s provide applications the ability to examine nodes as they are being constructed while parsing. As each node is examined, it may be modified or removed, or the entire parse may be terminated early.**
  **At the time any of the filter methods are called by the parser, the owner Document and DOMImplementation objects exist and are accessible. The document element is never passed to the `LSParserFilter` methods, i.e. it is not possible to filter out the document element. `Document`, `DocumentType`, `Notation`, `Entity`, and `Attr` nodes are never passed to the `acceptNode` method on the filter.**

  **All validity checking while parsing a document occurs on the source document as it appears on the input stream, not on the DOM document as it is built in memory. With filters, the document in memory may be a subset of the document on the stream, and its validity may have been affected by the filtering.**

  **All default attributes must be present on elements when the elements are passed to the filter methods. All other default content must be passed to the filter methods.**

  **The `LSParser` ignores any exception raised in the filter.**

  **See also the [Document Object Model (DOM) Level 3 Load and Save Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-LS-20031107).**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                  |
    |-------------------|------------------------------------------------------------------------|
    | `static short`    | `FILTER_ACCEPT`<br>Accept the node.                                    |
    | `static short`    | `FILTER_INTERRUPT`<br>Interrupt the normal processing of the document. |
    | `static short`    | `FILTER_REJECT`<br>Reject the node and its children.                   |
    | `static short`    | `FILTER_SKIP`<br>Skip this single node.                                |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                 |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `short`           | `acceptNode``(`[`Node`](../Node.md)` nodeArg)`<br>This method will be called by the parser at the completion of the parsing of each node.                                                              |
    | `int`             | `getWhatToShow``()`<br>Tells the `LSParser` what types of nodes to show to the filter.                                                                                                                 |
    | `short`           | `startElement``(`[`Element`](../Element.md)` elementArg)`<br>The parser will call this method after each `Element` start tag has been scanned, but before the remainder of the `Element` is processed. |

<!-- -->

- - ### Field Detail

    - #### FILTER_ACCEPT

          static final short FILTER_ACCEPT

      Accept the node.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### FILTER_REJECT

          static final short FILTER_REJECT

      Reject the node and its children.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### FILTER_SKIP

          static final short FILTER_SKIP

      Skip this single node. The children of this node will still be considered.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### FILTER_INTERRUPT

          static final short FILTER_INTERRUPT

      Interrupt the normal processing of the document.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### startElement

          short startElement(Element elementArg)

      The parser will call this method after each `Element` start tag has been scanned, but before the remainder of the `Element` is processed. The intent is to allow the element, including any children, to be efficiently skipped. Note that only element nodes are passed to the `startElement` function.
      The element node passed to `startElement` for filtering will include all of the Element's attributes, but none of the children nodes. The Element may not yet be in place in the document being constructed (it may not have a parent node.)
      A `startElement` filter function may access or change the attributes for the Element. Changing Namespace declarations will have no effect on namespace resolution by the parser.
      For efficiency, the Element node passed to the filter may not be the same one as is actually placed in the tree if the node is accepted. And the actual node (node object identity) may be reused during the process of reading in and filtering a document.
      Parameters:
      `elementArg` - The newly encountered element. At the time this method is called, the element is incomplete - it will have its attributes, but no children.

      Returns:
      - `FILTER_ACCEPT` if the `Element` should be included in the DOM document being built.
      - `FILTER_REJECT` if the `Element` and all of its children should be rejected. This return value will be ignored if `element` is the documentElement, the documentElement cannot be rejected.
      - `FILTER_SKIP` if the `Element` should be skipped. All of its children are inserted in place of the skipped `Element` node. This return value will be ignored if `element` is the documentElement, the documentElement cannot be skipped.
      - `FILTER_INTERRUPT` if the filter wants to stop the processing of the document. Interrupting the processing of the document does no longer guarantee that the resulting DOM tree is XML well-formed. The `Element` is rejected.

      Returning any other values will result in unspecified behavior.

    <!-- -->

    - #### acceptNode

          short acceptNode(Node nodeArg)

      This method will be called by the parser at the completion of the parsing of each node. The node and all of its descendants will exist and be complete. The parent node will also exist, although it may be incomplete, i.e. it may have additional children that have not yet been parsed. Attribute nodes are never passed to this function.
      From within this method, the new node may be freely modified - children may be added or removed, text nodes modified, etc. The state of the rest of the document outside this node is not defined, and the affect of any attempt to navigate to, or to modify any other part of the document is undefined.
      For validating parsers, the checks are made on the original document, before any modification by the filter. No validity checks are made on any document modifications made by the filter.
      If this new node is rejected, the parser might reuse the new node and any of its descendants.
      Parameters:
      `nodeArg` - The newly constructed element. At the time this method is called, the element is complete - it has all of its children (and their children, recursively) and attributes, and is attached as a child to its parent.

      Returns:
      - `FILTER_ACCEPT` if this `Node` should be included in the DOM document being built.
      - `FILTER_REJECT` if the `Node` and all of its children should be rejected.
      - `FILTER_SKIP` if the `Node` should be skipped and the `Node` should be replaced by all the children of the `Node`.
      - `FILTER_INTERRUPT` if the filter wants to stop the processing of the document. Interrupting the processing of the document does no longer guarantee that the resulting DOM tree is XML well-formed. The `Node` is accepted and will be the last completely parsed node.

    <!-- -->

    - #### getWhatToShow

          int getWhatToShow()

      Tells the `LSParser` what types of nodes to show to the filter. See `NodeFilter` for definition of the constants. The constants `SHOW_ATTRIBUTE`, `SHOW_DOCUMENT` , `SHOW_DOCUMENT_TYPE`, `SHOW_NOTATION`, `SHOW_ENTITY`, and `SHOW_DOCUMENT_FRAGMENT` are meaningless here, those nodes will never be passed to a `LSParserFilter`.
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

- **[Prev Class](LSParser.md)**
- **[Next Class](LSProgressEvent.md)**

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
