An explanation is given of how to use binary Extensible Markup Language (binary XML) with C.

### 6.1 Introduction to Binary XML for C

Client-side processing of Extensible Markup Language (XML) data can use either `XMLType` data stored in the database, including data in binary XML format, or transient data that is not in the database.

### 6.2 Prerequisites for Using Binary XML with C

This chapter assumes that you are familiar with the XML Parser for C, the basic concepts of binary XML, and the OCI (Oracle Call Interface). Only the OCI API can be used for programming in C with binary XML.

**Related Topics**

- [Using the XML Parser for C](using-XML-parser-for-C.md)
- [Using Binary XML with Java](using-binary-XML-with-Java.md)

**See Also:**

- [Oracle XML DB Developer’s Guide](../adxdb/C-API-for-XMLType.md)

- [Oracle Call Interface Programmer's Guide](../lnoci/index.md)

### 6.3 Binary XML Storage Format – C

Binary XML is an optimized format for XML. It includes encoding and decoding of XML documents, from text to binary and binary to text. Binary XML is XML Schema-aware, but it can also be used for XML data that is not based on an XML schema.

A binary XML processor is a component that processes and transforms binary XML format into text and XML text into binary XML format.

The mid-tier and client tiers can produce, consume, and process XML in binary XML format. The C application fetches data from Oracle XML DB Repository, performs updates on the XML using DOM, and stores it back in the database. Or an XML document is created or input on the client and XSLT, XQuery, and other utilities can be used on it. Then the output XML is saved in Oracle XML DB. Further details of concepts and reference pages for OCI functions are described in the Oracle Call Interface Programmer's Guide.
