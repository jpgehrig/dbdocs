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

- **Prev Class**
- **[Next Class](XSQLActionHandlerImpl.md)**

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

**oracle.xml.xsql**

## **Interface XSQLActionHandler**

- **All Known Implementing Classes:**
  **[XSQLActionHandlerImpl](XSQLActionHandlerImpl.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XSQLActionHandler

  **Interface that must be implemented by all XSQL Action Element Handlers**
  **Upon encountering an XSQL Action Element of the form \<xsql:xxxx\> in an XSQL page, the XSQL Page Processor invokes the associated XSQL Action Handler by:**

  1.  **Constructing an instance of the handler using the no-args constructor**
  2.  **Invoking the XSQL Action Handler's init() method**
  3.  **Invoking the XSQL Action Handler's handleAction() method**

  **NOTE: conn parameter can be null if no connection specified for the XSQL page being processed.**

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                        |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `handleAction``(`[`Node`](../../../org/w3c/dom/Node.md)` rootNode)`<br>Handle the action, typically by executing some code and appending new child DOM nodes to the rootNode. |
    | `void`            | `init``(`[`XSQLPageRequest`](XSQLPageRequest.md)` env, `[`Element`](../../../org/w3c/dom/Element.md)` e)`<br>Initialize the Action Handler                                    |

<!-- -->

- - ### Method Detail

    - #### init

          void init(XSQLPageRequest env,
                    Element e)

      Initialize the Action Handler
      Parameters:
      `env` - XSQLPageRequest object

      `e` - DOM element representing the Action Element being handled

    <!-- -->

    - #### handleAction

          void handleAction(Node rootNode)
                     throws java.sql.SQLException

      Handle the action, typically by executing some code and appending new child DOM nodes to the rootNode.
      The XSQL Page Processor replaces the action element in the XSQL Page being processed with the document fragment of nodes that your handleAction method appends to the rootNode.

      Parameters:
      `rootNode` - Root node of generated document fragment

      Throws:
      `java.sql.SQLException`

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

- **Prev Class**
- **[Next Class](XSQLActionHandlerImpl.md)**

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
