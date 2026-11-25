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

- **[Prev Class](LSResourceResolver.md)**
- **[Next Class](LSSerializerFilter.md)**

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

## **Interface LSSerializer**

-

  ------------------------------------------------------------------------

  **
  **

      public interface LSSerializer

  **A `LSSerializer` provides an API for serializing (writing) a DOM document out into XML. The XML data is written to a string or an output stream.**
  **During serialization of XML data, namespace fixup is done as defined in \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\] , Appendix B. \[[DOM Level 2 Core](http://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113)\] allows empty strings as a real namespace URI. If the `namespaceURI` of a `Node` is empty string, the serialization will treat them as `null`, ignoring the prefix if any.**

  **`LSSerializer` accepts any node type for serialization. For nodes of type `Document` or `Entity`, well-formed XML will be created when possible (well-formedness is guaranteed if the document or entity comes from a parse operation and is unchanged since it was created). The serialized output for these node types is either as a XML document or an External XML Entity, respectively, and is acceptable input for an XML parser. For all other types of nodes the serialized form is implementation dependent.**

  **Within a `Document`, `DocumentFragment`, or `Entity` being serialized, `Nodes` are processed as follows**

  - **`Document` nodes are written, including the XML declaration (unless the parameter "xml-declaration" is set to `false`) and a DTD subset, if one exists in the DOM. Writing a `Document` node serializes the entire document.**
  - **`Entity` nodes, when written directly by `LSSerializer.write`, outputs the entity expansion but no namespace fixup is done. The resulting output will be valid as an external entity.**
  - **`EntityReference` nodes are serialized as an entity reference of the form "`&entityName;`" in the output. Child nodes (the expansion) of the entity reference are ignored.**
  - **CDATA sections containing content characters that cannot be represented in the specified output encoding are handled according to the " [split-cdata-sections](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_split_cdata_sections)" parameter. If the parameter is set to `true`, CDATA sections are split, and the unrepresentable characters are serialized as numeric character references in ordinary content. The exact position and number of splits is not specified. If the parameter is set to `false` , unrepresentable characters in a CDATA section are reported as `"invalid-data-in-cdata-section"` errors. The error is not recoverable - there is no mechanism for supplying alternative characters and continuing with the serialization.**
  - **`DocumentFragment` nodes are serialized by serializing the children of the document fragment in the order they appear in the document fragment.**
  - **All other node types (Element, Text, etc.) are serialized to their corresponding XML source form.**

  **Note: The serialization of a `Node` does not always generate a well-formed XML document, i.e. a `LSParser` might throw fatal errors when parsing the resulting serialization.**

  Within the character data of a document (outside of markup), any characters that cannot be represented directly are replaced with character references. Occurrences of '\<' and '&' are replaced by the predefined entities &lt; and &amp;. The other predefined entities (&gt;, &apos;, and &quot;) might not be used, except where needed (e.g. using &gt; in cases such as '\]\]\>'). Any characters that cannot be represented directly in the output character encoding are serialized as numeric character references (and since character encoding standards commonly use hexadecimal representations of characters, using the hexadecimal representation when serializing character references is encouraged).

  To allow attribute values to contain both single and double quotes, the apostrophe or single-quote character (') may be represented as "&apos;", and the double-quote character (") as "&quot;". New line characters and other characters that cannot be represented directly in attribute values in the output character encoding are serialized as a numeric character reference.

  Within markup, but outside of attributes, any occurrence of a character that cannot be represented in the output character encoding is reported as a fatal error. An example would be serializing the element \<LaCañada/\> with `encoding="us-ascii"`.

  When requested by setting the parameter " [normalize-characters](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_normalize_characters)" on `LSSerializer` to true, character normalization is performed according to the rules defined in \[[CharModel](http://www.w3.org/TR/2003/WD-charmod-20030822/)\] on all data to be serialized, both markup and character data. The character normalization process affects only the data as it is being written; it does not alter the DOM's view of the document after serialization has completed.

  When outputting unicode data, whether or not a byte order mark is serialized, or if the output is big-endian or little-endian, is implementation dependent.

  Namespaces are fixed up during serialization, the serialization process will verify that namespace declarations, namespace prefixes and the namespace URI's associated with elements and attributes are consistent. If inconsistencies are found, the serialized form of the document will be altered to remove them. The method used for doing the namespace fixup while serializing a document is the algorithm defined in Appendix B.1, "Namespace normalization", of \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\] .

  Any changes made affect only the namespace prefixes and declarations appearing in the serialized data. The DOM's view of the document is not altered by the serialization operation, and does not reflect any changes made to namespace declarations or prefixes in the serialized output. We may take back what we say in the above paragraph depending on feedback from implementors, but for now the belief is that the DOM's view of the document is not changed during serialization.

  While serializing a document, the parameter "discard-default-content" controls whether or not non-specified data is serialized.

  While serializing, errors and warnings are reported to the application through the error handler (`LSSerializer.config`'s " [error-handler](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_error_handler)" parameter). This specification does in no way try to define all possible errors and warnings that can occur while serializing a DOM node, but some common error and warning cases are defined. The types ( `DOMError.type`) of errors and warnings defined by this specification are:

  `"invalid-data-in-cdata-section" [fatal]`
  Raised if the configuration parameter " [split-cdata-sections](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_split_cdata_sections)" is set to `false` and invalid data is encountered in a CDATA section.

  `"no-output-specified" [fatal]`
  Raised when writing to a `LSOutput` if no output is specified in the `LSOutput`.

  `"unbound-prefix-in-entity-reference" [fatal]`
  Raised if the configuration parameter " [namespaces](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_namespaces)" is set to `true` and an entity whose replacement text contains unbound namespace prefixes is referenced in a location where there are no bindings for the namespace prefixes.

  `"unsupported-encoding" [fatal]`
  Raised if an unsupported encoding is encountered.

  In addition to raising the defined errors and warnings, implementations are expected to raise implementation specific errors and warnings for any other error and warning cases such as IO errors (file not found, permission denied,...) and so on.

  See also the [Document Object Model (DOM) Level 3 Load and Save Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-LS-20031107).

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                             | Method and Description                                                                                                                                                                                                                       |
    |-----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`DOMConfiguration`](../DOMConfiguration.md)  | `getConfig``()`<br>The `DOMConfiguration` object used by the `LSSerializer` when serializing a DOM node.                                                                                                                                     |
    | [`LSSerializerFilter`](LSSerializerFilter.md) | `getFilter``()`<br>When the application provides a filter, the serializer will call out to the filter before serializing each Node.                                                                                                          |
    | `java.lang.String`                            | `getNewLine``()`<br>The end-of-line sequence of characters to be used in the XML being written out.                                                                                                                                          |
    | `void`                                        | `setFilter``(`[`LSSerializerFilter`](LSSerializerFilter.md)` filter)`<br>When the application provides a filter, the serializer will call out to the filter before serializing each Node.                                                    |
    | `void`                                        | `setNewLine``(java.lang.String newLine)`<br>The end-of-line sequence of characters to be used in the XML being written out.                                                                                                                  |
    | `boolean`                                     | `write``(`[`Node`](../Node.md)` nodeArg, `[`LSOutput`](LSOutput.md)` destination)`<br>Serialize the specified node as described above in the general description of the `LSSerializer` interface.                                            |
    | `java.lang.String`                            | `writeToString``(`[`Node`](../Node.md)` nodeArg)`<br>Serialize the specified node as described above in the general description of the `LSSerializer` interface.                                                                             |
    | `boolean`                                     | `writeToURI``(`[`Node`](../Node.md)` nodeArg, java.lang.String uri)`<br>A convenience method that acts as if `LSSerializer.write` was called with a `LSOutput` with no encoding specified and `LSOutput.systemId` set to the `uri` argument. |

<!-- -->

- - ### Method Detail

    - #### getConfig

          DOMConfiguration getConfig()

      The `DOMConfiguration` object used by the `LSSerializer` when serializing a DOM node.
      In addition to the parameters recognized in the \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\] , the `DOMConfiguration` objects for `LSSerializer` adds, or modifies, the following parameters:
      `"canonical-form"`
      `true`
      \[*optional*\] This formatting writes the document according to the rules specified in \[[Canonical XML](http://www.w3.org/TR/2001/REC-xml-c14n-20010315)\]. Setting this parameter to `true` will set the parameter " format-pretty-print" to `false`.

      `false`
      \[*required*\] (*default*) Do not canonicalize the output.

      `"discard-default-content"`
      `true`
      \[*required*\] (*default*) Use the `Attr.specified` attribute to decide what attributes should be discarded. Note that some implementations might use whatever information available to the implementation (i.e. XML schema, DTD, the `Attr.specified` attribute, and so on) to determine what attributes and content to discard if this parameter is set to `true`.

      `false`
      \[*required*\]Keep all attributes and all content.

      `"format-pretty-print"`
      `true`
      \[*optional*\] Formatting the output by adding whitespace to produce a pretty-printed, indented, human-readable form. The exact form of the transformations is not specified by this specification. Pretty-printing changes the content of the document and may affect the validity of the document, validating implementations should preserve validity. Setting this parameter to `true` will set the parameter " [canonical-form](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_canonical_form)" to `false`.

      `false`
      \[*required*\] (*default*) Don't pretty-print the result.

      `"ignore-unknown-character-denormalizations"`
      `true`
      \[*required*\] (*default*) If, while verifying full normalization when \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\] is supported, a character is encountered for which the normalization properties cannot be determined, then raise a `"unknown-character-denormalization"` warning (instead of raising an error, if this parameter is not set) and ignore any possible denormalizations caused by these characters. IMO it would make sense to move this parameter into the DOM Level 3 Core spec, and the error/warning should be defined there.

      `false`
      \[*optional*\] Report an fatal error if a character is encountered for which the processor cannot determine the normalization properties.

      `"normalize-characters"`
      This parameter is equivalent to the one defined by `DOMConfiguration` in \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\] . Unlike in the Core, the default value for this parameter is `true`. While DOM implementations are not required to support fully normalizing the characters in the document according to the rules defined in \[[CharModel](http://www.w3.org/TR/2003/WD-charmod-20030822/)\] supplemented by the definitions of relevant constructs from Section 2.13 of \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\], this parameter must be activated by default if supported.

      `"xml-declaration"`
      `true`
      \[*required*\] (*default*) If a `Document`, `Element`, or `Entity` node is serialized, the XML declaration, or text declaration, should be included. The version (`Document.xmlVersion` if the document is a Level 3 document and the version is non-null, otherwise use the value "1.0"), and the output encoding (see `LSSerializer.write` for details on how to find the output encoding) are specified in the serialized XML declaration.

      `false`
      \[*required*\] Do not serialize the XML and text declarations. Report a `"xml-declaration-needed"` warning if this will cause problems (i.e. the serialized data is of an XML version other than \[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\], or an encoding would be needed to be able to re-parse the serialized data).


      The parameters " [well-formed](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_well_formed)", " [namespaces](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_namespaces)", and " [namespace-declarations](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_namespace_declarations)" cannot be set to `false`.

    <!-- -->

    - #### getNewLine

          java.lang.String getNewLine()

      The end-of-line sequence of characters to be used in the XML being written out. Any string is supported, but these are the recommended end-of-line sequences (using other character sequences than these recommended ones can result in a document that is either not serializable or not well-formed):
      `null`
      Use a default end-of-line sequence. DOM implementations should choose the default to match the usual convention for text files in the environment being used. Implementations must choose a default sequence that matches one of those allowed by section 2.11, "End-of-Line Handling" in \[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\], if the serialized content is XML 1.0 or section 2.11, "End-of-Line Handling" in \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\], if the serialized content is XML 1.1.

      CR
      The carriage-return character (#xD).

      CR-LF
      The carriage-return and line-feed characters (#xD \#xA).

      LF
      The line-feed character (#xA).


      The default value for this attribute is `null`.

    <!-- -->

    - #### setNewLine

          void setNewLine(java.lang.String newLine)

      The end-of-line sequence of characters to be used in the XML being written out. Any string is supported, but these are the recommended end-of-line sequences (using other character sequences than these recommended ones can result in a document that is either not serializable or not well-formed):
      `null`
      Use a default end-of-line sequence. DOM implementations should choose the default to match the usual convention for text files in the environment being used. Implementations must choose a default sequence that matches one of those allowed by section 2.11, "End-of-Line Handling" in \[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\], if the serialized content is XML 1.0 or section 2.11, "End-of-Line Handling" in \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\], if the serialized content is XML 1.1.

      CR
      The carriage-return character (#xD).

      CR-LF
      The carriage-return and line-feed characters (#xD \#xA).

      LF
      The line-feed character (#xA).


      The default value for this attribute is `null`.

    <!-- -->

    - #### getFilter

          LSSerializerFilter getFilter()

      When the application provides a filter, the serializer will call out to the filter before serializing each Node. The filter implementation can choose to remove the node from the stream or to terminate the serialization early.
      The filter is invoked before the operations requested by the `DOMConfiguration` parameters have been applied. For example, CDATA sections are passed to the filter even if " [cdata-sections](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_cdata_sections)" is set to `false`.

    <!-- -->

    - #### setFilter

          void setFilter(LSSerializerFilter filter)

      When the application provides a filter, the serializer will call out to the filter before serializing each Node. The filter implementation can choose to remove the node from the stream or to terminate the serialization early.
      The filter is invoked before the operations requested by the `DOMConfiguration` parameters have been applied. For example, CDATA sections are passed to the filter even if " [cdata-sections](http://www.w3.org/TR/DOM-Level-3-Core/core.html#parameter_cdata_sections)" is set to `false`.

    <!-- -->

    - #### write

          boolean write(Node nodeArg,
                        LSOutput destination)

      Serialize the specified node as described above in the general description of the `LSSerializer` interface. The output is written to the supplied `LSOutput`.
      When writing to a `LSOutput`, the encoding is found by looking at the encoding information that is reachable through the `LSOutput` and the item to be written (or its owner document) in this order:
      1.  `LSOutput.encoding`,
      2.  `Document.actualEncoding`,
      3.  `Document.xmlEncoding`.


      If no encoding is reachable through the above properties, a default encoding of "UTF-8" will be used.
      If the specified encoding is not supported an "unsupported-encoding" fatal error is raised. When outputting XML data, implementations are required to support the encodings "UTF-8", "UTF-16BE", and "UTF-16LE" to guarantee that data is serializable in all encodings that are required to be supported by all XML parsers.
      If no output is specified in the `LSOutput`, a "no-output-specified" fatal error is raised.
      The implementation is responsible of associating the appropriate media type with the serialized data.
      When writing to a HTTP URI, a HTTP PUT is performed. When writing to other types of URIs, the mechanism for writing the data to the URI is implementation dependent.
      Parameters:
      `nodeArg` - The node to serialize.

      `destination` - The destination for the serialized DOM.

      Returns:
      Returns `true` if `node` was successfully serialized and `false` in case the node couldn't be serialized.

    <!-- -->

    - #### writeToURI

          boolean writeToURI(Node nodeArg,
                             java.lang.String uri)

      A convenience method that acts as if `LSSerializer.write` was called with a `LSOutput` with no encoding specified and `LSOutput.systemId` set to the `uri` argument.
      Parameters:
      `nodeArg` - The node to serialize.

      `uri` - The URI to write to.

      Returns:
      Returns `true` if `node` was successfully serialized and `false` in case the node couldn't be serialized.

    <!-- -->

    - #### writeToString

          java.lang.String writeToString(Node nodeArg)
                                  throws DOMException

      Serialize the specified node as described above in the general description of the `LSSerializer` interface. The output is written to a `DOMString` that is returned to the caller (this method completely ignores all the encoding information available).
      Parameters:
      `nodeArg` - The node to serialize.

      Returns:
      Returns the serialized data, or `null` in case the node couldn't be serialized.

      Throws:
      [`DOMException`](../DOMException.md) - DOMSTRING_SIZE_ERR: Raised if the resulting string is too long to fit in a `DOMString`.

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

- **[Prev Class](LSResourceResolver.md)**
- **[Next Class](LSSerializerFilter.md)**

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
