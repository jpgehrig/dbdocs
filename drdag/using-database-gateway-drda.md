Using the Oracle Database Gateway for DRDA involves connecting to the corresponding gateway system and the remote DRDA database associated with the gateway.

- DRDA Gateway Features

- Processing a Database Link

- Accessing the Gateway

- Accessing i5/OS File Members

- Using the Synonym Feature

- Performing Distributed Queries

- Replicating in a Heterogeneous Environment

- Copying Data from Oracle Database to DRDA Server

- Copying Data from DRDA Server to Oracle Database

- Tracing SQL Statements

### DRDA Gateway Features

This section describes the following DRDA gateway features:

- CHAR Semantics

- Multi-byte Character Sets Ratio Suppression

- IPv6 Support

- Gateway Session IDLE Timeout

#### CHAR Semantics

This feature allows the gateway to optionally run in `CHAR` Semantics mode. Rather than always describing UDB `CHAR` columns as `CHAR(n BYTE)`, this feature describes them as `CHAR(n CHAR)` and `VARCHAR(n CHAR)`. The concept is similar to Oracle database `CHAR` Semantics. You need to specify `HS_NLS_LENGTH_SEMANTICS=CHAR` gateway parameter to activate this option. Refer to [Initialization Parameters](database-gateway-drda-initialization-parameters.md) for more detail.

#### Multi-byte Character Sets Ratio Suppression

This feature optionally suppresses the ratio expansion from UDB database to Oracle database involving multi-byte character set. By default, Oracle Database Gateway for DRDA assumes the worst ratio to prevent data being truncated or insufficient buffer size situation. However, if you have specific knowledge of your UDB database and do not want the expansion to occur, you can specify `HS_KEEP_REMOTE_COLUMN_SIZE` parameter to suppress the expansion. Refer to [Initialization Parameters](database-gateway-drda-initialization-parameters.md) for more detail.

#### IPv6 Support

Besides full IPv6 support between Oracle databases and the gateway, IPv6 is also supported between this gateway and UDB database. Refer to the `HS_FDS_CONNECT_INFO` parameter in [Initialization Parameters](database-gateway-drda-initialization-parameters.md) for more detail.

#### Gateway Session IDLE Timeout

You can optionally choose to terminate long idle gateway sessions automatically with the gateway parameter `HS_IDLE_TIMEOUT`. Specifically, when a gateway session is idle for more than the specified time limit, the gateway session is terminated with any pending update rolled back

### Processing a Database Link

The database and application administrators of a distributed database system are responsible for managing the database links that define paths to the Oracle Database Gateway for DRDA. The tasks are as follows:

- Creating Database Links

- Dropping Database Links

- Examining Available Database Links

- Limiting the Number of Active Database Links

#### Creating Database Links

To create a database link and define a path to a remote database, use the `CREATE` `DATABASE LINK `statement. The `CONNECT TO` clause specifies the remote user ID and password to use when creating a session in the remote database. The `USING` clause points to a tnsnames.ora connect descriptor.

**Note:**

If you do not specify a user ID and a password in the `CONNECT TO` clause, then the Oracle database user ID and password are used.

**See Also:**

Refer to Chapter 15, "Security Considerations" in [Oracle Database Gateway Installation and Configuration Guide for IBM AIX on POWER Systems (64-Bit), Linux x86-64, Oracle Solaris on SPARC (64-Bit), Oracle Solaris on x86-64 (64-Bit) and HP-UX Itanium](../otgis/drda-gateway-security-consideration.md) or [Oracle Database Gateway Installation and Configuration Guide for Microsoft Windows](../otgiw/security-consideration-drda-gateway.md) for details.

The following example creates a database link to access information in the DRDA server:

    CREATE PUBLIC DATABASE LINK dblink
    CONNECT TO userid IDENTIFIED BY password
    USING 'tns_name_entry';

where:

`dblink` is the complete database link name.

`user id` is the user ID used to establish a session in the remote database. This user ID must be a valid DRDA server user ID. It must be authorized to any table or file on the DRDA server that is referenced in the SQL commands. Length restrictions on user IDs are dependent on the authorization system used by the DRDA server. In many cases this limit is eight characters, but in other cases, it may be longer. See DB2 platform documentation for limitations.

`password` is the password used to establish a session in the remote database. This password must be a valid DRDA server password. Length restrictions on passwords are dependent on the authorization system used by the DRDA server. In many cases this limit is eight characters, but in other cases, it may be longer. See DB2 platform documentation for limitations.

`tns_name_entry` specifies the Oracle Net connect descriptor used to identify the gateway.

##### Guidelines for Database Links

Database links are active for the duration of a gateway session. If you want to close a database link during a session, then use the `ALTER SESSION CLOSE DATABASE LINK` `dblink` statement.

#### Dropping Database Links

You can drop a database link with the `DROP DATABASE LINK` statement. For example, to drop the public database link named` DBLINK,` use the statement:

    DROP PUBLIC DATABASE LINK dblink;

**Note:**

A database link should not be dropped if it is required to resolve an in-doubt distributed transaction. Refer to Oracle Database Administrator's Guide for additional information about dropping database links.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/DROP-DATABASE-LINK.md) for additional information about dropping database links

#### Examining Available Database Links

The data dictionary of each database stores the definitions of all the database links in that database. The `USER_DB_LINKS` data dictionary view shows the privately defined database links, that is, those accessible to the current Oracle user. The `ALL_DB_LINKS` data dictionary views show all accessible (public and private) database links.

#### Limiting the Number of Active Database Links

You can limit the number of connections from a user process to remote databases with the parameter `OPEN_LINKS`. This parameter controls the number of remote connections that any single user process can concurrently use with a single SQL statement. Refer to [Oracle Database Administrator’s Guide](../admin/distributed-database-concepts.md) for additional information about limiting the number of active database links.

### Accessing the Gateway

To access the gateway, complete the following steps on the Oracle database:

1.  Example 3-1
2.  Example 3-2
3.  Example 3-3

Example 3-1 Login to the Oracle Database

Login to the Oracle database to access the gateway

Example 3-2 Create a database link to the DRDA Database

For example, use:

    CREATE PUBLIC DATABASE LINK DRDA
    CONNECT TO ORADRDA IDENTIFIED BY oracle_pw
    USING 'tns_name_entry'

Example 3-3 Retrieve data from the DRDA Database

This query fetches the `TABLE` table in the schema `SECURE`, using the name `ORADRDA` as the DRDA server user profile. The `ORADRDA` user profile must have the appropriate privileges on the DRDA server to access the `SECURE.TABLE` files:

    SELECT * FROM SECURE.TABLE@DRDA

The following is an example of the error messages that are displayed if insufficient privileges are displayed:

    ORA-28500: connection from ORACLE to a non-Oracle system returned this message:
    [Oracle][ODBC DB2 Wire Protocol driver][UDB DB2 for Windows, UNIX, and
    Linux]ORADRDA DOES NOT HAVE PRIVILEGE TO PERFORM OPERATION SELECT ON THIS
    OBJECT SECURE.TABLE.
    ORA-02063: preceding 2 lines from DRDA

### Accessing i5/OS File Members

Access to i5/OS files and file members is not specifically controlled by DRDA or the gateway. However, DB2 UDB for iSeries uses a naming convention that implies that the file member name is the same as the name of the file being addressed. For example, accessing `schema.table` implies that table is the file name and also that table is the file member name being accessed.

To access file members with names that differ from the associated file name, you must create a view within the file so that DB2 UDB for iSeries can reference the correct file member.

One method for creating this view involves issuing the i5/OS command `Create Logical File` (`CRTLF`). This action creates a logical association between the file name and the file member name.

**See Also:**

For additional information, refer to the i5/OS Command Language (CL) documentation or to the DB2 UDB for iSeries SQL reference document.

### Using the Synonym Feature

You can provide complete data, location, and network transparency by using the synonym feature of Oracle database. When a synonym is defined, the user need not know the underlying table or network protocol being used. A synonym can be public, which means it is available to all Oracle users. A synonym can also be defined as private, available only to the user who created it. Refer to [Oracle Database Reference](../refrn/index.md) for details on the synonym feature.

The following statement creates a system-wide synonym for the `EMP` file in the DRDA server with ownership of `ORACLE`:

    CREATE PUBLIC SYNONYM EMP FOR ORACLE.EMP@DRDA

### Performing Distributed Queries

The Oracle Database Gateway technology enables the execution of distributed queries that join data in an Oracle database and in DRDA servers and data from any other data store for which Oracle provides a gateway. These complex operations can be completely transparent to the users requesting the data.

The following example joins data between an Oracle database, DB2 UDB for z/OS, and a DRDA server:

    SELECT o.custname, p.projno, e.ename, sum(e.rate*p.hours)
    FROM orders@DB2 o, EMP@ORACLE7 e, projects@DRDA p
    WHERE o.projno = p.projno
    AND p.empno = e.empno
    GROUP BY o.custname, p.projno, e.ename

A combination of views and synonyms, using the following SQL statements, keeps the process of distributed queries transparent to the user:

    CREATE SYNONYM orders for orders@DB2;
    CREATE SYNONYM PROJECTS for PROJECTS@DRDA;
    CREATE VIEW details (custname,projno,ename,spend)
    AS
    SELECT o.custname, p.projno, e.ename, sum(e.rate*p.hours)
    FROM orders o, EMP e, projects p
    WHERE o.projno = p.projno
    AND p.empno = e.empno
    GROUP BY o.custname, p.projno, e.ename

The following SQL statement retrieves information from these three data stores in one command:

    SELECT * FROM DETAILS;

The results of this command are:

    CUSTNAME   PROJNO     ENAME      SPEND
    ---------  ---------  ---------  ---------
    ABC Co.    1         Jones      400
    ABC Co.    1         Smith      180
    XYZ Inc.   2         Jones      400
    XYZ Inc.   2         Smith      180

#### Two-Phase Commit Processing

To fully participate in a two-phase commit transaction, a server must support the `PREPARE TRANSACTION` statement. The `PREPARE TRANSACTION` statement ensures that all participating databases are prepared to `COMMIT` or to `ROLLBACK` a specific unit of work.

Oracle database supports the `PREPARE TRANSACTION` statement. Any number of Oracle database can participate in a distributed two-phase commit transaction. The `PREPARE TRANSACTION` statement is performed automatically when a `COMMIT` is issued explicitly by an application or implicitly at the normal end of the application.

The gateway does not support the `PREPARE TRANSACTION` statement. This limits the two-phase commit protocol when the gateway participates in a distributed transaction. The gateway becomes the commit focal point site of a distributed transaction. The gateway is configured as commit/confirm, so it is always the commit point site, regardless of the commit point strength setting. The gateway commits the unit of work after verifying that all Oracle databases in the transaction have successfully committed their work. The gateway must coordinate the distributed transaction so that only one gateway instance can participate in a two-phase commit transaction.

Two-phase commit transactions are recorded in the `HS_TRANSACTION_LOG` table (see the initialization parameter `HS_FDS_TRANSACTION_LOG`), which is created during installation. This table is created when the `o2pc.sql `script is run. The owner of this table also owns the package. Refer to "DRDA Gateway Package Binding Considerations" on [Oracle Database Gateway Installation and Configuration Guide for IBM AIX on POWER Systems (64-Bit), Linux x86-64, Oracle Solaris on SPARC (64-Bit), Oracle Solaris on x86-64 (64-Bit) and HP-UX Itanium](../otgis/config-drda-server.md) or [Oracle Database Gateway Installation and Configuration Guide for Microsoft Windows](../otgiw/config-drda-server.md), depending on your platform, for more information.

#### Distributed DRDA Transactions

Because the `HS_TRANSACTION_LOG` table is used to record the status of a gateway transaction, this table must be in at the database where the DRDA update takes place. Therefore, all updates that take place over the gateway must be local to the IBM database.

**Note:**

- Updates to the `HS_TRANSACTION_LOG` table cannot be part of an IBM distributed transaction.

- The default commit mode on OS400 V5R1 and later is `READ UNCOMMITTED (*CHG)` and this requires files to be journaled. Hence, the object specified by the `HS_TRANSACTION_LOG` initialization parameter must be journaled.

For additional information about the two-phase commit process, refer to [Oracle Database Heterogeneous Connectivity User's Guide](../heter/two-phase-commit-protocol.md).

### Replicating in a Heterogeneous Environment

Oracle Database Gateway for DRDA provides a number of options for replicating Oracle and non-Oracle data throughout the enterprise.

#### Oracle Database Triggers

When updates are made to Oracle database, synchronous copies of Oracle and non-Oracle data can be maintained automatically by using Oracle database triggers.

#### Oracle Snapshots

Oracle Database Gateway for DRDA can use the Oracle snapshot feature to automatically replicate non-Oracle data into Oracle database. The complete refresh capability of Oracle snapshot can be used to propagate a complete copy or a subset of the non-Oracle data into Oracle database at user-defined intervals.

### Copying Data from Oracle Database to DRDA Server

This Oracle SQL INSERT command now works with the CALLBACK feature:

    INSERT INTO DRDA_table SELECT * FROM local_table

Alternatively, you could use sqlplus `COPY` command. The `COPY` command enables you to copy data from Oracle database to a DRDA server. To copy data from your Oracle database to the DRDA server, you can also use:

    COPY FROM username/password@connect_identifier -
    INSERT destination_table -
    USING query

For example, to select all rows from the local Oracle` ``EMP` table, insert them into the` EMP `table on the DRDA server, and commit the transaction, use:

    COPY FROM scott/tiger@ORACLE -
    INSERT scott.EMP@DRDA -
    USING SELECT * FROM EMP

The SQL\*Plus `COPY` command supports `APPEND`, `CREATE`, `INSERT`, and `REPLACE` commands. However, `INSERT` is the only command supported when copying to the DRDA server. For more information about the `COPY` command, refer to [SQL\*Plus User's Guide and Reference](../sqpug/COPY.md).

### Copying Data from DRDA Server to Oracle Database

The `CREATE TABLE` command enables you to copy data from a DRDA server to Oracle database. To create a table on your Oracle database and to insert rows from a DRDA server table, use:

    CREATE TABLE table_name
    AS query

A SQL `INSERT` into an Oracle table can be done selecting data from the gateway as follows:

    INSERT INTO local_table SELECT * FROM drda_table

The following example creates the table `EMP` in your local Oracle database and inserts the rows from the `EMP` table on the DRDA server:

    CREATE TABLE EMP
    AS SELECT * FROM scott.EMP@DRDA

Alternatively, you can use the SQL\*Plus `COPY` command to copy data from a DRDA server to Oracle database. For more information about the `COPY` command, refer to [SQL\*Plus User's Guide and Reference](../sqpug/COPY.md).

### Tracing SQL Statements

SQL statements issued through the gateway can be changed before reaching the DRDA database. These changes are made to make the format acceptable to the gateway or to make Oracle SQL compatible with DRDA server SQL. Oracle database and the gateway can change the statements depending on the situation.

For various reasons, you might need to assess whether the gateway has altered the statement correctly or whether the statement could be rewritten to improve performance. SQL tracing is a feature that allows you to view the changes made to a SQL statement by the Oracle database or the gateway.

SQL tracing reduces gateway performance. Use tracing only when testing and debugging your application. Do not enable SQL tracing when the application is running in a production environment. For more information about enabling SQL tracing, refer to the section on "[SQL Tracing and the Gateway](database-gateway-drda-error-messages.md) " in [Error Messages\_ Diagnosis\_ and Reporting](database-gateway-drda-error-messages.md).
