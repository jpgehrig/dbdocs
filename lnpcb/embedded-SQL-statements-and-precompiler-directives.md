This appendix describes Oracle embedded SQL statements and directives. These statements and directives are prefaced in your source code with the keywords, EXEC SQL.

Note: Only statements which differ in syntax from non-embedded SQL are described in this appendix. For details of the non-embedded SQL statements, see the [Oracle Database SQL Language Reference.](../sqlrf/index.md)

This appendix contains the following sections:

- Summary of Precompiler Directives and Embedded SQL Statements

- About the Statement Descriptions

- How to Read Syntax Diagrams

- ALLOCATE (Executable Embedded SQL Extension)

- ALLOCATE DESCRIPTOR (Executable Embedded SQL)

- CALL (Executable Embedded SQL)

- CLOSE (Executable Embedded SQL)

- COMMIT (Executable Embedded SQL)

- CONNECT (Executable Embedded SQL Extension)

- CONTEXT ALLOCATE (Executable Embedded SQL Extension)

- CONTEXT FREE (Executable Embedded SQL Extension)

- CONTEXT USE (Oracle Embedded SQL Directive)

- DECLARE CURSOR (Embedded SQL Directive)

- DECLARE DATABASE (Oracle Embedded SQL Directive)

- DECLARE STATEMENT (Embedded SQL Directive)

- DECLARE TABLE (Oracle Embedded SQL Directive)

- DELETE (Executable Embedded SQL)

- DESCRIBE (Executable Embedded SQL)

- DESCRIBE DESCRIPTOR (Executable Embedded SQL)

- ENABLE THREADS (Executable Embedded SQL Extension)

- EXECUTE ... END-EXEC (Executable Embedded SQL Extension)

- EXECUTE (Executable Embedded SQL)

- EXECUTE DESCRIPTOR (Executable Embedded SQL

- EXECUTE IMMEDIATE (Executable Embedded SQL)

- FETCH (Executable Embedded SQL)

- FETCH DESCRIPTOR (Executable Embedded SQL)

- FREE (Executable Embedded SQL Extension)

- GET DESCRIPTOR (Executable Embedded SQL)

- INSERT (Executable Embedded SQL)

- LOB APPEND (Executable Embedded SQL Extension)

- LOB ASSIGN (Executable Embedded SQL Extension)

- LOB CLOSE (Executable Embedded SQL Extension)

- LOB COPY (Executable Embedded SQL Extension)

- LOB CREATE TEMPORARY (Executable Embedded SQL Extension)

- LOB DESCRIBE (Executable Embedded SQL Extension)

- LOB DISABLE BUFFERING (Executable Embedded SQL Extension)

- LOB ENABLE BUFFERING (Executable Embedded SQL Extension)

- LOB ERASE (Executable Embedded SQL Extension)

- LOB FILE CLOSE ALL (Executable Embedded SQL Extension)

- LOB FILE SET (Executable Embedded SQL Extension)

- LOB FLUSH BUFFER (Executable Embedded SQL Extension)

- LOB FREE TEMPORARY (Executable Embedded SQL Extension)

- LOB LOAD (Executable Embedded SQL Extension)

- LOB OPEN (Executable Embedded SQL Extension)

- LOB READ (Executable Embedded SQL Extension)

- LOB TRIM (Executable Embedded SQL Extension)

- LOB WRITE (Executable Embedded SQL Extension)

- OPEN (Executable Embedded SQL)

- OPEN DESCRIPTOR (Executable Embedded SQL)

- PREPARE (Executable Embedded SQL)

- ROLLBACK (Executable Embedded SQL)

- SAVEPOINT (Executable Embedded SQL)

- SET DESCRIPTOR (Executable Embedded SQL)

- SELECT (Executable Embedded SQL)

- UPDATE (Executable Embedded SQL)

- VAR (Oracle Embedded SQL Directive)

- WHENEVER (Embedded SQL Directive)

### E.1 Summary of Precompiler Directives and Embedded SQL Statements

Embedded SQL statements place DDL, DML, and Transaction Control statements within a procedural language program. Embedded SQL is supported by the Oracle Precompilers. Table E-2 provides a functional summary of the embedded SQL statements and directives.

The Source/Type column in Table E-2 is displayed in the format source/type where:

Table E-1 Source/Type Column Meaning

| SQL Statements | Directives                                                |
|:---------------|:----------------------------------------------------------|
| source         | Is either standard SQL (S) or an Oracle extension (O).    |
| type           | Is either an executable (E) statement or a directive (D). |

Table E-2 Precompiler Directives and Embedded SQL Statements and Clauses

| EXEC SQL Statement    | Source/Type | Purpose                                                                                                         |
|:----------------------|:------------|:----------------------------------------------------------------------------------------------------------------|
| ALLOCATE              | O/E         | To allocate memory for a cursor variable, LOB locator or ROWID.                                                 |
| ALLOCATE DESCRIPTOR   | S/E         | To allocate a descriptor for ANSI dynamic SQL.                                                                  |
| CALL                  | S/E         | Call a stored procedure.                                                                                        |
| CLOSE                 | S/E         | To disable a cursor.                                                                                            |
| COMMIT                | S/E         | To make all database changes permanent.                                                                         |
| CONNECT               | O/E         | To log on to a database instance.                                                                               |
| CONTEXT ALLOCATE      | O/E         | To allocate memory for a SQLLIB runtime context.                                                                |
| CONTEXT FREE          | O/E         | To free memory for a SQLLIB runtime context.                                                                    |
| CONTEXT USE           | O/E         | To specify a SQLLIB runtime context.                                                                            |
| DEALLOCATE DESCRIPTOR | S/E         | To deallocate a descriptor area to free memory.                                                                 |
| DECLARE CURSOR        | S/D         | To declare a cursor, associating it with a query.                                                               |
| DECLARE DATABASE      | O/D         | To declare an identifier for a nondefault database to be accessed in subsequent embedded SQL statements.        |
| DECLARE STATEMENT     | S/D         | To assign a SQL variable name to a SQL statement.                                                               |
| DECLARE TABLE         | O/D         | To declare the table structure for semantic checking of embedded SQL statements by the Oracle Precompiler.      |
| DELETE                | S/E         | To remove rows from a table or from a view's base table.                                                        |
| DESCRIBE              | S/E         | To initialize a descriptor, a structure holding host variable descriptions.                                     |
| DESCRIBE DECRIPTOR    | S/E         | To obtain information about an ANSI SQL statement, and store it in a descriptor.                                |
| ENABLE THREADS        | O/E         | To initialize a process that supports multiple threads.                                                         |
| EXECUTE...END-EXEC    | O/E         | To execute an anonymous PL/SQL block.                                                                           |
| EXECUTE               | S/E         | To execute a prepared dynamic SQL statement.                                                                    |
| EXECUTE DESCRIPTOR    | S/E         | To execute a prepared statement using ANSI Dynamic SQL.                                                         |
| EXECUTE IMMEDIATE     | S/E         | To prepare and execute a SQL statement with no host variables.                                                  |
| FETCH                 | S/E         | To retrieve rows selected by a query.                                                                           |
| FETCH DESCRIPTOR      | S/E         | To retrieve rows selected by a query using ANSI Dynamic SQL.                                                    |
| FREE                  | S/E         | To free memory used by a cursor, LOB locator, or ROWID.                                                         |
| GET DESCRIPTOR        | S/E         | To move information from an ANSI SQL descriptor area into host variables.                                       |
| INSERT                | S/E         | To add rows to a table or to a view's base table.                                                               |
| LOB APPEND            | O/E         | To append a LOB to the end of another lOB.                                                                      |
| LOB ASSIGN            | O/E         | To assign a LOB or BFILE locator to another locator.                                                            |
| LOB CLOSE             | O/E         | To close an open LOB or BFILE.                                                                                  |
| LOB COPY              | O/E         | To copy all or part of a LOB value into another LOB.                                                            |
| LOB CREATE TEMPORARY  | O/E         | To create a temporary LOB.                                                                                      |
| LOB DESCRIBE          | O/E         | To retrieve attributes from a LOB.                                                                              |
| LOB DISABLE BUFFERING | O/E         | To disable LOB buffering.                                                                                       |
| LOB ENABLE BUFFERING  | O/E         | To enable LOB buffering.                                                                                        |
| LOB ERASE             | O/E         | To erase a given amount of LOB data starting from a given offset.                                               |
| LOB FILE CLOSE ALL    | O/E         | To close all open BFILE.                                                                                        |
| LOB FILE SET          | O/E         | To set DIRECTORY and FILENAME in a BFILE locator.                                                               |
| LOB FLUSH BUFFER      | O/E         | To write the LOB buffers to the database server.                                                                |
| LOB FREE TEMPORARY    | O/E         | To free temporary space for the LOB locator.                                                                    |
| LOB LOAD              | O/E         | To copy all or part of a BFILE into an internal LOB.                                                            |
| LOB OPEN              | O/E         | To open a LOB or BFILE to read or read/write access.                                                            |
| LOB READ              | O/E         | To read all or part of a LOB or BFILE into a buffer.                                                            |
| LOB TRIM              | O/E         | To truncate a lob value.                                                                                        |
| LOB WRITE             | O/E         | To write the contents of a buffer to a LOB.                                                                     |
| OPEN                  | S/E         | To execute the query associated with a cursor.                                                                  |
| OPEN DESCRIPTOR       | S/E         | To execute the query associated with a cursor in ANSI Dynamic SQL.                                              |
| PREPARE               | S/E         | To parse a dynamic SQL statement.                                                                               |
| ROLLBACK              | S/E         | To end the current transaction and discard all changes.                                                         |
| SAVEPOINT             | S/E         | To identify a point in a transaction to which you can later roll back.                                          |
| SELECT                | S/E         | To retrieve data from one or more tables, views, or snapshots, assigning the selected values to host variables. |
| SET DESCRIPTOR        | S/E         | To set information in the ANSI SQL descriptor area from host variables.                                         |
| UPDATE                | S/E         | To change existing values in a table or in a view's base table.                                                 |
| VAR                   | O/D         | To override the default datatype and assign a specific Oracle external datatype to a host variable.             |
| WHENEVER              | S/D         | To specify handling for error and warning conditions.                                                           |

### E.2 About the Statement Descriptions

The directives, and statements appear alphabetically. The description of each contains the following sections:

| Directives              | Description                                                                                                                                                                              |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Purpose                 | Describes the basic uses of the statement.                                                                                                                                               |
| Prerequisites           | Lists privileges you must have and steps that you must take before using the statement. Unless otherwise noted, most statements also require that the database be open by your instance. |
| Syntax                  | Shows the syntax diagram with the keywords and parameters of the statement.                                                                                                              |
| Keywords and Parameters | Describes the purpose of each keyword and parameter.                                                                                                                                     |
| Usage Notes             | Discusses how and when to use the statement.                                                                                                                                             |
| Prerequisites           | Lists privileges you must have and steps that you must take before using the statement. Unless otherwise noted, most statements also require that the database be open by your instance. |
| Syntax                  | Shows the syntax diagram with the keywords and parameters of the statement.                                                                                                              |

### E.3 How to Read Syntax Diagrams

Syntax diagrams are used to illustrate embedded SQL syntax. They are drawings that depict valid syntax.

Trace each diagram from left to right, in the direction shown by the arrows.

Statements keywords appear in UPPER CASE inside rectangles. Type them exactly as shown in the rectangles. Parameters appear in lower case inside ovals. Variables are used for the parameters. Operators, delimiters, and terminators appear inside circles.

If the syntax diagram has more than one path, you can choose any path to travel.

If you have the choice of more than one keyword, operator, or parameter, your options appear in a vertical list. In the following example, you can travel down the vertical line as far as you like, then continue along any horizontal line:

![Description of first.eps follows](img/first.png)
[Description of the illustration first.eps](img_text/first.md)

According to the diagram, all of the following statements are valid:

    EXEC SQL WHENEVER NOT FOUND ...
    EXEC SQL WHENEVER SQLERROR ...
    EXEC SQL WHENEVER SQLWARNING ...

#### E.3.1 Statement Terminator

In all Pro\*COBOL EXEC SQL diagrams, each statement is understood to end with the token END-EXEC.

#### E.3.2 Required Keywords and Parameters

Required keywords and parameters can appear singly or in a vertical list of alternatives. Single required keywords and parameters appear on the main path, that is, on the horizontal line you are currently traveling. In the following example, cursor is a required parameter:

![Description of reqp.eps follows](img/reqp.png)
[Description of the illustration reqp.eps](img_text/reqp.md)

If there is a cursor named EMPCURSOR, then, according to the diagram, the following statement is valid:

    EXEC SQL CLOSE EMPCURSOR END-EXEC.

If any of the keywords or parameters in a vertical list appears on the main path, one of them is required. That is, you must choose one of the keywords or parameters, but not necessarily the one that appears on the main path. In the following example, you must choose one of the four actions:

![Description of reqp1.eps follows](img/reqp1.png)
[Description of the illustration reqp1.eps](img_text/reqp1.md)

#### E.3.3 Optional Keywords and Parameters

If keywords and parameters appear in a vertical list preceding the main path, they are optional. In the following example, instead of traveling down a vertical line, you can continue along the main path:

![Description of optional.eps follows](img/optional.png)
[Description of the illustration optional.eps](img_text/optional.md)

If there is a database named oracle2, then, according to the diagram, all of the following statements are valid:

         EXEC SQL ROLLBACK END-EXEC.
         EXEC SQL ROLLBACK WORK END-EXEC.
         EXEC SQL AT ORACLE2 ROLLBACK END-EXEC.

#### E.3.4 Syntax Loops

Loops let you repeat the syntax within them as many times as you like. In the following example, column_name is inside a loop. So, after choosing one column name, you can go back repeatedly to choose another.

![Description of syntax.eps follows](img/syntax.png)
[Description of the illustration syntax.eps](img_text/syntax.md)

If DEBIT, CREDIT, and BALANCE are column names, then, according to the diagram, all of the following statements are valid:

    EXEC SQL SELECT DEBIT INTO ...
    EXEC SQL SELECT CREDIT, BALANCE INTO ...
    EXEC SQL SELECT DEBIT, CREDIT, BALANCE INTO ...

#### E.3.5 Multi-part Diagrams

Read a multi-part diagram as if all the main paths were joined end-to-end. The following example is a two-part diagram:

![Description of part.eps follows](img/part.png)
[Description of the illustration part.eps](img_text/part.md)

According to the diagram, the following statement is valid:

         EXEC SQL PREPARE statement_name FROM :host_string END-EXEC.

#### E.3.6 Oracle Names

The names of Oracle database objects, such as tables and columns, must not exceed 30 characters in length. The first character must be a letter, but the rest can be any combination of letters, numerals, dollar signs (\$), pound signs (#), and underscores (\_).

However, if a name is enclosed by quotation marks ("), it can contain any combination of legal characters, including spaces but excluding quotation marks.

Oracle names are not case-sensitive except when enclosed by quotation marks.

### E.4 ALLOCATE (Executable Embedded SQL Extension)

#### Purpose

To allocate a cursor variable to be referenced in a PL/SQL block, or to allocate a LOB locator, or a ROWID .

#### Prerequisites

A cursor variable (see [Embedded PL/SQL](embedded-PLSQL.md)) of type SQL-CURSOR must be declared before allocating memory for the cursor variable.

#### Syntax

![Description of allocob.eps follows](img/allocob.png)
[Description of the illustration allocob.eps](img_text/allocob.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                             |
|:------------------------|:----------------------------------------------------------------------------------------|
| cursor_variable         | A cursor variable of type SQL-CURSOR                                                    |
| host_ptr                | A variable of type SQL-ROWID for a ROWID, or SQL-BLOB, SQL-CLOB, or SQL-NCLOB for a LOB |

#### Usage Notes

Whereas a cursor is static, a cursor variable is dynamic because it is not tied to a specific query. You can open a cursor variable for any type-compatible query.

#### Example

This partial example illustrates the use of the ALLOCATE statement:

           ...
     01  EMP-CUR       SQL-CURSOR.
     01  EMP-REC.
         ...
         EXEC SQL ALLOCATE :EMP-CUR END-EXEC.
         ...

#### Related Topics

CLOSE (Executable Embedded SQL) .

EXECUTE (Executable Embedded SQL).

FETCH (Executable Embedded SQL) .

FREE (Executable Embedded SQL Extension).

### E.5 ALLOCATE DESCRIPTOR (Executable Embedded SQL)

#### Purpose

An ANSI dynamic SQL statement that allocates a descriptor.

#### Prerequisites

None.

#### Syntax

![Description of alldesc.eps follows](img/alldesc.png)
[Description of the illustration alldesc.eps](img_text/alldesc.md)

#### Keywords and Parameters

| Keywords and Parameters            | Description                                                                                 |
|:-----------------------------------|:--------------------------------------------------------------------------------------------|
| array_size<br>integer              | Host variable containing number of rows to be processed.<br>Number of rows to be processed. |
| descriptor_name<br>descriptor name | Host variable containing number of rows to be processed.<br>Number of rows to be processed. |
| GLOBAL \| LOCAL                    | LOCAL (the default) means file scope, as opposed to GLOBAL, which means application scope.  |
| WITH MAX integer                   | Maximum number of host variables. The default is 100.                                       |

#### Usage Notes

Use DYNAMIC=ANSI precompiler option. For information on using this statement, see "[ALLOCATE DESCRIPTOR](ANSI-dynamic-SQL.md)".

#### Example

         EXEC SQL
           FOR :batch ALLOCATE DESCRIPTOR GLOBAL :binddes WITH MAX 25
         END-EXEC.

#### Related Topics

DESCRIBE DESCRIPTOR (Executable Embedded SQL) .

GET DESCRIPTOR (Executable Embedded SQL).

SET DESCRIPTOR (Executable Embedded SQL).

### E.6 CALL (Executable Embedded SQL)

#### Purpose

To call a stored procedure.

#### Prerequisites

An active database connection must exist.

#### Syntax

![Description of call.eps follows](img/call.png)
[Description of the illustration call.eps](img_text/call.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                                                                                                                              |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| schema                  | Is the schema containing the procedure. If you omit schema, Oracle assumes the procedure is in your own schema.                                                                                                                                                          |
| pkg                     | The package where the procedure is stored.                                                                                                                                                                                                                               |
| st_proc                 | The stored procedure to be called.                                                                                                                                                                                                                                       |
| db_link                 | The complete or partial name of a database link to a remote database where the procedure is located. For information on referring to database links, see [References to Objects in Remote Databases](../sqlrf/Syntax-for-Schema-Objects-and-Parts-in-SQL-Statements.md). |
| expr                    | The list of expressions that are the parameters of the procedure.                                                                                                                                                                                                        |
| ret_var                 | The host variable that receives the returned value of a function.                                                                                                                                                                                                        |
| ret_ind                 | The indicator variable for ret_var.                                                                                                                                                                                                                                      |

#### Usage Notes

For more about this statement, see [Calling a Stored PL/SQL or Java Subprogram](embedded-PLSQL.md).

For a complete discussion of stored procedures, see [Developing Applications with Multiple Programming Languages](../adfns/external-procedures.md).

#### Example

     ...
         05  EMP-NAME      PIC X(10) VARYING.
         05  EMP-NUMBER    PIC S9(4) COMP VALUE ZERO.
         05  SALARY        PIC S9(5)V99 COMP-3 VALUE ZERO.
    ...
          05  D-EMP-NUMBER  PIC 9(4).
    ...
          ACCEPT D-EMP-NUMBER.
          EXEC SQL
            CALL mypkge.getsal(:EMP-NUMBER, :D-EMP-NUMBER, :EMP-NAME) INTO :SALARY
          END-EXEC.
    ...

#### Related Topics

None

### E.7 CLOSE (Executable Embedded SQL)

#### Purpose

To disable a cursor, freeing the resources acquired by opening the cursor, and releasing parse locks.

#### Prerequisites

The cursor or cursor variable must be open and MODE=ANSI.

#### Syntax

![Description of close.eps follows](img/close.png)
[Description of the illustration close.eps](img_text/close.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                       |
|:------------------------|:----------------------------------|
| cursor                  | The cursor to be closed           |
| cursor_variable         | The cursor variable to be closed. |

#### Usage Notes

Rows cannot be fetched from a closed cursor. A cursor need not be closed to be reopened. The HOLD_CURSOR and RELEASE_CURSOR precompiler options alter the effect of the CLOSE statement. For information on these options, see [Precompiler Options](precompiler-options.md).

#### Example

This example illustrates the use of the CLOSE statement:

         EXEC SQL CLOSE EMP-CUR END-EXEC.

#### Related Topics

DECLARE CURSOR (Embedded SQL Directive).

OPEN (Executable Embedded SQL) .

PREPARE (Executable Embedded SQL).

### E.8 COMMIT (Executable Embedded SQL)

#### Purpose

To end your current transaction, making permanent all its changes to the database and optionally freeing all resources and disconnecting from the database server.

#### Prerequisites

To commit your current transaction, no privileges are necessary.

To manually commit a distributed in-doubt transaction that you originally committed, you must have FORCE TRANSACTION system privilege. To manually commit a distributed in-doubt transaction that was originally committed by another user, you must have FORCE ANY TRANSACTION system privilege.

#### Syntax

![Description of commit.eps follows](img/commit.png)
[Description of the illustration commit.eps](img_text/commit.md)

#### Keyword and Parameters

| Keywords and Parameters | Description                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AT                      | Identifies the database to which the COMMIT statement is issued. The database can be identified by either:                                                                                                                                                                                                                                                                                                                   |
| db_name                 | A database identifier declared in a previous DECLARE DATABASE statement or used in a CONNECT statement.                                                                                                                                                                                                                                                                                                                      |
| host_variable           | If you omit this clause, Oracle issues the statement to your default database.                                                                                                                                                                                                                                                                                                                                               |
| WORK                    | Is supported only for compliance with standard SQL. The statements COMMIT and COMMIT WORK are equivalent.                                                                                                                                                                                                                                                                                                                    |
| COMMENT                 | Specifies a comment to be associated with the current transaction. The 'text' is a quoted literal of up to 50 characters that Oracle stores in the data dictionary view DBA_2PC_PENDING along with the transaction ID if the transaction becomes in-doubt.                                                                                                                                                                   |
| RELEASE                 | Frees all resources and disconnects the application from the Oracle Server.                                                                                                                                                                                                                                                                                                                                                  |
| FORCE                   | Manually commits an in-doubt distributed transaction. The transaction is identified by the 'text' containing its local or global transaction ID. To find the IDs of such transactions, query the data dictionary view DBA_2PC_PENDING. You can also use the optional integer to explicitly assign the transaction a system change number (SCN). If you omit the integer, the transaction is committed using the current SCN. |

#### Usage Notes

Always explicitly commit or rollback the last transaction in your program by using the COMMIT or ROLLBACK statement and the RELEASE option. Oracle automatically rolls back changes if the program terminates abnormally.

The COMMIT statement has no effect on host variables or on the flow of control in the program. For more information on this statement, see "[Using the COMMIT Statement](database-concepts.md)".

#### Example

This example illustrates the use of the embedded SQL COMMIT statement:

         EXEC SQL AT SALESDB COMMIT RELEASE END-EXEC.

#### Related Topics

ROLLBACK (Executable Embedded SQL) .

SAVEPOINT (Executable Embedded SQL) .

### E.9 CONNECT (Executable Embedded SQL Extension)

#### Purpose

To logon to an Oracle database.

#### Prerequisites

You must have CREATE SESSION system privilege in the specified database.

#### Syntax

![Description of connect.eps follows](img/connect.png)
[Description of the illustration connect.eps](img_text/connect.md)

#### Keyword and Parameters

| Keywords and Parameters           | Description                                                                                                                                                                                                |
|:----------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| user<br>password                  | Specifies your username and password separately.                                                                                                                                                           |
| user_password                     | Is a single host variable containing the connect string username/password\[@dbname\].<br>To allow Oracle to verify your connection through your operating system, specify "/" as the :user_password value. |
| AT                                | Identifies the database to which the connection is made. The database can be identified by either:                                                                                                         |
| db_name                           | A database identifier declared in a previous DECLARE DATABASE statement.                                                                                                                                   |
| host_variable                     | A host variable whose value is a previously declared db_name.                                                                                                                                              |
| USING                             | Specifies the Oracle Net Services database specification string used to connect to a nondefault database. If you omit this clause, you are connected to your default database.                             |
| ALTER AUTHORIZATION               | Change password to the following string.                                                                                                                                                                   |
| new_password                      | New password string.                                                                                                                                                                                       |
| IN SYSDBA MODE<br>IN SYSOPER MODE | Connect with SYSDBA or SYSOPER system privileges. Not allowed when ALTER AUTHORIZATION is used, or precompiler option AUTO_CONNECT is set to YES.                                                          |

#### Usage Notes

A program can have multiple connections, but can only connect once to your default database. For more information on this statement, see: "[Concurrent Logons](database-concepts.md)".

#### Example

The following example illustrate the use of CONNECT:

         EXEC SQL CONNECT :USERNAME
              IDENTIFIED BY :PASSWORD
         END-EXEC.

You can also use this statement in which the value of :userid is the value of :username and :password separated by a "/" such as 'SCOTT/TIGER':

         EXEC SQL CONNECT :USERID END-EXEC.

#### Related Topics

COMMIT (Executable Embedded SQL) .

DECLARE DATABASE (Oracle Embedded SQL Directive).

ROLLBACK (Executable Embedded SQL) .

### E.10 CONTEXT ALLOCATE (Executable Embedded SQL Extension)

#### Purpose

To initialize a SQLLIB runtime context that is referenced in an EXEC SQL CONTEXT USE statement.

#### Prerequisites

The runtime context must be declared of type SQL-CONTEXT.

#### Syntax

![Description of conall.eps follows](img/conall.png)
[Description of the illustration conall.eps](img_text/conall.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                     |
|:------------------------|:----------------------------------------------------------------|
| context                 | The SQLLIB runtime context for which memory is to be allocated. |

#### Usage Notes

For more information on this statement, see "[Embedded SQL Statements and Directives for Runtime Contexts](multithreaded-applications.md)".

#### Example

This example illustrates the use of a CONTEXT ALLOCATE statement in a Pro\*COBOL embedded SQL program:

         EXEC SQL CONTEXT ALLOCATE :ctx1 END-EXEC.

#### Related Topics

CONTEXT FREE (Executable Embedded SQL Extension).

CONTEXT USE (Oracle Embedded SQL Directive).

### E.11 CONTEXT FREE (Executable Embedded SQL Extension)

#### Purpose

To free all memory associated with a runtime context and place a null pointer in the host program variable.

#### Prerequisites

The CONTEXT ALLOCATE statement must be used to allocate memory for the specified runtime context before the CONTEXT FREE statement can free the memory allocated for it.

#### Syntax

![Description of confree.eps follows](img/confree.png)
[Description of the illustration confree.eps](img_text/confree.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                              |
|:------------------------|:-------------------------------------------------------------------------|
| context                 | The allocated runtime context for which the memory is to be deallocated. |

#### Usage Notes

For more information on this statement, see "[Embedded SQL Statements and Directives for Runtime Contexts](multithreaded-applications.md)".

#### Example

This example illustrates the use of a CONTEXT FREE statement in a Pro\*COBOL embedded SQL program:

         EXEC SQL CONTEXT FREE :ctx1 END-EXEC.

#### Related Topics

CONTEXT ALLOCATE (Executable Embedded SQL Extension).

CONTEXT USE (Oracle Embedded SQL Directive).

### E.12 CONTEXT USE (Oracle Embedded SQL Directive)

#### Purpose

To instruct the precompiler to use the specified SQLLIB runtime context on subsequent executable SQL statements

#### Prerequisites

The runtime context specified by the CONTEXT USE directive must be previously declared.

#### Syntax

![Description of conuse.eps follows](img/conuse.png)
[Description of the illustration conuse.eps](img_text/conuse.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                                                                                                                                                                       |
|:------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| context                 | The allocated runtime context to use for subsequent executable SQL statements that follow it. For example, after specifying in your source code which context to use (multiple contexts can be allocated), you can connect to the Oracle Server and perform database operations within the scope of that context. |
| DEFAULT                 | Indicates that the global context is to be used.                                                                                                                                                                                                                                                                  |

#### Usage Notes

This statement has no effect on declarative statements such as EXEC SQL INCLUDE or EXEC ORACLE OPTION. It works similarly to the EXEC SQL WHENEVER directive in that it affects all executable SQL statements which positionally follow it in a given source file without regard to standard C scope rules.

For more information on this statement, see "[Embedded SQL Statements and Directives for Runtime Contexts](multithreaded-applications.md)".

#### Example

This example illustrates the use of a CONTEXT USE directive in a Pro\*COBOL program:

         EXEC SQL CONTEXT USE :ctx1 END-EXEC.

#### Related Topics

CONTEXT ALLOCATE (Executable Embedded SQL Extension).

CONTEXT FREE (Executable Embedded SQL Extension).

### E.13 DEALLOCATE DESCRIPTOR (Embedded SQL Statement)

#### Purpose

An ANSI dynamic SQL statement that deallocates a descriptor area to free memory.

#### Prerequisites

The descriptor specified by the DEALLOCATE DESCRIPTOR statement must be previously allocated using the ALLOCATE DESCRIPTOR statement.

#### Syntax

![Description of dealdesc.eps follows](img/dealdesc.png)
[Description of the illustration dealdesc.eps](img_text/dealdesc.md)

#### Keywords and Parameters

| Keywords and Parameters               | Description                                                                                                   |
|:--------------------------------------|:--------------------------------------------------------------------------------------------------------------|
| GLOBAL \| LOCAL                       | LOCAL (the default) means file scope, as opposed to GLOBAL, which means application scope.                    |
| descriptor_name<br>'descriptor name'  | Host variable containing the name of the allocated ANSI descriptor.<br>Name of the allocated ANSI descriptor. |

#### Usage Notes

Use DYNAMIC=ANSI precompiler option.

For more information on this statement, see "[DEALLOCATE DESCRIPTOR](ANSI-dynamic-SQL.md)".

#### Example

         EXEC SQL DEALLOCATE DESCRIPTOR GLOBAL 'SELDES'  END-EXEC.

#### Related Topics

ALLOCATE DESCRIPTOR (Executable Embedded SQL).

DESCRIBE DESCRIPTOR (Executable Embedded SQL) .

GET DESCRIPTOR (Executable Embedded SQL).

PREPARE (Executable Embedded SQL).

SET DESCRIPTOR (Executable Embedded SQL).

### E.14 DECLARE CURSOR (Embedded SQL Directive)

#### Purpose

To declare a cursor, giving it a name and associating it with a SQL statement or a PL/SQL block.

#### Prerequisites

If you associate the cursor with an identifier for a SQL statement or PL/SQL block, you must have declared this identifier in a previous DECLARE STATEMENT statement.

#### Syntax

![Description of dclco.eps follows](img/dclco.png)
[Description of the illustration dclco.eps](img_text/dclco.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                                 |
|:------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AT                      | Identifies the database on which the cursor is declared. The database can be identified by either:                                                                          |
| db_name                 | Database identifier declared in a previous DECLARE DATABASE statement.                                                                                                      |
| host_variable           | Host variable whose value is a previously declared db_name.<br>If you omit this clause, Oracle declares the cursor on your default database.                                |
| cursor                  | Name of the cursor to be declared.                                                                                                                                          |
| WITH HOLD               | Cursor remains open after a COMMIT. The cursor must not be declared for UPDATE.                                                                                             |
| SELECT statement        | Is a SELECT statement to be associated with the cursor. The following statement cannot contain an INTO clause.                                                              |
| statement_name          | Identifies a SQL statement or PL/SQL block to be associated with the cursor. The statement_name or block_name must be previously declared in a DECLARE STATEMENT statement. |

#### Usage Notes

You must declare a cursor before referencing it in other embedded SQL statements. The scope of a cursor declaration is global within its precompilation unit and the name of each cursor must be unique in its scope. You cannot declare two cursors with the same name in a single precompilation unit.

You can reference the cursor in the WHERE clause of an UPDATE or DELETE statement using the CURRENT OF syntax, if the cursor has been opened with an OPEN statement and positioned on a row with a FETCH statement. For more information on this statement, see "[WITH HOLD Clause in DECLARE CURSOR Statements](database-concepts.md)".

By default, held cursors are closed after ROLLBACK to conform to SQL standard behavior. To have held cursors remain open after ROLLBACK for backward compatibility, set the command-line option, CWH_SQL99, to NO.

New para added for feature 25546-1

#### Example

This example illustrates the use of a DECLARE CURSOR statement:

         EXEC SQL DECLARE EMPCURSOR CURSOR
             FOR SELECT ENAME, EMPNO, JOB, SAL
             FROM EMP
             WHERE DEPTNO = :DEPTNO
         END-EXEC.

#### Related Topics

CLOSE (Executable Embedded SQL) .

DECLARE DATABASE (Oracle Embedded SQL Directive).

DECLARE STATEMENT (Embedded SQL Directive) .

DELETE (Executable Embedded SQL) .

FETCH (Executable Embedded SQL) .

OPEN (Executable Embedded SQL) .

PREPARE (Executable Embedded SQL).

SELECT (Executable Embedded SQL).

UPDATE (Executable Embedded SQL) .

### E.15 DECLARE DATABASE (Oracle Embedded SQL Directive)

#### Purpose

To declare an identifier for a nondefault database to be accessed in subsequent embedded SQL statements.

#### Prerequisites

You must have access to a username on the nondefault database.

#### Syntax

![Description of dcldbase.eps follows](img/dcldbase.png)
[Description of the illustration dcldbase.eps](img_text/dcldbase.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                             |
|:------------------------|:--------------------------------------------------------|
| db_name                 | The identifier established for the nondefault database. |

#### Usage Notes

You declare a db_name for a nondefault database so that other embedded SQL statements can refer to that database using the AT clause. Before issuing a CONNECT statement with an AT clause, you must declare a db_name for the nondefault database with a DECLARE DATABASE statement.

For more information on this statement, see "[Using Username/Password](database-concepts.md)".

#### Example

This example illustrates the use of a DECLARE DATABASE directive:

         EXEC SQL DECLARE ORACLE3 DATABASE END-EXEC.

#### Related Topics

COMMIT (Executable Embedded SQL)

CONNECT (Executable Embedded SQL Extension) .

DECLARE CURSOR (Embedded SQL Directive).

DECLARE STATEMENT (Embedded SQL Directive) .

DELETE (Executable Embedded SQL) .

EXECUTE (Executable Embedded SQL).

EXECUTE IMMEDIATE (Executable Embedded SQL).

INSERT (Executable Embedded SQL) .

SELECT (Executable Embedded SQL).

UPDATE (Executable Embedded SQL) .

### E.16 DECLARE STATEMENT (Embedded SQL Directive)

#### Purpose

To declare an identifier for a SQL statement or PL/SQL block to be used in other embedded SQL statements.

#### Prerequisites

None.

#### Syntax

![Description of dcl_stmt.eps follows](img/dcl_stmt.png)
[Description of the illustration dcl_stmt.eps](img_text/dcl_stmt.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                               |
|:------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AT                      | Identifies the database on which the SQL statement or PL/SQL block is declared. The database can be identified by either:                                                 |
| db_name                 | Database identifier declared in a previous DECLARE DATABASE statement.                                                                                                    |
| host_variable           | Host variable whose value is a previously declared db_name. If you omit this clause, Oracle Database declares the SQL statement or PL/SQL block on your default database. |
| statement_name          | Is the declared identifier for the statement or PL/SQL block.                                                                                                             |

#### Usage Notes

You must declare an identifier for a SQL statement or PL/SQL block with a DECLARE STATEMENT statement only if a DECLARE CURSOR statement referencing the identifier appears physically (not logically) in the embedded SQL program before the PREPARE statement that parses the statement or block and associates it with its identifier.

The scope of a statement declaration is global within its precompilation unit, like a cursor declaration. For more information on this statement, see "[DECLARE](Oracle-dynamic-SQL.md)".

#### Example I

This example illustrates the use of the DECLARE STATEMENT statement:

         EXEC SQL AT REMOTEDB
             DECLARE MYSTATEMENT STATEMENT
         END-EXEC.
         EXEC SQL PREPARE MYSTATEMENT FROM :MY-STRING
         END-EXEC.
         EXEC SQL EXECUTE MYSTATEMENT END-EXEC.

#### Example II

In this example, the DECLARE STATEMENT statement is required because the DECLARE CURSOR statement precedes the PREPARE statement:

         EXEC SQL DECLARE MYSTATEMENT STATEMENT END-EXEC.
         ...
         EXEC SQL DECLARE EMPCURSOR CURSOR FOR MYSTATEMENT END-EXEC.
         ...
         EXEC SQL PREPARE MYSTATEMENT FROM :MY-STRING END-EXEC.
         ...

#### Related Topics

CLOSE (Executable Embedded SQL) .

DECLARE DATABASE (Oracle Embedded SQL Directive).

FETCH (Executable Embedded SQL) .

OPEN (Executable Embedded SQL) .

PREPARE (Executable Embedded SQL).

### E.17 DECLARE TABLE (Oracle Embedded SQL Directive)

#### Purpose

To define the structure of a table or view, including each column's datatype, default value, and NULL or NOT NULL specification for semantic checking by the precompiler when option SQLCHECK=SEMANTICS (or FULL).

#### Prerequisites

None.

#### Syntax

![Description of dcltab.eps follows](img/dcltab.png)
[Description of the illustration dcltab.eps](img_text/dcltab.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                            |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| table                   | The name of the declared table.                                                                                                        |
| column                  | A column of the table.                                                                                                                 |
| datatype                | The datatype of a column. For information on Oracle datatypes, see "[The Oracle Database Datatypes](datatypes-and-host-variables.md)". |
| NOT NULL                | Specifies that a column cannot contain nulls.                                                                                          |

#### Usage Notes

Datatypes can only use integers (not expressions) for length, precision, scale. For more information on using this statement, see "[Specifying SQLCHECK=SEMANTICS](syntactic-and-semantic-checking.md)".

#### Example

The following statement declares the PARTS table with the PARTNO, BIN, and QTY columns:

         EXEC SQL DECLARE PARTS TABLE
             (PARTNO  NUMBER  NOT NULL,
              BIN     NUMBER,
              QTY     NUMBER)
         END-EXEC.

#### Related Topics

None.

### E.18 DELETE (Executable Embedded SQL)

#### Purpose

To remove rows from a table or from a view's base table.

#### Prerequisites

For you to delete rows from a table, the table must be in your own schema or you must have DELETE privilege on the table.

For you to delete rows from the base table of a view, the owner of the schema containing the view must have DELETE privilege on the base table. Also, if the view is in a schema other than your own, you must be granted DELETE privilege on the view.

The DELETE ANY TABLE system privilege also enables you to delete rows from any table or any view's base table.

#### Syntax

![Description of delete.eps follows](img/delete.png)
[Description of the illustration delete.eps](img_text/delete.md)

where the DML Returning clause is:

![Description of return.eps follows](img/return.png)
[Description of the illustration return.eps](img_text/return.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AT                      | Identifies the database to which the DELETE statement is issued. The database can be identified by either:<br>db_name:a database identifier declared in a previous DECLARE DATABASE statement.<br>host_variable: a host variable whose value is a previously declared db_name. <br>If you omit this clause, the DELETE statement is issued to your default database.                                                                                       |
| host_integer<br>integer | Limits the number of times the statement is executed if the WHERE clause contains array host variables. If you omit this clause, the database executes the statement once for each component of the smallest array.                                                                                                                                                                                                                                        |
| schema                  | The schema containing the table or view. If you omit schema, the database assumes the table or view is in your own schema.                                                                                                                                                                                                                                                                                                                                 |
| table view              | The name of a table from which the rows are to be deleted. If you specify view, the database deletes rows from the view's base table.                                                                                                                                                                                                                                                                                                                      |
| dblink                  | The complete or partial name of a database link to a remote database where the table or view is located. For information on referring to database links, see [Basic Elements of Oracle SQL](../sqlrf/Basic-Elements-of-Oracle-SQL.md).You can only delete rows from a remote table or view if you are using the database with the distributed option.<br>If you omit dblink, the database assumes that the table or view is located on the local database. |
| part_name               | Name of partition in the table                                                                                                                                                                                                                                                                                                                                                                                                                             |
| alias                   | The alias assigned to the table. Aliases are generally used in DELETE statements with correlated queries.                                                                                                                                                                                                                                                                                                                                                  |
| WHERE                   | Specifies which rows are deleted. If you omit this clause entirely, all rows are deleted from the table or view.<br>condition specifies a combination of one or more expressions and logical (Boolean) operators and returns a value of TRUE, FALSE, or UNKNOWN.<br>CURRENT OF specifies deletion of the record that was last fetched by the cursor.                                                                                                       |
| DML returning clause    | See "[DML Returning Clause](embedded-SQL.md)" for a discussion.                                                                                                                                                                                                                                                                                                                                                                                            |

#### Usage Notes

The host variables in the WHERE clause should be either all scalars or all arrays. If they are scalars, the database executes the DELETE statement only once. If they are arrays, the database executes the statement once for each set of array components. Each execution may delete zero, one, or multiple rows.

Array host variables in the WHERE clause can have different sizes. In this case, the number of times the database executes the statement is determined by the smaller of the following values:

- the size of the smallest array

- the value of the host_integer in the optional FOR clause

If no rows satisfy the condition, no rows are deleted and the SQLCODE returns a NOT_FOUND condition.

The cumulative number of rows deleted is returned through the SQLCA. If the WHERE clause contains array host variables, this value reflects the total number of rows deleted for all components of the array processed by the DELETE statement.

If no rows satisfy the condition, the database returns an error through the SQLCODE of the SQLCA. If you omit the WHERE clause, the database raises a warning flag in the fifth component of SQLWARN in the SQLCA. For more information on this statement and the SQLCA, see "[Using the SQL Communications Area](error-handling-and-diagnostics.md)".

You can use comments in a DELETE statement to pass instructions, or hints, to the Oracle Database optimizer. The optimizer uses hints to choose an execution plan for the statement. For more information on hints, see[ Oracle Database Performance Tuning Guide.](../tgdba/managing-operating-system-resources.md)

#### Example

This example illustrates the use of the DELETE statement:

         EXEC SQL DELETE FROM EMP
            WHERE DEPTNO = :DEPTNO
            AND JOB = :JOB
        END-EXEC.
        EXEC SQL DECLARE EMPCURSOR CURSOR
            FOR SELECT EMPNO, COMM
            FROM EMP
        END-EXEC.
        EXEC SQL OPEN EMPCURSOR END-EXEC.
        EXEC SQL FETCH EMPCURSOR
            INTO :EMP-NUMBER, :COMMISSION
        END-EXEC.
        EXEC SQL DELETE FROM EMP
            WHERE CURRENT OF EMPCURSOR
        END-EXEC.

#### Related Topics

DECLARE DATABASE (Oracle Embedded SQL Directive).

DECLARE STATEMENT (Embedded SQL Directive) .

### E.19 DESCRIBE (Executable Embedded SQL)

#### Purpose

To initialize a descriptor to hold descriptions of host variables for an Oracle dynamic SQL statement or PL/SQL block.

#### Prerequisites

You must have prepared the SQL statement or PL/SQL block in a previous embedded SQL PREPARE statement.

#### Syntax

![Description of describe.eps follows](img/describe.png)
[Description of the illustration describe.eps](img_text/describe.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                     |
|:------------------------|:----------------------------------------------------------------------------------------------------------------|
| BIND VARIABLES FOR      | Initializes the descriptor to hold information about the input variables for the SQL statement or PL/SQL block. |
| SELECT LIST FOR         | Initializes the descriptor to hold information about the select list of a SELECT statement.                     |
| \-                      | The default is SELECT LIST FOR.                                                                                 |
| statement_name          | Identifies a SQL statement or PL/SQL block previously prepared with a PREPARE statement.                        |
| descriptor              | The name of the descriptor to be initialized.                                                                   |

#### Usage Notes

You must issue a DESCRIBE statement before manipulating the bind or select descriptor within an embedded SQL program.

You cannot describe both input variables and output variables into the same descriptor.

The number of variables found by a DESCRIBE statement is the total number of placeholders in the prepare SQL statement or PL/SQL block, rather than the total number of uniquely named placeholders. For more information on this statement, see "[The DESCRIBE Statement](Oracle-dynamic-SQL.md)".

#### Example

This example illustrates the use of the DESCRIBE statement in a Pro\*COBOL embedded SQL program:

         EXEC SQL PREPARE MYSTATEMENT FROM :MY-STRING END-EXEC.
         EXEC SQL DECLARE EMPCURSOR
             FOR SELECT EMPNO, ENAME, SAL, COMM
             FROM EMP
             WHERE DEPTNO = :DEPT-NUMBER
         END-EXEC.
         EXEC SQL DESCRIBE BIND VARIABLES FOR MYSTATEMENT
             INTO BINDDESCRIPTOR
         END-EXEC.
         EXEC SQL OPEN EMPCURSOR
             USING BINDDESCRIPTOR
         END-EXEC.
         EXEC SQL DESCRIBE SELECT LIST FOR MY-STATEMENT
             INTO SELECTDESCRIPTOR
         END-EXEC.
         EXEC SQL FETCH EMPCURSOR
             INTO SELECTDESCRIPTOR
         END-EXEC.

#### Related Topics

PREPARE (Executable Embedded SQL).

### E.20 DESCRIBE DESCRIPTOR (Executable Embedded SQL)

#### Purpose

Used to obtain information about an ANSI SQL statement, and to store it in a descriptor.

#### Prerequisites

You must have prepared the SQL statement in a previous embedded SQL PREPARE statement.

#### Syntax

![Description of descans.eps follows](img/descans.png)
[Description of the illustration descans.eps](img_text/descans.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                             |
|:------------------------|:--------------------------------------------------------------------------------------------------------|
| statement_id            | The name of the previously prepared SQL statement or PL/SQL block. OUTPUT is the default.               |
| desc_name               | Host variable containing the name of the descriptor that will hold information about the SQL statement. |
| 'descriptor name'       | Name of the descriptor                                                                                  |
| GLOBAL \| LOCAL         | LOCAL is the default. It means file scope, as opposed to GLOBAL, which means application scope.         |

#### Usage Notes

Use DYNAMIC=ANSI precompiler option. Only COUNT and NAME are implemented for the INPUT descriptor.

The number of variables found by a DESCRIBE statement is the total number of place-holders in the prepare SQL statement or PL/SQL block, rather than the total number of uniquely named place-holders. For more information on this statement, see [ANSI Dynamic SQL](ANSI-dynamic-SQL.md).

#### Example

         EXEC SQL PREPARE s FROM :my_stament END-EXEC.
         EXEC SQL DESCRIBE INPUT s USING DESCRIPTOR 'in' END-EXEC.

#### Related Topics

ALLOCATE DESCRIPTOR (Executable Embedded SQL).

DEALLOCATE DESCRIPTOR (Embedded SQL Statement).

GET DESCRIPTOR (Executable Embedded SQL).

PREPARE (Executable Embedded SQL).

SET DESCRIPTOR (Executable Embedded SQL).

### E.21 ENABLE THREADS (Executable Embedded SQL Extension)

#### Purpose

To initialize a process that supports multiple threads.

#### Prerequisites

You must be developing a precompiler application for and compiling it on a platform that supports multithreaded applications, and THREADS=YES must be specified on the command line.

#### Syntax

![Description of enable_t.eps follows](img/enable_t.png)
[Description of the illustration enable_t.eps](img_text/enable_t.md)

#### Keywords and Parameters

None.

#### Usage Notes

The ENABLE THREADS statement must be executed once, and only once, before any other executable SQL statement and before spawning any threads. This statement does not require a host-variable specification.

#### Example

This example illustrates the use of the ENABLE THREADS statement in a Pro\*COBOL program:

    EXEC SQL ENABLE THREADS END-EXEC.

#### Related Topics

CONTEXT ALLOCATE (Executable Embedded SQL Extension).

CONTEXT FREE (Executable Embedded SQL Extension).

CONTEXT USE (Oracle Embedded SQL Directive).

### E.22 EXECUTE ... END-EXEC (Executable Embedded SQL Extension)

#### Purpose

To embed an anonymous PL/SQL block into an Oracle Pro\*COBOL program.

#### Prerequisites

None.

#### Syntax

![Description of execeex.eps follows](img/execeex.png)
[Description of the illustration execeex.eps](img_text/execeex.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                   |
|:------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| AT                      | Identifies the database on which the PL/SQL block is executed. The database can be identified by either:                                      |
| db_name                 | A database identifier declared in a previous DECLARE DATABASE statement.                                                                      |
| host_variable           | A host variable whose value is a previously declared db_name. If you omit this clause, the PL/SQL block is executed on your default database. |
| pl/sql_block            | For information on PL/SQL, including how to write PL/SQL blocks, see the[ Oracle Database PL/SQL Language Reference](../lnpls/index.md).      |
| END-EXEC                | Must appear after the embedded PL/SQL block.                                                                                                  |

#### Usage Notes

Since the Oracle Precompilers treat an embedded PL/SQL block like a single embedded SQL statement, you can embed a PL/SQL block anywhere in an Oracle Precompiler program that you can embed a SQL statement. For more information on embedding PL/SQL blocks in Oracle Precompiler programs, see [Embedded PL/SQL](embedded-PLSQL.md).

#### Example

Placing this EXECUTE statement in an Oracle Precompiler program embeds a PL/SQL block in the program:

         EXEC SQL EXECUTE
         BEGIN
            SELECT ENAME, JOB, SAL
                INTO :EMP-NAME:IND-NAME, :JOB-TITLE, :SALARY
                FROM EMP
                WHERE EMPNO = :EMP-NUMBER;
            IF :EMP-NAME:IND-NAME IS NULL
                THEN RAISE NAME-MISSING;
            END IF;
         END;
         END-EXEC.

#### Related Topics

EXECUTE IMMEDIATE (Executable Embedded SQL).

### E.23 EXECUTE (Executable Embedded SQL)

#### Purpose

In Oracle dynamic SQL, to execute a DELETE, INSERT, or UPDATE statement or a PL/SQL block that has been previously prepared with an embedded SQL PREPARE statement.

#### Prerequisites

You must first prepare the SQL statement or PL/SQL block with an embedded SQL PREPARE statement.

#### Syntax

![Description of execo.eps follows](img/execo.png)
[Description of the illustration execo.eps](img_text/execo.md)

#### Keywords and Parameters

| Keywords and Parameters           | Description                                                                                                                                                                                                                                                                                                       |
|:----------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| FOR :array_size<br>FOR integer    | Host variable containing the number of rows to be processed.<br>Number of rows to be processed.<br>Limits the number of times the statement is executed when the USING clause contains array host variables If you omit this clause, Oracle executes the statement once for each component of the smallest array. |
| statement_id                      | A precompiler identifier associated with the SQL statement or PL/SQL block to be executed. Use the embedded SQL PREPARE statement to associate the precompiler identifier with the statement or PL/SQL block.                                                                                                     |
| USING DESCRIPTOR SQLDA_descriptor | Uses an Oracle descriptor.<br>CANNOT be used together with an ANSI descriptor (INTO clause).                                                                                                                                                                                                                      |
| USING                             | Specifies a list of host variables with optional indicator variables that Oracle substitutes as input variables into the statement to be executed. The host and indicator variables must be either all scalars or all arrays.                                                                                     |
| host_variable                     | Host variables.                                                                                                                                                                                                                                                                                                   |
| indicator_variable                | Indicator variables.                                                                                                                                                                                                                                                                                              |

#### Usage Note

For more information on this statement, see [Oracle Dynamic SQL](Oracle-dynamic-SQL.md).

#### Example

This example illustrates the use of the EXECUTE statement in a Pro\*COBOL embedded SQL program:

         EXEC SQL PREPARE MY-STATEMENT FROM MY-STRING END-EXEC.
         EXEC SQL EXECUTE MY-STATEMENT USING :MY-VAR END-EXEC.

#### Related Topics

DECLARE DATABASE (Oracle Embedded SQL Directive).

PREPARE (Executable Embedded SQL).

### E.24 EXECUTE DESCRIPTOR (Executable Embedded SQL

#### Purpose

In ANSI SQL Method 4, to execute a DELETE, INSERT, or UPDATE statement or a PL/SQL block that has been previously prepared with an embedded SQL PREPARE statement.

#### Prerequisites

You must first prepare the SQL statement or PL/SQL block with an embedded SQL PREPARE statement.

#### Syntax

![Description of execa.eps follows](img/execa.png)
[Description of the illustration execa.eps](img_text/execa.md)

#### Keywords and Parameters

| Keywords and Parameters                     | Description                                                                                                                                                                                                                           |
|:--------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| FOR :array_size<br>FOR integer              | Host variable containing the number of rows to be processed.<br>Number of rows to be processed.<br>Limits the number of times the statement is executed. Oracle executes the statement once for each component of the smallest array. |
| statement_id                                | A precompiler identifier associated with the SQL statement or PL/SQL block to be executed. Use the embedded SQL PREPARE statement to associate the precompiler identifier with the statement or PL/SQL block.                         |
| USING<br>descriptor_name<br>descriptor name | An ANSI input descriptor.<br>Host variable containing name of the input descriptor.<br>Name of the input descriptor.                                                                                                                  |
| INTO<br>descriptor_name<br>descriptor name  | An ANSI output descriptor.<br>Host variable containing the name of the output descriptor.<br>Name of the output descriptor.                                                                                                           |
| GLOBAL \| LOCAL                             | LOCAL (the default) means file scope, as opposed to GLOBAL, which means application scope.                                                                                                                                            |

#### Usage Notes

For more information on this statement, see "[EXECUTE](ANSI-dynamic-SQL.md)".

#### Examples

The ANSI dynamic SQL Method 4 enables DML RETURNING in a SELECT to be supported by the INTO clause in EXECUTE:

    EXEC SQL EXECUTE S2 USING DESCRIPTOR :bv1 INTO DESCRIPTOR 'SELDES' END-EXEC.

#### Related Topics

DECLARE DATABASE (Oracle Embedded SQL Directive).

PREPARE (Executable Embedded SQL).

### E.25 EXECUTE IMMEDIATE (Executable Embedded SQL)

#### Purpose

To prepare and execute a DELETE, INSERT, or UPDATE statement or a PL/SQL block containing no host variables.

#### Prerequisites

None.

#### Syntax

![Description of execi.eps follows](img/execi.png)
[Description of the illustration execi.eps](img_text/execi.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                                                                                                 |
|:------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AT                      | Identifies the database on which the SQL statement or PL/SQL block is executed. The database can be identified by either db_name or host_variable.<br>If you omit this clause, the statement or block is executed on your default database. |
| db_name                 | A database identifier declared in a previous DECLARE DATABASE statement.                                                                                                                                                                    |
| host_variable           | A host variable whose value is a previously declared db_name.                                                                                                                                                                               |
| host_string             | A host variable whose value is the SQL statement or PL/SQL block to be executed.                                                                                                                                                            |
| text                    | A text literal containing the SQL statement or PL/SQL block to be executed. The quotes may be omitted.<br>The SQL statement can only be a DELETE, INSERT, or UPDATE statement.                                                              |

#### Usage Notes

When you issue an EXECUTE IMMEDIATE statement, the database parses the specified SQL statement or PL/SQL block, checking for errors, and executes it. If any errors are encountered, they are returned in the SQLCODE component of the SQLCA.

For more information on this statement, see "[The EXECUTE IMMEDIATE Statement](Oracle-dynamic-SQL.md)".

#### Example

This example illustrates the use of the EXECUTE IMMEDIATE statement:

         EXEC SQL
             EXECUTE IMMEDIATE 'DELETE FROM EMP WHERE EMPNO = 9460'
         END-EXEC.

#### Related Topics

PREPARE (Executable Embedded SQL).

EXECUTE (Executable Embedded SQL).

### E.26 FETCH (Executable Embedded SQL)

#### Purpose

To retrieve one or more rows returned by a query, assigning the select list values to host variables. For ANSI Dynamic SQL Method 4, see "FETCH DESCRIPTOR (Executable Embedded SQL) ".

#### Prerequisites

You must first open the cursor with an the OPEN statement.

#### Syntax

![Description of fetcho.eps follows](img/fetcho.png)
[Description of the illustration fetcho.eps](img_text/fetcho.md)

#### Keywords and Parameters

| Keywords and Parameters        | Description                                                                                                                                                                                                                                                 |
|:-------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| FOR :array_size<br>FOR integer | Host variable containing the number of rows to be processed.<br>Number of rows to be processed.<br>Limits the number of rows fetched if you are using array host variables. If you omit this clause, Oracle fetches enough rows to fill the smallest array. |
| cursor                         | A cursor that is declared by a DECLARE CURSOR statement. The FETCH statement returns one of the rows selected by the query associated with the cursor.                                                                                                      |
| cursor_variable                | A cursor variable is allocated an ALLOCATE statement. The FETCH statement returns one of the rows selected by the query associated with the cursor variable.                                                                                                |
| INTO                           | Specifies a list of host variables and optional indicator variables into which data is fetched. These host variables and indicator variables must be declared within the program.                                                                           |
| USING SQLDA_variable           | Specifies the Oracle descriptor referenced in a previous DESCRIBE statement. Only use this clause with dynamic embedded SQL, method 4. The USING clause does not apply when a cursor variable is used.                                                      |
| host_variable                  | The host variable into which data is returned.                                                                                                                                                                                                              |
| indicator_variable             | The host indicator variable.                                                                                                                                                                                                                                |

#### Usage Notes

The FETCH statement reads the rows of the active set and names the output variables which contain the results. Indicator values are set to -1 if their associated host variable is null.

The number of rows retrieved is specified by the size of the output host variables or the value specified in the FOR clause. The host variables to receive the data should be either all scalars or all arrays. If they are scalars, Oracle fetches only one row. If they are arrays, Oracle fetches enough rows to fill the arrays.

Array host variables can have different sizes. In this case, the number of rows Oracle fetches is determined by the smaller of the following values:

- The size of the smallest array

- The value of the host_integer in the optional FOR clause

Of course, the number of rows fetched can be further limited by the number of rows that actually satisfy the query.

If a FETCH statement does not retrieve all rows returned by the query, the cursor is positioned on the next returned row. When the last row returned by the query has been retrieved, the next FETCH statement results in an warning code returned in the SQLCODE element of the SQLCA.

If the array is not completely filled then the warning is issued and you should check SQLERRD(3) to see how many rows were actually fetched.

Note that the FETCH statement does not contain an AT clause. You must specify the database accessed by the cursor in the DECLARE CURSOR statement.

You can only move forward through the active set with FETCH statements. If you want to revisit any of the previously fetched rows, you must reopen the cursor and fetch each row in turn. If you want to change the active set, you must assign new values to the input host variables in the cursor's query and reopen the cursor.

#### Example

This example illustrates the FETCH statement in a Pro\*COBOL embedded SQL program:

         EXEC SQL DECLARE EMPCURSOR CURSOR FOR
             SELECT JOB, SAL FROM EMP WHERE DEPTNO = 30
         END-EXEC.
         ...
         EXEC SQL WHENEVER NOT FOUND GOTO ...
     LOOP.
         EXEC SQL FETCH EMPCURSOR INTO :JOB-TITLE1, :SALARY1 END-EXEC.
         EXEC SQL FETCH EMPCURSOR INTO :JOB-TITLE2, :SALARY2 END-EXEC.
         ...
         GO TO LOOP.
         ...

#### Related Topics

CLOSE (Executable Embedded SQL) .

DECLARE CURSOR (Embedded SQL Directive).

OPEN (Executable Embedded SQL) .

PREPARE (Executable Embedded SQL).

### E.27 FETCH DESCRIPTOR (Executable Embedded SQL)

#### Purpose

To retrieve one or more rows returned by a query, assigning the select list values to host variables. Used in ANSI Dynamic SQL Method 4.

#### Prerequisites

You must first open the cursor with an the OPEN statement.

#### Syntax

![Description of fetcha.eps follows](img/fetcha.png)
[Description of the illustration fetcha.eps](img_text/fetcha.md)

#### Keywords and Parameters

| Keywords and Parameters                         | Description                                                                                                                                                                                                                                                 |
|:------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| FOR :array_size<br>FOR integer                  | Host variable containing the number of rows to be processed.<br>Number of rows to be processed.<br>Limits the number of rows fetched if you are using array host variables. If you omit this clause, Oracle fetches enough rows to fill the smallest array. |
| cursor                                          | A cursor that is declared by a DECLARE CURSOR statement. The FETCH statement returns one of the rows selected by the query associated with the cursor.                                                                                                      |
| cursor_variable                                 | A cursor variable is allocated an ALLOCATE statement. The FETCH statement returns one of the rows selected by the query associated with the cursor variable.                                                                                                |
| INTO                                            | Specifies a list of host variables and optional indicator variables into which data is fetched. These host variables and indicator variables must be declared within the program.                                                                           |
| INTO 'descriptor name'<br>INTO :descriptor_name | Name of the output ANSI descriptor.<br>Host variable containing the name of the output descriptor.                                                                                                                                                          |
| GLOBAL \| LOCAL                                 | LOCAL (the default) means file scope, as opposed to GLOBAL, which means application scope.                                                                                                                                                                  |

#### Usage Notes

The number of rows retrieved is specified by the size of the output host variables and the value specified in the FOR clause. The host variables to receive the data should be either all scalars or all arrays. If they are scalars, Oracle fetches only one row. If they are arrays, Oracle fetches enough rows to fill the arrays.

Array host variables can have different sizes. In this case, the number of rows Oracle fetches is determined by the smaller of the following values:

- The size of the smallest array

- The value of the array_size in the optional FOR clause

- Of course, the number of rows fetched can be further limited by the number of rows that actually satisfy the query.

If a FETCH statement does not retrieve all rows returned by the query, the cursor is positioned on the next returned row. When the last row returned by the query has been retrieved, the next FETCH statement results in a warning code returned in the SQLCODE element of the SQLCA.

If the array is not completely filled then the warning is issued and you should check SQLERRD(3) to see how many rows were actually fetched.

Note that the FETCH statement does not contain an AT clause. You must specify the database accessed by the cursor in the DECLARE CURSOR statement.

You can only move forward through the active set with FETCH statements. If you want to revisit any of the previously fetched rows, you must reopen the cursor and fetch each row in turn. If you want to change the active set, you must assign new values to the input host variables in the cursor's query and reopen the cursor.

Use DYNAMIC=ANSI precompiler option for the ANSI SQL Method 4 application. For more information, see "[FETCH](ANSI-dynamic-SQL.md)" for the ANSI SQL Method 4 application.

#### Example

    ...
    EXEC SQL ALLOCATE DESCRIPTOR 'output_descriptor' END-EXEC.
    ...
    EXEC SQL PREPARE S FROM :dyn_statement END-EXEC.
    EXEC SQL DECLARE mycursor CURSOR FOR S END-EXEC.
    ...
    EXEC SQL FETCH mycursor INTO DESCRIPTOR 'output_descriptor' END-EXEC.
    ...

#### Related Topics

PREPARE statement.

### E.28 FREE (Executable Embedded SQL Extension)

#### Purpose

To free memory used by a cursor, LOB locator, or ROWID.

#### Prerequisites

The memory has to have been already allocated.

#### Syntax

![Description of freecob.eps follows](img/freecob.png)
[Description of the illustration freecob.eps](img_text/freecob.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                                                                        |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| cursor_variable         | A cursor variable that has previously been allocated in an ALLOCATE statement. It is of type SQL-CURSOR.<br>The FETCH statement returns one of the rows selected by the query associated with the cursor variable. |
| host_ptr                | A variable of type SQL-ROWID for a ROWID, or SQL-BLOB, SQL-CLOB, or SQL-NCLOB for a LOB.                                                                                                                           |

#### Usage Notes

See "[Cursors](embedded-SQL.md)" and "[Cursor Variables](embedded-PLSQL.md)".

#### Example

    * CURSOR VARIABLE EXAMPLE
    ...
     01  CUR      SQL-CURSOR.
    ...
         EXEC SQL ALLOCATE :CUR END-EXEC.
    ...
         EXEC SQL CLOSE :CUR END-EXEC.
         EXEC SQL FREE  :CUR END-EXEC.
    ...

#### Related Topics

ALLOCATE (Executable Embedded SQL Extension).

CLOSE (Executable Embedded SQL) .

DECLARE CURSOR (Embedded SQL Directive).

### E.29 GET DESCRIPTOR (Executable Embedded SQL)

#### Purpose

To obtain information about host variables from a SQL descriptor area.

#### Prerequisites

Use only with value semantics and ANSI dynamic SQL Method 4.

#### Syntax

![Description of getdesc.eps follows](img/getdesc.png)
[Description of the illustration getdesc.eps](img_text/getdesc.md)

where `item_name` can be one of these choices:

![Description of getdncob.eps follows](img/getdncob.png)
[Description of the illustration getdncob.eps](img_text/getdncob.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                            |
|:------------------------|:-------------------------------------------------------------------------------------------------------|
| array_size<br>integer   | Host variable containing the number of rows to be processed.<br>Number of rows to be processed.        |
| :descriptor_name        | Host variable containing the name of the allocated ANSI descriptor.                                    |
| 'descriptor name'       | Name of the allocated ANSI descriptor.                                                                 |
| GLOBAL \| LOCAL         | LOCAL (the default) means file scope, as opposed to GLOBAL, which means application scope.             |
| host_var=COUNT          | Host variable containing the total number of input or output variables.                                |
| integer                 | Total number of input or output variables.                                                             |
| VALUE :host_integer     | Host variable containing the position of the referenced input or output variable.                      |
| VALUE integer           | The position of the referenced input or output variable.                                               |
| host_var                | Host variable which will receive the item's value.                                                     |
| item_name               | The item_name is found in Table 10-4, and Table 10-5, under the "Descriptor Item Name" column heading. |

#### Usage Notes

Use DYNAMIC=ANSI precompiler option. The array size clause can be used with DATA, RETURNED_LENGTH, and INDICATOR item names. See "[GET DESCRIPTOR](ANSI-dynamic-SQL.md)".

#### Example

         EXEC SQL GET DESCRIPTOR GLOBAL 'mydesc' :mydesc_num_vars = COUNT END-EXEC.

#### Related Topics

ALLOCATE DESCRIPTOR (Executable Embedded SQL).

DESCRIBE DESCRIPTOR (Executable Embedded SQL) .

SET DESCRIPTOR (Executable Embedded SQL).

### E.30 INSERT (Executable Embedded SQL)

#### Purpose

To add rows to a table or to a view's base table.

#### Prerequisites

For you to insert rows into a table, the table must be in your own schema or you must have INSERT privilege on the table.

For you to insert rows into the base table of a view, the owner of the schema containing the view must have INSERT privilege on the base table. Also, if the view is in a schema other than your own, you must have INSERT privilege on the view.

The INSERT ANY TABLE system privilege also enables you to insert rows into any table or any view's base table.

#### Syntax

![Description of insert.eps follows](img/insert.png)
[Description of the illustration insert.eps](img_text/insert.md)

where DML returning clause is:

![Description of return.eps follows](img/return.png)
[Description of the illustration return.eps](img_text/return.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AT                      | Identifies the database on which the INSERT statement is executed. The database can be identified by either:                                                                                                                                                                                                                                                                                                                                                                            |
| db_name                 | A database identifier declared in a previous DECLARE DATABASE statement.                                                                                                                                                                                                                                                                                                                                                                                                                |
| host_variable           | A host variable whose value is a previously declared db_name. If you omit this clause, the INSERT statement is executed on your default database.                                                                                                                                                                                                                                                                                                                                       |
| FOR :host_integer       | Limits the number of times the statement is executed if the VALUES clause contains array host variables. If you omit this clause, Oracle executes the statement once for each component in the smallest array.                                                                                                                                                                                                                                                                          |
| schema                  | The schema containing the table or view. If you omit schema, Oracle assumes the table or view is in your own schema.                                                                                                                                                                                                                                                                                                                                                                    |
| table<br>view           | The name of the table into which rows are to be inserted. If you specify view, Oracle inserts rows into the view's base table.                                                                                                                                                                                                                                                                                                                                                          |
| db_link                 | A complete or partial name of a database link to a remote database where the table or view is located. For information on referring to database links, see [Syntax for Schema Objects and Parts in SQL Statements](../sqlrf/Syntax-for-Schema-Objects-and-Parts-in-SQL-Statements.md).You can only insert rows into a remote table or view if you are using Oracle with the distributed option.<br>If you omit db_link, Oracle assumes that the table or view is on the local database. |
| part_name               | The name of partition in the table                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| column                  | A column of the table or view. In the inserted row, each column in this list is assigned a value from the VALUES clause or the query.<br>If you omit one of the table's columns from this list, the column's value for the inserted row is the column's default value as specified when the table was created. If you omit the column list altogether, the VALUES clause or query must specify values for all columns in the table.                                                     |
| VALUES                  | Specifies a row of values to be inserted into the table or view. Note that the expressions can be host variables with optional indicator variables. You must specify an expression in the VALUES clause for each column in the column list.                                                                                                                                                                                                                                             |
| subquery                | A subquery that returns rows that are inserted into the table. The select list of this subquery must have the same number of columns as the column list of the INSERT statement. For the syntax description of a subquery, see [SELECT](../sqlrf/SELECT.md).                                                                                                                                                                                                                            |
| DML returning clause    | See "[DML Returning Clause](embedded-SQL.md)" for a discussion.                                                                                                                                                                                                                                                                                                                                                                                                                         |

#### Usage Notes

Any host variables that appear in the WHERE clause should be either all scalars or all arrays. If they are scalars, Oracle executes the INSERT statement once. If they are arrays, Oracle executes the INSERT statement once for each set of array components, inserting one row each time.

Array host variables in the WHERE clause can have different sizes. In this case, the number of times Oracle executes the statement is determined by the smaller of the following values:

- Size of the smallest array

- The value of the host_integer in the optional FOR clause.

For more information on this statement, see "[The Basic SQL Statements](embedded-SQL.md) ".

#### Example I

This example illustrates the use of the embedded SQL INSERT statement:

         EXEC SQL
             INSERT INTO EMP (ENAME, EMPNO, SAL)
             VALUES (:ENAME, :EMPNO, :SAL)
         END-EXEC.

#### Example II

This example shows an embedded SQL INSERT statement with a subquery:

         EXEC SQL
             INSERT INTO NEWEMP (ENAME, EMPNO, SAL)
             SELECT ENAME, EMPNO, SAL FROM EMP
             WHERE DEPTNO = :DEPTNO
         END-EXEC.

#### Related Topics

DECLARE DATABASE (Oracle Embedded SQL Directive).

### E.31 LOB APPEND (Executable Embedded SQL Extension)

#### Purpose

To append a LOB to the end of another LOB.

#### Prerequisites

LOB buffering must not be enabled.The destination LOB must have been initialized.

#### Syntax

![Description of lobapp.eps follows](img/lobapp.png)
[Description of the illustration lobapp.eps](img_text/lobapp.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[APPEND](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.32 LOB ASSIGN (Executable Embedded SQL Extension)

#### Purpose

To assign a LOB or BFILE locator to another locator.

#### Syntax

![Description of lobass.eps follows](img/lobass.png)
[Description of the illustration lobass.eps](img_text/lobass.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[ASSIGN](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.33 LOB CLOSE (Executable Embedded SQL Extension)

#### Purpose

To close an open LOB or BFILE.

#### Syntax

![Description of lobclose.eps follows](img/lobclose.png)
[Description of the illustration lobclose.eps](img_text/lobclose.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[CLOSE](large-objects-LOBs.md)" .

#### Related Topics

See the other LOB statements.

### E.34 LOB COPY (Executable Embedded SQL Extension)

#### Purpose

To copy all or part of a LOB value into another LOB.

#### Syntax

![Description of lobcop.eps follows](img/lobcop.png)
[Description of the illustration lobcop.eps](img_text/lobcop.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[COPY](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.35 LOB CREATE TEMPORARY (Executable Embedded SQL Extension)

#### Purpose

To create a temporary LOB.

#### Syntax

![Description of lobcreat.eps follows](img/lobcreat.png)
[Description of the illustration lobcreat.eps](img_text/lobcreat.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[CREATE TEMPORARY](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.36 LOB DESCRIBE (Executable Embedded SQL Extension)

#### Purpose

To retrieve attributes from a LOB.

#### Syntax

![Description of lobdesc.eps follows](img/lobdesc.png)
[Description of the illustration lobdesc.eps](img_text/lobdesc.md)

where `attrib` is:

![Description of lobatt.eps follows](img/lobatt.png)
[Description of the illustration lobatt.eps](img_text/lobatt.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[DESCRIBE](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.37 LOB DISABLE BUFFERING (Executable Embedded SQL Extension)

#### Purpose

To disable LOB buffering.

#### Syntax

![Description of lobdisab.eps follows](img/lobdisab.png)
[Description of the illustration lobdisab.eps](img_text/lobdisab.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[DISABLE BUFFERING](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.38 LOB ENABLE BUFFERING (Executable Embedded SQL Extension)

#### Purpose

To enable LOB buffering.

#### Syntax

![Description of lobenab.eps follows](img/lobenab.png)
[Description of the illustration lobenab.eps](img_text/lobenab.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see [ENABLE BUFFERING](large-objects-LOBs.md)

#### Related Topics

See the other LOB statements.

### E.39 LOB ERASE (Executable Embedded SQL Extension)

#### Purpose

To erase a given amount of LOB data starting from a given offset.

#### Syntax

![Description of loberas.eps follows](img/loberas.png)
[Description of the illustration loberas.eps](img_text/loberas.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[ERASE](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.40 LOB FILE CLOSE ALL (Executable Embedded SQL Extension)

#### Purpose

To close all open BFILEs in the current session.

#### Syntax

![Description of lobficl.eps follows](img/lobficl.png)
[Description of the illustration lobficl.eps](img_text/lobficl.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[FILE CLOSE ALL](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.41 LOB FILE SET (Executable Embedded SQL Extension)

#### Purpose

To set DIRECTORY and FILENAME in a BFILE locator.

#### Syntax

![Description of lobfise.eps follows](img/lobfise.png)
[Description of the illustration lobfise.eps](img_text/lobfise.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[FILE SET](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.42 LOB FLUSH BUFFER (Executable Embedded SQL Extension)

#### Purpose

To write the LOB buffers to the database server.

#### Syntax

![Description of lobflbuf.eps follows](img/lobflbuf.png)
[Description of the illustration lobflbuf.eps](img_text/lobflbuf.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[FLUSH BUFFER](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.43 LOB FREE TEMPORARY (Executable Embedded SQL Extension)

#### Purpose

To free temporary space for the LOB locator.

#### Syntax

![Description of lobfrtem.eps follows](img/lobfrtem.png)
[Description of the illustration lobfrtem.eps](img_text/lobfrtem.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[FREE TEMPORARY](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.44 LOB LOAD (Executable Embedded SQL Extension)

#### Purpose

To copy all or part of a BFILE into an internal LOB.

#### Syntax

![Description of loblofr.eps follows](img/loblofr.png)
[Description of the illustration loblofr.eps](img_text/loblofr.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[LOAD FROM FILE](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.45 LOB OPEN (Executable Embedded SQL Extension)

#### Purpose

To open a LOB or BFILE for read or read/write access.

#### Syntax

![Description of lobopen.eps follows](img/lobopen.png)
[Description of the illustration lobopen.eps](img_text/lobopen.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[OPEN](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.46 LOB READ (Executable Embedded SQL Extension)

#### Purpose

To read all or part of a LOB or BFILE into a buffer.

#### Syntax

![Description of lobread.eps follows](img/lobread.png)
[Description of the illustration lobread.eps](img_text/lobread.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[READ](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.47 LOB TRIM (Executable Embedded SQL Extension)

#### Purpose

To truncate a LOB value.

#### Syntax

![Description of lobtrim.eps follows](img/lobtrim.png)
[Description of the illustration lobtrim.eps](img_text/lobtrim.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[TRIM](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.48 LOB WRITE (Executable Embedded SQL Extension)

#### Purpose

To write the contents of a buffer to a LOB.

#### Syntax

![Description of lobwri.eps follows](img/lobwri.png)
[Description of the illustration lobwri.eps](img_text/lobwri.md)

#### Usage Notes

For usage notes as well as keywords, parameters, and examples, see "[WRITE](large-objects-LOBs.md)".

#### Related Topics

See the other LOB statements.

### E.49 OPEN (Executable Embedded SQL)

#### Purpose

To open a cursor, evaluating the associated query and substituting the host variable names supplied by the USING clause into the WHERE clause of the query. It can be used in place of EXECUTE in dynamic SQL. For the ANSI Dynamic SQL syntax, see "OPEN DESCRIPTOR (Executable Embedded SQL) ".

#### Prerequisites

You must declare the cursor with a DECLARE CURSOR embedded SQL statement before opening it.

#### Syntax

![Description of openo.eps follows](img/openo.png)
[Description of the illustration openo.eps](img_text/openo.md)

#### Keywords and Parameters

| Keywords and Parameters     | Description                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:----------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| array_size<br>integer       | Host variable containing the number of rows to be processed.<br>Number of rows to be processed.<br>Can only be used when the OPEN is equivalent to EXECUTE.                                                                                                                                                                                                                                                                           |
| cursor                      | The (previously declared) cursor to be opened.                                                                                                                                                                                                                                                                                                                                                                                        |
| host_variable               | Specifies a host variable with an optional indicator variable to be substituted into the statement associated with the cursor.<br>CANNOT be used together with an ANSI descriptor (INTO clause).                                                                                                                                                                                                                                      |
| DESCRIPTOR SQLDA_descriptor | Specifies an Oracle descriptor that describes the host variables to be substituted into the WHERE clause of the associated query. The descriptor must be initialized in a previous DESCRIBE statement. The substitution is based on position. The host variable names specified in this statement can be different from the variable names in the associated query.<br>CANNOT be used together with an ANSI descriptor (INTO clause). |

#### Usage Notes

The OPEN statement defines the active set of rows and initializes the cursor just before the first row of the active set. The values of the host variables at the time of the OPEN are substituted in the statement. This statement does not actually retrieve rows; rows are retrieved by the FETCH statement.

Once you have opened a cursor, its input host variables are not reexamined until you reopen the cursor. To change any input host variables and therefore the active set, you must reopen the cursor.

All cursors in a program are in a closed state when the program is initiated or when they have been explicitly closed using the CLOSE statement.

You can reopen a cursor without first closing it. For more information on this statement, see "[Opening a Cursor](embedded-SQL.md)".

#### Example

This example illustrates the use of the OPEN statement in a Pro\*COBOL program:

         EXEC SQL DECLARE EMPCURSOR CURSOR FOR
             SELECT ENAME, EMPNO, JOB, SAL
             FROM EMP
             WHERE DEPTNO = :DEPTNO
         END-EXEC.
         EXEC SQL OPEN EMPCURSOR END-EXEC.

#### Related Topics

CLOSE (Executable Embedded SQL) .

DECLARE CURSOR (Embedded SQL Directive) .

EXECUTE (Executable Embedded SQL).

FETCH (Executable Embedded SQL) .

PREPARE (Executable Embedded SQL) .

### E.50 OPEN DESCRIPTOR (Executable Embedded SQL)

#### Purpose

To open a cursor (for ANSI Dynamic SQL Method 4), evaluating the associated query and substituting the input host variable names supplied by the USING clause into the WHERE clause of the query. The INTO clause denotes the output descriptor. It can be used in place of EXECUTE in dynamic SQL.

#### Prerequisites

You must declare the cursor with a DECLARE CURSOR embedded SQL statement before opening it.

#### Syntax

![Description of opena.eps follows](img/opena.png)
[Description of the illustration opena.eps](img_text/opena.md)

#### Keywords and Parameters

| Keywords and Parameters                               | Description                                                                                                                                                     |
|:------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| array_size<br>integer                                 | Host variable containing the number of rows to be processed.<br>Number of rows to be processed.<br>Used only with dynamic SQL when it is equivalent to EXECUTE. |
| cursor                                                | The (previously declared) cursor to be opened.                                                                                                                  |
| USING DESCRIPTOR<br>descriptor_name 'descriptor name' | Specifies an ANSI input descriptor with the host variable containing the name of the ANSI descriptor, or the name of the ANSI descriptor.                       |
| INTO DESCRIPTOR descriptor_name 'descriptor name'     | Specifies an ANSI output descriptor with the host variable containing the name of the ANSI descriptor, or the name of the ANSI descriptor.                      |
| GLOBAL \| LOCAL                                       | LOCAL (the default) means file scope, as opposed to GLOBAL, which means application scope.                                                                      |

#### Usage Notes

Set the precompiler option DYNAMIC to ANSI.

The OPEN statement defines the active set of rows and initializes the cursor just before the first row of the active set. The values of the host variables at the time of the OPEN are substituted in the statement. This statement does not actually retrieve rows; rows are retrieved by the FETCH statement.

Once you have opened a cursor, its input host variables are not reexamined until you reopen the cursor. To change any input host variables and therefore the active set, you must reopen the cursor.

All cursors in a program are in a closed state when the program is initiated or when they have been explicitly closed using the CLOSE statement.

You can reopen a cursor without first closing it. For more information on this statement, see "[Inserting Rows](embedded-SQL.md)".

#### Example

     01 DYN-STATEMENT PIC X(58) VALUE "SELECT ENAME, EMPNO FROM EMP WHERE
           DEPTNO =:DEPTNO-DAT".
     01 DEPTNO-DAT PIC S9(9) COMP VALUE 10.
     ...
         EXEC SQL ALLOCATE DESCRIPTOR 'input-descriptor' END-EXEC.
         EXEC SQL ALLOCATE DESCRIPTOR 'output-descriptor'
         ...
         EXEC SQL PREPARE S FROM :DYN-STATEMENT END-EXEC.
         EXEC SQL DECLARE C CURSOR FOR S END-EXEC.
         ...
         EXEC SQL OPEN C USING DESCRIPTOR 'input-descriptor' END-EXEC.
         ...

#### Related Topics

CLOSE (Executable Embedded SQL) .

DECLARE CURSOR (Embedded SQL Directive).

FETCH DESCRIPTOR (Executable Embedded SQL) .

PREPARE (Executable Embedded SQL).

### E.51 PREPARE (Executable Embedded SQL)

#### Purpose

To parse a SQL statement or PL/SQL block specified by a host variable and associate it with an identifier.

#### Prerequisites

None.

#### Syntax

![Description of prepare.eps follows](img/prepare.png)
[Description of the illustration prepare.eps](img_text/prepare.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                                                                    |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| db_name                 | A null-terminated string containing the database connection name, as established previously in a CONNECT statement. If it is omitted, or if it is an empty string, the default database connection is assumed. |
| host_variable           | A host variable containing the name of the database connection.                                                                                                                                                |
| array_size<br>integer   | Host variable containing the number of rows to be processed.<br>Number of rows to be processed.                                                                                                                |
| statement_id            | The identifier to be associated with the prepared SQL statement or PL/SQL block. If this identifier was previously assigned to another statement or block, the prior assignment is superseded.                 |
| host_string             | A host variable whose value is the text of a SQL statement or PL/SQL block to be prepared.                                                                                                                     |
| text                    | A text literal containing the SQL statement or PL/SQL block to be executed. The quotes may be omitted.                                                                                                         |
| select_command          | A SELECT statement.                                                                                                                                                                                            |

#### Usage Notes

Any variables that appear in the host_string or text are placeholders. The actual host variable names are assigned in the USING clause of the OPEN statement (input host variables) or in the INTO clause of the FETCH statement (output host variables).

A SQL statement is prepared only once, but can be executed any number of times.

#### Example

This example illustrates the use of a PREPARE statement in a Pro\*COBOL embedded SQL program:

         EXEC SQL PREPARE MYSTATEMENT FROM :MY-STRING END-EXEC.
         EXEC SQL EXECUTE MYSTATEMENT END-EXEC.

#### Related Topics

CLOSE (Executable Embedded SQL) .

DECLARE CURSOR (Embedded SQL Directive).

FETCH (Executable Embedded SQL) .

OPEN (Executable Embedded SQL) .

### E.52 ROLLBACK (Executable Embedded SQL)

#### Purpose

To undo work done in the current transaction. You can also use this statement to manually undo the work done by an in-doubt distributed transaction.

#### Prerequisites

To roll back your current transaction, no privileges are necessary.

To manually roll back an in-doubt distributed transaction that you originally committed, you must have FORCE TRANSACTION system privilege. To manually roll back an in-doubt distributed transaction originally committed by another user, you must have FORCE ANY TRANSACTION system privilege.

#### Syntax

![Description of rollb.eps follows](img/rollb.png)
[Description of the illustration rollb.eps](img_text/rollb.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                                                                                                                                                                       |
|:------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| db_name                 | A null-terminated string containing the database connection name, as established previously in a CONNECT statement. If it is omitted, or if it is an empty string, the default database connection is assumed.                                                                                                    |
| host_variable           | A host variable containing the name of the database connection. If you omit this clause, the savepoint is created on your default database.                                                                                                                                                                       |
| WORK                    | Is optional and is provided for ANSI compatibility.                                                                                                                                                                                                                                                               |
| TO                      | Rolls back the current transaction to the specified savepoint. If you omit this clause, the ROLLBACK statement rolls back the entire transaction.                                                                                                                                                                 |
| FORCE                   | Manually rolls back an in-doubt distributed transaction. The transaction is identified by the text containing its local or global transaction ID. To find the IDs of such transactions, query the data dictionary view DBA_2PC_PENDING.<br>ROLLBACK statements with the FORCE clause are not supported in PL/SQL. |
| RELEASE                 | Frees all resources and disconnects the application from the database server. The RELEASE clause is not allowed with SAVEPOINT and FORCE clauses.                                                                                                                                                                 |
| savepoint               | The name of the savepoint to be rolled back to.                                                                                                                                                                                                                                                                   |

#### Usage Notes

A transaction (or a logical unit of work) is a sequence of SQL statements that Oracle treats as a single unit. A transaction begins with the first executable SQL statement after a COMMIT, ROLLBACK or connection to the database. A transaction ends with a COMMIT statement, a ROLLBACK statement, or disconnection (intentional or unintentional) from the database. Note that Oracle issues an implicit COMMIT statement before and after processing any data definition language statement.

Using the ROLLBACK statement without the TO SAVEPOINT clause performs the following operations:

- ends the transaction

- undoes all changes in the current transaction

- erases all savepoints in the transaction

- releases the transaction's locks

Using the ROLLBACK statement with the TO SAVEPOINT clause performs the following operations:

- rolls back just the portion of the transaction after the savepoint.

- loses all savepoints created after that savepoint. Note that the named savepoint is retained, so you can roll back to the same savepoint multiple times. Prior savepoints are also retained.

- releases all table and row locks acquired since the savepoint. Note that other transactions that have requested access to rows locked after the savepoint must continue to wait until the transaction is committed or rolled back. Other transactions that have not already requested the rows can request and access the rows immediately.

It is recommended that you explicitly end transactions in application programs using either a COMMIT or ROLLBACK statement. If you do not explicitly commit the transaction and the program terminates abnormally, Oracle rolls back the last uncommitted transaction.

#### Example I

The following statement rolls back your entire current transaction:

         EXEC SQL ROLLBACK END-EXEC.

#### Example II

The following statement rolls back your current transaction to savepoint SP5:

          EXEC SQL ROLLBACK TO SAVEPOINT SP5 END-EXEC.

#### Distributed Transactions

Oracle with the distributed option enables you to perform distributed transactions, or transactions that modify data on multiple databases. To commit or roll back a distributed transaction, you need only issue a COMMIT or ROLLBACK statement as you would any other transaction.

If there is a network failure during the commit process for a distributed transaction, the state of the transaction may be unknown, or in-doubt. After consultation with the administrators of the other databases involved in the transaction, you may decide to manually commit or roll back the transaction on your local database. You can manually roll back the transaction on your local database by issuing a ROLLBACK statement with the FORCE clause.

You cannot manually roll back an in-doubt transaction to a savepoint.

A ROLLBACK statement with a FORCE clause only rolls back the specified transaction. Such a statement does not affect your current transaction.

#### Example III

The following statement manually rolls back an in-doubt distributed transaction:

         EXEC SQL ROLLBACK WORK FORCE '25.32.87' END-EXEC.

#### Related Topics

COMMIT (Executable Embedded SQL) .

SAVEPOINT (Executable Embedded SQL) .

### E.53 SAVEPOINT (Executable Embedded SQL)

#### Purpose

To identify a point in a transaction to which you can later roll back.

#### Prerequisites

None.

#### Syntax

![Description of savep.eps follows](img/savep.png)
[Description of the illustration savep.eps](img_text/savep.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                               |
|:------------------------|:------------------------------------------------------------------------------------------------------------------------------------------|
| AT                      | Identifies the database on which the savepoint is created. The database can be identified by either:                                      |
| db_name                 | A database identifier declared in a previous DECLARE DATABASE statement.                                                                  |
| host_variable           | A host variable whose value is a previously declared db_name. If you omit this clause, the savepoint is created on your default database. |
| savepoint               | The name of the savepoint to be created.                                                                                                  |

#### Usage Notes

For more information on this statement, see "[Using the SAVEPOINT Statement](database-concepts.md)".

#### Example

This example illustrates the use of the embedded SQL SAVEPOINT statement:

         EXEC SQL SAVEPOINT SAVE3 END-EXEC.

#### Related Topics

COMMIT (Executable Embedded SQL) .

ROLLBACK (Executable Embedded SQL) .

### E.54 SELECT (Executable Embedded SQL)

#### Purpose

To retrieve data from one or more tables, views, or snapshots, assigning the selected values to host variables.

#### Prerequisites

For you to select data from a table or snapshot, the table or snapshot must be in your own schema or you must have SELECT privilege on the table or snapshot.

For you to select rows from the base tables of a view, the owner of the schema containing the view must have SELECT privilege on the base tables. Also, if the view is in a schema other than your own, you must have SELECT privilege on the view.

The SELECT ANY TABLE system privilege also enables you to select data from any table or any snapshot or any view's base table.

#### Syntax

![Description of select_a.eps follows](img/select_a.png)
[Description of the illustration select_a.eps](img_text/select_a.md)

![Description of select_b.eps follows](img/select_b.png)
[Description of the illustration select_b.eps](img_text/select_b.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                                                                                                                                                            |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AT                      | Identifies the database to which the SELECT statement is issued. The database can be identified by either:                                                                                                                                                                                             |
| db_name                 | A database identifier declared in a previous DECLARE DATABASE statement.                                                                                                                                                                                                                               |
| host_variable           | A host variable whose value is a previously declared db_name. If you omit this clause, the SELECT statement is issued to your default database.                                                                                                                                                        |
| select_list             | Identical to the non-embedded SELECT statement except that a host variables can be used in place of literals.                                                                                                                                                                                          |
| INTO                    | Specifies output host variables and optional indicator variables to receive the data returned by the SELECT statement. Note that these variables must be either all scalars or all arrays, but arrays need not have the same size.                                                                     |
| WHERE                   | Restricts the rows returned to those for which the condition is TRUE. See [About SQL Conditions](../sqlrf/About-SQL-Conditions.md)for more information. The condition can contain host variables, but cannot contain indicator variables. These host variables should be scalars and cannot be arrays. |

All other keywords and parameters are identical to the non-embedded SQL SELECT statement.

#### Usage Notes

If no rows meet the WHERE clause condition, no rows are retrieved and Oracle returns an error code through the SQLCODE component of the SQLCA.

You can use comments in a SELECT statement to pass instructions, or hints, to the Oracle optimizer. The optimizer uses hints to choose an execution plan for the statement.

#### Example

This example illustrates the use of the embedded SQL SELECT statement:

         EXEC SQL SELECT ENAME, SAL + 100, JOB
             INTO :ENAME, :SAL, :JOB
             FROM EMP
             WHERE EMPNO = :EMPNO
         END-EXEC.

#### Related Topics

DECLARE CURSOR (Embedded SQL Directive).

DECLARE DATABASE (Oracle Embedded SQL Directive).

EXECUTE (Executable Embedded SQL).

FETCH (Executable Embedded SQL) .

PREPARE (Executable Embedded SQL).

### E.55 SET DESCRIPTOR (Executable Embedded SQL)

#### Purpose

Use this ANSI dynamic SQL statement to set information in the descriptor area from host variables.

#### Prerequisites

Use after a DESCRIBE DESCRIPTOR.

#### Syntax

![Description of setdesc.eps follows](img/setdesc.png)
[Description of the illustration setdesc.eps](img_text/setdesc.md)

where `item_name` can be one of these choices:

![Description of setdncob.eps follows](img/setdncob.png)
[Description of the illustration setdncob.eps](img_text/setdncob.md)

#### Keywords and Parameters

| Keywords and Parameters              | Description                                                                                                                                                                                 |
|:-------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| array_size<br>integer                | Host variable containing the number of rows to be processed.<br>Number of rows to be processed. The array size clause can only be used with DATA, RETURNED_LENGTH and INDICATOR item names. |
| GLOBAL \| LOCAL                      | LOCAL (the default) means file scope, as opposed to GLOBAL, which means application scope.                                                                                                  |
| descriptor_name<br>'descriptor name' | Host variable containing the name of the allocated ANSI descriptor.<br>Name of the allocated ANSI descriptor.                                                                               |
| COUNT                                | The total number of input or output variables.                                                                                                                                              |
| VALUE                                | The position of the referenced host variable in the statement.                                                                                                                              |
| item_name                            | See Table 10-6 and Table 10-7 for lists of the item_names, and their descriptions.                                                                                                          |
| host_var                             | Host variable containing the total number of input or output variables.                                                                                                                     |
| integer                              | Total number of input or output variables.                                                                                                                                                  |
| host_var                             | The host variables used to set the item.                                                                                                                                                    |
| REF                                  | Reference semantics are to be used. Can be used only with RETURNED_LENGTH, DATA, and INDICATOR item names.<br>Must be used to set RETURNED_LENGTH.                                          |

#### Usage Notes

Use DYNAMIC=ANSI precompiler option. Set CHARACTER_SET_NAME to UTF16 for client-side Unicode support. See "[SET DESCRIPTOR](ANSI-dynamic-SQL.md)" for complete details, including tables of descriptor item names.

#### Example

         EXEC SQL SET DESCRIPTOR GLOBAL :mydescr COUNT = 3 END-EXEC.

#### Related Topics

ALLOCATE DESCRIPTOR (Executable Embedded SQL).

DEALLOCATE DESCRIPTOR (Embedded SQL Statement).

DESCRIBE DESCRIPTOR (Executable Embedded SQL) .

GET DESCRIPTOR (Executable Embedded SQL).

PREPARE (Executable Embedded SQL).

### E.56 UPDATE (Executable Embedded SQL)

#### Purpose

To change existing values in a table or in a view's base table.

#### Prerequisites

For you to update values in a table or snapshot, the table must be in your own schema or you must have UPDATE privilege on the table.

For you to update values in the base table of a view, the owner of the schema containing the view must have UPDATE privilege on the base table. Also, if the view is in a schema other than your own, you must have UPDATE privilege on the view.

The UPDATE ANY TABLE system privilege also enables you to update values in any table or any view's base table.

#### Syntax

![Description of update.eps follows](img/update.png)
[Description of the illustration update.eps](img_text/update.md)

where DML returning clause is:

![Description of return.eps follows](img/return.png)
[Description of the illustration return.eps](img_text/return.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                                                                                                                                                                                                                                                       |
|:------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AT                      | identifies the database to which the UPDATE statement is issued. The database can be identified by either dbname or host_variable.<br>If you omit this clause, the UPDATE statement is issued to your default database.                                                                                                                                                                           |
| dbname                  | A database identifier declared in a previous DECLARE DATABASE statement.                                                                                                                                                                                                                                                                                                                          |
| host_variable           | A host variable whose value is a previously declared dbname.                                                                                                                                                                                                                                                                                                                                      |
| FOR :host_integer       | Limits the number of times the UPDATE statement is executed if the SET and WHERE clauses contain array host variables. If you omit this clause, Oracle executes the statement once for each component of the smallest array.                                                                                                                                                                      |
| schema                  | The schema containing the table or view. If you omit schema, Oracle assumes the table or view is in your own schema.                                                                                                                                                                                                                                                                              |
| table view              | The name of the table to be updated. If you specify view, Oracle updates the view's base table.                                                                                                                                                                                                                                                                                                   |
| dblink                  | A complete or partial name of a database link to a remote database where the table or view is located. For information on referring to database links, see [References to Objects in Remote Databases](../sqlrf/Syntax-for-Schema-Objects-and-Parts-in-SQL-Statements.md). You can only use a database link to update a remote table or view if you are using Oracle with the distributed option. |
| part_name               | Name of partition in the table                                                                                                                                                                                                                                                                                                                                                                    |
| alias                   | A name used to reference the table, view, or subquery elsewhere in the statement.                                                                                                                                                                                                                                                                                                                 |
| column                  | The name of a column of the table or view that is to be updated. If you omit a column of the table from the SET clause, that column's value remains unchanged.                                                                                                                                                                                                                                    |
| expr                    | The new value assigned to the corresponding column. This expression can contain host variables and optional indicator variables.                                                                                                                                                                                                                                                                  |
| subquery_1              | A subquery that returns new values that are assigned to the corresponding columns. For the syntax of a subquery, see [SELECT](../sqlrf/SELECT.md).                                                                                                                                                                                                                                                |
| subquery_2              | A subquery that return a new value that is assigned to the corresponding column. For the syntax of a subquery, see [SELECT](../sqlrf/SELECT.md).                                                                                                                                                                                                                                                  |
| WHERE                   | Specifies which rows of the table or view are updated.<br>If you omit this clause entirely, the database updates all rows of the table or view.<br>condition specifies a combination of one or more expressions and logical (Boolean) operators and returns a value of TRUE, FALSE, or UNKNOWN.<br>CURRENT OF specifies deletion of the record that was last fetched by the cursor.               |
| DML returning clause    | See "[DML Returning Clause](embedded-SQL.md)" for a discussion.                                                                                                                                                                                                                                                                                                                                   |

#### Usage Notes

Host variables in the SET and WHERE clauses must be either all scalars or all arrays. If they are scalars, Oracle executes the UPDATE statement only once. If they are arrays, Oracle executes the statement once for each set of array components. Each execution may update zero, one, or multiple rows.

Array host variables can have different sizes. In this case, the number of times Oracle executes the statement is determined by the smaller

of the following values:

- The size of the smallest array

- The value of the host_integer in the optional FOR clause

The cumulative number of rows updated is returned through the third element of the SQLERRD component of the SQLCA. When arrays are used as input host variables, this count reflects the total number of updates for all components of the array processed in the UPDATE statement. If no rows satisfy the condition, no rows are updated and Oracle returns an error message through the SQLCODE element of the SQLCA. If you omit the WHERE clause, all rows are updated and Oracle raises a warning flag in the fifth component of the SQLWARN element of the SQLCA.

You can use comments in an UPDATE statement to pass instructions, or hints, to the Oracle optimizer. The optimizer uses hints to choose an execution plan for the statement.

For more information on this statement, see "[The Basic SQL Statements](embedded-SQL.md) " and [Database Concepts](database-concepts.md).

#### Examples

The following examples illustrate the use of the embedded SQL UPDATE statement:

         EXEC SQL UPDATE EMP
             SET SAL = :SAL, COMM = :COMM INDICATOR :COMM-IND
             WHERE ENAME = :ENAME
         END-EXEC.

         EXEC SQL UPDATE EMP
             SET (SAL, COMM) =
                 (SELECT AVG(SAL)*1.1, AVG(COMM)*1.1
                 FROM EMP)
             WHERE ENAME = 'JONES'
         END-EXEC.

#### Related Topics

DECLARE DATABASE (Oracle Embedded SQL Directive).

### E.57 VAR (Oracle Embedded SQL Directive)

#### Purpose

To perform host variable equivalencing, to assign a specific Oracle external datatype to an individual host variable, overriding the default datatype assignment. There is an optional clause, CONVBUFSZ, that specifies the size of a buffer for character set conversion.

#### Prerequisites

The host variable must be previously declared in the embedded SQL program.

#### Syntax

![Description of var.eps follows](img/var.png)
[Description of the illustration var.eps](img_text/var.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                                                                                                                                                                                                             |
|:------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| host_variable           | The host variable to be assigned an Oracle external datatype.                                                                                                                                                                                                                                           |
| dtyp                    | An Oracle external datatype recognized by Pro\*COBOL (not an Oracle internal datatype). The datatype may include a length, precision, or scale. This external datatype is assigned to the host_variable. For a list of external datatypes, see "[External Datatypes](datatypes-and-host-variables.md)". |
| size                    | The size in bytes of a buffer in the Oracle runtime library used to perform conversion between character sets of the host_variable.                                                                                                                                                                     |

#### Usage Notes

Datatype equivalencing is useful for any of the following purposes:

- To store program data as binary data in the database

- To override default datatype conversion

For more information about Oracle datatypes, see "[Sample Program 4: Datatype Equivalencing](datatypes-and-host-variables.md)".

#### Example

This example equivalences the host variable DEPT_NAME to the datatype VARCHAR2 and the host variable BUFFER to the datatype RAW(200):

         EXEC SQL BEGIN DECLARE SECTION END-EXEC.
         ...
         01 DEPT-NAME  PIC X(15).
    * -- default datatype is CHAR
         EXEC SQL VAR DEPT-NAME IS VARCHAR2 END-EXEC.
    * -- reset to STRING
         ...
         01 BUFFER-VAR.
              05 BUFFER  PIC X(200).
    * -- default datatype is CHAR
         EXEC SQL VAR BUFFER IS RAW(200) END-EXEC.
    * -- refer to RAW
         ...
         EXEC SQL END DECLARE SECTION END-EXEC.

#### Related Topics

None.

### E.58 WHENEVER (Embedded SQL Directive)

#### Purpose

To specify the action to be taken when an error or warning results from executing an embedded SQL program.

#### Prerequisites

None.

#### Syntax

![Description of whenever.eps follows](img/whenever.png)
[Description of the illustration whenever.eps](img_text/whenever.md)

where DO.CALL.CLAUSE is:

![Description of docall.eps follows](img/docall.png)
[Description of the illustration docall.eps](img_text/docall.md)

#### Keywords and Parameters

| Keywords and Parameters | Description                                                                                                        |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------|
| NOT FOUND \| NOTFOUND   | Identifies any exception condition that returns an error code of +1403 to SQLCODE (or a +100 code when MODE=ANSI). |
| SQLERROR                | Identifies a condition that results in a negative return code.                                                     |
| SQLWARNING              | Identifies a non-fatal warning condition.                                                                          |
| CONTINUE                | Indicates that the program should progress to the next statement.                                                  |
| GOTO \| GO TO           | Indicates that the program should branch to the statement named by label.                                          |
| STOP                    | Stops program execution.                                                                                           |
| DO PERFORM              | Indicates that the program should perform a paragraph or section at label.                                         |
| DO CALL                 | Indicates that the program should execute a subprogram.                                                            |
| subprogram_name         | The subprogram to be executed. It may have to be inside quotes (").                                                |
| USING                   | Indicates that the parameters of the subprogram follow.                                                            |
| param                   | A list of subprogram parameters separated by blanks.                                                               |

The WHENEVER directive enables your program to take one of several possible actions in the event an embedded SQL statement results in an error or warning.

The scope of a WHENEVER statement is positional, rather than logical. A WHENEVER statement applies to all embedded SQL statements that textually follow it in the source file, not in the flow of the program logic. A WHENEVER statement remains in effect until it is superseded by another WHENEVER statement checking for the same condition.

For more information about and examples of the conditions and actions of this directive, see "[WHENEVER Directive](error-handling-and-diagnostics.md)".

Do not confuse the WHENEVER embedded SQL directive with the WHENEVER SQL\*Plus command.

#### Example

The following example illustrates the use of the WHENEVER directive in a Pro\*COBOL embedded SQL program:

         EXEC SQL WHENEVER NOT FOUND CONTINUE END-EXEC.
         ...
         EXEC SQL WHENEVER SQLERROR GOTO SQL-ERROR END-EXEC.
         ...
     SQL-ERROR.
         EXEC SQL WHENEVER SQLERROR CONTINUE END-EXEC.
         DISPLAY "ORACLE ERROR DETECTED.".
         EXEC SQL ROLLBACK RELEASE END-EXEC.
         STOP RUN.

#### Related Topics

None
