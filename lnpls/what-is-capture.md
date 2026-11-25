## B.5 What is Capture?

When a declaration or definition prevents the compiler from correctly resolving a reference in another scope, the declaration or definition is said to capture the reference. Capture is usually the result of migration or schema evolution.

### Topics

- Outer Capture

- Same-Scope Capture

- Inner Capture

**Note:**

Same-scope and inner capture occur only in SQL scope.

### B.5.1 Outer Capture

Outer capture occurs when a name in an inner scope, which had resolved to an item in an inner scope, now resolves to an item in an outer scope. Both PL/SQL and SQL are designed to prevent outer capture; you need not be careful to avoid it.

### B.5.2 Same-Scope Capture

Same-scope capture occurs when a column is added to one of two tables used in a join, and the new column has the same name as a column in the other table. When only one table had a column with that name, the name could appear in the join unqualified. Now, to avoid same-scope capture, you must qualify the column name with the appropriate table name, everywhere that the column name appears in the join.

### B.5.3 Inner Capture

Inner capture occurs when a name in an inner scope, which had resolved to an item in an outer scope, now either resolves to an item in an inner scope or cannot be resolved. In the first case, the result might change. In the second case, an error occurs.

In Example B-6, a new column captures a reference to an old column with the same name. Before new column `col2` is added to table `tab2`, `col2` resolves to `tab1.col2`; afterward, it resolves to `tab2.col2`.

To avoid inner capture, follow the rules in "[Avoiding Inner Capture in SELECT and DML Statements](avoiding-inner-capture-select-and-dml-statements.md)".

Example B-6 Inner Capture of Column Reference

Table `tab1` has a column named `col2`, but table `tab2` does not:

    DROP TABLE tab1;
    CREATE TABLE tab1 (col1 NUMBER, col2 NUMBER);
    INSERT INTO tab1 (col1, col2) VALUES (100, 10);

    DROP TABLE tab2;
    CREATE TABLE tab2 (col1 NUMBER);
    INSERT INTO tab2 (col1) VALUES (100);

Therefore, in the inner `SELECT` statement, the reference to `col2` resolves to column `tab1.col2`:

    CREATE OR REPLACE PROCEDURE proc AUTHID DEFINER AS
      CURSOR c1 IS
        SELECT * FROM tab1
        WHERE EXISTS (SELECT * FROM tab2 WHERE col2 = 10);
    BEGIN
      OPEN c1;
      CLOSE c1;
    END;
    /

Add a column named `col2` to table `tab2`:

    ALTER TABLE tab2 ADD (col2 NUMBER);

Now procedure `proc` is invalid. At its next invocation, the database automatically recompiles it, and the reference to `col2` in the inner `SELECT` statement resolves to column `tab2.col2`.
