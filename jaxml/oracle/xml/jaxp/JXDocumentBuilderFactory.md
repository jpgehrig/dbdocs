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

- **[Prev Class](JXDocumentBuilder.md)**
- **[Next Class](JXSAXParser.md)**

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

**oracle.xml.jaxp**

## **Class JXDocumentBuilderFactory**

- **java.lang.Object**

- - **[javax.xml.parsers.DocumentBuilderFactory](../../../javax/xml/parsers/DocumentBuilderFactory.md)**

  - - **oracle.xml.jaxp.JXDocumentBuilderFactory**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class JXDocumentBuilderFactory
      extends DocumentBuilderFactory

  **Defines a factory API that enables applications to obtain a parser that produces DOM object trees from XML documents. Reference: http://java.sun.com/j2se/1.5.0/docs/api/javax/xml/parsers/package-summary.html**
  **Since:**
  **JAXP 1.0**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                    |
    |---------------------------|--------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `BASE_URL`<br>Base URL used in parsing entities.                                                                         |
    | `static java.lang.String` | `DEBUG_MODE`<br>Sets Debug Mode - Boolean.TRUE or Boolean.FALSE                                                          |
    | `static java.lang.String` | `DTD_OBJECT`<br>DTD Object to be used for validation.                                                                    |
    | `static java.lang.String` | `ERROR_ENCODING`<br>Encoding for errors report via error stream (only if ERROR_STREAM is set)                            |
    | `static java.lang.String` | `ERROR_STREAM`<br>Error stream for reporting errors.                                                                     |
    | `static java.lang.String` | `NODE_FACTORY`<br>Set NodeFactory to build custom Nodes                                                                  |
    | `static java.lang.String` | `SCHEMA_LANGUAGE`<br>Schema language attribute for validation.                                                           |
    | `static java.lang.String` | `SCHEMA_OBJECT`<br>Schema Object to be used for validation.                                                              |
    | `static java.lang.String` | `SCHEMA_SOURCE`<br>Schema source attribute for validation.                                                               |
    | `static java.lang.String` | `SHOW_WARNINGS`<br>Boolean to ignore warnings - Boolean.TRUE or Boolean.FALSE                                            |
    | `static java.lang.String` | `USE_DTD_ONLY_FOR_VALIDATION`<br>If true, DTD Object is used only for validation and is not added to the parser document |
    | `static java.lang.String` | `XSDRECNS`<br>XMLSchema attribute value for validation.                                                                  |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                           |
    |-------------------------------------------------------|
    | `JXDocumentBuilderFactory``()`<br>Default Constructor |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                  | Method and Description                                                                                                                          |
    |--------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                                 | `getAttribute``(java.lang.String name)`<br>Allows the user to retrieve specific attributes on the underlying implementation.                    |
    | `boolean`                                                          | `getFeature``(java.lang.String name)`                                                                                                           |
    | `javax.xml.validation.Schema`                                      | `getSchema``()`                                                                                                                                 |
    | `boolean`                                                          | `isIgnoreElementContentWhitespace``()`                                                                                                          |
    | [`DocumentBuilder`](../../../javax/xml/parsers/DocumentBuilder.md) | `newDocumentBuilder``()`<br>Creates a new instance of a DocumentBuilder using the currently configured parameters.                              |
    | `void`                                                             | `setAttribute``(java.lang.String name, java.lang.Object value)`<br>Allows the user to set specific attributes on the underlying implementation. |
    | `void`                                                             | `setFeature``(java.lang.String name, boolean value)`                                                                                            |
    | `void`                                                             | `setIgnoreElementContentWhitespace``(boolean whitespace)`                                                                                       |
    | `void`                                                             | `setSchema``(javax.xml.validation.Schema schema)`                                                                                               |

    - ### Methods inherited from class javax.xml.parsers.[DocumentBuilderFactory](../../../javax/xml/parsers/DocumentBuilderFactory.md)

      [`isCoalescing`](../../../javax/xml/parsers/DocumentBuilderFactory.md)`, `[`isExpandEntityReferences`](../../../javax/xml/parsers/DocumentBuilderFactory.md)`, `[`isIgnoringComments`](../../../javax/xml/parsers/DocumentBuilderFactory.md)`, `[`isIgnoringElementContentWhitespace`](../../../javax/xml/parsers/DocumentBuilderFactory.md)`, `[`isNamespaceAware`](../../../javax/xml/parsers/DocumentBuilderFactory.md)`, `[`isValidating`](../../../javax/xml/parsers/DocumentBuilderFactory.md)`, `[`newInstance`](../../../javax/xml/parsers/DocumentBuilderFactory.md)`, `[`setCoalescing`](../../../javax/xml/parsers/DocumentBuilderFactory.md)`, `[`setExpandEntityReferences`](../../../javax/xml/parsers/DocumentBuilderFactory.md)`, `[`setIgnoringComments`](../../../javax/xml/parsers/DocumentBuilderFactory.md)`, `[`setIgnoringElementContentWhitespace`](../../../javax/xml/parsers/DocumentBuilderFactory.md)`, `[`setNamespaceAware`](../../../javax/xml/parsers/DocumentBuilderFactory.md)`, `[`setValidating`](../../../javax/xml/parsers/DocumentBuilderFactory.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ERROR_STREAM

          public static final java.lang.String ERROR_STREAM

      Error stream for reporting errors. The object can be OutputStream or PrintWriter. This attribute is ignored if ErrorHandler is set.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ERROR_ENCODING

          public static final java.lang.String ERROR_ENCODING

      Encoding for errors report via error stream (only if ERROR_STREAM is set)
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SHOW_WARNINGS

          public static final java.lang.String SHOW_WARNINGS

      Boolean to ignore warnings - Boolean.TRUE or Boolean.FALSE
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DEBUG_MODE

          public static final java.lang.String DEBUG_MODE

      Sets Debug Mode - Boolean.TRUE or Boolean.FALSE
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NODE_FACTORY

          public static final java.lang.String NODE_FACTORY

      Set NodeFactory to build custom Nodes
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DTD_OBJECT

          public static final java.lang.String DTD_OBJECT

      DTD Object to be used for validation.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### USE_DTD_ONLY_FOR_VALIDATION

          public static final java.lang.String USE_DTD_ONLY_FOR_VALIDATION

      If true, DTD Object is used only for validation and is not added to the parser document
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SCHEMA_OBJECT

          public static final java.lang.String SCHEMA_OBJECT

      Schema Object to be used for validation.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### BASE_URL

          public static final java.lang.String BASE_URL

      Base URL used in parsing entities.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SCHEMA_LANGUAGE

          public static final java.lang.String SCHEMA_LANGUAGE

      Schema language attribute for validation.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SCHEMA_SOURCE

          public static final java.lang.String SCHEMA_SOURCE

      Schema source attribute for validation.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XSDRECNS

          public static final java.lang.String XSDRECNS

      XMLSchema attribute value for validation.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### JXDocumentBuilderFactory

          public JXDocumentBuilderFactory()

      Default Constructor

  <!-- -->

  - ### Method Detail

    - #### newDocumentBuilder

          public DocumentBuilder newDocumentBuilder()
                                             throws ParserConfigurationException

      Creates a new instance of a DocumentBuilder using the currently configured parameters.
      Specified by:
      [`newDocumentBuilder`](../../../javax/xml/parsers/DocumentBuilderFactory.md) in class [`DocumentBuilderFactory`](../../../javax/xml/parsers/DocumentBuilderFactory.md)

      Throws:
      [`ParserConfigurationException`](../../../javax/xml/parsers/ParserConfigurationException.md) - if a DocumentBuilder cannot be created which satisfies the configuration requested

    <!-- -->

    - #### isIgnoreElementContentWhitespace

          public boolean isIgnoreElementContentWhitespace()

    <!-- -->

    - #### setIgnoreElementContentWhitespace

          public void setIgnoreElementContentWhitespace(boolean whitespace)

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String name,
                                   java.lang.Object value)
                            throws java.lang.IllegalArgumentException

      Allows the user to set specific attributes on the underlying implementation.
      Specified by:
      [`setAttribute`](../../../javax/xml/parsers/DocumentBuilderFactory.md) in class [`DocumentBuilderFactory`](../../../javax/xml/parsers/DocumentBuilderFactory.md)

      Parameters:
      `name` - The name of the attribute.

      `value` - The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

    <!-- -->

    - #### getAttribute

          public java.lang.Object getAttribute(java.lang.String name)
                                        throws java.lang.IllegalArgumentException

      Allows the user to retrieve specific attributes on the underlying implementation.
      Specified by:
      [`getAttribute`](../../../javax/xml/parsers/DocumentBuilderFactory.md) in class [`DocumentBuilderFactory`](../../../javax/xml/parsers/DocumentBuilderFactory.md)

      Parameters:
      `name` - The name of the attribute.

      Returns:
      value The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

    <!-- -->

    - #### setFeature

          public void setFeature(java.lang.String name,
                                 boolean value)
                          throws ParserConfigurationException

      Throws:
      [`ParserConfigurationException`](../../../javax/xml/parsers/ParserConfigurationException.md)

    <!-- -->

    - #### getFeature

          public boolean getFeature(java.lang.String name)
                             throws ParserConfigurationException

      Throws:
      [`ParserConfigurationException`](../../../javax/xml/parsers/ParserConfigurationException.md)

    <!-- -->

    - #### setSchema

          public void setSchema(javax.xml.validation.Schema schema)

    <!-- -->

    - #### getSchema

          public javax.xml.validation.Schema getSchema()

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

- **[Prev Class](JXDocumentBuilder.md)**
- **[Next Class](JXSAXParser.md)**

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
