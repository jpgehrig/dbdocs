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

- **[Prev Class](DTDHandler.md)**
- **[Next Class](ErrorHandler.md)**

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

**org.xml.sax**

## **Interface EntityResolver**

- **All Known Implementing Classes:**
  **[CXMLHandlerBase](../../../oracle/xml/comp/CXMLHandlerBase.md), [DefaultHandler](helpers/DefaultHandler.md), [DefaultXMLDocumentHandler](../../../oracle/xml/parser/v2/DefaultXMLDocumentHandler.md), [DocumentBuilder](../../../oracle/xml/parser/v2/DocumentBuilder.md), [HandlerBase](HandlerBase.md), [XMLFilterImpl](helpers/XMLFilterImpl.md), [XMLSAXSerializer](../../../oracle/xml/parser/v2/XMLSAXSerializer.md), [XMLTokenizer](../../../oracle/xml/parser/v2/XMLTokenizer.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface EntityResolver

  **Basic interface for resolving entities.**
  > ***This module, both source code and documentation, is in the Public Domain, and comes with **NO WARRANTY**.***

  **If a SAX application needs to implement customized handling for external entities, it must implement this interface and register an instance with the SAX driver using the [`setEntityResolver`](XMLReader.md) method.**

  **The XML reader will then allow the application to intercept any external entities (including the external DTD subset and external parameter entities, if any) before including them.**

  **Many SAX applications will not need to implement this interface, but it will be especially useful for applications that build XML documents from databases or other specialised input sources, or for applications that use URI types other than URLs.**

  **The following resolver would provide the application with a special character stream for the entity with the system identifier "http://www.myhost.com/today":**

       import org.xml.sax.EntityResolver;
       import org.xml.sax.InputSource;

       public class MyResolver implements EntityResolver {
         public InputSource resolveEntity (String publicId, String systemId)
         {
           if (systemId.equals("http://www.myhost.com/today")) {
                    // return a special input source
             MyReader reader = new MyReader();
             return new InputSource(reader);
           } else {
                    // use the default behaviour
             return null;
           }
         }
       }


  **The application can also use this interface to redirect system identifiers to local URIs or to look up replacements in a catalog (possibly by using the public identifier).**

  **Since:**
  **SAX 1.0**

  **See Also:**
  **[`Parser.setEntityResolver(org.xml.sax.EntityResolver)`](Parser.md), [`InputSource`](InputSource.md)**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type               | Method and Description                                                                                                         |
    |---------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
    | [`InputSource`](InputSource.md) | `resolveEntity``(java.lang.String publicId, java.lang.String systemId)`<br>Allow the application to resolve external entities. |

<!-- -->

- - ### Method Detail

    - #### resolveEntity

          InputSource resolveEntity(java.lang.String publicId,
                                    java.lang.String systemId)
                             throws SAXException,
                                    java.io.IOException

      Allow the application to resolve external entities.
      The Parser will call this method before opening any external entity except the top-level document entity (including the external DTD subset, external entities referenced within the DTD, and external entities referenced within the document element): the application may request that the parser resolve the entity itself, that it use an alternative URI, or that it use an entirely different input source.

      Application writers can use this method to redirect external system identifiers to secure and/or local URIs, to look up public identifiers in a catalogue, or to read an entity from a database or other input source (including, for example, a dialog box).

      If the system identifier is a URL, the SAX parser must resolve it fully before reporting it to the application.

      Parameters:
      `publicId` - The public identifier of the external entity being referenced, or null if none was supplied.

      `systemId` - The system identifier of the external entity being referenced.

      Returns:
      An InputSource object describing the new input source, or null to request that the parser open a regular URI connection to the system identifier.

      Throws:
      [`SAXException`](SAXException.md) - Any SAX exception, possibly wrapping another exception.

      `java.io.IOException` - A Java-specific IO exception, possibly the result of creating a new InputStream or Reader for the InputSource.

      See Also:
      [`InputSource`](InputSource.md)

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

- **[Prev Class](DTDHandler.md)**
- **[Next Class](ErrorHandler.md)**

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

**org.xml.sax, org.xml.sax.ext, and org.xml.sax.helpers are SAX packages, and are in the public domain. See <http://www.saxproject.org>.**
