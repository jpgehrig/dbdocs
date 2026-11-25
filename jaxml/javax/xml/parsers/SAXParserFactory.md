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

- **[Prev Class](SAXParser.md)**
- **Next Class**

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

**javax.xml.parsers**

## **Class SAXParserFactory**

- **java.lang.Object**

- - **javax.xml.parsers.SAXParserFactory**

<!-- -->

- **Direct Known Subclasses:**
  **[JXSAXParserFactory](../../../oracle/xml/jaxp/JXSAXParserFactory.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class SAXParserFactory
      extends java.lang.Object

  **Defines a factory API that enables applications to configure and obtain a SAX based parser to parse XML documents.**
  **Since:**
  **JAXP 1.0**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                      | Method and Description                                                                                                                            |
    |----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract boolean`                     | `getFeature``(java.lang.String name)`<br>returns the particular property requested for in the underlying implementation of org.xml.sax.XMLReader. |
    | `boolean`                              | `isNamespaceAware``()`<br>Indicates whether or not the factory is configured to produce parsers which are namespace aware.                        |
    | `boolean`                              | `isValidating``()`<br>Indicates whether or not the factory is configured to produce parsers which validate the XML content during parse.          |
    | `static SAXParserFactory`              | `newInstance``()`<br>Obtain a new instance of a `SAXParserFactory`.                                                                               |
    | `abstract `[`SAXParser`](SAXParser.md) | `newSAXParser``()`<br>Creates a new instance of a SAXParser using the currently configured factory parameters.                                    |
    | `abstract void`                        | `setFeature``(java.lang.String name, boolean value)`<br>Sets the particular feature in the underlying implementation of org.xml.sax.XMLReader.    |
    | `void`                                 | `setNamespaceAware``(boolean awareness)`<br>Specifies that the parser produced by this code will provide support for XML namespaces.              |
    | `void`                                 | `setValidating``(boolean validating)`<br>Specifies that the parser produced by this code will validate documents as they are parsed.              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### newInstance

          public static SAXParserFactory newInstance()

      Obtain a new instance of a `SAXParserFactory`. This static method creates a new factory instance This method uses the following ordered lookup procedure to determine the `SAXParserFactory` implementation class to load:
      - Use the `javax.xml.parsers.SAXParserFactory` system property.
      - Use the JAVA_HOME(the parent directory where jdk is installed)/lib/jaxp.properties for a property file that contains the name of the implementation class keyed on the same value as the system property defined above.
      - Use the Services API (as detailed in teh JAR specification), if available, to determine the classname. The Services API will look for a classname in the file `META-INF/services/javax.xml.parsers.SAXParserFactory` in jars available to the runtime.
      - Platform default `SAXParserFactory` instance.

      Once an application has obtained a reference to a `SAXParserFactory` it can use the factory to configure and obtain parser instances.
      Throws:
      [`FactoryConfigurationError`](FactoryConfigurationError.md) - if the implementation is not available or cannot be instantiated.

    <!-- -->

    - #### newSAXParser

          public abstract SAXParser newSAXParser()
                                          throws ParserConfigurationException,
                                                 SAXException

      Creates a new instance of a SAXParser using the currently configured factory parameters.
      Throws:
      [`ParserConfigurationException`](ParserConfigurationException.md) - if a parser cannot be created which satisfies the requested configuration.

      [`SAXException`](../../../org/xml/sax/SAXException.md)

    <!-- -->

    - #### setNamespaceAware

          public void setNamespaceAware(boolean awareness)

      Specifies that the parser produced by this code will provide support for XML namespaces. By default the value of this is set to `false`

    <!-- -->

    - #### setValidating

          public void setValidating(boolean validating)

      Specifies that the parser produced by this code will validate documents as they are parsed. By default the value of this is set to `false`

    <!-- -->

    - #### isNamespaceAware

          public boolean isNamespaceAware()

      Indicates whether or not the factory is configured to produce parsers which are namespace aware.

    <!-- -->

    - #### isValidating

          public boolean isValidating()

      Indicates whether or not the factory is configured to produce parsers which validate the XML content during parse.

    <!-- -->

    - #### setFeature

          public abstract void setFeature(java.lang.String name,
                                          boolean value)
                                   throws ParserConfigurationException,
                                          SAXNotRecognizedException,
                                          SAXNotSupportedException

      Sets the particular feature in the underlying implementation of org.xml.sax.XMLReader. A list of the core features and properties can be found at <http://www.megginson.com/SAX/Java/features.html>
      Parameters:
      `name` - The name of the feature to be set.

      `value` - The value of the feature to be set.

      Throws:
      [`SAXNotRecognizedException`](../../../org/xml/sax/SAXNotRecognizedException.md) - When the underlying XMLReader does not recognize the property name.

      [`SAXNotSupportedException`](../../../org/xml/sax/SAXNotSupportedException.md) - When the underlying XMLReader recognizes the property name but doesn't support the property.

      [`ParserConfigurationException`](ParserConfigurationException.md)

      See Also:
      [`XMLReader.setFeature(java.lang.String, boolean)`](../../../org/xml/sax/XMLReader.md)

    <!-- -->

    - #### getFeature

          public abstract boolean getFeature(java.lang.String name)
                                      throws ParserConfigurationException,
                                             SAXNotRecognizedException,
                                             SAXNotSupportedException

      returns the particular property requested for in the underlying implementation of org.xml.sax.XMLReader.
      Parameters:
      `name` - The name of the property to be retrieved.

      Returns:
      Value of the requested property.

      Throws:
      [`SAXNotRecognizedException`](../../../org/xml/sax/SAXNotRecognizedException.md) - When the underlying XMLReader does not recognize the property name.

      [`SAXNotSupportedException`](../../../org/xml/sax/SAXNotSupportedException.md) - When the underlying XMLReader recognizes the property name but doesn't support the property.

      [`ParserConfigurationException`](ParserConfigurationException.md)

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

- **[Prev Class](SAXParser.md)**
- **Next Class**

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
