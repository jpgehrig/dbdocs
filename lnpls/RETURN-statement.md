## 13.54 RETURN Statement

The `RETURN` statement immediately ends the execution of the subprogram or anonymous block that contains it.

In a function, the `RETURN` statement assigns a specified value to the function identifier and returns control to the invoker, where execution resumes immediately after the invocation (possibly inside the invoking statement). Every execution path in a function must lead to a `RETURN` statement (otherwise, the PL/SQL compiler issues compile-time warning PLW-05005).

In a procedure, the `RETURN` statement returns control to the invoker, where execution resumes immediately after the invocation.

In an anonymous block, the `RETURN` statement exits its own block and all enclosing blocks.

A subprogram or anonymous block can contain multiple `RETURN` statements.

**Note:**

The `RETURN` statement differs from the `RETURN` clause in a function heading, which specifies the data type of the return value.

### Topics

- Syntax

- Semantics

- Examples

- Related Topics

### Syntax

### return_statement ::=

![Description of return_statement.eps follows](img/return_statement.gif)
[Description of the illustration return_statement.eps](img_text/return_statement.md)

( [expression ::=](expression.md) )

### Semantics

expression

Optional when the `RETURN` statement is in a pipelined table function. Required when the `RETURN` statement is in any other function. Not allowed when the `RETURN` statement is in a procedure or anonymous block.

The `RETURN` statement assigns the value of `expression` to the function identifier. Therefore, the data type of `expression` must be compatible with the data type in the `RETURN` clause of the function. For information about expressions, see "[Expression](expression.md)".

### Examples

- [Example 8-3](subprogram-parts.md), "Execution Resumes After RETURN Statement in Function"

- [Example 8-4](subprogram-parts.md), "Function Where Not Every Execution Path Leads to RETURN Statement"

- [Example 8-5](subprogram-parts.md), "Function Where Every Execution Path Leads to RETURN Statement"

- [Example 8-6](subprogram-parts.md), "Execution Resumes After RETURN Statement in Procedure"

- [Example 8-7](subprogram-parts.md), "Execution Resumes After RETURN Statement in Anonymous Block"

### Related Topics

In this chapter:

- "[Block](block.md)"

- "[Function Declaration and Definition](function-declaration-and-definition.md)"

- "[Procedure Declaration and Definition](procedure-declaration-and-definition.md)"

In other chapters:

- "[RETURN Statement](subprogram-parts.md)"
