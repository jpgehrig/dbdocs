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

- **[Prev Class](XSQLDiagnostic.md)**
- **[Next Class](XSQLError.md)**

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

## **Interface XSQLDocumentSerializer**

-

  ------------------------------------------------------------------------

  **
  **

      public interface XSQLDocumentSerializer

  **Interface that must be implemented by all XSQL Serializers which serialize an XSQL data page as an XML Document to a PrintWriter.**
  **Upon encountering a serializer="XXX" pseudo-attribute in an \<?xml-stylesheet?\> processing instruction, the XSQL Page Processor invokes the associated serializer by:**

  1.  **Constructing an instance of the serializer using the no-args constructor**
  2.  **Invoking the XSQL document serializer's serialize() method**

  **NOTE: An implementation of XSQLDocumentSerializer is expected to do the following actions.**
  1.  First, call env.setContentType() to set the content type
  2.  Then, call env.getWriter() to get the Writer to write to

  If the serializer throws an unhandled exception, the XSQL Page Processor will format the stacktrace.
  See oracle.xml.xsql.src.serializers.XSQLSampleSerializer for an example.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                              |
    |-------------------|---------------------------------------------------------------------------------------------------------------------|
    | `void`            | `serialize``(`[`Document`](../../../org/w3c/dom/Document.md)` doc, `[`XSQLPageRequest`](XSQLPageRequest.md)` env)`  |

<!-- -->

- - ### Method Detail

    - #### serialize

          void serialize(Document doc,
                         XSQLPageRequest env)
                  throws java.lang.Throwable

      Throws:
      `java.lang.Throwable`

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

- **[Prev Class](XSQLDiagnostic.md)**
- **[Next Class](XSQLError.md)**

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
