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

- **[Prev Class](XSQLErrorHandler.md)**
- **[Next Class](XSQLHttpUtil.md)**

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

## **Class XSQLErrorWriter**

- **java.lang.Object**

- - **oracle.xml.xsql.XSQLErrorWriter**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public final class XSQLErrorWriter
      extends java.lang.Object

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                                                                                       |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `XSQLErrorWriter``(`[`SAXParseException`](../../../org/xml/sax/SAXParseException.md)` s, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`                                          |
    | `XSQLErrorWriter``(java.lang.String x, `[`SAXParseException`](../../../org/xml/sax/SAXParseException.md)` s, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`                      |
    | `XSQLErrorWriter``(java.lang.String x, java.lang.String y, `[`SAXParseException`](../../../org/xml/sax/SAXParseException.md)` s, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`  |
    | `XSQLErrorWriter``(java.lang.String x, java.lang.String y, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`                                                                        |
    | `XSQLErrorWriter``(java.lang.String s, java.lang.Throwable e, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`                                                                     |
    | `XSQLErrorWriter``(java.lang.String s, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`                                                                                            |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                    |
    |---------------------------|---------------------------------------------------------------------------|
    | `static java.lang.String` | `getXSQLVersionMessage``(`[`XSQLPageRequest`](XSQLPageRequest.md)` env)`  |
    | `void`                    | `print``()`                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSQLErrorWriter

          public XSQLErrorWriter(java.lang.String s,
                                 java.lang.Throwable e,
                                 XSQLPageRequest env)

    <!-- -->

    - #### XSQLErrorWriter

          public XSQLErrorWriter(java.lang.String s,
                                 XSQLPageRequest env)

    <!-- -->

    - #### XSQLErrorWriter

          public XSQLErrorWriter(java.lang.String x,
                                 java.lang.String y,
                                 XSQLPageRequest env)

    <!-- -->

    - #### XSQLErrorWriter

          public XSQLErrorWriter(java.lang.String x,
                                 java.lang.String y,
                                 SAXParseException s,
                                 XSQLPageRequest env)

    <!-- -->

    - #### XSQLErrorWriter

          public XSQLErrorWriter(java.lang.String x,
                                 SAXParseException s,
                                 XSQLPageRequest env)

    <!-- -->

    - #### XSQLErrorWriter

          public XSQLErrorWriter(SAXParseException s,
                                 XSQLPageRequest env)

  <!-- -->

  - ### Method Detail

    - #### print

          public void print()

    <!-- -->

    - #### getXSQLVersionMessage

          public static java.lang.String getXSQLVersionMessage(XSQLPageRequest env)

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

- **[Prev Class](XSQLErrorHandler.md)**
- **[Next Class](XSQLHttpUtil.md)**

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
