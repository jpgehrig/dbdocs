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

- **[Prev Class](XSQLActionHandler.md)**
- **[Next Class](XSQLCommandLine.md)**

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

## **Class XSQLActionHandlerImpl**

- **java.lang.Object**

- - **oracle.xml.xsql.XSQLActionHandlerImpl**

<!-- -->

- **All Implemented Interfaces:**
  **[XSQLActionHandler](XSQLActionHandler.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class XSQLActionHandlerImpl
      extends java.lang.Object
      implements XSQLActionHandler

  **Base Implementation of XSQLActionHandler that can be extended to create your own custom handlers.**
  **Includes a set of useful helper methods.**

  **NOTE: If you extend this class and override the init() method, make sure to call:**

      super.init(env,e);

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description  |
    |------------------------------|
    | `XSQLActionHandlerImpl``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                     |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `init``(`[`XSQLPageRequest`](XSQLPageRequest.md)` env, `[`Element`](../../../org/w3c/dom/Element.md)` e)`<br>Initialize the Action Handler |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.xml.xsql.[XSQLActionHandler](XSQLActionHandler.md)

      [`handleAction`](XSQLActionHandler.md)

<!-- -->

- - ### Constructor Detail

    - #### XSQLActionHandlerImpl

          public XSQLActionHandlerImpl()

  <!-- -->

  - ### Method Detail

    - #### init

          public void init(XSQLPageRequest env,
                           Element e)

      Description copied from interface: [`XSQLActionHandler`](XSQLActionHandler.md)
      Initialize the Action Handler
      Specified by:
      [`init`](XSQLActionHandler.md) in interface [`XSQLActionHandler`](XSQLActionHandler.md)

      Parameters:
      `env` - XSQLPageRequest object

      `e` - DOM element representing the Action Element being handled

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

- **[Prev Class](XSQLActionHandler.md)**
- **[Next Class](XSQLCommandLine.md)**

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
