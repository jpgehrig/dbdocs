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

- **[Prev Class](MarshalException.md)**
- **[Next Class](NotIdentifiableEvent.md)**

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

## **Interface Marshaller**

-

  ------------------------------------------------------------------------

  **
  **

      public interface Marshaller

  **The `Marshaller` class is responsible for governing the process of serializing Java content trees back into XML data. It provides the basic marshalling methods:**

  ***Assume the following setup code in all following code fragments:***

  >            JAXBContext jc = JAXBContext.newInstance( "com.acme.foo" );
  >            Unmarshaller u = jc.createUnmarshaller();
  >            FooObject obj = (FooObject)u.unmarshal( new File( "foo.xml" ) );
  >            Marshaller m = jc.createMarshaller();
  >

  **Marshalling to a File:**

  >            OutputStream os = new FileOutputStream( "nosferatu.xml" );
  >            m.marshal( obj, os );
  >

  **Marshalling to a SAX ContentHandler:**

  >            // assume MyContentHandler instanceof ContentHandler
  >            m.marshal( obj, new MyContentHandler() );
  >

  **Marshalling to a DOM Node:**

  >            DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();
  >            dbf.setNamespaceAware(true);
  >            DocumentBuilder db = dbf.newDocumentBuilder();
  >            Document doc = db.newDocument();
  >
  >            m.marshal( obj, doc );
  >

  **Marshalling to a java.io.OutputStream:**

  >            m.marshal( obj, System.out );
  >

  **Marshalling to a java.io.Writer:**

  >            m.marshal( obj, new PrintWriter( System.out ) );
  >

  **Marshalling to a javax.xml.transform.SAXResult:**

  >            // assume MyContentHandler instanceof ContentHandler
  >            SAXResult result = new SAXResult( new MyContentHandler() );
  >
  >            m.marshal( obj, result );
  >

  **Marshalling to a javax.xml.transform.DOMResult:**

  >            DOMResult result = new DOMResult();
  >
  >            m.marshal( obj, result );
  >

  **Marshalling to a javax.xml.transform.StreamResult:**

  >            StreamResult result = new StreamResult( System.out );
  >
  >            m.marshal( obj, result );
  >

  **Marshalling `java.lang.Object` Objects
  **

  > Although each of the marshal methods accepts a `java.lang.Object` as its first parameter, JAXB Providers are not required to be able to marshal **any** arbitrary `java.lang.Object`. If the `JAXBContext` object that was used to create this `Marshaller` does not have enough information to know how to marshal the object parameter (or any objects reachable from it), then the marshal operation will throw a [`MarshalException`](MarshalException.md). Even though JAXB Providers are not required to be able to marshal arbitrary `java.lang.Object` objects, some providers may allow it.

  **Encoding**

  > By default, the Marshaller will use UTF-8 encoding when generating XML data to a `java.io.File`, `java.io.OutputStream`, and `java.io.Writer`. Use the `setProperty` API to change the ouput encoding used during these marshal operations.

  **Validation and Well-Formedness**

  > Client applications are not required to validate the Java content tree prior to calling any of the marshal API's. Furthermore, there is no requirement that the Java content tree be valid with respect to its original schema in order to marshal it back into XML data. Different JAXB Providers will support marshalling invalid Java content trees at varying levels, however all JAXB Providers must be able to marshal a valid content tree back to XML data. A JAXB Provider must throw a `MarshalException` when it is unable to complete the marshal operation due to invalid content. Some JAXB Providers will fully allow marshalling invalid content, others will fail on the first validation error.
  >
  > Although there is no way to enable validation during the marshal operation, it is possible that certain types of validation events will be detected during the operation. These events will be reported to the registered event handler. If the client application has not registered an event handler prior to invoking one of the marshal API's, then events will be delivered to the default event handler which will terminate the marshal operation after encountering the first error or fatal error.

  **Supported Properties**

  > `jaxb.encoding`
  > The output encoding to use when marshalling the XML data. The Marshaller will use "UTF-8" by default if this property is not specified.
  >
  > `jaxb.formatted.output`
  > This property controls whether or not the Marshaller will format the resulting XML data with line breaks and indentation. A true value for this property indicates human readable indented xml data, while a false value indicates unformatted xml data. The Marshaller will default to false (unformatted) if this property is not specified.
  >
  > `jaxb.schemaLocation`
  > This property allows the client application to specify an xsi:schemaLocation attribute in the generated XML data. The format of the schemaLocation attribute value is discussed in an easy to understand, non-normative form in [Section 5.6 of the W3C XML Schema Part 0: Primer](http://www.w3.org/TR/xmlschema-0/#schemaLocation) and specified in [Section 2.6 of the W3C XML Schema Part 1: Structures](http://www.w3.org/TR/xmlschema-1/#Instance_Document_Constructions).
  >
  > `jaxb.noNamespaceSchemaLocation`
  > This property allows the client application to specify an xsi:noNamespaceSchemaLocation attribute in the generated XML data. The format of the schemaLocation attribute value is discussed in an easy to understand, non-normative form in [Section 5.6 of the W3C XML Schema Part 0: Primer](http://www.w3.org/TR/xmlschema-0/#schemaLocation) and specified in [Section 2.6 of the W3C XML Schema Part 1: Structures](http://www.w3.org/TR/xmlschema-1/#Instance_Document_Constructions).

  **Encoding Parameter Name**

  > JAXB Providers **must** convert the encoding parameter to its canonical form as defined by the [IANA Charset Registry](http://www.iana.org/assignments/character-sets). Some character sets have a *historical name* that is defined for compatibility with previous versions of the Java platform. These *historical names* **must not** be used since they may violate the W3C XML v1.0 Recommendation requirements for valid encoding names. In some cases, the historical name is the same as the canonical name, but not always. The client application should be allowed to specify the encoding using any of the available aliases for that charset (For example, "UTF8" and "UTF-8" should both resolve to the canonical name for this encoding which is "UTF-8". However, the *historical name* is "UTF8", which should not be used by providers).
  >
  > Please refer to the javadocs for [java.nio.charset.Charset](https://docs.oracle.com/javase/7/docs/api/java/nio/charset/Charset.html) for more details.

  Since:
  JAXB1.0

  See Also:
  [`JAXBContext`](JAXBContext.md), [`Validator`](Validator.md), [`Unmarshaller`](Unmarshaller.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                     |
    |---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `JAXB_ENCODING`<br>The name of the property used to specify the output encoding in the marshalled XML data.                                                               |
    | `static java.lang.String` | `JAXB_FORMATTED_OUTPUT`<br>The name of the property used to specify whether or not the marshalled XML data is formated with linefeeds and indentation.                    |
    | `static java.lang.String` | `JAXB_NONAMESPACESCHEMALOCATION`<br>The name of the property used to specify the the xsi:noNamespaceSchemaLocation attribute value to place in the marshalled XML output. |
    | `static java.lang.String` | `JAXB_SCHEMALOCATION`<br>The name of the property used to specify the xsi:schemaLocation attribute value to place in the marshalled XML output.                           |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                                    |
    |-------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ValidationEventHandler`](ValidationEventHandler.md) | `getEventHandler``()`<br>Return the current event handler or the default event handler if one hasn't been set.                                                            |
    | `java.lang.Object`                                    | `getProperty``(java.lang.String name)`<br>Get the particular property in the underlying implementation of `Marshaller`.                                                   |
    | `void`                                                | `marshal``(java.lang.Object obj, `[`ContentHandler`](../../../org/xml/sax/ContentHandler.md)` handler)`<br>Marshal the content tree rooted at obj into SAX2 events.       |
    | `void`                                                | `marshal``(java.lang.Object obj, `[`Node`](../../../org/w3c/dom/Node.md)` node)`<br>Marshal the content tree rooted at obj into a DOM tree.                               |
    | `void`                                                | `marshal``(java.lang.Object obj, java.io.OutputStream os)`<br>Marshal the content tree rooted at obj into an output stream.                                               |
    | `void`                                                | `marshal``(java.lang.Object obj, `[`Result`](../transform/Result.md)` result)`<br>Marshal the content tree rooted at obj into the specified `javax.xml.transform.Result`. |
    | `void`                                                | `marshal``(java.lang.Object obj, java.io.Writer writer)`<br>Marshal the content tree rooted at obj into a Writer.                                                         |
    | `void`                                                | `setEventHandler``(`[`ValidationEventHandler`](ValidationEventHandler.md)` handler)`<br>Allow an application to register a validation event handler.                      |
    | `void`                                                | `setProperty``(java.lang.String name, java.lang.Object value)`<br>Set the particular property in the underlying implementation of `Marshaller`.                           |

<!-- -->

- - ### Field Detail

    - #### JAXB_ENCODING

          static final java.lang.String JAXB_ENCODING

      The name of the property used to specify the output encoding in the marshalled XML data.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### JAXB_FORMATTED_OUTPUT

          static final java.lang.String JAXB_FORMATTED_OUTPUT

      The name of the property used to specify whether or not the marshalled XML data is formated with linefeeds and indentation.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### JAXB_SCHEMALOCATION

          static final java.lang.String JAXB_SCHEMALOCATION

      The name of the property used to specify the xsi:schemaLocation attribute value to place in the marshalled XML output.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### JAXB_NONAMESPACESCHEMALOCATION

          static final java.lang.String JAXB_NONAMESPACESCHEMALOCATION

      The name of the property used to specify the the xsi:noNamespaceSchemaLocation attribute value to place in the marshalled XML output.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### marshal

          void marshal(java.lang.Object obj,
                       Result result)
                throws JAXBException

      Marshal the content tree rooted at obj into the specified `javax.xml.transform.Result`.
      All JAXB Providers must at least support [`DOMResult`](../transform/dom/DOMResult.md), [`SAXResult`](../transform/sax/SAXResult.md), and [`StreamResult`](../transform/stream/StreamResult.md). It can support other derived classes of `Result` as well.

      Parameters:
      `obj` - The content tree to be marshalled.

      `result` - XML will be sent to this Result

      Throws:
      [`JAXBException`](JAXBException.md) - If any unexpected problem occurs during the marshalling.

      [`MarshalException`](MarshalException.md) - If obj (or any object reachable from obj) can not be marshalled. See Marshalling objects.

    <!-- -->

    - #### marshal

          void marshal(java.lang.Object obj,
                       java.io.OutputStream os)
                throws JAXBException

      Marshal the content tree rooted at obj into an output stream.
      Parameters:
      `obj` - The content tree to be marshalled.

      `os` - XML will be added to this stream.

      Throws:
      [`JAXBException`](JAXBException.md) - If any unexpected problem occurs during the marshalling.

      [`MarshalException`](MarshalException.md) - If obj (or any object reachable from obj) can not be marshalled. See Marshalling objects.

    <!-- -->

    - #### marshal

          void marshal(java.lang.Object obj,
                       java.io.Writer writer)
                throws JAXBException

      Marshal the content tree rooted at obj into a Writer.
      Parameters:
      `obj` - The content tree to be marshalled.

      `writer` - XML will be sent to this writer.

      Throws:
      [`JAXBException`](JAXBException.md) - If any unexpected problem occurs during the marshalling.

      [`MarshalException`](MarshalException.md) - If obj (or any object reachable from obj) can not be marshalled. See Marshalling objects.

    <!-- -->

    - #### marshal

          void marshal(java.lang.Object obj,
                       ContentHandler handler)
                throws JAXBException

      Marshal the content tree rooted at obj into SAX2 events.
      Parameters:
      `obj` - The content tree to be marshalled.

      `handler` - XML will be sent to this handler as SAX2 events.

      Throws:
      [`JAXBException`](JAXBException.md) - If any unexpected problem occurs during the marshalling.

      [`MarshalException`](MarshalException.md) - If obj (or any object reachable from obj) can not be marshalled. See Marshalling objects.

    <!-- -->

    - #### marshal

          void marshal(java.lang.Object obj,
                       Node node)
                throws JAXBException

      Marshal the content tree rooted at obj into a DOM tree.
      Parameters:
      `obj` - The content tree to be marshalled.

      `node` - DOM nodes will be added as children of this node. This parameter must be a Node that accepts children ([`Document`](../../../org/w3c/dom/Document.md), [`DocumentFragment`](../../../org/w3c/dom/DocumentFragment.md), or [`Element`](../../../org/w3c/dom/Element.md))

      Throws:
      [`JAXBException`](JAXBException.md) - If any unexpected problem occurs during the marshalling.

      [`MarshalException`](MarshalException.md) - If obj (or any object reachable from obj) can not be marshalled. See Marshalling objects.

    <!-- -->

    - #### setProperty

          void setProperty(java.lang.String name,
                           java.lang.Object value)
                    throws PropertyException

      Set the particular property in the underlying implementation of `Marshaller`. See Supported Properties .
      Parameters:
      `name` - the name of the property to be set. This value can either be specified using one of the constant fields or a user supplied string.

      `value` - the value of the property to be set

      Throws:
      [`PropertyException`](PropertyException.md) - when there is an error processing the given property or value

    <!-- -->

    - #### getProperty

          java.lang.Object getProperty(java.lang.String name)
                                throws PropertyException

      Get the particular property in the underlying implementation of `Marshaller`. See Supported Properties .
      Parameters:
      `name` - the name of the property to retrieve

      Returns:
      the value of the requested property

      Throws:
      [`PropertyException`](PropertyException.md) - when there is an error retrieving the given property or value property name

    <!-- -->

    - #### setEventHandler

          void setEventHandler(ValidationEventHandler handler)
                        throws JAXBException

      Allow an application to register a validation event handler.
      The validation event handler will be called by the JAXB Provider if any validation errors are encountered during calls to any of the marshal API's. If the client application does not register a validation event handler before invoking one of the marshal methods, then validation events will be handled by the default event handler which will terminate the marshal operation after the first error or fatal error is encountered.

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

- **[Prev Class](MarshalException.md)**
- **[Next Class](NotIdentifiableEvent.md)**

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
