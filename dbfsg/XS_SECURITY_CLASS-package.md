## 11.9 XS_SECURITY_CLASS Package

The `XS_SECURITY_CLASS` package includes procedures to create, manage, and delete security classes and their privileges. The package also includes procedures for managing security class inheritance.

This section includes the following topics:

- Security Model for the XS_SECURITY_CLASS Package

- Summary of XS_SECURITY_CLASS Subprograms

### 11.9.1 Security Model for the XS_SECURITY_CLASS Package

The `XS_SECURITY_CLASS` package is created under the `SYS` schema. The `DBA` role is granted the `ADMIN_ANY_SEC_POLICY`, which allows it to administer schema objects like ACLs, security classes, and security policies across all schemas.

Users can administer schema objects in their own schema if they have been granted the `RESOURCE` role for the schema. The `RESOURCE` role and the `XS_RESOURCE` application role include the `ADMIN_SEC_POLICY` privilege, required to administer schema objects in the schema as well as administering the policy artifacts within the granted schema to achieve policy management within an application.

Users can administer policy enforcement on the schema if they have been granted the `APPLY_SEC_POLICY` privilege. With this privilege, the user can administer policy enforcement within granted schemas to achieve policy management within an application.

### 11.9.2 Summary of XS_SECURITY_CLASS Subprograms

Table 11-11 Summary of XS_SECURITY_CLASS Subprograms

| Subprogram                          | Description                                                                   |
|:------------------------------------|:------------------------------------------------------------------------------|
| CREATE_SECURITY_CLASS Procedure     | Creates a new security class.                                                 |
| ADD_PARENTS Procedure               | Adds one or more parent security classes for the specified security class.    |
| REMOVE_PARENTS Procedure            | Removes one or more parent security classes for the specified security class. |
| ADD_PRIVILEGES Procedure            | Adds one or more privileges to the specified security class.                  |
| REMOVE_PRIVILEGES Procedure         | Removes one or more privileges for the specified security class.              |
| ADD_IMPLIED_PRIVILEGES Procedure    | Adds one or more implied privileges for the specified aggregate privilege.    |
| REMOVE_IMPLIED_PRIVILEGES Procedure | Removes one or more implied privileges from an aggregate privilege.           |
| SET_DESCRIPTION Procedure           | Sets a description string for the specified security class.                   |
| DELETE_SECURITY_CLASS Procedure     | Deletes the specified security class.                                         |

This section describes the following XS_SECURITY_CLASS subprograms:

#### 11.9.2.1 CREATE_SECURITY_CLASS Procedure

The `CREATE_SECURITY_CLASS` creates a new security class.

##### Syntax

    XS_SECURITY_CLASS.CREATE_SECURITY_CLASS (
      name         IN VARCHAR2,
      priv_list    IN XS$PRIVILEGE_LIST,
      parent_list  IN XS$NAME_LIST := NULL,
      description  IN VARCHAR2 := NULL);

##### Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                            |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`        | The name of the security class to be created.<br>The name is schema qualified, for example, `SCOTT.SC1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `SC1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.SC1`. |
| `priv_list`   | The list of privileges to include in the security class.                                                                                                                                                                                                                                                                               |
| `parent_list` | The list of parent security classes from which the security class is inherited. This is optional.                                                                                                                                                                                                                                      |
| `description` | An optional description for the security class.                                                                                                                                                                                                                                                                                        |

##### Examples

The following example creates a security class called HRPRIVS. The security class includes a set of privileges defined in `priv_list`. The security class uses the `DML` class as its parent security class.

    DECLARE
      pr_list  XS$PRIVILEGE_LIST;
    BEGIN
      pr_list :=XS$PRIVILEGE_LIST(
         XS$PRIVILEGE(name=>'VIEW_SENSITIVE_INFO'),
         XS$PRIVILEGE(name=>'UPDATE_INFO',
                      implied_priv_list=>XS$NAME_LIST
                      ('"UPDATE"', '"DELETE"', '"INSERT"')));

      SYS.XS_SECURITY_CLASS.CREATE_SECURITY_CLASS(
         name=>'HRPRIVS',
         priv_list=>pr_list,
         parent_list=>XS$NAME_LIST('DML'));
    END;

#### 11.9.2.2 ADD_PARENTS Procedure

The `ADD_PARENTS` procedure adds one or more parent security classes for the specified security class.

##### Syntax

    XS_SECURITY_CLASS.ADD_PARENTS (
      sec_class   IN VARCHAR2,
      parent      IN VARCHAR2);

    XS_SECURITY_CLASS.ADD_PARENTS (
      sec_class   IN VARCHAR2,
      parent_list IN XS$NAME_LIST);

##### Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                       |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sec_class`   | The name of the security class for which parent classes are to be added.<br>The name is schema qualified, for example, `SCOTT.SC1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `SC1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.SC1`. |
| `parent`      | The name of the parent security class to be added.                                                                                                                                                                                                                                                                                                                |
| `parent_list` | The list of parent classes to be added.                                                                                                                                                                                                                                                                                                                           |

##### Examples

The following example adds the parent security class `GENPRIVS` to the `HRPRIVS` security class.

    BEGIN
      SYS.XS_SECURITY_CLASS.ADD_PARENTS('HRPRIVS','GENPRIVS');
    END;

#### 11.9.2.3 REMOVE_PARENTS Procedure

The `REMOVE_PARENTS` procedure removes one or more parent classes for the specified security class.

##### Syntax

    XS_SECURITY_CLASS.REMOVE_PARENTS (
      sec_class IN VARCHAR2);

    XS_SECURITY_CLASS.REMOVE_PARENTS (
      sec_class IN VARCHAR2,
      parent    IN VARCHAR2);

    XS_SECURITY_CLASS.REMOVE_PARENTS (
      sec_class   IN VARCHAR2,
      parent_list IN XS$NAME_LIST);

##### Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                     |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sec_class`   | The name of the security class whose parent classes are to be removed.<br>The name is schema qualified, for example, `SCOTT.SC1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `SC1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.SC1`. |
| `parent`      | The parent security class that is to be removed.                                                                                                                                                                                                                                                                                                                |
| `parent_list` | The list of parent security classes that are to be removed.                                                                                                                                                                                                                                                                                                     |

##### Examples

The following example removes the parent security class `GENPRIVS` from the `HRPRIVS` security class.

    BEGIN
      SYS.XS_SECURITY_CLASS.REMOVE_PARENTS('HRPRIVS','GENPRIVS');
    END;

#### 11.9.2.4 ADD_PRIVILEGES Procedure

The `ADD_PRIVILEGES` procedure adds one or more privileges to a security class.

##### Syntax

    XS_SECURITY_CLASS.ADD_PRIVILEGES (
      sec_class         IN VARCHAR2,
      priv              IN VARCHAR2,
      implied_priv_list IN XS$NAME_LIST := NULL,
      description       IN VARCHAR2 := NULL);

    XS_SECURITY_CLASS.ADD_PRIVILEGES (
      sec_class  IN VARCHAR2,
      priv_list  IN XS$PRIVILEGE_LIST);

##### Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                      |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sec_class`         | The name of the security class to which the privileges are to be added.<br>The name is schema qualified, for example, `SCOTT.SC1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `SC1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.SC1`. |
| `priv`              | The name of the privilege to be added.                                                                                                                                                                                                                                                                                                                           |
| `priv_list`         | The list of privileges to be added.                                                                                                                                                                                                                                                                                                                              |
| `implied_priv_list` | An optional list of implied privileges to be added.                                                                                                                                                                                                                                                                                                              |
| `description`       | An optional description of the privilege being added.                                                                                                                                                                                                                                                                                                            |

##### Examples

The following example adds an aggregate privilege called `UPDATE_INFO` to the `HRPRIVS` security class. The aggregate privilege contains the implied privileges, `UPDATE`, `DELETE`, and `INSERT`.

    BEGIN
      SYS.XS_SECURITY_CLASS.ADD_PRIVILEGES(sec_class=>'HRPRIVS',priv=>'UPDATE_INFO',
                                           implied_priv_list=>XS$NAME_LIST('"UPDATE"',
                                                        '"DELETE"', '"INSERT"'));
    END;

#### 11.9.2.5 REMOVE_PRIVILEGES Procedure

The `REMOVE_PRIVILEGES` procedure removes one or more privileges from the specified security class. If no privilege name or list is specified, then all privileges are removed from the specified security class.

##### Syntax

    XS_SECURITY_CLASS.REMOVE_PRIVILEGES (
      sec_class   IN VARCHAR2,
      priv        IN VARCHAR2);

    XS_SECURITY_CLASS.REMOVE_PRIVILEGES (
      sec_class    IN VARCHAR2,
      priv_list    IN XS$NAME_LIST);

    XS_SECURITY_CLASS.REMOVE_PRIVILEGES (
      sec_class IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                         |
|:------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sec_class` | The name of the security class for which the privileges are to be removed.<br>The name is schema qualified, for example, `SCOTT.SC1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `SC1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.SC1`. |
| `priv`      | The name of the privilege to be removed.                                                                                                                                                                                                                                                                                                                            |
| `priv_list` | The list of privileges to be removed.                                                                                                                                                                                                                                                                                                                               |

##### Examples

The following example removes the `UPDATE_INFO` privilege from the `HRPRIVS` security class.

    BEGIN
      SYS.XS_SECURITY_CLASS.REMOVE_PRIVILEGES('HRPRIVS','UPDATE_INFO');
    END;

The following example removes all privileges from the `HRPRIVS` security class.

    BEGIN
      SYS.XS_SECURITY_CLASS.REMOVE_PRIVILEGES('HRPRIVS');
    END;

#### 11.9.2.6 ADD_IMPLIED_PRIVILEGES Procedure

The `ADD_IMPLIED_PRIVILEGES` procedure adds one or more implied privileges to an aggregate privilege.

##### Syntax

    XS_SECURITY_CLASS.ADD_IMPLIED_PRIVILEGES (
      sec_class    IN VARCHAR2,
      priv         IN VARCHAR2,
      implied_priv IN VARCHAR2);

    XS_SECURITY_CLASS.ADD_IMPLIED_PRIVILEGES (
      sec_class         IN VARCHAR2,
      priv              IN VARCHAR2,
      implied_priv_list IN XS$NAME_LIST);

##### Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                      |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sec_class`         | The name of the security class to which the privileges are to be added.<br>The name is schema qualified, for example, `SCOTT.SC1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `SC1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.SC1`. |
| `priv`              | Name of the aggregate privilege for which the implied privileges are to be added.                                                                                                                                                                                                                                                                                |
| `implied_priv`      | The implied privilege to be added.                                                                                                                                                                                                                                                                                                                               |
| `implied_priv_list` | A list of implied privileges to be added for the aggregate privilege.                                                                                                                                                                                                                                                                                            |

##### Examples

The following example adds a list of implied privileges for the aggregate privilege `UPDATE_INFO` to the `HRPRIVS` security class:

    BEGIN
      SYS.XS_SECURITY_CLASS.ADD_IMPLIED_PRIVILEGES(sec_class=>'HRPRIVS', priv=>'UPDATE_INFO', implied_priv_list=>XS$NAME_LIST('"UPDATE"', '"DELETE"', '"INSERT"'));
    END;

#### 11.9.2.7 REMOVE_IMPLIED_PRIVILEGES Procedure

The `REMOVE_IMPLIED_PRIVILEGES` procedure removes the specified implied privileges from an aggregate privilege. If no implied privileges are specified, then all implied privileges are removed from the aggregate privilege.

##### Syntax

    XS_SECURITY_CLASS.REMOVE_IMPLIED_PRIVILEGES (
      sec_class    IN VARCHAR2,
      priv         IN VARCHAR2,
      implied_priv IN VARCHAR2);

    XS_SECURITY_CLASS.REMOVE_IMPLIED_PRIVILEGES (
      sec_class         IN VARCHAR2,
      priv              IN VARCHAR2,
      implied_priv_list IN XS$NAME_LIST);

    XS_SECURITY_CLASS.REMOVE_IMPLIED_PRIVILEGES (
      sec_class   IN VARCHAR2,
      priv        IN VARCHAR2);

##### Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                         |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sec_class`         | The name of the security class for which the privileges are to be removed.<br>The name is schema qualified, for example, `SCOTT.SC1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `SC1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.SC1`. |
| `priv`              | The name of the aggregate privilege from which the implied privileges are to be removed.                                                                                                                                                                                                                                                                            |
| `implied_priv`      | The implied privilege to be removed from the aggregate privilege.                                                                                                                                                                                                                                                                                                   |
| `implied_priv_list` | The list of implied privileges to be removed from the aggregate privilege.                                                                                                                                                                                                                                                                                          |

##### Examples

The following example removes the implicit privilege `DELETE` from the aggregate privilege `UPDATE_INFO` from the `HRPRIVS` security class:

    BEGIN
      SYS.XS_SECURITY_CLASS.REMOVE_IMPLIED_PRIVILEGES('HRPRIVS','UPDATE_INFO','"DELETE"');
    END;

The following example removes all implicit privileges from the aggregate privilege `UPDATE_INFO` from the `HRPRIVS` security class.

    BEGIN
      SYS.XS_SECURITY_CLASS.REMOVE_IMPLIED_PRIVILEGES('HRPRIVS','UPDATE_INFO');
    END;

#### 11.9.2.8 SET_DESCRIPTION Procedure

The `SET_DESCRIPTION` procedure sets a description string for the specified security class.

##### Syntax

    XS_SECURITY_CLASS.SET_DESCRIPTION (
      sec_class   IN VARCHAR2,
      description IN VARCHAR2);

##### Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                     |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sec_class`   | The name of the security class for which the description is to be set.<br>The name is schema qualified, for example, `SCOTT.SC1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `SC1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.SC1`. |
| `description` | A description string for the specified security class.                                                                                                                                                                                                                                                                                                          |

##### Examples

The following example sets a description string for the `HRPRIVS` security class:

    BEGIN
      SYS.XS_SECURITY_CLASS.SET_DESCRIPTION(
        'HRPRIVS','Contains privileges required to manage HR data');
    END;

#### 11.9.2.9 DELETE_SECURITY_CLASS Procedure

The `DELETE_SECURITY_CLASS` procedure deletes the specified security class.

##### Syntax

    XS_SECURITY_CLASS.DELETE_SECURITY_CLASS (
      sec_class     IN VARCHAR2,
      delete_option IN NUMBER:=XS_ADMIN_UTIL.DEFAULT_OPTION);

##### Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sec_class`     | The name of the security class to be deleted.<br>The name is schema qualified, for example, `SCOTT.SC1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `SC1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.SC1`.                                                                                                                                                                                                                                                                                                                                        |
| `delete_option` | The delete option to use. The following options are available:<br>• `DEFAULT_OPTION:`<br>• The default option allows deleting a security class only if it is not referenced elsewhere. If there are other entities that reference the security class, then the security class cannot be deleted.<br>• `CASCADE_OPTION`:<br>• The cascade option deletes the security class together with any references to it.The user deleting the security class must have privileges to delete these references as well.<br>• `ALLOW_INCONSISTENCIES_OPTION: `<br>• The allow inconsistencies option lets you delete the entity even if other entities have late binding references to it. |

##### Examples

The following example deletes the `HRPRIVS` security class using the default option:

    BEGIN
      SYS.XS_SECURITY_CLASS.DELETE_SECURITY_CLASS('HRPRIVS',XS_ADMIN_UTIL.DEFAULT_OPTION);
    END;
