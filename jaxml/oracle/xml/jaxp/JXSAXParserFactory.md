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

- **[Prev Class](JXSAXParser.md)**
- **[Next Class](JXSAXTransformerFactory.md)**

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

## **Class JXSAXParserFactory**

- **java.lang.Object**

- - **[javax.xml.parsers.SAXParserFactory](../../../javax/xml/parsers/SAXParserFactory.md)**

  - - **oracle.xml.jaxp.JXSAXParserFactory**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class JXSAXParserFactory
      extends SAXParserFactory

  **Defines a factory API that enables applications to configure and obtain a SAX-based parser to parse XML documents. Reference: http://java.sun.com/j2se/1.5.0/docs/api/javax/xml/parsers/package-summary.html**
  **Since:**
  **JAXP 1.0**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                     |
    |-------------------------------------------------|
    | `JXSAXParserFactory``()`<br>Default Constructor |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                                                                                                            |
    |--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                              | `getFeature``(java.lang.String name)`<br>returns the particular property requested for in the underlying implementation of org.xml.sax.XMLReader. |
    | [`SAXParser`](../../../javax/xml/parsers/SAXParser.md) | `newSAXParser``()`<br>Creates a new instance of a SAXParser using the currently configured factory parameters.                                    |
    | `void`                                                 | `setFeature``(java.lang.String name, boolean value)`<br>Sets the particular feature in the underlying implementation of org.xml.sax.XMLReader.    |

    - ### Methods inherited from class javax.xml.parsers.[SAXParserFactory](../../../javax/xml/parsers/SAXParserFactory.md)

      [`isNamespaceAware`](../../../javax/xml/parsers/SAXParserFactory.md)`, `[`isValidating`](../../../javax/xml/parsers/SAXParserFactory.md)`, `[`newInstance`](../../../javax/xml/parsers/SAXParserFactory.md)`, `[`setNamespaceAware`](../../../javax/xml/parsers/SAXParserFactory.md)`, `[`setValidating`](../../../javax/xml/parsers/SAXParserFactory.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### JXSAXParserFactory

          public JXSAXParserFactory()

      Default Constructor

  <!-- -->

  - ### Method Detail

    - #### newSAXParser

          public SAXParser newSAXParser()
                                 throws ParserConfigurationException,
                                        SAXException

      Creates a new instance of a SAXParser using the currently configured factory parameters.
      Specified by:
      [`newSAXParser`](../../../javax/xml/parsers/SAXParserFactory.md) in class [`SAXParserFactory`](../../../javax/xml/parsers/SAXParserFactory.md)

      Throws:
      [`ParserConfigurationException`](../../../javax/xml/parsers/ParserConfigurationException.md) - if a parser cannot be created which satisfies the requested configuration.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### setFeature

          public void setFeature(java.lang.String name,
                                 boolean value)
                          throws ParserConfigurationException,
                                 SAXNotRecognizedException,
                                 SAXNotSupportedException

      Sets the particular feature in the underlying implementation of org.xml.sax.XMLReader.
      Specified by:
      [`setFeature`](../../../javax/xml/parsers/SAXParserFactory.md) in class [`SAXParserFactory`](../../../javax/xml/parsers/SAXParserFactory.md)

      Parameters:
      `name` - The name of the feature to be set.

      `value` - The value of the feature to be set.

      Throws:
      `java.lang.NullPointerException` - If the "name" parameter is null.

      [`SAXNotRecognizedException`](../../../org/xml/sax/SAXNotRecognizedException.md) - When the underlying XMLReader does not recognize the property name.

      [`SAXNotSupportedException`](../../../org/xml/sax/SAXNotSupportedException.md) - When the underlying XMLReader recognizes the property name but doesn't support the property.

      [`ParserConfigurationException`](../../../javax/xml/parsers/ParserConfigurationException.md) - If a parser cannot be created which satisfies the requested configuration.

      See Also:
      [`XMLReader.setFeature(java.lang.String, boolean)`](../../../org/xml/sax/XMLReader.md)

    <!-- -->

    - #### getFeature

          public boolean getFeature(java.lang.String name)
                             throws ParserConfigurationException,
                                    SAXNotRecognizedException,
                                    SAXNotSupportedException

      returns the particular property requested for in the underlying implementation of org.xml.sax.XMLReader.
      Specified by:
      [`getFeature`](../../../javax/xml/parsers/SAXParserFactory.md) in class [`SAXParserFactory`](../../../javax/xml/parsers/SAXParserFactory.md)

      Parameters:
      `name` - The name of the property to be retrieved. \#

      Returns:
      Value of the requested property.

      Throws:
      `java.lang.NullPointerException` - If the "name" parameter is null.

      [`SAXNotRecognizedException`](../../../org/xml/sax/SAXNotRecognizedException.md) - When the underlying XMLReader does not recognize the property name.

      [`SAXNotSupportedException`](../../../org/xml/sax/SAXNotSupportedException.md) - When the underlying XMLReader recognizes the property name but doesn't support the property.

      [`ParserConfigurationException`](../../../javax/xml/parsers/ParserConfigurationException.md) - If a parser cannot be created which satisfies the requested configuration.

      See Also:
      [`XMLReader.getProperty(java.lang.String)`](../../../org/xml/sax/XMLReader.md)

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

- **[Prev Class](JXSAXParser.md)**
- **[Next Class](JXSAXTransformerFactory.md)**

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
