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

- **[Prev Class](XQStackTraceElement.md)**
- **[Next Class](XQStaticContext.md)**

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

**javax.xml.xquery**

## **Class XQStackTraceVariable**

- **java.lang.Object**

- - **javax.xml.xquery.XQStackTraceVariable**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Serializable**

  ------------------------------------------------------------------------

  **
  **

      public class XQStackTraceVariable
      extends java.lang.Object
      implements java.io.Serializable

  **This class represents the list of variables and their values in an error stack.**
  **See Also:**
  **[`XQStackTraceElement`](XQStackTraceElement.md), [`XQQueryException`](XQQueryException.md), [Serialized Form](../../../serialized-form.md)**

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                   |
    |-------------------------------------------------------------------------------------------------------------------------------|
    | `XQStackTraceVariable``(javax.xml.namespace.QName qname, java.lang.String value)`<br>Construct a stack trace variable object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                   |
    |-----------------------------|------------------------------------------------------------------------------------------|
    | `javax.xml.namespace.QName` | `getQName``()`<br>Gets the `QName` of the variable.                                      |
    | `java.lang.String`          | `getValue``()`<br>Gets a short string representation of the value of the stack variable. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XQStackTraceVariable

          public XQStackTraceVariable(javax.xml.namespace.QName qname,
                                      java.lang.String value)

      Construct a stack trace variable object.
      Parameters:
      `qname` - the `QName` of the variable in the error stack

      `value` - a vendor specific short string representation of the value of the variable in the error stack

  <!-- -->

  - ### Method Detail

    - #### getQName

          public javax.xml.namespace.QName getQName()

      Gets the `QName` of the variable.
      Returns:
      the `QName` of the variable in the stack

    <!-- -->

    - #### getValue

          public java.lang.String getValue()

      Gets a short string representation of the value of the stack variable. Representations of values are vendor specific and for XML node types may be XPath descriptions such as "doc("0596003870/book1.xml")/book/chapter\[5\]". Sequences may print just some set of values from the sequence such as '("5", "6", "7", ...)'.
      Returns:
      the `String` representation of the value of the variable. This representation is vendor specific.

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

- **[Prev Class](XQStackTraceElement.md)**
- **[Next Class](XQStaticContext.md)**

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
