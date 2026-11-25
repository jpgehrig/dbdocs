## 9 Oracle Database Real Application Security Data Dictionary Views

This chapter describes the data dictionary views provided with Oracle Database Real Application Security.

Table 9-1 summarizes these views. For additional data dictionary views related to Oracle Real Application Security, see [Oracle Database Reference](../refrn/DBA_XS_AUDIT_POLICY_OPTIONS.md).

Table 9-1 Oracle Database Real Application Security Data Dictionary Views

| Data Dictionary View          | Summary Description                                                                                                                                                                                                                                                                                                                                                                     |
|:------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| DBA_XS_OBJECTS                | Displays all Real Application Security objects                                                                                                                                                                                                                                                                                                                                          |
| DBA_XS_PRINCIPALS             | Displays all application users and application roles                                                                                                                                                                                                                                                                                                                                    |
| DBA_XS_EXTERNAL_PRINCIPALS    | Displays all external application users and application roles                                                                                                                                                                                                                                                                                                                           |
| DBA_XS_USERS                  | Displays all application users                                                                                                                                                                                                                                                                                                                                                          |
| USER_XS_USERS                 | Displays the application users own account information                                                                                                                                                                                                                                                                                                                                  |
| USER_XS_PASSWORD_LIMITS       | Displays password limits for the currently logged on application user                                                                                                                                                                                                                                                                                                                   |
| DBA_XS_ROLES                  | Displays all application roles                                                                                                                                                                                                                                                                                                                                                          |
| DBA_XS_DYNAMIC_ROLES          | Displays all dynamic application roles                                                                                                                                                                                                                                                                                                                                                  |
| DBA_XS_PROXY_ROLES            | Displays all proxy application roles                                                                                                                                                                                                                                                                                                                                                    |
| DBA_XS_ROLE_GRANTS            | Displays all Real Application Security application role grants                                                                                                                                                                                                                                                                                                                          |
| DBA_XS_PRIVILEGES             | Lists all Real Application Security application privileges defined in the database.                                                                                                                                                                                                                                                                                                     |
| USER_XS_PRIVILEGES            | Lists application privileges contained in security classes owned by the current user                                                                                                                                                                                                                                                                                                    |
| DBA_XS_IMPLIED_PRIVILEGES     | Lists all the Real Application Security implied application privileges defined in the database                                                                                                                                                                                                                                                                                          |
| USER_XS_IMPLIED_PRIVILEGES    | Lists all the implied application privileges contained in security classes owned by the current user                                                                                                                                                                                                                                                                                    |
| DBA_XS_SECURITY_CLASSES       | Lists all security classes defined in the database                                                                                                                                                                                                                                                                                                                                      |
| USER_XS_SECURITY_CLASSES      | Lists all security classes owned by the current application user                                                                                                                                                                                                                                                                                                                        |
| DBA_XS_SECURITY_CLASS_DEP     | Lists the dependencies between security classes.                                                                                                                                                                                                                                                                                                                                        |
| USER_XS_SECURITY_CLASS_DEP    | Lists the parent security classes for the dependent security classes owned by the current user.                                                                                                                                                                                                                                                                                         |
| DBA_XS_ACLS                   | Lists all existing ACLs                                                                                                                                                                                                                                                                                                                                                                 |
| USER_XS_ACLS                  | lists all ACLs owned by the current user                                                                                                                                                                                                                                                                                                                                                |
| DBA_XS_ACES                   | Lists all the Access Control Entries (ACEs)                                                                                                                                                                                                                                                                                                                                             |
| USER_XS_ACES                  | Lists all the ACEs from the ACLs owned by the current user                                                                                                                                                                                                                                                                                                                              |
| DBA_XS_POLICIES               | Lists all the data security policies                                                                                                                                                                                                                                                                                                                                                    |
| USER_XS_POLICIES              | Lists all the data security policies owned by the current application user                                                                                                                                                                                                                                                                                                              |
| DBA_XS_REALM_CONSTRAINTS      | Lists all Real Application Security realms                                                                                                                                                                                                                                                                                                                                              |
| USER_XS_REALM_CONSTRAINTS     | Lists all Real Application Security realms owned by the current user                                                                                                                                                                                                                                                                                                                    |
| DBA_XS_INHERITED_REALMS       | Lists all Real Application Security inherited realms                                                                                                                                                                                                                                                                                                                                    |
| USER_XS_INHERITED_REALMS      | Lists all Real Application Security inherited realms owned by the current user                                                                                                                                                                                                                                                                                                          |
| DBA_XS_ACL_PARAMETERS         | Lists all Real Application Security ACL parameters                                                                                                                                                                                                                                                                                                                                      |
| USER_XS_ACL_PARAMETERS        | Lists all Real Application Security ACL parameters defined in data security policies owned by the current user                                                                                                                                                                                                                                                                          |
| DBA_XS_COLUMN_CONSTRAINTS     | Lists all Real Application Security column constraints                                                                                                                                                                                                                                                                                                                                  |
| USER_XS_COLUMN_CONSTRAINTS    | Lists all Real Application Security column constraints owned by the current user                                                                                                                                                                                                                                                                                                        |
| DBA_XS_APPLIED_POLICIES       | Displays all database objects on which Real Application Security data security policies are enabled                                                                                                                                                                                                                                                                                     |
| DBA_XS_MODIFIED_POLICIES      | Displays all database objects on which Real Application Security data security policies are modified                                                                                                                                                                                                                                                                                    |
| DBA_XS_SESSIONS               | Lists all application sessions in the database                                                                                                                                                                                                                                                                                                                                          |
| DBA_XS_ACTIVE_SESSIONS        | Lists all attached application sessions in the database                                                                                                                                                                                                                                                                                                                                 |
| DBA_XS_SESSION_ROLES          | Lists application roles enabled in application sessions                                                                                                                                                                                                                                                                                                                                 |
| DBA_XS_SESSION_NS_ATTRIBUTES  | Displays namespace attributes across application sessions as of last saved state                                                                                                                                                                                                                                                                                                        |
| DBA_XS_NS_TEMPLATES           | Describes all Real Application Security namespace templates                                                                                                                                                                                                                                                                                                                             |
| DBA_XS_NS_TEMPLATE_ATTRIBUTES | Describes all namespace templates together with their attribute details                                                                                                                                                                                                                                                                                                                 |
| ALL_XDS_ACL_REFRESH           | Displays all static ACL refresh settings for tables that are accessible to the application user.                                                                                                                                                                                                                                                                                        |
| ALL_XDS_ACL_REFSTAT           | Displays all static ACL refresh job status history that has been done for tables accessible to the application user.                                                                                                                                                                                                                                                                    |
| ALL_XDS_LATEST_ACL_REFSTAT    | Displays the ACL refreshjob status for the most recent refreshment job for each table accessible to the application user.                                                                                                                                                                                                                                                               |
| DBA_XDS_ACL_REFRESH           | Displays all static ACL refresh settings in the database.                                                                                                                                                                                                                                                                                                                               |
| DBA_XDS_ACL_REFSTAT           | Displays all static ACL refresh job status history that has been done in the database                                                                                                                                                                                                                                                                                                   |
| DBA_XDS_LATEST_ACL_REFSTAT    | Displays the ACL refresh job status for the most recent refreshment job for each table in the database                                                                                                                                                                                                                                                                                  |
| USER_XDS_ACL_REFRESH          | Displays all static ACL refresh settings for tables that are owned by the user.                                                                                                                                                                                                                                                                                                         |
| USER_XDS_ACL_REFSTAT          | Displays all static ACL refresh job status history that has been done for tables owned by the user.                                                                                                                                                                                                                                                                                     |
| USER_XDS_LATEST_ACL_REFSTAT   | Displays the ACL refresh job status for the most recent refreshment job for each table owned by the user.                                                                                                                                                                                                                                                                               |
| V\$XS_SESSION_NS_ATTRIBUTES   | Displays information about the namespaces and attributes in the current application session.                                                                                                                                                                                                                                                                                            |
| V\$XS_SESSION_ROLES           | Displays all enabled application roles in the current application session.                                                                                                                                                                                                                                                                                                              |
| `DBA_XS_AUDIT_POLICY_OPTIONS` | Describes the auditing options that were defined for Real Application Security unified audit policies. See [Oracle Database Reference](../refrn/DBA_XS_AUDIT_POLICY_OPTIONS.md) for more information. For information about unified auditing in an Oracle Database Real Application Security environment, see [Oracle Database Security Guide](../dbseg/configuring-audit-policies.md). |
| `DBA_XS_AUDIT_TRAIL`          | Provides detailed information about Real Application Security that were audited. See [Oracle Database Reference](../refrn/DBA_XS_AUDIT_TRAIL.md) for more information. For information about unified auditing in an Oracle Database Real Application Security environment, see [Oracle Database Security Guide](../dbseg/configuring-audit-policies.md).                                |
| `DBA_XS_ENB_AUDIT_POLICIES`   | Lists users for whom Real Application Security unified audit polices are enabled. See [Oracle Database Reference](../refrn/DBA_XS_ENB_AUDIT_POLICIES.md) for more information. For information about unified auditing in an Oracle Database Real Application Security environment, see [Oracle Database Security Guide](../dbseg/configuring-audit-policies.md).                        |

This section describes the following Oracle Database Real Application Security data dictionary views:

### 9.1 DBA_XS_OBJECTS

The `DBA_XS_OBJECTS` data dictionary view lists all the existing Real Application Security objects in the database.

#### Related Views

- DBA_XS_PRINCIPALS

- DBA_XS_SECURITY_CLASSES

- DBA_XS_ACLS

- DBA_XS_POLICIES

- DBA_XS_NS_TEMPLATES

| Column   | Datatype        | NULL       | Description                                                                                                                                                                                             |
|:---------|:----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`   | `VARCHAR2(128)` |            | Name of the object                                                                                                                                                                                      |
| `OWNER`  | `VARCHAR2(128)` |            | Owner of the object                                                                                                                                                                                     |
| `ID`     | `NUMBER`        | `NOT NULL` | Identifier number for the object                                                                                                                                                                        |
| `TYPE`   | `VARCHAR2(18)`  |            | Type of the object. Possible values are:<br>• `PRINCIPAL` (Application User/Application Role)<br>• `SECURITY CLASS`<br>• `ACL`<br>• `PRIVILEGE`<br>• `DATA SECURITY` (Policy)<br>• `NAMESPACE TEMPLATE` |
| `STATUS` | `VARCHAR2(8)`   |            | Status of the object. Possible values are:<br>• `INVALID`<br>• `VALID`<br>• `EXTERNAL`                                                                                                                  |

### 9.2 DBA_XS_PRINCIPALS

The `DBA_XS_PRINCIPALS` data dictionary view describes all the existing application users and application roles in the database.

#### Related Views

- DBA_XS_USERS

- DBA_XS_ROLES

- DBA_XS_DYNAMIC_ROLES

- DBA_XS_PROXY_ROLES

- DBA_XS_EXTERNAL_PRINCIPALS

| Column            | Datatype         | NULL | Description                                                                       |
|:------------------|:-----------------|:-----|:----------------------------------------------------------------------------------|
| `NAME`            | `VARCHAR2(128)`  |      | Name of the principal (application user or application role)                      |
| `GUID`            | `RAW(16)`        |      | Globally unique identifier for the principal                                      |
| `TYPE`            | `VARCHAR2(12)`   |      | Type of the principal. Possible values are:<br>• USER<br>• ROLE<br>• DYNAMIC ROLE |
| `EXTERNAL_SOURCE` | `VARCHAR2(128)`  |      | External source of the principal                                                  |
| `DESCRIPTION`     | `VARCHAR2(4000)` |      | Description of the principal                                                      |

### 9.3 DBA_XS_EXTERNAL_PRINCIPALS

The `DBA_XS_EXTERNAL_PRINCIPALS` data dictionary view lists all the external application users and application roles.

#### Related Views

- DBA_XS_PRINCIPALS

- DBA_XS_USERS

- DBA_XS_ROLES

- DBA_XS_DYNAMIC_ROLES

- DBA_XS_PROXY_ROLES

| Column | Datatype        | NULL | Description                    |
|:-------|:----------------|:-----|:-------------------------------|
| `NAME` | `VARCHAR2(128)` |      | Name of the external principal |

### 9.4 DBA_XS_USERS

The `DBA_XS_USERS` data dictionary view describes all existing application users defined in the database.

#### Related Views

- DBA_XS_PRINCIPALS

- USER_XS_USERS

- DBA_XS_ROLES

- DBA_XS_DYNAMIC_ROLES

- DBA_XS_PROXY_ROLES

| Column                  | Datatype                      | NULL       | Description                                                                                                                          |
|:------------------------|:------------------------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`                  | `VARCHAR2(128)`               |            | Name of the application user                                                                                                         |
| `GUID`                  | `RAW(16)`                     |            | Globally unique identifier for the application user                                                                                  |
| `EXTERNAL_SOURCE`       | `VARCHAR2(128)`               |            | External Source of application users, such as LDAP                                                                                   |
| `ROLES_DEFAULT_ENABLED` | `VARCHAR2(3)`                 |            | Indicates whether all the application roles granted to the application user are enabled by default. Valid values are `YES` and `NO`. |
| `STATUS`                | `VARCHAR2(8)`                 |            | Status of the application user. Valid values are `ACTIVE` and `INACTIVE`.                                                            |
| `ACCOUNT_STATUS`        | `VARCHAR2(32)`                | `NOT NULL` | Direct login password policy account status of the user. Indicates whether the account is locked, expired, or unlocked.              |
| `LOCK_DATE`             | `DATE`                        |            | The date the account became locked for the direct login user                                                                         |
| `EXPIRY_DATE`           | `DATE`                        |            | The date the passward became expired for the direct login user                                                                       |
| `PROFILE`               | `VARCHAR2(128)`               |            | The name of the database profile associated with the application user                                                                |
| `SCHEMA`                | `VARCHAR2(128)`               |            | Application user schema                                                                                                              |
| `START_DATE`            | `TIMESTAMP(6) WITH TIME ZONE` |            | Effective start date for the user                                                                                                    |
| `END_DATE`              | `TIMESTAMP(6) WITH TIME ZONE` |            | Effective end date for the user                                                                                                      |
| `DIRECT_LOGON_USER`     | `VARCHAR2(3)`                 |            | Indicates whether this user has direct logon capability                                                                              |
| `VERIFIER_TYPE`         | `VARCHAR2(11)`                |            | Type of the verifier assigned to the direct logon user. Only XS\_`SHA512` and `XS_SALTED`\_`SHA1 `are allowed.)                      |
| `ACL`                   | `VARCHAR2(128)`               |            | The Real Application Security session privilege.                                                                                     |
| `DESCRIPTION`           | `VARCHAR2(4000)`              |            | Description of the application user                                                                                                  |

### 9.5 USER_XS_USERS

The `USER_XS_USERS` data dictionary view describes the current application users own account information.

#### Related Views

- DBA_XS_USERS

- DBA_XS_PRINCIPALS

- DBA_XS_ROLES

- DBA_XS_DYNAMIC_ROLES

- DBA_XS_PROXY_ROLES

| Column              | Datatype         | NULL       | Description                                                                                                                                                             |
|:--------------------|:-----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`              | `VARCHAR2(128)`  |            | Name of the current application user                                                                                                                                    |
| `STATUS`            | `VARCHAR2(8)`    |            | Status of the current application user. Valid values are `ACTIVE` and `INACTIVE` only.                                                                                  |
| `ACCOUNT_STATUS`    | `VARCHAR2(32)`   | `NOT NULL` | Direct login password policy account status of the current user. Valid values are `UNLOCK`, `LOCKED`, and `EXPIRED`. `UNLOCK` means the current user's account is open. |
| `LOCK_DATE`         | `DATE`           |            | The date the account became locked for the direct login session for the current user                                                                                    |
| `EXPIRY_DATE`       | `DATE`           |            | The date the passward became expired or the direct login session for the current user                                                                                   |
| `DIRECT_LOGON_USER` | `VARCHAR2(3)`    |            | Indicates whether this user has direct logon capability                                                                                                                 |
| `DESCRIPTION`       | `VARCHAR2(4000)` |            | Description of the application user                                                                                                                                     |

### 9.6 USER_XS_PASSWORD_LIMITS

The `USER_XS_PASSWORD_LIMITS` data dictionary view describes the password limits for the currently logged on application user. The DBA can query this view to check the limits for any direct login user.

#### Related Views

| Column          | Datatype        | NULL       | Description                       |
|:----------------|:----------------|:-----------|:----------------------------------|
| `RESOURCE_NAME` | `VARCHAR2(32)`  | `NOT NULL` | Name of the password resource     |
| `LIMIT`         | `VARCHAR2(128)` |            | The limit placed on this resource |

### 9.7 DBA_XS_ROLES

The `DBA_XS_ROLES` data dictionary view describes all existing application roles in the database.

#### Related Views

- DBA_XS_PRINCIPALS

- DBA_XS_USERS

- DBA_XS_DYNAMIC_ROLES

- DBA_XS_PROXY_ROLES

- DBA_XS_ROLE_GRANTS

| Column            | Datatype                      | NULL | Description                                                                         |
|:------------------|:------------------------------|:-----|:------------------------------------------------------------------------------------|
| `NAME`            | `VARCHAR2(128)`               |      | Name of the application role                                                        |
| `GUID`            | `RAW(16)`                     |      | Globally unique identifier for the application role                                 |
| `EXTERNAL_SOURCE` | `VARCHAR2(128)`               |      | External Source of the application role, such as LDAP                               |
| `DEFAULT_ENABLED` | `VARCHAR(3)`                  |      | Whether or not the application role is enabled by default. Values can be YES or NO. |
| `START_DATE`      | `TIMESTAMP(6) WITH TIME ZONE` |      | Start date from which the application role is valid                                 |
| `END_DATE`        | `TIMESTAMP(6) WITH TIME ZONE` |      | End date until which the application role is valid                                  |
| `DESCRIPTION`     | `VARCHAR2(4000)`              |      | Description of the application role                                                 |

### 9.8 DBA_XS_DYNAMIC_ROLES

The `DBA_XS_DYNAMIC_ROLES` data dictionary view describes all existing dynamic application roles in the database.

#### Related Views

- DBA_XS_PRINCIPALS

- DBA_XS_USERS

- DBA_XS_ROLES

- DBA_XS_ROLE_GRANTS

| Column           | Datatype         | NULL | Description                                                                                          |
|:-----------------|:-----------------|:-----|:-----------------------------------------------------------------------------------------------------|
| `NAME`           | `VARCHAR2(128)`  |      | Name of the dynamic application role                                                                 |
| `GUID`           | `RAW(16)`        |      | Globally unique identifier for the dynamic application role                                          |
| `DURATION`       | `NUMBER`         |      | Duration (in minutes) for which the role has been active                                             |
| `SYSTEM_DEFINED` | `VARCHAR2(3)`    |      | Indicates whether the application role is a system-defined role. Possible values are `YES` and `NO`. |
| `SCOPE`          | `VARCHAR2(7)`    |      | Scope of the application role. Possible values are `SESSION` and `REQUEST`.                          |
| `ACL`            | `VARCHAR2(128)`  |      | The Real Application Security session privilege.                                                     |
| `DESCRIPTION`    | `VARCHAR2(4000)` |      | Description of the dynamic application role.                                                         |

### 9.9 DBA_XS_PROXY_ROLES

The `DBA_XS_PROXY_ROLES` data dictionary view describes all Real Application Security proxy application role grants.

#### Related Views

- DBA_XS_PRINCIPALS

- DBA_XS_USERS

- DBA_XS_ROLES

- DBA_XS_DYNAMIC_ROLES

- DBA_XS_ROLE_GRANTS

| Column         | Datatype        | NULL | Description                         |
|:---------------|:----------------|:-----|:------------------------------------|
| `PROXY_``USER` | `VARCHAR2(128)` |      | Name of the proxy application user  |
| `TARGET_USER`  | `VARCHAR2(128)` |      | Name of the target application user |
| `TARGET_ROLE`  | `VARCHAR2(128)` |      | Name of the target application role |

### 9.10 DBA_XS_ROLE_GRANTS

The `DBA_XS_ROLE_GRANTS` data dictionary view describes all Real Application Security application role grants.

#### Related Views

- DBA_XS_PRINCIPALS

- DBA_XS_USERS

- DBA_XS_ROLES

- DBA_XS_DYNAMIC_ROLES

- DBA_XS_PROXY_ROLES

| Column              | Datatype                      | NULL | Description                                                    |
|:--------------------|:------------------------------|:-----|:---------------------------------------------------------------|
| `GRANTEE`           | `VARCHAR2(128)`               |      | Name of the principal to which the application role is granted |
| `GRANTED_ROLE`      | `VARCHAR2(128)`               |      | Name of the granted application role                           |
| `GRANTED_ROLE_TYPE` | `VARCHAR2(11)`                |      | Name of the granted role                                       |
| `START_DATE`        | `TIMESTAMP(6) WITH TIME ZONE` |      | Start date from which the application role grant is valid      |
| `END_DATE`          | `TIMESTAMP(6) WITH TIME ZONE` |      | End date until which the application role grant is valid       |

### 9.11 DBA_XS_PRIVILEGES

The `DBA_XS_PRIVILEGES` data dictionary view lists all the Real Application Security application privileges defined in the database.

#### Related Views

- USER_XS_PRIVILEGES

- DBA_XS_IMPLIED_PRIVILEGES

- USER_XS_IMPLIED_PRIVILEGES

- DBA_XS_SECURITY_CLASSES

- ALL_XS_PRIVILEGES

| Column                 | Datatype         | NULL | Description                                                         |
|:-----------------------|:-----------------|:-----|:--------------------------------------------------------------------|
| `NAME`                 | `VARCHAR2(128)`  |      | Name of the application privilege                                   |
| `SECURITY_CLASS`       | `VARCHAR2(128`)  |      | Name of the security class that contains the application privilege  |
| `SECURITY_CLASS_OWNER` | `VARCHAR2(128)`  |      | Owner of the security class that contains the application privilege |
| `DESCRIPTION`          | `VARCHAR2(4000)` |      | Description of the application privilege.                           |

### 9.12 USER_XS_PRIVILEGES

The `USER_XS_PRIVILEGES` data dictionary view lists the application privileges contained in security classes owned by the current user.

#### Related Views

- DBA_XS_PRIVILEGES

- DBA_XS_IMPLIED_PRIVILEGES

- USER_XS_IMPLIED_PRIVILEGES

- USER_XS_SECURITY_CLASSES

- ALL_XS_PRIVILEGES

- ALL_XS_IMPLIED_PRIVILEGES

| Column           | Datatype         | NULL | Description                                                        |
|:-----------------|:-----------------|:-----|:-------------------------------------------------------------------|
| `NAME`           | `VARCHAR2(128)`  |      | Name of the application privilege                                  |
| `SECURITY_CLASS` | `VARCHAR2(128`)  |      | Name of the security class that contains the application privilege |
| `DESCRIPTION`    | `VARCHAR2(4000)` |      | Description of the application privilege.                          |

### 9.13 ALL_XS_PRIVILEGES

The `ALL_XS_PRIVILEGES` data dictionary view lists all the Real Application Security application privileges scoped by the security classes accessible to the current user.

#### Related Views

- USER_XS_PRIVILEGES

- DBA_XS_IMPLIED_PRIVILEGES

- USER_XS_IMPLIED_PRIVILEGES

- DBA_XS_SECURITY_CLASSES

| Column                 | Datatype         | NULL | Description                                                         |
|:-----------------------|:-----------------|:-----|:--------------------------------------------------------------------|
| `NAME`                 | `VARCHAR2(128)`  |      | Name of the application privilege                                   |
| `SECURITY_CLASS`       | `VARCHAR2(128`)  |      | Name of the security class that contains the application privilege  |
| `SECURITY_CLASS_OWNER` | `VARCHAR2(128)`  |      | Owner of the security class that contains the application privilege |
| `DESCRIPTION`          | `VARCHAR2(4000)` |      | Description of the application privilege.                           |

### 9.14 DBA_XS_IMPLIED_PRIVILEGES

The `DBA_XS_IMPLIED_PRIVILEGES` data dictionary view lists all the Real Application Security implied application privileges defined in the database.

#### Related Views

- DBA_XS_PRIVILEGES

- USER_XS_PRIVILEGES

- USER_XS_IMPLIED_PRIVILEGES

- DBA_XS_SECURITY_CLASSES

- ALL_XS_PRIVILEGES

- ALL_XS_IMPLIED_PRIVILEGES

- ALL_XS_SECURITY_CLASSES

| Column                 | Datatype        | NULL | Description                                                                    |
|:-----------------------|:----------------|:-----|:-------------------------------------------------------------------------------|
| `PRIVILEGE`            | `VARCHAR2(128)` |      | Name of the application privilege containing the implied application privilege |
| `IMPLIED_PRIVILEGE`    | `VARCHAR2(128)` |      | Name of the implied application privilege                                      |
| `SECURITY_CLASS`       | `VARCHAR2(128`) |      | Name of the security class that contains the application privilege             |
| `SECURITY_CLASS_OWNER` | `VARCHAR2(128)` |      | Owner of the security class that contains the application privilege            |

### 9.15 USER_XS_IMPLIED_PRIVILEGES

The `USER_XS_IMPLIED_PRIVILEGES` data dictionary view lists the implied application privileges contained in security classes owned by the current user.

#### Related Views

- DBA_XS_PRIVILEGES

- USER_XS_PRIVILEGES

- DBA_XS_IMPLIED_PRIVILEGES

- USER_XS_SECURITY_CLASSES

- ALL_XS_PRIVILEGES

- ALL_XS_IMPLIED_PRIVILEGES

- ALL_XS_SECURITY_CLASSES

| Column              | Datatype        | NULL | Description                                                                    |
|:--------------------|:----------------|:-----|:-------------------------------------------------------------------------------|
| `PRIVILEGE`         | `VARCHAR2(128)` |      | Name of the application privilege containing the implied application privilege |
| `IMPLIED_PRIVILEGE` | `VARCHAR2(128)` |      | Name of the implied application privilege                                      |
| `SECURITY_CLASS`    | `VARCHAR2(128`) |      | Name of the security class that contains the application privilege             |

### 9.16 ALL_XS_IMPLIED_PRIVILEGES

The `ALL_XS_IMPLIED_PRIVILEGES` data dictionary view lists all the Real Application Security implied application privileges scoped by the security classes accessible to the current user.

#### Related Views

- DBA_XS_PRIVILEGES

- USER_XS_PRIVILEGES

- USER_XS_IMPLIED_PRIVILEGES

- DBA_XS_SECURITY_CLASSES

| Column                 | Datatype        | NULL | Description                                                                    |
|:-----------------------|:----------------|:-----|:-------------------------------------------------------------------------------|
| `PRIVILEGE`            | `VARCHAR2(128)` |      | Name of the application privilege containing the implied application privilege |
| `IMPLIED_PRIVILEGE`    | `VARCHAR2(128)` |      | Name of the implied application privilege                                      |
| `SECURITY_CLASS`       | `VARCHAR2(128`) |      | Name of the security class that contains the application privilege             |
| `SECURITY_CLASS_OWNER` | `VARCHAR2(128)` |      | Owner of the security class that contains the application privilege            |

### 9.17 DBA_XS_PRIVILEGE_GRANTS

The `DBA_XS_PRIVILEGE_GRANTS` data dictionary view lists all the Real Application Security system or schema level privilege grants defined in the database.

#### Related Views

- USER_XS_PRIVILEGES

- DBA_XS_PRIVILEGES

| Column         | Datatype        | NULL | Description                                                             |
|:---------------|:----------------|:-----|:------------------------------------------------------------------------|
| `PRIVILEGE`    | `VARCHAR2(128)` |      | Name of the application privilege                                       |
| `GRANTEE`      | `VARCHAR2(128`) |      | Name of the user to whom access was granted                             |
| `GRANTEE_TYPE` | `VARCHAR2(5)`   |      | Type of the grantee: Database or Real Application Security user or role |
| `SCHEMA`       | `VARCHAR2(128)` |      | Schema of the privilege                                                 |

### 9.18 DBA_XS_SECURITY_CLASSES

The `DBA_XS_SECURITY_CLASSES` data dictionary view lists all Real Application Security security classes defined in the database.

#### Related Views

- USER_XS_SECURITY_CLASSES

- DBA_XS_SECURITY_CLASS_DEP

- USER_XS_SECURITY_CLASS_DEP

- ALL_XS_SECURITY_CLASSES

- ALL_XS_SECURITY_CLASS_DEP

| Column        | Datatype         | NULL | Description                        |
|:--------------|:-----------------|:-----|:-----------------------------------|
| `NAME`        | `VARCHAR2(128)`  |      | Name of the security class.        |
| `OWNER`       | `VARCHAR2(128)`  |      | Owner of the security class.       |
| `DESCRIPTION` | `VARCHAR2(4000)` |      | Description of the security class. |

### 9.19 USER_XS_SECURITY_CLASSES

The `USER_XS_SECURITY_CLASSES` data dictionary view lists all Real Application Security security classes owned by the current user.

#### Related Views

- DBA_XS_SECURITY_CLASSES

- DBA_XS_SECURITY_CLASS_DEP

- USER_XS_SECURITY_CLASS_DEP

- ALL_XS_SECURITY_CLASS_DEP

- ALL_XS_SECURITY_CLASSES

| Column        | Datatype         | NULL | Description                        |
|:--------------|:-----------------|:-----|:-----------------------------------|
| `NAME`        | `VARCHAR2(128)`  |      | Name of the security class.        |
| `DESCRIPTION` | `VARCHAR2(4000)` |      | Description of the security class. |

### 9.20 ALL_XS_SECURITY_CLASSES

The `ALL_XS_SECURITY_CLASSES` data dictionary view lists all Real Application Security security classes accessible to the current user.

#### Related Views

- USER_XS_SECURITY_CLASSES

- DBA_XS_SECURITY_CLASS_DEP

- USER_XS_SECURITY_CLASS_DEP

- ALL_XS_SECURITY_CLASS_DEP

| Column        | Datatype         | NULL | Description                        |
|:--------------|:-----------------|:-----|:-----------------------------------|
| `NAME`        | `VARCHAR2(128)`  |      | Name of the security class.        |
| `OWNER`       | `VARCHAR2(128)`  |      | Owner of the security class.       |
| `DESCRIPTION` | `VARCHAR2(4000)` |      | Description of the security class. |

### 9.21 DBA_XS_SECURITY_CLASS_DEP

The `DBA_XS_SECURITY_CLASS_DEP` data dictionary view lists the dependencies between all security classes defined in the database.

#### Related Views

- USER_XS_SECURITY_CLASS_DEP

- DBA_XS_SECURITY_CLASSES

- USER_XS_SECURITY_CLASSES

- ALL_XS_SECURITY_CLASS_DEP

- ALL_XS_SECURITY_CLASSES

| Column           | Datatype        | NULL | Description                        |
|:-----------------|:----------------|:-----|:-----------------------------------|
| `SECURITY_CLASS` | `VARCHAR2(128`) |      | Name of the security class         |
| `OWNER`          | `VARCHAR2(128)` |      | Owner of the security class        |
| `PARENT`         | `VARCHAR2(128)` |      | Name of the parent security class  |
| `PARENT_OWNER`   | `VARCHAR2(128)` |      | Owner of the parent security class |

### 9.22 USER_XS_SECURITY_CLASS_DEP

The `USER_XS_SECURITY_CLASS_DEP` data dictionary view lists the parent security classes for the dependent security classes owned by the current user.

#### Related Views

- DBA_XS_SECURITY_CLASS_DEP

- DBA_XS_SECURITY_CLASSES

- USER_XS_SECURITY_CLASSES

- ALL_XS_SECURITY_CLASS_DEP

- ALL_XS_SECURITY_CLASSES

| Column           | Datatype        | NULL | Description                        |
|:-----------------|:----------------|:-----|:-----------------------------------|
| `SECURITY_CLASS` | `VARCHAR2(128`) |      | Name of the security class         |
| `PARENT`         | `VARCHAR2(128)` |      | Name of the parent security class  |
| `PARENT_OWNER`   | `VARCHAR2(128)` |      | Owner of the parent security class |

### 9.23 ALL_XS_SECURITY_CLASS_DEP

The `ALL_XS_SECURITY_CLASS_DEP` data dictionary view lists all the RAS security classes that the security classes accessible to the current user are dependent on.

#### Related Views

- USER_XS_SECURITY_CLASS_DEP

- DBA_XS_SECURITY_CLASSES

- USER_XS_SECURITY_CLASSES

- ALL_XS_SECURITY_CLASSES

| Column           | Datatype        | NULL | Description                        |
|:-----------------|:----------------|:-----|:-----------------------------------|
| `SECURITY_CLASS` | `VARCHAR2(128`) |      | Name of the security class         |
| `OWNER`          | `VARCHAR2(128)` |      | Owner of the security class        |
| `PARENT`         | `VARCHAR2(128)` |      | Name of the parent security class  |
| `PARENT_OWNER`   | `VARCHAR2(128)` |      | Owner of the parent security class |

### 9.24 DBA_XS_ACLS

The `DBA_XS_ACLS` data dictionary view lists all the existing Real Application Security ACLs defined in the database.

#### Related Views

- USER_XS_ACLS

- DBA_XS_ACES

- ALL_XS_ACLS

| Column                 | Datatype         | NULL | Description                                               |
|:-----------------------|:-----------------|:-----|:----------------------------------------------------------|
| `NAME`                 | `VARCHAR2(128)`  |      | Name of the ACL.                                          |
| `OWNER`                | `VARCHAR2(128)`  |      | Owner of the ACL.                                         |
| `SECURITY_CLASS`       | `VARCHAR2(128)`  |      | Name of the security class associated with the ACL        |
| `SECURITY_CLASS_OWNER` | `VARCHAR2(128)`  |      | Owner of the security class associated with the ACL.      |
| `PARENT_ACL`           | `VARCHAR2(128)`  |      | Name of the parent ACL.                                   |
| `PARENT_ACL_OWNER`     | `VARCHAR2(128)`  |      | Owner of the parent ACL                                   |
| `INHERITANCE_TYPE`     | `VARCHAR2(11)`   |      | Inheritance type of the ACL (`EXTENDED` or `CONSTRAINED`) |
| `DESCRIPTION`          | `VARCHAR2(4000)` |      | Description of the ACL                                    |

### 9.25 USER_XS_ACLS

The `USER_XS_ACLS` data dictionary view lists all the ACLs owned by the current user.

#### Related Views

- DBA_XS_ACLS

- USER_XS_ACES

- ALL_XS_ACLS

- ALL_XS_ACES

| Column                 | Datatype         | NULL | Description                                               |
|:-----------------------|:-----------------|:-----|:----------------------------------------------------------|
| `NAME`                 | `VARCHAR2(128)`  |      | Name of the ACL.                                          |
| `SECURITY_CLASS`       | `VARCHAR2(128)`  |      | Name of the security class associated with the ACL        |
| `SECURITY_CLASS_OWNER` | `VARCHAR2(128)`  |      | Owner of the security class associated with the ACL.      |
| `PARENT_ACL`           | `VARCHAR2(128)`  |      | Name of the parent ACL.                                   |
| `PARENT_ACL_OWNER`     | `VARCHAR2(128)`  |      | Owner of the parent ACL                                   |
| `INHERITANCE_TYPE`     | `VARCHAR2(11)`   |      | Inheritance type of the ACL (`EXTENDED` or `CONSTRAINED`) |
| `DESCRIPTION`          | `VARCHAR2(4000)` |      | Description of the ACL                                    |

### 9.26 ALL_XS_ACLS

The `ALL_XS_ACLS` data dictionary view lists all the existing Real Application Security ACLs accessible to the current user.

#### Related Views

- USER_XS_ACLS

- DBA_XS_ACES

| Column                 | Datatype         | NULL | Description                                               |
|:-----------------------|:-----------------|:-----|:----------------------------------------------------------|
| `NAME`                 | `VARCHAR2(128)`  |      | Name of the ACL.                                          |
| `OWNER`                | `VARCHAR2(128)`  |      | Owner of the ACL.                                         |
| `SECURITY_CLASS`       | `VARCHAR2(128)`  |      | Name of the security class associated with the ACL        |
| `SECURITY_CLASS_OWNER` | `VARCHAR2(128)`  |      | Owner of the security class associated with the ACL.      |
| `PARENT_ACL`           | `VARCHAR2(128)`  |      | Name of the parent ACL.                                   |
| `PARENT_ACL_OWNER`     | `VARCHAR2(128)`  |      | Owner of the parent ACL                                   |
| `INHERITANCE_TYPE`     | `VARCHAR2(11)`   |      | Inheritance type of the ACL (`EXTENDED` or `CONSTRAINED`) |
| `DESCRIPTION`          | `VARCHAR2(4000)` |      | Description of the ACL                                    |

### 9.27 DBA_XS_ACES

The `DBA_XS_ACES` data dictionary view lists all the Access Control Entries (ACEs) defined in the database.

#### Related Views

- USER_XS_ACES

- DBA_XS_ACLS

- ALL_XS_ACES

- ALL_XS_ACLS

| Column                 | Datatype        | NULL       | Description                                                         |
|:-----------------------|:----------------|:-----------|:--------------------------------------------------------------------|
| `ACL`                  | `VARCHAR2(128)` |            | Name of the ACL                                                     |
| `OWNER`                | `VARCHAR2(128)` |            | Owner of the ACL                                                    |
| `ACE_ORDER`            | `NUMBER`        | `NOT NULL` | Order number of the ACE in the ACL                                  |
| `START_DATE`           | `TIMESTAMP(6)`  |            | Effective start date of the ACE                                     |
| `END_DATE`             | `TIMESTAMP(6)`  |            | Effective end date of the ACE                                       |
| `GRANT_TYPE`           | `VARCHAR2(5)`   |            | Specifies whether the ACE is a `GRANT` or `DENY`                    |
| `INVERTED_PRINCIPAL`   | `VARCHAR2(3)`   |            | `YES` if the principal is inverted, else `NO`                       |
| `PRINCIPAL`            | `VARCHAR2(128)` |            | Name of the principal to whom the ACE applies                       |
| `PRINCIPAL_TYPE`       | `VARCHAR2(16)`  |            | Type of the principal, such as application user or application role |
| `PRIVILEGE`            | `VARCHAR2(128)` |            | Name of the application privilege                                   |
| `SECURITY_CLASS`       | `VARCHAR2(128)` |            | Name of the security class that scopes the ACL                      |
| `SECURITY_CLASS_OWNER` | `VARCHAR2(128)` |            | Owner of the security class that scopes the ACL                     |

### 9.28 USER_XS_ACES

The `USER_XS_ACES` data dictionary view lists all the Access Control Entries (ACEs) from the ACLs owned by the current user.

#### Related Views

- DBA_XS_ACES

- USER_XS_ACLS

- ALL_XS_ACES

- ALL_XS_ACLS

| Column                 | Datatype        | NULL       | Description                                                         |
|:-----------------------|:----------------|:-----------|:--------------------------------------------------------------------|
| `ACL`                  | `VARCHAR2(128)` |            | Name of the ACL                                                     |
| `ACE_ORDER`            | `NUMBER`        | `NOT NULL` | Order number of the ACE in the ACL                                  |
| `START_DATE`           | `TIMESTAMP(6)`  |            | Effective start date of the ACE                                     |
| `END_DATE`             | `TIMESTAMP(6)`  |            | Effective end date of the ACE                                       |
| `GRANT_TYPE`           | `VARCHAR2(5)`   |            | Specifies whether the ACE is a `GRANT` or `DENY`                    |
| `INVERTED_PRINCIPAL`   | `VARCHAR2(3)`   |            | `YES` if the principal is inverted, else `NO`                       |
| `PRINCIPAL`            | `VARCHAR2(128)` |            | Name of the principal to whom the ACE applies                       |
| `PRINCIPAL_TYPE`       | `VARCHAR2(16)`  |            | Type of the principal, such as application user or application role |
| `PRIVILEGE`            | `VARCHAR2(128)` |            | Name of the application privilege                                   |
| `SECURITY_CLASS`       | `VARCHAR2(128)` |            | Name of the security class that scopes the ACL                      |
| `SECURITY_CLASS_OWNER` | `VARCHAR2(128)` |            | Owner of the security class that scopes the ACL                     |

### 9.29 ALL_XS_ACES

The `ALL_XS_ACES` data dictionary view lists all the Access Control Entries (ACEs) accessible to the current user.

#### Related Views

- USER_XS_ACES

- DBA_XS_ACLS

| Column                 | Datatype        | NULL       | Description                                                         |
|:-----------------------|:----------------|:-----------|:--------------------------------------------------------------------|
| `ACL`                  | `VARCHAR2(128)` |            | Name of the ACL                                                     |
| `OWNER`                | `VARCHAR2(128)` |            | Owner of the ACL                                                    |
| `ACE_ORDER`            | `NUMBER`        | `NOT NULL` | Order number of the ACE in the ACL                                  |
| `START_DATE`           | `TIMESTAMP(6)`  |            | Effective start date of the ACE                                     |
| `END_DATE`             | `TIMESTAMP(6)`  |            | Effective end date of the ACE                                       |
| `GRANT_TYPE`           | `VARCHAR2(5)`   |            | Specifies whether the ACE is a `GRANT` or `DENY`                    |
| `INVERTED_PRINCIPAL`   | `VARCHAR2(3)`   |            | `YES` if the principal is inverted, else `NO`                       |
| `PRINCIPAL`            | `VARCHAR2(128)` |            | Name of the principal to whom the ACE applies                       |
| `PRINCIPAL_TYPE`       | `VARCHAR2(16)`  |            | Type of the principal, such as application user or application role |
| `PRIVILEGE`            | `VARCHAR2(128)` |            | Name of the application privilege                                   |
| `SECURITY_CLASS`       | `VARCHAR2(128)` |            | Name of the security class that scopes the ACL                      |
| `SECURITY_CLASS_OWNER` | `VARCHAR2(128)` |            | Owner of the security class that scopes the ACL                     |

### 9.30 DBA_XS_POLICIES

The `DBA_XS_POLICIES` data dictionary view lists all the existing Real Application Security data security policies defined in the database.

#### Related Views

- USER_XS_POLICIES

- DBA_XS_REALM_CONSTRAINTS

- DBA_XS_COLUMN_CONSTRAINTS

- ALL_XS_POLICIES

- ALL_XS_COLUMN_CONSTRAINTS

- ALL_XS_REALM_CONSTRAINTS

| Column        | Datatype         | NULL | Description                             |
|:--------------|:-----------------|:-----|:----------------------------------------|
| `NAME`        | `VARCHAR2(128)`  |      | Name of the data security policy        |
| `OWNER`       | `VARCHAR2(128)`  |      | Owner of the data security policy       |
| `CREATE_TIME` | `TIMESTAMP(6)`   |      | When was the policy created             |
| `MODIFY_TIME` | `TIMESTAMP(6)`   |      | When was the policy last modified       |
| `DESCRIPTION` | `VARCHAR2(4000)` |      | Description of the data security policy |

### 9.31 USER_XS_POLICIES

The `USER_XS_POLICIES` data dictionary view lists all the existing Real Application Security data security policies owned by the current user.

#### Related Views

- DBA_XS_POLICIES

- USER_XS_REALM_CONSTRAINTS

- USER_XS_COLUMN_CONSTRAINTS

- ALL_XS_POLICIES

- ALL_XS_COLUMN_CONSTRAINTS

- ALL_XS_REALM_CONSTRAINTS

| Column        | Datatype         | NULL | Description                             |
|:--------------|:-----------------|:-----|:----------------------------------------|
| `NAME`        | `VARCHAR2(128)`  |      | Name of the data security policy        |
| `CREATE_TIME` | `TIMESTAMP(6)`   |      | When was the policy created             |
| `MODIFY_TIME` | `TIMESTAMP(6)`   |      | When was the policy last modified       |
| `DESCRIPTION` | `VARCHAR2(4000)` |      | Description of the data security policy |

### 9.32 ALL_XS_POLICIES

The `ALL_XS_POLICIES` data dictionary view lists all the existing Real Application Security data security policies accessible to the current user.

#### Related Views

- USER_XS_POLICIES

- DBA_XS_REALM_CONSTRAINTS

- DBA_XS_COLUMN_CONSTRAINTS

| Column        | Datatype         | NULL | Description                             |
|:--------------|:-----------------|:-----|:----------------------------------------|
| `NAME`        | `VARCHAR2(128)`  |      | Name of the data security policy        |
| `OWNER`       | `VARCHAR2(128)`  |      | Owner of the data security policy       |
| `CREATE_TIME` | `TIMESTAMP(6)`   |      | When was the policy created             |
| `MODIFY_TIME` | `TIMESTAMP(6)`   |      | When was the policy last modified       |
| `DESCRIPTION` | `VARCHAR2(4000)` |      | Description of the data security policy |

### 9.33 DBA_XS_REALM_CONSTRAINTS

The `DBA_XS_REALM_CONSTRAINTS` data dictionary view displays all existing Real Application Security realms in the database.

#### Related Views

- USER_XS_REALM_CONSTRAINTS

- DBA_XS_COLUMN_CONSTRAINTS

- ALL_XS_REALM_CONSTRAINTS

- ALL_XS_COLUMN_CONSTRAINTS

| Column          | Datatype         | NULL       | Description                                                                          |
|:----------------|:-----------------|:-----------|:-------------------------------------------------------------------------------------|
| `POLICY`        | `VARCHAR2(128`)  |            | Name of the data security policy                                                     |
| `POLICY_OWNER`  | `VARCHAR2(128)`  |            | Owner of the data security policy                                                    |
| `REALM_ORDER`   | `NUMBER`         | `NOT NULL` | The order of the realm within the data security policy                               |
| `REALM_TYPE`    | `VARCHAR2(13)`   |            | The type of the realm. Valid values are `REGULAR`, `PARAMETERIZED`, and `INHERITED.` |
| `STATIC`        | `VARCHAR2(7)`    |            | Indicates whether the realm is `STATIC` or `DYNAMIC`                                 |
| `REALM`         | `VARCHAR2(4000)` |            | The data realm.                                                                      |
| `ACL`           | `VARCHAR2(128)`  |            | ACL associated with the realm if the realm type is `REGULAR`                         |
| `ACL_OWNER`     | `VARCHAR2(128)`  |            | Owner of the ACL associated with the `REGULAR` realm                                 |
| `PARENT_OBJECT` | `VARCHAR2(128)`  |            | Name of the parent object if the realm type is `INHERITED`                           |
| `PARENT_SCHEMA` | `VARCHAR2(128)`  |            | Schema of the parent object if the realm type is `INHERITED`                         |

### 9.34 USER_XS_REALM_CONSTRAINTS

The `USER_XS_REALM_CONSTRAINTS` data dictionary view displays all existing Real Application Security realms owned by the current user.

#### Related Views

- DBA_XS_REALM_CONSTRAINTS

- USER_XS_COLUMN_CONSTRAINTS

- ALL_XS_REALM_CONSTRAINTS

- ALL_XS_COLUMN_CONSTRAINTS

| Column          | Datatype         | NULL       | Description                                                                          |
|:----------------|:-----------------|:-----------|:-------------------------------------------------------------------------------------|
| `POLICY`        | `VARCHAR2(128`)  |            | Name of the data security policy                                                     |
| `REALM_ORDER`   | `NUMBER`         | `NOT NULL` | The order of the realm within the data security policy                               |
| `REALM_TYPE`    | `VARCHAR2(13)`   |            | The type of the realm. Valid values are `REGULAR`, `PARAMETERIZED`, and `INHERITED.` |
| `STATIC`        | `VARCHAR2(7)`    |            | Indicates whether the realm is `STATIC` or `DYNAMIC`                                 |
| `REALM`         | `VARCHAR2(4000)` |            | The data realm.                                                                      |
| `ACL`           | `VARCHAR2(128)`  |            | ACL associated with the realm if the realm type is `REGULAR`                         |
| `ACL_OWNER`     | `VARCHAR2(128)`  |            | Owner of the ACL associated with the `REGULAR` realm                                 |
| `PARENT_OBJECT` | `VARCHAR2(128)`  |            | Name of the parent object if the realm type is `INHERITED`                           |
| `PARENT_SCHEMA` | `VARCHAR2(128)`  |            | Schema of the parent object if the realm type is `INHERITED`                         |

### 9.35 ALL_XS_REALM_CONSTRAINTS

The `ALL_XS_REALM_CONSTRAINTS` data dictionary view displays all existing Real Application Security realms accessible to the current user.

#### Related Views

- USER_XS_REALM_CONSTRAINTS

- DBA_XS_COLUMN_CONSTRAINTS

| Column          | Datatype         | NULL       | Description                                                                          |
|:----------------|:-----------------|:-----------|:-------------------------------------------------------------------------------------|
| `POLICY`        | `VARCHAR2(128`)  |            | Name of the data security policy                                                     |
| `POLICY_OWNER`  | `VARCHAR2(128)`  |            | Owner of the data security policy                                                    |
| `REALM_ORDER`   | `NUMBER`         | `NOT NULL` | The order of the realm within the data security policy                               |
| `REALM_TYPE`    | `VARCHAR2(13)`   |            | The type of the realm. Valid values are `REGULAR`, `PARAMETERIZED`, and `INHERITED.` |
| `STATIC`        | `VARCHAR2(7)`    |            | Indicates whether the realm is `STATIC` or `DYNAMIC`                                 |
| `REALM`         | `VARCHAR2(4000)` |            | The data realm.                                                                      |
| `ACL`           | `VARCHAR2(128)`  |            | ACL associated with the realm if the realm type is `REGULAR`                         |
| `ACL_OWNER`     | `VARCHAR2(128)`  |            | Owner of the ACL associated with the `REGULAR` realm                                 |
| `PARENT_OBJECT` | `VARCHAR2(128)`  |            | Name of the parent object if the realm type is `INHERITED`                           |
| `PARENT_SCHEMA` | `VARCHAR2(128)`  |            | Schema of the parent object if the realm type is `INHERITED`                         |

### 9.36 DBA_XS_INHERITED_REALMS

The `DBA_XS_INHERITED_REALMS` data dictionary view displays all the inherited Real Application Security realms in the database.

#### Related Views

- USER_XS_INHERITED_REALMS

- DBA_XS_REALM_CONSTRAINTS

- ALL_XS_INHERITED_REALMS

- ALL_XS_REALM_CONSTRAINTS

| Column             | Datatype         | NULL       | Description                                                      |
|:-------------------|:-----------------|:-----------|:-----------------------------------------------------------------|
| `POLICY`           | `VARCHAR2(128`)  |            | Name of the data security policy                                 |
| `POLICY_OWNER`     | `VARCHAR2(128)`  |            | Owner of the data security policy                                |
| `REALM_ORDER`      | `NUMBER`         | `NOT NULL` | The order of the realm within the data security policy           |
| `PARENT_OBJECT`    | `VARCHAR2(128)`  |            | Name of the parent object                                        |
| `PARENT_SCHEMA`    | `VARCHAR2(128)`  |            | Schema of the parent object                                      |
| `PRIMARY_KEY`      | `VARCHAR2(128)`  |            | The column name in the master table                              |
| `FOREIGN_KEY`      | `VARCHAR2(4000)` |            | The column name or value in the detail table                     |
| `FOREIGN_KEY_TYPE` | `VARCHAR2(5)`    |            | Type of the foreign key. Possible values are `NAME` and `VALUE.` |

### 9.37 USER_XS_INHERITED_REALMS

The `USER_XS_INHERITED_REALMS` data dictionary view displays all the inherited Real Application Security realms owned by the current user.

#### Related Views

- DBA_XS_INHERITED_REALMS

- USER_XS_REALM_CONSTRAINTS

- ALL_XS_INHERITED_REALMS

- ALL_XS_REALM_CONSTRAINTS

| Column             | Datatype         | NULL       | Description                                                      |
|:-------------------|:-----------------|:-----------|:-----------------------------------------------------------------|
| `POLICY`           | `VARCHAR2(128`)  |            | Name of the data security policy                                 |
| `REALM_ORDER`      | `NUMBER`         | `NOT NULL` | The order of the realm within the data security policy           |
| `PARENT_OBJECT`    | `VARCHAR2(128)`  |            | Name of the parent object                                        |
| `PARENT_SCHEMA`    | `VARCHAR2(128)`  |            | Schema of the parent object                                      |
| `PRIMARY_KEY`      | `VARCHAR2(128)`  |            | The column name in the master table                              |
| `FOREIGN_KEY`      | `VARCHAR2(4000)` |            | The column name or value in the detail table                     |
| `FOREIGN_KEY_TYPE` | `VARCHAR2(5)`    |            | Type of the foreign key. Possible values are `NAME` and `VALUE.` |

### 9.38 ALL_XS_INHERITED_REALMS

The `ALL_XS_INHERITED_REALMS` data dictionary view displays all the inherited Real Application Security realms accessible to the current user.

#### Related Views

- USER_XS_INHERITED_REALMS

- DBA_XS_REALM_CONSTRAINTS

| Column             | Datatype         | NULL       | Description                                                      |
|:-------------------|:-----------------|:-----------|:-----------------------------------------------------------------|
| `POLICY`           | `VARCHAR2(128`)  |            | Name of the data security policy                                 |
| `POLICY_OWNER`     | `VARCHAR2(128)`  |            | Owner of the data security policy                                |
| `REALM_ORDER`      | `NUMBER`         | `NOT NULL` | The order of the realm within the data security policy           |
| `PARENT_OBJECT`    | `VARCHAR2(128)`  |            | Name of the parent object                                        |
| `PARENT_SCHEMA`    | `VARCHAR2(128)`  |            | Schema of the parent object                                      |
| `PRIMARY_KEY`      | `VARCHAR2(128)`  |            | The column name in the master table                              |
| `FOREIGN_KEY`      | `VARCHAR2(4000)` |            | The column name or value in the detail table                     |
| `FOREIGN_KEY_TYPE` | `VARCHAR2(5)`    |            | Type of the foreign key. Possible values are `NAME` and `VALUE.` |

### 9.39 DBA_XS_ACL_PARAMETERS

The `DBA_XS_ACL_PARAMETERS` data dictionary view displays all existing Real Application Security ACL parameters.

#### Related Views

- USER_XS_ACL_PARAMETERS

- DBA_XS_REALM_CONSTRAINTS

- ALL_XS_ACL_PARAMETERS

- ALL_XS_REALM_CONSTRAINTS

| Column         | Datatype         | NULL | Description                                                          |
|:---------------|:-----------------|:-----|:---------------------------------------------------------------------|
| `POLICY`       | `VARCHAR2(128`)  |      | Name of the data security policy where the ACL parameter is defined  |
| `POLICY_OWNER` | `VARCHAR2(128)`  |      | Owner of the data security policy where the ACL parameter is defined |
| `ACL`          | `VARCHAR2(128)`  |      | Name of the ACL                                                      |
| `ACL_OWNER`    | `VARCHAR2(128)`  |      | Owner of the ACL                                                     |
| `PARAMETER`    | `VARCHAR2(128)`  |      | Name of the ACL parameter                                            |
| `DATATYPE`     | `VARCHAR2(9)`    |      | Data type of the ACL parameter                                       |
| `VALUE`        | `VARCHAR2(4000)` |      | Value of the ACL parameter                                           |
| `REALM_ORDER`  | `NUMBER`         |      | The order of the realm within the data security policy               |
| `REALM`        | `VARCHAR2(4000)` |      | The realm that contains the ACL parameter                            |

### 9.40 USER_XS_ACL_PARAMETERS

The `USER_XS_ACL_PARAMETERS` data dictionary view displays all ACL parameters defined in the data security policies owned by the current user.

#### Related Views

- DBA_XS_ACL_PARAMETERS

- USER_XS_REALM_CONSTRAINTS

- ALL_XS_ACL_PARAMETERS

- ALL_XS_REALM_CONSTRAINTS

| Column        | Datatype         | NULL | Description                                                         |
|:--------------|:-----------------|:-----|:--------------------------------------------------------------------|
| `POLICY`      | `VARCHAR2(128`)  |      | Name of the data security policy where the ACL parameter is defined |
| `ACL`         | `VARCHAR2(128)`  |      | Name of the ACL                                                     |
| `ACL_OWNER`   | `VARCHAR2(128)`  |      | Owner of the ACL                                                    |
| `PARAMETER`   | `VARCHAR2(128)`  |      | Name of the ACL parameter                                           |
| `DATATYPE`    | `VARCHAR2(9)`    |      | Data type of the ACL parameter                                      |
| `VALUE`       | `VARCHAR2(4000)` |      | Value of the ACL parameter                                          |
| `REALM_ORDER` | `NUMBER`         |      | The order of the realm within the data security policy              |
| `REALM`       | `VARCHAR2(4000)` |      | The realm that contains the ACL parameter                           |

### 9.41 ALL_XS_ACL_PARAMETERS

The `ALL_XS_ACL_PARAMETERS` data dictionary view displays all existing Real Application Security ACL parameters defined in the data security policies accessible to the current user.

#### Related Views

- USER_XS_ACL_PARAMETERS

- DBA_XS_REALM_CONSTRAINTS

| Column         | Datatype         | NULL | Description                                                          |
|:---------------|:-----------------|:-----|:---------------------------------------------------------------------|
| `POLICY`       | `VARCHAR2(128`)  |      | Name of the data security policy where the ACL parameter is defined  |
| `POLICY_OWNER` | `VARCHAR2(128)`  |      | Owner of the data security policy where the ACL parameter is defined |
| `ACL`          | `VARCHAR2(128)`  |      | Name of the ACL                                                      |
| `ACL_OWNER`    | `VARCHAR2(128)`  |      | Owner of the ACL                                                     |
| `PARAMETER`    | `VARCHAR2(128)`  |      | Name of the ACL parameter                                            |
| `DATATYPE`     | `VARCHAR2(9)`    |      | Data type of the ACL parameter                                       |
| `VALUE`        | `VARCHAR2(4000)` |      | Value of the ACL parameter                                           |
| `REALM_ORDER`  | `NUMBER`         |      | The order of the realm within the data security policy               |
| `REALM`        | `VARCHAR2(4000)` |      | The realm that contains the ACL parameter                            |

### 9.42 DBA_XS_COLUMN_CONSTRAINTS

The `DBA_XS_COLUMN_CONSTRAINTS` data dictionary view lists all Real Application Security column constraints defined in the database.

#### Related Views

- USER_XS_COLUMN_CONSTRAINTS

- DBA_XS_POLICIES

- ALL_XS_COLUMN_CONSTRAINTS

- ALL_XS_POLICIES

| Column        | Datatype        | NULL | Description                                                        |
|:--------------|:----------------|:-----|:-------------------------------------------------------------------|
| `POLICY`      | `VARCHAR2(128)` | NA   | Name of the data security policy containing the column constraint  |
| `OWNER`       | `VARCHAR2(128)` | NA   | Owner of the data security policy containing the column constraint |
| `COLUMN_NAME` | `VARCHAR2(128)` | NA   | Name of the column that has the column constraint applied to it    |
| `PRIVILEGE`   | `VARCHAR2(128)` | NA   | Name of the application privilege required to access the column    |

### 9.43 USER_XS_COLUMN_CONSTRAINTS

The `USER_XS_COLUMN_CONSTRAINTS` data dictionary view lists all Real Application Security column constraints owned by the current user.

#### Related Views

- DBA_XS_COLUMN_CONSTRAINTS

- USER_XS_POLICIES

- ALL_XS_COLUMN_CONSTRAINTS

- ALL_XS_POLICIES

| Column        | Datatype        | NULL | Description                                                        |
|:--------------|:----------------|:-----|:-------------------------------------------------------------------|
| `POLICY`      | `VARCHAR2(128)` |      | Name of the data security policy containing the column constraint  |
| `OWNER`       | `VARCHAR2(128)` |      | Owner of the data security policy containing the column constraint |
| `COLUMN_NAME` | `VARCHAR2(128)` |      | Name of the column that has the column constraint applied to it    |
| `PRIVILEGE`   | `VARCHAR2(128)` |      | Name of the application privilege required to access the column    |

### 9.44 ALL_XS_COLUMN_CONSTRAINTS

The `ALL_XS_COLUMN_CONSTRAINTS` data dictionary view lists all Real Application Security column constraints accessible to the current user.

#### Related Views

- USER_XS_COLUMN_CONSTRAINTS

- DBA_XS_POLICIES

| Column        | Datatype        | NULL | Description                                                        |
|:--------------|:----------------|:-----|:-------------------------------------------------------------------|
| `POLICY`      | `VARCHAR2(128)` | NA   | Name of the data security policy containing the column constraint  |
| `OWNER`       | `VARCHAR2(128)` | NA   | Owner of the data security policy containing the column constraint |
| `COLUMN_NAME` | `VARCHAR2(128)` | NA   | Name of the column that has the column constraint applied to it    |
| `PRIVILEGE`   | `VARCHAR2(128)` | NA   | Name of the application privilege required to access the column    |

### 9.45 DBA_XS_APPLIED_POLICIES

The `DBA_XS_APPLIED_POLICIES` data dictionary view displays all database objects on which Real Application Security data security policies are enabled.

#### Related Views

- DBA_XS_POLICIES

- ALL_XS_POLICIES

| Column         | Datatype        | NULL       | Description                                                                      |
|:---------------|:----------------|:-----------|:---------------------------------------------------------------------------------|
| `SCHEMA`       | `VARCHAR2(128`) | `NOT NULL` | Schema containing the object                                                     |
| `OBJECT`       | `VARCHAR2(128)` | `NOT NULL` | Name of the data security enabled object in the database                         |
| `POLICY`       | `VARCHAR2(128)` |            | Name of the data security policy associated with the object                      |
| `POLICY_OWNER` | `VARCHAR2(128)` | `NOT NULL` | Owner of the data security policy associated with the object                     |
| `SEL`          | `VARCHAR2(3`)   |            | Policy enabled for `SELECT` statements                                           |
| `INS`          | `VARCHAR2(3)`   |            | Policy enabled for `INSERT` statements                                           |
| `UPD`          | `VARCHAR2(3)`   |            | Policy enabled for `UPDATE` statements                                           |
| `DEL`          | `VARCHAR2(3)`   |            | Policy enabled for `DELETE` statements                                           |
| `IDX`          | `VARCHAR2(3)`   |            | Policy enabled for `INDEX` statements                                            |
| `STATUS`       | `VARCHAR2(8)`   |            | `ENABLED` if the data security policy is enabled for the object, else `DISABLED` |

### 9.46 ALL_XS_APPLIED_POLICIES

The `ALL_XS_APPLIED_POLICIES` data dictionary view displays all database objects on which Real Application Security data security policies are accessible to the current user are enabled.

#### Related Views

- DBA_XS_POLICIES

| Column         | Datatype        | NULL       | Description                                                                      |
|:---------------|:----------------|:-----------|:---------------------------------------------------------------------------------|
| `SCHEMA`       | `VARCHAR2(128`) | `NOT NULL` | Schema containing the object                                                     |
| `OBJECT`       | `VARCHAR2(128)` | `NOT NULL` | Name of the data security enabled object in the database                         |
| `POLICY`       | `VARCHAR2(128)` |            | Name of the data security policy associated with the object                      |
| `POLICY_OWNER` | `VARCHAR2(128)` | `NOT NULL` | Owner of the data security policy associated with the object                     |
| `SEL`          | `VARCHAR2(3`)   |            | Policy enabled for `SELECT` statements                                           |
| `INS`          | `VARCHAR2(3)`   |            | Policy enabled for `INSERT` statements                                           |
| `UPD`          | `VARCHAR2(3)`   |            | Policy enabled for `UPDATE` statements                                           |
| `DEL`          | `VARCHAR2(3)`   |            | Policy enabled for `DELETE` statements                                           |
| `IDX`          | `VARCHAR2(3)`   |            | Policy enabled for `INDEX` statements                                            |
| `STATUS`       | `VARCHAR2(8)`   |            | `ENABLED` if the data security policy is enabled for the object, else `DISABLED` |

### 9.47 DBA_XS_MODIFIED_POLICIES

The `DBA_XS_MODIFIED_POLICIES` data dictionary view displays all database objects on which Real Application Security data security policies are modified.

#### Related Views

- DBA_XS_POLICIES

- DBA_XS_APPLIED_POLICIES

| Column   | Datatype        | NULL       | Description                                                 |
|:---------|:----------------|:-----------|:------------------------------------------------------------|
| `POLICY` | `VARCHAR2(128)` | NOT NULL   | Name of the data security policy associated with the object |
| `OBJECT` | `VARCHAR2(128)` | `NOT NULL` | Name of the data security modified object in the database   |

### 9.48 DBA_XS_SESSIONS

The `DBA_XS_SESSIONS` dynamic data dictionary view displays all the application sessions in the database. Only database administrators can select from this view.

#### Related Views

- DBA_XS_ACTIVE_SESSIONS

- DBA_XS_SESSION_ROLES

- DBA_XS_SESSION_NS_ATTRIBUTES

| Column             | Datatype         | NULL       | Description                                                                            |
|:-------------------|:-----------------|:-----------|:---------------------------------------------------------------------------------------|
| `USER_NAME`        | `VARCHAR2(128`)  | `NOT NULL` | Application user name of the application session                                       |
| `SESSIONID`        | `RAW(16)`        | `NOT NULL` | Application Session identifier                                                         |
| `PROXY_USER`       | `VARCHAR2(128)`  |            | Name of the proxy application user                                                     |
| `COOKIE`           | `VARCHAR2(1024)` |            | The server-unique cookie value associated with the session                             |
| `CREATE_TIME`      | `TIMESTAMP(6)`   | `NOT NULL` | Creation time for the application session                                              |
| `AUTH_TIME`        | `TIMESTAMP(6)`   | `NOT NULL` | Last time the application user was authenticated.                                      |
| `ACCESS_TIME`      | `TIMESTAMP(6)`   | `NOT NULL` | Last time that the application session was accessed                                    |
| `INACTIVE_TIMEOUT` | `NUMBER(6)`      |            | The amount of time (in minutes) before the application session is considered timed out |

### 9.49 DBA_XS_ACTIVE_SESSIONS

The `DBA_XS_ACTIVE_SESSIONS` dynamic data dictionary view displays all attached application sessions in the database. Only database administrators can select from this view.

#### Related Views

- DBA_XS_SESSIONS

- DBA_XS_SESSION_ROLES

- DBA_XS_SESSION_NS_ATTRIBUTES

| Column               | Datatype         | NULL       | Description                                                                            |
|:---------------------|:-----------------|:-----------|:---------------------------------------------------------------------------------------|
| `USER_NAME`          | `VARCHAR2(128`)  | `NOT NULL` | Application user name of the application session                                       |
| `SESSIONID`          | `RAW(16)`        | `NOT NULL` | Application Session identifier                                                         |
| `DATABASE_SESSIONID` | `NUMBER`         |            | The database session ID to which the application session is associated.                |
| `PROXY_USER`         | `VARCHAR2(128)`  |            | Name of the proxy application user                                                     |
| `COOKIE`             | `VARCHAR2(1024)` |            | The server-unique cookie value associated with the session                             |
| `CREATE_TIME`        | `TIMESTAMP(6)`   | `NOT NULL` | Creation time for the application session                                              |
| `AUTH_TIME`          | `TIMESTAMP(6)`   | `NOT NULL` | Last time the application user was authenticated.                                      |
| `ACCESS_TIME`        | `TIMESTAMP(6)`   | `NOT NULL` | Last time that the application session was accessed                                    |
| `INACTIVE_TIMEOUT`   | `NUMBER(6)`      |            | The amount of time (in minutes) before the application session is considered timed out |

### 9.50 DBA_XS_SESSION_ROLES

The `DBA_XS_SESSION_ROLES` dynamic data dictionary view lists application roles enabled in application sessions.

#### Related Views

- DBA_XS_SESSIONS

- DBA_XS_ACTIVE_SESSIONS

- DBA_XS_SESSION_NS_ATTRIBUTES

| Column      | Datatype        | NULL       | Description                  |
|:------------|:----------------|:-----------|:-----------------------------|
| `SESSIONID` | `RAW(16)`       | `NOT NULL` | Application session ID       |
| `ROLE`      | `VARCHAR2(128)` | `NOT NULL` | Name of the application role |

### 9.51 DBA_XS_SESSION_NS_ATTRIBUTES

The `DBA_XS_SESSION_NS_ATTRIBUTES` data dictionary view displays namespace attributes across application sessions as of last saved state.

#### Related Views

- DBA_XS_SESSIONS

- DBA_XS_ACTIVE_SESSIONS

- DBA_XS_SESSION_ROLES

| Column            | Datatype         | NULL       | Description                                                                                                             |
|:------------------|:-----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------|
| `SESSIONID`       | `RAW(16)`        | `NOT NULL` | Session ID of the application session                                                                                   |
| `ATTRIBUTE`       | `VARCHAR2(4000)` |            | Name of the attribute                                                                                                   |
| `NAMESPACE`       | `VARCHAR2(128)`  | `NOT NULL` | Name of the namespace                                                                                                   |
| `VALUE`           | `VARCHAR2(4000)` |            | Value of the attribute                                                                                                  |
| `DEFAULT_VALUE`   | `VARCHAR2(4000)` |            | Default value of the attribute                                                                                          |
| `FIRSTREAD_EVENT` | `VARCHAR2(2)`    |            | Indicates whether the handler function is invoked when the attribute is first read. Possible values are `YES` and `NO`. |
| `MODIFY_EVENT`    | `VARCHAR2(2)`    |            | Indicates whether the handler function is invoked when the attribute is modified. Possible values are `YES` and `NO`.   |

### 9.52 DBA_XS_NS_TEMPLATES

The `DBA_XS_NS_TEMPLATES` data dictionary view describes all Real Application Security namespace templates.

#### Related Views

- DBA_XS_NS_TEMPLATE_ATTRIBUTES

| Column             | Datatype         | NULL | Description                                                               |
|:-------------------|:-----------------|:-----|:--------------------------------------------------------------------------|
| `NAME`             | `VARCHAR2(128)`  |      | Name of the namespace template                                            |
| `HANDLER_SCHEMA`   | `VARCHAR2(128)`  |      | Schema of the namespace handler function                                  |
| `HANDLER_PACKAGE`  | `VARCHAR2(128)`  |      | Package containing the namespace handler function                         |
| `HANDLER_FUNCTION` | `VARCHAR2(128)`  |      | The namespace handler function                                            |
| `HANDLER_STATUS`   | `VARCHAR2(7)`    |      | Indicates whether the namespace handler function is `VALID` or `INVALID`. |
| `ACL`              | `VARCHAR2(128)`  |      | Name of ACL for the namespace template.                                   |
| `DESCRIPTION`      | `VARCHAR2(4000)` |      | Description of the namespace template.                                    |

### 9.53 DBA_XS_NS_TEMPLATE_ATTRIBUTES

The `DBA_XS_NS_TEMPLATE_ATTRIBUTES` data dictionary view describes all namespace attributes defined in namespace template documents.

#### Related Views

- DBA_XS_NS_TEMPLATES

| Column            | Datatype         | NULL | Description                                                                                                                        |
|:------------------|:-----------------|:-----|:-----------------------------------------------------------------------------------------------------------------------------------|
| `ATTRIBUTE`       | `VARCHAR2(4000)` |      | Name of the attribute defined in the namespace template                                                                            |
| `NAMESPACE`       | `VARCHAR2(128)`  |      | Name of the namespace instantiated by the namespace template                                                                       |
| `DEFAULT_VALUE`   | `VARCHAR2(4000)` |      | Default value of the attribute defined in the namespace template                                                                   |
| `FIRSTREAD_EVENT` | `VARCHAR2(3)`    |      | Indicates whether the namespace handler function is invoked when the attribute is first read. Valid values are `YES` and `NO`.     |
| `MODIFY_EVENT`    | `VARCHAR2(3)`    |      | Indicates whether the namespace handler function is invoked when the attribute value is modified. Valid values are `YES` and `NO`. |

### 9.54 ALL_XDS_ACL_REFRESH

The `ALL_XDS_ACL_REFRESH` data dictionary view displays all static ACL refresh settings for tables that are accessible to the application user.

#### Related Views

- DBA_XDS_ACL_REFRESH

- USER_XDS_ACL_REFRESH

| Column             | Datatype                      | NULL       | Description                                                            |
|:-------------------|:------------------------------|:-----------|:-----------------------------------------------------------------------|
| `SCHEMA_NAME`      | `VARCHAR2(128`)               | `NOT NULL` | Name of schema                                                         |
| `TABLE_NAME`       | `VARCHAR2(128)`               | `NOT NULL` | Name of table                                                          |
| `ACL_MVIEW_NAME`   | `VARCHAR2(128)`               | `NOT NULL` | Name of ACL MV for this table                                          |
| `REFRESH_MODE`     | `VARCHAR2(9)`                 |            | `ON COMMIT`, `SCHEDULED`, or `ON DEMAND`                               |
| `REFRESH_ABILITY`  | `VARCHAR2(11)`                |            | `COMPLETE` or `INCREMENTAL`                                            |
| `ACL_STATUS`       | `VARCHAR2(5)`                 |            | `STALE` or `FRESH`                                                     |
| `USER_SUPPLIED_MV` | `VARCHAR2(1)`                 |            | `Y` or `N`                                                             |
| `START_DATE`       | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job scheduled to run after the timestamp, if scheduled |
| `REPEAT_INTERVAL`  | `VARCHAR2(4000)`              |            | The `repeat_interval` to run the refreshment job, if scheduled         |
| `REFRESH_COUNT`    | `NUMBER`                      |            | Number of times this ACL MV has been refreshed so far                  |
| `COMMENTS`         | `VARCHAR2(240)`               |            | Comments for the refreshment                                           |

### 9.55 ALL_XDS_ACL_REFSTAT

The `ALL_XDS_ACL_REFSTAT` data dictionary view displays all static ACL refresh job status history that has been done for tables that are accessible to the application user.

#### Related Views

- DBA_XDS_ACL_REFSTAT

- USER_XDS_ACL_REFSTAT

| Column             | Datatype                      | NULL       | Description                                                                         |
|:-------------------|:------------------------------|:-----------|:------------------------------------------------------------------------------------|
| `SCHEMA_NAME`      | `VARCHAR2(128`)               | `NOT NULL` | Name of schema                                                                      |
| `TABLE_NAME`       | `VARCHAR2(128)`               | `NOT NULL` | Name of table                                                                       |
| `REFRESH_MODE`     | `VARCHAR2(9)`                 |            | `ON COMMIT`, `SCHEDULED`, or `ON DEMAND`                                            |
| `REFRESH_ABILITY`  | `VARCHAR2(11)`                |            | `COMPLETE` or `INCREMENTAL`                                                         |
| `JOB_START_TIME`   | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job starting time                                                   |
| `JOB_END_TIME`     | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job ending time                                                     |
| `ROW_UPDATE_COUNT` | `NUMBER`                      |            | Number of rows have been updated for static ACL sync                                |
| `STATUS`           | `NUMBER`                      |            | Refreshment job status:<br>0 means success, otherwise an error number is displayed. |
| `ERROR_MESSAGE`    | `VARCHAR2(4000)`              |            | The error message for the error, if there is any.                                   |

### 9.56 ALL_XDS_LATEST_ACL_REFSTAT

The `ALL_XDS_LATEST_ACL_REFSTAT` data dictionary view displays all latest static ACL refresh job status history that has been done for tables that are accessible to the application user. It has the same schema as `ALL_XDS_ACL_REFSTAT` dictionary view, but a subset of its rows.

#### Related Views

- DBA_XDS_LATEST_ACL_REFSTAT

- USER_XDS_LATEST_ACL_REFSTAT

- ALL_XDS_ACL_REFSTAT

| Column             | Datatype                      | NULL       | Description                                                                         |
|:-------------------|:------------------------------|:-----------|:------------------------------------------------------------------------------------|
| `SCHEMA_NAME`      | `VARCHAR2(128`)               | `NOT NULL` | Name of schema                                                                      |
| `TABLE_NAME`       | `VARCHAR2(128)`               | `NOT NULL` | Name of table                                                                       |
| `REFRESH_MODE`     | `VARCHAR2(9)`                 |            | `ON COMMIT`, `SCHEDULED`, or `ON DEMAND`                                            |
| `REFRESH_ABILITY`  | `VARCHAR2(11)`                |            | `COMPLETE` or `INCREMENTAL`                                                         |
| `JOB_START_TIME`   | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job starting time                                                   |
| `JOB_END_TIME`     | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job ending time                                                     |
| `ROW_UPDATE_COUNT` | `NUMBER`                      |            | Number of rows have been updated for static ACL sync                                |
| `STATUS`           | `NUMBER`                      |            | Refreshment job status:<br>0 means success, otherwise an error number is displayed. |
| `ERROR_MESSAGE`    | `VARCHAR2(4000)`              |            | The error message for the error, if there is any.                                   |

### 9.57 DBA_XDS_ACL_REFRESH

The `DBA_XDS_ACL_REFRESH` data dictionary view displays all static ACL refresh settings in the database.

#### Related Views

- ALL_XDS_ACL_REFRESH

- USER_XDS_ACL_REFRESH

| Column             | Datatype                      | NULL       | Description                                                            |
|:-------------------|:------------------------------|:-----------|:-----------------------------------------------------------------------|
| `SCHEMA_NAME`      | `VARCHAR2(128`)               | `NOT NULL` | Name of schema                                                         |
| `TABLE_NAME`       | `VARCHAR2(128)`               | `NOT NULL` | Name of table                                                          |
| `ACL_MVIEW_NAME`   | `VARCHAR2(128)`               | `NOT NULL` | Name of ACL MV for this table                                          |
| `REFRESH_MODE`     | `VARCHAR2(9)`                 |            | `ON COMMIT`, `SCHEDULED`, or `ON DEMAND`                               |
| `REFRESH_ABILITY`  | `VARCHAR2(11)`                |            | `COMPLETE` or `INCREMENTAL`                                            |
| `ACL_STATUS`       | `VARCHAR2(5)`                 |            | `STALE` or `FRESH`                                                     |
| `USER_SUPPLIED_MV` | `VARCHAR2(1)`                 |            | `Y` or `N`                                                             |
| `START_DATE`       | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job scheduled to run after the timestamp, if scheduled |
| `REPEAT_INTERVAL`  | `VARCHAR2(4000)`              |            | The `repeat_interval` to run the refreshment job, if scheduled.        |
| `REFRESH_COUNT`    | `NUMBER`                      |            | Number of refreshment has been done so far                             |
| `COMMENTS`         | `VARCHAR2(240)`               |            | Comments for the refreshment                                           |

### 9.58 DBA_XDS_ACL_REFSTAT

The `DBA_XDS_ACL_REFSTAT` data dictionary view displays all static ACL refresh job status history that has been done in the database.

#### Related Views

- ALL_XDS_ACL_REFSTAT

- USER_XDS_ACL_REFSTAT

| Column             | Datatype                      | NULL       | Description                                                                         |
|:-------------------|:------------------------------|:-----------|:------------------------------------------------------------------------------------|
| `SCHEMA_NAME`      | `VARCHAR2(128`)               | `NOT NULL` | Name of schema                                                                      |
| `TABLE_NAME`       | `VARCHAR2(128)`               | `NOT NULL` | Name of table                                                                       |
| `REFRESH_MODE`     | `VARCHAR2(9)`                 |            | `ON COMMIT`, `SCHEDULED`, or `ON DEMAND`                                            |
| `REFRESH_ABILITY`  | `VARCHAR2(11)`                |            | `COMPLETE` or `INCREMENTAL`                                                         |
| `JOB_START_TIME`   | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job starting time                                                   |
| `JOB_END_TIME`     | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job ending time                                                     |
| `ROW_UPDATE_COUNT` | `NUMBER`                      |            | Number of rows have been updated for static ACL sync                                |
| `STATUS`           | `NUMBER`                      |            | Refreshment job status:<br>0 means success, otherwise an error number is displayed. |
| `ERROR_MESSAGE`    | `VARCHAR2(4000)`              |            | The error message for the error, if there is any.                                   |

### 9.59 DBA_XDS_LATEST_ACL_REFSTAT

The `DBA_XDS_LATEST_ACL_REFSTAT` data dictionary view displays all latest static ACL refresh job status history that has been done in the database. It has the same schema as `DBA_XDS_ACL_REFSTAT` dictionary view, but a subset of its rows.

#### Related Views

- ALL_XDS_LATEST_ACL_REFSTAT

- USER_XDS_LATEST_ACL_REFSTAT

- DBA_XDS_ACL_REFSTAT

| Column             | Datatype                      | NULL       | Description                                                                         |
|:-------------------|:------------------------------|:-----------|:------------------------------------------------------------------------------------|
| `SCHEMA_NAME`      | `VARCHAR2(128`)               | `NOT NULL` | Name of schema                                                                      |
| `TABLE_NAME`       | `VARCHAR2(128)`               | `NOT NULL` | Name of table                                                                       |
| `REFRESH_MODE`     | `VARCHAR2(9)`                 |            | `ON COMMIT`, `SCHEDULED`, or `ON DEMAND`                                            |
| `REFRESH_ABILITY`  | `VARCHAR2(11)`                |            | `COMPLETE` or `INCREMENTAL`                                                         |
| `JOB_START_TIME`   | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job starting time                                                   |
| `JOB_END_TIME`     | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job ending time                                                     |
| `ROW_UPDATE_COUNT` | `NUMBER`                      |            | Number of rows have been updated for static ACL sync                                |
| `STATUS`           | `NUMBER`                      |            | Refreshment job status:<br>0 means success, otherwise an error number is displayed. |
| `ERROR_MESSAGE`    | `VARCHAR2(4000)`              |            | The error message for the error, if there is any.                                   |

### 9.60 USER_XDS_ACL_REFRESH

The `USER_XDS_ACL_REFRESH` data dictionary view displays all static ACL refresh settings for tables that are owned by the user.

#### Related Views

- ALL_XDS_ACL_REFRESH

- DBA_XDS_ACL_REFRESH

| Column             | Datatype                      | NULL       | Description                                                            |
|:-------------------|:------------------------------|:-----------|:-----------------------------------------------------------------------|
| `SCHEMA_NAME`      | `VARCHAR2(128`)               | `NOT NULL` | Name of schema                                                         |
| `TABLE_NAME`       | `VARCHAR2(128)`               | `NOT NULL` | Name of table                                                          |
| `ACL_MVIEW_NAME`   | `VARCHAR2(128)`               | `NOT NULL` | Name of ACL MV for this table                                          |
| `REFRESH_MODE`     | `VARCHAR2(9)`                 |            | `ON COMMIT`, `SCHEDULED`, or `ON DEMAND`                               |
| `REFRESH_ABILITY`  | `VARCHAR2(11)`                |            | `COMPLETE` or `INCREMENTAL`                                            |
| `ACL_STATUS`       | `VARCHAR2(5)`                 |            | `STALE` or `FRESH`                                                     |
| `USER_SUPPLIED_MV` | `VARCHAR2(1)`                 |            | `Y` or `N`                                                             |
| `START_DATE`       | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job scheduled to run after the timestamp, if scheduled |
| `REPEAT_INTERVAL`  | `VARCHAR2(4000)`              |            | The `repeat_interval` to run the refreshment job, if scheduled.        |
| `REFRESH_COUNT`    | `NUMBER`                      |            | Number of refreshment has been done so far                             |
| `COMMENTS`         | `VARCHAR2(240)`               |            | Comments for the refreshment                                           |

### 9.61 USER_XDS_ACL_REFSTAT

The `USER_XDS_ACL_REFSTAT` data dictionary view displays all static ACL refresh job status history that has been done for tables that are owned by the user.

#### Related Views

- ALL_XDS_ACL_REFSTAT

- DBA_XDS_ACL_REFSTAT

| Column             | Datatype                      | NULL       | Description                                                                         |
|:-------------------|:------------------------------|:-----------|:------------------------------------------------------------------------------------|
| `SCHEMA_NAME`      | `VARCHAR2(128`)               | `NOT NULL` | Name of schema                                                                      |
| `TABLE_NAME`       | `VARCHAR2(128)`               | `NOT NULL` | Name of table                                                                       |
| `REFRESH_MODE`     | `VARCHAR2(9)`                 |            | `ON COMMIT`, `SCHEDULED`, or `ON DEMAND`                                            |
| `REFRESH_ABILITY`  | `VARCHAR2(11)`                |            | `COMPLETE` or `INCREMENTAL`                                                         |
| `JOB_START_TIME`   | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job starting time                                                   |
| `JOB_END_TIME`     | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job ending time                                                     |
| `ROW_UPDATE_COUNT` | `NUMBER`                      |            | Number of rows have been updated for static ACL sync                                |
| `STATUS`           | `NUMBER`                      |            | Refreshment job status:<br>0 means success, otherwise an error number is displayed. |
| `ERROR_MESSAGE`    | `VARCHAR2(4000)`              |            | The error message for the error, if there is any.                                   |

### 9.62 USER_XDS_LATEST_ACL_REFSTAT

The `USER_XDS_LATEST_ACL_REFSTAT` data dictionary view displays all latest static ACL refresh job status history that has been done for tables that are owned by the user. It has the same schema as `USER_XDS_ACL_REFSTAT` dictionary view, but a subset of its rows.

#### Related Views

- ALL_XDS_LATEST_ACL_REFSTAT

- DBA_XDS_LATEST_ACL_REFSTAT

- USER_XDS_ACL_REFSTAT

| Column             | Datatype                      | NULL       | Description                                                                         |
|:-------------------|:------------------------------|:-----------|:------------------------------------------------------------------------------------|
| `SCHEMA_NAME`      | `VARCHAR2(128`)               | `NOT NULL` | Name of schema                                                                      |
| `TABLE_NAME`       | `VARCHAR2(128)`               | `NOT NULL` | Name of table                                                                       |
| `REFRESH_MODE`     | `VARCHAR2(9)`                 |            | `ON COMMIT`, `SCHEDULED`, or `ON DEMAND`                                            |
| `REFRESH_ABILITY`  | `VARCHAR2(11)`                |            | `COMPLETE` or `INCREMENTAL`                                                         |
| `JOB_START_TIME`   | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job starting time                                                   |
| `JOB_END_TIME`     | `TIMESTAMP(6) WITH TIME ZONE` |            | The refreshment job ending time                                                     |
| `ROW_UPDATE_COUNT` | `NUMBER`                      |            | Number of rows have been updated for static ACL sync                                |
| `STATUS`           | `NUMBER`                      |            | Refreshment job status:<br>0 means success, otherwise an error number is displayed. |
| `ERROR_MESSAGE`    | `VARCHAR2(4000)`              |            | The error message for the error, if there is any.                                   |

### 9.63 V\$XS_SESSION_NS_ATTRIBUTES

The `V$XS_SESSION_NS_ATTRIBUTES` dynamic data dictionary view displays information about the namespaces and attributes in all application sessions in the database as of the end of the last request. The state of any active request is not reflected in this view. Only database administrators can select from this view.

#### Related Views

- DBA_XS_SESSIONS

- DBA_XS_SESSION_NS_ATTRIBUTES

- V\$XS_SESSION_ROLES

| Column                    | Datatype         | NULL | Description                                      |
|:--------------------------|:-----------------|:-----|:-------------------------------------------------|
| `NAMESPACE_NAME`          | `VARCHAR2(4000)` |      | Name of the namespace                            |
| `WORKSPACE_NAME`          | `VARCHAR2(129)`  |      | Name of the workspace space for the namespace    |
| `ATTRIBUTE_NAME`          | `VARCHAR2(4000)` |      | Name of the attribute                            |
| `ATTRIBUTE_VALUE`         | `VARCHAR2(4000)` |      | Value of the attribute                           |
| `ATTRIBUTE_EVENTS`        | `VARCHAR2(4000)` |      | Events associated with this attribute            |
| `ATTRIBUTE_DEFAULT_VALUE` | `VARCHAR2(4000)` |      | Default value for the attribute                  |
| `ATTRIBUTE_TYPE`          | VARCHAR2(4000)   |      | Type of attribute, either `TEMPLATE` or `CUSTOM` |
| `CON_ID`                  | `NUMBER`         |      | Container ID                                     |

### 9.64 V\$XS_SESSION_ROLES

The `V$XS_SESSION_ROLES` static data dictionary view displays all enabled application roles in application session in the current request.

#### Related Views

- DBA_XS_SESSIONS

- DBA_XS_SESSION_ROLES

- V\$XS_SESSION_NS_ATTRIBUTES

| Column        | Datatype         | NULL | Description                            |
|:--------------|:-----------------|:-----|:---------------------------------------|
| `ROLE_WSPACE` | `VARCHAR2(129)`  |      | The workspace of the application role. |
| `ROLE_NAME`   | `VARCHAR2(4000`) |      | Name of enabled application role       |
| `FLAGS`       | `NUMBER`         |      | Status flag                            |
| `CON_ID`      | `NUMBER`         |      | Container ID                           |
