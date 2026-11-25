## 13.10 Collection Method Invocation

A collection method is a PL/SQL subprogram that either returns information about a collection or operates on a collection.

### Topics

- Syntax

- Semantics

- Examples

- Related Topics

### Syntax

### collection_method_call ::=

![Description of collection_method_call.eps follows](img/collection_method_call.gif)
[Description of the illustration collection_method_call.eps](img_text/collection_method_call.md)

### Semantics

### collection_method_call

collection

Name of the collection whose method you are invoking.

COUNT

Function that returns the number of elements in the collection, explained in "[COUNT Collection Method](collection-methods.md)".

DELETE

Procedure that deletes elements from the collection, explained in "[DELETE Collection Method](collection-methods.md)".

Restriction on DELETE

If `collection` is a varray, you cannot specify indexes with `DELETE`.

index

Numeric expression whose data type either is `PLS_INTEGER` or can be implicitly converted to `PLS_INTEGER` (for information about the latter, see "[s](pls_integer-and-binary_integer-data-types.md)").

EXISTS

Function that returns `TRUE` if the `index`th element of the collection exists and `FALSE` otherwise, explained in "[EXISTS Collection Method](collection-methods.md)".

EXTEND

Procedure that adds elements to the end of the collection, explained in "[EXTEND Collection Method](collection-methods.md)".

Restriction on EXTEND

You cannot use `EXTEND` if `collection` is an associative array.

FIRST

Function that returns the first index in the collection, explained in "[FIRST and LAST Collection Methods](collection-methods.md)".

LAST

Function that returns the last index in the collection, explained in "[FIRST and LAST Collection Methods](collection-methods.md)".

LIMIT

Function that returns the maximum number of elements that the collection can have. If the collection has no maximum size, then `LIMIT` returns `NULL`. For an example, see "[LIMIT Collection Method](collection-methods.md)".

NEXT

Function that returns the index of the succeeding existing element of the collection, if one exists. Otherwise, `NEXT` returns `NULL`. For more information, see "[PRIOR and NEXT Collection Methods](collection-methods.md)".

PRIOR

Function that returns the index of the preceding existing element of the collection, if one exists. Otherwise, `NEXT` returns `NULL`. For more information, see "[PRIOR and NEXT Collection Methods](collection-methods.md)".

TRIM

Procedure that deletes elements from the end of a collection, explained in "[TRIM Collection Method](collection-methods.md)".

Restriction on TRIM

You cannot use `TRIM` if `collection` is an associative array.

number

Number of elements to delete from the end of a collection. Default: one.

### Examples

- [Example 5-19](collection-methods.md), "DELETE Method with Nested Table"

- [Example 5-20](collection-methods.md), "DELETE Method with Associative Array Indexed by String"

- [Example 5-21](collection-methods.md), "TRIM Method with Nested Table"

- [Example 5-22](collection-methods.md), "EXTEND Method with Nested Table"

- [Example 5-23](collection-methods.md), "EXISTS Method with Nested Table"

- [Example 5-24](collection-methods.md), "FIRST and LAST Values for Associative Array Indexed by PLS_INTEGER"

- [Example 5-25](collection-methods.md), "FIRST and LAST Values for Associative Array Indexed by String"

- [Example 5-26](collection-methods.md), "Printing Varray with FIRST and LAST in FOR LOOP"

- [Example 5-27](collection-methods.md), "Printing Nested Table with FIRST and LAST in FOR LOOP"

- [Example 5-28](collection-methods.md), "COUNT and LAST Values for Varray"

- [Example 5-29](collection-methods.md), "COUNT and LAST Values for Nested Table"

- [Example 5-30](collection-methods.md), "LIMIT and COUNT Values for Different Collection Types"

- [Example 5-31](collection-methods.md), "PRIOR and NEXT Methods"

- [Example 5-32](collection-methods.md), "Printing Elements of Sparse Nested Table"

### Related Topics

In this chapter:

- "[Collection Variable Declaration](collection-variable.md)"

In other chapters:

- "[Collection Methods](collection-methods.md)"
