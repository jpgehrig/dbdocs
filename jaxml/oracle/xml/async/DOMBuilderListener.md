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

- **[Prev Class](DOMBuilderEvent.md)**
- **[Next Class](ResourceManager.md)**

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

## **Interface DOMBuilderListener**

- **All Superinterfaces:**
  **java.util.EventListener**

  <!-- -->

  **All Known Implementing Classes:**
  **[XMLDiff](../differ/XMLDiff.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DOMBuilderListener
      extends java.util.EventListener

  **This interface must be implemented in order to receive notifications about events during the asyncronous parsing. The class implementing this interface must be added to the DOMBuilder using addDOMBuilderListener method.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                               |
    |-------------------|----------------------------------------------------------------------------------------------------------------------|
    | `void`            | `domBuilderError``(`[`DOMBuilderEvent`](DOMBuilderEvent.md)` p0)`<br>This method is called when parse error occur.   |
    | `void`            | `domBuilderOver``(`[`DOMBuilderEvent`](DOMBuilderEvent.md)` p0)`<br>This method is called when the parse is complete |
    | `void`            | `domBuilderStarted``(`[`DOMBuilderEvent`](DOMBuilderEvent.md)` p0)`<br>This method is called when parse starts       |

<!-- -->

- - ### Method Detail

    - #### domBuilderError

          void domBuilderError(DOMBuilderEvent p0)

      This method is called when parse error occur.
      Parameters:
      `p0` - - The DOMBuilderEvent object produced by the DOMBuilder

    <!-- -->

    - #### domBuilderOver

          void domBuilderOver(DOMBuilderEvent p0)

      This method is called when the parse is complete
      Parameters:
      `p0` - - The DOMBuilderEvent object produced by the DOMBuilder

    <!-- -->

    - #### domBuilderStarted

          void domBuilderStarted(DOMBuilderEvent p0)

      This method is called when parse starts
      Parameters:
      `p0` - - The DOMBuilderEvent object produced by the DOMBuilder

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

- **[Prev Class](DOMBuilderEvent.md)**
- **[Next Class](ResourceManager.md)**

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
