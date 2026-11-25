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

- **[Prev Class](JXSAXParserFactory.md)**
- **[Next Class](JXTransformer.md)**

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

## **Class JXSAXTransformerFactory**

- **java.lang.Object**

- - **[javax.xml.transform.TransformerFactory](../../../javax/xml/transform/TransformerFactory.md)**

  - - **[javax.xml.transform.sax.SAXTransformerFactory](../../../javax/xml/transform/sax/SAXTransformerFactory.md)**

    - - **oracle.xml.jaxp.JXSAXTransformerFactory**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class JXSAXTransformerFactory
      extends SAXTransformerFactory

  **A JXTransformerFactory instance can be used to create Transformer and Templates objects.**
  **The system property that determines which Factory implementation to create is named "javax.xml.transform.TransformerFactory". This property names a concrete subclass of the TransformerFactory abstract class (in our case, it is JXSAXTransformerFactory). If the property is not defined, a platform default is be used.**

  **This class also provides SAX-specific factory methods. It provides two types of ContentHandlers, one for creating Transformers, the other for creating Templates objects.

  **
  **If an application wants to set the ErrorHandler or EntityResolver for an XMLReader used during a transformation, it should use a URIResolver to return the SAXSource which provides (with getXMLReader) a reference to the XMLReader.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description |
    |---------------------------|-----------------------|
    | `static java.lang.String` | `COMPATIBLE_VERSION`  |

    -

      ### **Fields inherited from class javax.xml.transform.sax.[SAXTransformerFactory](../../../javax/xml/transform/sax/SAXTransformerFactory.md)**

      **[`FEATURE`](../../../javax/xml/transform/sax/SAXTransformerFactory.md)`, `[`FEATURE_XMLFILTER`](../../../javax/xml/transform/sax/SAXTransformerFactory.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                              |
    |----------------------------------------------------------|
    | `JXSAXTransformerFactory``()`<br>The default constructor |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                              | Method and Description                                                                                                                                                                                                                                                                                                                                                                                         |
    |--------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Source`](../../../javax/xml/transform/Source.md)                             | `getAssociatedStylesheet``(`[`Source`](../../../javax/xml/transform/Source.md)` source, java.lang.String media, java.lang.String title, java.lang.String charset)`<br>Get the stylesheet specification(s) associated via the xml-stylesheet processing instruction (see http://www.w3.org/TR/xml-stylesheet/) with the document document specified in the source parameter, and that match the given criteria. |
    | `java.lang.Object`                                                             | `getAttribute``(java.lang.String name)`<br>Allows the user to retrieve specific attributes on the underlying implementation.                                                                                                                                                                                                                                                                                   |
    | [`ErrorListener`](../../../javax/xml/transform/ErrorListener.md)               | `getErrorListener``()`<br>Get the error event handler for the TransformerFactory.                                                                                                                                                                                                                                                                                                                              |
    | `boolean`                                                                      | `getFeature``(java.lang.String name)`<br>Look up the value of a feature.                                                                                                                                                                                                                                                                                                                                       |
    | `oracle.xml.xslt.OutputURIResolver`                                            | `getOutputURIResolver``()`<br>Get the object that is used by default during the transformation to resolve URIs used in xsl:result-document                                                                                                                                                                                                                                                                     |
    | [`URIResolver`](../../../javax/xml/transform/URIResolver.md)                   | `getURIResolver``()`<br>Get the object that is used by default during the transformation to resolve URIs used in document(), xsl:import, or xsl:include.                                                                                                                                                                                                                                                       |
    | [`Templates`](../../../javax/xml/transform/Templates.md)                       | `newTemplates``(`[`Source`](../../../javax/xml/transform/Source.md)` source)`<br>Process the Source into a Templates object, which is a a compiled representation of the source.                                                                                                                                                                                                                               |
    | [`TemplatesHandler`](../../../javax/xml/transform/sax/TemplatesHandler.md)     | `newTemplatesHandler``()`<br>Get a TemplatesHandler object that can process SAX ContentHandler events into a Templates object.                                                                                                                                                                                                                                                                                 |
    | [`Transformer`](../../../javax/xml/transform/Transformer.md)                   | `newTransformer``()`<br>Create a new Transformer object that performs a copy of the source to the result.                                                                                                                                                                                                                                                                                                      |
    | [`Transformer`](../../../javax/xml/transform/Transformer.md)                   | `newTransformer``(`[`Source`](../../../javax/xml/transform/Source.md)` source)`<br>Process the Source into a Transformer object.                                                                                                                                                                                                                                                                               |
    | [`TransformerHandler`](../../../javax/xml/transform/sax/TransformerHandler.md) | `newTransformerHandler``()`<br>Get a TransformerHandler object that can process SAX ContentHandler events into a Result.                                                                                                                                                                                                                                                                                       |
    | [`TransformerHandler`](../../../javax/xml/transform/sax/TransformerHandler.md) | `newTransformerHandler``(`[`Source`](../../../javax/xml/transform/Source.md)` src)`<br>Get a TransformerHandler object that can process SAX ContentHandler events into a Result, based on the transformation instructions specified by the argument.                                                                                                                                                           |
    | [`TransformerHandler`](../../../javax/xml/transform/sax/TransformerHandler.md) | `newTransformerHandler``(`[`Templates`](../../../javax/xml/transform/Templates.md)` templates)`<br>Get a TransformerHandler object that can process SAX ContentHandler events into a Result, based on the Templates argument.                                                                                                                                                                                  |
    | [`XMLFilter`](../../../org/xml/sax/XMLFilter.md)                               | `newXMLFilter``(`[`Source`](../../../javax/xml/transform/Source.md)` src)`<br>Create an XMLFilter that uses the given Source as the transformation instructions.                                                                                                                                                                                                                                               |
    | [`XMLFilter`](../../../org/xml/sax/XMLFilter.md)                               | `newXMLFilter``(`[`Templates`](../../../javax/xml/transform/Templates.md)` templates)`<br>Create an XMLFilter, based on the Templates argument..                                                                                                                                                                                                                                                               |
    | `void`                                                                         | `setAttribute``(java.lang.String name, java.lang.Object value)`<br>Allows the user to set specific attributes on the underlying implementation.                                                                                                                                                                                                                                                                |
    | `void`                                                                         | `setErrorListener``(`[`ErrorListener`](../../../javax/xml/transform/ErrorListener.md)` listener)`<br>Set the error event listener for the TransformerFactory, which is used for the processing of transformation instructions, and not for the transformation itself.                                                                                                                                          |
    | `void`                                                                         | `setFeature``(java.lang.String name, boolean value)`                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                                                         | `setOutputURIResolver``(oracle.xml.xslt.OutputURIResolver resolver)`<br>Set an object that is used by default during the transformation to resolve output URIs used for xsl:result-document.                                                                                                                                                                                                                   |
    | `void`                                                                         | `setURIResolver``(`[`URIResolver`](../../../javax/xml/transform/URIResolver.md)` resolver)`<br>Set an object that is used by default during the transformation to resolve URIs used in xsl:import, or xsl:include.                                                                                                                                                                                             |

    - ### Methods inherited from class javax.xml.transform.[TransformerFactory](../../../javax/xml/transform/TransformerFactory.md)

      [`newInstance`](../../../javax/xml/transform/TransformerFactory.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### COMPATIBLE_VERSION

          public static final java.lang.String COMPATIBLE_VERSION

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### JXSAXTransformerFactory

          public JXSAXTransformerFactory()

      The default constructor

  <!-- -->

  - ### Method Detail

    - #### newTransformerHandler

          public TransformerHandler newTransformerHandler(Source src)
                                                   throws TransformerConfigurationException

      Get a TransformerHandler object that can process SAX ContentHandler events into a Result, based on the transformation instructions specified by the argument.
      Specified by:
      [`newTransformerHandler`](../../../javax/xml/transform/sax/SAXTransformerFactory.md) in class [`SAXTransformerFactory`](../../../javax/xml/transform/sax/SAXTransformerFactory.md)

      Parameters:
      `src` - The Source of the transformation instructions.

      Returns:
      TransformerHandler ready to transform SAX events.

      Throws:
      [`TransformerConfigurationException`](../../../javax/xml/transform/TransformerConfigurationException.md) - If for some reason the TransformerHandler can not be created.

    <!-- -->

    - #### newTransformerHandler

          public TransformerHandler newTransformerHandler(Templates templates)
                                                   throws TransformerConfigurationException

      Get a TransformerHandler object that can process SAX ContentHandler events into a Result, based on the Templates argument.
      Specified by:
      [`newTransformerHandler`](../../../javax/xml/transform/sax/SAXTransformerFactory.md) in class [`SAXTransformerFactory`](../../../javax/xml/transform/sax/SAXTransformerFactory.md)

      Parameters:
      `templates` - The compiled transformation instructions.

      Returns:
      TransformerHandler ready to transform SAX events.

      Throws:
      [`TransformerConfigurationException`](../../../javax/xml/transform/TransformerConfigurationException.md) - If for some reason the TransformerHandler can not be created.

    <!-- -->

    - #### newTransformerHandler

          public TransformerHandler newTransformerHandler()
                                                   throws TransformerConfigurationException

      Get a TransformerHandler object that can process SAX ContentHandler events into a Result. The transformation is defined as an identity (or copy) transformation, for example to copy a series of SAX parse events into a DOM tree.
      Specified by:
      [`newTransformerHandler`](../../../javax/xml/transform/sax/SAXTransformerFactory.md) in class [`SAXTransformerFactory`](../../../javax/xml/transform/sax/SAXTransformerFactory.md)

      Returns:
      A non-null reference to a TransformerHandler, that may be used as a ContentHandler for SAX parse events.

      Throws:
      [`TransformerConfigurationException`](../../../javax/xml/transform/TransformerConfigurationException.md) - If for some reason the TransformerHandler cannot be created.

    <!-- -->

    - #### newTemplatesHandler

          public TemplatesHandler newTemplatesHandler()
                                               throws TransformerConfigurationException

      Get a TemplatesHandler object that can process SAX ContentHandler events into a Templates object.
      Specified by:
      [`newTemplatesHandler`](../../../javax/xml/transform/sax/SAXTransformerFactory.md) in class [`SAXTransformerFactory`](../../../javax/xml/transform/sax/SAXTransformerFactory.md)

      Returns:
      A non-null reference to a TransformerHandler, that may be used as a ContentHandler for SAX parse events.

      Throws:
      [`TransformerConfigurationException`](../../../javax/xml/transform/TransformerConfigurationException.md) - If for some reason the TemplatesHandler cannot be created.

    <!-- -->

    - #### newXMLFilter

          public XMLFilter newXMLFilter(Source src)
                                 throws TransformerConfigurationException

      Create an XMLFilter that uses the given Source as the transformation instructions.
      Specified by:
      [`newXMLFilter`](../../../javax/xml/transform/sax/SAXTransformerFactory.md) in class [`SAXTransformerFactory`](../../../javax/xml/transform/sax/SAXTransformerFactory.md)

      Parameters:
      `src` - The Source of the transformation instructions.

      Returns:
      An XMLFilter object, or null if this feature is not supported.

      Throws:
      [`TransformerConfigurationException`](../../../javax/xml/transform/TransformerConfigurationException.md) - If for some reason the TemplatesHandler cannot be created.

    <!-- -->

    - #### newXMLFilter

          public XMLFilter newXMLFilter(Templates templates)
                                 throws TransformerConfigurationException

      Create an XMLFilter, based on the Templates argument..
      Specified by:
      [`newXMLFilter`](../../../javax/xml/transform/sax/SAXTransformerFactory.md) in class [`SAXTransformerFactory`](../../../javax/xml/transform/sax/SAXTransformerFactory.md)

      Parameters:
      `templates` - The compiled transformation instructions.

      Returns:
      An XMLFilter object, or null if this feature is not supported.

      Throws:
      [`TransformerConfigurationException`](../../../javax/xml/transform/TransformerConfigurationException.md) - If for some reason the TemplatesHandler cannot be created.

    <!-- -->

    - #### newTransformer

          public Transformer newTransformer(Source source)
                                     throws TransformerConfigurationException

      Process the Source into a Transformer object. Care must be given not to use this object in multiple threads running concurrently. Different TransformerFactories can be used concurrently by different threads.
      Specified by:
      [`newTransformer`](../../../javax/xml/transform/TransformerFactory.md) in class [`TransformerFactory`](../../../javax/xml/transform/TransformerFactory.md)

      Parameters:
      `source` - An object that holds a URI, input stream, etc.

      Returns:
      A Transformer object that may be used to perform a transformation in a single thread, never null.

      Throws:
      [`TransformerConfigurationException`](../../../javax/xml/transform/TransformerConfigurationException.md) - May throw this during the parse when it is constructing the Templates object and fails.

    <!-- -->

    - #### newTransformer

          public Transformer newTransformer()
                                     throws TransformerConfigurationException

      Create a new Transformer object that performs a copy of the source to the result.
      Specified by:
      [`newTransformer`](../../../javax/xml/transform/TransformerFactory.md) in class [`TransformerFactory`](../../../javax/xml/transform/TransformerFactory.md)

      Returns:
      A Transformer object that may be used to perform a transformation in a single thread, never null.

      Throws:
      [`TransformerConfigurationException`](../../../javax/xml/transform/TransformerConfigurationException.md) - May throw this during the parse when it is constructing the Templates object and fails.

    <!-- -->

    - #### newTemplates

          public Templates newTemplates(Source source)
                                 throws TransformerConfigurationException

      Process the Source into a Templates object, which is a a compiled representation of the source. This Templates object may then be used concurrently across multiple threads. Creating a Templates object allows the TransformerFactory to do detailed performance optimization of transformation instructions, without penalizing runtime transformation.
      Specified by:
      [`newTemplates`](../../../javax/xml/transform/TransformerFactory.md) in class [`TransformerFactory`](../../../javax/xml/transform/TransformerFactory.md)

      Parameters:
      `source` - An object that holds a URL, input stream, etc.

      Returns:
      A Templates object capable of being used for transformation purposes, never null.

      Throws:
      [`TransformerConfigurationException`](../../../javax/xml/transform/TransformerConfigurationException.md) - May throw this during the parse when it is constructing the Templates object and fails.

    <!-- -->

    - #### getAssociatedStylesheet

          public Source getAssociatedStylesheet(Source source,
                                                java.lang.String media,
                                                java.lang.String title,
                                                java.lang.String charset)
                                         throws TransformerConfigurationException

      Get the stylesheet specification(s) associated via the xml-stylesheet processing instruction (see http://www.w3.org/TR/xml-stylesheet/) with the document document specified in the source parameter, and that match the given criteria. Note that it is possible to return several stylesheets, in which case they are applied as if they were a list of imports or cascades in a single stylesheet.
      Specified by:
      [`getAssociatedStylesheet`](../../../javax/xml/transform/TransformerFactory.md) in class [`TransformerFactory`](../../../javax/xml/transform/TransformerFactory.md)

      Parameters:
      `source` - The XML source document.

      `media` - The media attribute to be matched. May be null, in which case the prefered templates will be used (i.e. alternate = no).

      `title` - The value of the title attribute to match. May be null.

      `charset` - The value of the charset attribute to match. May be null.

      Returns:
      A Source object suitable for passing to the TransformerFactory.

      Throws:
      `TransformerConfigurationException.`

      [`TransformerConfigurationException`](../../../javax/xml/transform/TransformerConfigurationException.md)

    <!-- -->

    - #### setURIResolver

          public void setURIResolver(URIResolver resolver)

      Set an object that is used by default during the transformation to resolve URIs used in xsl:import, or xsl:include.
      Specified by:
      [`setURIResolver`](../../../javax/xml/transform/TransformerFactory.md) in class [`TransformerFactory`](../../../javax/xml/transform/TransformerFactory.md)

      Parameters:
      `resolver` - An object that implements the URIResolver interface, or null.

    <!-- -->

    - #### setOutputURIResolver

          public void setOutputURIResolver(oracle.xml.xslt.OutputURIResolver resolver)

      Set an object that is used by default during the transformation to resolve output URIs used for xsl:result-document.
      Parameters:
      `resolver` - An object that implements the OutputURIResolver interface, or null.

    <!-- -->

    - #### getURIResolver

          public URIResolver getURIResolver()

      Get the object that is used by default during the transformation to resolve URIs used in document(), xsl:import, or xsl:include.
      Specified by:
      [`getURIResolver`](../../../javax/xml/transform/TransformerFactory.md) in class [`TransformerFactory`](../../../javax/xml/transform/TransformerFactory.md)

      Returns:
      The URIResolver that was set with setURIResolver.

    <!-- -->

    - #### getOutputURIResolver

          public oracle.xml.xslt.OutputURIResolver getOutputURIResolver()

      Get the object that is used by default during the transformation to resolve URIs used in xsl:result-document
      Returns:
      The OutputURIResolver that was set with setOutputURIResolver.

    <!-- -->

    - #### setFeature

          public void setFeature(java.lang.String name,
                                 boolean value)
                          throws TransformerConfigurationException

      Throws:
      [`TransformerConfigurationException`](../../../javax/xml/transform/TransformerConfigurationException.md)

    <!-- -->

    - #### getFeature

          public boolean getFeature(java.lang.String name)

      Look up the value of a feature.
      The feature name is any absolute URI.

      Specified by:
      [`getFeature`](../../../javax/xml/transform/TransformerFactory.md) in class [`TransformerFactory`](../../../javax/xml/transform/TransformerFactory.md)

      Parameters:
      `name` - The feature name, which is an absolute URI.

      Returns:
      The current state of the feature (true or false).

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String name,
                                   java.lang.Object value)
                            throws java.lang.IllegalArgumentException

      Allows the user to set specific attributes on the underlying implementation. An attribute in this context is defined to be an option that the implementation provides.
      Specified by:
      [`setAttribute`](../../../javax/xml/transform/TransformerFactory.md) in class [`TransformerFactory`](../../../javax/xml/transform/TransformerFactory.md)

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
      [`getAttribute`](../../../javax/xml/transform/TransformerFactory.md) in class [`TransformerFactory`](../../../javax/xml/transform/TransformerFactory.md)

      Parameters:
      `name` - The name of the attribute.

      Returns:
      value The value of the attribute.

      Throws:
      `java.lang.IllegalArgumentException` - thrown if the underlying implementation doesn't recognize the attribute.

    <!-- -->

    - #### setErrorListener

          public void setErrorListener(ErrorListener listener)
                                throws java.lang.IllegalArgumentException

      Set the error event listener for the TransformerFactory, which is used for the processing of transformation instructions, and not for the transformation itself.
      Specified by:
      [`setErrorListener`](../../../javax/xml/transform/TransformerFactory.md) in class [`TransformerFactory`](../../../javax/xml/transform/TransformerFactory.md)

      Parameters:
      `listener` - The new error listener.

      Throws:
      `java.lang.IllegalArgumentException` - if listener is null.

    <!-- -->

    - #### getErrorListener

          public ErrorListener getErrorListener()

      Get the error event handler for the TransformerFactory.
      Specified by:
      [`getErrorListener`](../../../javax/xml/transform/TransformerFactory.md) in class [`TransformerFactory`](../../../javax/xml/transform/TransformerFactory.md)

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

- **[Prev Class](JXSAXParserFactory.md)**
- **[Next Class](JXTransformer.md)**

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
