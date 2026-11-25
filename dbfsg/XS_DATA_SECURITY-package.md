## 11.4 XS_DATA_SECURITY Package

The `XS_DATA_SECURITY` package includes procedures to create, manage, and delete data security policies, associated data realm constraints, column constraints, and ACL parameters.

This section includes the following topics:

- [Security Model](XS_DATA_SECURITY_UTIL-package.md)

- Object Types, Constructor Functions, Synonyms, and Grants

- Summary of XS_DATA_SECURITY Subprograms

### 11.4.1 Security Model for the XS_DATA_SECURITY Package

The `XS_DATA_SECURITY` package is created under the `SYS` schema. The `DBA` role is granted the `ADMIN_ANY_SEC_POLICY`, which allows it to administer schema objects like ACLs, security classes, and security policies across all schemas. In addition, users granted the `ADMIN_ANY_SEC_POLICY` can call the following procedures: `ENABLE_OBJECT_POLICY`, `DISABLE_OBJECT_POLICY`, `APPLY_OBJECT_POLICY`, and `REMOVE_OBJECT_POLICY`.

Users can administer schema objects in their own schema if they have been granted the `RESOURCE` role for the schema. The `RESOURCE` role and the `XS_RESOURCE` application role include the `ADMIN_SEC_POLICY` privilege, required to administer schema objects in the schema as well as administering the policy artifacts within the granted schema to achieve policy management within an application.

Users can administer policy enforcement on the schema if they have been granted the `APPLY_SEC_POLICY` privilege. With this privilege, the user can administer policy enforcement within granted schemas to achieve policy management within an application.

### 11.4.2 Object Types, Constructor Functions, Synonyms, and Grants

The following object types, constructor functions, synonyms, and `GRANT` statements are defined for this package.

    -- Create a type for key
    CREATE OR REPLACE TYPE XS$KEY_TYPE AS OBJECT (
    primary_key      VARCHAR2(130),
    foreign_key      VARCHAR2(4000),
    -- Foreign key type; 1 = col name, 2 = col value
    foreign_key_type NUMBER,
    -- Constructor function
    CONSTRUCTOR FUNCTION XS$KEY_TYPE
                         (primary_key      IN VARCHAR2,
                          foreign_key      IN VARCHAR2,
                          foreign_key_type IN NUMBER)
                          RETURN SELF AS RESULT,

    MEMBER FUNCTION GET_PRIMARY_KEY RETURN VARCHAR2,
    MEMBER FUNCTION GET_FOREIGN_KEY RETURN VARCHAR2,
    MEMBER FUNCTION GET_FOREIGN_KEY_TYPE RETURN NUMBER,
    );
    CREATE OR REPLACE TYPE XS$KEY_LIST AS VARRAY(1000) OF XS$KEY_TYPE;
    CREATE OR REPLACE TYPE XS$REALM_CONSTRAINT_TYPE AS OBJECT (
    -- Member variables
    realm_type    NUMBER,
    -- Member evaluation rule
    realm              VARCHAR2(4000),
    -- acl list of instance set
    acl_list              XS$NAME_LIST,
    -- isStatic variable for instance set. Stored as INTEGER. No boolean datatype
    -- for objects. False is stored as 0 and TRUE is stored as 1
    is_static          INTEGER,
    -- Indicate if the realm is parameterized.
    parameterized      INTEGER,
    -- parent schema name for inherited from
    parent_schema      VARCHAR2(130),
    -- parent object name for inherited from
    parent_object      VARCHAR2(130),
    -- keys for inherited from
    key_list           XS$KEY_LIST,
    -- when condition for inherited from
    when_condition     VARCHAR2(4000),

    -- Constructor function - row_level realm
    CONSTRUCTOR FUNCTION XS$REALM_CONSTRAINT_TYPE
                         (realm                  IN VARCHAR2,
                          acl_list               IN XS$NAME_LIST,
                          is_static              IN BOOLEAN := FALSE)
                          RETURN SELF AS RESULT,

    -- Constructor function - parameterized row_level realm
    CONSTRUCTOR FUNCTION XS$REALM_CONSTRAINT_TYPE
                         (realm                  IN VARCHAR2,
                          is_static              IN BOOLEAN := FALSE)
                          RETURN SELF AS RESULT,

    -- Constructor function - master realm
    CONSTRUCTOR FUNCTION XS$REALM_CONSTRAINT_TYPE
                         (parent_schema  IN VARCHAR2,
                          parent_object  IN VARCHAR2,
                          key_list       IN XS$KEY_LIST,
                          when_condition IN VARCHAR2:= NULL)
                          RETURN SELF AS RESULT,

    -- Accessor functions
    MEMBER FUNCTION GET_TYPE RETURN NUMBER,
    MEMBER FUNCTION GET_REALM RETURN VARCHAR2,
    MEMBER FUNCTION GET_ACLS RETURN XS$NAME_LIST,
    MEMBER FUNCTION IS_DYNAMIC_REALM RETURN BOOLEAN,
    MEMBER FUNCTION IS_STATIC_REALM RETURN BOOLEAN,
    MEMBER FUNCTION IS_PARAMETERIZED_REALM RETURN BOOLEAN,
    MEMBER FUNCTION GET_KEYS RETURN XS$KEY_LIST,
    MEMBER FUNCTION GET_PARENT_SCHEMA RETURN VARCHAR2,
    MEMBER FUNCTION GET_PARENT_OBJECT RETURN VARCHAR2,
    MEMBER FUNCTION GET_WHEN_CONDITION RETURN VARCHAR2,
    MEMBER PROCEDURE SET_REALM(realm IN VARCHAR2),
    MEMBER PROCEDURE ADD_ACLS(acl      IN VARCHAR2),
    MEMBER PROCEDURE ADD_ACLS(acl_list IN XS$NAME_LIST),
    MEMBER PROCEDURE SET_ACLS(acl_list IN XS$NAME_LIST),
    MEMBER PROCEDURE SET_DYNAMIC,
    MEMBER PROCEDURE SET_STATIC,
    MEMBER PROCEDURE ADD_KEYS(key IN XS$KEY_TYPE),
    MEMBER PROCEDURE ADD_KEYS(key_list IN XS$KEY_LIST),
    MEMBER PROCEDURE SET_KEYS(key_list IN XS$KEY_LIST),
    MEMBER PROCEDURE SET_PARENT_SCHEMA(parent_schema IN VARCHAR2),
    MEMBER PROCEDURE SET_PARENT_OBJECT(parent_object IN VARCHAR2),
    MEMBER PROCEDURE SET_WHEN_CONDITION(when_condition IN VARCHAR2)
    );
    -- Create a list of realm constraint type
    CREATE OR REPLACE TYPE XS$REALM_CONSTRAINT_LIST AS VARRAY(1000)
                           OF XS$REALM_CONSTRAINT_TYPE;
    -- Create a type for column(attribute) security
    CREATE OR REPLACE TYPE XS$COLUMN_CONSTRAINT_TYPE AS OBJECT (
    -- column list
    column_list        XS$LIST,
    -- privilege for column security
    privilege          VARCHAR2(261),
    -- Constructor function
    CONSTRUCTOR FUNCTION XS$COLUMN_CONSTRAINT_TYPE
                         (column_list  IN XS$LIST,
                          privilege    IN VARCHAR2)
                          return SELF AS RESULT,
    MEMBER FUNCTION GET_COLUMNS RETURN XS$LIST,
    MEMBER FUNCTION GET_PRIVILEGE RETURN VARCHAR2,
    MEMBER PROCEDURE ADD_COLUMNS(column IN VARCHAR2),
    MEMBER PROCEDURE ADD_COLUMNS(column_list IN XS$LIST),
    MEMBER PROCEDURE SET_COLUMNS(column_list IN XS$LIST),
    MEMBER PROCEDURE SET_PRIVILEGE(privilege IN VARCHAR2)
    );
    -- Create a list of column constraint for column security
    CREATE OR REPLACE TYPE XS$COLUMN_CONSTRAINT_LIST
                           IS VARRAY(1000) of XS$COLUMN_CONSTRAINT_TYPE;

### 11.4.3 Summary of XS_DATA_SECURITY Subprograms

Table 11-5 Summary of XS_DATA_SECURITY Subprograms

| Subprogram                          | Brief Description                                                            |
|:------------------------------------|:-----------------------------------------------------------------------------|
| CREATE_POLICY Procedure             | Creates a new data security policy.                                          |
| APPEND_REALM_CONSTRAINTS Procedure  | Adds one or more data realm constraints to an existing data security policy. |
| REMOVE_REALM_CONSTRAINTS Procedure  | Removes all data realm constraints for the specified data security policy.   |
| ADD_COLUMN_CONSTRAINTS Procedure    | Adds one or more column constraint to the specified data security policy.    |
| REMOVE_COLUMN_CONSTRAINTS Procedure | Removes all column constraints from a data security policy.                  |
| CREATE_ACL_PARAMETER Procedure      | Creates an ACL parameter for the specified data security policy.             |
| DELETE_ACL_PARAMETER Procedure      | Deletes an ACL parameter from the specified data security policy.            |
| SET_DESCRIPTION Procedure           | Sets a description string for the specified data security policy.            |
| DELETE_POLICY Procedure             | Deletes a data security policy.                                              |

Table 11-6 Summary of XS_DATA_SECURITY Subprograms for Managing Data Security Policies on Tables or Views

| Subprogram                      | Brief Description                                                                        |
|:--------------------------------|:-----------------------------------------------------------------------------------------|
| ENABLE_OBJECT_POLICY Procedure  | Enables the data security policy for the specified table or view.                        |
| DISABLE_OBJECT_POLICY Procedure | Disables the data security policy for the specified table or view.                       |
| REMOVE_OBJECT_POLICY Procedure  | Removes or drops the data security from the specified table or view without deleting it. |
| APPLY_OBJECT_POLICY Procedure   | Enables or reenables the data security policy for the specified table or view.           |

This section describes the following XS_DATA_SECURITY subprograms:

#### 11.4.3.1 CREATE_POLICY Procedure

The `CREATE_POLICY` procedure creates a new data security policy.

##### Syntax

    XS_DATA_SECURITY.CREATE_POLICY (
      name                   IN VARCHAR2,
      realm_constraint_list  IN XS$REALM_CONSTRAINT_LIST,
      column_constraint_list IN XS$COLUMN_CONSTRAINT_LIST := NULL,
      description            IN VARCHAR2 :=NULL) ;

##### Parameters

| Parameter                | Description                                                                                                                                                                                                                                                                                                                                               |
|:-------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`                   | The name for the data security policy to be created.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`. |
| `realm_constraint_list`  | The list of data realm constraints, which determine the rows to be protected by the data security policy.                                                                                                                                                                                                                                                 |
| `column_constraint_list` | This is optional. The list of attributes and the privileges protecting them.                                                                                                                                                                                                                                                                              |
| `description`            | An optional description for the data security policy.                                                                                                                                                                                                                                                                                                     |

##### Examples

The following example creates a data security policy called `USER1.EMPLOYEES_DS`. It uses a data realm constraint to protect data related to department numbers `60 `and `100`. In addition, access to the `SALARY` column (attribute) is restricted using an column constraint.

    DECLARE
      realm_cons XS$REALM_CONSTRAINT_LIST;
      column_cons XS$COLUMN_CONSTRAINT_LIST;
    BEGIN
      realm_cons :=
        XS$REALM_CONSTRAINT_LIST(
          XS$REALM_CONSTRAINT_TYPE(realm=> 'DEPARTMENT_ID in (60, 100)',
                                   acl_list=> XS$NAME_LIST('HRACL')));

      column_cons :=
        XS$COLUMN_CONSTRAINT_LIST(
          XS$COLUMN_CONSTRAINT_TYPE(column_list=> XS$LIST('SALARY'),
                                privilege=> 'VIEW_SENSITIVE_INFO'));

      SYS.XS_DATA_SECURITY.CREATE_POLICY(
              name=>'USER1.EMPLOYEES_DS',
              realm_constraint_list=>realm_cons,
              column_constraint_list=>column_cons);
    END;

#### 11.4.3.2 APPEND_REALM_CONSTRAINTS Procedure

The `APPEND_REALM_CONSTRAINTS` procedure adds one or more data realm constraints to an existing data security policy.

##### Syntax

    XS_DATA_SECURITY.APPEND_REALM_CONSTRAINTS (
      policy           IN VARCHAR2,
      realm_constraint IN XS$REALM_CONSTRAINT_TYPE);

    XS_DATA_SECURITY.APPEND_REALM_CONSTRAINTS (
      policy                IN VARCHAR2,
      realm_constraint_list IN XS$REALM_CONSTRAINT_LIST);

##### Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                                                                                                                                    |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy`                | The name of the data security policy to which the data realm constraints are to be added.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`. |
| `realm_constraint`      | The data realm constraint to be added to the data security policy.                                                                                                                                                                                                                                                                                                                             |
| `realm_constraint_list` | The list of data realm constraints to be added to the data security policy.                                                                                                                                                                                                                                                                                                                    |

##### Examples

The following example appends a new data realm constraint to the `EMPLOYEES_DS` data security policy.

    DECLARE
      realm_cons XS$REALM_CONSTRAINT_TYPE;
    BEGIN
      realm_cons :=
          XS$REALM_CONSTRAINT_TYPE(realm=> 'DEPARTMENT_ID in (40, 50)',
                                   acl_list=> XS$NAME_LIST('HRACL'));

      SYS.XS_DATA_SECURITY.APPEND_REALM_CONSTRAINTS(
              policy=>'EMPLOYEES_DS',
              realm_constraint=>realm_cons);
    END;

#### 11.4.3.3 REMOVE_REALM_CONSTRAINTS Procedure

The `REMOVE_REALM_CONSTRAINTS` procedure removes all data realm constraints from a data security policy.

##### Syntax

    XS_DATA_SECURITY.REMOVE_REALM_CONSTRAINTS (
      policy IN VARCHAR2);

##### Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                        |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy`  | The name of the data security policy from which the data realm constraints are to be removed.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`. |

##### Examples

The following example removes all data realm constraints from the `EMPLOYEES_DS` data security policy.

    BEGIN
      SYS.XS_DATA_SECURITY.REMOVE_REALM_CONSTRAINTS('EMPLOYEES_DS');
    END;

#### 11.4.3.4 ADD_COLUMN_CONSTRAINTS Procedure

The `ADD_COLUMN_CONSTRAINTS` procedure adds one or more column constraint to a data security policy.

##### Syntax

    XS_DATA_SECURITY.ADD_COLUMN_CONSTRAINTS (
      policy            IN VARCHAR2,
      column_constraint IN XS$COLUMN_CONSTRAINT_TYPE);

    XS_DATA_SECURITY.ADD_COLUMN_CONSTRAINTS (
      policy                 IN VARCHAR2,
      column_constraint_list IN XS$COLUMN_CONSTRAINT_LIST);

##### Parameters

| Parameter                | Description                                                                                                                                                                                                                                                                                                                                                                                   |
|:-------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy`                 | The name of the data security policy to which the attribute constraints are to be added.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`. |
| `column_constraint`      | The column constraint to be added.                                                                                                                                                                                                                                                                                                                                                            |
| `column_constraint_list` | The list of column constraints to be added.                                                                                                                                                                                                                                                                                                                                                   |

##### Examples

The following example adds a column constraint on the `COMMISSION_PCT` column in the `EMPLOYEES_DS` data security policy:

    DECLARE
      column_cons XS$COLUMN_CONSTRAINT_TYPE;
    BEGIN
      column_cons :=
          XS$COLUMN_CONSTRAINT_TYPE(column_list=> XS$LIST('COMMISSION_PCT'),
                                privilege=> 'VIEW_SENSITIVE_INFO');

      SYS.XS_DATA_SECURITY.ADD_COLUMN_CONSTRAINTS(
              policy=>'EMPLOYEES_DS',
              column_constraint=>column_cons);
    END;

#### 11.4.3.5 REMOVE_COLUMN_CONSTRAINTS Procedure

The `REMOVE_COLUMN_CONSTRAINTS` procedure removes all column constraints from a data security policy.

##### Syntax

    XS_DATA_SECURITY.REMOVE_COLUMN_CONSTRAINTS (
      policy IN VARCHAR2,);

##### Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                   |
|:----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy`  | The name of the data security policy for which the column constraints are to be removed.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`. |

##### Examples

The following example removes all column constraints from the `EMPLOYEES_DS` data security policy:

    BEGIN
      SYS.XS_DATA_SECURITY.REMOVE_COLUMN_CONSTRAINTS('EMPLOYEES_DS');
    END;

#### 11.4.3.6 CREATE_ACL_PARAMETER Procedure

The `CREATE_ACL_PARAMETER` procedure creates an ACL parameter for a data security policy.

##### Syntax

    XS_DATA_SECURITY.CREATE_ACL_PARAMETER (
      policy     IN VARCHAR2,
      parameter  IN VARCHAR2,
      param_type IN NUMBER);

##### Parameters

| Parameter    | Description                                                                                                                                                                                                                                                                                                                                                                                |
|:-------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy`     | The name of the data security policy for which the ACL parameter needs to be created.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`. |
| `parameter`  | The name of the ACL parameter to be created.                                                                                                                                                                                                                                                                                                                                               |
| `param_type` | The data type of the parameter. This can be `1` (NUMBER) or `2` (VARCHAR).                                                                                                                                                                                                                                                                                                                 |

##### Examples

The following examples creates an ACL parameter, called `DEPT_POLICY`, for the `EMPLOYEES_DS` data security policy:

    BEGIN
      SYS.XS_DATA_SECURITY.CREATE_ACL_PARAMETER('EMPLOYEES_DS','DEPT_POLICY',1);
    END;

#### 11.4.3.7 DELETE_ACL_PARAMETER Procedure

The `DELETE_ACL_PARAMETER` procedure deletes an ACL parameter for a data security policy.

##### Syntax

    XS_DATA_SECURITY.DELETE_ACL_PARAMETER (
      policy                IN VARCHAR2,
      parameter             IN VARCHAR2,
      delete_option         IN PLS_INTEGER := XS_ADMIN_UTIL.DEFAULT_OPTION);

##### Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy`        | The name of the data security policy for which the ACL parameter is to be deleted.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`.                                                                                                                                                                                                                                                                                                                                                                                          |
| `parameter`     | The name of the ACL parameter to be deleted.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `delete_option` | The delete option to use. The following options are available:<br>• `DEFAULT_OPTION` (default):<br>• The default option allows deleting an ACL parameter only if it is not referenced elsewhere. If there are other entities that reference the ACL parameter, then the ACL parameter cannot be deleted.<br>• `CASCADE_OPTION`:<br>• The cascade option deletes the ACL parameter together with any references to it.The user deleting the security class must have privileges to delete these references as well.<br>• `ALLOW_INCONSISTENCIES_OPTION: `<br>• The allow inconsistencies option lets you delete the entity even if other entities have late binding references to it. If the entity is part of an early dependency, then the delete fails and an error is raised. |

##### Examples

The following example deletes the `DEPT_POLICY` ACL parameter from the `EMPLOYEES_DS` data security policy, using the default option.

    BEGIN
      SYS.XS_DATA_SECURITY.DELETE_ACL_PARAMETER('EMPLOYEES_DS','DEPT_POLICY',
                                                XS_ADMIN_UTIL.DEFAULT_OPTION);
    END;

#### 11.4.3.8 SET_DESCRIPTION Procedure

The `SET_DESCRPTION` procedure sets a description string for the specified data security policy.

##### Syntax

    XS_DATA_SECURITY.SET_DESCRIPTION (
      policy         IN VARCHAR2,
      description    IN VARCHAR2);

##### Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                       |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy`      | The name of the data security policy for which the description is to be set.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`. |
| `description` | A description string for the specified data security policy.                                                                                                                                                                                                                                                                                                                      |

##### Examples

The following example sets a description string for the `EMPLOYEES_DS` data security policy:

    BEGIN
      SYS.XS_DATA_SECURITY.SET_DESCRIPTION('EMPLOYEES_DS',
                                           'Data Security Policy for HR.EMPLOYEES');
    END;

#### 11.4.3.9 DELETE_POLICY Procedure

The `DELETE_POLICY` procedure deletes a data security policy.

##### Syntax

    XS_DATA_SECURITY.DELETE_POLICY(
      policy        IN VARCHAR2,
      delete_option IN PLS_INTEGER := XS_ADMIN_UTIL.DEFAULT_OPTION);

##### Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy`        | The name of the data security policy to be deleted.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `delete_option` | The delete option to use. To the security policy, the behavior of the following options is the same:<br>• `DEFAULT_OPTION:`<br>• The default option allows deleting a data security policy only if it is not referenced elsewhere. If there are other entities that reference the data security policy, then the data security policy cannot be deleted.<br>• `CASCADE_OPTION`:<br>• The cascade option deletes the data security policy together with any references to it.The user deleting the data security policy deletes these references as well.<br>• `ALLOW_INCONSISTENCIES_OPTION: `<br>• The allow inconsistencies option lets you delete the entity even if other entities have late binding references to it. If the entity is part of an early dependency, then the delete fails and an error is raised. |

##### Examples

The following example deletes the `EMPLOYEES_DS` data security policy using the default option.

    BEGIN
      SYS.XS_DATA_SECURITY.DELETE_POLICY('EMPLOYEES_DS',
                                            XS_ADMIN_UTIL.DEFAULT_OPTION);
    END;

#### 11.4.3.10 ENABLE_OBJECT_POLICY Procedure

The `ENABLE_OBJECT_POLICY` procedure enables the data security policy for the specified table or view. `ENABLE_OBJECT_POLICY` enables the ACL-based row level security policy for the table or view.

You may want to enable data security policies after you perform an import or export on the tables that it affects, or for debugging purposes.

To find the status of the data security policies for tables or views available for the current user, query the [DBA_XS_APPLIED_POLICIES](real-application-security-data-dictionary-views.md) data dictionary view.

Before enforcing policies, a check is made for the `APPLY_SEC_POLICY` privilege.

##### Syntax

    XS_DATA_SECURITY.ENABLE_OBJECT_POLICY (
     policy  IN VARCHAR2,
     schema  IN VARCHAR2,
     object  IN VARCHAR2);

##### Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                              |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy`  | The name of the data security policy to be enabled.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`. |
| `schema`  | The name of the schema that contains the table or view to enable.                                                                                                                                                                                                                                                                                        |
| `object`  | The name of the table or view to enable the data security policy.                                                                                                                                                                                                                                                                                        |

##### Examples

The following example enables XDS for the `products` table in the `sales` schema.

    BEGIN
      SYS.XS_DATA_SECURITY.ENABLE_OBJECT_POLICY(policy =>'CUST_DS', schema=>'sales', object=>'products');
    END;

#### 11.4.3.11 DISABLE_OBJECT_POLICY Procedure

The `DISABLE_OBJECT_POLICY` procedure disables the data security policy for the specified table or view. `DISABLE_OBJECT_POLICY` disables the ACL-based row level security policy for the table or view.

You may want to disable Real Application Security if you are performing an import or export on the tables that it affects, or for debugging purposes.

To find the status of the data security policies for tables or views available for the current user, query the [DBA_XS_APPLIED_POLICIES](real-application-security-data-dictionary-views.md) data dictionary view.

Before enforcing policies, a check is made for the `APPLY_SEC_POLICY` privilege.

##### Syntax

    XS_DATA_SECURITY.DISABLE_OBJECT_POLICY (
     policy  IN VARCHAR2,
     schema  IN VARCHAR2,
     object  IN VARCHAR2);

##### Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                               |
|:----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy`  | The name of the data security policy to be disabled.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`. |
| `schema`  | The name of the schema that contains the table or view to disable.                                                                                                                                                                                                                                                                                        |
| `object`  | The name of the table or view to disable a data security policy.                                                                                                                                                                                                                                                                                          |

##### Examples

The following example disables XDS for the `products` table in the `sales` schema.

    BEGIN
      SYS.XS_DATA_SECURITY.DISABLE_OBJECT_POLICY(policy =>'CUST_DS', schema=>'sales', object=>'products');
    END;

#### 11.4.3.12 REMOVE_OBJECT_POLICY Procedure

The `REMOVE_OBJECT_POLICY` procedure drops the data security policy from the specified table or view without deleting it. `REMOVE_OBJECT_POLICY` drops the ACL Materialized View built by `ENABLE_XDS` on a static data realm constraint.

To find the status of the data security policies for tables or views available for the current user, query the [DBA_XS_APPLIED_POLICIES](real-application-security-data-dictionary-views.md) data dictionary view.

Before enforcing policies, a check is made for the `APPLY_SEC_POLICY` privilege.

##### Syntax

    XS_DATA_SECURITY.REMOVE_OBJECT_POLICY (
     policy  IN VARCHAR2,
     schema  IN VARCHAR2,
     object  IN VARCHAR2);

##### Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                              |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy`  | The name of the data security policy to be dropped.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`. |
| `schema ` | The name of the schema that contains the table or view from which to remove the data security policy.                                                                                                                                                                                                                                                    |
| `object`  | The name of the table or view from which to remove the data security. policy                                                                                                                                                                                                                                                                             |

##### Examples

The following example drops the `CUST_DS` data security policy from the `products` table in the `sales` schema.

    BEGIN
      SYS.XS_DATA_SECURITY.REMOVE_OBJECT_POLICY(policy=>'CUST_DS', schema=>'sales', object=>'products');
    END;

#### 11.4.3.13 APPLY_OBJECT_POLICY Procedure

The `APPLY_OBJECT_POLICY` procedure enables or reenables the data security policy for the specified database table or view.

To find the status of the data security policies for tables or views available for the current user, query the [DBA_XS_APPLIED_POLICIES](real-application-security-data-dictionary-views.md) data dictionary view.

Before enforcing policies, a check is made for the `APPLY_SEC_POLICY` privilege.

##### Syntax

    XS_DATA_SECURITY.APPLY_OBJECT_POLICY (
     policy          IN VARCHAR2,
     schema          IN VARCHAR2,
     object          IN VARCHAR2,
     row_acl         IN BOOLEAN DEFAULT FALSE,
     owner_bypass    IN BOOLEAN DEFAULT FALSE,
     statement_types IN VARCHAR2 DEFAULT NULL,
     aclmv           IN VARCHAR2 DEFAULT NULL );

##### Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|:------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy`          | Name of the data security policy to be enabled.<br>The name is schema qualified, for example, `SCOTT.POLICY1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `POLICY1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.POLICY1`.                                                                                                                                                                                                                                                                                                                      |
| `schema `         | The name of the schema that contains the relational table or view to enable or re-enable.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `object`          | The name of the relational table or view to enable or re-enable for the data security policy.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `row_acl`         | The default is `FALSE`. When set to `TRUE`, creates the hidden column `SYS_ACLOD`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `owner_bypass`    | The owner of the object can bypass the data security policy. The default is `FALSE`.<br>**Note:**<br>The security policy will be bypassed if the user who owns the table or the view queries it. For any other user querying the table or the view, the security policy will be applied.                                                                                                                                                                                                                                                                                                                                                                                  |
| `statement_types` | The types can be: `SELECT`, `INSERT`, `UPDATE`, `DELETE`, and `INDEX`.<br>Note that if your application security requires that you must update table rows and also restrict read access to certain columns in the same table, you must use two `APPLY_OBJECT_POLICY` procedures to enforce each data security policy to ensure precise enforcement of each policy. For example, one `APPLY_OBJECT_POLICY` procedure would enforce the DML `statement_types` required for updating table rows (for example, `INSERT`, `UPDATE`, `DELETE`), while the other `APPLY_OBJECT_POLICY` procedure would enforce only the `statement_types` of `SELECT` for the column constraint. |
| `aclmv`           | Specifies a user-provided MV name that maintains static ACL information. The MV has two columns: `TABLEROWID` and `ACLIDLIST`. The default value for `aclmv` is `NULL`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

##### Examples

The following example enables the `DEPT_POLICY` data security policy for the `EMP` table in the `HR` schema.

    BEGIN
      sys.xs_data_security.apply_object_policy(
               policy => 'HR.EMPLOYEES_DS',
               schema => 'HR',
               object => 'EMPLOYEES',
               statement_types => 'SELECT',
               owner_bypass => true);
    END;
