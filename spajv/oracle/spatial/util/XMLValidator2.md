Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](XMLValidator.md)
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.util

## Class XMLValidator2

- java.lang.Object

- - oracle.spatial.util.XMLValidator2

<!-- -->

-

  ------------------------------------------------------------------------



      public class XMLValidator2
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                  |
    |----------------------------------------------|
    | `XMLValidator2``(java.sql.Connection conn)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                       |
    |--------------------|--------------------------------------------------------------|
    | `java.lang.String` | `getErrors``()`<br>Returns errors.                           |
    | `int`              | `isSchemaValid``(CLOB xml, java.lang.String schema)`         |
    | `int`              | `isSchemaValid``(OracleClob xml, java.lang.String schema)`   |
    | `void`             | `schemaValidate``(CLOB xml, java.lang.String schema)`        |
    | `void`             | `schemaValidate``(OracleClob xml, java.lang.String schema)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XMLValidator2

          public XMLValidator2(java.sql.Connection conn)

  <!-- -->

  - ### Method Detail

    - #### getErrors

          public java.lang.String getErrors()

      Returns errors.
      Returns:
      String

    <!-- -->

    - #### isSchemaValid

          public int isSchemaValid(CLOB xml,
                                   java.lang.String schema)

      Parameters:
      `xml` - The CLOB object for the XML to be validated.

      `schema` - The URL for the XSD to be validated.

      Returns:
      1 if valid; else 0.

    <!-- -->

    - #### isSchemaValid

          public int isSchemaValid(OracleClob xml,
                                   java.lang.String schema)

      Parameters:
      `xml` - The CLOB object for the XML to be validated.

      `schema` - The URL for the XSD to be validated.

      Returns:
      1 if valid; else 0.

    <!-- -->

    - #### schemaValidate

          public void schemaValidate(CLOB xml,
                                     java.lang.String schema)
                              throws XMLParseException,
                                     org.xml.sax.SAXException,
                                     java.io.IOException,
                                     XSDException,
                                     java.sql.SQLException,
                                     java.lang.Exception

      Parameters:
      `xml` - The CLOB object for the XML to be validated.

      `schema` - The URL for the XSD to be validated.

      Throws:
      `XMLParseException`

      `org.xml.sax.SAXException`

      `java.io.IOException`

      `XSDException`

      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### schemaValidate

          public void schemaValidate(OracleClob xml,
                                     java.lang.String schema)
                              throws XMLParseException,
                                     org.xml.sax.SAXException,
                                     java.io.IOException,
                                     XSDException,
                                     java.sql.SQLException,
                                     java.lang.Exception

      Parameters:
      `xml` - The OracleClob object for the XML to be validated.

      `schema` - The URL for the XSD to be validated.

      Throws:
      `XMLParseException`

      `org.xml.sax.SAXException`

      `java.io.IOException`

      `XSDException`

      `java.sql.SQLException`

      `java.lang.Exception`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](XMLValidator.md)
- Next Class

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
