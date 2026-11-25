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

- **[Prev Class](BinXMLProcessorFactory.md)**
- **[Next Class](BinXMLStream.md)**

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

**oracle.xml.binxml**

## **Class BinXMLSerializer**

- **java.lang.Object**

- - **oracle.xml.binxml.BinXMLSerializer**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class BinXMLSerializer
      extends java.lang.Object

  **The BinXMLSerializer class provides pull style serialization**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                    |
    |---------------------------|------------------------------------------|
    | `static java.lang.String` | `ENCODING`<br>Output encoding property   |
    | `static java.lang.String` | `INDENT`<br>Output Indenting             |
    | `static java.lang.String` | `OMIT_XML_DECL`<br>Print XML Declaration |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                               |
    |-----------------------|------------------------------------------------------------------------------------------------------|
    | `java.io.InputStream` | `getInputStream``()`<br>Get inputStream from serializer                                              |
    | `java.io.Reader`      | `getReader``()`<br>Get reader from serializer                                                        |
    | `void`                | `setProperty``(java.lang.String property, java.lang.Object value)`<br>Set output printing properties |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ENCODING

          public static final java.lang.String ENCODING

      Output encoding property
      See Also:
      `setProperty(java.lang.String, java.lang.Object)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### INDENT

          public static final java.lang.String INDENT

      Output Indenting
      See Also:
      `setProperty(java.lang.String, java.lang.Object)`, [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### OMIT_XML_DECL

          public static final java.lang.String OMIT_XML_DECL

      Print XML Declaration
      See Also:
      `setProperty(java.lang.String, java.lang.Object)`, [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getInputStream

          public java.io.InputStream getInputStream()
                                             throws java.io.IOException,
                                                    BinXMLException

      Get inputStream from serializer
      Returns:
      InputStream

      Throws:
      `java.io.IOException`

      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### getReader

          public java.io.Reader getReader()
                                   throws java.io.IOException,
                                          BinXMLException

      Get reader from serializer
      Returns:
      Reader

      Throws:
      `java.io.IOException`

      [`BinXMLException`](BinXMLException.md)

    <!-- -->

    - #### setProperty

          public void setProperty(java.lang.String property,
                                  java.lang.Object value)

      Set output printing properties
      Parameters:
      `property` -

      `value` - of the property

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

- **[Prev Class](BinXMLProcessorFactory.md)**
- **[Next Class](BinXMLStream.md)**

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
