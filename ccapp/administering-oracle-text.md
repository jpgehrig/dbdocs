Become familiar with Oracle Text administration.

This chapter contains the following topics:

- Oracle Text Users and Roles

- DML Queue

- CTX_OUTPUT Package

- CTX_REPORT Package

- Text Manager in Oracle Enterprise Manager

- Servers and Indexing

- Tracking Database Feature Usage in Oracle Enterprise Manager

- Oracle Text on Oracle Real Application Clusters

- Configuring Oracle Text in Oracle Database Vault Environment

- Unsupported Oracle Text Operations in Oracle Database Vault Realm

### 17.1 Oracle Text Users and Roles

While any user can create an Oracle Text index and enter a `CONTAINS` query, Oracle Text provides the `CTXSYS` user for administration and the `CTXAPP` role for application developers.

This section contains the following sections:

- CTXSYS User

- CTXAPP Role

- Granting Roles and Privileges to Users

#### 17.1.1 CTXSYS User

The `CTXSYS` user is created during installation and can:

- View all indexes

- Sync all indexes

- Run `ctxkbtc,` the knowledge base extension compiler

- Query all system-defined views

- Perform all tasks of a user with the `CTXAPP` role

**Note:**

In earlier releases of Oracle Text, `CTXSYS` had `SYSDBA` privileges, and only `CTXSYS` users could perform certain functions, such as modifying system-defined preferences or setting system parameters.

Starting with Oracle Database Release 19c, the `CTXSYS` user is a schema only user. To use the `CTXSYS` schema, run the following statements:

    connect / as sysdba;

    alter session set CURRENT_SCHEMA=CTXSYS;

#### 17.1.2 CTXAPP Role

The `CTXAPP` role is a system-defined role that enables users to:

- Create and delete Oracle Text preferences

- Use the Oracle Text PL/SQL packages

#### 17.1.3 Granting Roles and Privileges to Users

The system uses the standard `SQL` model for granting roles to users. To grant an Oracle Text role to a user, use the `GRANT` statement.

In addition, to allow application developers to call procedures in the Oracle Text PL/SQL packages, you must explicitly grant `EXECUTE` privileges for the Oracle Text package to each user.

**See Also:**

"[Creating an Oracle Text User](getting-started-with-oracle-text.md)"

### 17.2 DML Queue

When you make inserts, updates, or deletes to documents in your base table, the data manipulation language (DML) queue stores the requests for documents waiting to be indexed. When you synchronize the index with `CTX_DDL`.`SYNC_INDEX,` requests are removed from this queue.

You can query pending insert, update, and delete operations with the `CTX_PENDING` and `CTX_USER_PENDING` views.

You can query insert, update, and delete errors with the `CTX_INDEX_ERRORS` or `CTX_USER_INDEX_ERRORS` view.

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-views.md) for more information about these views

### 17.3 CTX_OUTPUT Package

Use the `CTX_OUTPUT` PL/SQL package to log indexing and document service requests.

**See Also:**

[Oracle Text Reference](../ccref/CTX_OUTPUT-package.md) for more information about this package

### 17.4 CTX_REPORT Package

Use the `CTX_REPORT` package to produce reports on indexes and queries. These reports can help you fine-tune or troubleshoot your applications.

**See Also:**

[Oracle Text Reference](../ccref/CTX_REPORT-package.md) for more information about this package

The `CTX_REPORT` package contains the following procedures:

#### CTX_REPORT.DESCRIBE_INDEX and CTX_REPORT.DESCRIBE_POLICY

These procedures create reports that describe an existing index or policy, including the settings of the index metadata, the indexing objects, the settings of the attributes of the objects, and (for `CTX_REPORT.DESCRIBE_INDEX`) the index partition information, if any. These procedures are especially useful for diagnosing index-related problems.

This is sample output from `DESCRIBE_INDEX,` run on a simple context index:

    =================================================================
                            INDEX DESCRIPTION
    =================================================================
    index name:                      "DR_TEST"."TDRBPRX0"
    index id:                        1160
    index type:                      context
    base table:                      "DR_TEST"."TDRBPR"
    primary key column:              ID
    text column:                     TEXT2
    text column type:                VARCHAR2(80)
    language column:
    format column:
    charset column:
    =================================================================
                              INDEX OBJECTS
    =================================================================
    datastore:                       DIRECT_DATASTORE
    filter:                          NULL_FILTER
    section group:                   NULL_SECTION_GROUP
    lexer:                           BASIC_LEXER
    wordlist:                        BASIC_WORDLIST
       stemmer:                         ENGLISH
       fuzzy_match:                     GENERIC
    stoplist:                        BASIC_STOPLIST
       stopword:                       teststopword
    storage:                         BASIC_STORAGE
       r_table_clause:                  lob (data) store as (cache)
       i_index_clause:                  compress 2

#### CTX_REPORT.CREATE_INDEX_SCRIPT and CTX_REPORT.CREATE_POLICY_SCRIPT

`CREATE_INDEX_SCRIPT` creates a SQL\*Plus script that can create a duplicate of a given Oracle Text index. Use this when you have an index but you do not have the original script (if any) that was used to create this index, and you want to be able to re-create the index. For example, if you accidentally drop a script, `CREATE_INDEX_SCRIPT` can re-create it. Likewise, `CREATE_INDEX_SCRIPT` can be useful if you have inherited indexes from another user but not the scripts that created them.

`CREATE_POLICY_SCRIPT` does the same thing as `CREATE_INDEX_SCRIPT,` except that it enables you to re-create a policy instead of an index.

This is sample output from `CREATE_INDEX_SCRIPT,` run on a simple context index (not a complete listing):

    begin
      ctx_ddl.create_preference('"TDRBPRX0_DST"','DIRECT_DATASTORE');
    end;
    /
    ...
    /
    begin
      ctx_ddl.create_section_group('"TDRBPRX0_SGP"','NULL_SECTION_GROUP');
    end;
    /
    ...
    begin
      ctx_ddl.create_preference('"TDRBPRX0_WDL"','BASIC_WORDLIST');
      ctx_ddl.set_attribute('"TDRBPRX0_WDL"','STEMMER','ENGLISH');
      ctx_ddl.set_attribute('"TDRBPRX0_WDL"','FUZZY_MATCH','GENERIC');
    end;
    /
    begin
      ctx_ddl.create_stoplist('"TDRBPRX0_SPL"','BASIC_STOPLIST');
      ctx_ddl.add_stopword('"TDRBPRX0_SPL"','teststopword');
    end;
    /
    ...
    /
    begin
      ctx_output.start_log('TDRBPRX0_LOG');
    end;
    /
    create index "DR_TEST"."TDRBPRX0"
      on "DR_TEST"."TDRBPR"
          ("TEXT2")
      indextype is ctxsys.context
      parameters('
        datastore       "TDRBPRX0_DST"
        filter          "TDRBPRX0_FIL"
        section group   "TDRBPRX0_SGP"
        lexer           "TDRBPRX0_LEX"
        wordlist        "TDRBPRX0_WDL"
        stoplist        "TDRBPRX0_SPL"
        storage         "TDRBPRX0_STO"
      ')
    /

#### CTX_REPORT.INDEX_SIZE

This procedure creates a report of the names of the internal index objects, along with their tablespaces, allocated sizes, and used sizes. It is useful for DBAs who may need to monitor the size of their indexes (for example, when disk space is at a premium).

Sample output from this procedure looks like this (partial listing):

    =================================================================
                    INDEX SIZE FOR DR_TEST.TDRBPRX10
    =================================================================
    TABLE:                          DR_TEST.DR$TDRBPRX10$I
    TABLESPACE NAME:                DRSYS
    BLOCKS ALLOCATED:                                            4
    BLOCKS USED:                                                 1
    BYTES ALLOCATED:                               8,192 (8.00 KB)
    BYTES USED:                                    2,048 (2.00 KB)

    INDEX (LOB):                    DR_TEST.SYS_IL0000023161C00006$$
    TABLE NAME:                     DR_TEST.DR$TDRBPRX10$I
    TABLESPACE NAME:                DRSYS
    BLOCKS ALLOCATED:                                            5
    BLOCKS USED:                                                 2
    BYTES ALLOCATED:                             10,240 (10.00 KB)
    BYTES USED:                                    4,096 (4.00 KB)

    INDEX (NORMAL):                 DR_TEST.DR$TDRBPRX10$X
    TABLE NAME:                     DR_TEST.DR$TDRBPRX10$I
    TABLESPACE NAME:                DRSYS
    BLOCKS ALLOCATED:                                            4
    BLOCKS USED:                                                 2
    BYTES ALLOCATED:                               8,192 (8.00 KB)
    BYTES USED:                                    4,096 (4.00 KB)

#### CTX_REPORT.INDEX_STATS

`INDEX_STATS` produces a variety of calculated statistics about an index, such as how many documents are indexed, how many unique tokens in the index, average size of its tokens, and fragmentation information for the index. Optimizing stoplists is an example of a use for `INDEX_STATS.`

#### CTX_REPORT.QUERY_LOG_SUMMARY

This procedure creates a report of logged queries, which you can use to perform simple analyses. With query analysis, you can find out:

- Which queries were made

- Which queries were successful

- Which queries were unsuccessful

- How many times each query was made

You can combine these factors in various ways, such as determining the 50 most frequent unsuccessful queries made by your application.

#### CTX_REPORT.TOKEN_INFO

`TOKEN_INFO` helps you diagnose query problems. For example, use it to check that index data is not corrupted and to find out which documents are producing unexpected or bad tokens.

#### CTX_REPORT.TOKEN_TYPE

`TOKEN_TYPE` is a lookup function that is used mainly as input to other functions (`CTX_DDL.OPTIMIZE_INDEX`, `CTX_REPORT.TOKEN_INFO`, and so on).

**See Also:**

- [Oracle Text Reference](../ccref/CTX_REPORT-package.md) for an example of the output of `CTX_REPORT.INDEX_STATS` procedure

- [Oracle Text Reference](../ccref/CTX_REPORT-package.md) for an example of the output of `CTX_REPORT.QUERY_LOG_SUMMARY` procedure

### 17.5 Text Manager in Oracle Enterprise Manager

Oracle Enterprise Manager provides Text Manager for configuring, maintaining, and administering Oracle Text indexes. With Text Manager, you can perform all of the basic configuration and administration tasks for Oracle Text indexes. You can monitor the overall health of Oracle Text indexes for a single Oracle Database instance or for the Oracle Real Application Clusters environment. Text Manager provides summaries of critical information and enables you to drill down to the level of detail that you want, to resolve issues, and to understand any actions that you need to take.

The Text Indexes page shows the jobs that are in progress, that are scheduled within the last seven days, or that are experiencing problems. From this page, you can go to the Job Scheduler to see a summary of all jobs for this database instance and to manage selected jobs. The online help in Oracle Enterprise Manager provides details and procedures for using each Text Manager feature.

This section contains the following sections:

- Using Text Manager

- Viewing General Information for an Oracle Text Index

- Checking Oracle Text Index Health

**Note:**

You cannot create an Oracle Text index with Text Manager. Use the `CREATE` `INDEX` statement to create an Oracle Text index as described in [Indexing with Oracle Text](indexing-with-oracle-text.md) under [Creating Oracle Text Indexes](creating-oracle-text-indexes.md).

#### 17.5.1 Using Text Manager

You can access Text Manager to manage Oracle Text indexes or schedule jobs for a specific index.

On the main Text Manager page, you can perform the following actions on the selected index from the Actions list:

- Synchronize

- Optimize

- Rebuild

- Resume Failed Operation

- Show Logs

- Show Errors

1.  Sign in to the database with a user account that is authorized to access Cloud Control. For example, use `SYS` or `SYSTEM` and the password that you specified during database installation.
2.  On the Database Home page, click the Schema tab.
3.  In the Text Manager group, select Text Indexes.
    The Text Indexes page displays a list of Oracle Text indexes for this database instance.

When you select an Oracle Text index from the Text Indexes page, edit and action options become available for that index. For example, to configure attributes for searching, click Edit for the selected index. On the Edit Text Index page, you can set such attributes as Wild Card Maximum Term, Fuzzy Score, and Number of Fuzzy Expansions. You can also change index and partition names, and specify settings for `NETWORK_DATASTORE`.

#### 17.5.2 Viewing General Information for an Oracle Text Index

Use the View Text Index page to see general information about a specific index, such as index type, parallel degree, synchronization mode, wild card limit, fuzzy score, fuzzy numeric result, and datastore. Information about any partitions on the index is also available.

To view general information for an Oracle Text index, on the Text Indexes page, in the list of indexes, click the name of the index. The View Text Index page opens and the General tab is selected. From here, you can select actions to perform maintenance tasks.

#### 17.5.3 Checking Oracle Text Index Health

In Text Manager, the Text Indexes page displays the Oracle Text indexes for the database instance. Use that page to help you understand the critical actions that are necessary to make sure that the entire application is performing properly.

Use the Text Indexes page to see:

- The status of the indexes and jobs submitted during the last seven days.

- The number of Oracle Text indexes that contain invalid partitions, and which are, therefore, invalid. The number of partitions that are invalid, if any, for all Oracle Text indexes is also shown.

- The number of indexes and partitions that are in an in-progress state.

- The number of indexes where all partitions are valid, and no activity is in progress.

- The sum total of the Oracle Text indexes found for this database instance.

- The index type for each Oracle Text index, the owner, the number of documents that are not synchronized, total number of documents, and percentage of fragmentation.

After you select an Oracle Text index from the list, options become available for editing or performing actions.

### 17.6 Servers and Indexing

You index documents and enter queries with standard SQL. No server is needed for performing batch insert, update, and delete operations. You can synchronize the `CONTEXT` index with the `CTX_DDL`.`SYNC_INDEX` procedure, or from Text Manager in Oracle Enterprise Manager.

**See Also:**

[Indexing with Oracle Text](indexing-with-oracle-text.md) for more information about indexing and index synchronization

### 17.7 Tracking Database Feature Usage in Oracle Enterprise Manager

In Oracle Enterprise Manager, Database Feature Usage statistics provide an approximation of how often various database features are used. Tracking this information is useful for application development and for auditing.

To access Database Feature Usage, in Oracle Enterprise Manager, click the Server tab, and then select Database Feature Usage under Database Configuration.

Database Feature Usage captures the following information for Oracle Text:

- Index Usage Statistics: The number of existing indexes in the database for the `CONTEXT, CTXCAT,` and `CTXRULE` index types

- SQL Operator Usage Statistics: Whether the user has ever used the `CONTAINS, CATSEARCH,` and `MATCHES` operators

- Package Usage Statistics: How often, if ever, and when the following packages were used:

  - `CTX_ADM`

  - `CTX_CLS`

  - `CTX_DDL`

  - `CTX_DOC`

  - `CTX_OUTPUT`

  - `CTX_QUERY`

  - `CTX_REPORT`

  - `CTX_THES`

  - `CTX_ULEXER`

**Note:**

The feature usage tracking statistics might not be 100 percent accurate.

### 17.8 Oracle Text on Oracle Real Application Clusters

For maximum throughput and performance for OLAP applications, you can parallelize Oracle Text queries across Oracle Real Application Clusters (Oracle RAC) nodes. You can manage Oracle Text indexes on Oracle RAC nodes with Text Manager in Oracle Enterprise Manager, as described in "Text Manager in Oracle Enterprise Manager".

**See Also:**

"[Parallelizing Queries Across Oracle RAC Nodes](tuning-oracle-text.md)"

### 17.9 Configuring Oracle Text in Oracle Database Vault Environment

In an Oracle Database Vault environment, you can create a `CTXSYS` user if you have the `DV_ACCTMGR` role.

To create a `CTXSYS` user, run the `@$ORACLE_HOME/ctx/admin/catctx_user.sql` SQL script. Then, connect as `SYS` user and run the `@$ORACLE_HOME/ctx/admin/catctx_schema.sql` SQL script.

**Note:**

If the `SYS` user also has the `DV_ACCTMGR` role, then you can run the `@$ORACLE_HOME/ctx/admin/catctx.sql` SQL script which installs both, `catctx_user.sql` and `catctx_schema.sql` scripts.

### 17.10 Unsupported Oracle Text Operations in Oracle Database Vault Realm

Oracle Database Vault realms place restrictions on DDL operations within a realm. For this reason, once you are added to a realm but if you are not authorized in the realm, then you cannot create, alter, or drop an Oracle Text index. You also cannot use any DDL operations contained in the `CTX_DDL` package.

The DDL error messages and query error messages on indexes that could not be created within the realm might indicate insufficient privileges as the cause. The insufficient privilege message is specific to DDL operations not being allowed within the realm.
