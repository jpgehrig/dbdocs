## 13.55 RETURNING INTO Clause

The `RETURNING` `INTO` clause specifies the variables in which to store the values returned by the statement to which the clause belongs.

The variables can be either individual variables or collections. If the statement affects no rows, then the values of the variables are undefined.

The static `RETURNING` `INTO` clause belongs to a `DELETE`, `INSERT`, or `UPDATE` statement. The dynamic `RETURNING` `INTO` clause belongs to the `EXECUTE` `IMMEDIATE` statement.

**Note:**

You cannot use the `RETURNING` `INTO` clause for remote or parallel deletes.

### Topics

- Syntax

- Semantics

- Examples

- Related Topics

### Syntax

### static_returning_clause ::=

![Description of static_returning_clause.eps follows](img/static_returning_clause.gif)
[Description of the illustration static_returning_clause.eps](img_text/static_returning_clause.md)

### dynamic_returning_clause ::=

![Description of dynamic_returning_clause.eps follows](img/dynamic_returning_clause.gif)
[Description of the illustration dynamic_returning_clause.eps](img_text/dynamic_returning_clause.md)

### into_clause ::=

![Description of into_clause.eps follows](img/into_clause.gif)
[Description of the illustration into_clause.eps](img_text/into_clause.md)

### bulk_collect_into_clause ::=

![Description of bulk_collect_into_clause.eps follows](img/bulk_collect_into_clause.gif)
[Description of the illustration bulk_collect_into_clause.eps](img_text/bulk_collect_into_clause.md)

### Semantics

### static_returning_clause

column

Expression whose value is the name of a column of a database table.

### into_clause

Specifies the variables or record in which to store the column values that the statement returns.

Restriction on into_clause

Use `into_clause` in `dynamic_returning_clause` if and only if `dynamic_sql_stmt` (which appears in "[EXECUTE IMMEDIATE Statement](EXECUTE-IMMEDIATE-statement.md)") returns a single row.

record

The name of a record variable in which to store the row that the statement returns. For each select_list item in the statement, the record must have a corresponding, type-compatible field.

variable

Either the name of a scalar variable in which to store a column that the statement returns or the name of a host cursor variable that is declared in a PL/SQL host environment and passed to PL/SQL as a bind variable. Each select_list item in the statement must have a corresponding, type-compatible variable. The data type of a host cursor variable is compatible with the return type of any PL/SQL cursor variable.

Restriction on variable

`variable` cannot have the data type `BOOLEAN`.

### bulk_collect_into_clause

Specifies one or more existing collections or host arrays in which to store the rows that the statement returns. For each select_list item in the statement, `bulk_collect_into_clause` must have a corresponding, type-compatible `collection` or `host_array`.

For the reason to use this clause, see "[Bulk SQL and Bulk Binding](bulk-sql-and-bulk-binding.md)".

Restrictions on bulk_collect_into_clause

- Use the `bulk_collect_into_clause` clause in `dynamic_returning_clause` if and only if `dynamic_sql_stmt` (which appears in "[EXECUTE IMMEDIATE Statement](EXECUTE-IMMEDIATE-statement.md)") can return multiple rows.

- You cannot use `bulk_collect_into_clause` in client programs.

- When the statement that includes `bulk_collect_into_clause` requires implicit data type conversions, `bulk_collect_into_clause` can have only one `collection` or `host_array`.

collection

Name of a collection variable in which to store the rows that the statement returns.

Restrictions on collection

- `collection` cannot be the name of an associative array that is indexed by a string.

- When the statement requires implicit data type conversions, `collection` cannot be the name of a collection of a composite type.

:host_array

Name of an array declared in a PL/SQL host environment and passed to PL/SQL as a bind variable. Do not put space between the colon (:) and `host_array`.

### Examples

- [Example 5-52](assigning-values-record-variables.md), "UPDATE Statement Assigns Values to Record Variable"

- [Example 6-1](description-static-sql.md), "Static SQL Statements"

- [Example 12-25](bulk-sql-and-bulk-binding.md), "Returning Deleted Rows in Two Nested Tables"

- [Example 12-26](bulk-sql-and-bulk-binding.md), "DELETE with RETURN BULK COLLECT INTO in FORALL Statement"

### Related Topics

In this chapter:

- "[DELETE Statement Extension](DELETE-statement-extension.md)"

- "[EXECUTE IMMEDIATE Statement](EXECUTE-IMMEDIATE-statement.md)"

- "[FETCH Statement](FETCH-statement.md)"

- "[SELECT INTO Statement](SELECT-INTO-statement.md)"

- "[UPDATE Statement Extensions](UPDATE-statement-extensions.md)"

In other chapters:

- "[Using SQL Statements to Return Rows in PL/SQL Record Variables](assigning-values-record-variables.md)"

- "[EXECUTE IMMEDIATE Statement](native-dynamic-sql.md)"

- "[RETURNING INTO Clause with BULK COLLECT Clause](bulk-sql-and-bulk-binding.md)"
