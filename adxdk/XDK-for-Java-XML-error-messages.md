Error messages are listed for applications that use Oracle XML Developer's Kit (XDK) for Java during the execution of Extensible Markup Language (XML) interfaces.

### A.1 XML Parser Error Messages

Extensible Markup Language (XML) parser error messages are in the range XML-20000 through XML-20999.

#### XML-20003: missing token string at line string, column string

Cause: An expected token was not found in the input data.

Action: Check/update the input data to fix the syntax error.

#### XML-20004: missing keyword string at line string, column string

Cause: An expected keyword was not found in the input data.

Action: Check/update the input data to the correct keyword.

#### XML-20005: missing keyword string or string at line string, column string

Cause: An expected keyword was not found in the input data.

Action: Check/update the input data to the correct keyword.

#### XML-20006: unexpected text at line string, column string; expected EOF

Cause: More text was found after the end-tag of the root element.

Action: The end-tag of the root element can be followed only by comments, PI, or white space. Remove the extra text after the end-tag.

#### XML-20007: missing content model in element declaration at line string, column string

Cause: The element declaration was missing the required content model spec. See Production \[45\] in XML 1.0 2nd Edition.

Action: Add the required content spec to the element declaration.

#### XML-20008: missing element name in content model at line string, column string

Cause: The content model in the element declaration was invalid, the content particle requires an element name. See Production \[48\] in XML 1.0 2nd Edition.

Action: Add the element name to fix the content spec syntactically.

#### XML-20009: target name string of processing instruction at line string, column string is reserved

Cause: The target names `"XML: xml"`, and so on are reserved for standardization in future versions of XML specification. See Production \[17\] in XML 1.0 2nd Edition.

Action: If the PI is meant to be XML declaration, make sure the declaration occurs at the very beginning of the file. Otherwise, change to name of the PI.

#### XML-20010: missing notation name in unparsed entity declaration at line string, column string

Cause: The notation name used in the unparsed entity declaration did not match the name in a declared notation. See Production \[76\] in XML 1.0 2nd Edition.

Action: Add the notation declaration to the DTD.

#### XML-20011: missing attribute type in attribute-list declaration at line string, column string

Cause: The attribute type was missing the attribute-list declaration. One of these types CDATA, ID, IDREF, IDREFS, ENTITY, ENTITIES, NMTOKEN, or NMTOKENS must be added. See Production \[52\], \[53\] in XML 1.0 2nd Edition.

Action: Check and correct attribute declaration.

#### XML-20012: missing white space at line string, column string

Cause: The required white space was missing.

Action: Add white space to fix the syntax error.

#### XML-20013: invalid character string in entity value at line string, column string

Cause: An invalid character was used in the entity value. Characters `&`, `%`, and either `"` or `'` (based on the value delimiters) are invalid. See Production \[9\] in XML 1.0 2nd Edition.

Action: Use entity or character references instead of the characters For example, `&amp;` or `&#38;` can be used instead of `&`.

#### XML-20014: -- not allowed in comment at line string, column string

Cause: A syntax error in comment due to the use of "--"See Production \[15\] in XML 1.0 2nd Edition.

Action: Fix the comment, and use `--` only as part of end of comment `-->`

#### XML-20015: \]\> not allowed in text at line string, column string

Cause: `]>` is not allowed in text. It is used only as end marker for CDATA Section. See Production \[14\] in XML 1.0 2nd Edition.

Action: Fix the text content by using `&gt;` or char ref for `>`.

#### XML-20016: white space not allowed before occurrence indicator at line string, column string

Cause: White space is not allowed in the contentspec before the occurrence indicator. For example, `<!ELEMENT x (a,b) *>` is not valid. See Production \[47\], \[48\] in XML 1.0 2nd Edition.

Action: Fix the contentspec by removing the extra space

#### XML-20017: occurrence indicator string not allowed in mixed-content at line string, column string

Cause: Occurrence is not allowed in mixed content declaration. For example, `<!ELEMENT x (#PCDATA)?>` is not valid. See Production \[51\] in XML 1.0 2nd Edition.

Action: Fix the syntax to remove the occurrence indicator.

#### XML-20018: content list not allowed inside mixed-content at line string, column string

Cause: Content list is not allowed in mixed-content declaration. For example, `<!ELEMENT x (#PCDATA | (a,b))>` is not valid. See Production \[51\] in XML 1.0 2nd Edition.

Action: Fix the syntax to remove the content list.

#### XML-20019: duplicate element string in mixed-content declaration at line string, column string

Cause: Duplicate element name was found in mixed-content declaration. For example, `<!ELEMENT x (#PCDATA | a | a)>` is not valid. See Production \[51\] in XML 1.0 2nd Edition

Action: Remove the duplicate element name.

#### XML-20020: root element string does not match the DOCTYPE name string at line string, column string

Cause: failed: The name in the document type declaration must match the element type of the root element. For example: `<?xml version="1.0"?> <!DOCTYPE ``greeting`` [ <!ELEMENT ``greeting`` (#PCDATA)> ]> <``salutation``>Hello!</``salutation``>`. The document's root element, `salutation`, does not match the root element declared in the DTD (`greeting`).

Action: Correct the document.

#### XML-20021: duplicate element declaration string at line string, column string

Cause: Element was declared twice in the DTD.

Action: Remove the duplicate declaration.

#### XML-20022: element string has multiple ID attributes at line string, column string

Cause: failed: No element type may have more than one ID attribute specified.

Action: Correct the document, by removing the duplicate ID attribute `decl`.

#### XML-20023: ID attribute string in element string must be \#IMPLIED or \#REQUIRED at line string, column string

Cause: failed: An ID attribute must have a declared default of `#IMPLIED` or `#REQUIRED`.

Action: Fix the attribute declaration.

#### XML-20024: missing required attribute string in element string at line string, column string

Cause: failed: If the default declaration is the keyword `#REQUIRED`, then the attribute must be specified for all elements of the type in the attribute-list declaration.

Action: Fix the input document by specifying the required attribute.

#### XML-20025: duplicate ID value: string

Cause: Values of type ID must match the Name production. A name must not appear more than once in an XML document as a value of this type; thus, ID values must uniquely identify the elements which bear them.

Action: Fix the input document by removing the duplicate ID value.

#### XML-20026: undefined ID value string in IDREF

Cause: failed "Values of type IDREF must match value of some ID attribute.

Action: Fix the document by adding an ID corresponding the to the IDREF, or removing the IDREF.

#### XML-20027: attribute string in element string has invalid enumeration value string at line string, column string

Cause: failed: Values of this type must match one of the Nmtoken tokens in the declaration.

Action: Fix the attribute value to match one of the enumerated values.

#### XML-20028: attribute string in element string has invalid value string, must be string at line string, column {5}

Cause: failed: If an attribute has a default value declared with the `#FIXED` keyword, instances of that attribute must match the default value.

Action: Update the attribute value to match the fixed default value.

#### XML-20029: attribute default must be REQUIRED, IMPLIED, or FIXED at line string, column string

Cause: The declared default value must meet the lexical constraints o the declared attribute type.

Action: Use one of `REQUIRED`, `IMPLIED`, or `FIXED` for attribute default `decl`.

#### XML-20030: invalid text in content of element string at line string, column string

Cause: The element does not allow text in content. An element is valid if there is a declaration matching element `decl` where the Name matches the element type, and one of these holds:

The declaration matches children and the sequence of child elements belongs to the language generated by the regular expression in the content model, with optional white space (characters matching the nonterminal S) between the start-tag and the first child element, between child elements, or between the last child element and the end-tag. A CDATA section containing only white space does not match the nonterminal S, and hence cannot appear in these positions.

Action: Fix the content by removing unexpected text.

#### XML-20031: invalid element string in content of element string at line string, column string

Cause: The element has invalid content. An element is valid if there is a declaration matching element `decl` where the Name matches the element type, and one of these holds:

1.  The declaration matches children and the sequence of child elements belongs to the language generated by the regular expression in the content model, with optional white space (characters matching the nonterminal S) between the start-tag and the first child element, between child elements, or between the last child element and the end-tag. A CDATA section containing only white space does not match the nonterminal S, and hence cannot appear in these positions.

2.  The declaration matches Mixed and the content consists of character data and child elements whose types match names in the content model.

Action: Fix the content by removing unexpected elements.

#### XML-20032: incomplete content in element string at line string, column string

Cause: The element has invalid content. An element is valid if there is a declaration matching element `decl` where the Name matches the element type, and one of these holds:

1.  The declaration matches children and the sequence of child elements belongs to the language generated by the regular expression in the content model, with optional white space (characters matching the nonterminal S) between the start-tag and the first child element, between child elements, or between the last child element and the end-tag. A CDATA section containing only white space does not match the nonterminal S, and hence cannot appear in these positions.

2.  The declaration matches Mixed and the content consists of character data and child elements whose types match names in the content model.

Action: Fix the content by removing unexpected elements.

#### XML-20033: invalid replacement-text for entity string at line string, column string

Cause: Parameter-entity replacement text must be properly nested with markup declarations. That is to say, if either the first character or the last character of a markup declaration (markup `decl` above) is contained in the replacement text for a parameter-entity reference, both must be contained in the same replacement text.

Action: Fix the entity value.

#### XML-20034: end-element tag string does not match start-element tag string at line string, column string

Cause: The Name in an element's end-tag must match the element type in the start-tag.

Action: Fix the end-tag or start-tag to match the other.

#### XML-20035: duplicate attribute string in element string at line string, column string

Cause: No attribute name may appear more than once in the same start-tag or empty-element tag.

Action: Remove the duplicate attribute.

#### XML-20036: invalid character string in attribute value at line string, column string

Cause: An invalid character was used in the attribute value, the characters `&`, `<`, and either `"` or `'` (based on the value delimiters) are invalid. See Production \[10\] in XML 1.0 2nd Edition.

Action: Use entity or character references instead of the characters For example, `&amp;` or `&#38;` can be used instead of `&`.

#### XML-20037: invalid reference to external entity string in attribute string at line string, column string

Cause: Attribute values cannot contain direct or indirect entity references to external entities.

Action: Fix document to remove reference to external entity in attribute.

#### XML-20038: invalid reference to unparsed entity string in element string at line string, column string

Cause: An entity reference must not contain the name of an unparsed entity. Unparsed entities may be referenced only in attribute values declared to be of type ENTITY or ENTITIES.

Action: Fix document to remove reference to unparsed entity in content.

#### XML-20039: invalid attribute type string in attribute-list declaration at line string, column string

Cause: Invalid attribute type was used in the attribute-list declaration. One of these types CDATA, ID, IDREF, IDREFS, ENTITY, ENTITIES, NMTOKEN, or NMTOKENS must be added. See Production \[52\], \[53\] in XML 1.0 2nd Edition.

Action: Check and correct attribute declaration.

#### XML-20040: invalid character string in element content at line string, column string

Cause: Characters referred to using character references must match the production for Char.

Action: Fix the document by removing the invalid character or char-ref.

#### XML-20041: entity reference string refers to itself at line string, column string

Cause: A parsed entity must not contain a recursive reference to itself, either directly or indirectly.

Action: Fix the document.

#### XML-20042: invalid Nmtoken: string

Cause: Values of this type must match one of the Nmtoken tokens in the declaration, and must be valid Nmtoken"

Action: Fix the attribute value.

#### XML-20043: invalid character string in public identifier at line string, column string

Cause: Invalid character used in public identifier. See Production \[12\], \[13\] in XML 1.0 2nd Edition.

Action: Fix the public identifier.

#### XML-20044: undeclared namespace prefix string used at line string, column string

Cause: The prefix was not defined in any namespace declaration in scope.

Action: Add a namespace declaration to define the prefix.

#### XML-20045: attribute string in element string must be an unparsed entity at line string, column string

Cause: Values of type ENTITY must match the Name production, values of type ENTITIES must match Names; each Name must match the name of an unparsed entity declared in the DTD.

Action: Fix the attribute value to refer to an unparsed entity.

#### XML-20046: undeclared notation string used in unparsed entity string at line string, column string

Cause: Values of this type must match one of the notation names included in the declaration; all notation names in the declaration must be declared.

Action: Fix the notation name in the unparsed entity declaration.

#### XML-20047: missing element declaration string

Cause: The element declaration referred to by an attribute declaration was not found in the DTD.

Action: Fix the DTD by adding the element declaration.

#### XML-20048: duplicate entity declaration string at line string, column string

Cause: Warning regarding duplicate entity declaration.

Action: No action required.

#### XML-20049: invalid use of NDATA in parameter entity declaration at line string, column string

Cause: `NDATA` declaration was found in parameter entity declaration. It is allowed only in general unparsed entity declaration. See Production \[72\], \[74\] in XML 1.0 2nd Edition.

Action: Fix the entity declaration.

#### XML-20050: duplicate attribute declaration string at line string, column string

Cause: Warning regarding duplicate attribute declaration.

Action: No action required.

#### XML-20051: duplicate notation declaration string at line string, column string

Cause: Only one notation declaration can declare a given Name.

Action: Fix the document by removing the duplicate notation.

#### XML-20052: undeclared attribute string used at line string, column string

Cause: The attribute declaration was not found in the DTD.

Action: Fix the DTD by adding the attribute declaration.

#### XML-20053: undeclared element string used at line string, column string

Cause: The element declaration was not found in the DTD.

Action: Fix the DTD by adding the element declaration.

#### XML-20054: undeclared entity string used at line string, column string

Cause: The entity declaration was not found in the DTD.

Action: Fix the DTD by adding the element declaration.

#### XML-20055: invalid document returned by NodeFactory's createDocument

Cause: The document returned by `createDocument` function of `NodeFactory` was invalid, either it was null or instance of an unsupported class.

Action: Fix `NodeFactory` implementation to return an instance of `XMLDocument` or its subclass.

#### XML-20056: invalid SAX feature string

Cause: The SAX feature supplied was not a valid feature name.

Action: See the documentation for a valid list of features.

#### XML-20057: invalid value string passed for SAX feature string

Cause: The value supplied for the SAX feature was not valid.

Action: See the documentation for a valid list of features and their corresponding values.

#### XML-20058: invalid SAX property string

Cause: The SAX property supplied was not a valid property name.

Action: See the documentation for a valid list of properties.

#### XML-20059: invalid value passed for SAX property string

Cause: The value supplied for the SAX property was not valid.

Action: See the documentation for a valid list of properties and their corresponding values

#### XML-20060: Error occurred while opening URL string

Cause: An error occurred while opening the supplied URL.

Action: Verify the URL, and take appropriate action to allow data to be read.

#### XML-20061: invalid byte stream string in UTF8 encoded data

Cause: The input data contained bytes that are not valid with respect to UTF-8 encoding scheme.

Action: Fix the input data.

#### XML-20062: 5-byte UTF8 encoding not supported

Cause: The XML Parser does not support 5-byte UTF-8 encoding scheme. It is also possible that invalid UTF-8 characters were misinterpreted as 5-byte UTF-8 encoding.

Action: If the data contains invalid UTF-8 bytes, fix the input, otherwise if 5-byte UTF-8 supported is required, contact Oracle Support.

#### XML-20063: 6-byte UTF8 encoding not supported

Cause: The XML Parser does not support 6-byte UTF-8 encoding scheme. It is also possible that invalid UTF-8 characters were misinterpreted as 6-byte UTF-8 encoding.

Action: If the data contains invalid UTF-8 bytes, fix the input, otherwise if 6-byte UTF-8 supported is required, contact Oracle Support.

#### XML-20064: invalid XML character string

Cause: Invalid XML character was found in the input data.

Action: Fix the input data.

#### XML-20065: encoding string doesn't match encoding string in XML declaration

Cause: The encoding of the data (either by auto-detection or user supplied)didn't match the encoding specified in the XML declaration.

Action: Fix the XML declaration to match the encoding of the data.

#### XML-20066: encoding string not supported

Cause: The XML Parser does not support the specified encoding.

Action: If the support for the encoding is required, contact Oracle Support.

#### XML-20067: invalid InputSource returned by EntityResolver's resolveEntity

Cause: An invalid instance of `InputSource` was returned by the `EntityResolverAn` `InputSource` can be invalid if the none of `Reader`, `InputStream`, and `SystemId` were initialized or if the `SystemId` was invalid.

Action: Fix the `EntityResolver` class to return a valid instance of `InputSource`.

#### XML-20100: Expected string.

#### XML-20101: Expected string or string.

#### XML-20102: Expected string, string, or string.

#### XML-20103: Illegal token in content model.

#### XML-20104: Could not find element with ID string.

#### XML-20105: ENTITY type Attribute value string does not match any unparsed Entity.

#### XML-20106: Could not find Notation string.

#### XML-20107: Could not find declaration for element string.

#### XML-20108: Start of root element expected.

#### XML-20109: PI with the name 'xml' can occur only in the beginning of the document.

#### XML-20110: \#PCDATA expected in mixed-content declaration.

#### XML-20111: Element string repeated in mixed-content declaration.

#### XML-20112: Error opening external DTD string.

#### XML-20113: Unable to open input source (string).

#### XML-20114: Bad conditional section start syntax, expected '\['.

#### XML-20115: Expected '\]\>' to end conditional section.

#### XML-20116: Entity string already defined, using the first definition.

#### XML-20117: NDATA not allowed in parameter entity declaration.

#### XML-20118: NDATA value required.

#### XML-20119: Entity Value should start with quote.

#### XML-20120: Entity value not well-formed.

#### XML-20121: End tag does not match start tag string.

#### XML-20122: '=' missing in attribute.

#### XML-20123: '\>' Missing from end tag.

#### XML-20124: An attribute cannot appear more than once in the same start tag.

#### XML-20125: Attribute value should start with quote.

#### XML-20126: '\<' cannot appear in attribute value.

#### XML-20127: Reference to an external entity not allowed in attribute value.

#### XML-20128: Reference to unparsed entity not allowed in element content.

#### XML-20129: Namespace prefix string used but not declared.

#### XML-20130: Root element name must match the DOCTYPE name.

#### XML-20131: Element string already declared.

#### XML-20132: Element cannot have more than one ID attribute.

#### XML-20133: Attr type missing.

#### XML-20134: ID attribute must be declared \#IMPLIED or \#REQUIRED.

#### XML-20135: Attribute string already defined, using the first definition.

#### XML-20136: Notation string already declared.

#### XML-20137: Attribute string used but not declared.

#### XML-20138: REQUIRED attribute string is not specified.

#### XML-20139: ID value string is not unique.

#### XML-20140: IDREF value string does not match any ID attribute value.

#### XML-20141: Attribute value string should be one of the declared enumerated values.

#### XML-20142: Unknown attribute type.

#### XML-20143: Unrecognized text at end of attribute value.

#### XML-20144: FIXED type Attribute value not equal to the default value string.

#### XML-20145: Unexpected text in content of Element string.

#### XML-20146: Unexpected text in content of Element string, expected elements string.

#### XML-20147: Invalid element string in content of string, expected closing tag.

#### XML-20148: Invalid element string in content of string, expected elements string.

#### XML-20149: Element string used but not declared.

#### XML-20150: Element string not complete, expected elements string.

#### XML-20151: Entity string used but not declared.

#### XML-20170: Invalid UTF8 encoding.

#### XML-20171: Invalid XML character(string).

#### XML-20172: 5-byte UTF8 encoding not supported.

#### XML-20173: 6-byte UTF8 encoding not supported.

#### XML-20180: User Supplied NodeFactory returned a Null Pointer.

#### XML-20190: Whitespace required.

#### XML-20191: '\>' required to end DTD.

#### XML-20192: Unexpected text in DTD.

#### XML-20193: Unexpected EOF.

#### XML-20194: Unable to write to output stream.

#### XML-20195: Encoding not supported in PrintWriter.

#### XML-20200: Expected string instead of string.

#### XML-20201: Expected string instead of string.

#### XML-20202: Expected string to be string.

#### XML-20205: Expected string.

#### XML-20206: Expected string or string.

#### XML-20210: Unexpected string.

#### XML-20211: string is not allowed in string.

#### XML-20220: Invalid InputSource.

#### XML-20221: Invalid char in text.

#### XML-20230: Illegal change of encoding: from string to string.

#### XML-20240: Unable to open InputSource.

#### XML-20241: Unable to open entity string.

#### XML-20242: Error opening external DTD string.

#### XML-20250: Missing entity string.

#### XML-20251: Cyclic Entity Reference in entity string.

#### XML-20280: Bad character (string).

#### XML-20281: NMToken must contain atleast one NMChar.

#### XML-20282: string not allowed in a PubIdLiteral.

#### XML-20284: Illegal white space before optional character in content model.

#### XML-20285: Illegal mixed content model.

#### XML-20286: Content list not allowed inside mixed content model.

#### XML-20287: Content particles not allowed inside mixed content model.

#### XML-20288: Invalid default declaration in attribute declaration.

#### XML-20500: SAX feature string not recognized.

#### XML-20501: SAX feature string not supported.

#### XML-20502: SAX property string not recognized.

#### XML-20503: SAX property string not supported.

### A.2 DOM Error Messages

DOM error messages are described.

Document Object Model (DOM) error messages are in the range XML-21000 through XML-21999.

#### XML-21000: invalid size string specified

Cause: An invalid size or count was passed to a DOM function.

Action: Correct the argument passed to a valid value.

#### XML-21001: invalid index string specified; must be between 0 and string

Cause: An invalid index was passed to a DOM function.

Action: Correct the argument passed to a valid value specified by the bounds in the error messag

#### XML-21002: cannot add an ancestor as a child node

Cause: The DOM operation was trying to a add an ancestor node as a child. This can lead to inconsistencies in the tree, so it is not allowed.

Action: Check the application to fix the usage.

#### XML-21003: node of type string cannot be added to node of type string

Cause: The DOM specification does not allow the parent-child combinationused in the DOM operation.

Action: See the DOM specification to fix the usage.

XML-21004: document node can have only one string node as child

Cause: The XML well-formedness requires that the document node have onlyone element node as its child. The application tried adding addinga second element node.

Action: Fix usage in the application.

#### XML-21005: node of type string cannot be added to attribute list

Cause: The attribute list (instance of NamedNodeMap) can contain onlyattribute nodes.

Action: Fix usage of NamedNodeMap.

#### XML-21006: cannot add a node belonging to a different document

Cause: The node being added was created by a different document. The DOMspecification does not allow use of nodes across documents.

Action: Use importNode or adoptNode to move a node from one document to another, before adding it.

#### XML-21007: invalid character string in name

Cause: The qualified or local name passed was invalid.

Action: Fix the name to contain only valid

#### XML-21008: cannot set value for node of type string

Cause: The node of the specified type cannot have value.

Action: Fix usage of DOM functions.

#### XML-21009: cannot modify descendants of entity or entity reference nodes

Cause: The descendants of entity or entity reference nodes are read-onlynodes, and modification is not allowed.

Action: Fix usage of DOM functions.

#### XML-21010: cannot modify DTD's content

Cause: DTD and all its content is read-only and cannot be modified.

Action: Fix usage of DOM functions.

#### XML-21011: cannot remove attribute; not found in the current element

Cause: An attempt was made to remove an attribute that does not belong thecurrent element.

Action: Fix usage in application.

#### XML-21012: cannot remove or replace node; it is not a child of the current node

Cause: An attempt was made to remove an node that does not belong thecurrent node as a child.

Action: Fix usage in application.

#### XML-21013: parameter string not recognized

Cause: The DOM parameter was not recognized.

Action: See the documentation for a valid list of parameters.

#### XML-21014: value string of parameter string is not supported

Cause: The DOM parameter was not recognized.

Action: See the documentation for a valid list of parameters.

#### XML-21015: cannot add attribute belonging to another element

Cause: An attempt was made to add an attribute that belonged theanother element.

Action: Fix usage in application.

#### XML-21016: invalid namespace string for prefix string

Cause: The namespace for xml, and xmlns prefixes is fixed, and usage mustmatch these.

Action: Correct the namespace for the prefixes, namespaces are xml = http://www.w3.org/XML/1998/namespace xmlns = http://www.w3.org/2000/xmlns/

#### XML-21017: invalid qualified name: string

Cause: The qualified name passed to a DOM function was invalid.

Action: Fix the qualified name.

#### XML-21018: conflicting namespace declarations string and string for prefix string

Cause: The DOM tree has conflicting namespace declarations for the sameprefix. Such a DOM tree cannot be serialized.

Action: Fix the DOM tree, before printing it.

#### XML-21019: string object is detached

Cause: The object was detached, no operations are supported ona detached object. The object can be a Range or iterator object

Action: Fix the usage in application.

#### XML-21020: bad boundary specified; cannot partially select a node of type string

Cause: The boundary specified in the range was invalid. The selectioncan be partial only for text nodes.

Action: Fix the usage in the application.

#### XML-21021: node of type string does not support range operation string

Cause: The range operation is not supported on the node type specified.

Action: See the DOM documentation for restrictions of node types for each range operation.

#### XML-21022: invalid event type: string

Cause: The event type passed was invalid.

Action: Fix usage in the application.

#### XML-21023: prefix not allowed on nodes of type string

Cause: The application tried to set prefix on a node on which prefix is notallowed

Action: Fix usage in the application.

#### XML-21024: import not allowed on nodes of type string

Cause: The application tried to import a node of type DOCUMENT orDOCUMENT FRAGMENT.

Action: Fix usage in the application.

#### XML-21025: rename not allowed on nodes of type string

Cause: The application tried to import a node of type other than ELEMENT orATTRIBUTE.

Action: Fix usage in the application.

#### XML-21026: Unrepresentable character in node: string

Cause: A node contains an invalid character, eg. CDATA section contain a termination character.

Action: Set appropriate DOMConfiguration parameter.

#### XML-21027: Namespace normalization error in node: string

Cause: Namespace fixup cannot be performed on this node.

Action: Set namespace normalization to false.

#### XML-21997: function not supported on THICK DOM

Cause: A function on THICK (for example, XDB based) DOM which is not supported was called.

Action: See the XDK documentation for possible alternatives for functions not supported on THICK DOM.

#### XML-21998: system error occurred: string

Cause: Non-DOM related system errors occurred.

Action: Check with ORA error(s) embedded in the message and consult with developers for possible causes.

### A.3 XSLT Error Messages

Extensible Stylesheet Language Transformation (XSLT) error messages are in the range XML-22000 through XML-22999.

#### XML-22000: Error while parsing XSL file (string).

#### XML-22001: XSL Stylesheet does not belong to XSLT namespace.

#### XML-22002: Error while processing include XSL file (string).

#### XML-22003: Unable to write to output stream (string).

#### XML-22004: Error while parsing input XML document (string).

#### XML-22005: Error while reading input XML stream (string).

#### XML-22006: Error while reading input XML URL (string).

#### XML-22007: Error while reading input XML reader (string).

#### XML-22008: Namespace prefix string used but not declared.

#### XML-22009: Attribute string not found in string.

#### XML-22010: Element string not found in string.

#### XML-22011: Cannot construct XML PI with content: string.

#### XML-22012: Cannot construct XML comment with content: string.

#### XML-22013: Error in expression: string.

#### XML-22014: Expecting node-set before relative location path.

#### XML-22015: Function string not found.

#### XML-22016: Extension function namespace should start with string.

#### XML-22017: Literal expected in string function. Found string.

#### XML-22018: Parse Error in string function.

#### XML-22019: Expected string instead of string.

#### XML-22020: Error in extension function arguments.

#### XML-22021: Error parsing external document: string.

#### XML-22022: Error while testing predicates. Not a nodeset type.

#### XML-22023: Literal Mismatch.

#### XML-22024: Unknown multiply operator.

#### XML-22025: Expression error: Empty string.

#### XML-22026: Unknown expression at EOF: string.

#### XML-22027: Closing } not found in Attribute Value template.

#### XML-22028: Expression value type string not recognized by string.

#### XML-22029: Cannot transform child string in string.

#### XML-22030: Attribute value string not expected for string.

#### XML-22031: Variable not defined: string.

#### XML-22032: Found a single } outside expression in Attribute value template.

#### XML-22033: Token not recognized:!.

#### XML-22034: Namespace definition not found for prefix string.

#### XML-22035: Axis string not found

#### XML-22036: Cannot convert string to string.

#### XML-22037: Unsupported feature: string.

#### XML-22038: Expected Node-set in Path Expression.

#### XML-22039: Extension function error: Error invoking constructor for string

#### XML-22040: Extension function error: Overloaded constructors for string

#### XML-22041: Extension function error: Constructor not found for string

#### XML-22042: Extension function error: Overloaded method string

#### XML-22043: Extension function error: Method not found string

#### XML-22044: Extension function error: Error invoking string:string

#### XML-22045: Extension function error: Class not found string

#### XML-22046: Apply import cannot be called when current template is null.

#### XML-22047: Invalid instantiation of string in string context.

#### XML-22048: The string element children must precede all other element children of an string element.

#### XML-22049: Template string invoked but not defined.

#### XML-22050: Duplicate variable string definition.

#### XML-22051: only a literal or a reference to a variable or parameter is allowed in id() function when used as a pattern

#### XML-22052: no sort key named as: string was defined

#### XML-22053: cannot detect encoding in unparsed-text(), please specify

#### XML-22054: no such xsl:function with namespace: string and local name: string was defined

#### XML-22055: range expression can only accept xs:integer data type, but not string

#### XML-22056: exactly one of four group attributes must be present in xsl:for-each-group

#### XML-22057: string can only have string as children

#### XML-22058: wrong child of xsl:function

#### XML-22059: wrong child order of xsl:function

#### XML-22060: TERMINATE PROCESSING

#### XML-22061: teminate attribute in \<xsl:message\> can only be yes or no

#### XML-22062: string must have at least one string child

#### XML-22063: no definition for character-map with qname string

#### XML-22064: cannot define character-map with the same name string and the same import precedence

Cause: A required child was not found.

Action: After error `mesgfreeze` is over, throws an error (without the required child element, it can do nothing).

#### XML-22065: at least one string must be defined under string

Cause: A required child is missing.

Action: Without the required child, it can do nothing.

#### XML-22066: if select attribute is present, string instructions sequence-constructor must be empty

Cause: Attribute and sequence constructor `select` must be mutually exclusive for this instruction.

Action: None.

#### XML-22067: if use attribute is present, string instructions sequence-constructor must be empty

Cause: Attribute and sequence constructor `use` must be mutually exclusive for this instruction.

Action: None.

#### XML-22068: only primary sort key is allowed to have the stable attribute.

Cause: The secondary sort key has a stable attribute.

Action: None.

#### XML-22069: only string or string is allowed.

Cause: User typo.

Action: None.

#### XML-22101: DOMSource node as this type not supported.

#### XML-22103: DOMResult can not be this kind of node.

#### XML-22106: Invalid StreamSource - InputStream, Reader, and SystemId are null.

#### XML-22107: Invalid SAXSource - InputSource is null.

#### XML-22108: Invalid Source - URL format is incorrect.

#### XML-22109: Internal error while reporting SAX events.

#### XML-22110: Invalid StreamResult set in TransformerHandler.

#### XML-22111: Invalid Result set in TransformerHandler.

#### XML-22112: Namespace URI missing }.

#### XML-22113: Namespace URI should start with {.

#### XML-22117: URL format has problems (null or bad format or missing 'href' or missing '=').

#### XML-22121: Could not get associated stylesheet.

#### XML-22122: Invalid StreamResult - OutputStream, Writer, and SystemId are null.

#### XML-22900: An internal error condition occurred.

### A.4 XPath Error Messages

XPath error messages are in the range XML-23000 through XML-23999.

#### XML-23002: internal xpath error

Cause: This was an error returned by the XPath/XQuery datamodel or XPath F&O.

Action: Check the XPath expression.

#### XML-23003: XPath 2.0 feature schema-element/schema-attribute not supported

Cause: This error was caused by using the kindtest schema-element or schema-attribute. These are not supported for this release.

Action: Remove usage of schema-element or schema-attribute kindtest

#### XML-23006: value does not match required type

Cause: During the evaluation phase, there was a type error as the value did not match a required type specified by the matching rules in XPath 2.0 `SequenceType` matching.

Action: Modify the stylesheet to reflect the correct type.

#### XML-23007: FOAR0001: division by zero

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23008: FOAR0002: numeric operation overflow/unflow

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23009: FOCA0001: Error in casting to decimal

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23010: FOCA0002: invalid lexical value

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23011: FOCA0003: input value too large for integer

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23012: FOCA0004: Error in casting to integer

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23013: FOCA0005: NaN supplied as float/double value

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23014: FOCH0001: invalid codepoint

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23015: FOCH0002: unsupported collation

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23016: FOCH0003: unsupported normalization form

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23017: FOCH0004: collation does not support collation units

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23018: FODC0001: no context document

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23019: FODC0002: Error retrieving resource

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23020: FODC0003: Error parsing contents of resource

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23021: FODC0004: invalid argument to fn:collection()

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23022: FODT0001: overflow in date/time arithmetic

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23023: FODT0002: overflow in duration arithmetic

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23024: FONC0001: undefined context item

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23025: FONS0002: default namespace is defined

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23026: FONS0003: no prefix defined for namespace

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23027: FONS0004: no namespace found for prefix

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23028: FONS0005: base URI not defined in the static context

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23029: FORG0001: invalid value for cast/constructor

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23030: FORG0002: invalid argument to fn:resolve-uri()

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23031: FORG0003: zero-or-one called with sequence containing more than one item

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23032: FORG0004: fn:one-or-more called with sequence containing no items

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23033: FORG0005: exactly-one called with sequence containing zero or more than one item

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23034: FORG0006: invalid argument type

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23035: FORG0007: invalid argument to aggregate function

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23036: FORG0008: both arguments to fn:dateTime have a specified timezone

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23037: FORG0009: base uri argument to fn:resolve-uri is not an absolute URI

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23038: FORX0001: invalid regular expression flags

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23039: FORX0002: invalid regular expression

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23040: FORX0003: regular expression matches zero-length string

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23041: FORX0004: invalid replacement string

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23042: FOTY0001: type error

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23043: FOTY0011: context item is not a node

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23044: FOTY0012: items not comparable

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23045: FOTY0013: type does not have equality defined

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23046: FOTY0014: type exception

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23047: FORT0001: invalid number of parameters

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23048: FOTY0002: type definition not found

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23049: FOTY0021: invalid node type

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23050: FOER0000: unidentified error

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23051: FODC0005: invalid argument to fn:doc

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

#### XML-23052: FODT0003: invalid timezone value

Cause: This was an XPath 2.0 F&O specification error.

Action: Check the XPath expression.

### A.5 XML Schema Validation Error Messages

XML schema validation error messages are in the range XML-24000 through XML-24099.

#### XML-24000: internal error

Cause: An unexpected error occurred during processing.

Action: Report the error.

#### XML-24001: attribute string not expected at line string, column string

Cause: \[cvc-assess-attr.1\] The attribute were not expected for owner element.

Action: Add the attribute declaration to the type of the owner element.

#### XML-24002: can not find element declaration string.

Cause: \[cvc-assess-elt.1.1.1.1\]The element declaration required by processorfor validation was absent.

Action: Add the element declaration to schema, or change the instance document to comply to schema.

#### XML-24003: context-determined element declaration string absent.

Cause: \[cvc-assess-elt.1.1.1.2\] The element declaration required by context was missing in schema.

Action: Add the element declaration to schema.

#### XML-24004: declaration for element string absent.

Cause: \[cvc-assess-elt.1.1.1.3\] The context-determined declaration was not skip and the declaration that matches the element could not be found in schema.

Action: Add the element declaration to schema or change the context-determined declaration to skip.

#### XML-24005: element string not assessed

Cause: \[cvc-assess-elt.2\]

#### XML-24006: element string laxly assessed

Cause: \[cvc-assess-elt.2\]

#### XML-24007: missing attribute declaration stringin element string

Cause: \[cvc-attribute.1\] Attribute declaration was absent from element declaration.

Action: Add the attribute declaration to schema.

#### XML-24008: type absent for attribute string

Cause: \[cvc-attribute.2\] Missing type definition for the attribute declaration.

Action: Specify a data type for the attribute declaration.

#### XML-24009: invalid attribute value string

Cause: \[cvc-attribute.3\] Invalid attribute value with respect to its type.

Action: Correct the attribute value in instance.

#### XML-24010: attribute value string and fixed value string not match

Cause: \[cvc-au\] Attribute's normalized value was not the same as the fixed value declared.

Action: Change attribute value to the required value.

#### XML-24011: type of element string is abstract.

Cause: \[cvc-complex-type.1\] The type of this element was specified as abstract.

Action: Remove the abstract attribute from the type definition.

#### XML-24012: no children allowed for element string with empty content type

Cause: \[cvc-complex-type.2.1\] The content type was specified empty while the actual content was not.

Action: Make the content empty or modify the content type of this element.

#### XML-24013: element child string not allowed for simple content

Cause: \[cvc-complex-type.2.2\] Element was declared with simple content, but instance had element children.

Action: Use only character content for this element.

#### XML-24014: characters string not allowed for element-only content

Cause: \[cvc-complex-type.2.3\] Characters appeared in the content of element with element-only content.

Action: Use only element children for this element.

#### XML-24015: multiple ID attributes in element string at line string, column string

Cause: \[cvc-complex-type.2.5\] More than one attributes with type ID or its derivation matched attribute wildcard.

Action: Do not use more than one attributes with ID or ID derived type.

#### XML-24016: invalid string value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid with respect to string type.

Action: Correct the value to satisfy the declared type.

#### XML-24017: invalid boolean value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid with respect to boolean type.

Action: Correct the value to satisfy Boolean type, valid values are `"0: 1"`, `"true"`, and `"false"`.

#### XML-24018: invalid decimal value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters could not be parsed into a decimal value.

Action: Correct the data value to satisfy decimal type.

#### XML-24019: invalid float value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters could not be parsed into a float value.

Action: Correct the value to satisfy string type

#### XML-24020: invalid double value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not in valid double format as specified in IEEE 754-1985.

Action: Correct the value to satisfy double format.

#### XML-24021: invalid duration string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not in correct extended date time format defined in ISO 8601.

Action: Correct the value to satisfy format `PnYnMnDTnHnMnS`.

#### XML-24022: invalid date value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not in valid calendar date format specified in ISO 8601.

Action: Correct the value to satisfy `CCYY-MM-DD` format.

#### XML-24023: invalid dateTime value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not in valid combined data time format as specified in ISO 8601.

Action: Correct the value to satisfy format `CCYY-MM-DDThh:mm:ss` with optional time zone.

#### XML-24024: invalid time value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not in valid time format as specified in ISO 8601.

Action: Correct the value to satisfy format `DDThh:mm:ss` with optional time zone.

#### XML-24025: invalid gYearMonth value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not in valid right-truncated date format, as specified in ISO 8601.

Action: Correct the value to satisfy format `CCYY-MM`.

#### XML-24026: invalid gYear value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not in valid right-truncated date format, as specified in ISO 8601.

Action: Correct the value to satisfy format `CCYY`.

#### XML-24027: invalid gMonthDay value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not in valid left-truncated date format, as specified in ISO 8601.

Action: Correct the value to required format `--MM-DD`.

#### XML-24028: invalid gDay value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not in valid left-truncated date format, as specified in ISO 8601.

Action: Correct the value to required format `---DD`.

#### XML-24029: invalid gMonth value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not in valid left-and-right-truncated date format, as specified in ISO 8601.

Action: Correct the value to required format `--MM--`.

#### XML-24030: invalid hexBinary value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid hex encoded binary.

Action: Correct the value to satisfy `hexBinary` type.

#### XML-24031: invalid base64Binary value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid with respect to base64 encoding.

Action: Correct the value to satisfy base64 binary encoding.

#### XML-24032: invalid anyURI value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not in valid format as specified in RFC 2396 and RFC 2732.

Action: Correct the value to satisfy anyURI type.

#### XML-24033: invalid QName value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not in valid QName format.

Action: Correct the value to satisfy QName type.

#### XML-24034: invalid NOTATION value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `NOTATION` type.

Action: Correct the value to satisfy `NOTATION` type.

#### XML-24035: invalid normalizedString value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid `normalizedString` value.

Action: Correct the value to satisfy `normalizedString` type.

#### XML-24036: invalid token value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for token type.

Action: Correct the value to satisfy token type.

#### XML-24037: invalid language value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for language type.

Action: Correct the value to satisfy language type.

#### XML-24038: invalid NMTOKEN value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `NMTOKEN` type.

Action: Correct the value to satisfy `NMTOKEN` type.

#### XML-24039: invalid NMTOKENS value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid list of `NMTOKEN` type.

Action: Correct the value to satisfy `NMTOKENS` type.

#### XML-24040: invalid Name value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `Name` type.

Action: Correct the value to satisfy `Name` type.

#### XML-24041: invalid NCName value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `NCName` type.

Action: Correct the value to satisfy `NCName` type.

#### XML-24042: invalid ID value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `ID` type.

Action: Correct the value to satisfy `ID` type.

#### XML-24043: invalid IDREF value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `IDREF` type.

Action: Correct the value to satisfy `IDREF` type.

#### XML-24044: invalid ENTITY value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `ENTITY` type

Action: Correct the value to satisfy `ENTITY` type.

#### XML-24045: invalid ENTITIES value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid list of `ENTITY` value.

Action: Correct the value to satisfy `ENTITIES` type.

#### XML-24046: invalid integer value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for integer type.

Action: Correct the value to satisfy integer type.

#### XML-24047: invalid nonPositiveInteger value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `nonPositiveInteger` type.

Action: Correct the value to satisfy `nonPositiveInteger` type.

#### XML-24048: invalid negativeInteger value string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `negativeInteger` type.

Action: Correct the value to satisfy `negativeInteger` type.

#### XML-24049: invalid long value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `long` type.

Action: Correct the value to satisfy `long` type.

#### XML-24050: invalid int value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `int` type.

Action: Correct the value to satisfy `int` type.

#### XML-24051: invalid short value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `short` type.

Action: Correct the value to satisfy `short` type.

#### XML-24052: invalid byte value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `byte` type.

Action: Correct the value to satisfy `byte` type.

#### XML-24053: invalid nonNegativeInteger value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `nonNegativeInteger` type.

Action: Correct the value to satisfy `nonNegativeInteger` type.

#### XML-24054: invalid unsignedLong value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `unsignedlong` type.

Action: Correct the value to satisfy `unsignedlong` type.

#### XML-24055: invalid unsignedInt value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value of `unsignedInt` type.

Action: Correct the value to satisfy `unsignedInt` type.

#### XML-24056: invalid unsignedShort value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `unsignedShort` type.

Action: Correct the value to satisfy `unsignedShort` type.

#### XML-24057: invalid unsignedByte value string at line string, column string

Cause: \[cvc-datatype-valid.1.2.2\] Characters were not valid value for `unsignedByte` type.

Action: Correct the value to satisfy `unsignedByte` type.

#### XML-24058: value string must be valid with respect to one member type

Cause: \[cvc-datatype-valid.1.2.3\] Characters were invalid with respect to any member type of union.

Action: Correct data value to satisfy at least one member type.

#### XML-24059: element string not expected at line string, column string

Cause: \[cvc-elt.1\]

#### XML-24060: element string abstract

Cause: \[cvc-elt.2\] Element declared abstract was used in instance document.

Action: Do not declare the element as abstract.

#### XML-24061: element string not nillable

Cause: \[cvc-elt.3.1\] There was an attribute `xsi:nil`, which was not allowed because the element declaration was not nillable.

Action: Remove `xsi:nil` attribute from the element.

#### XML-24062: no character or element children allowed for nil content string

Cause: \[cvc-elt.3.2.1\] Element was specified `nil` but had character or element children.

Action: Remove any element content or remove `nil` attribute.

#### XML-24063: nil element does not satisfy fixed value constraint

Cause: \[cvc-elt.3.2.2\] Element had an fixed value while the content in instance was empty.

Action: Remove `nil` attribute from element.

#### XML-24064: xsi:type not a QName at line string, column string

Cause: \[cvc-elt.4.1\] The value of attribute `xsi:type` was not a QName.

Action: Change the value to a valid QName that references a type.

#### XML-24065: xsi:type string not resolved to a type definition

Cause: \[cvc-elt.4.2\] The referenced type specified by `xsi:type` was absent.

Action: Correct the value of `xsi:type` so it points to a valid type definition.

#### XML-24066: local type string not validly derived from the type of element string

Cause: \[cvc-elt.4.3\] The type referenced by `xsi:type` was not derived from original type.

Action: Modify the reference type definition so that it satisfies the constraint, or use another type that is derived from the original type.

#### XML-24067: value string not in enumeration

Cause: \[cvc-enumeration-valid\] The value was not one in the enumeration constraint.

Action: Use valid value specified in enumeration.

#### XML-24068: invalid facet string for type string

Cause: \[cvc-facet-valid\] The given data value violates the constraining facet.

Action: Correct the data value.

#### XML-24069: too many fraction digits in value string at line string, column string

Cause: \[cvc-fractionDigits-valid\] The given number violated the `fractionDigits` constraining facet.

Action: Use fewer fraction digits.

#### XML-24070: missing ID definition for ID reference string at line string, column string

Cause: \[cvc-id.1\] There is no `ID` binding in the `ID`/`IDREF` table for validation root

Action: Define the `ID` for the `ID` reference

#### XML-24071: duplicate ID string at line string, column string

Cause: \[cvc-id.2\] Same `ID` was defined more than once.

Action: Eliminate duplicate `ID` attributes.

#### XML-24072: duplicate key sequence string

Cause: \[cvc-identity-constraint\] The document contained duplicate key sequence that violated uniqueness constraint.

Action: Correct the document to make key sequence unique, or modify XPath to avoid it.

#### XML-24073: target node set not equals to qualified node set for key string

Cause: \[cvc-identity-constraint.4.2.1\] There were empty key sequences in key constraint.

Action: Make sure every element in target node set has a nonempty key sequence.

#### XML-24074: element member string in key sequence is nillable

Cause: \[cvc-identity-constraint.4.2.3\] The element selected as a member in a key sequence was nillable, which is not allowed.

Action: Modify the schema to make corresponding element declaration not nillable.

#### XML-24075: missing key sequence for key reference string

Cause: \[cvc-identity-constraint.4.3\] A `keyref` referenced to empty key sequence.

Action: Make sure every key sequence for `keyref` is has a corresponding key sequence for referenced key.

#### XML-24076: incorrect length of value string

Cause: \[cvc-length-valid\] The length of the value was not the same as specified in length facet.

Action: Use data value with correct length.

#### XML-24077: value string greater than or equal to maxExclusive

Cause: \[cvc-maxExclusive-valid\] The data value was out of boundary specified in `maxExclusive` facet.

Action: Correct the data value.

#### XML-24078: value string greater than the maxInclusive

Cause: \[cvc-maxInclusive-valid\] The data value was out of boundary specified in `maxInclusive` facet.

Action: Correct the data value.

#### XML-24079: value length of string greater than maxLength

Cause: \[cvc-maxLength-valid\] The length of the data value was greater than `maxLength`.

Action: Make the data value's length smaller than `maxLength`.

#### XML-24080: value string smaller or equals to minExclusive

Cause: \[cvc-minExclusive-valid\] The data value was out of lower boundary of value range.

Action: Use data value that is greater to `minExclusive`.

#### XML-24081: value string smaller than minInclusive

Cause: \[cvc-minInclusive-valid\] The data value was too small.

Action: Use data value not smaller than the value of `minInclusive`.

#### XML-24082: value string shorter than minLength

Cause: \[cvc-minLength-valid\] The length of value was smaller than that specified in `minLength`.

Action: Use data value with length greater than or equals to `minLength`.

#### XML-24083: wildcard particle in the content of element string not done

Cause: \[cvc-particle.1.1\] The wildcard particle's `minOccurs` had not been met.

Action: Have more elements in the content that match the wildcard.

#### XML-24084: element particle string not done

Cause: \[cvc-particle.1.2\] The element particle's `minOccurs` had not been met.

Action: Have more elements that match the element declaration or members in its substitution group.

#### XML-24085: model group string in the content of element string not done

Cause: \[cvc-particle.1.3\] The model group particle's `minOccurs` had not been met.

Action: Have more elements in the content that match the model group.

#### XML-24086: invlid literal string with respect to pattern facet string

Cause: \[cvc-pattern-valid\] The literal did not match the pattern constraining facet.

Action: Correct the lexical data to match pattern facet.

#### XML-24087: undefined type string

Cause: \[cvc-resolve-instance.1\] Could not resolve the type reference to a type definition

Action: Add the type definition to schema

#### XML-24088: undeclared attribute string

Cause: \[cvc-resolve-instance.2\] Could not resolve attribute reference to an attribute declaration.

Action: Add the attribute declaration to schema.

#### XML-24089: undeclared element string

Cause: \[cvc-resolve-instance.3\] Could not resolve element reference to an element declaration

Action: Add the element declaration to schema.

#### XML-24090: undefined attribute group string

Cause: \[cvc-resolve-instance.4\] Could not resolve the attribute group reference to an attribute group definition.

Action: Define the attribute group definition in schema.

#### XML-24091: undefined model group string

Cause: \[cvc-resolve-instance.5\] Could not resolve the model group reference to a model group definition.

Action: Define the model group in schema.

#### XML-24092: undeclared notation string

Cause: \[cvc-resolve-instance.6\] Could not resolve the notation reference to a notation declaration.

Action: Add the notation declaration to schema.

#### XML-24093: too many digits in value string at line string, column string

Cause: \[cvc-totalDigits-valid\] The number of digits in numeric value was greater than the value of `totalDigits` facet.

Action: Use smaller numbers.

### A.6 Schema Representation Constraint Error Messages

Schema representation constraint error messages are in the range XML-24100 through XML-24199.

#### XML-24100: element string must belong to XML Schema namespace

Cause: Element in XML Schema document did not have Schema namespace.

Action: Specify XML Schema namespace http://www.w3.org/2001/XMLSchema

#### XML-24101: can not build schema from location string

Cause: \[schema_reference.2\] Processor could not find schema from given schema location

Action: Fix the schema location

#### XML-24102: can not resolve schema by target namespace string

Cause: \[schema_reference.3\] Processor was unable to retrieve schema based on given namespace.

Action: Fix the schema namespace

#### XML-24103: invalid annotation representation at line string, column string

Cause: \[src-annotation\]

#### XML-24104: multiple annotations at line string, column string

Cause: \[src-annotation\] More than one annotation elements appeared in component.

Action: Remove extra annotation.

#### XML-24105: annotation must be the first element at line string, column string

Cause: \[src-annotation\] Annotation was not the first element in component.

Action: Move annotation to the begining of component content.

#### XML-24106: attribute wildcard before attribute declaration at line string, column string

Cause: The attribute wildcard appeared before attribute declarations.

Action: Move attribute wildcard to the end of declaration.

#### XML-24107: multiple attribute wildcard

Cause: \[src-attribute.1\] More than one anyAttributes were declared.

Action: Remove extra attribute wildcards.

#### XML-24108: default string and fixed string both present

Cause: \[src-attribute.1\] Both default and fixed attriubtes were present in attriubte declaration.

Action: Remove either default or fixed attribute.

#### XML-24109: default value string conflicts with attribute use string

Cause: \[src-attribute.2\] Both default and use were present, and value for use is not optional.

Action: Remove either default or use value.

#### XML-24110: missing name or ref attribute

Cause: \[src-attribute.3.1\] Neither name nor ref attribute was present in declaration.

Action: Add name or ref to the declaration.

#### XML-24111: both name and ref presented in attribute declaration

Cause: \[src-attribute.3.1\] Name and ref attribute were both present in attribute declaration.

Action: Add name or ref to the declaration.

#### XML-24112: ref conflicits with form, type, or simpleType child

Cause: \[src-attribute.3.2\] The attribute was a reference, and form, type or simpleType child were specified.

Action: Either change ref to name, or remove form; or remove type, or children, or both.

#### XML-24113: type attribute conflicts with simpleType child

Cause: \[src-attribute.4\] Both type attribute and simpleType child were present.

Action: Remove either type reference or type definition.

#### XML-24114: intersecton of attribute wildcard is not expressible

Cause: \[src-attribute_group.2\] Attriubes wildcards defined were not expressible with a wildcard.

Action: Remove inexpressible attribute wildcards.

#### XML-24115: circular attribute group reference string

Cause: \[src-attribute_group.3\] Attriubte group were circularly referenced outside redefine

Action: Remove circular reference

#### XML-24116: circular group reference string

Cause: group were circularly referenced outside redefine.

Action: Remove circular reference

#### XML-24117: base type string for complexContent is not complex type

Cause: \[src-ct.1\] Derived a complexType with complex content from simple type

Action: Change base type to complex type

#### XML-24118: simple content required in base type string

Cause: \[src-ct.2\] A complexType with simpleContent was derived from a complexType with complex content

Action: Change base type to simple type (if derivation is extension) or simpleContent complex type.

#### XML-24119: properties specified with element reference string

Cause: \[src-element.2.2\] Element reference also had complexType, simpleType, key, keyrefunique children or nillable, form, default, block, or type attribute.

Action: Remove conflict attributes or children.

#### XML-24120: simpleType and complexType can not both present in element declaration string

Cause: \[src-element.3\] Element declaration had both complexType, simpleType children.

Action: Remove either simpleType or complexType child.

#### XML-24121: imported namespace string must different from namespace string

Cause: \[src-import.1.1\] The namespce of import was the same as the target namespace of importing schema

Action: Change import to inclusion.

#### XML-24122: target namespace string required

Cause: \[src-import.1.2\] Imported namespace was specified but absent imported schema.

Action: Remove namespace attribute in element import, or add target namespac to the imported schema.

#### XML-24123: namespace stringis different from expedted targetNamespace string

Cause: \[src-import.3.1\] Specified namespace was different from actual targetNamespace impported.

Action: Correct the namespace attribute in import element.

#### XML-24124: targetNamespace string not expected in schema

Cause: \[src-import.3.2\] Specified a no-namespace schema, but actual schema had targetNamespace.

Action: Remove the imported schema's targetNamespace attribute

#### XML-24125: can not include schema from string

Cause: \[src-include.1\] Processor was unable to include a schema from given location.

Action: Check correctness of URL and URL resolver

#### XML-24126: included targetNamespace string must the same as string

Cause: \[src-include.2.1\] Tried to include a achema with different targetNamespace.

Action: Use import instead of include.

#### XML-24127: no-namespace schema can not include schema with target namespace string

Cause: \[src-include.2.2\] A schema without targetNamespace tried to include a schema with targetNamespace.

Action: Use import instead of include

#### XML-24128: itemType attribute conflicits with simpleType child

Cause: \[src-list-itemType-or-simpleType\] Both itemType attribute and simpleType child were present in list simple type declaration.

Action: Remove either itemType attribute or simpleType child.

#### XML-24129: prefix of qname string can not be resolved

Cause: \[src-qname\] Prefix of a qname was present, but did not map to any in-scope namespace.

Action: Declare a namespace corresponding to the prefix.

#### XML-24130: redefined schema has different namespace. line string column string

Cause: Redefined schema's targetNamespace was not the same as the targetNamespace of redefining schema.

Action: Correct the targetNamespace in redefined schema.

#### XML-24131: no-namespace schema can only redefine schema without targetNamespace

Cause: \[src-redefine.3.2\] A no-namespace schema tried to redefine a schema with namespace

Action: Remove the targetNamespace attribute from redefined schema.

#### XML-24132: type derivation string must be restriction

Cause: \[src-redefine.5\] A simpleType or complexType was present in redefine, but the derivation was not restriction.

Action: Change the type redefinition, make it a restriction.

#### XML-24132: type string must redefine itself at line string, column string

Cause: \[src-redefine.5\] A simpleType or complexType was present in redefine, but its base type was not itself.

Action: Change the base type to redefine itself.

#### XML-24133: group string can have only one self reference in redefinition

Cause: \[src-redefine.6.1.1\] A group was present in redefine and it had more than onereferences to itself in its content.

Action: Remove extra self references in the group redefinition.

#### XML-24134: self reference of group string must not have minOccurs or maxOccurs other than 1 in redefinition

Cause: \[src-redefine.6.1.2\] A minOccurs or maxOccurs with value other than 1 was specified in a group self reference in redefine.

Action: Remove the minOccurs or maxOccurs attribute.

#### XML-24135: redefined group stringis not a restriction of its orginal group

Cause: \[src-redefine.6.2.2\] A group presented in redefine, without self reference but was nota valid restriction of its original group.

Action: Modify the content of the group, make it a valid restriction of its original.

#### XML-24236: attribute group string can have only one self reference in redefinition

Cause: \[src-redefine.7.1\] An attributeGroup was present in redefine and it had more than oneself references in its content.

Action: Remove extra self references.

#### XML-24136: redefined attribute group string must be a restriction of its orginal group

Cause: \[src-redefine.7.2.2\] An attributeGroup presented in redefine, without self reference but was not a valid restriction of its original.

Action: Modify the content of the attribute group, make it valid restriction of its original.

#### XML-24137: restriction must not have both base and simpleType child

Cause: \[src-restriction-base-or-simpleType\]

#### XML-24138: simple type restriction must have either base attribute or simpleType child

Cause: \[src-simple-type.2\] Both base and simpleType were absent in simple type restriction

Action: Add either base attribute or simpleType child.

#### XML-24139: neitehr itemType or simpleType child present for list

Cause: \[src-simple-type.3\] Missing itemType attribute or simpleType child in list definition.

Action: Add either itemType or simpleType child

#### XML-24140: itemType and simpleType child can not both be present in list type.

Cause: \[src-simple-type.3\] Both itemType attribute and simpleType child were present inlist definition

Action: Remove either itemType or simpleType child.

#### XML-24141: circular union type is disallowed

Cause: \[src-simple-type.4\] Some member types in union type made references to the union type

Action: Remove the circular references

#### XML-24142: facet string can not be specified more than once

Cause: \[src-single-facet-value\] Same facet other than enumeration and pattern had been specified more than once, which is not allowed.

Action: Remove extra facets.

#### XML-24143: memberTypes and simpleType child can not both be absent in union

Cause: \[src-union-memberTypes-or-simpleTypes\] Both memberTypes and simpleType were absent for a union type.

Action: Either specify memberTypes or add simpleType children.

#### XML-24144: facets can only used for restriction

Cause: \[st-restrict-facets\] Derivation was not restriction while facet children were present.

Action: Remove facet children.

### A.7 Schema Component Constraint Error Messages

Schema component constraint error messages are in the range XML-24200 through XML-24399.

#### XML-24201: duplicate attribute string declaration

Cause: \[ag-props-correct.1\] There were more than one attribute declarations with same namespace and name in attribute group definition.

Action: Remove duplicate attribute declarations.

#### XML-24202: more than one attributes with ID type not allowed

Cause: \[ag-props-correct.2\] There were more than one attribute declarations with type ID.

Action: Change to other types for such attriubte declarations

#### XML-24203: invalid value constraint string

Cause: \[a-props-correct.2\] The fixed value or default value did not satisfy the attribute's type

Action: Use type valid default for fixed value.

#### XML-24204: value constraint string not allowed for ID type

Cause: \[a-props-correct.3\] Attribute with ID type had either fixed or default value constraint.

Action: Remove value constraint.

#### XML-24205: fixed value string does not match string in attribute declaration

Cause: \[au-props-correct.2\] Attriubte reference specified a fixed value which is not the same as that in referenced declaration.

Action: Correct the fixed value to the same as specified in attribute declaration

#### XML-24206: value constraint must be fixed to match that in attribute declaration

Cause: \[au-props-correct.2\] Attriubte reference specified a default value, while the referenced declaration had a fixed value.

Action: Remove default value form attribute reference.

#### XML-24207: invalid xpath expression string

Cause: \[c-fields-xpaths.1\] The value of xpath was not valid xpath expression as specified in XPath 1.0.

Action: Use correct xpath

#### XML-24208: invalid field xpath string

Cause: \[c-fields-xpaths.2\] The value of xpath did not satisfied field's restricted xpath syntax.

Action: Correct the xpath expression

#### XML-24209: maxOccurs in element string of All group must be 0 or 1

Cause: \[cos-all-limited\] Some elements in a All group had maxOccurs greater than one.

#### XML-24210: All group has to form a content type.

Cause: All group was contained in another model group

Action: Make all group at the top of a content type

#### XML-24211: All group has to form a content type.

Cause: \[cos-applicable-facets\] All group was contained in another model group

Action: Make all group at the top of a content type

#### XML-24212: type string does not allow facet string

Cause: \[cos-applicable-facets\] A facet not applicable to the simple type was used.

Action: Remove the facet.

#### XML-24213: wildcard intersection is not exprssible

Cause: \[cos-aw-intersect\] Two wilcards in an attribtue group had different negative namespaces

Action: Use only one wildcard with negative namespace

#### XML-24214: base type not allow string derivation

Cause: \[cos-ct-derived-ok.1\] Base type's final prevented the derivation.

Action: Remove the derivation method from the value of final in base type

#### XML-24215: complex type string is not a derivation of type string

Cause: \[cos-ct-derived-ok.2\] There was no derivation chain from base type to derived type.

Action: Fix the derivation chaining.

#### XML-24216: must specify a particle in extened content type

Cause: \[cos-ct-extends.1.4.2.1\] The content type of an extension of a complex type was empty

Action: Add particle to the content type of extension.

#### XML-24217: content type string conflicts with base type's content type string

Cause: \[cos-ct-extends.1.4.2.2.2\] Base type's content type was not empty and was not the same as the content type specified.

Action: Match the specified content type with that in base type.

#### XML-24218: inconsistent local element declarations string

Cause: More than one elements in the content had same name and namespace, but did not refer to the same type.

Action: Make type references the same for all elements equal in name and namespace

Comments: cos-element-consistent

#### XML-24219: element string is not valid substitutable for element string

Cause: \[cos-equiv-derived-ok-rec\]

#### XML-24220: itemType string can not be list

Cause: \[cos-list-of-atomic\] The itemType of a list type was itself a list.

Action: Use atomic or union type as the itemType of list.

#### XML-24221: cricular union string not allowed

Cause: \[cos-no-circular-union\] Union's name and namespace matched one of its memberType.

Action: Remove any circular references

#### XML-24222: ambiguous particles string

Cause: \[cos-nanambig\] particles in a content type violated UPA (Unique Particle Attrition) constraint.

Action: Make content type particle unambiguous.

#### XML-24223: invalid particle extension

Cause: \[cos-particle-extend\]

#### XML-24224: invalid particle restriction

Cause: \[cos-particle-restrict\]

#### XML-24225: simple type string does not allowed restriction

Cause: \[cos-st-derived-ok\] Derivation was restriction but restriction was in base type's final.

Action: Remove restriction from base type's final.

#### XML-24226: invalid derivation from base type string

Cause: \[cos-st-derived-ok\] The derivation violated the "type derivaton OK (simple)" constraint.

Action: Make the derivation satisfy the constraint.

#### XML-24227: atomic type can not restrict list string

Cause: \[cos-st-restricts.1.1\] base type is list,

#### XML-24228: base type can not be ur-type in restriction

Cause: \[cos-st-restricts.1.1\] Tried to directly restrict anySimipleType.

#### XML-24229: base type of list must be list or ur-type

Cause: \[cos-st-restricts.2.3\]

#### XML-24230: base type of union must be union or ur-type

Cause: \[cos-st-restricts.3.3\]

#### XML-24231: element default stringrequires mixed content to be emptiable

Cause: \[cos-valide-default\] Element had default constraint but its mixed content type was not emtiable.

Action: Remove default value constraint.

#### XML-24232: element default string requires mixed content or simple content

Cause: \[cos-valide-default\] Element had default value constraint but its content type was element only or empty.

Action: Remove default value constraint.

#### XML-24233: element default string must be valid to its content type

Cause: \[cos-valide-default\] Element's default value constraint was invalid to its type.

Action: Correct the default value or remove it.

#### XML-24234: wrong field cardinality for keyref string

Cause: \[c-props-correct\] Number of fields were different between keyref and referenced key.

Action: Ensure that keyref and referenced key have same number of fields.

#### XML-24235: complex type can only extend simple type string

Cause: \[ct-props-correct\] Complex type was derived from simple type, but derivation was not extension.

Action: Change restriction to extension.

#### XML-24236: cricular type definition string

Cause: \[ct-props-correct\] Type was in its own derivation chain.

Action: Remove recursive derivation.

#### XML-24237: base type string must be complex type

Cause: \[derivation-ok-restriction.1\] Complex type was restricted from a simple type.

Action: Change the restriction from a complex type.

#### XML-24238: attribute string not allowed in base type

Cause: \[derivation-ok-restriction.2\] The attribute in restriction was not allowed for base type.

Action: Correct the restriction of attribute use.

#### XML-24239: required attribute string not in restriction

Cause: \[derivation-ok-restriction.3\] Restriction's attribute uses was not a subset of basetype's attribute uses.

Action: Correct the restriction of attribute uses.

#### XML-24240: no correspoonding attribue wildcard in bas type string

Cause: \[derivation-ok-restriction.4\] Restriction had an attribute wildard that did not corrspond to any attribute wildcard in base type.

Action: Correct the derivation.

#### XML-24241: base type string must have simple content or emptiable

Cause: \[derivation-ok-restriction.5.1\] Content type was simple, but the base type has complex content that is not mixed or not emptiable.

Action: Change the content type from simple to element only.

#### XML-24242: base type string must have empty content or emptiable

Cause: \[derivation-ok-restriction.5.2\] Content type was empty, but the base type had simple content or not emptiable complex content.

Action: Change the content type from simple to element only.

#### XML-24243: enumeration facet required for NOTATION

Cause: \[enumeration-required-notation\] NOTATION type was used without enumeration facet.

Action: Specify enumeration facet for NOTATION.

#### XML-24244: invalid value string in enumeration

Cause: \[enumeration-valid-restriction\] Some value in enumeration was not valid in respect to the type.

Action: Correct invalid values.

#### XML-24245: default value stringis element type invalid

Cause: \[e-props-correct.2\] Default value was invalid in respect to the type of element.

Action: Correct the default value.

#### XML-24246: invalid substitutionGroup string, type invalid

Cause: \[e-props-correc.3\] The type of the element was not a validly derivation from the type ofelement's substitutionGroup.

Action: Correct the type or remove substitutionGroup.

#### XML-24247: ID type does not allow value constraint string

Cause: \[e-props-correct.4\] Type was ID or its derivation whild there was a value constraint.

Action: Remove value constraint.

#### XML-24248: fractionDigits stringgreater than totalDigits string

Cause: \[fractionDigits-totalDigits\] The value for fractionDigits was greater than totalDigits.

Action: Make fractionDigits smaller or equal to totalDigits.

#### XML-24249: length facet can not be specified with minLength or maxLength

Cause: \[length-minLength-maxLength\] Both length and either minLength or maxLength were specified.

Action: Remove length facet.

#### XML-24250: length string not the same as length in base type's

Cause: \[length-valid-restriction\] Specified a length that was not the same as the length in base type.

Action: Remove length facet.

#### XML-24251: maxExclusive greater than its original

Cause: \[maxExclusive-valid-restriction\] Restricted maxExclusive was greater thant its original in base type.

#### XML-24252: minInclusive greater than or equal to maxExclusive

Cause: \[maxInclusive-maxExclusive\] Specified a minInclusive that was greater or equal to maxExclusive.

Action: Make minInclusive smaller than maxExclusive.

#### XML-24253: maxLength is greater than that in base type

Cause: \[maxLength-valid-restriction\] Specified a maxLength greater than orginal in base type.

Action: Sepcify a smaller maxLength to make it valid restriction.

#### XML-24254: circular group stringdisallowed

Cause: \[mg-props-correct\] Circular model group references.

Action: Remove circular references in model group definition.

#### XML-24256: minExclusive must be less than or equal to maxExclusive

Cause: \[minExclusive-less-than-equals-to-maxExclusive\] minExclusive was bigger than maxExclusive.

Action: Use smaller value for minExclusive.

#### XML-24257: minExclusive stringmust be less than maxInclusive

Cause: \[minExclusive-less-than-maxInclusive\] inExclusive specified was greater than or equal to maxInclusive.

Action: Specify smaller minExclusive.

#### XML-24258: invalid minExclusive string

Cause: \[minExclusive-valid-restriction\] Restriction's minExclusive was less than base type's minExclusive

Action: Specify greater value for minExclusive.

#### XML-24259: invalid minExclusive string

Cause: \[minExclusive-valid-restriction\] Restriction's minExclusive was less than base type's minInclusive

Action: Specify greater value for minExclusive

#### XML-24260: invalid minExclusive string

Cause: \[minExclusive-valid-restriction\] Restriction's minExlcusive was greater than base type's maxInclusive

Action: Specify smaller value for minExclusive

#### XML-24261: invalid minExclusive string

Cause: \[minExclusive-valid-restriction\] Restriction's minExclusive was greater than or equals to base type's maxExclusive

Action: Specify smaller value for minExclusive.

#### XML-24262: minInclusive string must not be greater than maxInclusive

Cause: \[minInclusive-less-than-equal-to-maxInclusive\] Specified a minInclusive that was greater than maxInclusive

Action: Specify smaller value for minInclusive.

#### XML-24263: Can not specify both minInclusive and minExclusive

Cause: \[minInclusive-minExclusive\]\] Restriction specified both minInclusive and minExclusive.

Action: Remove either minInclusive or minExclusive.

#### XML-24264: invalid minInclusive string

Cause: \[minInclusive-valid-restriction\] Restriction's minInclusive was less than or equal to minInclusive in base type.

Action: Use minInclusive larger than that of base type.

#### XML-24265: invalid minInclusive string

Cause: \[minInclusive-valid-restriction\] Restriction's minInclusive was less than minExclusivein base type.

Action: Use minInclusive larger than or equal to the minExclusive of base type.

#### XML-24267: invalid minInclusive string

Cause: \[minInclusive-valid-restriction\] Restriction's minInclusive was greater than maxInclusive in base type.

Action: Use minInclusive smaller than or equal to the maxInclusive of base type.

#### XML-24268: invalid minInclusive string

Cause: Restriction's minInclusive was greater than or equal to maxEnclusive in base type.

Action: Use minInclusive smaller than the maxEnclusive of base type.

Comments: minInclusive-valid-restriction

#### XML-24269: invalid minLength string

Cause: \[minLength-less-than-equal-to-maxLength\] minLength in restriction is greater than base type's maxLength.

Action: Make minLength within the length range of base type.

#### XML-24270: invalid minLength string

Cause: \[minLength-valid-restriction\] Value of minLength is smaller than that of base type in restriction.

Action: Use bigger value for minLength.

#### XML-24271: can not declare xmlns attribute

Cause: \[no-xmlns\] Declared an attribute with name xmlns.

Action: Remove such declaraton.

#### XML-24272: no xsi for targetNamespace

Cause: \[no-xsi\] The schema's target namespace matched http://www.w3.org/2001/XMLSchema-instance

Action: Use other target namespace.

#### XML-24272: minOccurs is greater than maxOccurs

Cause: \[n-props-correct\] The minOccurs of particle was greater than the maxOccurs.

Action: Use smaller value for minOccurs.

#### XML-24281: maxOccurs must greater than or equal to 1

Cause: \[ p-props-correct\] The maxOccurs of particle was less than 1.

Action: Use greater value for maxOccurs.

#### XML-24282: incorrect Notation properties

Cause: \[n-props-correct\] The Notation declaration had incorrect properties.

Action: Fix Noation declaration.

#### XML-24283: particle's range is not valid restriction

Cause: \[range-ok\] Range of restriction was not within the range of parent particle.

#### XML-24284: sequence group is not valid derivation of choice group

Cause: Restriction did not satisfy constraint: Particle Derivation OK (Sequence:Choice -- MapAndSum)

Comments: rcase-MapAndSum

#### XML-24285: element string is not valid restriction of element string

Cause: \[rcase-NameAndTypeOK\] Restriction did not satisfy constraint: Particle Restriction OK

#### XML-24286: element string is not valid restriction of wildcard

Cause: \[rcase-NSCompat\] Restriction did not satisfy constraint: Particle Restriction OK

#### XML-24287: group is not valid restriction of wildcard

Cause: \[rcase-NSRecurseCheckCardinality\] Restriction did not satisfy constraint: Particle Restriction OK

#### XML-24288: group any is not valid restriction

Cause: \[rcase-NSSubset\] Restriction did not satisfy constraint: Particle Restriction OK(Any:Any -- NSSubset)

#### XML-24289: invalid restriction of all or sequence group

Cause: \[ rcase-Recurse\] Restriction did not satisfy constraint: Particle Restriction OK(All:All, Seqiemce"Sequence:-- Recurse)

#### XML-24290: wildcard is not valid restriction

Cause: \[rcase-RecurseLax\] The wildcard was not validly restricted from another wildcard.

#### XML-24291: sequence is not a valid restriction of all

Cause: Restriction violated constraint: Particle Derivation OK (Sequence:All--RecurseUnordered)

Action: Fix the restriction.

#### XML-24292: duplicate component definitions string

Cause: \[sch-props-correct\] There were two schema components with same name and namespace.

Action: Remove duplicate definitions.

#### XML-24293: Incorrect simple type definition properties

Cause: \[st-props-correct\]

#### XML-24294: wildcard is not a subset of its super

Cause: \[w-props-correct\] The namespace constraint was not a restriction of its super

Action: Correct namespace constraint.

#### XML-24295: totalDigits stringis greater than string in base type

Cause: \[totalDigits-valid-restriction\] Restriction specified a totalDigits with value greater than that in base type.

Action: Use smaller value for totalDigits.

#### XML-24296: whiteSpace string can not restrict base type's string

Cause: \[whiteSpace-valid-restriction\] Restriction's whiteSpace was replace or preserve, and base had whiteSpace collapse, or restriction had replace while base had preserve.

Action: Eliminate conflicit whiteSpace values.

#### XML-24297: circular substitution group string

Cause: Substitution group was circular.

Action: Remove the circular substitution group

### A.8 XSQL Server Pages Error Messages

XSQL server error messages are in the range XML-25000 through XML-25999.

#### XML-25001: Cannot locate requested XSQL file. Check the name.

#### XML-25002: Cannot acquire database connection from pool: string

#### XML-25003: Failed to find config file string in CLASSPATH.

#### XML-25004: Could not acquire a database connection named: string

#### XML-25005: XSQL page is not well-formed.

#### XML-25006: XSLT stylesheet is not well-formed: string

#### XML-25007: Cannot acquire a database connection to process page.

#### XML-25008: Cannot find XSLT Stylesheet: string

#### XML-25009: Missing arguments on command line

#### XML-25010: Error creating: string\nUsing standard output.

#### XML-25011: Error processing XSLT stylesheet: string

#### XML-25012: Cannot Read XSQL Page

#### XML-25013: XSQL Page URI is null; check exact case of file name.

#### XML-25014: Resulting page is an empty document or had multiple document elements.

#### XML-25015: Error inserting XML Document

#### XML-25016: Error parsing posted XML Document

#### XML-25017: Unexpected Error Occurred

#### XML-25018: Unexpected Error Occurred processing stylesheet string

#### XML-25019: Unexpected Error Occurred reading stylesheet string

#### XML-25020: Config file string is not well-formed.

#### XML-25021: Serializer string is not defined in XSQL configuration file

#### XML-25022: Cannot load serializer class string

#### XML-25023: Class string is not an XSQL Serializer

#### XML-25024: Attempted to get response Writer after getting OutputStream

#### XML-25025: Attempted to get response OutputStream after getting Writer

#### XML-25026: Stylesheet URL references an untrusted server.

#### XML-25027: Failed to load string class for built-in xsql:string action.

#### XML-25028: Error reading string. Check case of the name.

#### XML-25029: Cannot load error handler class string

#### XML-25030: Class string is not an XSQL ErrorHandler

#### XML-25100: You must supply a string attribute.

#### XML-25101: Fatal error in Stylesheet Pool

#### XML-25102: Error instantiating class string

#### XML-25103: Unable to load class string

#### XML-25104: Class string is not an XSQLActionHandler

#### XML-25105: XML returned from PLSQL agent was not well-formed

#### XML-25106: Invalid URL string

#### XML-25107: Error loading URL string

#### XML-25108: XML Document string is not well-formed

#### XML-25109: XML Document returned from database is not well-formed

#### XML-25110: XML Document in parameter string is not well-formed

#### XML-25111: Problem including string

#### XML-25112: Error reading parameter value

#### XML-25113: Error loading XSL transform string

#### XML-25114: Parameter string has a null value

#### XML-25115: No posted document to process

#### XML-25116: No query statement supplied

#### XML-25117: No PL/SQL function name supplied

#### XML-25118: Stylesheet URL references an untrusted server.

#### XML-25119: You must supply either the string or string attribute.

#### XML-25120: You selected fewer than the expected string values.

#### XML-25121: Cannot use 'xpath' to set multiple parameters.

#### XML-25122: Query must be supplied to set multiple parameters

#### XML-25123: Error reading string. Check case of the name.

#### XML-25124: Error printing additional error information.

#### XML-25125: Only one of (string) attributes is allowed.

#### XML-25126: One of (string) attributes must be supplied.

### A.9 XML Pipeline Error Messages

XML pipeline error messages are in the range XML-30000 through XML-30999.

#### XML-30000: Error ignored in string: string

Cause: Error occurred while processes execution is ignored

Action: None required

#### XML-30001: Error occurred in execution of Process

Cause: Component being wrapped by pipeline process is causing error

Action: Fix input XML content

#### XML-30002: Only XML type(s) string allowed.

Comments: Must not occur normally

#### XML-30003: Error creating/writing to output string

Cause: Output URL provided might be invalid

#### XML-30004: Error creating base url string

Cause: URL provided as base URL is invalid

Action: Fix base URL provided

#### XML-30005: Error reading input string

Cause: Input URL provided might be invalid

#### XML-30006: Error in processing pipedoc Error element

#### XML-30007: Error converting output to xml type required by dependent process

#### XML-30008: A valid parameter target is required

Cause: Parameter with name target is missing or invalid

Action: Add parameter target pointing to the target output label

#### XML-30009: Error piping output to input

#### XML-30010: Process definition element string needs to be defined

Cause: Element `procdef` is missing

Action: Add process definition to `pipedoc`.

#### XML-30011: ContentHandler not available

Cause: The dependent process does not provide a valid `ContentHandler`

Action: Implement the `getContentHandler` API in your Process.

#### XML-30012: Pipeline components are not compatible

Cause: Component output and input don't match in terms of document/docfrag.

Action: Fix the `pipedoc` to use components which are compatible.

#### XML-30013: Process with output label string not found

Cause: Process whose output label matched target label is not available.

Action: Create a process in the `pipedoc`, where the output label matches the label of the target parameter.

#### XML-30014: Pipeline is not complete, missing output/outparam label called string

Cause: A dependent process output label has not been named correctly, or a dependent process is missing.

Action: Ensure that each dependent input has a corresponding output.

#### XML-30016: Unable to instantiate class

Cause: A process could not be created because there is an error in the process definition element associated with it.

Action: Correctly specify the class for a process definition.

#### XML-30017: Target is up-to-date, pipeline not executed

Cause: Either the target does not exist, or the pipeline inputs are more recent than the target.

Action: Use the `force` option to execute pipeline regardless of whether the target is up to date.

### A.10 JAXB Error Messages

Java Architecture for XML Binding (JAXB) error messages are in the range XML-32000 through XML32999.

#### XML-32202: a problem was encountered because multiple \<schemaBindings\> were defined.

Cause: There was more than one instance of `<schemaBindings>` declaration in the annotation element of the `<schema>` element.

Action: Update the annotation to remove duplicate `<schemaBinding>` declaration.

#### XML-32203: a problem was encountered because multiple \<class\> name annotations were defined on node string.

Cause: There was more than one instance of `<class>` declaration in the annotation element of the node.

Action: Update the annotation to remove duplicate `<class>` declaration.

#### XML-32204: a problem was encountered because the name in \<class\> declaration contained a package name prefix string which was not allowed.

Cause: A failure occurred because the name attribute in the `<class>` declaration contained a package prefix.

Action: Update the `className` in the `<class>` declaration.

Comments: The package prefix is inherited from the current value of package.

#### XML-32205: a problem was encountered because the property customization was not specified correctly on node string.

Cause: A failure occurred because the property customization was not specified correctly.

Action: Update the `<property>` customization.

#### XML-32206: a problem was encountered because the javaType customization was not specified correctly on node string.

Cause: A failure occurred because the property customization was not specified correctly.

Action: Update the `<javaType>` customization.

#### XML-32207: a problem was encountered in declaring the baseType customization on the node string.

Cause: A failure occurred because the `<baseType>` customization was not specified correctly.

Action: Update the `<baseType>` customization.

#### XML-32208: a problem was encountered because multiple baseType customizations were declared on the node string.

Cause: A failure occurred because multiple `<baseType>` customizations were declared.

Action: Remove one of the `<baseType>` customization declaration.

#### XML-32209: a problem was encountered because multiple javaType customizations were declared on the node string.

Cause: A failure occurred because multiple `<javaType>` customizations were declared.

Action: Remove one of the `<javaType>` customization declaration.

#### XML-32210: a problem was encountered because invalid value was specified on customization of string.

Cause: A failure occurred because an invalid value was specified on the `globalBindings` customization declaration.

Action: Check and correct the `globalBindings` customization value.

#### XML-32211: a problem was encountered because incorrect \<schemaBindings\> customization was specified.

Cause: A failure occurred because an invalid value was specified on the `schemaBindings` customization.

Action: Check and correct the `schemaBindings` customization value.

#### XML-32212: the \<class\> customization did not support specifiying the implementation class using implClass declaration. The implClass declaration specified on node string was ignored.

Cause: A warning occurred because the `implClass` customization declaration was not supported.

#### XML-32213: the \<globalBindings\> customization did not support specifiying user specific class that implements java.util.List. The collectionType declaration was ignored.

Cause: A warning occurred because the user specific implementation class for `java.util.List` was not supported.
