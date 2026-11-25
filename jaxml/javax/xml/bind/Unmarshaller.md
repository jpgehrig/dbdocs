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

- **[Prev Class](UnmarshalException.md)**
- **[Next Class](UnmarshallerHandler.md)**

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

**javax.xml.bind**

## **Interface Unmarshaller**

-

  ------------------------------------------------------------------------

  **
  **

      public interface Unmarshaller

  **The `Unmarshaller` class governs the process of deserializing XML data into newly created Java content trees, optionally validating the XML data as it is unmarshalled. It provides the basic unmarshalling methods:**
  **Unmarshalling from a File:**

  >            JAXBContext jc = JAXBContext.newInstance( "com.acme.foo" );
  >            Unmarshaller u = jc.createUnmarshaller();
  >            Object o = u.unmarshal( new File( "nosferatu.xml" ) );
  >

  **Unmarshalling from an InputStream:**

  >            InputStream is = new FileInputStream( "nosferatu.xml" );
  >            JAXBContext jc = JAXBContext.newInstance( "com.acme.foo" );
  >            Unmarshaller u = jc.createUnmarshaller();
  >            Object o = u.unmarshal( is );
  >

  **Unmarshalling from a URL:**

  >            JAXBContext jc = JAXBContext.newInstance( "com.acme.foo" );
  >            Unmarshaller u = jc.createUnmarshaller();
  >            URL url = new URL( "http://beaker.east/nosferatu.xml" );
  >            Object o = u.unmarshal( url );
  >

  **Unmarshalling from a StringBuffer using a `javax.xml.transform.stream.StreamSource`:**

  >            JAXBContext jc = JAXBContext.newInstance( "com.acme.foo" );
  >            Unmarshaller u = jc.createUnmarshaller();
  >            StringBuffer xmlStr = new StringBuffer( "<?xml version="1.0"?>..." );
  >            Object o = u.unmarshal( new StreamSource( new StringReader( xmlStr.toString() ) ) );
  >

  **Unmarshalling from a `org.w3c.dom.Node`:**

  >            JAXBContext jc = JAXBContext.newInstance( "com.acme.foo" );
  >            Unmarshaller u = jc.createUnmarshaller();
  >
  >            DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();
  >            dbf.setNamespaceAware(true);
  >            DocumentBuilder db = dbf.newDocumentBuilder();
  >            Document doc = db.parse(new File( "nosferatu.xml"));
  >
  >            Object o = u.unmarshal( doc );
  >

  **Unmarshalling from a `javax.xml.transform.sax.SAXSource` using a client specified validating SAX2.0 parser:**

  >            // configure a validating SAX2.0 parser (Xerces2)
  >            static final String JAXP_SCHEMA_LANGUAGE =
  >                "http://java.sun.com/xml/jaxp/properties/schemaLanguage";
  >            static final String JAXP_SCHEMA_LOCATION =
  >                "http://java.sun.com/xml/jaxp/properties/schemaSource";
  >            static final String W3C_XML_SCHEMA =
  >                "http://www.w3.org/2001/XMLSchema";
  >
  >            System.setProperty( "javax.xml.parsers.SAXParserFactory",
  >                                "org.apache.xerces.jaxp.SAXParserFactoryImpl" );
  >
  >            SAXParserFactory spf = SAXParserFactory.newInstance();
  >            spf.setNamespaceAware(true);
  >            spf.setValidating(true);
  >            SAXParser saxParser = spf.newSAXParser();
  >
  >            try {
  >                saxParser.setProperty(JAXP_SCHEMA_LANGUAGE, W3C_XML_SCHEMA);
  >                saxParser.setProperty(JAXP_SCHEMA_LOCATION, "http://....");
  >            } catch (SAXNotRecognizedException x) {
  >                // exception handling omitted
  >            }
  >
  >            XMLReader xmlReader = saxParser.getXMLReader();
  >            SAXSource source =
  >                new SAXSource( xmlReader, new InputSource( "http://..." ) );
  >
  >            // Setup JAXB to unmarshal
  >            JAXBContext jc = JAXBContext.newInstance( "com.acme.foo" );
  >            Unmarshaller u = jc.createUnmarshaller();
  >            ValidationEventCollector vec = new ValidationEventCollector();
  >            u.setEventHandler( vec );
  >
  >            // turn off the JAXB provider's default validation mechanism to
  >            // avoid duplicate validation
  >            u.setValidating( false )
  >
  >            // unmarshal
  >            Object o = u.unmarshal( source );
  >
  >            // check for events
  >            if( vec.hasEvents() ) {
  >               // iterate over events
  >            }
  >

  **Unmarshalling XML Data
  **

  > The `JAXBContext` object used to create this `Unmarshaller` was initialized with a `contextPath` which determines the schema derived content available to the `Marshaller`, `Unmarshaller`, and `Validator` objects it produces. If the `JAXBContext` object that was used to create this `Unmarshaller` does not have enough information to know how to unmarshal the XML content from the specified source, then the unmarshal operation will abort immediately by throwing a [`UnmarshalException`](UnmarshalException.md).

  **Support for SAX2.0 Compliant Parsers**

  > A client application has the ability to select the SAX2.0 compliant parser of their choice. If a SAX parser is not selected, then the JAXB Provider's default parser will be used. Eventhough the JAXB Provider's default parser is not required to be SAX2.0 compliant, all providers are required to allow a client application to specify their own SAX2.0 parser. Some providers may require the client application to specify the SAX2.0 parser at schema compile time. See `unmarshal(Source)` for more detail.

  **Validation and Well-Formedness**

  > A client application can enable or disable the provider's default validation mechanism via the `setValidating` API. Sophisticated clients can specify their own validating SAX 2.0 compliant parser and bypass the provider's default validation mechanism using the `unmarshal(Source)` API.
  >
  > For a more detailed definition of how validation errors and warnings are handled, see the [`Validator`](Validator.md) javadoc.

  Since:
  JAXB1.0

  See Also:
  [`JAXBContext`](JAXBContext.md), [`Marshaller`](Marshaller.md), [`Validator`](Validator.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                                       |
    |-------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ValidationEventHandler`](ValidationEventHandler.md) | `getEventHandler``()`<br>Return the current event handler or the default event handler if one hasn't been set.                                                               |
    | [`UnmarshallerHandler`](UnmarshallerHandler.md)       | `getUnmarshallerHandler``()`<br>Get an unmarshaller handler object that can be used as a component in an XML pipeline.                                                       |
    | `boolean`                                             | `isValidating``()`<br>Indicates whether or not the `Unmarshaller` is configured to validate during unmarshal operations.                                                     |
    | `void`                                                | `setEventHandler``(`[`ValidationEventHandler`](ValidationEventHandler.md)` handler)`<br>Allow an application to register a `ValidationEventHandler`.                         |
    | `void`                                                | `setValidating``(boolean validating)`<br>Specifies whether or not the default validation mechanism of the `Unmarshaller` should validate during unmarshal operations.        |
    | `java.lang.Object`                                    | `unmarshal``(java.io.File f)`<br>Unmarshal XML data from the specified file and return the resulting content tree.                                                           |
    | `java.lang.Object`                                    | `unmarshal``(`[`InputSource`](../../../org/xml/sax/InputSource.md)` source)`<br>Unmarshal XML data from the specified SAX InputSource and return the resulting content tree. |
    | `java.lang.Object`                                    | `unmarshal``(java.io.InputStream is)`<br>Unmarshal XML data from the specified InputStream and return the resulting content tree.                                            |
    | `java.lang.Object`                                    | `unmarshal``(`[`Node`](../../../org/w3c/dom/Node.md)` node)`<br>Unmarshal XML data from the specified DOM tree and return the resulting content tree.                        |
    | `java.lang.Object`                                    | `unmarshal``(`[`Source`](../transform/Source.md)` source)`<br>Unmarshal XML data from the specified XML Source and return the resulting content tree.                        |
    | `java.lang.Object`                                    | `unmarshal``(java.net.URL url)`<br>Unmarshal XML data from the specified URL and return the resulting content tree.                                                          |

<!-- -->

- - ### Method Detail

    - #### unmarshal

          java.lang.Object unmarshal(java.io.File f)
                              throws JAXBException

      Unmarshal XML data from the specified file and return the resulting content tree.
      Parameters:
      `f` - the file to unmarshal XML data from

      Returns:
      the newly created root object of the java content tree

      Throws:
      [`JAXBException`](JAXBException.md) - If any unexpected errors occur while unmarshalling

      [`UnmarshalException`](UnmarshalException.md) - If the `Unmarshaller` is unable to perform the XML to Java binding. See Unmarshalling XML Data

    <!-- -->

    - #### unmarshal

          java.lang.Object unmarshal(java.io.InputStream is)
                              throws JAXBException

      Unmarshal XML data from the specified InputStream and return the resulting content tree.
      Parameters:
      `is` - the InputStream to unmarshal XML data from

      Returns:
      the newly created root object of the java content tree

      Throws:
      [`JAXBException`](JAXBException.md) - If any unexpected errors occur while unmarshalling

      [`UnmarshalException`](UnmarshalException.md) - If the `Unmarshaller` is unable to perform the XML to Java binding. See Unmarshalling XML Data

    <!-- -->

    - #### unmarshal

          java.lang.Object unmarshal(java.net.URL url)
                              throws JAXBException

      Unmarshal XML data from the specified URL and return the resulting content tree.
      Parameters:
      `url` - the url to unmarshal XML data from

      Returns:
      the newly created root object of the java content tree

      Throws:
      [`JAXBException`](JAXBException.md) - If any unexpected errors occur while unmarshalling

      [`UnmarshalException`](UnmarshalException.md) - If the `Unmarshaller` is unable to perform the XML to Java binding. See Unmarshalling XML Data

    <!-- -->

    - #### unmarshal

          java.lang.Object unmarshal(InputSource source)
                              throws JAXBException

      Unmarshal XML data from the specified SAX InputSource and return the resulting content tree.
      Parameters:
      `source` - the input source to unmarshal XML data from

      Returns:
      the newly created root object of the java content tree

      Throws:
      [`JAXBException`](JAXBException.md) - If any unexpected errors occur while unmarshalling

      [`UnmarshalException`](UnmarshalException.md) - If the `Unmarshaller` is unable to perform the XML to Java binding. See Unmarshalling XML Data

    <!-- -->

    - #### unmarshal

          java.lang.Object unmarshal(Node node)
                              throws JAXBException

      Unmarshal XML data from the specified DOM tree and return the resulting content tree.
      Parameters:
      `node` - the document/element to unmarshal XML data from. The caller must support at least Document and Element.

      Returns:
      the newly created root object of the java content tree

      Throws:
      [`JAXBException`](JAXBException.md) - If any unexpected errors occur while unmarshalling

      [`UnmarshalException`](UnmarshalException.md) - If the `Unmarshaller` is unable to perform the XML to Java binding. See Unmarshalling XML Data

    <!-- -->

    - #### unmarshal

          java.lang.Object unmarshal(Source source)
                              throws JAXBException

      Unmarshal XML data from the specified XML Source and return the resulting content tree.
      **SAX 2.0 Parser Pluggability**

      A client application can choose not to use the default parser mechanism supplied with their JAXB provider. Any SAX 2.0 compliant parser can be substituted for the JAXB provider's default mechanism. To do so, the client application must properly configure a `SAXSource` containing an `XMLReader` implemented by the SAX 2.0 parser provider. If the `XMLReader` has an `org.xml.sax.ErrorHandler` registered on it, it will be replaced by the JAXB Provider so that validation errors can be reported via the `ValidationEventHandler` mechanism of JAXB. If the `SAXSource` does not contain an `XMLReader`, then the JAXB provider's default parser mechanism will be used.

      This parser replacement mechanism can also be used to replace the JAXB provider's unmarshal-time validation engine. The client application must properly configure their SAX 2.0 compliant parser to perform validation (as shown in the example above). Any `SAXParserExceptions` encountered by the parser during the unmarshal operation will be processed by the JAXB provider and converted into JAXB `ValidationEvent` objects which will be reported back to the client via the `ValidationEventHandler` registered with the `Unmarshaller`. *Note:* specifying a substitute validating SAX 2.0 parser for unmarshalling does not necessarily replace the validation engine used by the JAXB provider for performing on-demand validation.

      The only way for a client application to specify an alternate parser mechanism to be used during unmarshal is via the `unmarshal(SAXSource)` API. All other forms of the unmarshal method (File, URL, Node, etc) will use the JAXB provider's default parser and validator mechanisms.

      Parameters:
      `source` - the XML Source to unmarshal XML data from (providers are only required to support SAXSource, DOMSource, and StreamSource)

      Returns:
      the newly created root object of the java content tree

      Throws:
      [`JAXBException`](JAXBException.md) - If any unexpected errors occur while unmarshalling

      [`UnmarshalException`](UnmarshalException.md) - If the `Unmarshaller` is unable to perform the XML to Java binding. See Unmarshalling XML Data

    <!-- -->

    - #### getUnmarshallerHandler

          UnmarshallerHandler getUnmarshallerHandler()

      Get an unmarshaller handler object that can be used as a component in an XML pipeline.
      The JAXB Provider can return the same handler object for multiple invocations of this method. In other words, this method does not necessarily create a new instance of `UnmarshallerHandler`. If the application needs to use more than one `UnmarshallerHandler`, it should create more than one `Unmarshaller`.

      Returns:
      the unmarshaller handler object

      See Also:
      [`UnmarshallerHandler`](UnmarshallerHandler.md)

    <!-- -->

    - #### setValidating

          void setValidating(boolean validating)
                      throws JAXBException

      Specifies whether or not the default validation mechanism of the `Unmarshaller` should validate during unmarshal operations. By default, the `Unmarshaller` does not validate.
      This method may only be invoked before or after calling one of the unmarshal methods.

      This method only controls the JAXB Provider's default unmarshal-time validation mechanism - it has no impact on clients that specify their own validating SAX 2.0 compliant parser. Clients that specify their own unmarshal-time validation mechanism may wish to turn off the JAXB Provider's default validation mechanism via this API to avoid "double validation".

      Parameters:
      `validating` - true if the Unmarshaller should validate during unmarshal, false otherwise

      Throws:
      [`JAXBException`](JAXBException.md) - if an error occurred while enabling or disabling validation at unmarshal time

    <!-- -->

    - #### isValidating

          boolean isValidating()
                        throws JAXBException

      Indicates whether or not the `Unmarshaller` is configured to validate during unmarshal operations.
      This API returns the state of the JAXB Provider's default unmarshal-time validation mechanism.

      Returns:
      true if the Unmarshaller is configured to validate during unmarshal operations, false otherwise

      Throws:
      [`JAXBException`](JAXBException.md) - if an error occurs while retrieving the validating flag

    <!-- -->

    - #### setEventHandler

          void setEventHandler(ValidationEventHandler handler)
                        throws JAXBException

      Allow an application to register a `ValidationEventHandler`.
      The `ValidationEventHandler` will be called by the JAXB Provider if any validation errors are encountered during calls to any of the unmarshal methods. If the client application does not register a `ValidationEventHandler` before invoking the unmarshal methods, then `ValidationEvents` will be handled by the default event handler which will terminate the unmarshal operation after the first error or fatal error is encountered.

      Parameters:
      `handler` - the validation event handler

      Throws:
      [`JAXBException`](JAXBException.md) - if an error was encountered while setting the event handler

    <!-- -->

    - #### getEventHandler

          ValidationEventHandler getEventHandler()
                                          throws JAXBException

      Return the current event handler or the default event handler if one hasn't been set.
      Returns:
      the current ValidationEventHandler or the default event handler if it hasn't been set

      Throws:
      [`JAXBException`](JAXBException.md) - if an error was encountered while getting the current event handler

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

- **[Prev Class](UnmarshalException.md)**
- **[Next Class](UnmarshallerHandler.md)**

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
