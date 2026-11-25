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

- **[Prev Class](TransformerException.md)**
- **[Next Class](TransformerFactoryConfigurationError.md)**

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

**javax.xml.transform**

## **Class TransformerFactory**

- **java.lang.Object**

- - **javax.xml.transform.TransformerFactory**

<!-- -->

- **Direct Known Subclasses:**
  **[SAXTransformerFactory](sax/SAXTransformerFactory.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class TransformerFactory
      extends java.lang.Object

  **A TransformerFactory instance can be used to create Transformer and Template objects.**
  **The system property that determines which Factory implementation to create is named "javax.xml.transform.TransformerFactory". This property names a concrete subclass of the TransformerFactory abstract class. If the property is not defined, a platform default is be used.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                              | Method and Description                                                                                                                                                                                                                                                                                                                                                            |
    |------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`Source`](Source.md)               | `getAssociatedStylesheet``(`[`Source`](Source.md)` source, java.lang.String media, java.lang.String title, java.lang.String charset)`<br>Get the stylesheet specification(s) associated via the xml-stylesheet processing instruction (see http://www.w3.org/TR/xml-stylesheet/) with the document document specified in the source parameter, and that match the given criteria. |
    | `abstract java.lang.Object`                    | `getAttribute``(java.lang.String name)`<br>Allows the user to retrieve specific attributes on the underlying implementation.                                                                                                                                                                                                                                                      |
    | `abstract `[`ErrorListener`](ErrorListener.md) | `getErrorListener``()`<br>Get the error event handler for the TransformerFactory.                                                                                                                                                                                                                                                                                                 |
    | `abstract boolean`                             | `getFeature``(java.lang.String name)`<br>Look up the value of a feature.                                                                                                                                                                                                                                                                                                          |
    | `abstract `[`URIResolver`](URIResolver.md)     | `getURIResolver``()`<br>Get the object that is used by default during the transformation to resolve URIs used in document(), xsl:import, or xsl:include.                                                                                                                                                                                                                          |
    | `static TransformerFactory`                    | `newInstance``()`<br>Obtain a new instance of a `TransformerFactory`.                                                                                                                                                                                                                                                                                                             |
    | `abstract `[`Templates`](Templates.md)         | `newTemplates``(`[`Source`](Source.md)` source)`<br>Process the Source into a Templates object, which is a a compiled representation of the source.                                                                                                                                                                                                                               |
    | `abstract `[`Transformer`](Transformer.md)     | `newTransformer``()`<br>Create a new Transformer object that performs a copy of the source to the result.                                                                                                                                                                                                                                                                         |
    | `abstract `[`Transformer`](Transformer.md)     | `newTransformer``(`[`Source`](Source.md)` source)`<br>Process the Source into a Transformer object.                                                                                                                                                                                                                                                                               |
    | `abstract void`                                | `setAttribute``(java.lang.String name, java.lang.Object value)`<br>Allows the user to set specific attributes on the underlying implementation.                                                                                                                                                                                                                                   |
    | `abstract void`                                | `setErrorListener``(`[`ErrorListener`](ErrorListener.md)` listener)`<br>Set the error event listener for the TransformerFactory, which is used for the processing of transformation instructions, and not for the transformation itself.                                                                                                                                          |
    | `abstract void`                                | `setURIResolver``(`[`URIResolver`](URIResolver.md)` resolver)`<br>Set an object that is used by default during the transformation to resolve URIs used in xsl:import, or xsl:include.                                                                                                                                                                                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### newInstance

          public static TransformerFactory newInstance()
                                                throws TransformerFactoryConfigurationError

      Obtain a new instance of a `TransformerFactory`. This static method creates a new factory instance This method uses the following ordered lookup procedure to determine the `TransformerFactory` implementation class to load:
      - Use the `javax.xml.parsers.DocumentBuilderFactory` system property.
      - Use the JAVA_HOME(the parent directory where jdk is installed)/lib/jaxp.properties for a property file that contains the name of the implementation class keyed on the same value as the system property defined above.
      - Use the Services API (as detailed in teh JAR specification), if available, to determine the classname. The Services API will look for a classname in the file `META-INF/services/javax.xml.parsers.TransformerFactory` in jars available to the runtime.
      - Platform default `TransformerFactory` instance.

      Once an application has obtained a reference to a `TransformerFactory` it can use the factory to configure and obtain parser instances.
      Returns:
      new TransformerFactory instance, never null.

      Throws:
      [`TransformerFactoryConfigurationError`](TransformerFactoryConfigurationError.md) - if the implmentation is not available or cannot be instantiated.

    <!-- -->

    - #### newTransformer

          public abstract Transformer newTransformer(Source source)
                                              throws TransformerConfigurationException

      Process the Source into a Transformer object. Care must be given not to use this object in multiple threads running concurrently. Different TransformerFactories can be used concurrently by different threads.
      Parameters:
      `source` - An object that holds a URI, input stream, etc.

      Returns:
      A Transformer object that may be used to perform a transformation in a single thread, never null.

      Throws:
      [`TransformerConfigurationException`](TransformerConfigurationException.md) - May throw this during the parse when it is constructing the Templates object and fails.

    <!-- -->

    - #### newTransformer

          public abstract Transformer newTransformer()
                                              throws TransformerConfigurationException

      Create a new Transformer object that performs a copy of the source to the result.
      Returns:
      A Transformer object that may be used to perform a transformation in a single thread, never null.

      Throws:
      [`TransformerConfigurationException`](TransformerConfigurationException.md) - May throw this during the parse when it is constructing the Templates object and fails.

    <!-- -->

    - #### newTemplates

          public abstract Templates newTemplates(Source source)
                                          throws TransformerConfigurationException

      Process the Source into a Templates object, which is a a compiled representation of the source. This Templates object may then be used concurrently across multiple threads. Creating a Templates object allows the TransformerFactory to do detailed performance optimization of transformation instructions, without penalizing runtime transformation.
      Parameters:
      `source` - An object that holds a URL, input stream, etc.

      Returns:
      A Templates object capable of being used for transformation purposes, never null.

      Throws:
      [`TransformerConfigurationException`](TransformerConfigurationException.md) - May throw this during the parse when it is constructing the Templates object and fails.

    <!-- -->

    - #### getAssociatedStylesheet

          public abstract Source getAssociatedStylesheet(Source source,
                                                         java.lang.String media,
                                                         java.lang.String title,
                                                         java.lang.String charset)
                                                  throws TransformerConfigurationException

      Get the stylesheet specification(s) associated via the xml-stylesheet processing instruction (see http://www.w3.org/TR/xml-stylesheet/) with the document document specified in the source parameter, and that match the given criteria. Note that it is possible to return several stylesheets, in which case they are applied as if they were a list of imports or cascades in a single stylesheet.
      Parameters:
      `source` - The XML source document.

      `media` - The media attribute to be matched. May be null, in which case the prefered templates will be used (i.e. alternate = no).

      `title` - The value of the title attribute to match. May be null.

      `charset` - The value of the charset attribute to match. May be null.

      Returns:
      A Source object suitable for passing to the TransformerFactory.

      Throws:
      `TransformerConfigurationException.`

      [`TransformerConfigurationException`](TransformerConfigurationException.md)

    <!-- -->

    - #### setURIResolver

          public abstract void setURIResolver(URIResolver resolver)

      Set an object that is used by default during the transformation to resolve URIs used in xsl:import, or xsl:include.
      Parameters:
      `resolver` - An object that implements the URIResolver interface, or null.

    <!-- -->

    - #### getURIResolver

          public abstract URIResolver getURIResolver()

      Get the object that is used by default during the transformation to resolve URIs used in document(), xsl:import, or xsl:include.
      Returns:
      The URIResolver that was set with setURIResolver.

    <!-- -->

    - #### getFeature

          public abstract boolean getFeature(java.lang.String name)

      Look up the value of a feature.
      The feature name is any absolute URI.

      Parameters:
      `name` - The feature name, which is an absolute URI.

      Returns:
      The current state of the feature (true or false).

    <!-- -->

    - #### setAttribute

          public abstract void setAttribute(java.lang.String name,
                                            java.lang.Object value)
                                     throws java.lang.IllegalArgumentException

      Allows the user to set specific attributes on the underlying implementation. An attribute in this context is defined to be an option that the implementation provides.
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

    <!-- -->

    - #### setErrorListener

          public abstract void setErrorListener(ErrorListener listener)
                                         throws java.lang.IllegalArgumentException

      Set the error event listener for the TransformerFactory, which is used for the processing of transformation instructions, and not for the transformation itself.
      Parameters:
      `listener` - The new error listener.

      Throws:
      `java.lang.IllegalArgumentException` - if listener is null.

    <!-- -->

    - #### getErrorListener

          public abstract ErrorListener getErrorListener()

      Get the error event handler for the TransformerFactory.
      Returns:
      The current error handler, which should never be null.

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

- **[Prev Class](TransformerException.md)**
- **[Next Class](TransformerFactoryConfigurationError.md)**

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
