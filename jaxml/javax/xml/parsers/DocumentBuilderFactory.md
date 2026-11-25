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

- **[Prev Class](DocumentBuilder.md)**
- **[Next Class](FactoryConfigurationError.md)**

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

## **Class DocumentBuilderFactory**

- **java.lang.Object**

- - **javax.xml.parsers.DocumentBuilderFactory**

<!-- -->

- **Direct Known Subclasses:**
  **[JXDocumentBuilderFactory](../../../oracle/xml/jaxp/JXDocumentBuilderFactory.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class DocumentBuilderFactory
      extends java.lang.Object

  **Defines a factory API that enables applications to obtain a parser that produces DOM object trees from XML documents.**
  **Since:**
  **JAXP 1.0**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                  | Method and Description                                                                                                                                                                                                                                            |
    |----------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract java.lang.Object`                        | `getAttribute``(java.lang.String name)`<br>Allows the user to retrieve specific attributes on the underlying implementation.                                                                                                                                      |
    | `boolean`                                          | `isCoalescing``()`<br>Indicates whether or not the factory is configured to produce parsers which converts CDATA nodes to Text nodes and appends it to the adjacent (if any) Text node.                                                                           |
    | `boolean`                                          | `isExpandEntityReferences``()`<br>Indicates whether or not the factory is configured to produce parsers which expand entity reference nodes.                                                                                                                      |
    | `boolean`                                          | `isIgnoringComments``()`<br>Indicates whether or not the factory is configured to produce parsers which ignores comments.                                                                                                                                         |
    | `boolean`                                          | `isIgnoringElementContentWhitespace``()`<br>Indicates whether or not the factory is configured to produce parsers which ignore ignorable whitespace in element content.                                                                                           |
    | `boolean`                                          | `isNamespaceAware``()`<br>Indicates whether or not the factory is configured to produce parsers which are namespace aware.                                                                                                                                        |
    | `boolean`                                          | `isValidating``()`<br>Indicates whether or not the factory is configured to produce parsers which validate the XML content during parse.                                                                                                                          |
    | `abstract `[`DocumentBuilder`](DocumentBuilder.md) | `newDocumentBuilder``()`<br>Creates a new instance of a DocumentBuilder using the currently configured parameters.                                                                                                                                                |
    | `static DocumentBuilderFactory`                    | `newInstance``()`<br>Obtain a new instance of a `DocumentBuilderFactory`.                                                                                                                                                                                         |
    | `abstract void`                                    | `setAttribute``(java.lang.String name, java.lang.Object value)`<br>Allows the user to set specific attributes on the underlying implementation.                                                                                                                   |
    | `void`                                             | `setCoalescing``(boolean coalescing)`<br>Specifies that the parser produced by this code will convert CDATA nodes to Text nodes and append it to the adjacent (if any) text node.                                                                                 |
    | `void`                                             | `setExpandEntityReferences``(boolean expandEntityRef)`<br>Specifies that the parser produced by this code will expand entity reference nodes.                                                                                                                     |
    | `void`                                             | `setIgnoringComments``(boolean ignoreComments)`<br>Specifies that the parser produced by this code will ignore comments.                                                                                                                                          |
    | `void`                                             | `setIgnoringElementContentWhitespace``(boolean whitespace)`<br>Specifies that the parsers created by this factory must eliminate whitespace in element content (sometimes known loosely as 'ignorable whitespace') when parsing XML documents (see XML Rec 2.10). |
    | `void`                                             | `setNamespaceAware``(boolean awareness)`<br>Specifies that the parser produced by this code will provide support for XML namespaces.                                                                                                                              |
    | `void`                                             | `setValidating``(boolean validating)`<br>Specifies that the parser produced by this code will validate documents as they are parsed.                                                                                                                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### newInstance

          public static DocumentBuilderFactory newInstance()

      Obtain a new instance of a `DocumentBuilderFactory`. This static method creates a new factory instance. This method uses the following ordered lookup procedure to determine the `DocumentBuilderFactory` implementation class to load:
      - Use the `javax.xml.parsers.DocumentBuilderFactory` system property.
      - Use the JAVA_HOME(the parent directory where jdk is installed)/lib/jaxp.properties for a property file that contains the name of the implementation class keyed on the same value as the system property defined above.
      - Use the Services API (as detailed in teh JAR specification), if available, to determine the classname. The Services API will look for a classname in the file `META-INF/services/javax.xml.parsers.DocumentBuilderFactory` in jars available to the runtime.
      - Platform default `DocumentBuilderFactory` instance.

      Once an application has obtained a reference to a `DocumentBuilderFactory` it can use the factory to configure and obtain parser instances.
      Throws:
      [`FactoryConfigurationError`](FactoryConfigurationError.md) - if the implementation is not available or cannot be instantiated.

    <!-- -->

    - #### newDocumentBuilder

          public abstract DocumentBuilder newDocumentBuilder()
                                                      throws ParserConfigurationException

      Creates a new instance of a DocumentBuilder using the currently configured parameters.
      Throws:
      [`ParserConfigurationException`](ParserConfigurationException.md) - if a DocumentBuilder cannot be created which satisfies the configuration requested

    <!-- -->

    - #### setNamespaceAware

          public void setNamespaceAware(boolean awareness)

      Specifies that the parser produced by this code will provide support for XML namespaces. By default the value of this is set to `false`

    <!-- -->

    - #### setValidating

          public void setValidating(boolean validating)

      Specifies that the parser produced by this code will validate documents as they are parsed. By default the value of this is set to `false`

    <!-- -->

    - #### setIgnoringElementContentWhitespace

          public void setIgnoringElementContentWhitespace(boolean whitespace)

      Specifies that the parsers created by this factory must eliminate whitespace in element content (sometimes known loosely as 'ignorable whitespace') when parsing XML documents (see XML Rec 2.10). Note that only whitespace which is directly contained within element content that has an element only content model (see XML Rec 3.2.1) will be eliminated. Due to reliance on the content model this setting requires the parser to be in validating mode. By default the value of this is set to `false`

    <!-- -->

    - #### setExpandEntityReferences

          public void setExpandEntityReferences(boolean expandEntityRef)

      Specifies that the parser produced by this code will expand entity reference nodes. By default the value of this is set to `true`

    <!-- -->

    - #### setIgnoringComments

          public void setIgnoringComments(boolean ignoreComments)

      Specifies that the parser produced by this code will ignore comments. By default the value of this is set to `false`

    <!-- -->

    - #### setCoalescing

          public void setCoalescing(boolean coalescing)

      Specifies that the parser produced by this code will convert CDATA nodes to Text nodes and append it to the adjacent (if any) text node. By default the value of this is set to `false`

    <!-- -->

    - #### isNamespaceAware

          public boolean isNamespaceAware()

      Indicates whether or not the factory is configured to produce parsers which are namespace aware.

    <!-- -->

    - #### isValidating

          public boolean isValidating()

      Indicates whether or not the factory is configured to produce parsers which validate the XML content during parse.

    <!-- -->

    - #### isIgnoringElementContentWhitespace

          public boolean isIgnoringElementContentWhitespace()

      Indicates whether or not the factory is configured to produce parsers which ignore ignorable whitespace in element content.

    <!-- -->

    - #### isExpandEntityReferences

          public boolean isExpandEntityReferences()

      Indicates whether or not the factory is configured to produce parsers which expand entity reference nodes.

    <!-- -->

    - #### isIgnoringComments

          public boolean isIgnoringComments()

      Indicates whether or not the factory is configured to produce parsers which ignores comments.

    <!-- -->

    - #### isCoalescing

          public boolean isCoalescing()

      Indicates whether or not the factory is configured to produce parsers which converts CDATA nodes to Text nodes and appends it to the adjacent (if any) Text node.

    <!-- -->

    - #### setAttribute

          public abstract void setAttribute(java.lang.String name,
                                            java.lang.Object value)
                                     throws java.lang.IllegalArgumentException

      Allows the user to set specific attributes on the underlying implementation.
      Parameters:
      `name` - The name of the attribute.

      `value` - The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

    <!-- -->

    - #### getAttribute

          public abstract java.lang.Object getAttribute(java.lang.String name)
                                                 throws java.lang.IllegalArgumentException

      Allows the user to retrieve specific attributes on the underlying implementation.
      Parameters:
      `name` - The name of the attribute.

      Returns:
      value The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

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

- **[Prev Class](DocumentBuilder.md)**
- **[Next Class](FactoryConfigurationError.md)**

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
