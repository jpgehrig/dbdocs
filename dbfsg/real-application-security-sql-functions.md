## 10  Oracle Database Real Application Security SQL Functions

This chapter describes the SQL functions and procedures that are available with Oracle Database Real Application Security.

Table 10-1 summarizes these functions and procedures. Detailed information on each function and procedure follows this table.

Table 10-1 Oracle Database Real Application Security SQL Functions and Procedures

| SQL Function or Procedure      | Brief Description                                                                                                                |
|:-------------------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| COLUMN_AUTH_INDICATOR Function | Checks whether the specified table column is authorized on a particular table row.                                               |
| XS_SYS_CONTEXT Function        | Retrieves the session attributes and the `XS$GLOBAL_VAR` namespace attribute for the current application session.                |
| ORA_CHECK_ACL Function         | Checks whether an application user has the queried application privileges according to a list of ACLs.                           |
| ORA_GET_ACLIDS Function        | Returns a list of ACL identifiers associated with an object instance of the XDS-enabled tables for the current application user. |
| ORA_CHECK_PRIVILEGE Function   | Checks whether the specified system privileges have been granted to an application user                                          |
| TO_ACLID Function              | Returns the ACL IDs of the supplied ACL names                                                                                    |

### 10.1 COLUMN_AUTH_INDICATOR Function

The `COLUMN_AUTH_INDICATOR` function checks whether the specified table column is authorized on a particular table row. If the current application user is authorized by data security policies to access the column value of the current row, or if the column is not protected by any data security policies, then it returns 1. If the application user is not authorized, it returns `0`.

#### Syntax

    COLUMN_AUTH_INDICATOR(col)
    RETURN BOOLEAN;

#### Parameters

| Parameter | Description                                                                                        |
|:----------|:---------------------------------------------------------------------------------------------------|
| `col`     | A column in a table or view.<br>This parameter does not accept object type columns or expressions. |

#### Example

    SELECT po_number, project_id, region,
     DECODE(COLUMN_AUTH_INDICATOR(price), 0, 'xxxxxx', 1, price) price
     FROM purchaseorder
     WHERE po_number
     BETWEEN 10000 and 10003;

**See Also:**

- "[Applying Additional Application Privileges to a Column](configuring-data-security.md)" for more detailed example of using the `COLUMN_AUTH_INDICATOR` function

- [Oracle Database Real Application Security Data Dictionary Views](real-application-security-data-dictionary-views.md) for information about the `ALL_ATTRIBUTE_SECS`, `DBA_ATTRIBUTE_SECS`, and `USER_ATTRIBUTE_SECS` data dictionary views, which list existing tables that use column level security

### 10.2 XS_SYS_CONTEXT Function

The `XS_SYS_CONTEXT` function provides quick access to session attributes in the current application session without incurring the overhead that results from using the PL/SQL APIs. The `SYS_XS_CONTEXT` function definition mirrors that of the `SYS_CONTEXT` function and can be described as application session counterpart to `SYS_CONTEXT`. `XS_SYS_CONTEXT` returns the requested namespace and attribute. If they do not exist, then it returns `NULL`.

Table 10-2 lists the attributes in predefined namespace `XS$SESSION`.

Table 10-2 Predefined Parameters

| Parameter                | Return Value                                                                                                                                                                                                                     |
|:-------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CREATED_BY               | The owner who created the current application session.                                                                                                                                                                           |
| CREATE_TIME              | The time in which the current application session was created.                                                                                                                                                                   |
| COOKIE                   | The secure session cookie, passed as the parameter, that can be used to identify the newly created Real Application Security application session in future calls, until the cookie value is changed or the session is destroyed. |
| CURRENT_XS_USER          | The name of the Real Application Security session application user whose privileges are currently active.                                                                                                                        |
| CURRENT_XS_USER_GUID     | The identifier of the Real Application Security session application user whose privileges are currently active.                                                                                                                  |
| INACTIVITY_TIMEOUT       | The specified inactivity timeout value in minutes for the current application session.                                                                                                                                           |
| LAST_ACCESS_TIME         | The last time the session was accessed by a session application user.                                                                                                                                                            |
| LAST_AUTHENTICATION_TIME | The last time the session application user was authenticated.                                                                                                                                                                    |
| LAST_UPDATED_BY          | The last time the application session was updated.                                                                                                                                                                               |
| PROXY_GUID               | Identifier of the Real Application Security session application user who opened the current session on behalf of `SESSION_XS_USER`.                                                                                              |
| SESSION_ID               | The session identifier for the application session.                                                                                                                                                                              |
| SESSION_XS_USER          | The name of the Real Application Security session application user at logon.                                                                                                                                                     |
| SESSION_XS_USER_GUID     | The identifier of the Real Application Security session application user at logon.                                                                                                                                               |
| USERNAME                 | The session application user name.                                                                                                                                                                                               |
| USER_ID                  | The identifier of the session application user.                                                                                                                                                                                  |

To retrieve the name of the currently attached Real Application Security session application user, you can use the following form of the `XS_SYS_CONTEXT` function:

    XS_SYS_CONTEXT('XS$SESSION', 'SESSION_XS_USER')

The function returns `NULL` if no Real Application Security session is currently attached to the database session. The function returns the currently attached Real Application Security session application user even if it is called from within the body of a definer's rights unit, like a definer's rights view.

To retrieve the identifier (ID) for the currently attached Real Application Security session application user, you can use the following form of the `XS_SYS_CONTEXT` function:

    XS_SYS_CONTEXT('XS$SESSION', 'SESSION_XS_USER_GUID')

The function returns `NULL` if no Real Application Security session is currently attached to the database session. The function returns the currently attached Real Application Security session application user ID even if it is called from within the body of a definer's rights unit, like a definer's rights view.

#### Syntax

    XS_SYS_CONTEXT(
     namespace   IN VARCHAR2
     attribute   IN VARCHAR2)
    RETURN VARCHAR2;

#### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                              |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `namespace` | The name of the application context. You can specify either a string or an expression.<br>To find information about the namespaces and attributes for the current application session, query the [V\$XS_SESSION_NS_ATTRIBUTES](real-application-security-data-dictionary-views.md) data dictionary view. |
| `attribute` | A parameter within the `namespace` application context.                                                                                                                                                                                                                                                  |

#### Example

    SELECT XS_SYS_CONTEXT('XS$SESSION', 'SESSION_ID') FROM DUAL;

### 10.3 ORA_CHECK_ACL Function

The `ORA_CHECK_ACL` function checks whether an application user has the queried application privileges according to a list of ACLs. Oracle Database uses this function automatically when the application user runs a query on a table that has data security policy enabled. If the specified application privileges have been granted to the application user, `ORA_CHECK_ACL` returns `1`. If they are not granted to the application user, then it returns `0`.

#### Syntax

    ORA_CHECK_ACL(
     acls        IN RAW,
     (privileges IN VARCHAR(128))+)
    return NUMBER;

#### Parameters

| Parameter    | Description                                                                                                 |
|:-------------|:------------------------------------------------------------------------------------------------------------|
| `acls`       | RAW list of ACL ids of 8 byte. The maximum number of acls allowed is 250.                                   |
| `privileges` | The application privilege names being checked. The maximum number of application privileges allowed is 100. |

#### Examples

The following example uses `ORA_CHECK_ACL` to check whether the application user has been granted the `P1` and `P2` application privileges in the `ACL1` ACL.

    SELECT ORA_CHECK_ACL(TO_ACLID('ACL1'),'P1', 'P2') INTO ACLRESULT FROM DUAL;

### 10.4 ORA_GET_ACLIDS Function

The `ORA_GET_ACLIDS` function returns a list of ACL IDS associated with an object instance of data security policy enabled tables for the current application user. Oracle Database evaluates every dynamic data realm constraint rule, because `ORA_GET_ACLIDS` captures all ACL identifiers that are associated with the matching data realm constraints, if access to the current row has been granted. If the data realm constraints are from detail tables in a master-detail relationship, `ORA_GET_ACLIDS` retrieves the ACL identifiers from the master table as well as the detail table. If multiple data security policies have been applied to a table, `ORA_GET_ACLIDS` returns the ACLs associated with each policy.

#### Syntax

    ORA_GET_ACLIDS (
     table_alias  IN VARCHAR2,
     (privileges IN VARCHAR(128))+)
    RETURN RAW;

#### Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                  |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_alias` | Table or view object alias in the query from a clause.<br>Ensure that the table is XDS-enabled. To do so, query the [DBA_XS_APPLIED_POLICIES](real-application-security-data-dictionary-views.md) data dictionary view.<br>If you specify a view that is resolved to XDS-enabled tables, and if there are more than one XDS-enabled tables in the view, then Oracle Database only returns one of the tables. |
| `privileges`  | The application privilege names that are associated with the returned ACL identifiers. The maximum number of application privileges allowed is 100.                                                                                                                                                                                                                                                          |

#### Example

    SELECT ORA_GET_ACLIDS(t, 'SELECT', 'VIEW_LOC') from SCOTT.DEPT t;

### 10.5 ORA_CHECK_PRIVILEGE Function

The `ORA_CHECK_PRIVILEGE` function checks whether the specified privileges have been granted to an application user. If the specified privileges have been granted to the application user, `ORA_CHECK_PRIVILEGE` returns `1`. This function only works for system privileges, such as `CREATE_SESSION`. If the system privileges are not granted to the application user, then it returns `0`.

#### Syntax

    ORA_CHECK_PRIVILEGE(
     (privs IN VARCHAR(128))+)
    return NUMBER;

#### Parameters

| Parameter | Description                                                                         |
|:----------|:------------------------------------------------------------------------------------|
| `privs`   | The privilege names being checked. The maximum number of privileges allowed is 100. |

#### Examples

The following example uses `ORA_CHECK_PRIVILEGE` to check whether the application user has been granted the `CREATE_SESSION` system privilege.

    SELECT ORA_CHECK_PRIVILEGE('CREATE_SESSION') FROM DUAL;

### 10.6 TO_ACLID Function

The `TO_ACLID` function returns the ACL IDs of the ACL names supplied to it.

#### Syntax

    TO_ACLID(
     (acls IN VARCHAR(128))+)
    return NUMBER;

#### Parameters

| Parameter | Description                               |
|:----------|:------------------------------------------|
| `acls`    | The ACL names whose ACL IDs are returned. |

#### Examples

The following example uses the `TO_ACLID` function to return the ACL ID for ACL1.

    SELECT ORA_CHECK_ACL(TO_ACLID('ACL1'),'P1', 'P2') INTO ACLRESULT FROM DUAL;
