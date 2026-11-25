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

- **[Prev Class](XSLStylesheet.md)**
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

**oracle.xml.parser.v2**

## **Class XSLTContext**

- **java.lang.Object**

- - **oracle.xml.parser.v2.XSLTContext**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XSLTContext
      extends java.lang.Object

  **Class for Xpath processing Context**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                                                                |
    |---------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | [`XMLNode`](XMLNode.md)   | `getContextNode``()`<br>Get the current context node                                                                  |
    | `int`                     | `getContextPosition``()`<br>Get the current context node position                                                     |
    | `int`                     | `getContextSize``()`<br>Get the current context size                                                                  |
    | [`XMLError`](XMLError.md) | `getError``()`<br>Get the XMLError instance for reporting errors                                                      |
    | `void`                    | `reportCharacters``(java.lang.String data, boolean disableoutesc)`<br>Report characters to the current output handler |
    | `void`                    | `reportNode``(`[`XMLNode`](XMLNode.md)` node)`<br>Report a XMLNode to the current output handler                      |
    | `void`                    | `setError``(`[`XMLError`](XMLError.md)` err)`<br>Set the XMLError                                                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getContextNode

          public XMLNode getContextNode()
                                 throws XSLException

      Get the current context node
      Returns:
      XMLNode - current context node

      Throws:
      [`XSLException`](XSLException.md)

    <!-- -->

    - #### getContextSize

          public int getContextSize()
                             throws XSLException

      Get the current context size
      Returns:
      int - current context size

      Throws:
      [`XSLException`](XSLException.md)

    <!-- -->

    - #### getContextPosition

          public int getContextPosition()
                                 throws XSLException

      Get the current context node position
      Returns:
      int - current context node position

      Throws:
      [`XSLException`](XSLException.md)

    <!-- -->

    - #### reportCharacters

          public void reportCharacters(java.lang.String data,
                                       boolean disableoutesc)
                                throws XSLException

      Report characters to the current output handler
      Parameters:
      `data` - - String to be printed

      `disableoutesc` - - boolean to disable output escaping

      Throws:
      [`XSLException`](XSLException.md)

    <!-- -->

    - #### reportNode

          public void reportNode(XMLNode node)
                          throws XSLException

      Report a XMLNode to the current output handler
      Parameters:
      `node` - - node to be outptu

      Throws:
      [`XSLException`](XSLException.md)

    <!-- -->

    - #### getError

          public XMLError getError()

      Get the XMLError instance for reporting errors
      Returns:
      XMLError

    <!-- -->

    - #### setError

          public void setError(XMLError err)

      Set the XMLError
      Parameters:
      `err` - - instance of XMLError

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

- **[Prev Class](XSLStylesheet.md)**
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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
