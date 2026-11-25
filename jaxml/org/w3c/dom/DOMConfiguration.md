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

- **[Prev Class](DocumentType.md)**
- **[Next Class](DOMError.md)**

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

**org.w3c.dom**

## **Interface DOMConfiguration**

-

  ------------------------------------------------------------------------

  **
  **

      public interface DOMConfiguration

  **The `DOMConfiguration` interface represents the configuration of a document and maintains a table of recognized parameters. Using the configuration, it is possible to change `Document.normalizeDocument()` behavior, such as replacing the `CDATASection` nodes with `Text` nodes or specifying the type of the schema that must be used when the validation of the `Document` is requested. `DOMConfiguration` objects are also used in \[[DOM Level 3 Load and Save](http://www.w3.org/TR/2003/CR-DOM-Level-3-LS-20031107)\] in the `DOMParser` and `DOMSerializer` interfaces.**
  **The parameter names used by the `DOMConfiguration` object are defined throughout the DOM Level 3 specifications. Names are case-insensitives. To avoid possible conflicts, as a convention, names referring to parameters defined outside the DOM specification should be made unique. Because parameters are exposed as properties in the , names are recommended to follow the section 5.16 Identifiers of \[Unicode\] with the addition of the character '-' (HYPHEN-MINUS) but it is not enforced by the DOM implementation. DOM Level 3 Core Implementations are required to recognize all parameters defined in this specification. Some parameter values may also be required to be supported by the implementation. Refer to the definition of the parameter to know if a value must be supported or not.**

  **Note: Parameters are similar to features and properties used in SAX2 \[[SAX](http://www.saxproject.org/)\].**

  The following list of parameters defined in the DOM:

  `"canonical-form"`
  `true`
  \[*optional*\]Canonicalize the document according to the rules specified in \[[Canonical XML](http://www.w3.org/TR/2001/REC-xml-c14n-20010315)\]. Note that this is limited to what can be represented in the DOM. In particular, there is no way to specify the order of the attributes in the DOM.This forces the following parameters to `false`: "entities ", "normalize-characters", "cdata-sections".This forces the following parameters to `true`: "namespaces", "namespace-declarations", " well-formed", "element-content-whitespace".Other parameters are not changed unless explicitly specified in the description of the parameters. In addition, the `DocumentType` node is removed from the tree if any and superfluous namespace declarations are removed from each element. Note that querying this parameter with `getParameter` cannot return `true` unless it has been set to `true` and the parameters described above are appropriately set.

  `false`
  \[*required*\] (*default*)Do not canonicalize the document.

  `"cdata-sections"`
  `true`
  \[*required*\] (*default*)Keep `CDATASection` nodes in the document.

  `false`
  \[*required*\]Transform `CDATASection` nodes in the document into `Text` nodes. The new `Text` node is then combined with any adjacent `Text` node.

  `"check-character-normalization"`
  `true`
  \[*optional*\] Check if the characters in the document are fully normalized according to the rules defined in \[[CharModel](http://www.w3.org/TR/2003/WD-charmod-20030822/)\] supplemented by the definitions of relevant constructs from [Section 2.13](http://www.w3.org/TR/2003/PR-xml11-20031105/#sec-normalization-checking) of \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\].

  `false`
  \[*required*\] (*default*)Do not check if characters are normalized.

  `"comments"`
  `true`
  \[*required*\] (*default*)Keep `Comment` nodes in the document.

  `false`
  \[*required*\]Discard `Comment` nodes in the document.

  `"datatype-normalization"`
  `true`
  \[*optional*\] Exposed schema-normalized values in the tree. Since this parameter requires to have schema information, the "validate" parameter will also be set to `true`. Having this parameter activated when "validate" is `false` has no effect and no schema-normalization will happen.

  **Note:** Since the document contains the result of the XML 1.0 processing, this parameter does not apply to attribute value normalization as defined in section 3.3.3 of \[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\] and is only meant for schema languages other than Document Type Definition (DTD).

  `false`
  \[*required*\] (*default*) Do not perform schema normalization on the tree.

  `"entities"`
  `true`
  \[*required*\] (*default*)Keep `EntityReference` and `Entity` nodes in the document.

  `false`
  \[*required*\] Remove all `EntityReference` and `Entity` nodes from the document, putting the entity expansions directly in their place. `Text` nodes are normalized, as defined in `Node.normalize`. Only `EntityReference` nodes to non-defined entities are kept in the document, with their associated `Entity` nodes if any.

  `"error-handler"`
  \[*required*\] Contains a `DOMErrorHandler` object. If an error is encountered in the document, the implementation will call back the `DOMErrorHandler` registered using this parameter. The implementation may provide a default `DOMErrorHandler` object. When called, `DOMError.relatedData` will contain the closest node to where the error occurred. If the implementation is unable to determine the node where the error occurs, `DOMError.relatedData` will contain the `Document` node. Mutations to the document from within an error handler will result in implementation dependent behavior.

  `"infoset"`
  `true`
  \[*required*\]Keep in the document the information defined in the XML Information Set \[[XML Information Set](http://www.w3.org/TR/2001/REC-xml-infoset-20011024/)\] .This forces the following parameters to `false`: " validate-if-schema", "entities", "datatype-normalization", "cdata-sections ".This forces the following parameters to `true`: " namespace-declarations", "well-formed", "element-content-whitespace", " comments", "namespaces".Other parameters are not changed unless explicitly specified in the description of the parameters. Note that querying this parameter with `getParameter` returns `true` only if the individual parameters specified above are appropriately set.

  `false`
  Setting `infoset` to `false` has no effect.

  `"namespaces"`
  `true`
  \[*required*\] (*default*) Perform the namespace processing as defined in .

  `false`
  \[*optional*\] Do not perform the namespace processing.

  `"namespace-declarations"`
  `true`
  \[*required*\] (*default*) Include namespace declaration attributes, specified or defaulted from the schema, in the document. See also the sections "Declaring Namespaces" in \[[XML Namespaces](http://www.w3.org/TR/1999/REC-xml-names-19990114/)\] and \[[XML Namespaces 1.1](http://www.w3.org/TR/2003/PR-xml-names11-20031105/)\] .

  `false`
  \[*required*\]Discard all namespace declaration attributes. The namespace prefixes ( `Node.prefix`) are retained even if this parameter is set to `false`.

  `"normalize-characters"`
  `true`
  \[*optional*\] Fully normalize the characters in the document according to the rules defined in \[[CharModel](http://www.w3.org/TR/2003/WD-charmod-20030822/)\] supplemented by the definitions of relevant constructs from [Section 2.13](http://www.w3.org/TR/2003/PR-xml11-20031105/#sec-normalization-checking) of \[[XML 1.1](http://www.w3.org/TR/2003/PR-xml11-20031105/)\].

  `false`
  \[*required*\] (*default*)Do not perform character normalization.

  `"schema-location"`
  \[*optional*\] Represent a `DOMString` object containing a list of URIs, separated by whitespaces (characters matching the [nonterminal production S](http://www.w3.org/TR/2000/REC-xml-20001006#NT-S) defined in section 2.3 \[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\]), that represents the schemas against which validation should occur, i.e. the current schema. The types of schemas referenced in this list must match the type specified with `schema-type`, otherwise the behavior of an implementation is undefined. The schemas specified using this property take precedence to the schema information specified in the document itself. For namespace aware schema, if a schema specified using this property and a schema specified in the document instance (i.e. using the `schemaLocation` attribute) in a schema document (i.e. using schema `import` mechanisms) share the same `targetNamespace`, the schema specified by the user using this property will be used. If two schemas specified using this property share the same `targetNamespace` or have no namespace, the behavior is implementation dependent. If no location has been provided, this parameter is `null`.

  **Note:** The `"schema-location"` parameter is ignored unless the "schema-type" parameter value is set. It is strongly recommended that `Document.documentURI` will be set so that an implementation can successfully resolve any external entities referenced.

  `"schema-type"`
  \[*optional*\] Represent a `DOMString` object containing an absolute URI and representing the type of the schema language used to validate a document against. Note that no lexical checking is done on the absolute URI. If this parameter is not set, a default value may be provided by the implementation, based on the schema languages supported and on the schema language used at load time. If no value is provided, this parameter is `null`.

  **Note:** For XML Schema \[[XML Schema Part 1](http://www.w3.org/TR/2001/REC-xmlschema-1-20010502/)\] , applications must use the value `"http://www.w3.org/2001/XMLSchema"`. For XML DTD \[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\], applications must use the value `"http://www.w3.org/TR/REC-xml"`. Other schema languages are outside the scope of the W3C and therefore should recommend an absolute URI in order to use this method.

  `"split-cdata-sections"`
  `true`
  \[*required*\] (*default*)Split CDATA sections containing the CDATA section termination marker '\]\]\>'. When a CDATA section is split a warning is issued with a `DOMError.type` equals to `"cdata-sections-splitted"` and `DOMError.relatedData` equals to the first `CDATASection` node in document order resulting from the split.

  `false`
  \[*required*\]Signal an error if a `CDATASection` contains an unrepresentable character.

  `"validate"`
  `true`
  \[*optional*\] Require the validation against a schema (i.e. XML schema, DTD, any other type or representation of schema) of the document as it is being normalized as defined by \[[XML 1.0](http://www.w3.org/TR/2000/REC-xml-20001006)\]. If validation errors are found, or no schema was found, the error handler is notified. Schema-normalized values will not be exposed according to the schema in used unless the parameter "datatype-normalization" is `true`. This parameter will reevaluate:

  - Attribute nodes with `Attr.specified` equals to `false`, as specified in the description of the `Attr` interface;
  - The value of the attribute `Text.isElementContentWhitespace` for all `Text` nodes;
  - The value of the attribute `Attr.isId` for all `Attr` nodes;
  - The attributes `Element.schemaTypeInfo` and `Attr.schemaTypeInfo`.

  **Note:** "validate-if-schema" and "validate" are mutually exclusive, setting one of them to `true` will set the other one to `false`. Applications should also consider setting the parameter "well-formed" to `true`, which is the default for that option, when validating the document.

  `false`
  \[*required*\] (*default*) Do not accomplish schema processing, including the internal subset processing. Note that validation might still happen if " "validate-if-schema" is `true`.

  `"validate-if-schema"`
  `true`
  \[*optional*\]Enable validation only if a declaration for the document element can be found in a schema (independently of where it is found, i.e. XML schema, DTD, or any other type or representation of schema). If validation is enabled, this parameter has the same behavior as the parameter "validate" set to `true`.

  **Note:** "validate-if-schema" and "validate" are mutually exclusive, setting one of them to `true` will set the other one to `false`.

  `false`
  \[*required*\] (*default*) No schema processing should be performed if the document has a schema, including internal subset processing. Note that validation must still happen if "validate" is `true`.

  `"well-formed"`
  `true`
  \[*required*\] (*default*) Check if all nodes are XML well formed according to the XML version in use in `Document.xmlVersion`:

  - check if the attribute `Node.nodeName` contains invalid characters according to its node type and generate a `DOMError` of type `"wf-invalid-character-in-node-name"`, with a `DOMError.SEVERITY_ERROR` severity, if necessary;
  - check if the text content inside `Attr`, `Element`, `Comment`, `Text`, `CDATASection` nodes for invalid characters and generate a `DOMError` of type `"wf-invalid-character"`, with a `DOMError.SEVERITY_ERROR` severity, if necessary;
  - check if the data inside `ProcessingInstruction` nodes for invalid characters and generate a `DOMError` of type `"wf-invalid-character"`, with a `DOMError.SEVERITY_ERROR` severity, if necessary;

  `false`
  \[*optional*\] Do not check for XML well-formedness.

  `"element-content-whitespace"`
  `true`
  \[*required*\] (*default*)Keep all whitespaces in the document.

  `false`
  \[*optional*\] Discard all `Text` nodes that contain whitespaces in element content, as described in [\[element content whitespace\]](http://www.w3.org/TR/2001/REC-xml-infoset-20011024#infoitem.character). The implementation is expected to use the attribute `Text.isElementContentWhitespace` to determine if a `Text` node should be discarded or not.

  The resolution of the system identifiers associated with entities is done using `Document.documentURI`. However, when the feature "LS" defined in \[[DOM Level 3 Load and Save](http://www.w3.org/TR/2003/CR-DOM-Level-3-LS-20031107)\] is supported by the DOM implementation, the parameter "resource-resolver" can also be used on `DOMConfiguration` objects attached to `Document` nodes. If this parameter is set, `Document.normalizeDocument()` will invoke the resource resolver instead of using `Document.documentURI`.

  See also the [Document Object Model (DOM) Level 3 Core Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107).

  Since:
  DOM Level 3

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                   | Method and Description                                                                                                                                            |
    |-------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                           | `canSetParameter``(java.lang.String name, java.lang.Object value)`<br>Check if setting a parameter to a specific value is supported.                              |
    | `java.lang.Object`                  | `getParameter``(java.lang.String name)`<br>Return the value of a parameter if known.                                                                              |
    | [`DOMStringList`](DOMStringList.md) | `getParameterNames``()`<br>The list of the parameters supported by this `DOMConfiguration` object and for which at least one value can be set by the application. |
    | `void`                              | `setParameter``(java.lang.String name, java.lang.Object value)`<br>Set the value of a parameter.                                                                  |

<!-- -->

- - ### Method Detail

    - #### setParameter

          void setParameter(java.lang.String name,
                            java.lang.Object value)
                     throws DOMException

      Set the value of a parameter.
      Parameters:
      `name` - The name of the parameter to set.

      `value` - The new value or `null` if the user wishes to unset the parameter. While the type of the value parameter is defined as `DOMUserData`, the object type must match the type defined by the definition of the parameter. For example, if the parameter is "error-handler", the value must be of type `DOMErrorHandler`.

      Throws:
      [`DOMException`](DOMException.md) - NOT_FOUND_ERR: Raised when the parameter name is not recognized.
      NOT_SUPPORTED_ERR: Raised when the parameter name is recognized but the requested value cannot be set.
      TYPE_MISMATCH_ERR: Raised if the value type for this parameter name is incompatible with the expected value type.

    <!-- -->

    - #### getParameter

          java.lang.Object getParameter(java.lang.String name)
                                 throws DOMException

      Return the value of a parameter if known.
      Parameters:
      `name` - The name of the parameter.

      Returns:
      The current object associated with the specified parameter or `null` if no object has been associated or if the parameter is not supported.

      Throws:
      [`DOMException`](DOMException.md) - NOT_FOUND_ERR: Raised when the parameter name is not recognized.

    <!-- -->

    - #### canSetParameter

          boolean canSetParameter(java.lang.String name,
                                  java.lang.Object value)

      Check if setting a parameter to a specific value is supported.
      Parameters:
      `name` - The name of the parameter to check.

      `value` - An object. if `null`, the returned value is `true`.

      Returns:
      `true` if the parameter could be successfully set to the specified value, or `false` if the parameter is not recognized or the requested value is not supported. This does not change the current value of the parameter itself.

    <!-- -->

    - #### getParameterNames

          DOMStringList getParameterNames()

      The list of the parameters supported by this `DOMConfiguration` object and for which at least one value can be set by the application. Note that this list can also contain parameter names defined outside this specification.

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

- **[Prev Class](DocumentType.md)**
- **[Next Class](DOMError.md)**

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

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
