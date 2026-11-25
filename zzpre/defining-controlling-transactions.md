This chapter explains how to perform transaction processing. You learn the basic techniques that safeguard the consistency of your database, including how to control whether changes to Oracle data are made permanent or undone. The following topics are discussed:

- Some Terms You Should Know

- How Transactions Guard Your Database

- How to Begin and End Transactions

- About Using the COMMIT Statement

- About Using the ROLLBACK Statement

- About Using the SAVEPOINT Statement

- About Using the RELEASE Option

- About Using the SET TRANSACTION Statement

- About Overriding Default Locking

- About Fetching Across Commits

- About Handling Distributed Transactions

- Guidelines

### 7.1 Some Terms You Should Know

Before delving into the subject of transactions, you should know the terms defined in this section.

The jobs or tasks that Oracle manages are called sessions. A user session is started when you run an application program or a tool such as Oracle Forms and connect to Oracle. Oracle allows user sessions to work "simultaneously" and share computer resources. To do this, Oracle must control concurrency, which means many user accessing the same data. Without adequate concurrency controls, there might be a loss of data integrity. That is, changes to data or structures might be made incorrectly.

Oracle uses locks to control concurrent access to data. A lock gives you temporary ownership of a database resource such as a table or row of data. Thus, data cannot be changed by other users until you finish with it. You need never explicitly lock a resource, because default locking mechanisms protect Oracle data and structures. However, you can request data locks on tables or rows when it is to your advantage to override default locking. You can choose from several modes of locking such as row share and exclusive.

A deadlock can occur when two or more users try to access the same database object. For example, two users updating the same table might wait if each tries to update a row currently locked by the other. Because each user is waiting for resources held by another user, neither can continue until Oracle breaks the deadlock. Oracle signals an error to the participating transaction that had completed the least amount of work, and the "deadlock detected while waiting for resource" Oracle error code is returned to SQLCODE in the SQLCA.

When a table is being queried by one user and updated by another at the same time, Oracle generates a read-consistent view of the table's data for the query. That is, after a query begins and as it proceeds, the data read by the query does not change. As update activity continues, Oracle takes snapshots of the table's data and records changes in a rollback segment. Oracle uses information in the rollback segment to build read-consistent query results and to undo changes if necessary.

### 7.2 How Transactions Guard Your Database

Oracle is transaction oriented; that is, it uses transactions to ensure data integrity. A transaction is a series of one or more logically related SQL statements you define to accomplish some task. Oracle treats the series of SQL statements as a unit so that all the changes brought about by the statements are either committed (made permanent) or rolled back (undone) at the same time. If your application program fails in the middle of a transaction, the database is automatically restored to its former (pre-transaction) state.

The subsequent sections show you how to define and control transactions. Specifically, you learn how to

- Begin and end transactions

- Use the `COMMIT` statement to make transactions permanent

- Use the `SAVEPOINT` statement with the `ROLLBACK` `TO` statement to undo parts of transactions

- Use the `ROLLBACK` statement to undo whole transactions

- Specify the `RELEASE` option to free resources and log off the database

- Use the `SET` `TRANSACTION` statement to set read-only transactions

- Use the `FOR` `UPDATE` clause or `LOCK` `TABLE` statement to override default locking

For details about the SQL statements discussed in this chapter, see the [Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md).

### 7.3 How to Begin and End Transactions

You begin a transaction with the first executable SQL statement (other than `CONNECT`) in your program. When one transaction ends, the next executable SQL statement automatically begins another transaction. Thus, every executable statement is part of a transaction. Because they cannot be rolled back and need not be committed, declarative SQL statements are not considered part of a transaction.

You end a transaction in one of the following ways:

- Code a `COMMIT` or `ROLLBACK` statement, with or without the `RELEASE` option. This explicitly makes permanent or undoes changes to the database.

- Code a data definition statement (`ALTER`, `CREATE`, or `GRANT`, for example) that issues an automatic commit before and after executing. This implicitly makes permanent changes to the database.

A transaction also ends when there is a system failure or your user session stops unexpectedly because of software problems, hardware problems, or a forced interruption. Oracle rolls back the transaction.

If your program fails in the middle of a transaction, Oracle detects the error and rolls back the transaction. If your operating system fails, Oracle restores the database to its former (pre-transaction) state.

### 7.4 About Using the COMMIT Statement

You use the `COMMIT` statement to make changes to the database permanent. Until changes are committed, other users cannot access the changed data; they see it as it was before your transaction began. The `COMMIT` statement has no effect on the values of host variables or on the flow of control in your program. Specifically, the `COMMIT` statement

- Makes permanent all changes made to the database during the current transaction

- Makes these changes visible to other users

- Erases all savepoints (refer to About Using the ROLLBACK Statement)

- Releases all row and table locks, but not parse locks

- Closes cursors referenced in a CURRENT OF clause or, when `MODE={ANSI13|ORACLE}`, closes all explicit cursors

- Ends the transaction

When `MODE={ANSI13|ORACLE}`, explicit cursors not referenced in a `CURRENT OF `clause remain open across commits. This can boost performance. For an example, refer to "About Fetching Across Commits".

Because they are part of normal processing, `COMMIT` statements should be placed inline, on the main path through your program. Before your program terminates, it must explicitly commit pending changes. Otherwise, Oracle rolls them back. In the following example, you commit your transaction and disconnect from Oracle:

    EXEC SQL COMMIT WORK RELEASE;

The optional keyword WORK provides ANSI compatibility. The RELEASE option frees all Oracle resources (locks and cursors) held by your program and logs off the database.

You need not follow a data definition statement with a COMMIT statement because data definition statements issue an automatic commit before and after executing. So, whether they succeed or fail, the prior transaction is committed.

### 7.5 About Using the ROLLBACK Statement

You use the `ROLLBACK` statement to undo pending changes made to the database. For example, if you make a mistake such as deleting the wrong row from a table, you can use `ROLLBACK` to restore the original data. The `ROLLBACK` statement has no effect on the values of host variables or on the flow of control in your program. Specifically, the `ROLLBACK` statement

- Undoes all changes made to the database during the current transaction

- Erases all savepoints

- Ends The Transaction

- Releases All Row And Table Locks, But Not Parse Locks

- Closes cursors referenced in a CURRENT OF clause or, when `MODE={ANSI|ANSI14}`, closes all explicit cursors

When `MODE={ANSI13|ORACLE}`, explicit cursors not referenced in a `CURRENT OF` clause remain open across rollbacks.

Because they are part of exception processing, `ROLLBACK` statements should be placed in error handling routines, off the main path through your program. In the following example, you roll back your transaction and disconnect from Oracle:

    EXEC SQL ROLLBACK WORK RELEASE;

The optional keyword `WORK` provides ANSI compatibility. The `RELEASE` option frees all resources held by your program and logs off the database.

If a `WHENEVER` SQLERROR `GOTO` statement branches to an error handling routine that includes a `ROLLBACK` statement, your program might enter an infinite loop if the rollback fails with an error. You can avoid this by coding `WHENEVER` SQLERROR `CONTINUE` before the `ROLLBACK` statement.

For example, consider the following:

    EXEC SQL WHENEVER SQLERROR GOTO sql_error;
    FOR EACH new employee
     display 'Employee number? ';
     read emp_number;
     display 'Employee name? ';
     read emp_name;
     EXEC SQL INSERT INTO EMP (EMPNO, ENAME)
     VALUES (:emp_number, :emp_name);
    ENDFOR;
    ...
    sql_error:
     EXEC SQL WHENEVER SQLERROR CONTINUE;
     EXEC SQL ROLLBACK WORK RELEASE;
     display 'Processing error';
     exit program with an error;

Oracle rolls back transactions if your program terminates abnormally.

#### 7.5.1 Statement-Level Rollbacks

Before executing any SQL statement, Oracle marks an implicit savepoint (not available to you). Then, if the statement fails, Oracle rolls it back automatically and returns the applicable error code to SQLCODE in the SQLCA. For example, if an INSERT statement causes an error by trying to insert a duplicate value in a unique index, the statement is rolled back.

Only work started by the failed SQL statement is lost; work done before that statement in the current transaction is kept. Thus, if a data definition statement fails, the automatic commit that precedes it is not undone.

Note that before executing a SQL statement, Oracle must parse it, that is, examine it to make sure it follows syntax rules and refers to valid database objects. Errors detected while executing a SQL statement cause a rollback, but errors detected while parsing the statement do not.

Oracle can also roll back single SQL statements to break deadlocks. Oracle signals an error to one of the participating transactions and rolls back the current statement in that transaction.

### 7.6 About Using the SAVEPOINT Statement

You use the `SAVEPOINT` statement to mark and name the current point in the processing of a transaction. Each marked point is called a savepoint. For example, the following statement marks a savepoint named start_delete:

    EXEC SQL SAVEPOINT start_delete;

Savepoints let you divide long transactions, giving you more control over complex procedures. For example, if a transaction performs several functions, you can mark a savepoint before each function. Then, if a function fails, you can easily restore the Oracle data to its former state, recover, then reexecute the function.

To undo part of a transaction, you use savepoints with the `ROLLBACK` statement and its T`O SAVEPOINT` clause. The `TO SAVEPOINT `clause lets you roll back to an intermediate statement in the current transaction, so you do not have to undo all your changes. Specifically, the `ROLLBACK TO SAVEPOINT` statement

- Undoes changes made to the database since the specified savepoint was marked

- Erases all savepoints marked after the specified savepoint

- Releases all row and table locks acquired since the specified savepoint was marked

In the example, you access the table `MAIL_LIST` to insert new listings, update old listings, and delete (a few) inactive listings. After the delete, you check SQLERRD(3) in the SQLCA for the number of rows deleted. If the number is unexpectedly large, you roll back to the savepoint start_delete, undoing just the delete.

    FOR EACH new customer
     display 'Customer number? ';
     read cust_number;
     display 'Customer name? ';
     read cust_name;
    EXEC SQL INSERT INTO MAIL_LIST (CUSTNO, CNAME, STAT)
     VALUES (:cust_number, :cust_name, 'ACTIVE');
    ENDFOR;
    FOR EACH revised status
     display 'Customer number? ';
     read cust_number;
     display 'New status? ';
     read new_status;
     EXEC SQL UPDATE MAIL_LIST
     SET STAT = :new_status WHERE CUSTNO = :cust_number;
    ENDFOR;
    -- mark savepoint
    EXEC SQL SAVEPOINT start_delete;
    EXEC SQL DELETE FROM MAIL_LIST WHERE STAT = 'INACTIVE';
    IF sqlca.sqlerrd(3) < 25 THEN -- check number of rows deleted
     display 'Number of rows deleted is ', sqlca.sqlerrd(3);
    ELSE
     display 'Undoing deletion of ', sqlca.sqlerrd(3), ' rows';
     EXEC SQL WHENEVER SQLERROR GOTO sql_error;
     EXEC SQL ROLLBACK TO SAVEPOINT start_delete;
    ENDIF;
    EXEC SQL WHENEVER SQLERROR CONTINUE;
    EXEC SQL COMMIT WORK RELEASE;
    exit program;
    sql_error:
     EXEC SQL WHENEVER SQLERROR CONTINUE;
     EXEC SQL ROLLBACK WORK RELEASE;
     display 'Processing error';
     exit program with an error;

Note that you cannot specify the `RELEASE` option in a `ROLLBACK TO SAVEPOINT `statement.

Rolling back to a savepoint erases any savepoints marked after that savepoint. The savepoint to which you roll back, however, is not erased. For example, if you mark five savepoints, then roll back to the third, only the fourth and fifth are erased. A `COMMIT` or `ROLLBACK` statement erases all savepoints.

By default, the number of active savepoints in each user session is limited to 5. An active savepoint is one that you marked since the last commit or rollback. Your Database Administrator (DBA) can raise the limit by increasing the value of the Oracle initialization parameter `SAVEPOINTS`. If you give two savepoints the same name, the earlier savepoint is erased.

### 7.7 About Using the RELEASE Option

Oracle rolls back changes automatically if your program terminates abnormally. Abnormal termination occurs when your program does not explicitly commit or roll back work and disconnect from Oracle using the RELEASE option.

Normal termination occurs when your program runs its course, closes open cursors, explicitly commits or rolls back work, disconnects from Oracle, and returns control to the user. Your program will exit gracefully if the last SQL statement it executes is either

    EXEC SQL COMMIT RELEASE;

or

    EXEC SQL ROLLBACK RELEASE;

Otherwise, locks and cursors acquired by your user session are held after program termination until Oracle recognizes that the user session is no longer active. This might cause other users in a multiuser environment to wait longer than necessary for the locked resources.

### 7.8 About Using the SET TRANSACTION Statement

You use the `SET TRANSACTION` statement to begin a read-only or read/write transaction, or to assign your current transaction to a specified rollback segment. A `COMMIT`, `ROLLBACK`, or data definition statement ends a read-only transaction.

Because they allow "repeatable reads," read-only transactions are useful for running multiple queries against one or more tables while other users update the same tables. During a read-only transaction, all queries refer to the same snapshot of the database, providing a multitable, multiquery, read-consistent view. Other users can continue to query or update data as usual. An example of the `SET TRANSACTION` statement follows:

    EXEC SQL SET TRANSACTION READ ONLY;

The `SET TRANSACTION` statement must be the first SQL statement in a read-only transaction and can appear only once in a transaction. The `READ ONLY` parameter is required. Its use does not affect other transactions. Only the `SELECT` (without `FOR` `UPDATE`), `LOCK TABLE`,` SET ROLE`, `ALTER SESSION`, `ALTER SYSTEM`, `COMMIT`, and `ROLLBACK` statements are allowed in a read-only transaction.

In the example, as a store manager, you check sales activity for the day, the past week, and the past month by using a read-only transaction to generate a summary report. The report is unaffected by other users updating the database during the transaction.

    EXEC SQL SET TRANSACTION READ ONLY;
     EXEC SQL SELECT SUM(SALEAMT) INTO :daily FROM SALES
     WHERE SALEDATE = SYSDATE;
     EXEC SQL SELECT SUM(SALEAMT) INTO :weekly FROM SALES
     WHERE SALEDATE > SYSDATE - 7;
     EXEC SQL SELECT SUM(SALEAMT) INTO :monthly FROM SALES
     WHERE SALEDATE > SYSDATE - 30;
     EXEC SQL COMMIT WORK;
    -- simply ends the transaction since there are no changes
    -- to make permanent
    -- format and print report

### 7.9 About Overriding Default Locking

By default, Oracle implicitly (automatically) locks many data structures for you. However, you can request specific data locks on rows or tables when it is to your advantage to override default locking. Explicit locking lets you share or deny access to a table for the duration of a transaction or ensure multitable and multiquery read consistency.

With the `SELECT FOR UPDATE OF` statement, you can explicitly lock specific rows of a table to make sure they do not change before an update or delete is executed. However, Oracle automatically obtains row-level locks at update or delete time. So, use the `FOR UPDATE OF` clause only if you want to lock the rows before the update or delete.

You can explicitly lock entire tables using the `LOCK TABLE` statement.

#### 7.9.1 About Using the FOR UPDATE OF Clause

When you `DECLARE` a cursor that is referenced in the `CURRENT` `OF` clause of an `UPDATE` or `DELETE` statement, you use the FOR UPDATE OF clause to acquire exclusive row locks. `SELECT FOR UPDATE OF` identifies the rows that will be updated or deleted, then locks each row in the active set. (All rows are locked at the open, not as they are fetched.) This is useful, for example, when you want to base an update on the existing values in a row. You must make sure the row is not changed by another user before your update.

The `FOR UPDATE OF `clause is optional. For instance, instead of

    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT ENAME, JOB, SAL FROM EMP WHERE DEPTNO = 20
     FOR UPDATE OF SAL;

you can drop the `FOR UPDATE OF` clause and simply code

    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT ENAME, JOB, SAL FROM EMP WHERE DEPTNO = 20;

The `CURRENT OF` clause signals the precompiler to add a FOR UPDATE clause if necessary. You use the `CURRENT OF` clause to refer to the latest row fetched from a cursor.

#### 7.9.2 Restrictions

If you use the `FOR UPDATE OF` clause, you cannot reference multiple tables. Also, an explicit `FOR UPDATE OF` or an implicit `FOR UPDATE `acquires exclusive row locks. Row locks are released when you commit or rollback (except when you rollback to a savepoint). If you try to fetch from a `FOR UPDATE` cursor after a commit, Oracle generates the following error:

    ORA-01002: fetch out of sequence

#### 7.9.3 About Using the LOCK TABLE Statement

You use the` LOCK TABLE` statement to lock one or more tables in a specified lock mode. For example, the statement locks the EMP table in row share mode. Row share locks allow concurrent access to a table; they prevent other users from locking the entire table for exclusive use.

    EXEC SQL LOCK TABLE EMP IN ROW SHARE MODE NOWAIT;

The lock mode determines what other locks can be placed on the table. For example, many users can acquire row share locks on a table at the same time, but only one user at a time can acquire an exclusive lock. While one user has an exclusive lock on a table, no other users can insert, update, or delete rows in that table. For more information about lock modes, see [SQL Processing for Application Developers](../adfns/sql-processing-for-application-developers.md).

The optional keyword NOWAIT tells Oracle not to wait for a table if it has been locked by another user. Control is immediately returned to your program, so it can do other work before trying again to acquire the lock. (You can check SQLCODE in the SQLCA to see if the table lock failed.) If you omit `NOWAIT`, Oracle waits until the table is available; the wait has no set limit.

A table lock never keeps other users from querying a table, and a query never acquires a table lock. So, a query never blocks another query or an update, and an update never blocks a query. Only if two different transactions try to update the same row will one transaction wait for the other to complete. Table locks are released when your transaction issues a commit or rollback.

### 7.10 About Fetching Across Commits

If you want to intermix commits and fetches, do not use the `CURRENT OF` clause. Instead, select the rowid of each row, then use that value to identify the current row during the update or delete. Consider the following example:

    EXEC SQL DECLARE emp_cursor CURSOR FOR
     SELECT ENAME, SAL, ROWID FROM EMP WHERE JOB = 'CLERK';
    ...
    EXEC SQL OPEN emp_cursor;
    EXEC SQL WHENEVER NOT FOUND GOTO ...
    LOOP
     EXEC SQL FETCH emp_cursor INTO :emp_name, :salary, :row_id;
     ...
     EXEC SQL UPDATE EMP SET SAL = :new_salary
     WHERE ROWID = :row_id;
     EXEC SQL COMMIT;
    ENDLOOP;

**Note:**

The fetched rows are not locked. So, you might get inconsistent results if another user modifies a row after you read it but before you update or delete it.

### 7.11 About Handling Distributed Transactions

A distributed database is a single logical database comprising multiple physical databases at different nodes. A distributed statement is any SQL statement that accesses a remote node using a database link. A distributed transaction includes at least one distributed statement that updates data at multiple nodes of a distributed database. If the update affects only one node, the transaction is non-distributed.

When you issue a commit, changes to each database affected by the distributed transaction are made permanent. If you issue a rollback instead, all the changes are undone. However, if a network or computer fails during the commit or rollback, the state of the distributed transaction might be unknown or in doubt. In such cases, if you have F`ORCE TRANSACTION` system privileges, you can manually commit or roll back the transaction at your local database by using the `FORCE` clause. The transaction must be identified by a quoted literal containing the transaction ID, which can be found in the data dictionary view `DBA_2PC_PENDING`. Some examples follow:

    EXEC SQL COMMIT FORCE '22.31.83';
    ...
    EXEC SQL ROLLBACK FORCE '25.33.86';

`FORCE` commits or rolls back only the specified transaction and does not affect your current transaction. Note that you cannot manually roll back in-doubt transactions to a savepoint.

The `COMMENT` clause in the `COMMIT` statement lets you specify a comment to be associated with a distributed transaction. If ever the transaction is in doubt, Oracle stores the text specified by `COMMENT` in the data dictionary view `DBA_2PC_PENDING `along with the transaction ID. The text must be a quoted literal \<= 50 characters in length. An example follows:

    EXEC SQL COMMIT COMMENT 'In-doubt trans; notify Order Entry';

For more information about distributed transactions, see [Transactions](../cncpt/transactions.md).

### 7.12 Guidelines

The following guidelines will help you avoid some common problems.

#### 7.12.1 About Designing Applications

When designing your application, group logically related actions together in one transaction. A well-designed transaction includes all the steps necessary to accomplish a given task -- no more and no less.

Data in the tables you reference must be left in a consistent state. So, the SQL statements in a transaction should change the data in a consistent way. For example, a transfer of funds between two bank accounts should include a debit to one account and a credit to another. Both updates should either succeed or fail together. An unrelated update, such as a new deposit to one account, should not be included in the transaction.

#### 7.12.2 About Obtaining Locks

If your application programs include SQL locking statements, make sure the Oracle users requesting locks have the privileges needed to obtain the locks. Your DBA can lock any table. Other users can lock tables they own or tables for which they have a privilege, such as `ALTER`, `SELECT`, `INSERT`, `UPDATE`, or `DELETE`.

#### 7.12.3 About Using PL/SQL

If a PL/SQL block is part of a transaction, commits and rollbacks inside the block affect the whole transaction. In the following example, the rollback undoes changes made by the update and the insert:

    EXEC SQL INSERT INTO EMP ...
    EXEC SQL EXECUTE
     BEGIN UPDATE emp
    ...
     ...
     EXCEPTION
     WHEN DUP_VAL_ON_INDEX THEN
     ROLLBACK;
     END;
    END-EXEC;
    ...
