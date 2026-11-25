By checking the syntax and semantics of embedded SQL statements and PL/SQL blocks, the Oracle Precompilers help you quickly find and fix coding mistakes. This appendix shows you how to use the SQLCHECK option to control the type and extent of checking.

Topics are:

- Syntactic and Semantic Checking Basics

- Controlling the Type and Extent of Checking

- Specifying SQLCHECK=SEMANTICS

### D.1 Syntactic and Semantic Checking Basics

Rules of syntax specify how language elements are sequenced to form valid statements. Thus, syntactic checking verifies that keywords, object names, operators, delimiters, and so on are placed correctly in your SQL statement. It also applies to procedures and functions called from PL/SQL blocks. For example, the following embedded SQL statements contain syntax errors:

    * --  misspelled keyword WHERE
         EXEC SQL DELETE FROM EMP WERE DEPTNO = 20 END-EXEC.
    * --  missing parentheses around column names COMM and SAL
         EXEC SQL
             INSERT INTO EMP COMM, SAL VALUES (NULL, 1500)
         END-EXEC.

Rules of semantics specify how valid external references are made. Thus, semantic checking verifies that references to database objects and host variables are valid and that host-variable datatypes are correct. For example, the following embedded SQL statements contain semantic errors:

    * --  nonexistent table, EMPP
         EXEC SQL DELETE FROM EMPP WHERE DEPTNO = 20 END-EXEC.
    * --  undeclared host variable, EMP-NAME
         EXEC SQL SELECT * FROM EMP WHERE ENAME = :EMP-NAME END-EXEC.

The rules of SQL syntax and semantics are defined in the [Oracle Database SQL Language Reference](../sqlrf/index.md).

### D.2 Controlling the Type and Extent of Checking

You control the type and extent of checking by specifying the SQLCHECK option on the command line. With SQLCHECK, the type of checking can be syntactic, or both syntactic and semantic. The extent of checking can include data manipulation statements and PL/SQL blocks. However, SQLCHECK cannot check dynamic SQL statements because they are not defined fully until run time.

You can specify the following values for SQLCHECK:

- SEMANTICS \| FULL

- SYNTAX \| LIMITED

The values SEMANTICS and FULL are equivalent, as are the values SYNTAX and LIMITED. The default value is SYNTAX.

### D.3 Specifying SQLCHECK=SEMANTICS

When SQLCHECK=SEMANTICS, the precompiler checks the syntax and semantics of

- Data manipulation statements such as INSERT and UPDATE.

- PL/SQL blocks.

However, only syntactic checking is done on data manipulation statements that use the AT db_name clause.

The precompiler gets the information for a semantic check from embedded DECLARE TABLE statements or, if you specify the option USERID, by connecting to the database and accessing the data dictionary.

If you connect to the database but some table information cannot be found in the data dictionary, you must use DECLARE TABLE statements to supply the missing information. A DECLARE TABLE definition overrides a data dictionary definition if they conflict.

When checking data manipulation statements, the precompiler uses the Oracle set of syntax rules found in the [Oracle Database SQL Language Reference ](../sqlrf/index.md)but uses a stricter set of semantic rules. As a result, existing applications written for earlier versions of Oracle might not precompile successfully when SQLCHECK=SEMANTICS.

Specify SQLCHECK=SEMANTICS when precompiling new programs. If you embed PL/SQL blocks in a host program, you must specify SQLCHECK=SEMANTICS.

#### D.3.1 Enabling a Semantic Check

When SQLCHECK=SEMANTICS, the precompiler can get information needed for a semantic check in either of the following ways:

- Connect to Oracle and access the data dictionary

- Use embedded DECLARE TABLE statements

##### D.3.1.1 Connecting to Oracle

To do a semantic check, the precompiler can connect to the database that maintains definitions of tables and views referenced in your host program. After connecting, the precompiler accesses the data dictionary for needed information. The data dictionary stores table and column names, table and column constraints, column lengths, column datatypes, and so on.

If some of the needed information cannot be found in the data dictionary (because your program refers to a table not yet created, for example), you must supply the missing information using the DECLARE TABLE statement.

To connect to the database, specify the option USERID on the command line, using the syntax

    USERID=username/password

where username and password comprise a valid Oracle userid. If you omit the password, you are prompted for it. If, instead of a username and password, you specify

    USERID=/

the precompiler tries to connect to the database automatically with the userid

    <prefix><username>

where prefix is the value of the initialization parameter OS_AUTHENT_PREFIX (the default value is OPS\$) and username is your operating system user or task name.

If you try connecting, but cannot (for example, if the database is unavailable), the precompiler stops processing and issues an error message. If you omit the option USERID, the precompiler must get needed information from embedded DECLARE TABLE statements.

##### D.3.1.2 Using DECLARE TABLE

The precompiler can do a semantic check without connecting to the database as long as your program does not call any stored procedures or functions from an anonymous PL/SQL block. To do the check, the precompiler must get information about tables and views from embedded DECLARE TABLE directives. Thus, every table referenced in a data manipulation statement or PL/SQL block must be defined in a DECLARE TABLE statement.

The syntax of the DECLARE TABLE statement is

         EXEC SQL DECLARE table_name TABLE
             (col_name col_datatype [DEFAULT expr] [NULL|NOT NULL], ...)
         END-EXEC.

where expr is any expression that can be used as a default column value in the CREATE TABLE statement. col_datatype is an Oracle column declaration. Only integers can be used, not expressions. See "[DECLARE TABLE (Oracle Embedded SQL Directive)](embedded-SQL-statements-and-precompiler-directives.md) ".

If you use DECLARE TABLE to define a database table that already exists, the precompiler uses your definition, ignoring the one in the data dictionary.
