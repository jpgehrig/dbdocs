You can migrate Oracle Text applications into a new Oracle Database release.

When you upgrade to a new release of Oracle Database, you may have difficulty migrating your applications from earlier releases of Oracle Text. Where applicable, Oracle provides information about the migration steps to move Oracle Text applications into the new release.

This chapter contains the following topics:

- Oracle Text and Rolling Upgrade with Logical Standby

- Identifying and Copying Oracle Text Files to a New Oracle Home

**See Also:**

[Oracle Database Upgrade Guide](../upgrd/intro-to-upgrading-oracle-database.md) for information on upgrading Oracle Database and topics about migrating applications

### 18.1 Performing a Rolling Upgrade with a Logical Standby Database

You can use a logical standby database to perform a rolling upgrade of Oracle Database. To incur minimal downtime on the primary database, you can run different releases of Oracle Database on the primary and logical standby databases while you upgrade your databases, one at a time. Oracle Text takes full advantage of upgrading Oracle Text indexes.

All CTX PL/SQL procedures are fully replicated to the standby database and are upgraded, except with certain limitations for these procedures:

- CTX_DDL PL/SQL Procedures

- CTX_OUTPUT PL/SQL Procedures

- CTX_DOC PL/SQL Procedures

**See Also:**

[Oracle Data Guard Concepts and Administration](../sbydb/creating-oracle-data-guard-logical-standby.md) for information on creating a logical standby database to perform rolling upgrades

#### 18.1.1 CTX_DDL PL/SQL Procedures

Oracle Database uses rowids internally for the construction of indexes. The following `CTX_DDL` procedures are not fully replicated to the standby:

- `ADD_MDATA`

- `REMOVE_MDATA`

#### 18.1.2 CTX_OUTPUT PL/SQL Procedures

Only `CTX_OUTPUT.ENABLE_QUERY_STATS` and `CTX_OUTPUT.DISABLE_QUERY_STATS` are replicated. If you enable Oracle Text logging on the primary database before you run an operation that causes logging, then the operation runs with logging on the primary database and without logging on the secondary database.

#### 18.1.3 CTX_DOC PL/SQL Procedures

When you use the following `CTX_DOC` procedures with Oracle Text Result Tables, the data stored in the tables is replicated. When these procedures are used without Result Tables, they are not replicated.

- `CTX_DOC.SET_KEY_TYPE`

- `CTX_DOC.FILTER`

- `CTX_DOC.GIST`

- `CTX_DOC.MARKUP`

- `CTX_DOC.TOKENS`

- `CTX_DOC.THEMES`

- `CTX_DOC.HIGHLIGHT`

- `CTX_DOC.FILTER_CLOB_QUERY`

- `CTX_DOC.MARKUP_CLOB_QUERY`

- `CTX_DOC.HIGHLIGHT_CLOB_QUERY`

**See Also:**

[Oracle Data Guard Concepts and Administration](../sbydb/using-sql-apply-to-perform-rolling-upgrade.md) for information on performing a rolling upgrade for minimal downtime on the primary database

### 18.2 Identifying and Copying Oracle Text Files to a New Oracle Home

To upgrade Oracle Text, use this procedure to identify and copy required files from your existing Oracle home to the new release Oracle home. Complete this task after you upgrade Oracle Database.

Certain Oracle Text features rely on files under the Oracle home that you have configured. After manually upgrading to a new Oracle Database release, or after any process that changes the Oracle home, you must identify and move these files manually. These files include user filters, mail filter configuration files, and all knowledge base extension files. After you identify the files, copy the files from your existing Oracle home to the new Oracle home.

To identify and copy required files from your existing Oracle home to the new release Oracle home:

1.  Log in with the `SYS,` `SYSTEM,` or `CTXSYS` system privileges for the upgraded database.
2.  Under the Oracle home of the upgraded database, run the `$ORACLE_HOME/ctx/admin/ctx_oh_files.sql` SQL script.
    For example:

        sqlplus / as sysdba
        connected
        SQL> @?/ctx/admin/ctx_oh_files
3.  Review the output of the `ctx_oh_files.sql` command, and copy the files to the new Oracle home.
