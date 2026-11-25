JavaScript Object Notation (JSON) is defined in standards ECMA-404 (JSON Data Interchange Format) and ECMA-262 (ECMAScript Language Specification, third edition). The JavaScript dialect of ECMAScript is a general programming language used widely in web browsers and web servers.

- Overview of JSON
  **JavaScript Object Notation** (**JSON**) is defined in standards ECMA-404 (JSON Data Interchange Format) and ECMA-262 (ECMAScript Language Specification, third edition). The JavaScript dialect of ECMAScript is a general programming language used widely in web browsers and web servers.
- JSON Syntax and the Data It Represents
  JSON (and JavaScript) values, scalars, objects, and arrays are described.
- JSON Compared with XML
  Both JSON and XML (Extensible Markup Language) are commonly used as data-interchange languages. Their main differences are listed here.

**Parent topic:** [Introduction to JSON Data and Oracle Database](intro-to-json-data-and-oracle-database.md)

### 2.1 Overview of JSON

**JavaScript Object Notation** (**JSON**) is defined in standards ECMA-404 (JSON Data Interchange Format) and ECMA-262 (ECMAScript Language Specification, third edition). The JavaScript dialect of ECMAScript is a general programming language used widely in web browsers and web servers.

JSON is almost a subset of the object literal notation of JavaScript.<sup>Foot 1</sup> Because it can be used to represent JavaScript object literals, JSON commonly serves as a data-interchange language. In this it has much in common with XML.

Because it is (almost a subset of) JavaScript notation, JSON can often be used in JavaScript programs without any need for parsing or serializing. It is a text-based way of representing JavaScript object literals, arrays, and scalar data.

Although it was defined in the context of JavaScript, JSON is in fact a language-independent data format. A variety of programming languages can parse and generate JSON data.

JSON is relatively easy for humans to read and write, and easy for software to parse and generate. It is often used for serializing structured data and exchanging it over a network, typically between a server and web applications.

**See Also:**

- [ECMA 404](https://ecma-international.org/publications-and-standards/standards/ecma-404/) and [IETF RFC4627](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=tools_ietf_rfc4627) for the definition of the JSON Data Interchange Format

- [ECMA 262](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=ecma_262) for the ECMAScript Language Specification

- [JSON.org](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=json_org) for information about JSON

**Parent topic:** JSON Data

### 2.2 JSON Syntax and the Data It Represents

JSON (and JavaScript) values, scalars, objects, and arrays are described.

A JSON **value** is one of the following: object, array, number, string, Boolean (`true` or `false`), or `null`. All values except objects and arrays are **scalar**.

**Note:**

A JSON value of `null` is a value as far as SQL is concerned. It is not `NULL`, which in SQL represents the absence of a value (missing, unknown, or inapplicable data). In particular, SQL condition `IS NULL` returns false for a JSON `null` value, and SQL condition `IS NOT NULL` returns true.

A **JavaScript object** is an associative array, or dictionary, of zero or more pairs of property names and associated JSON values.<sup>Foot 2</sup> A **JSON object** is a **JavaScript object literal**.<sup>Foot 3</sup> It is written as such a property list enclosed in braces (`{`, `}`), with name–value pairs separated by commas (`,`), and with the name and value of each pair separated by a colon (`:`). (Whitespace before or after the comma or colon is optional and insignificant.)

In JSON each property name and each string value must be enclosed in double quotation marks (`"`). In JavaScript notation, a property name used in an object literal can be, but need not be, enclosed in double quotation marks. It can also be enclosed in single quotation marks (`'`).

As a result of this difference, in practice, data that is represented using unquoted or single-quoted property names is sometimes referred to loosely as being represented in JSON, and some implementations of JSON, including the Oracle Database implementation, support the lax syntax that allows the use of unquoted and single-quoted property names.

A string in JSON is composed of Unicode characters, with backslash (`\`) escaping. A JSON number (numeral) is represented in decimal notation, possibly signed and possibly including a decimal exponent.

An object property is typically called a **field**. It is sometimes called a **key**, but this documentation generally uses “field” to avoid confusion with other uses here of the word “key”. An object property name–value pair is often called an object **member** (but sometimes **member** can mean just the property). Order is not significant among object members.

**Note:**

- A JSON field name can be empty (written `""`).<sup>Foot 4</sup>

- Each field name in a given JSON object is not necessarily unique; the same field name can be repeated. The SQL/JSON path evaluation that Oracle Database employs always uses only one of the object members that have a given field name; any other members with the same name are ignored. It is unspecified which of multiple such members is used.

  See also [Unique Versus Duplicate Fields in JSON Objects](conditions-is-json-and-is-not-json.md).

A **JavaScript array** has zero or more elements. A **JSON array** is represented by brackets (`[`, `]`) surrounding the representations of the array **elements** (also called **items**), which are separated by commas (`,`), and each of which is an object, an array, or a scalar value. Array element order is significant. (Whitespace before or after a bracket or comma is optional and insignificant.)

Example 2-1 A JSON Object (Representation of a JavaScript Object Literal)

This example shows a JSON object that represents a purchase order, with top-level field names `PONumber`, `Reference`, `Requestor`, `User`, `Costcenter`, `ShippingInstruction`, `Special Instructions`, `AllowPartialShipment` and `LineItems`.

    { "PONumber"             : 1600,
      "Reference"            : "ABULL-20140421",
      "Requestor"            : "Alexis Bull",
      "User"                 : "ABULL",
      "CostCenter"           : "A50",
      "ShippingInstructions" : { "name"   : "Alexis Bull",
                                 "Address": { "street"  : "200 Sporting Green",
                                              "city"    : "South San Francisco",
                                              "state"   : "CA",
                                              "zipCode" : 99236,
                                              "country" : "United States of America" },
                                 "Phone" : [ { "type" : "Office", "number" : "909-555-7307" },
                                             { "type" : "Mobile", "number" : "415-555-1234" } ] },
      "Special Instructions" : null,
      "AllowPartialShipment" : false,
      "LineItems"            : [ { "ItemNumber" : 1,
                                   "Part"       : { "Description" : "One Magic Christmas",
                                                    "UnitPrice"   : 19.95,
                                                    "UPCCode"     : 13131092899 },
                                   "Quantity"   : 9.0 },
                                 { "ItemNumber" : 2,
                                   "Part"       : { "Description" : "Lethal Weapon",
                                                    "UnitPrice"   : 19.95,
                                                    "UPCCode"     : 85391628927 },
                                   "Quantity"   : 5.0 } ] }

- Most of the fields here have string values. For example: field `User` has value `"ABULL"`.

- Fields `PONumber` and `zipCode` have numeric values: `1600` and `99236`.

- Field `ShippingInstructions` has an object as its value. This object has three members, with fields `name`, `Address`, and `Phone`. Field `name` has a string value (`"Alexis Bull"`).

- The value of field `Address` is an object with fields `street`, `city`, `state`, `zipCode`, and `country`. Field `zipCode` has a numeric value; the others have string values.

- Field `Phone` has an array as value. This array has two elements, each of which is an object. Each of these objects has two members: fields `type` and `number` with their values.

- Field `Special Instructions `has a `null` value.

- Field `AllowPartialShipment` has the Boolean value `false`.

- Field `LineItems` has an array as value. This array has two elements, each of which is an object. Each of these objects has three members, with fields `ItemNumber`, `Part`, and `Quantity`.

- Fields `ItemNumber` and `Quantity` have numeric values. Field `Part` has an object as value, with fields `Description`, `UnitPrice`, and `UPCCode`. Field `Description` has a string value. Fields `UnitPrice` and `UPCCode` have numeric values.

**Related Topics**

- [About Strict and Lax JSON Syntax](conditions-is-json-and-is-not-json.md)

**See Also:**

[Example 4-2](creating-a-table-with-a-json-column.md)

**Parent topic:** JSON Data

### 2.3 JSON Compared with XML

Both JSON and XML (Extensible Markup Language) are commonly used as data-interchange languages. Their main differences are listed here.

JSON is most useful with simple, structured data. XML is useful for both structured and semi-structured data. JSON is generally data-centric, not document-centric; XML can be either. JSON is not a markup language; it is designed only for data representation. XML is both a document markup language and a data representation language.

- JSON data types are few and predefined. XML data can be either typeless or based on an XML schema or a document type definition (DTD).

- JSON has simple structure-defining and document-combining constructs: it lacks attributes, namespaces, inheritance, and substitution.

- The order of the members of a JavaScript object literal is insignificant. In general, order matters within an XML document.

- JSON lacks an equivalent of XML text nodes (XPath node test `text()`). In particular, this means that there is no mixed content (which is another way of saying that JSON is not a markup language).

- JSON has no date data type (unlike both XML and JavaScript). A date is represented in JSON using the available data types, such as string. There are some de facto standards for converting between dates and JSON strings. But programs using JSON must, one way or another, deal with date representation conversion.

Because of its simple definition and features, JSON data is generally easier to generate, parse, and process than XML data. Use cases that involve combining different data sources generally lend themselves well to the use of XML, because it offers namespaces and other constructs facilitating modularity and inheritance.

**Parent topic:** JSON Data

------------------------------------------------------------------------



Footnote Legend

Footnote 1:

JSON differs from JavaScript notation in this respect: JSON allows unescaped Unicode characters U+2028 (LINE SEPARATOR) and U+2029 (PARAGRAPH SEPARATOR) in strings. JavaScript notation requires control characters such as these to be escaped in strings. This difference can be important when generating JSONP (JSON with padding) data.


Footnote 2:

JavaScript objects are thus similar to hash tables in C and C++, HashMaps in Java, associative arrays in PHP, dictionaries in Python, and hashes in Perl and Ruby.


Footnote 3:

An object is created in JavaScript using either constructor `Object` or object literal syntax: `{`...`}`.


Footnote 4: In a few contexts an empty field name cannot be used with Oracle Database. Wherever it can be used, the name must be wrapped with double quotation marks.
