## 13.59 SELECT INTO Statement

The `SELECT` `INTO` statement retrieves values from one or more database tables (as the SQL `SELECT` statement does) and stores them in variables (which the SQL `SELECT` statement does not do).

**Caution:**

The `SELECT` `INTO` statement with the `BULK` `COLLECT` clause is vulnerable to aliasing, which can cause unexpected results. For details, see "[SELECT BULK COLLECT INTO Statements and Aliasing](bulk-sql-and-bulk-binding.md)".

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/SELECT.md) for the syntax of the SQL `SELECT` statement

### Topics

- Syntax

- Semantics

- Examples

- Related Topics

### Syntax

### select_into_statement ::=

![Description of select_into_statement.eps follows](img/select_into_statement.gif)
[Description of the illustration select_into_statement.eps](img_text/select_into_statement.md)

( [bulk_collect_into_clause ::=](RETURNING-INTO-clause.md), [into_clause ::=](RETURNING-INTO-clause.md), [Oracle Database SQL Language Reference](../sqlrf/SELECT.md) for select_list syntax)

### Semantics

### select_into_statement

### DISTINCT \| UNIQUE

Specify `DISTINCT` or `UNIQUE` if you want the database to return only one copy of each set of duplicate rows selected. These two keywords are synonymous. Duplicate rows are those with matching values for each expression in the select list.

Restrictions on DISTINCT and UNIQUE Queries

- The total number of bytes in all select list expressions is limited to the size of a data block minus some overhead. This size is specified by the initialization parameter `DB_BLOCK_SIZE`.

- You cannot specify `DISTINCT` if the select_list contains LOB columns.

### ALL

(Default) Causes the database to return all rows selected, including all copies of duplicates.

### select_list

If the `SELECT` `INTO` statement returns no rows, PL/SQL raises the predefined exception `NO_DATA_FOUND`. To guard against this exception, select the result of the aggregate function `COUNT(*)`, which returns a single value even if no rows match the condition.

### into_clause

With this clause, the `SELECT` `INTO` statement retrieves one or more columns from a single row and stores them in either one or more scalar variables or one record variable. For more information, see "[into_clause ::=](RETURNING-INTO-clause.md)".

### bulk_collect_into_clause

With this clause, the `SELECT` `INTO` statement retrieves an entire result set and stores it in one or more collection variables. For more information, see "[bulk_collect_into_clause ::=](RETURNING-INTO-clause.md)".

### rest_of_statement

Anything that can follow the keyword `FROM` in a SQL `SELECT` statement, described in [Oracle Database SQL Language Reference](../sqlrf/SELECT.md).

### Examples

- [Example 2-25](assigning-values-variables.md), "Assigning Value to Variable with SELECT INTO Statement"

- [Example 5-50](assigning-values-record-variables.md), "SELECT INTO Assigns Values to Record Variable"

- [Example 6-37](transaction-processing-and-control.md), "ROLLBACK Statement"

- [Example 6-38](transaction-processing-and-control.md), "SAVEPOINT and ROLLBACK Statements"

- [Example 6-43](autonomous-transactions.md), "Declaring Autonomous Function in Package"

- [Example 7-20](sql-injection.md), "Validation Checks Guarding Against SQL Injection"

- [Example 12-16](bulk-sql-and-bulk-binding.md), "Bulk-Selecting Two Database Columns into Two Nested Tables"

- [Example 12-17](bulk-sql-and-bulk-binding.md), "Bulk-Selecting into Nested Table of Records"

- [Example 12-21](bulk-sql-and-bulk-binding.md), "Limiting Bulk Selection with ROWNUM, SAMPLE, and FETCH FIRST"

### Related Topics

In this chapter:

- "[Assignment Statement](assignment-statement.md)"

- "[FETCH Statement](FETCH-statement.md)"

- "[%ROWTYPE Attribute](ROWTYPE-attribute.md)"

In other chapters:

- "[Assigning Values to Variables with the SELECT INTO Statement](assigning-values-variables.md)"

- "[Using SELECT INTO to Assign a Row to a Record Variable](assigning-values-record-variables.md)"

- "[Processing Query Result Sets With SELECT INTO Statements](processing-query-result-sets.md)"

- "[SELECT INTO Statement with BULK COLLECT Clause](bulk-sql-and-bulk-binding.md)"

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/SELECT.md) for information about the SQL `SELECT` statement
