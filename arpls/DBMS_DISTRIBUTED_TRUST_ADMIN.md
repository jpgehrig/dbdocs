## 66  DBMS_DISTRIBUTED_TRUST_ADMIN

`DBMS_DISTRIBUTED_TRUST_ADMIN` procedures maintain the Trusted Servers List. Use these procedures to define whether a server is trusted. If a database is not trusted, Oracle refuses current user database links from the database.

This chapter contains the following topics:

- Overview

- Security Model

- Examples

- Summary of DBMS_DISTRIBUTED_TRUST_ADMIN Subprograms

### 66.1 DBMS_DISTRIBUTED_TRUST_ADMIN Overview

Oracle uses local Trusted Servers Lists, along with enterprise domain membership lists stored in the enterprise LDAP directory service, to determine if another database is trusted. The LDAP directory service entries are managed with the Enterprise Security Manager Tool in Oracle Enterprise Manager.

Oracle considers another database to be "trusted" if it meets the following criteria:

1.  It is in the same enterprise domain in the directory service as the local database.

2.  The enterprise domain is marked as trusted in the directory service.

3.  It is not listed as untrusted in the local Trusted Servers List. Current user database links will only be accepted from another database if both databases involved trust each other.

You can list a database server locally in the Trusted Servers List regardless of what is listed in the directory service. However, if you list a database that is not in the same domain as the local database, or if that domain is untrusted, the entry will have no effect.

This functionality is part of the Enterprise User Security feature of the Oracle Advanced Security Option.

### 66.2 DBMS_DISTRIBUTED_TRUST_ADMIN Security Model

To execute `DBMS_DISTRIBUTED_TRUST_ADMIN`, the `EXECUTE_CATALOG_ROLE` role must be granted to the DBA. To select from the view `TRUSTED_SERVERS`, the `SELECT_CATALOG_ROLE` role must be granted to the DBA.

It is important to know whether all servers are trusted or not trusted. Trusting a particular server with the `ALLOW_SERVER` procedure does not have any effect if the database already trusts all databases, or if that database is already trusted. Similarly, denying a particular server with the `DENY_SERVER` procedure does not have any effect if the database already does not trust any database or if that database is already untrusted.

The procedures `DENY_ALL` and `ALLOW_ALL` delete all entries (in other words, server names) that are explicitly allowed or denied using the `ALLOW_SERVER` procedure or `DENY_SERVER` procedure respectively.

### 66.3 DBMS_DISTRIBUTED_TRUST_ADMIN Examples

If you have not yet used the package `DBMS_DISTRIBUTED_TRUST_ADMIN` to change the trust listing, by default you trust all databases in the same enterprise domain if that domain it listed as trusted in the directory service:

    SELECT * FROM TRUSTED_SERVERS;
    TRUST      NAME
    --------- ---------------------
    Trusted   All

Because all servers are currently trusted, you can execute the DENY_SERVER Procedure and specify that a particular server is not trusted:

    EXECUTE DBMS_DISTRIBUTED_TRUST_ADMIN.DENY_SERVER
                               ('SALES.US.AMERICAS.ACME_AUTO.COM');
    PL/SQL procedure successfully completed.

    SELECT * FROM TRUSTED_SERVERS;
    TRUST       NAME
    --------- -----------------------------------------------
    Untrusted SALES.US.AMERICAS.ACME_AUTO.COM

By executing the DENY_ALL Procedure, you can choose to not trust any database server:

    EXECUTE DBMS_DISTRIBUTED_TRUST_ADMIN.DENY_ALL;

    PL/SQL procedure successfully completed.

    SELECT * FROM TRUSTED_SERVERS;

    TRUST       NAME
    --------- -----------------------------------------------
    Untrusted All

The ALLOW_SERVER Procedure can be used to specify that one particular database is to be trusted:

    EXECUTE DBMS_DISTRIBUTED_TRUST_ADMIN.ALLOW_SERVER
                                ('SALES.US.AMERICAS.ACME_AUTO.COM');
    PL/SQL procedure successfully completed.

    SELECT * FROM TRUSTED_SERVERS;
    TRUST       NAME
    --------- ------------------------------------------------
    Trusted   SALES.US.AMERICAS.ACME_AUTO.COM

### 66.4 Summary of DBMS_DISTRIBUTED_TRUST_ADMIN Subprograms

This table lists and briefly describes the `DBMS_DISTRIBUTED_TRUST_ADMIN` subprograms.

Table 66-1 DBMS_DISTRIBUTED_TRUST_ADMIN Package Subprograms

| Subprogram             | Description                                                                                    |
|:-----------------------|:-----------------------------------------------------------------------------------------------|
| ALLOW_ALL Procedure    | Empties the list and inserts a row indicating that all servers should be trusted               |
| ALLOW_SERVER Procedure | Enables a specific server to be allowed access even though `deny` all is indicated in the list |
| DENY_ALL Procedure     | Empties the list and inserts a row indicating that all servers should be untrusted             |
| DENY_SERVER Procedure  | Enables a specific server to be denied access even though allow all is indicated in the list   |

#### 66.4.1 ALLOW_ALL Procedure

This procedure empties the Trusted Servers List and specifies that all servers that are members of a trusted domain in an enterprise directory service and that are in the same domain are allowed access.

The view `TRUSTED_SERVERS` will show "`TRUSTED` `ALL`" indicating that the database trusts all servers that are currently trusted by the enterprise directory service.

##### Syntax

    DBMS_DISTRIBUTED_TRUST_ADMIN.ALLOW_ALL;

##### Usage Notes

`ALLOW_ALL` only applies to servers listed as trusted in the enterprise directory service and in the same enterprise domain.

#### 66.4.2 ALLOW_SERVER Procedure

This procedure ensures that the specified server is considered trusted (even if you have previously specified "`deny` `all`").

##### Syntax

    DBMS_DISTRIBUTED_TRUST_ADMIN.ALLOW_SERVER (
       server IN VARCHAR2);

##### Parameters

Table 66-2 ALLOW_SERVER Procedure Parameters

| Parameter | Description                                               |
|:----------|:----------------------------------------------------------|
| `server`  | Unique, fully-qualified name of the server to be trusted. |

##### Usage Notes

If the Trusted Servers List contains the entry "`deny` `all`", then this procedure adds a specification indicating that a specific database (for example, `DBx`) is to be trusted.

If the Trusted Servers List contains the entry "`allow` `all`", and if there is no "`deny` `DBx`" entry in the list, then executing this procedure causes no change.

If the Trusted Servers List contains the entry "`allow` `all`", and if there is a "`deny` `DBx`" entry in the list, then that entry is deleted.

#### 66.4.3 DENY_ALL Procedure

This procedure empties the Trusted Servers List and specifies that all servers are denied access.

The view `TRUSTED_SERVERS` will show "`UNTRUSTED` `ALL`" indicating that no servers are currently trusted.

##### Syntax

    DBMS_DISTRIBUTED_TRUST_ADMIN.DENY_ALL;

#### 66.4.4 DENY_SERVER Procedure

This procedure ensures that the specified server is considered untrusted (even if you have previously specified `allow all`).

##### Syntax

    DBMS_DISTRIBUTED_TRUST_ADMIN.DENY_SERVER (
       server IN VARCHAR2);

##### Parameters

Table 66-3 DENY_SERVER Procedure Parameters

| Parameter | Description                                                 |
|:----------|:------------------------------------------------------------|
| `server`  | Unique, fully-qualified name of the server to be untrusted. |

##### Usage Notes

If the Trusted Servers List contains the entry `allow` `all`, then this procedure adds an entry indicating that the specified database (for example, `DBx`) is not to be trusted.

If the Trusted Servers List contains the entry "`deny` `all`", and if there is no "`allow` `DBx`" entry in the list, then this procedure causes no change.

If the Trusted Servers List contains the entry "`deny` `all`", and if there is an "`allow` `DBx`" entry, then this procedure causes that entry to be deleted.
