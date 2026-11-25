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

- **[Prev Class](XDBEvent.md)**
- **[Next Class](XDBHandlerList.md)**

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

**oracle.xdb.event**

## **Class XDBHandler**

- **java.lang.Object**

- - **oracle.xdb.event.XDBHandler**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XDBHandler
      extends java.lang.Object

  **This class stores information about handlers defined in resource configuration.**
  **Since:**
  **11.1.0.0.0**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                            |
    |--------------------|-------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getLanguage``()`<br>Returns the implementation language of the handler (JAVA or PL/SQL)                          |
    | `java.lang.String` | `getSchema``()`<br>Returns the schema containing the handler's source.                                            |
    | `java.lang.String` | `getSource``()`<br>Returns the name of the Java class, PL/SQL package or object type that implements the handler. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getSource

          public java.lang.String getSource()

      Returns the name of the Java class, PL/SQL package or object type that implements the handler.
      Returns:
      The name of the source

    <!-- -->

    - #### getSchema

          public java.lang.String getSchema()

      Returns the schema containing the handler's source.
      Returns:
      The name of the schema

    <!-- -->

    - #### getLanguage

          public java.lang.String getLanguage()

      Returns the implementation language of the handler (JAVA or PL/SQL)
      Returns:
      The name of the implementation language.

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

- **[Prev Class](XDBEvent.md)**
- **[Next Class](XDBHandlerList.md)**

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
