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

- **[Prev Class](XSQLDocumentSerializer.md)**
- **[Next Class](XSQLErrorHandler.md)**

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

## **Class XSQLError**

- **java.lang.Object**

- - **oracle.xml.xsql.XSQLError**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class XSQLError
      extends java.lang.Object

  **Represents a fatal error in the XSQL page processing engine.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                              | Method and Description                                                                           |
    |------------------------------------------------|--------------------------------------------------------------------------------------------------|
    | `java.lang.Integer`                            | `getErrorCode``()`<br>Returns the XSQL error code                                                |
    | `java.lang.String`                             | `getErrorXML``()`<br>Returns the XSQL error information formatted as a well-formed XML fragment. |
    | [`Document`](../../../org/w3c/dom/Document.md) | `getErrorXMLDocument``()`<br>Returns the XSQL error information as a DOM Document                |
    | `java.lang.String`                             | `getMessage``()`<br>Returns the text of the XSQL error that has occurred.                        |
    | `java.lang.Object[]`                           | `getSupplementalErrorInfo``()`<br>Returns an Object array of supplemental error information.     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getMessage

          public java.lang.String getMessage()

      Returns the text of the XSQL error that has occurred.

    <!-- -->

    - #### getSupplementalErrorInfo

          public java.lang.Object[] getSupplementalErrorInfo()

      Returns an Object array of supplemental error information.

    <!-- -->

    - #### getErrorXML

          public java.lang.String getErrorXML()

      Returns the XSQL error information formatted as a well-formed XML fragment.

    <!-- -->

    - #### getErrorXMLDocument

          public Document getErrorXMLDocument()

      Returns the XSQL error information as a DOM Document

    <!-- -->

    - #### getErrorCode

          public java.lang.Integer getErrorCode()

      Returns the XSQL error code

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

- **[Prev Class](XSQLDocumentSerializer.md)**
- **[Next Class](XSQLErrorHandler.md)**

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
