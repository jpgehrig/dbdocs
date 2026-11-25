## 11.8 XS_PRINCIPAL Package

The XS_PRINCIPAL package contains procedures used to create, manage, and delete application principals. These application principals include application users, regular application roles, and dynamic application roles.

This section includes the following topics:

- Security Model

- Constants

- Object Types, Constructor Functions, Synonyms, and Grants

- Summary of XS_PRINCIPAL Subprograms

### 11.8.1 Security Model

The `XS_PRINCIPAL` package is created under the `SYS` schema.

Users with Real Application Security `PROVISION` privilege can create, modify, or drop application users and roles. The privileges required to create, modify, or drop application users and roles are no longer governed by the same system privileges required to create, modify, or drop database users and roles.

### 11.8.2 Constants

The following constants define the user's status:

    ACTIVE          CONSTANT PLS_INTEGER := 1;
    INACTIVE        CONSTANT PLS_INTEGER := 2;
    UNLOCKED        CONSTANT PLS_INTEGER := 3;
    EXPIRED         CONSTANT PLS_INTEGER := 4;
    LOCKED          CONSTANT PLS_INTEGER := 5;

The following constants define dynamic role scope:

    SESSION_SCOPE   CONSTANT PLS_INTEGER := 0;
    REQUEST_SCOPE   CONSTANT PLS_INTEGER := 1;

The following constants define the verifier type:

    XS_SHA512       CONSTANT PLS_INTEGER := 2 ;
    XS_SALTED_SHA1  CONSTANT PLS_INTEGER := 1 ;

### 11.8.3 Object Types, Constructor Functions, Synonyms, and Grants

The following object types, constructor functions, synonyms, and `GRANT` statements are defined for this package.

    -- Type definition for roles granted to the principals
    CREATE OR REPLACE TYPE XS$ROLE_GRANT_TYPE AS OBJECT (
    -- Member Variables
    -- Constants defined in other packages cannot be recognized in a type.
    -- e.g.  XS_ADMIN_UTIL.XSNAME_MAXLEN
    -- name   VARCHAR2(XS_ADMIN_UTIL.XSNAME_MAXLEN),
      name          VARCHAR2(130),
    -- Start date of the effective date
      start_date    TIMESTAMP WITH TIME ZONE,
    -- End date of the effective date
      end_date      TIMESTAMP WITH TIME ZONE,

      CONSTRUCTOR FUNCTION XS$ROLE_GRANT_TYPE (
        name       IN VARCHAR2,
        start_date IN TIMESTAMP WITH TIME ZONE:= NULL,
        end_date   IN TIMESTAMP WITH TIME ZONE:= NULL)
      RETURN SELF AS RESULT,

      MEMBER FUNCTION get_role_name RETURN VARCHAR2,
      MEMBER PROCEDURE set_start_date(start_date IN TIMESTAMP WITH TIME ZONE),
      MEMBER FUNCTION get_start_date RETURN TIMESTAMP WITH TIME ZONE,
      MEMBER PROCEDURE set_end_date(end_date IN TIMESTAMP WITH TIME ZONE),
      MEMBER FUNCTION get_end_date RETURN TIMESTAMP WITH TIME ZONE
    );

    CREATE OR REPLACE TYPE XS$ROLE_GRANT_LIST AS VARRAY(1000) OF XS$ROLE_GRANT_TYPE;

### 11.8.4 Summary of XS_PRINCIPAL Subprograms

Table 11-10 Summary of XS_PRINCIPAL Subprograms

| Subprogram                          | Description                                                                                                                                                                                                  |
|:------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CREATE_USER Procedure               | Creates an application user.                                                                                                                                                                                 |
| CREATE_ROLE Procedure               | Creates an application role.                                                                                                                                                                                 |
| CREATE_DYNAMIC_ROLE Procedure       | Creates a dynamic application role.                                                                                                                                                                          |
| GRANT_ROLES Procedure               | Grants one or more application roles to an application principal.                                                                                                                                            |
| REVOKE_ROLES Procedure              | Revokes one or more roles from an application principal.                                                                                                                                                     |
| ADD_PROXY_USER Procedure            | Adds a proxy user for a target application user.                                                                                                                                                             |
| REMOVE_PROXY_USERS Procedure        | Removes specified proxy user or all proxy users for a target application user.                                                                                                                               |
| ADD_PROXY_TO_DBUSER                 | Add a proxy application user to a database user.                                                                                                                                                             |
| REMOVE_PROXY_FROM_DBUSER Procedure  | Remove a proxy application user from a database user.                                                                                                                                                        |
| SET_EFFECTIVE_DATES Procedure       | Sets or modifies the effective dates for an application user or role.                                                                                                                                        |
| SET_DYNAMIC_ROLE_DURATION Procedure | Sets or modifies the duration, in minutes, for a dynamic application role.                                                                                                                                   |
| SET_DYNAMIC_ROLE_SCOPE Procedure    | Sets or modifies the scope of a dynamic application role, such as `REQUEST_SCOPE` or `SESSION_SCOPE`.                                                                                                        |
| ENABLE_BY_DEFAULT Procedure         | Enables or disables an application role.                                                                                                                                                                     |
| ENABLE_ROLES_BY_DEFAULT Procedure   | Enables or disables all directly granted roles for the specified user.                                                                                                                                       |
| SET_USER_SCHEMA Procedure           | Sets the database schema for an application user.                                                                                                                                                            |
| SET_GUID Procedure                  | Sets the GUID for an external user or role.                                                                                                                                                                  |
| SET_ACL Procedure                   | Sets the Real Application Security session privilege for an application user or a dynamic role.                                                                                                              |
| SET_PROFILE Procedure               | Sets the application user's profile. This is a set of resource limits and password parameters that restrict database usage and database instance resources for a Real Application Security application user. |
| SET_USER_STATUS Procedure           | Sets or modifies the status of an application user account, such as `ACTIVE`, `INACTIVE`, `UNLOCK`, `LOCKED`, or `EXPIRED`.                                                                                  |
| SET_PASSWORD Procedure              | Sets or modifies the password for an application user account.                                                                                                                                               |
| SET_VERIFIER Procedure              | Sets or modifies the verifier for an application user account.                                                                                                                                               |
| SET_DESCRIPTION Procedure           | Sets the description string for an application user or role.                                                                                                                                                 |
| DELETE_PRINCIPAL Procedure          | Drops an application user or role.                                                                                                                                                                           |

This section describes the following XS_PRINCIPAL subprograms:

#### 11.8.4.1 CREATE_USER Procedure

The `CREATE_USER` procedure creates a new application user. You need the `CREATE USER` system privilege to create an application user.

You can use the [DBA_XS_USERS](real-application-security-data-dictionary-views.md) data dictionary view to get a list of all application users.

##### Syntax

    CREATE_USER (
      name            IN VARCHAR2,
      schema          IN VARCHAR2    := NULL,
      status          IN PLS_INTEGER := ACTIVE,
      start_date      IN TIMESTAMP WITH TIME ZONE  := NULL,
      end_date        IN TIMESTAMP WITH TIME ZONE  := NULL,
      guid            IN RAW         := NULL,
      external_source IN VARCHAR2    := NULL,
      description     IN VARCHAR2    := NULL,
      acl             IN VARCHAR2    := NULL);

##### Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`            | The name of the application user to be created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `status`          | The status of the user on creation. This can be one of the following values:<br>`ACTIVE`, `INACTIVE`.<br>The default value is `ACTIVE`.<br>The values `PASSWORDEXPIRED` and `LOCKED` are deprecated beginning with Oracle Database Release 12.1 (12.1.0.2).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `schema`          | The database schema to be associated with the user. This is optional.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `start_date`      | The date from which the user account becomes effective. This is optional.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `end_date`        | The date on which the user account becomes ineffective. This is optional.<br>If an `end_date` is specified, then the `start_date` must also be specified.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `guid`            | GUID of the user. This is valid for external users only.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `external_source` | Name of the system that is the source for this user. This is optional.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `description`     | A description for the user account. This is optional.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `acl`             | The Real Application Security session privilege. The default value is `NULL` meaning no ACL is set on the principal. The ACL must reside in the `SYS` schema, or else an error is thrown.<br>The Real Application Security session privilege to be set on the principal must follow the naming convention for Real Application Security objects and must exist before this procedure is called.<br>The session privilege is enforced as per the ACL set on the Real Application Security application user involved in the session operation. For example, a create session operation requires the caller to have the `CREATE SESSION` privilege in the ACL set on the Real Application Security application user.<br>Principal-specific ACL grants take precedence over existing system-level session privilege grants. A privilege check is first done in the ACL associated with the principal and if it succeeds, the operation proceeds. If the privilege check finds deny, the operation fails with an insufficient privilege error. If neither grant nor deny is found, the check is done in the system ACL associated with the `SESSION_SC` security class and the operation succeeds or fails based on this privilege check result. |

##### Examples

The following example creates a user:

    BEGIN
     SYS.XS_PRINCIPAL.CREATE_USER('TEST1');
    END;

The following example creates a user, and also specifies a schema and start date for the user:

    DECLARE
    st_date TIMESTAMP WITH TIME ZONE;
    BEGIN
      st_date := TO_TIMESTAMP_TZ('2010-06-18 11:00:00 -5:00','YYYY-MM-DD HH:MI:SS
      TZH:TZM');
      SYS.XS_PRINCIPAL.CREATE_USER(name=>'u2',
                                   schema=>'scott',
                                   start_date=>st_date);
    END;

#### 11.8.4.2 CREATE_ROLE Procedure

The `CREATE_ROLE` procedure creates a new application role. You need the `CREATE ROLE` system privilege to create a regular application role.

You can use the [DBA_XS_ROLES](real-application-security-data-dictionary-views.md) data dictionary view to get the list of application roles together with their attributes, like start date and end date

##### Syntax

    CREATE_ROLE (   name            IN VARCHAR2,
      enabled         IN BOOLEAN  := FALSE,
      start_date      IN TIMESTAMP WITH TIME ZONE := NULL,
      end_date        IN TIMESTAMP WITH TIME ZONE := NULL,
      guid            IN RAW      := NULL,
      external_source IN VARCHAR2 := NULL,
      description     IN VARCHAR2 := NULL);

##### Parameters

| Parameter         | Description                                                                                                                                       |
|:------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`            | The name of the application role to be created.                                                                                                   |
| `enabled`         | Specifies whether the role is enabled on creation. The default value is `FALSE`, which means that the role is disabled on creation.               |
| `start_date`      | The date from which the role becomes effective. This is optional.                                                                                 |
| `end_date`        | The date on which the role becomes ineffective. This is optional.<br>If an `end_date` is specified, then the `start_date` must also be specified. |
| `guid`            | GUID of the role. This is applicable for external roles only.                                                                                     |
| `external_source` | The name of the system that is the source for this role. This is optional.                                                                        |
| `description`     | An optional description for the role.                                                                                                             |

##### Examples

The following example creates an application role, called `hrmgr`:

    BEGIN
      SYS.XS_PRINCIPAL.CREATE_ROLE('hrmgr');
    END;

The following example creates an application role called `hrrep`. It also enables the role, and assigns the current date as start date for the role.

    DECLARE
      st_date TIMESTAMP WITH TIME ZONE;
    BEGIN
      st_date := SYSTIMESTAMP;
      SYS.XS_PRINCIPAL.CREATE_ROLE(name=>'hrrep',
                                   enabled=>true,
                                   start_date=>st_date);
    END;

#### 11.8.4.3 CREATE_DYNAMIC_ROLE Procedure

The `CREATE_DYNAMIC_ROLE` procedure creates a new dynamic application role. Dynamic application roles can be dynamically enabled or disabled by an application, based on the criteria defined by the application. You need the `CREATE ROLE` system privilege to create an dynamic application role.

You can use the [DBA_XS_DYNAMIC_ROLES](real-application-security-data-dictionary-views.md) data dictionary view to get a list of all dynamic application roles together with their attributes, like duration.

##### Syntax

    CREATE_DYNAMIC_ROLE (
      name        IN VARCHAR2,
      duration    IN PLS_INTEGER := NULL,
      scope       IN PLS_INTEGER := XS_PRINCIPAL.SESSION_SCOPE,
      description IN VARCHAR2    := NULL,
      acl         IN VARCHAR2    := NULL);

##### Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`        | The name of the dynamic application role to be created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `duration`    | The duration (in minutes) of the dynamic application role. This is an optional attribute.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `scope`       | The scope attribute of the dynamic application role. The possible values are `SESSION_SCOPE` and `REQUEST_SCOPE`. The default value is `XS_PRINCIPAL.SESSION_SCOPE.`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `description` | An optional description for the dynamic application role.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `acl`         | The Real Application Security session privilege. The default value is `NULL` meaning no ACL is set on the principal. The ACL must reside in the `SYS` schema, or else an error is thrown.<br>The Real Application Security session privilege to be set on the principal must follow the naming convention for Real Application Security objects and must exist before this procedure is called.<br>The session privilege is enforced as per the ACL set on the Real Application Security dynamic role involved in the session operation. For example, the attach operation with dynamic role requires the `ENABLE_DYNAMIC_ROLE` privilege in the ACLs to be set on the dynamic roles.<br>Principal-specific ACL grants take precedence over existing system-level session privilege grants. A privilege check is first done in the ACL associated with the principal and if it succeeds, the operation proceeds. If the privilege check finds deny, the operation fails with an insufficient privilege error. If neither grant nor deny is found, the check is done in the system ACL associated with the `SESSION_SC` security class and the operation succeeds or fails based on this privilege check result. |

##### Examples

The following example creates a dynamic application role, called `sslrole`:

    BEGIN
      SYS.XS_PRINCIPAL.CREATE_DYNAMIC_ROLE('sslrole');
    END;

The following example creates a dynamic application role called `reprole`. It also specifies a duration of 100 minutes for the role, and chooses the request scope for the role.

    BEGIN
      SYS.XS_PRINCIPAL.CREATE_DYNAMIC_ROLE(name=>'reprole',
                                           duration=>100,
                                           scope=>XS_PRINCIPAL.REQUEST_SCOPE);
    END;

#### 11.8.4.4 GRANT_ROLES Procedure

The `GRANT_ROLES` procedure grants one or more application roles to an application principal. You need the `GRANT ANY ROLE` system privilege to grant application roles.

You can use the [DBA_XS_ROLE_GRANTS](real-application-security-data-dictionary-views.md) data dictionary view to get the list of all role grants together with their details, like start date and end date.

##### Syntax

    GRANT_ROLES (
    grantee       IN VARCHAR2,
    role          IN VARCHAR2,
    start_date    IN TIMESTAMP WITH TIME ZONE:= NULL,
    end_date      IN TIMESTAMP WITH TIME ZONE:= NULL,);

    GRANT_ROLES (
    grantee   IN VARCHAR2,
    role_list IN XS$ROLE_GRANT_LIST);

##### Parameters

| Parameter    | Description                                                                 |
|:-------------|:----------------------------------------------------------------------------|
| `grantee`    | The name of the principal to which the role is granted.                     |
| `role`       | The name of the role to be granted.                                         |
| `role_list`  | The list of roles to be granted.                                            |
| `start_date` | The date on which the grant takes effect. This is an optional parameter.    |
| `end_date`   | The date until which the grant is in effect. This is an optional parameter. |

##### Examples

The following example grants the `HRREP` role to user `SMAVRIS` with a start date and an end date specified:

    DECLARE
      st_date TIMESTAMP WITH TIME ZONE;
      end_date TIMESTAMP WITH TIME ZONE;
    BEGIN
      st_date := TO_TIMESTAMP_TZ('2010-06-18 11:00:00 -5:00','YYYY-MM-DD HH:MI:SS
                                  TZH:TZM');
      end_date := TO_TIMESTAMP_Tz('2011-06-18 11:00:00 -5:00','YYYY-MM-DD HH:MI:SS
                                   TZH:TZM');
      SYS.XS_PRINCIPAL.GRANT_ROLES('SMAVRIS', 'HRREP', st_date, end_date);
    END;

The following example grants the `HRREP` and `HRMGR` roles to user `SMAVRIS`:

    DECLARE
      rg_list XS$ROLE_GRANT_LIST;
    BEGIN
      rg_list := XS$ROLE_GRANT_LIST(XS$ROLE_GRANT_TYPE('HRREP'),
                                    XS$ROLE_GRANT_TYPE('HRMGR'));

      SYS.XS_PRINCIPAL.GRANT_ROLES('SMAVRIS', rg_list);
    END;

The following example shows how to grant the role `XSCONNECT` to user `XSUSER`. This grant will allow user `XSUSER`` `using its password to connect to a database.

    EXEC SYS.XS_PRINCIPAL.GRANT_ROLES('XSUSER', 'XSCONNECT');

#### 11.8.4.5 REVOKE_ROLES Procedure

The `REVOKE_ROLES` procedure revokes the specified role(s) from the specified grantee. If no roles are specified, then all application roles are revoked from the grantee.You need the `GRANT ANY ROLE` system privilege to grant or revoke roles.

You can use the [DBA_XS_ROLE_GRANTS](real-application-security-data-dictionary-views.md) data dictionary view to get the list of all role grants together with their details, like start date and end date.

##### Syntax

    REVOKE_ROLES (
      grantee   IN VARCHAR2,
      role      IN VARCHAR2);

    REVOKE_ROLES (
      grantee   IN VARCHAR2,
      role_list IN XS$NAME_LIST);

    REVOKE_ROLES (
      grantee IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                        |
|:------------|:-------------------------------------------------------------------|
| `grantee`   | The application principal from whom the role(s) are to be revoked. |
| `role`      | The name of the application role that is to be revoked.            |
| `role_list` | The list of role names that are to be revoked.                     |

##### Examples

The following example revokes the `HRREP` role from user `SMAVRIS`:

    BEGIN
      XS_PRINCIPAL.REVOKE_ROLES('SMAVRIS','HRREP');
    END;

The following example revokes the `HRREP` and `HRMGR` roles from user `SMAVRIS`:

    DECLARE
      role_list XS$NAME_LIST;
    BEGIN
      role_list := XS$NAME_LIST('HRREP','HRMGR');
      SYS.XS_PRINCIPAL.REVOKE_ROLES('SMAVRIS', role_list);
    END;

The following example revokes all granted roles from user SMAVRIS:

    BEGIN
      SYS.XS_PRINCIPAL.REVOKE_ROLES('SMAVRIS');
    END;

#### 11.8.4.6 ADD_PROXY_USER Procedure

The `ADD_PROXY_USER` adds a target user for the specified application user. This allows the application user to proxy as the target user. There are two signatures for this procedure. The first signature allows you to specify a subset of roles of the target user using the `target_roles` parameter that are to be assigned to the proxy user. For the second signature there is no `target_roles` parameter, so all roles of the target user are assigned to the proxy user.

You need the `ALTER USER` system privilege to add or remove a proxy user.

##### Syntax

    ADD_PROXY_USER (
      target_user  IN VARCHAR2,
      proxy_user   IN VARCHAR2,
      target_roles IN XS$NAME_LIST);

    ADD_PROXY_USER (
      target_user  IN VARCHAR2,
      proxy_user   IN VARCHAR2);

##### Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                           |
|:---------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `target_user`  | The name of the target application user that can be proxied to.                                                                                                                                                                                                                                                                       |
| `proxy_user`   | The name of the proxy application user.                                                                                                                                                                                                                                                                                               |
| `target_roles` | A list of target user roles that can be proxied by the proxy user. This parameter is mandatory. If you pass an explicit `NULL` value, then this would be a case of configuring the proxy user without any role of the target user; otherwise, the `proxy_user` parameter uses the value you specify for the `target_roles` parameter. |

##### Examples

The following example enables user `DJONES` to proxy as target user `SMAVRIS`. The target roles granted to `DJONES` are `HRREP` and `HRMGR`.

    DECLARE
      pxy_roles XS$NAME_LIST;
    BEGIN
      pxy_roles := XS$NAME_LIST('HRREP','HRMGR');
      SYS.XS_PRINCIPAL.ADD_PROXY_USER('SMAVRIS','DJONES', pxy_roles);
    END;

The following example passes an explicit `NULL` value for the target role; in other words, it assigns no roles of the target user 'SMAVRIS' to the proxy user 'DJONES'.

    BEGIN
      SYS.XS_PRINCIPAL.ADD_PROXY_USER('SMAVRIS','DJONES', NULL);
    END;

The following example assigns all roles of target user 'SMAVRIS' to proxy user 'DJONES'.

    BEGIN
      SYS.XS_PRINCIPAL.ADD_PROXY_USER('SMAVRIS','DJONES');
    END;

#### 11.8.4.7 REMOVE_PROXY_USERS Procedure

The `REMOVE_PROXY_USERS` procedure disassociates one or all proxy users for a target application user. The associated proxy roles are automatically removed for the proxy users.

You need the `ALTER USER` system privilege to add or remove a proxy user.

##### Syntax

    REMOVE_PROXY_USERS (
      target_user  IN VARCHAR2);

    REMOVE_PROXY_USERS (
      target_user IN VARCHAR2,
      proxy_user  IN VARCHAR2);

##### Parameters

| Parameter     | Description                                                                     |
|:--------------|:--------------------------------------------------------------------------------|
| `target_user` | The target application user whose proxies are to be disassociated.              |
| `proxy_user`  | The proxy application user that needs to be disassociated from the target user. |

##### Examples

The following example removes all proxy users for target user `SMAVRIS`:

    BEGIN
      SYS.XS_PRINCIPAL.REMOVE_PROXY_USERS('SMAVRIS');
    END;

The following example disassociates the proxy user `DJONES` from the target user `SMAVRIS`:

    BEGIN
      SYS.XS_PRINCIPAL.REMOVE_PROXY_USERS('SMAVRIS','DJONES');
    END;

#### 11.8.4.8 ADD_PROXY_TO_DBUSER

The `ADD_PROXY_TO_DBUSER` adds the specified target proxy application user to the specified database user. The application user must be a direct logon user. This allows the application user to proxy as the target database user. By default, all roles assigned to the target user can be used by the proxy user. Similar to Oracle Database, the default roles of the target database users would be enabled after connection. Other roles assigned to the target database user can be set by using the `SET ROLE` statement.

You need the `ALTER USER` system privilege to add a proxy user to a database user.

##### Syntax

    ADD_PROXY_TO_DBUSER (
      database_user  IN VARCHAR2,
      proxy_user     IN VARCHAR2,
      is_external    IN BOOLEAN := FALSE);

##### Parameters

| Parameter       | Description                                                                                                             |
|:----------------|:------------------------------------------------------------------------------------------------------------------------|
| `database_user` | The name of the target database user that can be proxied to.                                                            |
| `proxy_user`    | The name of the proxy application user.                                                                                 |
| `is_external`   | The parameter to indicate whether the user is an external user or a regular Real Application Security application user. |

##### Examples

The following example enables application user `DJONES` to proxy as target database user `SMAVRIS`.

    BEGIN
      SYS.XS_PRINCIPAL.ADD_PROXY_TO_DBUSER('SMAVRIS','DJONES', TRUE);
    END;

#### 11.8.4.9 REMOVE_PROXY_FROM_DBUSER Procedure

The `REMOVE_PROXY_FROM_DBUSER` procedure disassociates a proxy application user from a database user. The associated proxy roles are automatically removed from the application user.

You need the `ALTER USER` system privilege to remove a proxy user from a database user.

##### Syntax

    REMOVE_PROXY_FROM_DBUSER (
      database_user IN VARCHAR2,
      proxy_user    IN VARCHAR2);

##### Parameters

| Parameter       | Description                                                                              |
|:----------------|:-----------------------------------------------------------------------------------------|
| `database_user` | The target database user whose proxies are to be disassociated.                          |
| `proxy_user`    | The proxy application user that needs to be disassociated from the target database user. |

##### Examples

The following example disassociates the proxy user `DJONES` from the target database user `SMAVRIS`:

    BEGIN
      SYS.XS_PRINCIPAL.REMOVE_PROXY_FROM_DBUSER('SMAVRIS','DJONES');
    END;

#### 11.8.4.10 SET_EFFECTIVE_DATES Procedure

The `SET_EFFECTIVE_DATES` procedure sets or modifies the effective dates for an application user or role. If the `start_date` and `end_date` values are specified as `NULL` by default, then the application user is not currently effective, so the session for the particular application user cannot be created.

You need the `ALTER USER` system privilege to run this procedure for an application user. You need the `ALTER ANY ROLE` system privilege to run this procedure for an application role.

##### Syntax

    SET_EFFECTIVE_DATES (
      principal         IN VARCHAR2,
      start_date        IN TIMESTAMP WITH TIME ZONE:= NULL,
      end_date          IN TIMESTAMP WITH TIME ZONE:= NULL);

##### Parameters

| Parameter    | Description                                                                       |
|:-------------|:----------------------------------------------------------------------------------|
| `principal`  | The name of the application user or role for which effective dates are to be set. |
| `start_date` | The start date of the effective dates period.                                     |
| `end_date`   | The end date of the effective dates period.                                       |

##### Examples

The following example sets the effective dates for user `DJONES`.

    DECLARE
      st_date TIMESTAMP WITH TIME ZONE;
      end_date TIMESTAMP WITH TIME ZONE;
    BEGIN
      st_date := TO_TIMESTAMP_TZ('2010-06-18 11:00:00 -5:00','YYYY-MM-DD HH:MI:SS
                                  TZH:TZM');
      end_date := TO_TIMESTAMP_Tz('2011-06-18 11:00:00 -5:00','YYYY-MM-DD HH:MI:SS
                                   TZH:TZM');
      SYS.XS_PRINCIPAL.SET_EFFECTIVE_DATES(principal=>'DJONES',
                                           start_date=>st_date,end_date=>end_date);
    END;

#### 11.8.4.11 SET_DYNAMIC_ROLE_DURATION Procedure

The `SET_DYNAMIC_ROLE_DURATION` procedure sets or modifies the duration for a dynamic application role. The duration is specified in minutes.

You need the `ALTER ANY ROLE` system privilege to modify a role.

##### Syntax

    SET_DYNAMIC_ROLE_DURATION (
      role      IN VARCHAR2,
      duration  IN PLS_INTEGER);

##### Parameters

| Parameter  | Description                                                                               |
|:-----------|:------------------------------------------------------------------------------------------|
| `role`     | The name of the dynamic application role.                                                 |
| `duration` | The duration of the dynamic application role in minutes. This cannot be a negative value. |

##### Examples

The following example sets the duration of the `reprole` dynamic application role to 60 minutes.

    BEGIN
      SYS.XS_PRINCIPAL.SET_DYNAMIC_ROLE_DURATION('reprole',60);
    END;

#### 11.8.4.12 SET_DYNAMIC_ROLE_SCOPE Procedure

The `SET_DYNAMIC_ROLE_SCOPE` procedure sets or modifies the scope of a dynamic application role. The session (`SESSION_SCOPE`) or request (`REQUEST_SCOPE`) scopes can be chosen.

You need the `ALTER ANY ROLE` system privilege to modify a role.

##### Syntax

    SET_DYNAMIC_ROLE_SCOPE (
      role      IN VARCHAR2,
      scope     IN PLS_INTEGER);

##### Parameters

| Parameter | Description                                                                                                                                |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| `role`    | The name of the dynamic application role.                                                                                                  |
| `scope`   | The scope of the dynamic application role to be set. The allowed values are `XS_PRINCIPAL.REQUEST_SCOPE `and `XS_PRINCIPAL.SESSION_SCOPE`. |

##### Examples

The following example sets the scope of the `reprole` dynamic application role to request scope:

    begin
      SYS.XS_PRINCIPAL.SET_DYNAMIC_ROLE_SCOPE('reprole',XS_PRINCIPAL.REQUEST_SCOPE);
    end;

#### 11.8.4.13 ENABLE_BY_DEFAULT Procedure

The `ENABLE_BY_DEFAULT` procedure enables or disables a regular application role.

If enabled, then the application role is automatically enabled for the principal to which it is granted. If disabled, then the privileges associated with the application role are not enabled even if the application role is granted to a principal.

You need the `ALTER ANY ROLE` system privilege to modify an application role.

##### Syntax

    ENABLE_BY_DEFAULT (
      role       IN VARCHAR2,
      enabled    IN BOOLEAN := TRUE);

##### Parameters

| Parameter | Description                                                                                                                                                  |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `role`    | The name of the regular application role.                                                                                                                    |
| `enabled` | The `enabled` attribute of the application role. Setting this to `TRUE` marks the application role as being enabled by default. The default value is `TRUE`. |

##### Examples

The following example sets the `enabled` attribute for the `HRREP` application role to `TRUE`:

    BEGIN
      SYS.XS_PRINCIPAL.ENABLE_BY_DEFAULT('HRREP',TRUE);
    END;

#### 11.8.4.14 ENABLE_ROLES_BY_DEFAULT Procedure

The `ENABLE_ROLES_BY_DEFAULT` procedure enables or disables all application roles that have been directly granted to an application user.

You need the `ALTER USER` system privilege to run this procedure for an application user.

##### Syntax

    ENABLE_ROLES_BY_DEFAULT (
      user       IN VARCHAR2,
      enabled    IN BOOLEAN := TRUE);

##### Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                       |
|:----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user`    | The name of the application user.                                                                                                                                                                                                                                                                                                                                                 |
| `enabled` | The `enabled` attribute for all application roles that have been directly granted to the application user.<br>Setting the enabled attribute to `TRUE` enables all directly granted application roles for the application user. The default value is `TRUE`.<br>Setting the enabled attribute to `FALSE` disables all directly granted application roles for the application user. |

##### Examples

The following example enables all directly granted roles for application user `SMAVRIS`:

    BEGIN
      SYS.XS_PRINCIPAL.ENABLE_ROLES_BY_DEFAULT('SMAVRIS',TRUE);
    END;

#### 11.8.4.15 SET_USER_SCHEMA Procedure

The `SET_USER_SCHEMA` procedure sets the database schema for an application user.

You need the `ALTER USER` system privilege to run this procedure for an application user.

##### Syntax

    SET_USER_SCHEMA (
      user        IN VARCHAR2,
      schema      IN VARCHAR2);

##### Parameters

| Parameter | Description                                                                                                            |
|:----------|:-----------------------------------------------------------------------------------------------------------------------|
| `user`    | The name of the application user.                                                                                      |
| `schema`  | The name of the database schema to be associated with the user. Setting this to `NULL` removes any schema association. |

##### Examples

The following example associates the `HR` schema with user `DJONES`.

    BEGIN
      SYS.XS_PRINCIPAL.SET_USER_SCHEMA('DJONES','HR');
    END;

#### 11.8.4.16 SET_GUID Procedure

The `SET_GUID` procedure sets the GUID for a principal. The principal must be an external user or role, and the current GUID must be `NULL`.

You need the `ALTER USER` system privilege to run this procedure for an application user. You need the `ALTER ANY ROLE` system privilege to run this procedure for an application role.

**Note:**

The `external_source` attribute for the user must have been set for SET_GUID to work.

##### Syntax

    SET_GUID (
      principal IN VARCHAR2,
      guid      IN RAW);

##### Parameters

| Parameter   | Description                             |
|:------------|:----------------------------------------|
| `principal` | The name of the external user or role.  |
| `guid`      | The GUID for the external user or role. |

##### Examples

The following example sets a GUID for user `Alex`:

    BEGIN
      SYS.XS_PRINCIPAL.SET_GUID('ALEX','7b6cb3a98f8a4e20ac31a37419cc7fa3');
    END;

#### 11.8.4.17 SET_ACL Procedure

##### Purpose

The `SET_ACL` procedure sets an ACL on the specified application user or dynamic role.

This procedure requires the caller to have the Real Application Security `PROVISION` privilege as the least privilege. Users with database `ALTER USER` privilege can also call the procedure if the principal is an application user. Users with the database role `ALTER ROLE` privilege can also call this procedure if the principal is a dynamic role.

##### Syntax

    SET_ACL(principal IN VARCHAR2,
            acl IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                         |
|:------------|:--------------------------------------------------------------------|
| `principal` | The application user or dynamic role to which the ACL is to be set. |
| `acl`       | The Real Application Security session privilege.                    |

##### Usage Notes

The ACLs must be created in the `SYS` schema.

An ACL set on an application user or dynamic role overrides a system-wide ACL.

The session privilege will be enforced as per the ACL set on Real Application Security application user or dynamic role involved in the session operation. For example, a create session operation requires the caller to have the `CREATE_SESSION` privilege in the ACL set on the Real Application Security application user or the attach operation with dynamic role requires the `ENABLE_DYNAMIC_ROLE` privilege in the ACLs to be set on the dynamic roles.

Principal-specific ACL grants take precedence over existing system-level session privilege grants. A privilege check is first done in the ACL associated with the principal and if it succeeds, the operation proceeds. If the privilege check finds deny, the operation fails with an insufficient privilege error. If neither grant nor deny is found, the check is done in the system ACL associated with the `SESSION_SC` security class and the operation succeeds or fails based on this privilege check result.

##### Examples

Example 11-1 Set the ACL Privilege CREATE_SESSION on Application User TEST1

The following example sets the ACL privilege `CREATE_SESSION` on the specified application user `test1`.

    BEGIN
      SYS.XS_PRINCIPAL.SET_ACL('test1','CREATE_SESSION');
    END;

#### 11.8.4.18 SET_PROFILE Procedure

The `SET_PROFILE` procedure sets the application user's profile. The profile is a set of resource limits and password parameters that restrict database usage and database instance resources for a Real Application Security application user. Both the application user and the profile must be existing entities.

The user executing this procedure must have the `ALTER_USER` privilege.

If a profile that is assigned to an application user is dropped using the cascade option, then the default profile would automatically become activated for that user.

##### Syntax

    SET_PROFILE (
      user     IN VARCHAR2,
      profile  IN VARCHAR2);

##### Parameters

| Parameter | Description                                                                                            |
|:----------|:-------------------------------------------------------------------------------------------------------|
| `user`    | The name of the Real Application Security application user. This must be an existing application user. |
| `profile` | The name of the profile.                                                                               |

##### Examples

The following example creates a profile named `prof` and then sets the profile named `prof` to an application user named `xsuser`.

    CREATE PROFILE prof LIMIT PASSWORD_REUSE_TIME 1/1440 PASSWORD_REUSE_MAX 3 PASSWORD_VERIFY_FUNCTION Verify_Pass;

    BEGIN
      SYS.XS_PRINCIPAL.SET_PROFILE('xsuser','prof');
    END;

#### 11.8.4.19 SET_USER_STATUS Procedure

The `SET_USER_STATUS` procedure sets or modifies the status of an application user account.

You need the `ALTER_USER` privilege to run this procedure for an application user.

##### Syntax

    SET_USER_STATUS (
      user        IN VARCHAR2,
      status      IN PLS_INTEGER);

##### Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user`    | The name of the user account whose status needs to be set or updated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `status`  | The new status of the Real Application Security user account. The status values can be divided into several classes:<br>• `ACTIVE` and `INACTIVE` - These two account status values will affect the user account's ability to create and attach to an application session.<br>• When set to `ACTIVE`, it allows the application user to use a direct login account to log into the database with a valid password. The application user is allowed to create and attach to an application session if the account has the required application privileges.<br>• When set to `INACTIVE`, the application user cannot use a direct login account to log into the database even with a valid password and can not create and attach to an application session.<br>• `UNLOCK`, `LOCKED`, or `EXPIRED` - These status values will be checked only for the direct login Real Application Security application user.<br>• When set to `UNLOCK`, it opens the application user account when the account is `LOCKED` and allows the application user to use a direct login account to log into the database with a valid password.<br>• When set to `LOCKED`, it locks the account of the application user. This means user connections using a direct login account will not be allowed even with a valid password. Provided that the user account is `ACTIVE`, a direct login will not succeed when the account is locked, but the user can create and attach to an application session.<br>• When set to `EXPIRED`, it expires the account of the application user. This means user connections using a direct login account will be allowed for valid passwords; however, the password must be changed at the time of logon.<br>• `PASSWORDEXPIRED` (Deprecated) - This status value is deprecated beginning with Release 1 (12.1.0.2).<br>If you try to pass any other value for the parameter `status`, an `ORA-46152: XS Security - invalid user status specified` error is returned. |

##### Examples

The following example sets the user status to `LOCKED` for user `DJONES`.

    BEGIN
      SYS.XS_PRINCIPAL.SET_USER_STATUS('DJONES',XS_PRINCIPAL.LOCKED);
    END;

#### 11.8.4.20 SET_PASSWORD Procedure

The `SET_PASSWORD` procedure sets or modifies the password for an application user account. When you use the `SET_PASSWORD` procedure, it creates a verifier for you based on the password and the `type` parameter and then inserts the verifier and the value of the `type` parameter into the dictionary table.

A direct login Real Application Security user can change his or her own password by providing its value using the `oldpass` parameter. If value of the old password is incorrect, then the failed login count is incremented with each attempt, returning an `ORA-28008: invalid old password` error. The new password is not set until the old supplied password is correct.

You need the `ALTER_USER` privilege to run this procedure for an application user or if you are changing the password of other Real Application Security users.

Native Real Application Security users synchronized from external ID stores are not allowed to change their own password. These users must change their password in the originating ID store. For example, if the Oracle Internet Directory 11g Release 1 (11.1.1) is the external store, for end-user self-service use the Oracle Identity Self Service interface provided by Oracle Identity Manager to manage your passwords. See [Fusion Middleware Performing Self Service Tasks with Oracle Identity Manager](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/dbfsg&id=password_self_service) for more information. You should contact your security administrator to determine if native Real Application Security users are synchronized from an external ID store, and if so, whether password management is provided in your directory server environment for end-user self-service.

The `SET_PASSWORD` operation and the SQL\*Plus `PASSWORD` command are both blocked on the logical standby database.

##### Syntax

    SET_PASSWORD (
      user      IN VARCHAR2,
      password  IN VARCHAR2,
      type      IN PLS_INTEGER := XS_SHA512,
      opassword IN VARCHAR2 :=NULL);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `user`      | The name of the application user account for which the password is to be set.                                                                                                                                              |
| `password`  | The password to be set.                                                                                                                                                                                                    |
| `type`      | The verifier type to be used for the password. The default value is `XS_SHA512`. The verifier type must be one of the following types:<br>`XS_SHA512, XS_SALTED_SHA1`                                                      |
| `opassword` | The old password. This parameter is required if the Real Application Security user is changing his or her own password. If not provided, then the user must have the required privilege to change his or her own password. |

##### Examples

The following example sets a password for application user `SMAVRIS`. It also specifies the `XS_SHA512` verifier type for the password.

    BEGIN
      SYS.XS_PRINCIPAL.SET_PASSWORD('SMAVRIS','2Hrd2Guess',XS_PRINCIPAL.XS_SHA512);
    END;

#### 11.8.4.21 SET_VERIFIER Procedure

The `SET_VERIFIER` procedure sets or modifies the verifier for an application user account. When you use the `SET_VERIFIER` procedure, the procedure directly inserts the verifier and the value of the `type` parameter into the dictionary table, `XS$VERIFIERS`. This enables administrators to migrate users into Real Application Security with knowledge of the verifier and not the password.

You need the `ALTER_USER` privilege to run this procedure for an application user.

The `SET_VERIFIER` operation and the SQL\*Plus `PASSWORD` command are both blocked on the logical standby database.

##### Syntax

    set_verifier (
      user      IN VARCHAR2,
      verifier  IN VARCHAR2,
      type      IN PLS_INTEGER := XS_SHA512);

##### Parameters

| Parameter  | Description                                                                                    |
|:-----------|:-----------------------------------------------------------------------------------------------|
| `user`     | The name of the application user for whom the verifier is set.                                 |
| `verifier` | A character string to be used as the verifier.                                                 |
| `type`     | The verifier type to be used. This can be one of the following:<br>`XS_SHA512, XS_SALTED_SHA1` |

##### Examples

Assume that a user by the name `LWUSER3` is created and the password is set with a verifier type of `XS_SALTED_SHA1`.

Next, query the view `DBA_XS_OBJECTS` to obtain the ID value for user `LWUSER3`.

    SQL> column name format A10;
    SQL> column owner format A6;
    SQL> select NAME, OWNER, ID, TYPE, STATUS from  DBA_XS_OBJECTS where NAME = 'LWUSER3';

    NAME       OWNER          ID TYPE               STATUS
    ---------- ------ ---------- ------------------ --------
    LWUSER3    SYS    2147493770 PRINCIPAL          VALID

Next, query the `XS$VERIFIERS` dictionary table for user `LWUSER3` whose ID is 2147493770.

    SQL> column user# format 9999999999;
    SQL> column type# format 99;
    SQL> column verifier format A62;
    SQL> select USER#, VERIFIER, TYPE# from XS$VERIFIERS where USER# = '2147493770';

          USER# VERIFIER                                                       TYPE#
    ----------- -------------------------------------------------------------- -----
     2147493770 S:14DC0F5ABB72FC869549B1F845C548E0BEF7B863A116DB24DFAE22F0501E     1

The value of the verifier includes its type as value “S” followed by a colon (:) to denote that it is a verifier type of `XS_SALTED_SHA1`, which is also indicated as being of type# 1.

Using the entire verifier value including “`S:`”, set the verifier for user `LWUSER3`.

    BEGIN
    SYS.XS_PRINCIPAL.SET_VERIFIER('lwuser3','S:14DC0F5ABB72FC869549B1F845C548E0BEF7B863A116DB24DFAE22F0501E',
    XS_PRINCIPAL.XS_SALTED_SHA1);
    END;
    /  2    3    4    5

    PL/SQL procedure successfully completed.

For this procedure to complete successfully, both the verifier value and its type must match the information in the `VERIFIER` column of the `XS$VERIFIERS` dictionary table for the user whose verifier is being set. Note that when you change the password for an application user, it automatically changes its verifier value with the option of changing its verifier type.

The previous example set the verifier to its same exact value to show the steps involved. You have the option to set the verifier for a password to any verifier value that displays for an application user when you query the `XS$VERIFIERS` dictionary table as long as the verifier value matches the verifier type that you set. For example, if you wanted to change the verifier value and the verifier type to `XS_SHA512`, do the following.

    SQL> BEGIN
    SYS.XS_PRINCIPAL.SET_VERIFIER('lwuser3','T:9BA95FEF2C2630A2BAACF2E7C5E41B0D50CDC7B0B6
    0C88AD4FE81F8155D002F99EEAF9D95477E4749870C67FDE870E154ED17809C359777F979E269010823FB
    981B2A998915EB1439FE3C6C1542A239C',
    XS_PRINCIPAL.XS_SHA512);
    END;
    /  2    3    4

    PL/SQL procedure successfully completed.

Note that this is the same verifier value and verifier type that was set for application user `LWUSER1` as shown in [Setting a Password Verifier for Direct Application User Accounts](configuring-application-users-and-application-roles.md).

#### 11.8.4.22 SET_DESCRIPTION Procedure

The `SET_DESCRIPTION` procedure is used to set the description for an application principal.

You need the `ALTER USER` system privilege to run this procedure for an application user. You need the `ALTER ANY ROLE` system privilege to run this procedure for an application role.

##### Syntax

    SET_DESCRIPTION (  principal   IN VARCHAR2,  description IN VARCHAR2);

##### Parameters

| Parameter     | Description                                                 |
|:--------------|:------------------------------------------------------------|
| `principal`   | The name of the principal for which the description is set. |
| `description` | A descriptive string about the principal.                   |

##### Examples

The following example sets a description for the application role `HRREP`:

    BEGIN
      SYS.XS_PRINCIPAL.SET_DESCRIPTION('HRREP','HR Representative role');
    END;

#### 11.8.4.23 DELETE_PRINCIPAL Procedure

The `DELETE_PRINCIPAL` procedure drops an application user or application role.

You need the `DROP USER` system privilege to run this procedure for an application user. You need the `DROP ANY ROLE` system privilege to run this procedure for an application role.

##### Syntax

    delete_principal (
      principal     IN VARCHAR2,
      delete_option IN PLS_INTEGER:=XS_ADMIN_UTIL.DEFAULT_OPTION);

##### Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `principal`     | The name of the application user or application role that is to be deleted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `delete_option` | The delete option to use. The following options are available:<br>• `DEFAULT_OPTION:`<br>• The default option allows deleting a principal only if it is not referenced elsewhere. If there are other entities that reference the principal, then the principal cannot be deleted.<br>• For example, the delete operation fails if you try to delete an application role that is granted to a principal.<br>• `CASCADE_OPTION`:<br>• The cascade option deletes the application user or application role together with any references to it.The user deleting the application user or application role must have privileges to delete these references as well.<br>• `ALLOW_INCONSISTENCIES_OPTION: `<br>• The allow inconsistencies option lets you delete the entity even if other entities have late binding references to it. If the entity is part of an early dependency, then the delete fails and an error is raised. |

##### Examples

The following example deletes the user `SMAVRIS` using the `DEFAULT_OPTION`:

    BEGIN
      SYS.XS_PRINCIPAL.DELETE_PRINCIPAL('SMAVRIS');
    END;
