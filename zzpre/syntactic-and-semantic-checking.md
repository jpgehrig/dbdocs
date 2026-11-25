This appendix contains the following sections:

- What Is Syntactic and Semantic Checking?

- About Controlling the Type and Extent of Checking

- About Specifying SQLCHECK=SEMANTICS

By checking the syntax and semantics of embedded SQL statements and PL/SQL blocks, the Oracle Precompilers help you quickly find and fix coding mistakes. This appendix shows you how to use the `SQLCHECK` option to control the type and extent of checking.

### D.1 What Is Syntactic and Semantic Checking?

Rules of syntax specify how language elements are sequenced to form valid statements. Thus, syntactic checking verifies that keywords, object names, operators, delimiters, and so on are placed correctly in your SQL statement. For example, the following embedded SQL statements contain syntax errors:

    -- misspelled keyword WHERE
    EXEC SQL DELETE FROM EMP WERE DEPTNO = 20;
    -- missing parentheses around column names COMM and SAL
    EXEC SQL INSERT INTO EMP COMM, SAL VALUES (NULL, 1500);

Rules of semantics specify how valid external references are made. Thus, semantic checking verifies that references to database objects and host variables are valid and that host-variable datatypes are correct. For example, the following embedded SQL statements contain semantic errors:

    -- nonexistent table, EMPP
    EXEC SQL DELETE FROM EMPP WHERE DEPTNO = 20;
    -- undeclared host variable, emp_name
    EXEC SQL SELECT * FROM EMP WHERE ENAME = :emp_name;

The rules of SQL syntax and semantics are defined in the [Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md).

### D.2 About Controlling the Type and Extent of Checking

You control the type and extent of checking by specifying the `SQLCHECK` option on the command line. With `SQLCHECK`, the type of checking can be syntactic, semantic, or both. The extent of checking can include data manipulation statements and PL/SQL blocks. However, `SQLCHECK` cannot check dynamic SQL statements because they are not defined fully until run time.

You can specify the following values for `SQLCHECK`:

- `SEMANTICS|FULL`

- `SYNTAX|LIMITED|NONE`

The values `SEMANTICS` and `FULL` are equivalent, as are the values `SYNTAX` and `LIMITED`. The default value is `SYNTAX`.

### D.3 About Specifying SQLCHECK=SEMANTICS

When `SQLCHECK=SEMANTICS`, the precompiler checks the syntax and semantics of:

- Data manipulation statements such as `INSERT` and `UPDATE`

- PL/SQL blocks

However, the precompiler checks only the syntax of remote data manipulation statements (those using the `AT` `db_name` clause).

The precompiler gets the information for a semantic check from embedded `DECLARE` `TABLE` statements or, if you specify the option `USERID`, by connecting to Oracle and accessing the data dictionary. You need not connect to Oracle if every table referenced in a data manipulation statement or PL/SQL block is defined in a `DECLARE` `TABLE` statement.

If you connect to Oracle but some information cannot be found in the data dictionary, then you must use `DECLARE` `TABLE` statements to supply the missing information. A `DECLARE` `TABLE` definition overrides a data dictionary definition if they conflict.

When checking data manipulation statements, the precompiler uses the Oracle database version 7 set of syntax rules found in the [Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md) but uses a stricter set of semantic rules. As a result, existing applications written for earlier versions of Oracle might not precompile successfully when `SQLCHECK=SEMANTICS`.

Specify `SQLCHECK=SEMANTICS` when precompiling new programs. If you embed PL/SQL blocks in a host program, then you must specify `SQLCHECK=SEMANTICS`.

#### D.3.1 About Enabling a Semantic Check

When `SQLCHECK=SEMANTICS`, the precompiler can get information needed for a semantic check in either of the following ways:

- Connect to Oracle and access the data dictionary

- Use embedded `DECLARE TABLE` statements

#### D.3.2 About Connecting to Oracle

To do a semantic check, the precompiler can connect to an Oracle database that maintains definitions of tables and views referenced in your host program. After connecting to Oracle, the precompiler accesses the data dictionary for needed information. The data dictionary stores table and column names, table and column constraints, column lengths, column datatypes, and so on.

If some of the needed information cannot be found in the data dictionary (because your program refers to a table not yet created, for example), you must supply the missing information using the `DECLARE TABLE` statement.

To connect to Oracle, specify the option `USERID` on the command line, using the syntax:

    USERID=username

where username is a valid Oracle userid. You are prompted for the password. If, instead of a username, you specify

    USERID=/

the precompiler tries to connect to Oracle automatically with the userid

    <prefix><username>

where prefix is the value of the Oracle initialization parameter `OS_AUTHENT_PREFIX` (the default value is null) and username is your operating system user or task name.

If you try connecting to Oracle but cannot (for example, if the database is unavailable), the precompiler stops processing and issues an error message. If you omit the option `USERID`, the precompiler must get needed information from embedded `DECLARE` `TABLE` statements.

#### D.3.3 About Using DECLARE TABLE

The precompiler can do a semantic check without connecting to Oracle. To do the check, the precompiler must get information about tables and views from embedded `DECLARE TABLE` statements. Thus, every table referenced in a data manipulation statement or PL/SQL block must be defined in a `DECLARE TABLE` statement.

The syntax of the `DECLARE TABLE` statement is:

    EXEC SQL DECLARE table_name TABLE
     (col_name col_datatype [DEFAULT expr] [NULL|NOT NULL], ...);

where expr is any expression that can be used as a default column value in the `CREATE TABLE` statement.

If you use `DECLARE TABLE` to define a database table that already exists, the precompiler uses your definition, ignoring the one in the data dictionary.
