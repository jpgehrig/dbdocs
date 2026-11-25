## 199  DBMS_XDB_ADMIN

The `DBMS_XDB_ADMIN` package provides an interface to manage the Oracle XML DB repository.

This chapter contains the following topics:

- DBMS_XDB_ADMIN Security Model

- Summary of DBMS_XDB_ADMIN Subprograms

**See Also:**

[Oracle XML DB Developer's Guide](../adxdb/administration-of-XML-DB.md) for information about Oracle XML DB Repository

### 199.1 DBMS_XDB_ADMIN Security Model

Owned by `XDB`, the `DBMS_XDB_ADMIN` package must be created by `SYS` or `XDB`. The `EXECUTE` privilege is granted to `SYS` or `XDB` or `DBA`. Subprograms in this package are executed using the privileges of the current user.

### 199.2 Summary of DBMS_XDB_ADMIN Subprograms

This table lists the package subprograms in alphabetical order.

Table 199-1 DBMS_XDB_ADM Package Subprograms

| Subprogram                         | Description                                                         |
|:-----------------------------------|:--------------------------------------------------------------------|
| CREATENONCEKEY Procedure           | Generates a nonce value for use in digest authentication            |
| INSTALLDEFAULTWALLET Procedure     | Installs the default XDB wallet in the default XDB wallet directory |
| MOVEXDB_TABLESPACE Procedure       | Moves the XDB (user) to the specified tablespace                    |
| REBUILDHIERARCHICALINDEX Procedure | Rebuilds the hierarchical index after import or export operations   |

#### 199.2.1 CREATENONCEKEY Procedure

This procedure generates a nonce value for use in digest authentication.

##### Syntax

    DBMS_XDB_ADMIN.CREATENONCEKEY;

#### 199.2.2 INSTALLDEFAULTWALLET Procedure

This procedure installs the default XDB wallet in the default XDB wallet directory.

The directory name where the XDB wallet is stored is prefixed either by `ORACLE_BASE` when it is defined, or `ORACLE_HOME`. It is then followed by `/admin/``db_name``/xdb_wallet` where db_name is the unique database name.

##### Syntax

    DBMS_XDB_ADMIN.INSTALLDEFAULTWALLET;

##### Usage Notes

Only `SYS` can install or replace the default wallet.

#### 199.2.3 MOVEXDB_TABLESPACE Procedure

This procedure moves the XDB (user) to the specified tablespace.

##### Syntax

    DBMS_XDB_ADMIN.MOVEXDB_TABLESPACE(
       new_tablespace   IN  VARCHAR2);

##### Parameters

Table 199-2 MOVEXDB_TABLESPACE Procedure Parameters

| Parameter        | Description                                      |
|:-----------------|:-------------------------------------------------|
| `new_tablespace` | Name of the tablespace to where the XDB is moved |

##### Usage Notes

- This operation waits for all concurrent XDB sessions to exit.

- If `MOVEXDB_TABLESPACE` fails, the user should restart the database before issuing any further command.Failure to do so will result into unexpected behavior from the database.

- The XDB repository by default resides in the `SYSAUX` tablespace. Using this procedure it can be moved to another tablespace. As a best practice we recommend to create a dedicated tablespace for the XDB repository only and not share it with other objects (such as tables). The tablespace containing the XDB repository should never be set to `READ` `ONLY` because this might affect various XML operations being executed.

#### 199.2.4 REBUILDHIERARCHICALINDEX Procedure

This procedure rebuilds the hierarchical index after import or export operations. This is necessary because data cannot be exported from index tables.

##### Syntax

    DBMS_XDB_ADMIN.REBUILDHIERARCHICALINDEX;
