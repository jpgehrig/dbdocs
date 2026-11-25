The use of XML Schema and object-relational storage of `XMLType` data is covered.

- [Choice of XMLType Storage and Indexing](choice-of-XMLType-storage-and-indexing.md)
  Important design choices for your application include what `XMLType` storage model to use and which indexing approaches to use.
- [XML Schema Storage and Query: Basic](XML-Schema-and-query-basic.md)
  XML Schema is a standard for describing the content and structure of XML documents. You can register, update, and delete an XML schema used with Oracle XML DB. You can define storage structures to use for your XML schema-based data and map XML Schema data types to SQL data types.
- [XML Schema Storage and Query: Object-Relational Storage](XML-Schema-and-query-object-relational-storage.md)
  Advanced techniques for XML Schema-based data include using object-relational storage; annotating XML schemas; mapping Schema data types to SQL; using `complexType` extensions and restrictions; creating, specifying relational constraints on, and partitioning XML Schema-based data, storing `XMLType` data out of line, working with complex or large schemas, and debugging schema registration.
- [XPath Rewrite for Object-Relational Storage](XPath-rewrite-for-object-relational-storage.md)
  For `XMLType` data stored object-relationally, queries involving XPath expression arguments to various SQL functions can often be automatically rewritten to queries against the underlying SQL tables, which are highly optimized.
- [XML Schema Evolution](XML-Schema-evolution.md)
  You can use XML schema evolution to update your XML schema after you have registered it with Oracle XML DB.
