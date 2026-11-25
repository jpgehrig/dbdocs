This section explains some of the constraints on SQL in a distributed environment.

These constraints apply to distributed environments that access non-Oracle systems or remote Oracle databases.

- Remote and Heterogeneous References
  Many of the rules for heterogeneous access also apply to remote references.
- Rules and Restrictions When Using SQL for Remote Mapping in a Distributed Environment
  There are rules and restrictions when you use SQL for remote mapping in a distributed environment.

**Parent topic:** [Features of Oracle Database Gateways](oracle-database-gateways-features.md)

### Remote and Heterogeneous References

Many of the rules for heterogeneous access also apply to remote references.

A SQL statement can, with restrictions, be executed on any database node referenced in the SQL statement or the local node. If all objects referenced are resolved to a single, referenced node, Oracle attempts to execute a query at that node. You can force execution at a referenced node by using the `/*+ REMOTE_MAPPED */` or `/*+ DRIVING_SITE */` hints. If a statement is forwarded to a node other than the node from where the statement was issued, the statement is remote-mapped.

There is complete data type checking support for remote-mapped statements. The result provides consistent data type checking and complete data type coercion.

SQL statements must follow specific rules to be remote-mapped. If these rules are not followed, an error occurs. The order in which the rules are applied does not matter.

Different constraints exist when you use SQL for remote mapping in a distributed environment. This distributed environment can include remote Oracle databases and non-Oracle databases that are accessed through Oracle Database gateways.

**Related Topics**

- [Oracle Database Server SQL Construct Processing](database-server-sql-construct-processing.md)
- Rules and Restrictions When Using SQL for Remote Mapping in a Distributed Environment

**See Also:**

[Oracle Database Administrator's Guide](../admin/distributed-database-concepts.md) for information about distributed databases.

**Parent topic:** Constraints on SQL in a Distributed Environment

### Rules and Restrictions When Using SQL for Remote Mapping in a Distributed Environment

There are rules and restrictions when you use SQL for remote mapping in a distributed environment.

The following section lists some of the different rules or restrictions that exist when you use SQL for remote mapping in a distributed environment.

**Note:**

In the examples that follow, the `remote_db` noun refers to a remote non-Oracle system, and the `remote_oracle_db` noun refers to a remote Oracle Database.

#### Rule A: A data definition language statement cannot be remote-mapped.

In Oracle data definition language, the target object syntactically has no place for a remote reference. Data definition language statements that contain remote references are executed locally. For Heterogeneous Services, this means it cannot directly create database objects in a non-Oracle database using SQL.

You can create database objects individually by using passthrough SQL, as shown in the following example:

    DECLARE
      num_rows INTEGER;
    BEGIN
      num_rows := DBMS_HS_PASSTHROUGH.EXECUTE_IMMEDIATE@remote_db
      (
         'create table x1 (c1 char, c2 int)'
      );
    END;

#### Rule B: INSERT, UPDATE and DELETE statements with a remote target table must be remote-mapped.

This rule is more restrictive for non-Oracle remote databases than for a remote Oracle database. This is because the remote system cannot retrieve data from the originating Oracle database while executing data manipulation language (DML) statements targeting tables in a non-Oracle system.

For example, to insert all local employees from the local `emp` table to a remote non-Oracle `emp` table, use the following statement:

    INSERT INTO emp@remote_db SELECT * FROM emp;

This statement is remote-mapped to the remote database. The remote-mapped statement sent to the remote database contains a remote reference back to the originating database for the `emp` table. A remote link received by the remote database is called a callback link.

**Note:**

Even though callback links are supported in generic Heterogeneous Services, they may not be implemented in all Heterogeneous Services agents. For more information, see your database gateway documentation to determine if callback links work with the database gateway that you are using.

If callback links are not supported by a particular gateway, the previous `INSERT` statements returns the following error:

    ORA-02025: all tables in the SQL statement must be at the remote database

The workaround is to write a PL/SQL block. For example:

    DECLARE
    CURSOR remote_insert IS SELECT * FROM emp;
    BEGIN
       FOR rec IN remote_insert LOOP
        INSERT INTO emp@remote_db (empno, ename, deptno) VALUES (
          rec.empno,
          rec.ename,
          rec.deptno
        );
       END loop;
    END;

Another special case involves session-specific SQL functions such as `USER`, `USERENV`, and `SYSDATE`. These functions must be executed at the originating site. A remote-mapped statement with these functions contains a callback link. For a non-Oracle database for which callbacks are not supported, this can (by default) result in a restriction error.

For example, consider the following statement:

    DELETE FROM emp@remote_db WHERE hiredate > sysdate;

The previous statement returns the following error message:

    ORA-02070: database REMOTE_DB does not support special functions in this context

This can be resolved by replacing special functions with a bind variable. For example:

    DELETE FROM emp@remote_db WHERE hiredate > :1;

#### Rule C: Object features such as tables with nested table columns, ADT columns, Opaque columns, or Ref Columns cannot be remote-mapped.

Currently, these column types are not supported for heterogeneous access. Hence, this limitation is not directly encountered.

#### Rule D: SQL statements containing operators and constructs that are not supported at the remote site cannot be remote-mapped.

In the case of an `INSERT`, `UPDATE`, or `DELETE` statement, the SQL statement cannot be executed (see Rule B). However, you might be able to execute the SQL statement if the unsupported operator or construct can be executed through a callback link.

In the case of a `SELECT` statement, you can execute a statement affected by this rule if none of the remaining rules require the statement to be remote-mapped. The `SELECT` statements affected by this rule are executed by retrieving all the necessary data through a remote `SELECT` operation, and processing the unsupported operator or construct locally using the SQL engine.

A remote `SELECT` operation is the operation that retrieves rows from a remote table, as opposed to an operation that retrieves data from a local table. A full table scan is when all the data in the remote table across the network without any filtering (for example, `SELECT * FROM EMP`) is retrieved.

Full table scans are expensive and, therefore, Oracle noun attempts to avoid them. If there are indexes on the remote table that can be used, these indexes are used in a `WHERE` clause predicate to reduce the number of rows retrieved across the network.

You can check the SQL statement generated by Oracle Database by explaining the statement and querying the `OTHER` column of the explain plan table for each `REMOTE` operation.

**See Also:**

[Example: Using Index and Table Statistics](optimizer-and-heterogeneous-services.md) for more information about how to interpret explain plans with remote references.

For example, consider the following statement:

    SELECT COUNT(*) FROM emp@remote_db WHERE hiredate < sysdate;

The statement returns the following output:

    COUNT(*)
    ----------
            14
    1 row selected.

The remote table scan is:

    SELECT hiredate FROM emp;

The predicate converted to a filter cannot be generated back and passed down to the remote operation because `sysdate` is not supported by the `remote_db` or evaluation rules. Thus `sysdate` must be executed locally.

**Note:**

Because the remote table scan operation is only partially related to the original query, the number of rows retrieved can be significantly larger than expected and can have a significant impact on performance.

#### Rule E: SQL statement containing a table expression cannot be remote-mapped.

This limitation is not directly encountered because table expressions are not supported in the heterogeneous access module.

#### Rule F: If a SQL statement selects LONG data, the statement must be mapped to the node where the table containing the LONG data resides.

Consider the following type of statement:

    SELECT long1 FROM table_with_long@remote_db, dual;

The previous statement returns the following error message (if callback links are not supported):

    ORA-02025: all tables in the SQL statement must be at the remote database

#### Rule G: The statement must be mapped to the node on which the table or tables with columns referenced in the FOR UPDATE OF clause resides when the SQL statement is of form "SELECT...FOR UPDATE OF..."

When the SQL statement is of the form `SELECT...FOR UPDATE OF..., `the statement must be mapped to the node on which the table or tables with columns referenced in the `FOR UPDATE OF` clause resides.

For example, consider the following statement:

    SELECT ename FROM emp@remote_db WHERE hiredate < sysdate FOR UPDATE OF empno;

The previous statement returns the following error message if it cannot be remote-mapped:

    ORA-02070: database REMOTE_DB does not support special functions in this context

#### Rule H: If the SQL statement contains sequences, then the statement must be mapped to the site where each sequence is located.

This rule is not encountered for the heterogeneous access module because remote non-Oracle sequences are not supported.

#### Rule I: If the statement contains user-defined operators, then the statement must be mapped to the node where each operator is defined.

If the statement contains user-defined operators, the entire statement needs to be remote-mapped to the database node where the operator is defined.

#### Rule J: A statement containing duplicate bind variables cannot be remote-mapped.

The workaround for this restriction is to use unique bind variables and bind by number.

**Parent topic:** Constraints on SQL in a Distributed Environment
