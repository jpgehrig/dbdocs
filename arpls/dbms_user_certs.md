## 190 DBMS_USER_CERTS

The `DBMS_USER_CERTS` package allows you add and delete certificates.

This chapter contains the following topics:

- DBMS_USER_CERTS Overview
- DBMS_USER_CERTS Security Model
- Summary of DBMS_USER_CERTS Subprograms

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-tables.md)

- [Oracle Database Concepts](../cncpt/tables-and-table-clusters.md)

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md)

- [Oracle Database Reference](../refrn/index.md)

- For information on hidden columns in blockchain tables, see [Hidden Columns in Blockchain Tables](../admin/managing-tables.md)

### 190.1 DBMS_USER_CERTS Overview

The `DBMS_USER_CERTS` package allows you add and delete certificates.

The `DBMS_USER_CERTS` package allows you to:

- add certificates
- delete certificates

One use case is to attach a digital signature to a row in a blockchain table and be able to verify the digital signature later. A certificate used to sign one or more rows in blockchain tables and which has since expired should remain in the database until all those rows have been deleted from the blockchain tables.

### 190.2 DBMS_USER_CERTS Security Model

The `DBMS_USER_CERTS` package is owned by `SYS` and is installed as part of database installation.

- Both `ADD_CERTIFICATE()` and `DROP_CERTIFICATE()` sub-programs can be executed by any database user. The `EXECUTE` privilege on `DBMS_USER_CERTS` package is granted to `PUBLIC` role.
- Using `ADD_CERTIFICATE()`, a database user can add multiple certificates, each one would be identified uniquely using a `GUID`.
- Only `SYSDBA` or the user who owns the certificate, can drop it using `DROP_CERTIFICATE()`.

### 190.3 Summary of DBMS_USER_CERTS Subprograms

The `DBMS_USER_CERTS` package uses `ADD_CERTIFICATE` and `DROP_CERTIFICATE` subprograms to add and delete `X.509` certificates which are used for signature verification for blockchain tables by the current user.

Table 190-1 DBMS_USER_CERTS Package Subprograms

| Subprogram                 | Description                                                                               |
|:---------------------------|:------------------------------------------------------------------------------------------|
| ADD_CERTIFICATE Procedure  | Adds `X.509` certificates which are used for signature verification of blockchain tables. |
| DROP_CERTIFICATE Procedure | Drops a certificate that is used for signature verification of blockchain tables.         |

#### 190.3.1 ADD_CERTIFICATE Procedure

This procedure can be used by the current user to add an `X.509` certificate that is used for signature verification of blockchain tables.

##### Syntax

    DBMS_USER_CERTS.ADD_CERTIFICATE(
       x509_cert                 IN  BLOB,
       cert_id                   OUT RAW);

##### Parameters

Table 190-2 ADD_CERTIFICATE Procedure Parameters

| Parameter   | Description                                                                   |
|:------------|:------------------------------------------------------------------------------|
| `x509_cert` | The `X.509` certificate used for signature verification of blockchain tables. |
| `cert_id`   | The Global Unique Identifier (GUID) for the certificate.                      |

#### 190.3.2 DROP_CERTIFICATE Procedure

This procedure can be used by the current user to drop a certificate that is used for signature verification of blockchain tables.

##### Syntax

    DBMS_USER_CERTS.DROP_CERTIFICATE(
       cert_id                    IN  RAW);

##### Parameters

Table 190-3 DROP_CERTIFICATE Procedure Parameters

| Parameter | Description                                             |
|:----------|:--------------------------------------------------------|
| `cert_id` | The Global Unique Identifier (GUID) of the certificate. |
