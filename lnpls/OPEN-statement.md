## 13.45 OPEN Statement

The `OPEN` statement opens an explicit cursor, allocates database resources to process the associated query, identifies the result set, and positions the cursor before the first row of the result set.

If the query has a `FOR` `UPDATE` clause, the `OPEN` statement locks the rows of the result set.

### Topics

- Syntax

- Semantics

- Examples

- Related Topics

### Syntax

### open_statement ::=

![Description of open_statement.eps follows](img/open_statement.gif)
[Description of the illustration open_statement.eps](img_text/open_statement.md)

### Semantics

cursor

Name of an explicit cursor that is not open.

actual_cursor_parameter

List of actual parameters for the cursor that you are opening. An actual parameter can be a constant, initialized variable, literal, or expression. The data type of each actual parameter must be compatible with the data type of the corresponding formal parameter.

You can specify actual cursor parameters with either positional notation or named notation. For information about these notations, see "[Positional, Named, and Mixed Notation for Actual Parameters](subprogram-parameters.md)".

If the cursor specifies a default value for a parameter, you can omit that parameter from the parameter list. If the cursor has no parameters, or specifies a default value for every parameter, you can either omit the parameter list or specify an empty parameter list.

### Examples

- [Example 6-11](cursors-overview.md), "Explicit Cursor that Accepts Parameters"

- [Example 6-12](cursors-overview.md), "Cursor Parameters with Default Values"

### Related Topics

In this chapter:

- "[CLOSE Statement](CLOSE-statement.md)"

- "[Explicit Cursor Declaration and Definition](explicit-cursor-declaration-and-definition.md)"

- "[FETCH Statement](FETCH-statement.md)"

- "[OPEN FOR Statement](OPEN-FOR-statement.md)"

In other chapters:

- "[Opening and Closing Explicit Cursors](cursors-overview.md)"

- "[Explicit Cursors that Accept Parameters](cursors-overview.md)"
