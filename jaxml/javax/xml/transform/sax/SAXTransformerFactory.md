Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](SAXSource.md)**
- **[Next Class](TemplatesHandler.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**javax.xml.transform.sax**

## **Class SAXTransformerFactory**

- **java.lang.Object**

- - **[javax.xml.transform.TransformerFactory](../TransformerFactory.md)**

  - - **javax.xml.transform.sax.SAXTransformerFactory**

<!-- -->

- **Direct Known Subclasses:**
  **[JXSAXTransformerFactory](../../../../oracle/xml/jaxp/JXSAXTransformerFactory.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class SAXTransformerFactory
      extends TransformerFactory

  **This class extends TransformerFactory to provide SAX-specific factory methods. It provides two types of ContentHandlers, one for creating Transformers, the other for creating Templates objects.**
  **If an application wants to set the ErrorHandler or EntityResolver for an XMLReader used during a transformation, it should use a URIResolver to return the SAXSource which provides (with getXMLReader) a reference to the XMLReader.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                                                                                                                                                |
    |---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `FEATURE`<br>If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the TransformerFactory returned from [`TransformerFactory.newInstance()`](../TransformerFactory.md) may be safely cast to a SAXTransformerFactory. |
    | `static java.lang.String` | `FEATURE_XMLFILTER`<br>If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the `newXMLFilter(Source src)` and `newXMLFilter(Templates templates)` methods are supported.                                            |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                              | Method and Description                                                                                                                                                                                                     |
    |----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`TemplatesHandler`](TemplatesHandler.md)           | `newTemplatesHandler``()`<br>Get a TemplatesHandler object that can process SAX ContentHandler events into a Templates object.                                                                                             |
    | `abstract `[`TransformerHandler`](TransformerHandler.md)       | `newTransformerHandler``()`<br>Get a TransformerHandler object that can process SAX ContentHandler events into a Result.                                                                                                   |
    | `abstract `[`TransformerHandler`](TransformerHandler.md)       | `newTransformerHandler``(`[`Source`](../Source.md)` src)`<br>Get a TransformerHandler object that can process SAX ContentHandler events into a Result, based on the transformation instructions specified by the argument. |
    | `abstract `[`TransformerHandler`](TransformerHandler.md)       | `newTransformerHandler``(`[`Templates`](../Templates.md)` templates)`<br>Get a TransformerHandler object that can process SAX ContentHandler events into a Result, based on the Templates argument.                        |
    | `abstract `[`XMLFilter`](../../../../org/xml/sax/XMLFilter.md) | `newXMLFilter``(`[`Source`](../Source.md)` src)`<br>Create an XMLFilter that uses the given Source as the transformation instructions.                                                                                     |
    | `abstract `[`XMLFilter`](../../../../org/xml/sax/XMLFilter.md) | `newXMLFilter``(`[`Templates`](../Templates.md)` templates)`<br>Create an XMLFilter, based on the Templates argument..                                                                                                     |

    - ### Methods inherited from class javax.xml.transform.[TransformerFactory](../TransformerFactory.md)

      [`getAssociatedStylesheet`](../TransformerFactory.md)`, `[`getAttribute`](../TransformerFactory.md)`, `[`getErrorListener`](../TransformerFactory.md)`, `[`getFeature`](../TransformerFactory.md)`, `[`getURIResolver`](../TransformerFactory.md)`, `[`newInstance`](../TransformerFactory.md)`, `[`newTemplates`](../TransformerFactory.md)`, `[`newTransformer`](../TransformerFactory.md)`, `[`newTransformer`](../TransformerFactory.md)`, `[`setAttribute`](../TransformerFactory.md)`, `[`setErrorListener`](../TransformerFactory.md)`, `[`setURIResolver`](../TransformerFactory.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### FEATURE

          public static final java.lang.String FEATURE

      If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the TransformerFactory returned from [`TransformerFactory.newInstance()`](../TransformerFactory.md) may be safely cast to a SAXTransformerFactory.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### FEATURE_XMLFILTER

          public static final java.lang.String FEATURE_XMLFILTER

      If [`TransformerFactory.getFeature(java.lang.String)`](../TransformerFactory.md) returns true when passed this value as an argument, the `newXMLFilter(Source src)` and `newXMLFilter(Templates templates)` methods are supported.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### newTransformerHandler

          public abstract TransformerHandler newTransformerHandler(Source src)
                                                            throws TransformerConfigurationException

      Get a TransformerHandler object that can process SAX ContentHandler events into a Result, based on the transformation instructions specified by the argument.
      Parameters:
      `src` - The Source of the transformation instructions.

      Returns:
      TransformerHandler ready to transform SAX events.

      Throws:
      [`TransformerConfigurationException`](../TransformerConfigurationException.md) - If for some reason the TransformerHandler can not be created.

    <!-- -->

    - #### newTransformerHandler

          public abstract TransformerHandler newTransformerHandler(Templates templates)
                                                            throws TransformerConfigurationException

      Get a TransformerHandler object that can process SAX ContentHandler events into a Result, based on the Templates argument.
      Parameters:
      `templates` - The compiled transformation instructions.

      Returns:
      TransformerHandler ready to transform SAX events.

      Throws:
      [`TransformerConfigurationException`](../TransformerConfigurationException.md) - If for some reason the TransformerHandler can not be created.

    <!-- -->

    - #### newTransformerHandler

          public abstract TransformerHandler newTransformerHandler()
                                                            throws TransformerConfigurationException

      Get a TransformerHandler object that can process SAX ContentHandler events into a Result. The transformation is defined as an identity (or copy) transformation, for example to copy a series of SAX parse events into a DOM tree.
      Returns:
      A non-null reference to a TransformerHandler, that may be used as a ContentHandler for SAX parse events.

      Throws:
      [`TransformerConfigurationException`](../TransformerConfigurationException.md) - If for some reason the TransformerHandler cannot be created.

    <!-- -->

    - #### newTemplatesHandler

          public abstract TemplatesHandler newTemplatesHandler()
                                                        throws TransformerConfigurationException

      Get a TemplatesHandler object that can process SAX ContentHandler events into a Templates object.
      Returns:
      A non-null reference to a TransformerHandler, that may be used as a ContentHandler for SAX parse events.

      Throws:
      [`TransformerConfigurationException`](../TransformerConfigurationException.md) - If for some reason the TemplatesHandler cannot be created.

    <!-- -->

    - #### newXMLFilter

          public abstract XMLFilter newXMLFilter(Source src)
                                          throws TransformerConfigurationException

      Create an XMLFilter that uses the given Source as the transformation instructions.
      Parameters:
      `src` - The Source of the transformation instructions.

      Returns:
      An XMLFilter object, or null if this feature is not supported.

      Throws:
      [`TransformerConfigurationException`](../TransformerConfigurationException.md) - If for some reason the TemplatesHandler cannot be created.

    <!-- -->

    - #### newXMLFilter

          public abstract XMLFilter newXMLFilter(Templates templates)
                                          throws TransformerConfigurationException

      Create an XMLFilter, based on the Templates argument..
      Parameters:
      `templates` - The compiled transformation instructions.

      Returns:
      An XMLFilter object, or null if this feature is not supported.

      Throws:
      [`TransformerConfigurationException`](../TransformerConfigurationException.md) - If for some reason the TemplatesHandler cannot be created.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](SAXSource.md)**
- **[Next Class](TemplatesHandler.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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
