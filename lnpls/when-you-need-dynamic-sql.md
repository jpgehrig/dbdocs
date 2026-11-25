## 7.1 When You Need Dynamic SQL

In PL/SQL, you need dynamic SQL to run:

- SQL whose text is unknown at compile time

  For example, a `SELECT` statement that includes an identifier that is unknown at compile time (such as a table name) or a `WHERE` clause in which the number of subclauses is unknown at compile time.

- SQL that is not supported as static SQL

  That is, any SQL construct not included in "[Description of Static SQL](description-static-sql.md)".

If you do not need dynamic SQL, use static SQL, which has these advantages:

- Successful compilation verifies that static SQL statements reference valid database objects and that the necessary privileges are in place to access those objects.

- Successful compilation creates schema object dependencies.

  For information about schema object dependencies, see [Oracle Database Development Guide](../adfns/schema-object-dependency.md).

For information about using static SQL statements with PL/SQL, see [PL/SQL Static SQL](static-sql.md).
