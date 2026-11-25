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

- **[Prev Class](XSLTransformerErrorEvent.md)**
- **[Next Class](XSLTransformerEvent.md)**

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

## **Interface XSLTransformerErrorListener**

- **All Superinterfaces:**
  **java.util.EventListener**

  ------------------------------------------------------------------------

  **
  **

      public interface XSLTransformerErrorListener
      extends java.util.EventListener

  **This interface must be implemented in order to receive notifications about error events during the asynchronous transformation. The class implementing this interface must be added to the XSLTransformer using addXSLTransformerListener method.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                            |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `xslTransformerErrorCalled``(`[`XSLTransformerErrorEvent`](XSLTransformerErrorEvent.md)` p0)`<br>This method is called when parse or transformation error occurs. |

<!-- -->

- - ### Method Detail

    - #### xslTransformerErrorCalled

          void xslTransformerErrorCalled(XSLTransformerErrorEvent p0)

      This method is called when parse or transformation error occurs.
      Parameters:
      `p0` - - The XSLTransformerErrorEvent object produced by the XSLTransformer

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

- **[Prev Class](XSLTransformerErrorEvent.md)**
- **[Next Class](XSLTransformerEvent.md)**

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
