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

- **[Prev Class](XSLTransformerEvent.md)**
- **Next Class**

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

## **Interface XSLTransformerListener**

- **All Superinterfaces:**
  **java.util.EventListener**

  ------------------------------------------------------------------------

  **
  **

      public interface XSLTransformerListener
      extends java.util.EventListener

  **This interface must be implemented in order to receive notifications about events during the asynchronous transformation. The class implementing this interface must be added to the XSLTransformer using addXSLTransformerListener method.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                           |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `xslTransformerError``(`[`XSLTransformerEvent`](XSLTransformerEvent.md)` p0)`<br>This method is called when parse or transformation error occur. |
    | `void`            | `xslTransformerOver``(`[`XSLTransformerEvent`](XSLTransformerEvent.md)` p0)`<br>This method is called when the transformation is complete        |
    | `void`            | `xslTransformerStarted``(`[`XSLTransformerEvent`](XSLTransformerEvent.md)` p0)`<br>This method is called when the transformation starts          |

<!-- -->

- - ### Method Detail

    - #### xslTransformerError

          void xslTransformerError(XSLTransformerEvent p0)

      This method is called when parse or transformation error occur.
      Parameters:
      `p0` - - The XSLTransformerEvent object produced by the XSLTransformer

    <!-- -->

    - #### xslTransformerOver

          void xslTransformerOver(XSLTransformerEvent p0)

      This method is called when the transformation is complete
      Parameters:
      `p0` - - The XSLTransformerEvent object produced by the XSLTransformer

    <!-- -->

    - #### xslTransformerStarted

          void xslTransformerStarted(XSLTransformerEvent p0)

      This method is called when the transformation starts
      Parameters:
      `p0` - - The XSLTransformerEvent object produced by the XSLTransformer

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

- **[Prev Class](XSLTransformerEvent.md)**
- **Next Class**

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
