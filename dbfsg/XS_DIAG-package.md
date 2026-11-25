## 11.6 XS_DIAG Package

The `XS_DIAG` package includes subprograms to diagnose potential problems in data security for principals, security classes, acls, data security policies, namespaces, and all objects in the work space. All subprograms return `TRUE` if the object is valid; otherwise, each returns `FALSE`. For each identified inconsistency, a row is inserted into the `XS$VALIDATION_TABLE` validation table until the maximum number of inconsistencies you specify with the `error_limit` parameter is reached. Users can query this validation table to determine the identified inconsistencies for information that includes the message code, the description about the error, the path leading to the invalid object, and any other helpful information that might assist you in identifying the nature of the inconsistency.

This section includes the following topics:

- Security Model

- Summary of XS_DIAG Subprograms

### 11.6.1 Security Model

The `XS_DIAG` package is created in the `SYS` schema. The caller has invoker's rights on this package and needs to have `ADMIN_ANY_SEC_POLICY` system privilege to run the `XS_DIAG` package. `EXECUTE` permission on the `XS_DIAG` package is granted to `PUBLIC`. `SELECT` permission on the `XS$VALIDATION_TABLE` validation table is granted to `PUBLIC`.

### 11.6.2 Summary of XS_DIAG Subprograms

Table 11-8 Summary of XS_DIAG Subprograms

| Subprogram                           | Description                                                                                        |
|:-------------------------------------|:---------------------------------------------------------------------------------------------------|
| VALIDATE_PRINCIPAL Function          | Validates the principal.                                                                           |
| VALIDATE_SECURITY_CLASS Function     | Validates the security class.                                                                      |
| VALIDATE_ACL Function                | Validates the ACL.                                                                                 |
| VALIDATE_DATA_SECURITY Function      | Validates the data security policy or validates the data security policy against a specific table. |
| VALIDATE_NAMESPACE_TEMPLATE Function | Validates the namespace template.                                                                  |
| VALIDATE_WORKSPACE Function          | Validates an entire workspace.                                                                     |

This section describes the following XS_DIAG subprograms:

#### 11.6.2.1 VALIDATE_PRINCIPAL Function

The `VALIDATE_PRINCIPAL` function validates the principal. This function returns `TRUE` if the object is valid; otherwise, it returns `FALSE`. For each identified inconsistency, a row is inserted into the `XS$VALIDATION_TABLE` validation table until the maximum number of inconsistencies that can be stored is reached. Users must query this validation table to find out what caused the validation failure.

##### Syntax

    validate_principal(name         IN VARCHAR2,
                       error_limit  IN PLS_INTEGER := 1)
       RETURN BOOLEAN;

##### Parameters

| Parameter     | Description                                                                       |
|:--------------|:----------------------------------------------------------------------------------|
| `name`        | The name of the object to be validated.                                           |
| `error_limit` | The maximum number of inconsistencies that may be stored in the validation table. |

##### Examples

Validate the principal, user `user1`, then query the validation table in case there are inconsistencies.

    begin
      if sys.xs_diag.validate_principal('user1', 100) then
        dbms_output.put_line('The user is valid.');
      else
        dbms_output.put_line('The user is invalid.');
      end if;
    end;
    /
    select * from xs$validation_table;

Validate the principal, role `role1`, then query the validation table in case there are inconsistencies.

    begin
      if sys.xs_diag.validate_principal('role1', 100) then
        dbms_output.put_line('The role is valid.');
      else
        dbms_output.put_line('The role is invalid.');
      end if;
    end;
    /
    select * from xs$validation_table;

#### 11.6.2.2 VALIDATE_SECURITY_CLASS Function

The `VALIDATE_SECURITY_CLASS` function validates the security class. This function returns `TRUE` if the object is valid; otherwise, it returns `FALSE`. For each identified inconsistency, a row is inserted into the `XS$VALIDATION_TABLE` validation table until the maximum number of inconsistencies that can be stored is reached. Users must query this validation table to find out what caused the validation failure.

##### Syntax

    validate_security_class(name         IN VARCHAR2,
                            error_limit  IN PLS_INTEGER := 1)
       RETURN BOOLEAN;

##### Parameters

| Parameter     | Description                                                                       |
|:--------------|:----------------------------------------------------------------------------------|
| `name`        | The name of the object to be validated.                                           |
| `error_limit` | The maximum number of inconsistencies that may be stored in the validation table. |

##### Examples

Validate the security class, `sec1`, then query the validation table in case there are inconsistencies.

    begin
      if sys.xs_diag.validate_security_class('sec1', 100) then
        dbms_output.put_line('The security class is valid.');
      else
        dbms_output.put_line('The security class is invalid.');
      end if;
    end;
    /
    select * from xs$validation_table;

#### 11.6.2.3 VALIDATE_ACL Function

The `VALIDATE_ACL` function validates the ACL. This function returns `TRUE` if the object is valid; otherwise, it returns `FALSE`. For each identified inconsistency, a row is inserted into the `XS$VALIDATION_TABLE` validation table until the maximum number of inconsistencies that can be stored is reached. Users must query this validation table to find out what caused the validation failure.

##### Syntax

    validate_acl(name         IN VARCHAR2,
                 error_limit  IN PLS_INTEGER := 1)
       RETURN BOOLEAN;

##### Parameters

| Parameter     | Description                                                                       |
|:--------------|:----------------------------------------------------------------------------------|
| `name`        | The name of the object to be validated.                                           |
| `error_limit` | The maximum number of inconsistencies that may be stored in the validation table. |

##### Examples

Validate the ACL, `acl1`, then query the validation table in case there are inconsistencies.

    begin
      if sys.xs_diag.validate_acl('acl1', 100) then
        dbms_output.put_line('The ACL is valid.');
      else
        dbms_output.put_line('The ACL is invalid.');
      end if;
    end;
    /
    select * from xs$validation_table;

#### 11.6.2.4 VALIDATE_DATA_SECURITY Function

The `VALIDATE_DATA_SECURITY` function validates the data security. This function returns `TRUE` if the object is valid; otherwise, it returns `FALSE`. For each identified inconsistency, a row is inserted into the `XS$VALIDATION_TABLE` validation table until the maximum number of inconsistencies that can be stored is reached. Users must query this validation table to find out what caused the validation failure.

This function has three styles of policy validation.

- When `policy` is not NULL and `table_name` is `NULL`, the function validates the policy against all the tables to which the policy is applied. Note that when `table_name` is NULL, `table_owner` is ignored even if it is not NULL.

- When both `policy` and `table_name` are not NULL, the function validates the policy against the specific table. If `table_owner` is not provided, the current schema is used.

- When policy is NULL and table_name is not NULL, the function validates all policies applied to the table against the table. If `table_owner` is not provided, the current schema is used.

##### Syntax

    validate_data_security(policy       IN VARCHAR2 :=NULL,
                           table_owner  IN VARCHAR2 :=NULL,
                           table_name   IN VARCHAR2 :=NULL,
                           error_limit  IN PLS_INTEGER := 1)
       RETURN BOOLEAN;

##### Parameters

| Parameter     | Description                                                                       |
|:--------------|:----------------------------------------------------------------------------------|
| `policy`      | The name of the object to be validated.                                           |
| `table_owner` | The name of the schema of the table or view.                                      |
| `table_name`  | The name of the table or view.                                                    |
| `error_limit` | The maximum number of inconsistencies that may be stored in the validation table. |

##### Examples

Validate a policy, `policy1` on all the applied tables, then query the validation table in case there are inconsistencies.

    begin
      if sys.xs_diag.validate_data_security(policy      => 'policy1',
                                            error_limit => 100) then
        dbms_output.put_line('The policy is valid on all the applied tables.');
      else
        dbms_output.put_line('The policy is invalid on some of the applied tables.');
      end if;
    end;
    /
    select * from xs$validation_table;

Validate a policy, `policy1` on a given table, then query the validation table in case there are inconsistencies.

    begin
      if sys.xs_diag.validate_data_security(policy      => 'policy1',
                                            table_owner => 'HR',
                                            table_name  => 'EMPLOYEES',
                                            error_limit => 100) then
        dbms_output.put_line('The policy is valid on the table.');
      else
        dbms_output.put_line('The policy is invalid on the table.');
      end if;
    end;
    /
    select * from xs$validation_table;

Validate all the policies applied to a given table, then query the validation table in case there are inconsistencies.

    begin
      if sys.xs_diag.validate_data_security(table_owner => 'HR',
                                            table_name  => 'EMPLOYEES',
                                            error_limit => 100) then
        dbms_output.put_line('All the applied policies on the table are valid.');
      else
        dbms_output.put_line('Some applied policies on the table are invalid');
      end if;
    end;
    /
    select * from xs$validation_table;

#### 11.6.2.5 VALIDATE_NAMESPACE_TEMPLATE Function

The `VALIDATE_NAMESPACE_TEMPLATE` function validates the namespace. This function returns `TRUE` if the object is valid; otherwise, it returns `FALSE`. For each identified inconsistency, a row is inserted into the `XS$VALIDATION_TABLE` validation table until the maximum number of inconsistencies that can be stored is reached. Users must query this validation table to find out what caused the validation failure.

##### Syntax

    validate_namespace_template(name         IN VARCHAR2,
                                error_limit  IN PLS_INTEGER := 1)
       RETURN BOOLEAN;

##### Parameters

| Parameter     | Description                                                                       |
|:--------------|:----------------------------------------------------------------------------------|
| `name`        | The name of the object to be validated.                                           |
| `error_limit` | The maximum number of inconsistencies that may be stored in the validation table. |

##### Examples

Validate the namespace, `ns1`, then query the validation table in case there are inconsistencies.

    begin
      if sys.xs_diag.validate_namespace_template('ns1', 100) then
        dbms_output.put_line('The namespace template is valid.');
      else
        dbms_output.put_line('The namespace template is invalid.');
      end if;
    end;
    /
    select * from xs$validation_table;

#### 11.6.2.6 VALIDATE_WORKSPACE Function

The `VALIDATE_WORKSPACE` function validates all the artifacts, in other words, it validates all objects that exist in the work space by using this one function. This function returns `TRUE` if all the objects are valid; otherwise, it returns `FALSE`. For each identified inconsistency, a row is inserted into the `XS$VALIDATION_TABLE` validation table until the maximum number of inconsistencies that can be stored is reached. Users must query this validation table to find out what caused the validation failure.

##### Syntax

    validate_workspace(error_limit  IN PLS_INTEGER := 1)
       RETURN BOOLEAN;

##### Parameters

| Parameter     | Description                                                                       |
|:--------------|:----------------------------------------------------------------------------------|
| `error_limit` | The maximum number of inconsistencies that may be stored in the validation table. |

##### Examples

Validate all the objects in the workspace, then query the validation table in case there are inconsistencies.

    begin
      if sys.xs_diag.validate_workspace(100) then
        dbms_output.put_line('The objects are valid.');
      else
        dbms_output.put_line('The objects are invalid.');
      end if;
    end;
    /
    select * from xs$validation_table;
