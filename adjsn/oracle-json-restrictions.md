The restrictions associated with Oracle support of JSON data in Oracle Database are listed here.

Unless otherwise specified, an error is raised if a specified limitation is not respected.

- General

  - Number of nesting levels for a JSON object or array: 1000, maximum.

  - JSON field name length: 32767 bytes, maximum.

- SQL/JSON functions

  - Return-value length: 32767 bytes, maximum.

  - Path length: 4K bytes, maximum.

  - Number of path steps: 65535, maximum.

- Simplified JSON syntax (dot notation)

  - Path length: 4K bytes, maximum.

  - Path component length: 128 bytes, maximum.

  - Return value from query: 4K bytes, maximum (even if the value of database parameter `max_string_size` is `extended`).

- JSON search index

  - Field name length: 255 bytes, maximum. If a document has a field name longer than 255 bytes then it might not be completely indexed. In that case, an error is recorded in database view `CTX_USER_INDEX_ERRORS`.

    **See Also:**

    [Oracle Text Reference](../ccref/oracle-text-indexing-elements.md)

- JSON data guide

  - Path length: 4000 bytes, maximum. A path longer than 4000 bytes is ignored by a data guide.

  - Number of children under a parent node: 1024, maximum. A node that has more than 1024 children is ignored by a data guide.

  - Field value length: 32767 bytes. If a JSON field has a value longer than 32767 bytes then the data guide reports the length as 32767.

  - Zero-length field name: A zero-length (empty) object field name (`""`) is not supported for use with JSON data guide. Data-guide behavior is undefined for JSON data that contains such a name.

- OSON

  - All field names, total size: 65535 bytes, maximum.

  - Field name length (each): 255 bytes, maximum.

  - No duplicate fields: If a JSON object with duplicate field names is represented using OSON then only one of these fields is present (kept).

- PL/SQL getter method `JSON_OBJECT_T.get_keys()` returns at most 32767 field names for a given JSON object. An error is raised if it is applied to an object with more than 32767 fields.
