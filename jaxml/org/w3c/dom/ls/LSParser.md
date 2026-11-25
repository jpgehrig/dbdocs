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

- **[Prev Class](LSOutput.md)**
- **[Next Class](LSParserFilter.md)**

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

## **Interface LSParser**

-

  ------------------------------------------------------------------------

  **
  **

      public interface LSParser

  **An interface to an object that is able to build, or augment, a DOM tree from various input sources.**
  **`LSParser` provides an API for parsing XML and building the corresponding DOM document structure. A `LSParser` instance can be obtained by invoking the `DOMImplementationLS.createLSParser()` method.**

  **As specified in \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\] , when a document is first made available via the LSParser:**

  - **there will never be two adjacent nodes of type NODE_TEXT, and there will never be empty text nodes.**
  - **it is expected that the `value` and `nodeValue` attributes of an `Attr` node initially return the [XML 1.0 normalized value](http://www.w3.org/TR/2000/REC-xml-20001006#AVNormalize). However, if the parameters " [validate-if-schema](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_validate_if_schema)" and " [datatype-normalization](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_datatype_normalization)" are set to `true`, depending on the attribute normalization used, the attribute values may differ from the ones obtained by the XML 1.0 attribute normalization. If the parameters " [datatype-normalization](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_datatype_normalization)" is set to `false`, the XML 1.0 attribute normalization is guaranteed to occur, and if the attributes list does not contain namespace declarations, the `attributes` attribute on `Element` node represents the property \[attributes\] defined in \[[XML Information Set](http://www.w3.org/TR/2001/REC-xml-infoset-20011024/)\] .**

  Asynchronous `LSParser` objects are expected to also implement the `events::EventTarget` interface so that event listeners can be registered on asynchronous `LSParser` objects.

  Events supported by asynchronous `LSParser` objects are:

  load
  The `LSParser` finishes to load the document. See also the definition of the `LSLoadEvent` interface.

  progress
  The `LSParser` signals progress as data is parsed. This specification does not attempt to define exactly when progress events should be dispatched, that is intentionally left as implementation depenedent, but here is one example of how an application might dispatch progress events. Once the parser starts receiving data, a progress event is dispatched to indicate that the parsing starts, then from there on, a progress event is dispatched for every 4096 bytes of data that is received and processed. This is only one example, though, and implementations can choose to dispatch progress events at any time while parsing, or not dispatch them at all. See also the definition of the `LSProgressEvent` interface.

  **Note:** All events defined in this specification use the namespace URI `"http://www.w3.org/2002/DOMLS"`.

  While parsing an input source, errors are reported to the application through the error handler (`LSParser.config`'s " [error-handler](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_error_handler)" parameter). This specification does in no way try to define all possible errors that can occur while parsing XML, or any other markup, but some common error cases are defined. The types (`DOMError.type`) of errors and warnings defined by this specification are:

  `"check-character-normalization-failure" [error]`
  Raised if the paramter " [check-character-normalization](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_check_character_normalization)" is set to true and a string is encoutered that fails normalization checking.

  `"doctype-not-allowed" [fatal]`
  Raised if the configuration parameter "disallow-doctype" is set to `true` and a doctype is encountered.

  `"pi-base-uri-not-preserved" [warning]`
  Raised if a processing instruction is encoutered in a location where the base URI of the processing instruction can not be preserved. One example of a case where this warning will be raised is if the configuration parameter " [entities](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_entities)" is set to `false` and the following XML file is parsed:

       <!DOCTYPE root [ <!ENTITY e SYSTEM 'subdir/myentity.ent' ]>
       <root> &e; </root>

  And `subdir/myentity.ent` contains:

      <one> <two/> </one> <?pi 3.14159?>
       <more/>

  `"unbound-prefix-in-entity" [warning]`
  An implementation dependent warning that may be raised if the configuration parameter " [namespaces](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_namespaces)" is set to `true` and an unbound namespace prefix is encountered in an entity's replacement text. Raising this warning is not enforced since some existing parsers may not recognize unbound namespace prefixes in the replacement text of entities.

  `"unknown-character-denormalization" [fatal]`
  Raised if the configuration parameter "ignore-unknown-character-denormalizations" is set to `false` and a character is encountered for which the processor cannot determine the normalization properties.

  `"unsupported-encoding" [fatal]`
  Raised if an unsupported encoding is encountered.

  `"unsupported-media-type" [fatal]`
  Raised if the configuration parameter "supported-media-types-only" is set to `true` and an unsupported media type is encountered.

  In addition to raising the defined errors and warnings, implementations are expected to raise implementation specific errors and warnings for any other error and warning cases such as IO errors (file not found, permission denied,...), XML well-formedness errors, and so on.

  See also the [Document Object Model (DOM) Level 3 Load and Save Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-LS-20031107).

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                        |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------|
    | `static short`    | `ACTION_APPEND_AS_CHILDREN`<br>Append the result of the parse operation as children of the context node.                     |
    | `static short`    | `ACTION_INSERT_AFTER`<br>Insert the result of the parse operation as the immediately following sibling of the context node.  |
    | `static short`    | `ACTION_INSERT_BEFORE`<br>Insert the result of the parse operation as the immediately preceding sibling of the context node. |
    | `static short`    | `ACTION_REPLACE`<br>Replace the context node with the result of the parse operation.                                         |
    | `static short`    | `ACTION_REPLACE_CHILDREN`<br>Replace all the children of the context node with the result of the parse operation.            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                            | Method and Description                                                                                                                                                                                                                                                                          |
    |----------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                       | `abort``()`<br>Abort the loading of the document that is currently being loaded by the `LSParser`.                                                                                                                                                                                              |
    | `boolean`                                    | `getAsync``()`<br>`true` if the `LSParser` is asynchronous, `false` if it is synchronous.                                                                                                                                                                                                       |
    | `boolean`                                    | `getBusy``()`<br>`true` if the `LSParser` is currently busy loading a document, otherwise `false`.                                                                                                                                                                                              |
    | [`DOMConfiguration`](../DOMConfiguration.md) | `getConfig``()`<br>The `DOMConfiguration` object used when parsing an input source.                                                                                                                                                                                                             |
    | [`LSParserFilter`](LSParserFilter.md)        | `getFilter``()`<br>When a filter is provided, the implementation will call out to the filter as it is constructing the DOM tree structure.                                                                                                                                                      |
    | [`Document`](../Document.md)                 | `parse``(`[`LSInput`](LSInput.md)` input)`<br>Parse an XML document from a resource identified by a `LSInput`.                                                                                                                                                                                  |
    | [`Document`](../Document.md)                 | `parseURI``(java.lang.String uri)`<br>Parse an XML document from a location identified by a URI reference \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\].                                                                                                                             |
    | [`Node`](../Node.md)                         | `parseWithContext``(`[`LSInput`](LSInput.md)` input, `[`Node`](../Node.md)` contextArg, short action)`<br>Parse an XML fragment from a resource identified by a `LSInput` and insert the content into an existing document at the position specified with the `context` and `action` arguments. |
    | `void`                                       | `setFilter``(`[`LSParserFilter`](LSParserFilter.md)` filter)`<br>When a filter is provided, the implementation will call out to the filter as it is constructing the DOM tree structure.                                                                                                        |

<!-- -->

- - ### Field Detail

    - #### ACTION_APPEND_AS_CHILDREN

          static final short ACTION_APPEND_AS_CHILDREN

      Append the result of the parse operation as children of the context node. For this action to work, the context node must be an `Element` or a `DocumentFragment`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ACTION_REPLACE_CHILDREN

          static final short ACTION_REPLACE_CHILDREN

      Replace all the children of the context node with the result of the parse operation. For this action to work, the context node must be an `Element`, a `Document`, or a `DocumentFragment`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ACTION_INSERT_BEFORE

          static final short ACTION_INSERT_BEFORE

      Insert the result of the parse operation as the immediately preceding sibling of the context node. For this action to work the context node's parent must be an `Element` or a `DocumentFragment`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ACTION_INSERT_AFTER

          static final short ACTION_INSERT_AFTER

      Insert the result of the parse operation as the immediately following sibling of the context node. For this action to work the context node's parent must be an `Element` or a `DocumentFragment`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ACTION_REPLACE

          static final short ACTION_REPLACE

      Replace the context node with the result of the parse operation. For this action to work, the context node must have a parent, and the parent must be an `Element` or a `DocumentFragment`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getConfig

          DOMConfiguration getConfig()

      The `DOMConfiguration` object used when parsing an input source. This `DOMConfiguration` is specific to the parse operation and no parameter values from this `DOMConfiguration` object are passed automatically to the `DOMConfiguration` object on the `Document` that is created, or used, by the parse operation. The DOM application is responsible for passing any needed parameter values from this `DOMConfiguration` object to the `DOMConfiguration` object referenced by the `Document` object.
      In addition to the parameters recognized in \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\] , the `DOMConfiguration` objects for `LSParser` add or modify the following parameters:
      `"charset-overrides-xml-encoding"`
      `true`
      \[*required*\] (*default*) If a higher level protocol such as HTTP \[[IETF RFC 2616](http://www.ietf.org/rfc/rfc2616.txt)\] provides an indication of the character encoding of the input stream being processed, that will override any encoding specified in the XML declaration or the Text declaration (see also section 4.3.3, "Character Encoding in Entities", in \[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\]). Explicitly setting an encoding in the `LSInput` overrides any encoding from the protocol.

      `false`
      \[*required*\] The parser ignores any character set encoding information from higher-level protocols.

      `"disallow-doctype"`
      `true`
      \[*optional*\] Throw a fatal **"doctype-not-allowed"** error if a doctype node is found while parsing the document. This is useful when dealing with things like SOAP envelopes where doctype nodes are not allowed.

      `false`
      \[*required*\] (*default*) Allow doctype nodes in the document.

      `"ignore-unknown-character-denormalizations"`
      `true`
      \[*required*\] (*default*) If, while verifying full normalization when \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\] is supported, a processor encounters characters for which it cannot determine the normalization properties, then the processor will ignore any possible denormalizations caused by these characters. This parameter is ignored for \[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\].

      `false`
      \[*optional*\] Report an fatal **"unknown-character-denormalization"** error if a character is encountered for which the processor cannot determine the normalization properties.

      `"infoset"`
      See the definition of `DOMConfiguration` for a description of this parameter. Unlike in \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\] , this parameter will default to `true` for `LSParser`.

      `"namespaces"`
      `true`
      \[*required*\] (*default*) Perform the namespace processing as defined in \[[XML Namespaces](http://www.w3.org/TR/1999/REC-xml-names-19990114/)\] and \[[XML Namespaces 1.1](http://www.w3.org/TR/2003/PR-xml-names11-20031105/)\] .

      `false`
      \[*optional*\] Do not perform the namespace processing.

      `"resource-resolver"`
      \[*required*\] A reference to a `LSResourceResolver` object, or null. If the value of this parameter is not null when an external resource (such as an external XML entity or an XML schema location) is encountered, the implementation will request that the `LSResourceResolver` referenced in this parameter resolves the resource.

      `"supported-media-types-only"`
      `true`
      \[*optional*\] Check that the media type of the parsed resource is a supported media type. If an unsupported media type is encountered, a fatal error of type **"unsupported-media-type"** will be raised. The media types defined in \[[IETF RFC 3023](http://www.ietf.org/rfc/rfc3023.txt)\] must always be accepted.

      `false`
      \[*required*\] (*default*) Accept any media type.


      The parameter " [well-formed](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_well_formed)" cannot be set to `false`.

    <!-- -->

    - #### getFilter

          LSParserFilter getFilter()

      When a filter is provided, the implementation will call out to the filter as it is constructing the DOM tree structure. The filter can choose to remove elements from the document being constructed, or to terminate the parsing early.
      The filter is invoked after the operations requested by the `DOMConfiguration` parameters have been applied. For example, if " [validate](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_validate)" is set to `true`, the validation is done before invoking the filter.

    <!-- -->

    - #### setFilter

          void setFilter(LSParserFilter filter)

      When a filter is provided, the implementation will call out to the filter as it is constructing the DOM tree structure. The filter can choose to remove elements from the document being constructed, or to terminate the parsing early.
      The filter is invoked after the operations requested by the `DOMConfiguration` parameters have been applied. For example, if " [validate](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_validate)" is set to `true`, the validation is done before invoking the filter.

    <!-- -->

    - #### getAsync

          boolean getAsync()

      `true` if the `LSParser` is asynchronous, `false` if it is synchronous.

    <!-- -->

    - #### getBusy

          boolean getBusy()

      `true` if the `LSParser` is currently busy loading a document, otherwise `false`.

    <!-- -->

    - #### parse

          Document parse(LSInput input)
                  throws DOMException

      Parse an XML document from a resource identified by a `LSInput`.
      Parameters:
      `input` - The `LSInput` from which the source of the document is to be read.

      Returns:
      If the `LSParser` is a synchronous `LSParser`, the newly created and populated `Document` is returned. If the `LSParser` is asynchronous, `null` is returned since the document object may not yet be constructed when this method returns.

      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if the `LSParser`'s `LSParser.busy` attribute is `true`.

    <!-- -->

    - #### parseURI

          Document parseURI(java.lang.String uri)
                     throws DOMException

      Parse an XML document from a location identified by a URI reference \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\]. If the URI contains a fragment identifier (see section 4.1 in \[[IETF RFC 2396](http://www.ietf.org/rfc/rfc2396.txt)\]), the behavior is not defined by this specification, future versions of this specification may define the behavior.
      Parameters:
      `uri` - The location of the XML document to be read.

      Returns:
      If the `LSParser` is a synchronous `LSParser`, the newly created and populated `Document` is returned. If the `LSParser` is asynchronous, `null` is returned since the document object may not yet be constructed when this method returns.

      Throws:
      [`DOMException`](../DOMException.md) - INVALID_STATE_ERR: Raised if the `LSParser.busy` attribute is `true`.

    <!-- -->

    - #### parseWithContext

          Node parseWithContext(LSInput input,
                                Node contextArg,
                                short action)
                         throws DOMException

      Parse an XML fragment from a resource identified by a `LSInput` and insert the content into an existing document at the position specified with the `context` and `action` arguments. When parsing the input stream, the context node (or its parent, depending on where the result will be inserted) is used for resolving unbound namespace prefixes. The context node's `ownerDocument` node (or the node itself if the node of type `DOCUMENT_NODE`) is used to resolve default attributes and entity references.
      As the new data is inserted into the document, at least one mutation event is fired per new immediate child or sibling of the context node.
      If the context node is a `Document` node and the action is `ACTION_REPLACE_CHILDREN`, then the document that is passed as the context node will be changed such that its `xmlEncoding`, `documentURI`, `xmlVersion`, `actualEncoding`, `xmlStandalone`, and all other such attributes are set to what they would be set to if the input source was parsed using `LSParser.parse()`.
      If the `LSParser` is asynchronous then the insertion of the resulting DOM structure is atomic, e.g. the whole structure is inserted only once the whole input stream is completely parsed without errors.
      If an error occurs while parsing, the caller is notified through the `ErrorHandler` instance associated with the " [error-handler](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_error_handler)" parameter of the `DOMConfiguration`.
      When calling `parseWithContext`, the values of the following configuration parameters will be ignored and their default values will always be used instead: " [validate](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_validate)", " [validate-if-schema](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_validate_if_schema)", and " [element-content-whitespace](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_element_content_whitespace)". Other parameters will be treated normally, and the parser is expected to call the `LSParserFilter` just as if a whole document was parsed.
      Parameters:
      `input` - The `LSInput` from which the source document is to be read. The source document must be an XML fragment, i.e. anything except a complete XML document (except in the case where the context node of type `DOCUMENT_NODE`, and the action is `ACTION_REPLACE_CHILDREN`), a DOCTYPE (internal subset), entity declaration(s), notation declaration(s), or XML or text declaration(s).

      `contextArg` - The node that is used as the context for the data that is being parsed. This node must be a `Document` node, a `DocumentFragment` node, or a node of a type that is allowed as a child of an `Element` node, e.g. it cannot be an `Attribute` node.

      `action` - This parameter describes which action should be taken between the new set of nodes being inserted and the existing children of the context node. The set of possible actions is defined in `ACTION_TYPES` above.

      Returns:
      Return the node that is the result of the parse operation. If the result is more than one top-level node, the first one is returned.

      Throws:
      [`DOMException`](../DOMException.md) - NOT_SUPPORTED_ERR: Raised if the `LSParser` doesn't support this method.
      NO_MODIFICATION_ALLOWED_ERR: Raised if the context node is a read only node.
      INVALID_STATE_ERR: Raised if the `LSParser.busy` attribute is `true`.

    <!-- -->

    - #### abort

          void abort()

      Abort the loading of the document that is currently being loaded by the `LSParser`. If the `LSParser` is currently not busy, a call to this method does nothing.

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

- **[Prev Class](LSOutput.md)**
- **[Next Class](LSParserFilter.md)**

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
