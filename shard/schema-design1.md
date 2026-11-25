## 6 Sharded Database Schema Design

To obtain the benefits of sharding, the schema of a sharded database should be designed in a way that maximizes the number of database requests executed on a single shard.

### Sharded Database Schema Design Considerations

Design of the database schema has a big impact on the performance and scalability of a sharded database. An improperly designed schema can lead to unbalanced distribution of data and workload across shards and large percentage of multi-shard operations.

The data model should be a hierarchical tree structure with a single root table. Oracle Sharding supports any number of levels within the hierarchy.

To obtain the benefits of sharding, the schema of a sharded database should be designed in a way that maximizes the number of database requests executed on a single shard.

A sharded database schema consists of a sharded table family and duplicated tables with the following characteristics.

Sharded table family

- A set of tables which are equi-partitioned by the sharding key.
  - Related data is always stored and moved together.
  - Joins and integrity constraint checks are done within a shard.
- The sharding method and key are based on the application's requirements.
- The sharding key must be included in the primary key.

Duplicated tables

- Non-sharded tables which are replicated to all shards.
- Usually contain common reference data.
- Can be read and updated on each shard.

Planning a Sharded Database Schema Design

Once the sharded database is populated with data, it is impossible to change many attributes of the schema, such as whether a table is sharded or duplicated, sharding key, and so on. Therefore, the following points should be carefully considered before deploying a sharded database.

- Which tables should be sharded?

- Which tables should be duplicated?

- Which sharded table should be the root table?

- What method should be used to link other tables to the root table?

- Which sharding method should be used?

- Which sharding key should be used?

- Which super sharding key should be used (if the sharding method is composite)?

### Choosing Sharding Keys

Sharded table partitions are distributed across shards at the tablespace level, based on a sharding key. Examples of keys include customer ID, account number, and country ID.

Sharding keys must adhere to the following characteristics.

- The sharding key should be very stable; its value should almost never change.

- The sharding key must be present in all of the sharded tables. This allows the creation of a family of equi-partitioned tables based on the sharding key.

- Joins between tables in a table family should be performed using the sharding key.

Sharding Keys for System-Managed Sharded Databases

For the system-managed sharding method, the sharding key must be based on a column that has high cardinality; the number of unique values in this column must be much bigger than the number of shards. Customer ID, for example, is a good candidate for the sharding key, while a United States state name is not.

A sharding key can be a single column or multiple columns. When multiple columns are present, the hash of the columns are concatenated to form the sharding key.

The following examples create a sharded table called Customers and specify that columns `cust_id` and `name` form the sharding keys for the table.

    CREATE SHARDED TABLE customers
    (cust_id     NUMBER NOT NULL
    , name        VARCHAR2(50)
    , address     VARCHAR2(250)
    , region      VARCHAR2(20)
    , class       VARCHAR2(3)
    , signup      DATE,
    CONSTRAINT cust_pk PRIMARY KEY(cust_id, name))
    PARTITION BY CONSISTENT HASH (cust_id,name)
    PARTITIONS AUTO
    TABLESPACE SET ts1;

    CREATE SHARDED TABLE Orders
    ( OrderNo   NUMBER NOT NULL
    , CustNo    NUMBER NOT NULL
    , Name      VARCHAR2(50) NOT NULL
    , OrderDate DATE
    , CONSTRAINT OrderPK PRIMARY KEY (CustNo, Name, OrderNo)
    , CONSTRAINT CustFK  FOREIGN KEY (CustNo, Name) REFERENCES Customers(Cust_ID, Name)
    )
    PARTITION BY REFERENCE (CustFK);

Sharding Keys for Composite Sharded Databases

Composite sharding enables two levels of sharding - one by list or range and another by consistent hash. This is accomplished by the application providing two keys: a super sharding key and a sharding key.

Composite sharding does not support multi-column `LIST` partitionsets, as shown here.

    CREATE SHARDED TABLE customers (
    cust_id     NUMBER NOT NULL,
    Name    VARCHAR2(50) NOT NULL,
    class VARCHAR2(3) NOT NULL ,
    class2 number not null,
    CONSTRAINT cust_pk PRIMARY KEY(cust_id,name,class))
    PARTITIONSET BY LIST (class, class2)
    PARTITION BY CONSISTENT HASH (cust_id,name)
    PARTITIONS AUTO (
    PARTITIONSET silver VALUES (('SLV',1),('BRZ',2)) TABLESPACE SET ts1
    PARTITIONSET gold   VALUES (('GLD',3),('OTH',4)) TABLESPACE SET ts2);

    PARTITION BY CONSISTENT HASH (cust_id,name)
    *
    ERROR at line 8:
    ORA-02514: list PARTITIONSET method expects a single partitioning column

Multi-column `RANGE` partitionsets are supported, as shown below.

    CREATE SHARDED TABLE customers (
    cust_id     NUMBER NOT NULL,
    Name    VARCHAR2(50) NOT NULL,
    class number NOT NULL ,
    class2 number not null,
    CONSTRAINT cust_pk PRIMARY KEY(cust_id,name,class))
    PARTITIONSET BY RANGE (class, class2)
    PARTITION BY CONSISTENT HASH (cust_id,name)
    PARTITIONS AUTO (
    PARTITIONSET silver VALUES LESS THAN (10,100) TABLESPACE SET ts1,
    PARTITIONSET gold   VALUES LESS THAN (20,200) TABLESPACE SET ts2);

    Table created.

In both of the above cases, the sharding key (not the partitionset key) can be multi-column.

Sharding Keys for User-Defined Sharded Databases

For partition by list in user-defined sharding, Oracle Sharding expects a single sharding key column. An error is thrown when multiple columns are specified for a list-partitioned sharded table.

    CREATE SHARDED TABLE accounts
    ( id             NUMBER
    , account_number NUMBER
    , customer_id    NUMBER
    , branch_id      NUMBER
    , state          VARCHAR(2) NOT NULL
    , state2         VARCHAR(2) NOT NULL
    , status         VARCHAR2(1)
    )
    PARTITION BY LIST (state,state2)
    ( PARTITION p_northwest VALUES ('OR', 'WA') TABLESPACE ts1
    , PARTITION p_southwest VALUES ('AZ', 'UT', 'NM') TABLESPACE ts2
    , PARTITION p_northcentral VALUES ('SD', 'WI') TABLESPACE ts3
    , PARTITION p_southcentral VALUES ('OK', 'TX') TABLESPACE ts4
    , PARTITION p_northeast VALUES ('NY', 'VM', 'NJ') TABLESPACE ts5
    , PARTITION p_southeast VALUES ('FL', 'GA') TABLESPACE ts6
    );

    ERROR at line 1:
    ORA-03813: list partition method expects a single partitioning column in
    user-defined sharding

For a range-partitioned sharded table, you can specify multiple columns as sharding key columns.

    CREATE SHARDED TABLE accounts
    ( id             NUMBER
    , account_number NUMBER
    , customer_id    NUMBER
    , branch_id      NUMBER
    , state          NUMBER NOT NULL
    , state2         NUMBER NOT NULL
    , status         VARCHAR2(1)
    )
    PARTITION BY RANGE (state, state2)
    ( PARTITION p_northwest VALUES LESS THAN(10, 100) TABLESPACE ts1
    , PARTITION p_southwest VALUES LESS THAN(20,200) TABLESPACE ts2);

    Table created.

But in both cases, the sharding key (not the partitionset key) can be multi-column.

Sharding Key Type Support

The following data types are supported for the sharding key.

- `NUMBER`

- `INTEGER`

- `SMALLINT`

- `RAW`

- `(N)VARCHAR`

- `(N)VARCHAR2`

- `(N)CHAR`

- `DATE`

- `TIMESTAMP`

### Primary Key and Foreign Key Constraints

In a sharding environment, the primary key constraints and foreign key constraints are controlled by the following rules.

- For primary keys, there are unique constraints and unique indexes on sharded tables; the column list must contain the sharding key columns. In earlier Oracle releases the restriction was that the sharding key must be a prefix of such columns, but this rule is now more relaxed.

- Foreign keys from one sharded table to another sharded table also must contain the sharding key. This is automatically enforced because a foreign key refers to either the primary key or unique columns of the referenced table.

- Foreign keys on sharded tables must be within the same table family. This is required because different table families have different sharding key columns.

- Foreign keys in sharded tables referencing local tables are not allowed.

- Foreign keys in sharded tables referencing duplicated tables are not allowed.

- Foreign keys in duplicated table referencing sharded tables are not allowed.

### Indexes on Sharded Tables

Only local indexes can be created on sharded tables. Unique local indexes on sharded tables must contain the sharding key.

Global indexes on sharded tables are not allowed because they can compromise the performance of online chunk movement.

The following example creates a local index named `id1` for the `id` column of the `account` table.

    CREATE INDEX id1 ON account (id) LOCAL;

The following example creates a local unique index named `id2` for the `id` and `state` columns of the `account` table.

    CREATE UNIQUE INDEX id2 ON account (id, state) LOCAL;

### DDL Execution in a Sharded Database

To create a schema in a sharded database, you must issue DDL commands on the shard catalog database, which validates the DDLs and executes them locally before they are executed on the shards.

The shard catalog database contains local copies of all of the objects that exist in the sharded database, and serves as the master copy of the sharded database schema. If the shard catalog validation and execution of DDLs are successful, the DDLs are automatically propagated to all of the shards and applied in the order in which they were issued on the shard catalog.

If a shard is down or not accessible during DDL propagation, the shard catalog keeps track of DDLs that could not be applied to the shard, and then applies them when the shard is back up.

When a new shard is added to a sharded database, all of the DDLs that have been executed in the sharded database are applied in the same order to the shard before it becomes accessible to clients.

There are two ways you can issue DDLs in a sharded database.

- Use the `GDSCTL SQL` command.

  When you issue a DDL with the `GDSCTL SQL` command, as shown in the following example, `GDSCTL` waits until all of the shards have finished executing the DDL and returns the status of the execution.

      GDSCTL> sql “create tablespace set tbsset”

- Connect to the shard catalog database using SQL\*Plus using the `GDS$CATALOG.``sdbname` service.

  When you issue a DDL command on the shard catalog database, it returns the status when it finishes executing locally, but the propagation of the DDL to all of the shards happens in the background asynchronously.

      SQL> create tablespace set tbsset;

**Note:**

Using the SYS account to execute shard DDL is not recommended; create a privileged account for this purpose.

For information about DDL syntax extensions for Oracle Sharding, see DDL Syntax Extensions for Oracle Sharding.

#### Creating Objects Locally and Globally

Objects created using GDSCTL creates global, sharded database objects; however, you can create local or global objects by connecting to the shard catalog with SQL\*Plus.

When a DDL to create an object is issued using the GDSCTL `sql` command, the object is created on all of the shards. A master copy of the object is also created in the shard catalog database. An object that exists on all shards, and the shard catalog database, is called a sharded database object.

When connecting to the shard catalog using SQL\*Plus, two types of objects can be created: sharded database objects and local objects. Local objects are traditional objects that exist only in the shard catalog. Local objects can be used for administrative purposes, or they can be used by multi-shard queries originated from the shard catalog database, to generate and store a report, for example.

Sharded objects cannot have any dependency on local objects. For example, you cannot create an all-shard view on a local table.

The type of object (sharded database or local) that is created in a SQL\*Plus session depends on whether the `SHARD DDL` mode is enabled in the session. This mode is enabled by default on the shard catalog database for the all-shards user, which is a user that exists on all of the shards and the shard catalog database. All of the objects created while `SHARD DDL` is enabled in a session are sharded database objects.

To enable `SHARD DDL` in the session, the all-shards user must run

    ALTER SESSION ENABLE SHARD DDL

All of the objects created while `SHARD DDL` is disabled are local objects. To create a local object, the all-shards user must first run

    ALTER SESSION DISABLE SHARD DDL

See ALTER SESSION for more information about the `SHARD DDL` session parameter.

#### DDL Syntax Extensions for Oracle Sharding

Oracle Sharding includes SQL DDL statements with syntax that can only be run against a sharded database.

Changes to query and DML statements are not required to support Oracle Sharding, and the changes to the DDL statements are very limited. Most existing DDL statements will work the same way on a sharded database, with the same syntax and semantics, as they do on a non-sharded database.

##### CREATE TABLESPACE SET

This statement creates a tablespace set that can be used as a logical storage unit for one or more sharded tables and indexes. A tablespace set consists of multiple Oracle tablespaces distributed across shards in a shardspace.

The `CREATE TABLESPACE SET` statement is intended specifically for Oracle Sharding. Its syntax is similar to `CREATE TABLESPACE`.

    CREATE TABLESPACE SET tablespace_set
           [IN SHARDSPACE shardspace]
                [USING TEMPLATE (
        { MINIMUM EXTENT size_clause
        | BLOCKSIZE integer [ K ]
        | logging_clause
        | FORCE LOGGING
        | ENCRYPTION tablespace_encryption_spec
        | DEFAULT [ table_compression ] storage_clause
        | { ONLINE | OFFLINE }
        | extent_management_clause
        | segment_management_clause
        | flashback_mode_clause
        }...
       )];

Note that in system-managed sharding there is only one default shardspace in the sharded database. The number of tablespaces in a tablespace set is determined automatically and is equal to the number of chunks in the corresponding shardspace.

All tablespaces in a tablespace set are bigfile tablespaces and have the same properties. The properties are specified in the `USING TEMPLATE` clause and they describe the properties of one single tablespace in the tablespace set. This clause is the same as `permanent_tablespace_clause` for a typical tablespace, with the exception that a data file name cannot be specified in the `datafile_tempfile_spec` clause. The data file name for each tablespace in a tablespace set is generated automatically.

Note that a tablespace set can only consist of permanent tablespaces, there is no system, undo, or temporary tablespace set. Also, note that in the example below the total data file size of the tablespace set is 100mxN (where N is the number of tablespaces in the tablespace set).

Example

    CREATE TABLESPACE SET TSP_SET_1 IN SHARDSPACE sgr1
    USING TEMPLATE
    ( DATAFILE SIZE 100m
      EXTEND MANAGEMENT LOCAL
      SEGMENT SPACE MANAGEMENT AUTO
    );

##### ALTER TABLESPACE SET

This statement alters a tablespace set that can be used as a logical storage unit for one or more sharded tables and indexes.

The `SHARDSPACE` property of a tablespace set cannot be modified. All other attributes of a tablespace set can be altered just as for a regular permanent tablespace. Because tablespaces in a tablespace set are bigfile, the `ADD DATAFILE` and `DROP DATAFILE` clauses are not supported.

##### DROP TABLESPACE SET and PURGE TABLESPACE SET

These statements drop or purge a tablespace set, which can be used as a logical storage unit for one or more sharded tables and indexes.

The syntax and semantics for these statements are similar to `DROP` and `PURGE TABLESPACE` statements.

##### CREATE TABLE

The `CREATE TABLE` statement has been extended to create sharded and duplicated tables, and specify a table family.

Syntax

    CREATE [ { GLOBAL TEMPORARY | SHARDED | DUPLICATED} ]
             TABLE [ schema. ] table
          { relational_table | object_table | XMLType_table }
            [ PARENT [ schema. ] table ] ;

The following parts of the `CREATE TABLE` statement are intended to support Oracle Sharding:

- The `SHARDED` and `DUPLICATED` keywords indicate that the table content is either partitioned across shards or duplicated on all shards respectively. The `DUPLICATED` keyword is the only syntax change to create duplicated tables. All other changes described below apply only to sharded tables.

- The `PARENT` clause links a sharded table to the root table of its table family.

- In system and composite sharding, to create a sharded table, `TABLESPACE SET` is used instead of `TABLESPACE`. All clauses that contain `TABLESPACE` are extended to contain `TABLESPACE SET`.

- Three clauses: `consistent_hash_partitions`, `consistent_hash_with_subpartitions`, and `partition_set_clause` in the `table_partitioning_clauses`.

      table_partitioning_clauses ::=
      {range_partitions
      | hash_partitions
      | list_partitions
      | composite_range_partitions
      | composite_hash_partitions
      | composite_list_partitions
      | reference_partitioning
      | system_partitioning
      | consistent_hash_partitions
      | consistent_hash_with_subpartitions
      | partition_set_clause
      }

Example

    CREATE SHARDED TABLE customers
    ( cust_id     NUMBER NOT NULL
    , name        VARCHAR2(50)
    , address     VARCHAR2(250)
    , location_id VARCHAR2(20)
    , class       VARCHAR2(3)
    , signup_date DATE
    ,
    CONSTRAINT cust_pk PRIMARY KEY(cust_id, class)
    )
    PARTITIONSET BY LIST (class)
    PARTITION BY CONSISTENT HASH (cust_id)
    PARTITIONS AUTO
    (PARTITIONSET gold   VALUES (‘gld’) TABLESPACE SET ts2,
     PARTITIONSET silver VALUES (‘slv’) TABLESPACE SET ts1)
    ;

Example of consistent_hash_with_subpartitions

    CREATE SHARDED TABLE Customers
           ( "custi_id" NUMBER NOT NULL
           , name VARCHAR2(50)
           , class VARCHAR2(3) NOT NULL
           , signup_date DATE
           ,
           CONSTRAINT cust_pk PRIMARY KEY("custi_id",name,signup_date,class)
           )
           PARTITIONSET BY LIST (class)
           PARTITION BY CONSISTENT HASH ("custi_id",name)
           SUBPARTITION BY RANGE (signup_date)
           SUBPARTITION TEMPLATE
              ( SUBPARTITION per1 VALUES LESS THAN (TO_DATE('01/01/2000','DD/MM/YYYY'))
              , SUBPARTITION per2 VALUES LESS THAN (TO_DATE('01/01/2010','DD/MM/YYYY'))
              , SUBPARTITION per3 VALUES LESS THAN (TO_DATE('01/01/2020','DD/MM/YYYY'))
              , SUBPARTITION future VALUES LESS THAN (MAXVALUE))
           PARTITIONS AUTO
           (
             PARTITIONSET "gold" VALUES ('Gld','BRZ') TABLESPACE SET ts1 SUBPARTITIONS STORE IN(TBS1,TBS2,TBS3,TBS4)
           , PARTITIONSET "silver" VALUES ('Slv','OTH') TABLESPACE SET ts2 SUBPARTITIONS STORE IN(TBS5,TBS6,TBS7,TBS8)
           ) ;

Limitations

Limitations for sharded tables in the current release:

- There is no default tablespace set for sharded tables.

- A temporary table cannot be sharded or duplicated.

- Index-organized sharded tables are not supported.

- A sharded table cannot contain a nested table column or an identity column.

- A primary key constraint defined on a sharded table must contain the sharding column(s). A foreign key constraint on a column of a sharded table referencing a duplicated table column is not supported.

- System partitioning and interval range partitioning are not supported for sharded tables. Specification of individual hash partitions is not supported for partitioning by consistent hash.

- A column in a sharded table used in `PARTITION BY` or `PARTITIONSET BY` clauses cannot be a virtual column.

Duplicated tables in the current release are not supported with the following:

- System and reference partitioned tables

- LONG, abstract (MDSYS data types are supported), REF data types

- Maximum number of columns without primary key is 999

- The `nologging` and `inmemory` options

- XMLType column in a duplicated table cannot be used in non-ASSM tablespace

See [CREATE TABLE](../sqlrf/CREATE-TABLE.md) for more information about using the clauses supporting Oracle Sharding.

##### ALTER TABLE

The `ALTER TABLE` statement is extended to modify sharded and duplicated tables.

There are limitations on using `ALTER TABLE` with a sharded database.

The following options are not supported for a sharded table in a system-managed or composite sharded database:

- Rename

- Add foreign key constraint

- All operations on individual partitions and subpartitions

- All partition-related operations on the shard, except `TRUNCATE` partition, `UNUSABLE LOCAL INDEXES`, and `REBUILD UNUSABLE LOCAL INDEXES`

The following are not supported for duplicated tables:

- Data types: long, abstract (`MDSYS` datatypes are supported), `REF`

- Column options: vector encode, invisible column, nested tables

- Object types

- Clustered table

- External table

- ILM policy

- `PARENT` clause

- Flashback table operation

- System and Reference partitioning

- Enable `NOLOGGING` option

- Drop duplicated table materialized view log

- Drop duplicated table materialized views on shards

- Alter materialized views (of duplicated tables) on shards

##### ALTER SESSION

The `ALTER SESSION` statement is extended to support sharded databases.

The session-level `SHARD DDL` parameter sets the scope for DDLs issued against the shard catalog database.

    ALTER SESSION { ENABLE | DISABLE } SHARD DDL;

When `SHARD DDL` is enabled, all DDLs issued in the session are executed on the shard catalog and all shards. When `SHARD DDL` is disabled, a DDL is executed only against the shard catalog database. `SHARD DDL` is enabled by default for a sharded database user (the user that exists on all shards and the catalog). To create a sharded database user, the `SHARD DDL` parameter must be enabled before running `CREATE USER`.

### PL/SQL Procedure Execution in a Sharded Database

In the same way that DDL statements can be executed on all shards in a configuration, so too can certain Oracle-provided PL/SQL procedures. These specific procedure calls behave as if they were sharded DDL statements, in that they are propogated to all shards, tracked by the catalog, and run whenever a new shard is added to a configuration.

All of the following procedures can act as if they were a sharded DDL statement.

- Any procedure in the DBMS_FGA package
- Any procedure in the DBMS_RLS package
- The following procudures from the DBMS_STATS package:
  - GATHER_INDEX_STATS
  - GATHER_TABLE_STATS
  - GATHER_SCHEMA_STATS
  - GATHER_DATABASE_STATS
  - GATHER_SYSTEM_STATS
- The following procedures from the DBMS_GOLDENGATE_ADM package:
  - ADD_AUTO_CDR
  - ADD_AUTO_CDR_COLUMN_GROUP
  - ADD_AUTO_CDR_DELTA_RES
  - ALTER_AUTO_CDR
  - ALTER_AUTO_CDR_COLUMN_GROUP
  - PURGE_TOMBSTONES
  - REMOVE_AUTO_CDR
  - REMOVE_AUTO_CDR_COLUMN_GROUP
  - REMOVE_AUTO_CDR_DELTA_RES

To run one of the procedures in the same way as sharded DDL statements, do the following steps.

1.  Connect to the shard catalog database using SQL\*Plus as a database user with the gsm_pooladmin_role.

2.  Enable sharding DDL using `alter session enable shard ddl`.

3.  Run the target procedure using a sharding-specific PL/SQL procedure named `SYS.EXEC_SHARD_PLSQL`.

    This procedure takes a single CLOB argument, which is a character string specifying a fully qualified procedure name and its arguments. Note that running the target procedure without using `EXEC_SHARD_PLSQL` causes the procedure to only be run on the catalog and it is not propogated to all of the shards. Running the procedure without specifying the fully qualified name (for example,` SYS.DBMS_RLS.ADD_POLICY`) will result in an error.

For example, to run `DBMS_RLS.ADD_POLICY` on all shards, do the following from SQL\*Plus after enabling shard DLL.

    exec sys.exec_shard_plsql('sys.dbms_rls.add_policy(object_schema               =>
              ''testuser1'',

              object_name     => ''DEPARTMENTS'',

              policy_name     => ''dept_vpd_pol'',

              function_schema => ''testuser1'',

              policy_function => ''authorized_emps'',

              statement_types => ''INSERT, UPDATE, DELETE, SELECT, INDEX'',

              update_check    => TRUE)'

              ) ;

Take careful note of the need for double single-quotes inside the target procedure call specification, because the call specification itself is a string parameter to `exec_shard_plsql`.

If the target procedure executes correctly on the shard catalog database, it will be queued for processing on all the currently deployed shards. Any error in the target procedure execution on the catalog is returned to the SQL\*Plus session. Errors during execution on the shards can be tracked in the same way they are for DDLs.

### Creating Sharded Database Schema Objects

The following topics show you how to create the schema objects in your sharded database. Refer back to the Sharded Database Schema Objects section in chapter 2 for conceptual information about these objects.

#### Create an All-Shards User

Local users that only exist in the shard catalog database do not have the privileges to create schema objects in the sharded database. The first step of creating the sharded database schema is to create an **all-shards** user.

Create an all-shards user by connecting to the shard catalog database as a privileged user, enabling `SHARD DDL`, and executing the `CREATE USER` command. When the all-shards user connects to the shard catalog database, the `SHARD DDL` mode is enabled by default.

**Note:**

Local users can create non-schema sharded database objects, such as tablespaces, directories, and contexts, if they enable `SHARD DDL` mode; however, they cannot create schema objects, such as tables, views, indexes, functions, procedures, and so on.

Sharded objects cannot have any dependency on local objects. For example, you cannot create an all-shard view on a local table.

You cannot grant `SYS` privileges to sharded users using sharded DDL. You must log in to each shard and grant the privilege to the account manually on that shard.

#### Creating a Sharded Table Family

Create a sharded table family with the `SQL CREATE TABLE` statement. You can specify parent-child relationships between tables using reference partitioning or equi-partitioning.

Use Reference Partitioning to Specify Parent-Child Relationships Between Tables

The recommended way to create a sharded table family is to specify parent-child relationships between tables using reference partitioning.

Partitioning by reference simplifies the syntax since the partitioning scheme is only specified for the root table. Also, partition management operations that are performed on the root table are automatically propagated to its descendents. For example, when adding a partition to the root table, a new partition is created on all its descendents.

The appropriate `CREATE TABLE` statements for Customers–Orders–LineItems schema using a system-managed sharding methodology are shown below. The first statement creates the root table of the table family, Customers.

    CREATE SHARDED TABLE Customers
    ( CustNo      NUMBER NOT NULL
    , Name        VARCHAR2(50)
    , Address     VARCHAR2(250)
    , CONSTRAINT RootPK PRIMARY KEY(CustNo)
    )
    PARTITION BY CONSISTENT HASH (CustNo)
    PARTITIONS AUTO
    TABLESPACE SET ts1
    ;

The following two statements create the Orders and LineItems tables, which are a child and grandchild of the Customers table.

    CREATE SHARDED TABLE Orders
    ( OrderNo   NUMBER NOT NULL
    , CustNo    NUMBER NOT NULL
    , OrderDate DATE
    , CONSTRAINT OrderPK PRIMARY KEY (CustNo, OrderNo)
    , CONSTRAINT CustFK  FOREIGN KEY (CustNo) REFERENCES Customers(CustNo)
    )
    PARTITION BY REFERENCE (CustFK)
    ;

    CREATE SHARDED TABLE LineItems
    ( CustNo    NUMBER NOT NULL
    , LineNo    NUMBER(2) NOT NULL
    , OrderNo   NUMBER(5) NOT NULL
    , StockNo   NUMBER(4)
    , Quantity  NUMBER(2)
    , CONSTRAINT LinePK  PRIMARY KEY (CustNo, OrderNo, LineNo)
    , CONSTRAINT LineFK  FOREIGN KEY (CustNo, OrderNo) REFERENCES Orders(CustNo, OrderNo)
    )
    PARTITION BY REFERENCE (LineFK)
    ;

In the example statements above, corresponding partitions of all tables in the family are stored in the same tablespace set, TS1. However, it is possible to specify separate tablespace sets for each table.

Note that in the example statements above, the partitioning column `CustNo` used as the sharding key is present in all three tables. This is despite the fact that reference partitioning, in general, allows a child table to be equi-partitioned with the parent table without having to duplicate the key columns in the child table. The reason for this is that reference partitioning requires a primary key in a parent table because the primary key must be specified in the foreign key constraint of a child table used to link the child to its parent. However, a primary key on a sharded table must be the same as, or contain, the sharding key. This makes it possible to enforce global uniqueness of a primary key without coordination with other shards, a critical requirement for linear scalability.

To summarize, the use of reference-partitioned tables in a sharded database requires adhering to the following rules:

- A primary key on a sharded table must either be the same as the sharding key, or contain the sharding key. This is required to enforce global uniqueness of a primary key without coordination with other shards.

- Reference partitioning requires a primary key in a parent table, because the primary key must be specified in the foreign key constraint of a child table to link the child to its parent. It is also possible to have a foreign key constraint when the parent table has just `UNIQUE` constraint, but no `PRIMARY KEY`. The sharding key must also be `NOT NULL`.

  For example, to link the LineItems (child) table to the Orders (parent) table, you need a primary key in the Orders table. The second rule implies that the primary key in the Orders table contains the `CustNo` value. (This is an existing partitioning rule not specific to Oracle Sharding.)

Use Equi-Partitioning to Specify Parent-Child Relationships Between Tables

In some cases it is impossible or undesirable to create primary and foreign key constraints that are required for reference partitioning. For such cases, specifying parent-child relationships in a table family requires that all tables are explicitly equi-partitioned. Each child table is created with the `PARENT` clause in `CREATE SHARDED TABLE` that contains the name of its parent. An example of the syntax is shown below.

     CREATE SHARDED TABLE Customers
    ( CustNo      NUMBER NOT NULL
    , Name        VARCHAR2(50)
    , Address     VARCHAR2(250)
    , region      VARCHAR2(20)
    , class       VARCHAR2(3)
    , signup      DATE
    )
    PARTITION BY CONSISTENT HASH (CustNo)
    PARTITIONS AUTO
    TABLESPACE SET ts1
    ;

    CREATE SHARDED TABLE Orders
    ( OrderNo   NUMBER
    , CustNo    NUMBER NOT NULL
    , OrderDate DATE
    )
    PARENT Customers
    PARTITION BY CONSISTENT HASH (CustNo)
    PARTITIONS AUTO
    TABLESPACE SET ts1
    ;

    CREATE SHARDED TABLE LineItems
    ( LineNo    NUMBER
    , OrderNo   NUMBER
    , CustNo    NUMBER NOT NULL
    , StockNo   NUMBER
    , Quantity  NUMBER
    )
    PARENT Customers
    PARTITION BY CONSISTENT HASH (CustNo)
    PARTITIONS AUTO
    TABLESPACE SET ts1
    ;

Because the partitioning scheme is fully specified in all of the `CREATE SHARDED TABLE` statements, any table can be independently subpartitioned. This is not permitted with reference partitioning where subpartitions can only be specified for the root table and the subpartitioning scheme is the same for all tables in a table family.

Note that this method only supports two-level table families, that is, all children must have the same parent and grandchildren cannot exist. This is not a limitation as long as the partitioning column from the parent table exists in all of the child tables.

**See Also:**

[Oracle Database VLDB and Partitioning Guide](../vldbg/partition-concepts.md) for information about reference partitioning

#### Creating Sharded Tables

A sharded table is a table that is partitioned into smaller and more manageable pieces among multiple databases, called shards.

Tablespace Set Sizing

In the system-managed and composite sharding methods, when you create a tablespace set on the shard catalog, you must make sure you have enough space for all of the tablespaces created on the shard catalog and on each of the shards. This is especially important in a metered usage environment.

For example, with a shard catalog and three shards in the configuration, you issue the following statements.

    ALTER SESSION ENABLE SHARD DDL;
    CREATE TABLESPACE SET TSP_SET_1 IN SHARDSPACE SHSPC_1 USING TEMPLATE
     (DATAFILE SIZE 100M  AUTOEXTEND ON NEXT 1M MAXSIZE UNLIMITED);

Assuming a default of 120 chunks per shard, the command creates 360 tablespaces of an initial tables space 100M each on the shard catalog and on each shard. While that doesn't sound like a lot of storage, when the database administrator allots 100G initially, they are not expecting 3.6TB per shard. If that amount of storage is not planned for, this may lead to a failed DDL, and will require significant effort to recover from.

Creating Sharded Tables in a System-Managed Sharded Database

In a system-managed sharded database, data is automatically distributed across the shards using partitioning by consistent hash.

Before creating a sharded table, create a tablespace set with `CREATE TABLESPACE SET` to store the table partitions.

    CREATE TABLESPACE SET ts1;

If you need to customize the tablespace attributes, add the `USING TEMPLATE` clause to `CREATE TABLESPACE SET` as shown in this example.

    CREATE TABLESPACE SET ts1
    USING TEMPLATE
    ( DATAFILE SIZE 10M
      EXTENT MANAGEMENT LOCAL UNIFORM SIZE 256K
      SEGMENT SPACE MANAGEMENT AUTO
      ONLINE
    )
    ;

You create a sharded table with `CREATE SHARDED TABLE`, horizontally partitioning the table across the shards based on the sharding key `cust_id`.

    CREATE SHARDED TABLE customers
    ( cust_id     NUMBER NOT NULL
    , name        VARCHAR2(50)
    , address     VARCHAR2(250)
    , region      VARCHAR2(20)
    , class       VARCHAR2(3)
    , signup      DATE
    CONSTRAINT cust_pk PRIMARY KEY(cust_id)
    )
    PARTITION BY CONSISTENT HASH (cust_id)
    PARTITIONS AUTO
    TABLESPACE SET ts1
    ;

A system-managed sharded table is partitioned by consistent hash, by specifying `PARTITION BY CONSISTENT HASH (``primary_key_column``)`.

The `PARTITIONS AUTO` clause specifies that the number of partitions is automatically set to the number of tablespaces in the tablespace set `ts1`, and each partition is stored in a separate tablespace.

Creating Sharded Tables in a User-Defined Sharded Database

In a user-defined sharded database, you explicitly map data to individual shards. A sharded table in a user-defined sharded database can be partitioned by range or list.

You do not create tablespace sets for user-defined sharded tables; however, you must create each tablespace individually and explicitly associate it with a shardspace deployed in the sharded database configuration, as shown here.

    CREATE TABLESPACE tbs1 IN SHARDSPACE west;
    CREATE TABLESPACE tbs2 IN SHARDSPACE west;

    CREATE TABLESPACE tbs3 IN SHARDSPACE central;
    CREATE TABLESPACE tbs4 IN SHARDSPACE central;

    CREATE TABLESPACE tbs5 IN SHARDSPACE east;
    CREATE TABLESPACE tbs6 IN SHARDSPACE east;

When you create the sharded table, you define the partitions with the ranges or lists of data to be stored in each tablespace, as shown in the following example.

    CREATE SHARDED TABLE accounts
    ( id             NUMBER
    , account_number NUMBER
    , customer_id    NUMBER
    , branch_id      NUMBER
    , state          VARCHAR(2) NOT NULL
    , status         VARCHAR2(1)
    )
    PARTITION BY LIST (state)
    ( PARTITION p_northwest VALUES ('OR', 'WA') TABLESPACE ts1
    , PARTITION p_southwest VALUES ('AZ', 'UT', 'NM') TABLESPACE ts2
    , PARTITION p_northcentral VALUES ('SD', 'WI') TABLESPACE ts3
    , PARTITION p_southcentral VALUES ('OK', 'TX') TABLESPACE ts4
    , PARTITION p_northeast VALUES ('NY', 'VM', 'NJ') TABLESPACE ts5
    , PARTITION p_southeast VALUES ('FL', 'GA') TABLESPACE ts6
    )
    ;

Creating Sharded Tables in a Composite Sharded Database

The sharded database using the composite sharding method allows you to partition subsets of data that correspond to a range or list of key values in a table partitioned by consistent hash.

With composite sharding, as with the other sharding methods, tablespaces are used to specify the mapping of partitions to shards. To partition subsets of data in a sharded table, a separate tablespace set must be created for each shardspace deployed in the sharded database configuration as shown in the following example.

    CREATE TABLESPACE SET tbs1 IN SHARDSPACE shspace1;
    CREATE TABLESPACE SET tbs2 IN SHARDSPACE shspace2;

The statement in the following example partitions a sharded table into two partition sets: gold and silver, based on class of service. Each partition set is stored in a separate tablespace. Then data in each partition set is further partitioned by consistent hash on customer ID.

    CREATE SHARDED TABLE customers
    ( cust_id NUMBER NOT NULL
    , name VARCHAR2(50)
    , address VARCHAR2(250)
    , location_id VARCHAR2(20)
    , class VARCHAR2(3)
    , signup_date DATE
    , CONSTRAINT cust_pk PRIMARY KEY(cust_id, class)
    )
    PARTITIONSET BY LIST (class)
      PARTITION BY CONSISTENT HASH (cust_id)
      PARTITIONS AUTO
    (PARTITIONSET gold VALUES (‘gld’) TABLESPACE SET tbs1,
     PARTITIONSET silver VALUES (‘slv’) TABLESPACE SET tbs2)
    ;

#### Creating Duplicated Tables

The number of database requests handled by a single shard can be maximized by duplicating read-only or read-mostly tables across all shards. This strategy is a good choice for relatively small tables that are not updated frequently, and that are often accessed together with sharded tables.

There are some limitations on duplicated tables. The following are not supported for duplicated tables.

- `NOLOGGING`
- `ALTER TABLE ADD/DROP CONSTRAINT` for primary key only
- ` ALTER TABLE ADD/DROP PRIMARY KEY`
- `ALTER TABLE RENAME COLUMN`
- `PARTITION BY REFERENCE`
- `PARTITION BY SYSTEM`
- `CLUSTERED TABLE`
- Non-final `UDT` or `NESTED TABLE`
- `LONG DATATYPE`
- `COLUMN VECTOR ENCODE`
- `INVISIBLE COLUMN`
- Column encryption
- Information Lifecycle Management (ILM) policy
- CTAS Parallel
- Foreign key constraints between duplicated tables and sharded tables are generally not allowed with the exception that in user-defined sharding, you can create `DISABLE NOVALIDATE` foreign key constraints between sharded and duplicated tables.
- Creation of duplicated tables with `inmemory` option is not supported; however, altering a duplicated table to be `inmemory` is supported.

The Products duplicated table can be created using the following statement.

    CREATE DUPLICATED TABLE Products
    ( StockNo     NUMBER PRIMARY KEY
    , Description VARCHAR2(20)
    , Price       NUMBER(6,2))
    ;

#### Updating Duplicated Tables and Synchronizing Their Contents

Oracle Sharding synchronizes the contents of duplicated tables using Materialized View Replication.

A duplicated table on each shard is represented by a materialized view. The master table for the materialized views is located in the shard catalog. The `CREATE DUPLICATED TABLE` statement automatically creates the master table, materialized views, and other objects required for materialized view replication.

You can connect to any shard and update a duplicated table directly on the shard. The update is first propagated over a database link from the shard to the master table on the shard catalog. Then the update is asynchronously propagated to all other shards as a result of a materialized view refresh.

The materialized views on all of the shards can be refreshed with one of the two options:

- Automatic refresh at a configurable frequency per table
- On-demand refresh by running a stored procedure

For automatic refresh, to get better refresh performance, you can also use a stored procedure interface to create materialized view refresh groups.

**Note:**

A race condition is possible when a transaction run on a shard tries to update a row which was deleted on the shard catalog. In this case, an error is returned and the transaction on the shard is rolled back.

The following use cases are not supported when updating duplicated tables on a shard.

- Updating a LOB or a data type not supported by database links
- Updating or deleting of a row inserted by the same transaction

### Schema Creation Examples

The following examples show the steps you would take to create a schema for a sharded database using the system-managed, user-defined, and composite sharding methods.

#### Create a System-Managed Sharded Database Schema

Create the tablespace set, sharded tables, and duplicated tables for a sharded database that uses the system-managed sharding method.

1.  Connect to the shard catalog database, create the application schema user, and grant privileges and roles to the user.
    In this example, the application schema user is called app_schema.

        $ sqlplus / as sysdba

        SQL> alter session enable shard ddl;
        SQL> create user app_schema identified by app_schema_password;
        SQL> grant all privileges to app_schema;
        SQL> grant gsmadmin_role to app_schema;
        SQL> grant select_catalog_role to app_schema;
        SQL> grant connect, resource to app_schema;
        SQL> grant dba to app_schema;
        SQL> grant execute on dbms_crypto to app_schema;
2.  Create a tablespace set for the sharded tables.
        SQL> CREATE TABLESPACE SET TSP_SET_1 using template
         (datafile size 100m autoextend on next 10M maxsize unlimited
          extent management local segment space management auto);
3.  If you use LOBs in a column, you can specify a tablespace set for the LOBs.
        SQL> CREATE TABLESPACE SET LOBTS1;

    **Note:**

    Tablespace sets for LOBS cannot be specified at the subpartitition level in system-managed sharding.
4.  Create a tablespace for the duplicated tables.
    In this example the duplicated table is the Products table in the sample Customers-Orders-Products schema.

        SQL> CREATE TABLESPACE products_tsp datafile size 100m
         autoextend on next 10M maxsize unlimited
         extent management local uniform size 1m;
5.  Create a sharded table for the root table.
    In this example, the root table is the Customers table in the sample Customers-Orders-Products schema.

        SQL> CONNECT app_schema/app_schema_password
        SQL> CREATE SHARDED TABLE Customers
          (
            CustId      VARCHAR2(60) NOT NULL,
            FirstName   VARCHAR2(60),
            LastName    VARCHAR2(60),
            Class       VARCHAR2(10),
            Geo         VARCHAR2(8),
            CustProfile VARCHAR2(4000),
            Passwd      RAW(60),
            CONSTRAINT pk_customers PRIMARY KEY (CustId),
            CONSTRAINT json_customers CHECK (CustProfile IS JSON)
          ) TABLESPACE SET TSP_SET_1
          PARTITION BY CONSISTENT HASH (CustId) PARTITIONS AUTO;

    **Note:**

    If any columns contain LOBs, you can include the tablespace set in the parent table creation statement, as shown here.

        SQL> CREATE SHARDED TABLE Customers
          (
            CustId      VARCHAR2(60) NOT NULL,
            FirstName   VARCHAR2(60),
            LastName    VARCHAR2(60),
            Class       VARCHAR2(10),
            Geo         VARCHAR2(8),
            CustProfile VARCHAR2(4000),
            Passwd      RAW(60),
            image       BLOB,
            CONSTRAINT pk_customers PRIMARY KEY (CustId),
            CONSTRAINT json_customers CHECK (CustProfile IS JSON)
          ) TABLESPACE SET TSP_SET_1
            LOB(image) store as (TABLESPACE SET LOBTS1)
          PARTITION BY CONSISTENT HASH (CustId) PARTITIONS AUTO;
6.  Create a sharded table for the other tables in the table family.
    In this example, sharded tables are created for the Orders and LineItems tables in the sample Customers-Orders-Products schema.

    The Orders sharded table is created first:

        SQL> CREATE SHARDED TABLE Orders
          (
            OrderId     INTEGER NOT NULL,
            CustId      VARCHAR2(60) NOT NULL,
            OrderDate   TIMESTAMP NOT NULL,
            SumTotal    NUMBER(19,4),
            Status      CHAR(4),
            CONSTRAINT  pk_orders PRIMARY KEY (CustId, OrderId),
            CONSTRAINT  fk_orders_parent FOREIGN KEY (CustId)
            REFERENCES Customers ON DELETE CASCADE
          ) PARTITION BY REFERENCE (fk_orders_parent);

    Create the sequence used for the OrderId column.

        SQL> CREATE SEQUENCE Orders_Seq;

    Create a sharded table for LineItems

        SQL> CREATE SHARDED TABLE LineItems
          (
            OrderId     INTEGER NOT NULL,
            CustId      VARCHAR2(60) NOT NULL,
            ProductId   INTEGER NOT NULL,
            Price       NUMBER(19,4),
            Qty         NUMBER,
            CONSTRAINT  pk_items PRIMARY KEY (CustId, OrderId, ProductId),
            CONSTRAINT  fk_items_parent FOREIGN KEY (CustId, OrderId)
            REFERENCES Orders ON DELETE CASCADE
          ) PARTITION BY REFERENCE (fk_items_parent);
7.  Create any required duplicated tables.
    In this example, the Products table is a duplicated object.

        SQL> CREATE DUPLICATED TABLE Products
          (
            ProductId  INTEGER GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
            Name       VARCHAR2(128),
            DescrUri   VARCHAR2(128),
            LastPrice  NUMBER(19,4)
          ) TABLESPACE products_tsp;

Next you should monitor the DDL execution and verify that the tablespace sets, tables, and chunks were correctly created on all of the shards.

#### Create a User-Defined Sharded Database Schema

Create the schema user, tablespace set, sharded tables, and duplicated tables for a sharded database that uses the user-defined sharding method.

1.  Connect to the shard catalog database, create the application schema user, and grant privileges and roles to the user.
    In this example, the application schema user is called app_schema.

        $ sqlplus / as sysdba

        SQL> alter session enable shard ddl;
        SQL> create user app_schema identified by app_schema_password;
        SQL> grant all privileges to app_schema;
        SQL> grant gsmadmin_role to app_schema;
        SQL> grant select_catalog_role to app_schema;
        SQL> grant connect, resource to app_schema;
        SQL> grant dba to app_schema;
        SQL> grant execute on dbms_crypto to app_schema;
2.  Create tablespaces for the sharded tables.
        SQL> CREATE TABLESPACE ck1_tsp DATAFILE SIZE 100M autoextend on next 10M maxsize
        unlimited extent management local segment space management auto in
         shardspace shspace1;

        SQL> CREATE TABLESPACE ck2_tsp DATAFILE SIZE 100M autoextend on next 10M maxsize
        unlimited extent management local segment space management auto in
         shardspace shspace2;
3.  If you use LOBs in any columns, you can specify tablespaces for the LOBs.
        SQL> CREATE TABLESPACE lobts1 ... in shardspace shspace1;

        SQL> CREATE TABLESPACE lobts2 ... in shardspace shspace2;
4.  Create a tablespace for the duplicated tables.
    In this example the duplicated table is the Products table in the sample Customers-Orders-Products schema.

        SQL> CREATE TABLESPACE products_tsp datafile size 100m autoextend
         on next 10M maxsize unlimited extent management local uniform size 1m;
5.  Create a sharded table for the root table.
    In this example, the root table is the Customers table in the sample Customers-Orders-Products schema.

        SQL> CONNECT app_schema/app_schema_password

        SQL> ALTER SESSION ENABLE SHARD DDL;

        SQL> CREATE SHARDED TABLE Customers
          (
            CustId      VARCHAR2(60) NOT NULL,
            CustProfile VARCHAR2(4000),
            Passwd      RAW(60),
            CONSTRAINT pk_customers PRIMARY KEY (CustId),
            CONSTRAINT json_customers CHECK (CustProfile IS JSON)
          ) PARTITION BY RANGE (CustId)
          ( PARTITION ck1 values less than ('m') tablespace ck1_tsp,
            PARTITION ck2 values less than (MAXVALUE) tablespace ck2_tsp
          );

    **Note:**

    If any columns in the sharded tables contain LOBs, the CREATE SHARDED TABLE statement can include the LOB tablespaces, as shown here.

        SQL> CREATE SHARDED TABLE Customers
          (
            CustId      VARCHAR2(60) NOT NULL,
            CustProfile VARCHAR2(4000),
            Passwd      RAW(60),
            image       BLOB,
            CONSTRAINT pk_customers PRIMARY KEY (CustId),
            CONSTRAINT json_customers CHECK (CustProfile IS JSON)
          ) PARTITION BY RANGE (CustId)
          ( PARTITION ck1 values less than ('m') tablespace ck1_tsp
             lob(image) store as (tablespace lobts1),
            PARTITION ck2 values less than (MAXVALUE) tablespace ck2_tsp
             lob(image) store as (tablespace lobts2)
          );
6.  Create a sharded table for the other tables in the table family.
    In this example, sharded tables are created for the Orders and LineItems tables in the sample Customers-Orders-Products schema.

    The Orders sharded table is created first:

        SQL> CREATE SHARDED TABLE Orders
          (
            OrderId     INTEGER NOT NULL,
            CustId      VARCHAR2(60) NOT NULL,
            OrderDate   TIMESTAMP NOT NULL,
            SumTotal    NUMBER(19,4),
            Status      CHAR(4),
            CONSTRAINT  pk_orders PRIMARY KEY (CustId, OrderId),
            CONSTRAINT  fk_orders_parent FOREIGN KEY (CustId)
            REFERENCES Customers ON DELETE CASCADE
          ) PARTITION BY REFERENCE (fk_orders_parent);

    Create the sequence used for the OrderId column.

        SQL> CREATE SEQUENCE Orders_Seq;

    Create a sharded table for LineItems

        SQL> CREATE SHARDED TABLE LineItems
          (
            OrderId     INTEGER NOT NULL,
            CustId      VARCHAR2(60) NOT NULL,
            ProductId   INTEGER NOT NULL,
            Price       NUMBER(19,4),
            Qty         NUMBER,
            CONSTRAINT  pk_items PRIMARY KEY (CustId, OrderId, ProductId),
            CONSTRAINT  fk_items_parent FOREIGN KEY (CustId, OrderId)
            REFERENCES Orders ON DELETE CASCADE
          ) PARTITION BY REFERENCE (fk_items_parent);
7.  Create any required duplicated tables.
    In this example, the Products table is a duplicated object.

        SQL> CREATE DUPLICATED TABLE Products
          (
            ProductId  INTEGER GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
            Name       VARCHAR2(128),
            DescrUri   VARCHAR2(128),
            LastPrice  NUMBER(19,4)
          ) TABLESPACE products_tsp;

Next you should monitor the DDL execution and verify that the tablespace sets, tables, and chunks were correctly created on all of the shards.

#### Create a Composite Sharded Database Schema

Create the schema user, tablespace set, sharded tables, and duplicated tables for a sharded database that uses the composite sharding method.

1.  Connect to the shard catalog host, and set the ORACLE_SID to the shard catalog name.
2.  Connect to the shard catalog database, create the application schema user, and grant privileges and roles to the user.
    In this example, the application schema user is called app_schema.

        $ sqlplus / as sysdba

        SQL> connect / as sysdba
        SQL> alter session enable shard ddl;
        SQL> create user app_schema identified by app_schema_password;
        SQL> grant connect, resource, alter session to app_schema;
        SQL> grant execute on dbms_crypto to app_schema;
        SQL> grant create table, create procedure, create tablespace,
         create materialized view to app_schema;
        SQL> grant unlimited tablespace to app_schema;
        SQL> grant select_catalog_role to app_schema;
        SQL> grant all privileges to app_schema;
        SQL> grant gsmadmin_role to app_schema;
        SQL> grant dba to app_schema;
3.  Create tablespace sets for the sharded tables.
        SQL> CREATE TABLESPACE SET
          TSP_SET_1 in shardspace cust_america using template
          (datafile size 100m autoextend on next 10M maxsize
           unlimited extent management
           local segment space management auto );

        SQL> CREATE TABLESPACE SET
          TSP_SET_2 in shardspace cust_europe using template
          (datafile size 100m autoextend on next 10M maxsize
           unlimited extent management
           local segment space management auto );
4.  If you use LOBs in any columns, you can specify tablespace sets for the LOBs.
        SQL> CREATE TABLESPACE SET LOBTS1 in shardspace cust_america ... ;

        SQL> CREATE TABLESPACE SET LOBTS2 in shardspace cust_europe ... ;

    **Note:**

    Tablespace sets for LOBs cannot be specified at the subpartitition level in composite sharding.
5.  Create a tablespace for the duplicated tables.
    In this example the duplicated table is the Products table in the sample Customers-Orders-Products schema.

        CREATE TABLESPACE products_tsp datafile size 100m autoextend on next 10M
         maxsize unlimited extent management local uniform size 1m;
6.  Create a sharded table for the root table.
    In this example, the root table is the Customers table in the sample Customers-Orders-Products schema.

        connect app_schema/app_schema_password
        alter session enable shard ddl;

        CREATE SHARDED TABLE Customers
        (
          CustId      VARCHAR2(60) NOT NULL,
          FirstName   VARCHAR2(60),
          LastName    VARCHAR2(60),
          Class       VARCHAR2(10),
          Geo         VARCHAR2(8),
          CustProfile VARCHAR2(4000),
          Passwd      RAW(60),
          CONSTRAINT pk_customers PRIMARY KEY (CustId),
          CONSTRAINT json_customers CHECK (CustProfile IS JSON)
        ) partitionset by list(GEO)
        partition by consistent hash(CustId)
        partitions auto
        (partitionset america values ('AMERICA') tablespace set tsp_set_1,
        partitionset europe values ('EUROPE') tablespace set tsp_set_2
        );

    **Note:**

    If any columns in the sharded tables contain LOBs, the CREATE SHARDED TABLE statement can include the LOB tablespace set, as shown here.

        CREATE SHARDED TABLE Customers
        (
          CustId      VARCHAR2(60)  NOT NULL,
          FirstName   VARCHAR2(60),
          LastName    VARCHAR2(60),
          Class       VARCHAR2(10),
          Geo         VARCHAR2(8)   NOT NULL,
          CustProfile VARCHAR2(4000),
          Passwd      RAW(60),
          image       BLOB,
          CONSTRAINT pk_customers PRIMARY KEY (CustId),
          CONSTRAINT json_customers CHECK (CustProfile IS JSON)
        ) partitionset by list(GEO)
        partition by consistent hash(CustId)
        partitions auto
        (partitionset america values ('AMERICA') tablespace set tsp_set_1
         lob(image) store as (tablespace set lobts1),
        partitionset europe values ('EUROPE') tablespace set tsp_set_2
         lob(image) store as (tablespace set lobts2));
7.  Create a sharded table for the other tables in the table family.
    In this example, sharded tables are created for the Orders and LineItems tables in the sample Customers-Orders-Products schema.

    Create the sequence used for the OrderId column.

        CREATE SEQUENCE Orders_Seq;

    The Orders sharded table is created first:

        CREATE SHARDED TABLE Orders
        (
          OrderId     INTEGER NOT NULL,
          CustId      VARCHAR2(60) NOT NULL,
          OrderDate   TIMESTAMP NOT NULL,
          SumTotal    NUMBER(19,4),
          Status      CHAR(4),
          constraint  pk_orders primary key (CustId, OrderId),
          constraint  fk_orders_parent foreign key (CustId)
            references Customers on delete cascade
        ) partition by reference (fk_orders_parent);

    Create a sharded table for LineItems

        CREATE SHARDED TABLE LineItems
        (
          OrderId     INTEGER NOT NULL,
          CustId      VARCHAR2(60) NOT NULL,
          ProductId   INTEGER NOT NULL,
          Price       NUMBER(19,4),
          Qty         NUMBER,
          constraint  pk_items primary key (CustId, OrderId, ProductId),
          constraint  fk_items_parent foreign key (CustId, OrderId)
            references Orders on delete cascade
        ) partition by reference (fk_items_parent);
8.  Create any required duplicated tables.
    In this example, the Products table is a duplicated object.

        CREATE DUPLICATED TABLE Products
        (
          ProductId  INTEGER GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
          Name       VARCHAR2(128),
          DescrUri   VARCHAR2(128),
          LastPrice  NUMBER(19,4)
        ) tablespace products_tsp;

Next you should monitor the DDL execution and verify that the tablespace sets, tables, and chunks were correctly created on all of the shards.

### Monitor DDL Execution and Verify Object Creation

You can monitor DDL execution using GDSCTL and SQL, to verify that the DDLs are propagated to all of the shards.

Monitor DDL Execution

You can check the status of the DDL propagation to the shards by using the GDSCTL `show ddl` and `config shard` commands.

This check is mandatory when a DDL is executed using SQL\*Plus on the shard catalog, because SQL\*Plus does not return the execution status on all of the shards.

The `show ddl` command output might be truncated. You can run `SELECT ddl_text FROM gsmadmin_internal.ddl_requests` on the shard catalog to see the full text of the statements.

Run the following command from the shard director host.

    GDSCTL> show ddl
    id    DDL Text                                  Failed shards
    --    --------                                  -------------
    5     grant connect, resource to app_schema
    6     grant dba to app_schema
    7     grant execute on dbms_crypto to app_s...
    8     CREATE TABLESPACE SET  TSP_SET_1 usin...
    9     CREATE TABLESPACE products_tsp datafi...
    10    CREATE SHARDED TABLE Customers (   Cu...
    11    CREATE SHARDED TABLE Orders (   Order...
    12    CREATE SEQUENCE Orders_Seq;
    13    CREATE SHARDED TABLE LineItems (   Or...
    14    CREATE MATERIALIZED VIEW "APP_SCHEMA"...

Run the `config shard` command on each shard in your configuration, as shown here, and note the Last Failed DDL line in the command output.

    GDSCTL> config shard -shard sh1
    Name: sh1
    Shard Group: primary_shardgroup
    Status: Ok
    State: Deployed
    Region: region1
    Connection string: shard_host_1:1521/sh1_host:dedicated
    SCAN address:
    ONS remote port: 0
    Disk Threshold, ms: 20
    CPU Threshold, %: 75
    Version: 18.0.0.0
    Last Failed DDL:
    DDL Error: ---
    Failed DDL id:
    Availability: ONLINE

    Supported services
    ------------------------
    Name                                          Preferred Status
    ----                                          --------- ------
    oltp_ro_srvc                                  Yes       Enabled
    oltp_rw_srvc                                  Yes       Enabled

Verify Tablespace Set Creation

Verify that the tablespaces of the tablespace set you created for the sharded table family, and the tablespaces you created for the duplicated tables, are created on all of the shards.

The number of tablespaces in the tablespace set, shown below as C001TSP_SET_1 through C006TSP_SET_1, is based on the number of chunks specified in the GDSCTL `create shardcatalog` command when the sharded database configuration was deployed.

The duplicated Products tablespace is shown below as PRODUCTS_TSP.

Run `SELECT TABLESPACE_NAME` on all of the shards in your configuration, as shown here.

    $ sqlplus / as sysdba

    SQL> select TABLESPACE_NAME, BYTES/1024/1024 MB from sys.dba_data_files
     order by tablespace_name;

    TABLESPACE_NAME             MB
    ----------------------- ----------
    C001TSP_SET_1           100
    C002TSP_SET_1           100
    C003TSP_SET_1                 100
    C004TSP_SET_1                 100
    C005TSP_SET_1                 100
    C006TSP_SET_1                 100
    PRODUCTS_TSP            100
    SYSAUX                  650
    SYSTEM                  890
    SYS_SHARD_TS                  100
    TSP_SET_1                     100

    TABLESPACE_NAME              MB
    ------------------------ ----------
    UNDOTBS1                       105
    USERS                                5

    13 rows selected.

Verify Chunk Creation and Distribution

Verify that the chunks and chunk tablespaces were created on all of the shards.

Run the GDSCTL `config chunks` command as shown here, and note the ranges of chunk IDs on each shard.

    GDSCTL> config chunks
    Chunks
    ------------------------
    Database                      From      To
    --------                      ----      --
    sh1                           1         6
    sh2                           1         6
    sh3                           7         12
    sh4                           7         12

Run the following SQL statements on each of the shards in your configuration, as shown here.

    SQL> show parameter db_unique_name

    NAME             TYPE        VALUE
    ---------------- ----------- ------------------------------
    db_unique_name   string      sh1

    SQL> select table_name, partition_name, tablespace_name
     from dba_tab_partitions
     where tablespace_name like 'C%TSP_SET_1'
     order by tablespace_name;

    TABLE_NAME       PARTITION_NAME   TABLESPACE_NAME
    ---------------- ---------------- --------------------
    ORDERS           CUSTOMERS_P1     C001TSP_SET_1
    CUSTOMERS        CUSTOMERS_P1     C001TSP_SET_1
    LINEITEMS        CUSTOMERS_P1     C001TSP_SET_1
    CUSTOMERS        CUSTOMERS_P2     C002TSP_SET_1
    LINEITEMS        CUSTOMERS_P2     C002TSP_SET_1
    ORDERS           CUSTOMERS_P2     C002TSP_SET_1
    CUSTOMERS        CUSTOMERS_P3     C003TSP_SET_1
    ORDERS           CUSTOMERS_P3     C003TSP_SET_1
    LINEITEMS        CUSTOMERS_P3     C003TSP_SET_1
    ORDERS           CUSTOMERS_P4     C004TSP_SET_1
    CUSTOMERS        CUSTOMERS_P4     C004TSP_SET_1

    TABLE_NAME       PARTITION_NAME   TABLESPACE_NAME
    ---------------- ---------------- --------------------
    LINEITEMS        CUSTOMERS_P4     C004TSP_SET_1
    CUSTOMERS        CUSTOMERS_P5     C005TSP_SET_1
    LINEITEMS        CUSTOMERS_P5     C005TSP_SET_1
    ORDERS           CUSTOMERS_P5     C005TSP_SET_1
    CUSTOMERS        CUSTOMERS_P6     C006TSP_SET_1
    LINEITEMS        CUSTOMERS_P6     C006TSP_SET_1
    ORDERS           CUSTOMERS_P6     C006TSP_SET_1
    18 rows selected.

Connect to the shard catalog database and verify that the chunks are uniformly distributed, as shown here.

    $ sqlplus / as sysdba

    SQL> SELECT a.name Shard, COUNT(b.chunk_number) Number_of_Chunks
      FROM gsmadmin_internal.database a, gsmadmin_internal.chunk_loc b
      WHERE a.database_num=b.database_num
      GROUP BY a.name
      ORDER BY a.name;

    SHARD                  NUMBER_OF_CHUNKS
    ------------------------------ ----------------
    sh1                        6
    sh2                       6
    sh3                       6
    sh4                       6

Verify Table Creation

To verify that the sharded and duplicated tables were created, log in as the application schema user on the shard catalog database and each of the shards and query the tables on a database shard, as shown below with the example app_schema user.

    $ sqlplus app_schema/app_schema_password
    Connected.

    SQL> select table_name from user_tables;

    TABLE_NAME
    -----------------------------------------------------------------------
    CUSTOMERS
    ORDERS
    LINEITEMS
    PRODUCTS

    4 rows selected.

### DDL Execution Failure and Recovery Examples

The following examples demonstrate the steps to issue a DDL, monitor its execution status, and what to do when errors are encountered.

When a DDL fails on a shard, all further DDLs on that shard are blocked until the failure is resolved and the GDSCTL `recover shard` command is run.

Note that you must have GSM_ADMIN privileges to run these GDSCTL commands.

The following examples demonstrate the case when a DDL is issued using SQL\*Plus, but the same status checking and corrective actions apply when using the `GDSCTL SQL` command.

Example 6-1 A DDL execution error on the shard catalog

In this example the user makes a typo in the `CREATE USER` command.

    SQL> alter session enable shard ddl;
    Session altered.

    SQL> CREATE USER example_user IDENTRIFIED BY out_standing1;
    CREATE USER example_user IDENTRIFIED BY out_Standing1
                       *
    ERROR at line 1:
    ORA-00922: missing or invalid option

The DDL fails to execute on the shard catalog and, as expected, the GDSCTL `show ddl` command shows that no DDL was executed on any of the shards:

    GDSCTL> show ddl
    id      DDL Text                         Failed shards
    --      --------                         -------------

Then the user repeats the command with the correct spelling. Note that there is no need to run `alter session enable shard ddl`again because the same session is used.

    SQL> CREATE USER example_user IDENTIFIED BY out_Standing1;
    User created.

Now `show ddl` shows that the DDL has been successfully executed on the shard catalog database and it did not fail on any shards that are online.

    GDSCTL> show ddl
    id      DDL Text                                     Failed shards
    --      --------                                     -------------
    1       create user example_user identified by *****

**Note:**

For any shard that is down at the time of the DDL execution, the DDL is automatically applied when the shard is back up.

Example 6-2 Recovery from an error on a shard by executing a corrective action on that shard

In this example, the user attempts to create a tablespace set for system-managed sharded tables. But the datafile directory on one of the shards is not writable, so the DDL is successfully executed on the catalog, but fails on the shard.

    SQL> connect example_user/out_Standing1
    Connected

    SQL> create tablespace set tbsset;
    Tablespace created.

Note that there is no need to run `alter session enable shard ddl` because the user example_user was created as the SDB user and shard ddl is enabled by default.

Check status using GDSCTL `show ddl`:

    GDSCTL> show ddl
    id      DDL Text                                      Failed shards
    --      --------                                      -------------
    1       create user example_user identified by *****
    2       create tablespace set tbsset                  shard01

The command output shows that the DDL failed on the shard shard01. Run the GDSCTL `config shard` command to get detailed information:

    GDSCTL> config shard -shard shard01

    Conversion = ':'Name: shard01
    Shard Group: dbs1
    Status: Ok
    State: Deployed
    Region: east
    Connection string: (DESCRIPTION=(ADDRESS=(HOST=shard01-host)(PORT=1521)(PROTOCOL=tcp))
    (CONNECT_DATA=(SID=shard01)))
    SCAN address:
    ONS remote port: 0
    Disk Threshold, ms: 20
    CPU Threshold, %: 75
    Version: 18.0.0.0
    Failed DDL: create tablespace set tbsset
    DDL Error: ORA-02585: create tablepsace set failure, one of its tablespaces not created
    ORA-01119: error in creating database file \'/ade/b/3667445372/oracle/rdbms/dbs/
    SHARD01/datafile/o1_mf_tbsset_%u_.dbf\'
    ORA-27040: file create error, unable to create file
    Linux-x86_64 Error: 13: Permission denied
    Additional information: 1 \(ngsmoci_execute\)
    Failed DDL id: 2
    Availability: ONLINE

The text beginning with “Failed DDL:” indicates the problem. To resolve it, the user must log in to the shard database host and make the directory writable.

Display the permissions on the directory:

    cd $ORACLE_HOME/rdbms/dbs
     ls –l ../ | grep dbs
    dr-xr-xr-x  4 oracle dba    102400 Jul 20 15:41 dbs/

Change the directory to writable:

    chmod +w .
    ls –l ../ | grep dbs
    drwxrwxr-x  4 oracle dba    102400 Jul 20 15:41 dbs/

Go back to the GDSCTL console and issue the `recover shard` command:

    GDSCTL> recover shard -shard shard01

Check the status again:

    GDSCTL> show ddl
    id      DDL Text                                      Failed shards
    --      --------                                      -------------
    1       create user example_user identified by *****
    2       create tablespace set tbsset

    GDSCTL> config shard -shard shard01

    Conversion = ':'Name: shard01
    Shard Group: dbs1
    Status: Ok
    State: Deployed
    Region: east
    Connection string: (DESCRIPTION=(ADDRESS=(HOST=shard01-host)(PORT=1521)(PROTOCOL=tcp))
    (CONNECT_DATA=(SID=shard01)))
    SCAN address:
    ONS remote port: 0
    Disk Threshold, ms: 20
    CPU Threshold, %: 75
    Version: 18.0.0.0
    Last Failed DDL:
    DDL Error: ---
    DDL id:
    Availability: ONLINE

As shown above, the failed DDL error no longer appears.

Example 6-3 Recovery from an error on a shard by executing a corrective action on all other shards

In this example, the user attempts to create another tablespace set, tbs_set, but the DDL fails on a shard because there is already an existing local tablespace with the same name.

On the shard catalog:

    SQL> create tablespace set tbs_set;
    Tablespace created.

Check status using the GDSCTL `show ddl` command:

    GDSCTL> show ddl
    id      DDL Text                                      Failed shards
    --      --------                                      -------------
    1       create user example_user identified by *****
    2       create tablespace set tbsset
    3       create tablespace set tbs_set                 shard01

    GDSCTL> config shard -shard shard01
    Conversion = ':'Name: shard01
    ……
    Failed DDL: create tablespace set tbs_set
    DDL Error: ORA-02585: create tablespace set failure, one of its tablespaces not created
    ORA-01543: tablespace \'TBS_SET\' already exists \(ngsmoci_execute\)

A solution to this problem is to login to shard01 as a local database administrator, drop the tablespace TBS_SET, and then run GDSCTL `recover shard -shard shard01`. But suppose you want to keep this tablespace, and instead choose to drop the newly created tablespace set that has the name conflict and create another tablespace set with a different name, such as tbsset2. The following example shows how to do that on the shard catalog:

    SQL> drop tablespace set tbs_set;
    SQL> create tablespace set tbs_set2;

Check status using GDSCTL:

    GDSCTL> show ddl
    id      DDL Text                                      Failed shards
    --      --------                                      -------------
    1       create user example_user identified by *****
    2       create tablespace set tbsset
    3       create tablespace set tbs_set                 shard01
    4       drop tablespace set tbs_set
    5       create tablespace set tbsset2

You can see that DDLs 4 and 5 are not attempted on shard01 because DDL 3 failed there. To make this shard consistent with the shard catalog, you must run the GDSCTL `recover shard` command. However, it does not make sense to execute DDL 3 on this shard because it will fail again and you actually do not want to create tablespace set tbs_set anymore. To skip DDL 3 run `recover shard` with the `–ignore_first` option:

    GDSCTL> recover shard -shard shard01 –ignore_first
    GSM Errors: dbs1 shard01:ORA-00959: tablespace \'TBS_SET\' does not exist
     (ngsmoci_execute)

    GDSCTL> show ddl
    id      DDL Text                                Failed shards
    --      --------                                -------------
    1       create user sidney identified by *****
    2       create tablespace set tbsset
    3       create tablespace set tbs_set
    4       drop tablespace set tbs_set             shard01
    5       create tablespace set tbsset2

There is no failure with DDL 3 this time because it was skipped. However, the next DDL (4 - drop tablespace set tbs_set) was applied and resulted in the error because the tablespace set to be dropped does not exist on the shard.

Because the `–ignore_first` option only skips the first DDL, you need to execute `recover shard` again to skip the `drop` statement as well:

    GDSCTL> recover shard -shard shard01 –ignore_first

    GDSCTL> show ddl
    id      DDL Text                                Failed shards
    --      --------                                -------------
    1       create user sidney identified by *****
    2       create tablespace set tbsset
    3       create tablespace set tbs_set
    4       drop tablespace set tbs_set
    5       create tablespace set tbsset2

Note that there are no longer any failures shown, and all of the DDLs were applied successfully on the shards.

When `recover shard` is run with the `–ignore_first` option, the failed DDL is marked to be ignored during incremental deployment. Therefore, DDL numbers 3 and 4 are skipped when a new shard is added to the SDB, and only DDL numbers 1, 2, and 5 are applied.

### Generating Unique Sequence Numbers Across Shards

Oracle Sharding allows you to generate globally unique sequence numbers across shards for non-primary key columns, and it is handled by the sharded database.

Customers often need to generate unique IDs for non-primary key columns, for example order_id, when the customer_id is the sharding key. For this case among others, this feature lets you generate unique sequence numbers across shards, while not requiring you to manage the global uniqueness of a given non-primary key column in your application.

This functionality is supported by a new object, `SHARDED SEQUENCE`. A sharded sequence is created on the shard catalog but has an instance on each shard. Each instance generates monotonically increasing numbers that belong to a range which does not overlap with ranges used on other shards. Therefore, every generated number is globally unique.

A sharded sequence can be used, for example, to generate a unique order number for a table sharded by a customer ID. An application that establishes a connection to a shard using the customer ID as a key can use a local instance of the sharded sequence to generate a globally unique order number.

Note that the number generated by a sharded sequence cannot be immediately used as a sharding key for a new row being inserted into this shard, because the key value may belong to another shard and the insert will result in an error. To insert a new row, the application should first generate a value of the sharding key and then use it to connect to the appropriate shard. A typical way to generate a new value of the sharding key would be use a regular (non-sharded) sequence on the shard catalog.

If a single sharding key generator becomes a bottleneck, a sharded sequence can be used for this purpose. In this case, an application should connect to a random shard (using the global service without specifying the sharding key), get a unique key value from a sharded sequence, and then connect to the appropriate shard using the key value.

To support this feature, new `SEQUENCE` object clauses, `SHARD` and `NOSHARD`, are included in the `SEQUENCE` object DDL syntax, as shown in the following `CREATE` statement syntax.

    CREATE | ALTER SEQUENCE [ schema. ]sequence
       [ { INCREMENT BY | START WITH } integer
       | { MAXVALUE integer | NOMAXVALUE }
       | { MINVALUE integer | NOMINVALUE }
       | { CYCLE | NOCYCLE }
       | { CACHE integer | NOCACHE }
       | { ORDER | NOORDER }
       | { SCALE {EXTEND | NOEXTEND} | NOSCALE}
       | { SHARD {EXTEND | NOEXTEND} | NOSHARD}
       ]

`NOSHARD` is the default for a sequence. If the `SHARD` clause is specified, this property is registered in the sequence object’s dictionary table, and is shown using the `DBA_SEQUENCES`, `USER_SEQUENCES`, and `ALL_SEQUENCES` views.

When `SHARD` is specified, the `EXTEND` and `NOEXTEND` clauses define the behavior of a sharded sequence. When `EXTEND` is specified, the generated sequence values are all of length (x+y), where x is the length of a `SHARD` offset of size 4 (corresponding to the width of the maximum number of shards, that is, 1000) affixed at beginning of the sequence values, and y is the maximum number of digits in the sequence `MAXVALUE`/`MINVALUE`.

The default setting for the `SHARD` clause is `NOEXTEND`. With the `NOEXTEND` setting, the generated sequence values are at most as wide as the maximum number of digits in the sequence `MAXVALUE`/`MINVALUE`. This setting is useful for integration with existing applications where sequences are used to populate fixed width columns. On invocation of `NEXTVAL` on a sequence with `SHARD NOEXTEND` specified, a user error is thrown if the generated value requires more digits of representation than the sequence’s `MAXVALUE`/`MINVALUE`.

If the `SCALE` clause is also specified with the `SHARD` clause, the sequence generates scalable values within a shard for multiple instances and sessions, which are globally unique. When `EXTEND` is specified with both the `SHARD` and `SCALE` keywords, the generated sequence values are all of length (x+y+z), where x is the length of a prepended `SHARD` offset of size 4, y is the length of the scalable offset (default 6), and z is the maximum number of digits in the sequence `MAXVALUE`/`MINVALUE`.

**Note:**

When using the `SHARD` clause, do not specify `ORDER` on the sequence. Using `SHARD` generates globally unordered values. If `ORDER` is required, create the sequences locally on each node.

The `SHARD` keyword will work in conjunction with `CACHE` and `NOCACHE` modes of operation.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Changes-in-This-Release-for-Oracle-Database-SQL-Language-Reference.md)
