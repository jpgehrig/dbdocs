## 180 DBMS_TNS

The `DBMS_TNS` package provides the `RESOLVE_TNSNAME` function to resolve a TNS name and return the corresponding Oracle Net8 connection string.

This chapter contains the following topics:

- DBMS_TNS Overview

- DBMS_TNS Security Model

- Summary of DBMS_TNS Subprograms

### 180.1 DBMS_TNS Overview

The `DBMS_TNS` package contains one function, `RESOLVE_TNSNAME`, which returns the resolved connect string from configured sources that have been defined in the `names.directory_path` parameter in the `sqlnet.ora` file.

The `RESOLVE_TNSNAME` function in this package helps you to identify interconnected databases and trace the system change number (SCN) flow across distributed databases.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-a-distributed-database.md) for more information about finding database link information

- [Oracle Database Reference](../refrn/ALL_DB_LINKS.md) for information about the `ALL_DB_LINKS` data dictionary view

### 180.2 DBMS_TNS Security Model

You must be granted the `EXECUTE` privilege on the `DBMS_TNS` package.

### 180.3 Summary of DBMS_TNS Subprograms

This table lists the `DBMS_TNS` subprograms and briefly describes them.

Table 180-1 DBMS_TNS Parameters

| Subprogram               | Description                                                                                                                                                      |
|:-------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| RESOLVE_TNSNAME Function | Returns the resolved connect string from any configured source (tnsnames, LDAP, Easy Connect) as indicated in the `sqlnet.ora` `names.directory_path` parameter) |

#### 180.3.1 RESOLVE_TNSNAME Function

This function returns the resolved connect string from any configured source (for example, TNS names, Lightweight Directory Access Protocol (LDAP), or Oracle Easy Connect) as indicated in the `sqlnet.ora` `names.directory_path` parameter.

##### Syntax

    DBMS_TNS.RESOLVE_TNSNAME (
       tns_name VARCHAR2)
      RETURN VARCHAR2;

##### RESOLVE_TNSNAME Function Parameters

| Parameter  | Description                                      |
|:-----------|:-------------------------------------------------|
| `tns_name` | Database address for establishing the connection |

##### Usage Notes

- Database administrators and system management tools can explicitly call the `DBMS_TNS.RESOLVE_TNSNAME function` to resolve a `tns_name`:

- Because the resolved value can change over time, Oracle does not recommend storing or caching this value, because these kinds of values can become invalid over time.

- You can use the `DBMS_TNS.RESOLVE_TNSNAME` function to resolve TNS names that were referred to by other data dictionary views such as `ALL_DB_LINKS` and `USER_DB_LINKS`. In addition, you can use it to find any TNS name entry in the `tnsnames.ora` file.

##### Example

    SELECT DB_LINK, DBMS_TNS.RESOLVE_TNSNAME(HOST) FROM DBA_DB_LINKS;

    DB_LINK
    --------------------------------------------------------------------------------
    DBMS_TNS.RESOLVE_TNSNAME(HOST)
    --------------------------------------------------------------------------------
    US.EXAMPLE.COM
    (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(KEY=may))(CONNECT_DATA=(SERVICE_NAME=us.example.com)(CID=(PROGRAM=oracle)(HOST=juno)(USER=psmith))
    ))
