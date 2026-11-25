## 11.3 XS_ADMIN_UTIL Package

The XS_ADMIN_UTIL package contains helper subprograms to be used by other packages.

This section includes the following topics:

- Security Model

- Constants

- Object Types, Constructor Functions, Synonyms, and Grants

- Summary of XS_ADMIN_UTIL Subprograms

### 11.3.1 Security Model

The `XS_ADMIN_UTIL` package is created in the `SYS` schema. The caller has invoker's rights on this package. The `SYS` privilege is required to grant or revoke a Real Application Security system privilege to or from a user or role.

### 11.3.2 Constants

The following constants define the delete options:

    DEFAULT_OPTION               CONSTANT PLS_INTEGER := 1;
    CASCADE_OPTION               CONSTANT PLS_INTEGER := 2;
    ALLOW_INCONSISTENCIES_OPTION CONSTANT PLS_INTEGER := 3;

The following constants define the principal's type:

    PTYPE_XS              CONSTANT PLS_INTEGER := 1;
    PTYPE_DB              CONSTANT PLS_INTEGER := 2;
    PTYPE_DN              CONSTANT PLS_INTEGER := 3;
    PTYPE_EXTERNAL        CONSTANT PLS_INTEGER := 4;

### 11.3.3 Object Types, Constructor Functions, Synonyms, and Grants

The following object types, constructor functions, synonyms, and `GRANT` statements are defined for this package.

    CREATE OR REPLACE TYPE XS$LIST IS VARRAY(1000) OF VARCHAR2(4000);
    CREATE OR REPLACE TYPE XS$NAME_LIST IS VARRAY(1000) OF VARCHAR2(261);

### 11.3.4 Summary of XS_ADMIN_UTIL Subprograms

Table 11-4 Summary of XS_ADMIN_UTIL Subprograms

| Subprogram                        | Brief Description                                                        |
|:----------------------------------|:-------------------------------------------------------------------------|
| GRANT_SYSTEM_PRIVILEGE Procedure  | Grant a Real Application Security system privilege to a user or role.    |
| REVOKE_SYSTEM_PRIVILEGE Procedure | Revoke a Real Application Security system privilege from a user or role. |

####

This section describes the following XS_ADMIN_UTIL subprograms:

#### 11.3.4.1 GRANT_SYSTEM_PRIVILEGE Procedure

The `GRANT_SYSTEM_PRIVILEGE` procedure is used to grant a Real Application Security system privilege or schema privilege to a user or role. Only `SYS` or a user who has `GRANT ANY PRIVILEGE` privilege can perform this operation.

The audit action `AUDIT_GRANT_PRIVILEGE`, audits all `GRANT_SYSTEM_PRIVILEGE` calls for granting system privileges or schema privileges.

##### Syntax

    XS_ADMIN_UTIL.GRANT_SYSTEM_PRIVILEGE (
      priv_name      IN VARCHAR2,
      user_name      IN VARCHAR2,
      user_type      IN  PLS_INTEGER := XS_ADMIN_UTIL.PTYPE_DB,
      schema         IN VARCHAR2);

##### Parameters

| Parameter    | Description                                                                                                                          |
|:-------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| `priv_name`  | Specifies the name of the Real Application Security system privilege or schema privilege to be granted.                              |
| `user_name ` | Specifies the name of the user or role to which the Real Application Security system privilege or schema privilege is to be granted. |
| `user_type`  | The type of user. By default the database user.                                                                                      |
| `schema`     | The schema on which the privilege is granted. The value is `NULL` if the privilege is a system privilege.                            |

##### Examples

The following example creates a database user, `dbuser1`, and grants Real Application Security privilege `ADMINISTER_SESSION` to this database user and specifies the `user_type` as `XS_ADMIN_UTIL.PTYPE_DB`, though by default, this is the default value and need not be specified.

    SQL> CREATE USER dbuser1 identified by password;

    SQL> EXEC SYS.XS_ADMIN_UTIL.GRANT_SYSTEM_PRIVILEGE('ADMINISTER_SESSION', 'dbuser1', XS_ADMIN_UTIL.PTYPE_DB, 'HR1');

The following example creates an application user, `user1`, and grants Real Application Security privilege `ADMINISTER_SESSION` to this application user, specifies the `user_type` as `XS_ADMIN_UTIL.PTYPE_XS`, and specifies the schema as HR1.

    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_USER('user1','HR1');

    SQL> EXEC SYS.XS_PRINCIPAL.SET_PASSWORD('user1', 'password');

    SQL> EXEC SYS.XS_ADMIN_UTIL.GRANT_SYSTEM_PRIVILEGE('ADMINISTER_SESSION', 'user1', XS_ADMIN_UTIL.PTYPE_XS, 'HR1');

#### 11.3.4.2 REVOKE_SYSTEM_PRIVILEGE Procedure

The `REVOKE_SYSTEM_PRIVILEGE` is used to revoke a Real Application Security ststem privilege or schema privilege from a user or role. Only `SYS` privilege or a user with `GRANT ANY PRIVILEGE` privilege can perform this operation.

The audit action `AUDIT_REVOKE_PRIVILEGE`, audits all `REVOKE_SYSTEM_PRIVILEGE` calls for revoking system privileges or schema privileges.

##### Syntax

    XS_ADMIN_UTIL.REVOKE_SYSTEM_PRIVILEGE (
      priv_name      IN VARCHAR2,
      user_name      IN VARCHAR2,
      user_type      IN PLS_INTEGER := XS_ADMIN_UTIL.PTYPE_DB,
      schema         IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                                                                                            |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| `priv_name` | Specifies the name of the Real Application Security system privilege or schema privilege to be revoked.                                |
| `user_name` | Specifies the name of the user or role from which the Real Application Security system privilege or schema privilege is to be revoked. |
| `user_type` | The type of user. By default the database user.                                                                                        |
| `schema`    | The schema on which the privilege is revoked. The value is `NULL` if the privilege is a system privilege.                              |

##### Examples

The following example creates a database user, `dbuser1`, and revokes Real Application Security privilege `ADMINISTER_SESSION` from this database user and specifies the `user_type` as `XS_ADMIN_UTIL.PTYPE_DB`, though by default, this is the default value and need not be specified.

    CREATE USER dbuser1 identified by password;

    SYS.XS_ADMIN_UTIL.REVOKE_SYSTEM_PRIVILEGE('ADMINISTER_SESSION','dbuser1', XS_ADMIN_UTIL.PTYPE_DB, 'HR1');

The following example creates an application user, `user1`, and revokes Real Application Security privilege `ADMINISTER_SESSION` from this application user and specifies the `user_type` as `XS_ADMIN_UTIL.PTYPE_XS`.

    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_USER('user1','HR1');

    SQL> EXEC SYS.XS_PRINCIPAL.SET_PASSWORD('user1', 'password');

    SQL> EXEC SYS.XS_ADMIN_UTIL.REVOKE_SYSTEM_PRIVILEGE('ADMINISTER_SESSION','user1', XS_ADMIN_UTIL.PTYPE_XS, 'HR1');
