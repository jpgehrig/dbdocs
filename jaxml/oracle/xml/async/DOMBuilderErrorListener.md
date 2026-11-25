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

- **[Prev Class](DOMBuilderErrorEvent.md)**
- **[Next Class](DOMBuilderEvent.md)**

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

**oracle.xml.async**

## **Interface DOMBuilderErrorListener**

- **All Superinterfaces:**
  **java.util.EventListener**

  <!-- -->

  **All Known Implementing Classes:**
  **[XMLDiff](../differ/XMLDiff.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DOMBuilderErrorListener
      extends java.util.EventListener

  **This interface must be implemented in order to receive notifications when error is found during parsing. The class implementing this interface must be added to the DOMBuilder using addDOMBuilderErrorListener method.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `domBuilderErrorCalled``(`[`DOMBuilderErrorEvent`](DOMBuilderErrorEvent.md)` p0)`<br>This method is called when a parse error occurs. |

<!-- -->

- - ### Method Detail

    - #### domBuilderErrorCalled

          void domBuilderErrorCalled(DOMBuilderErrorEvent p0)

      This method is called when a parse error occurs.
      Parameters:
      `p0` - The DOMBuilderErrorEvent object produced by the DOMBuilder as result of parsing error

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

- **[Prev Class](DOMBuilderErrorEvent.md)**
- **[Next Class](DOMBuilderEvent.md)**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
