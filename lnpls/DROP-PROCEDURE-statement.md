## 14.18 DROP PROCEDURE Statement

The `DROP` `PROCEDURE` statement drops a standalone procedure from the database.

**Note:**

Do not use this statement to remove a procedure that is part of a package. Instead, either drop the entire package using the "[DROP PACKAGE Statement](DROP-PACKAGE-statement.md)", or redefine the package without the procedure using the "[CREATE PACKAGE Statement](CREATE-PACKAGE-statement.md)" with the `OR` `REPLACE` clause.

### Topics

- Prerequisites

- Syntax

- Semantics

- Example

- Related Topics

### Prerequisites

The procedure must be in your schema or you must have the `DROP` `ANY` `PROCEDURE` system privilege.

### Syntax

### drop_procedure ::=

![Description of drop_procedure.eps follows](img/drop_procedure.gif)
[Description of the illustration drop_procedure.eps](img_text/drop_procedure.md)

### Semantics

IF EXISTS

Drops the procedure if it exists. If no such procedure exists, the statement is ignored without error.

schema

Name of the schema containing the procedure. Default: your schema.

procedure

Name of the procedure to be dropped.

When you drop a procedure, the database invalidates any local objects that depend upon the dropped procedure. If you subsequently reference one of these objects, then the database tries to recompile the object and returns an error message if you have not re-created the dropped procedure.

### Example

Example 14-35 Dropping a Procedure

This statement drops the procedure `remove_emp` owned by the user `hr` and invalidates all objects that depend upon `remove_emp`:

    DROP PROCEDURE IF EXISTS hr.remove_emp;

If `remove_emp` does not already exist in the schema, this statement is ignored without error. Note that the output message is the same whether or not the procedure exists (in this case, `Procedure dropped.`).

### Related Topics

- "[ALTER PROCEDURE Statement](ALTER-PROCEDURE-statement.md)"

- "[CREATE PROCEDURE Statement](CREATE-PROCEDURE-statement.md)"
