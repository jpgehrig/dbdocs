## JSON_MERGEPATCH

### Syntax



![Description of json_mergepatch.eps follows](img/json_mergepatch.gif)
[Description of the illustration json_mergepatch.eps](img_text/json_mergepatch.md)



### on_error_clause::=



![Description of on_error_clause.eps follows](img/on_error_clause.gif)
[Description of the illustration on_error_clause.eps](img_text/on_error_clause.md)



### Purpose

`JSON_MERGEPATCH` is a standardized functionality for modifying a target JSON document using a JSON document called a merge patch. The function is described in RFC 7396.

`target_expr` evaluates to the JSON value target document.

`patch_expr` evaluates to the JSON value patch document.

`JSON_MERGEPATCH` evalutes the patch document against the target document to produce the result document. If the target or the patch document is NULL, then the result is also NULL.

The `JSON_query_returning_clause` specifies the return type of the operator. The default return type is `VARCHAR2(4000)`.

The `PRETTY` keyword specifies that the result should be formatted for human readability.

The `ASCII` keyword specifies that non-ASCII characters should be output using JSON escape sequences.

The `TRUNCATE` keyword specifies that the result document should be truncated to fit in the specified return type.

The `on_error_clause` optionally controls the handling of errors that occur during the processing of the target and patch documents.

- `NULL ON ERROR` - Returns null when an error occurs. This is the default.
- `ERROR ON ERROR` - Returns the appropriate Oracle error when an error occurs.

**See Also:**

- [RFC 7396 JSON Merge Patch](https://tools.ietf.org/html/rfc7396)

- [Updating a JSON Document with JSON Merge Patch](../adjsn/updating-json-document-json-merge-patch.md)
