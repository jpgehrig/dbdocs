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
- **[Next Class](DOMResult.md)**

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

**javax.xml.transform.dom**

## **Interface DOMLocator**

- **All Superinterfaces:**
  **[SourceLocator](../SourceLocator.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DOMLocator
      extends SourceLocator

  **Indicates the position of a node in a source DOM, intended primarily for error reporting. To use a DOMLocator, the receiver of an error must downcast the SourceLocator object returned by an exception. A Transformer may use this object for purposes other than error reporting, for instance, to indicate the source node that originated a result node.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                         | Method and Description                                                |
    |-------------------------------------------|-----------------------------------------------------------------------|
    | [`Node`](../../../../org/w3c/dom/Node.md) | `getOriginatingNode``()`<br>Return the node where the event occurred. |

    - ### Methods inherited from interface javax.xml.transform.[SourceLocator](../SourceLocator.md)

      [`getColumnNumber`](../SourceLocator.md)`, `[`getLineNumber`](../SourceLocator.md)`, `[`getPublicId`](../SourceLocator.md)`, `[`getSystemId`](../SourceLocator.md)

<!-- -->

- - ### Method Detail

    - #### getOriginatingNode

          Node getOriginatingNode()

      Return the node where the event occurred.
      Returns:
      The node that is the location for the event.

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
- **[Next Class](DOMResult.md)**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
