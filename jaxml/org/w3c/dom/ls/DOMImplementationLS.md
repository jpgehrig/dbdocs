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

- **Prev Class**
- **[Next Class](LSInput.md)**

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

**org.w3c.dom.ls**

## **Interface DOMImplementationLS**

- **All Known Implementing Classes:**
  **[XMLDOMImplementation](../../../../oracle/xml/parser/v2/XMLDOMImplementation.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DOMImplementationLS

  **`DOMImplementationLS` contains the factory methods for creating Load and Save objects.**
  **The expectation is that an instance of the `DOMImplementationLS` interface can be obtained by using binding-specific casting methods on an instance of the `DOMImplementation` interface or, if the `Document` supports the feature `"Core"` version `"3.0"` defined in \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\] , by using the method `DOMImplementation.getFeature` with parameter values `"LS"` (or `"LS-Async"`) and `"3.0"` (respectively).**

  **See also the [Document Object Model (DOM) Level 3 Load and Save Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-LS-20031107).**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                     |
    |-------------------|-----------------------------------------------------------|
    | `static short`    | `MODE_ASYNCHRONOUS`<br>Create an asynchronous `LSParser`. |
    | `static short`    | `MODE_SYNCHRONOUS`<br>Create a synchronous `LSParser`.    |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                                                                                                                                                                                                       |
    |-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`LSInput`](LSInput.md)           | `createLSInput``()`<br>Create a new empty input source object where `LSInput.characterStream`, `LSInput.byteStream` , `LSInput.stringData` `LSInput.systemId`, `LSInput.publicId`, `LSInput.baseURI`, and `LSInput.encoding` are null, and `LSInput.certifiedText` is false. |
    | [`LSOutput`](LSOutput.md)         | `createLSOutput``()`<br>Create a new empty output destination object where `LSOutput.characterStream`, `LSOutput.byteStream`, `LSOutput.systemId`, `LSOutput.encoding` are null.                                                                                             |
    | [`LSParser`](LSParser.md)         | `createLSParser``(short mode, java.lang.String schemaType)`<br>Create a new `LSParser`.                                                                                                                                                                                      |
    | [`LSSerializer`](LSSerializer.md) | `createLSSerializer``()`<br>Create a new `LSSerializer` object.                                                                                                                                                                                                              |

<!-- -->

- - ### Field Detail

    - #### MODE_SYNCHRONOUS

          static final short MODE_SYNCHRONOUS

      Create a synchronous `LSParser`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### MODE_ASYNCHRONOUS

          static final short MODE_ASYNCHRONOUS

      Create an asynchronous `LSParser`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### createLSParser

          LSParser createLSParser(short mode,
                                  java.lang.String schemaType)
                           throws DOMException

      Create a new `LSParser`. The newly constructed parser may then be configured by means of its `DOMConfiguration` object, and used to parse documents by means of its `parse` method.
      Parameters:
      `mode` - The `mode` argument is either `MODE_SYNCHRONOUS` or `MODE_ASYNCHRONOUS`, if `mode` is `MODE_SYNCHRONOUS` then the `LSParser` that is created will operate in synchronous mode, if it's `MODE_ASYNCHRONOUS` then the `LSParser` that is created will operate in asynchronous mode.

      `schemaType` - An absolute URI representing the type of the schema language used during the load of a `Document` using the newly created `LSParser`. Note that no lexical checking is done on the absolute URI. In order to create a `LSParser` for any kind of schema types (i.e. the LSParser will be free to use any schema found), use the value `null`.

      **Note:** For W3C XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] , applications must use the value `"http://www.w3.org/2001/XMLSchema"`. For XML DTD \[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\], applications must use the value `"http://www.w3.org/TR/REC-xml"`. Other Schema languages are outside the scope of the W3C and therefore should recommend an absolute URI in order to use this method.

      Returns:
      The newly created `LSParser` object. This `LSParser` is either synchronous or asynchronous depending on the value of the `mode` argument.

      **Note:** By default, the newly created `LSParser` does not contain a `DOMErrorHandler`, i.e. the value of the " [error-handler](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_error_handler)" configuration parameter is `null`. However, implementations may provide a default error handler at creation time. In that case, the initial value of the `"error-handler"` configuration parameter on the new created `LSParser` contains a reference to the default error handler.

      Throws:
      [`DOMException`](../DOMException.md) - NOT_SUPPORTED_ERR: Raised if the requested mode or schema type is not supported.

    <!-- -->

    - #### createLSSerializer

          LSSerializer createLSSerializer()

      Create a new `LSSerializer` object.
      Returns:
      The newly created `LSSerializer` object.

      **Note:** By default, the newly created `LSSerializer` has no `DOMErrorHandler`, i.e. the value of the `"error-handler"` configuration parameter is `null`. However, implementations may provide a default error handler at creation time. In that case, the initial value of the `"error-handler"` configuration parameter on the new created `LSSerializer` contains a reference to the default error handler.

    <!-- -->

    - #### createLSInput

          LSInput createLSInput()

      Create a new empty input source object where `LSInput.characterStream`, `LSInput.byteStream` , `LSInput.stringData` `LSInput.systemId`, `LSInput.publicId`, `LSInput.baseURI`, and `LSInput.encoding` are null, and `LSInput.certifiedText` is false.
      Returns:
      The newly created input object.

    <!-- -->

    - #### createLSOutput

          LSOutput createLSOutput()

      Create a new empty output destination object where `LSOutput.characterStream`, `LSOutput.byteStream`, `LSOutput.systemId`, `LSOutput.encoding` are null.
      Returns:
      The newly created output object.

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

- **Prev Class**
- **[Next Class](LSInput.md)**

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

**[Copyright](http://www.w3.org/Consortium/Legal/ipr-notice#Copyright) ©2004 [W3C](http://www.w3.org/)® ([MIT](http://www.csail.mit.edu/), [ERCIM](http://www.ercim.org/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/ipr-notice#Legal_Disclaimer), [trademark](http://www.w3.org/Consortium/Legal/ipr-notice#W3C_Trademarks), [document use](http://www.w3.org/Consortium/Legal/copyright-documents) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software) rules apply. The latest version is at <http://www.w3.org/TR/DOM-Level-3-LS>.**
