## 11.2 XS_ACL Package

The `XS_ACL` package creates procedures to create and manage Access Control Lists (ACLs).

This section includes the following topics:

- Security Model for the XS_ACL Package

- Constants

- Object Types, Constructor Functions, Synonyms, and Grants

- Summary of XS_ACL Subprograms

### 11.2.1 Security Model for the XS_ACL Package

The `XS_ACL` package is created under the `SYS` schema.

The `DBA` role is granted the `ADMIN_ANY_SEC_POLICY` privilege, which allows it to administer schema objects like ACLs, security classes, and security policies across all schemas.

Users can administer schema objects in their own schema if they have been granted the `RESOURCE` role for the schema. The `RESOURCE` role and the `XS_RESOURCE` application role include the `ADMIN_SEC_POLICY` privilege, required to administer schema objects in the schema as well as administering the policy artifacts within the granted schema to achieve policy management within an application.

Users can administer policy enforcement on the schema if they have been granted the `APPLY_SEC_POLICY` privilege. With this privilege, the user can administer policy enforcement within granted schemas to achieve policy management within an application.

### 11.2.2 Constants

The following constants define the parent ACL type:

    EXTENDED              CONSTANT PLS_INTEGER := 1;
    CONSTRAINED           CONSTANT PLS_INTEGER := 2;

The following constants define the principal's type:

    PTYPE_XS              CONSTANT PLS_INTEGER := 1;
    PTYPE_DB              CONSTANT PLS_INTEGER := 2;
    PTYPE_DN              CONSTANT PLS_INTEGER := 3;
    PTYPE_EXTERNAL        CONSTANT PLS_INTEGER := 4;

The following constants define the parameter's value type:

    TYPE_NUMBER           CONSTANT PLS_INTEGER := 1;
    TYPE_VARCHAR          CONSTANT PLS_INTEGER := 2;

### 11.2.3 Object Types, Constructor Functions, Synonyms, and Grants

The following object types, constructor functions, synonyms, and `GRANT` statements are defined for this package.

    -- Type definition for ACE
    CREATE OR REPLACE TYPE XS$ACE_TYPE AS OBJECT (

    -- Member Variables
      privilege_list      XS$NAME_LIST,
      is_grant_ace        NUMBER,
      is_invert_principal NUMBER,
      principal_name      VARCHAR2(130),
      principal_type      NUMBER,
      start_date          TIMESTAMP WITH TIME ZONE,
      end_date            TIMESTAMP WITH TIME ZONE,

      CONSTRUCTOR FUNCTION XS$ACE_TYPE (
        privilege_list   IN XS$NAME_LIST,
        granted          IN BOOLEAN := TRUE,
        inverted         IN BOOLEAN := FALSE,
        principal_name   IN VARCHAR2,
        principal_type   IN PLS_INTEGER := 1,
        start_date       IN TIMESTAMP WITH TIME ZONE := NULL,
        end_date         IN TIMESTAMP WITH TIME ZONE := NULL)
      RETURN SELF AS RESULT,

      MEMBER PROCEDURE set_privileges(privilege_list IN XS$NAME_LIST),
      MEMBER FUNCTION get_privileges RETURN XS$NAME_LIST,
      MEMBER PROCEDURE set_grant(granted IN BOOLEAN),
      MEMBER FUNCTION is_granted RETURN BOOLEAN,
      MEMBER PROCEDURE set_inverted_principal(inverted IN BOOLEAN),
      MEMBER FUNCTION is_inverted_principal RETURN BOOLEAN,
      MEMBER PROCEDURE set_principal(principal_name IN VARCHAR2),
      MEMBER FUNCTION get_principal RETURN VARCHAR2,
      MEMBER PROCEDURE set_principal_type (principal_type IN PLS_INTEGER),
      MEMBER FUNCTION get_principal_type RETURN PLS_INTEGER,
      MEMBER PROCEDURE set_start_date(start_date IN TIMESTAMP WITH TIME ZONE),
      MEMBER FUNCTION get_start_date RETURN TIMESTAMP WITH TIME ZONE,
      MEMBER PROCEDURE set_end_date(end_date IN TIMESTAMP WITH TIME ZONE),
      MEMBER FUNCTION get_end_date RETURN TIMESTAMP WITH TIME ZONE
    );
    CREATE OR REPLACE TYPE XS$ACE_LIST AS VARRAY(1000) OF XS$ACE_TYPE;

### 11.2.4 Summary of XS_ACL Subprograms

Table 11-3 Summary of XS_ACL Subprograms

| Subprogram                      | Description                                                        |
|:--------------------------------|:-------------------------------------------------------------------|
| CREATE_ACL Procedure            | Creates an Access Control List (ACL).                              |
| APPEND_ACES Procedure           | Adds one or more Access Control Entries (ACEs) to an existing ACL. |
| REMOVE_ACES Procedure           | Removes all ACEs from an ACL.                                      |
| SET_SECURITY_CLASS Procedure    | Sets or modifies the security class for an ACL.                    |
| SET_PARENT_ACL Procedure        | Sets or modifies the parent ACL for an ACL.                        |
| ADD_ACL_PARAMETER Procedure     | Adds an ACL parameter value for a data security policy.            |
| REMOVE_ACL_PARAMETERS Procedure | Removes ACL parameters and values for an ACL.                      |
| SET_DESCRIPTION Procedure       | Sets a description string for an ACL.                              |
| DELETE_ACL Procedure            | Deletes the specified ACL.                                         |

####

This section describes the following XS_ACL subprograms:

#### 11.2.4.1 CREATE_ACL Procedure

The `CREATE_ACL` procedure creates a new Access Control List (ACL).

##### Syntax

    XS_ACL.CREATE_ACL (  name            IN VARCHAR2,
      ace_list        IN XS$ACE_LIST,
      sec_class       IN VARCHAR2 := NULL,
      parent          IN VARCHAR2 := NULL,
      inherit_mode    IN PLS_INTEGER := NULL,
      description     IN VARCHAR2 := NULL);

##### Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`         | The name of the ACL to be created.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`.                                                                                                                                         |
| `ace_list`     | The list of Access Control Entries (ACEs) in the ACL.                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `sec_class`    | The name of the security class that specifies the scope or type of the ACL. If no security class is specified, then the `DML` class is used as the default security class.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`. |
| `parent`       | The parent ACL name, if any.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`.                                                                                                                                               |
| `inherit_mode` | The inheritance mode if a parent ACL is specified. The allowed values are: `EXTENDED` or `CONSTRAINED`.                                                                                                                                                                                                                                                                                                                                                                |
| `description`  | An optional description for the ACL.                                                                                                                                                                                                                                                                                                                                                                                                                                   |

##### Examples

The following example creates an ACL called `HRACL`. This ACL includes ACEs contained in `ace_list`. The privileges used in `ace_list` are part of the `HRPRIVS` security class.

    DECLARE
      ace_list XS$ACE_LIST;
    BEGIN
      ace_list := XS$ACE_LIST(
          XS$ACE_TYPE(privilege_list=>XS$NAME_LIST('"SELECT"','VIEW_SENSITIVE_INFO'),
                      granted=>true,
                      principal_name=>'HRREP'),
          XS$ACE_TYPE(privilege_list=>XS$NAME_LIST('UPDATE_INFO'),
                      granted=>true,
                      principal_name=>'HRMGR'));
      SYS.XS_ACL.CREATE_ACL(name=>'HRACL',
                            ace_list=>ace_list,
                            sec_class=>'HRPRIVS',
                            description=>'HR Representative Access');
    END;

#### 11.2.4.2 APPEND_ACES Procedure

The `APPEND_ACES` procedure adds one or more ACE to an existing ACL.

##### Syntax

    XS_ACL.APPEND_ACES (
      acl      IN VARCHAR2,
      ace      IN XS$ACE_TYPE);

    XS.ACL.APPEND_ACES (
      acl      IN VARCHAR2,
      ace_list IN XS$ACE_LIST);

##### Parameters

| Parameter  | Description                                                                                                                                                                                                                                                                                                                                      |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `acl`      | The name of the ACL to which the ACE is to be added.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`. |
| `ace`      | The ACE to be added to the ACL.                                                                                                                                                                                                                                                                                                                  |
| `ace_list` | The list of ACEs to be added to the ACL.                                                                                                                                                                                                                                                                                                         |

##### Examples

The following example adds an ACE to the `HRACL` ACL. The ACE grants the `SELECT` privilege to the `DB_HR` database user.

    DECLARE
      ace_entry XS$ACE_TYPE;
    BEGIN
      ace_entry := XS$ACE_TYPE(privilege_list=>XS$NAME_LIST('"SELECT"'),
                               granted=>true,
                               principal_name=>'DB_HR',
                               principal_type=>XS_ACL.PTYPE_DB);
      SYS.XS_ACL.APPEND_ACES('HRACL',ace_entry);
    END;

#### 11.2.4.3 REMOVE_ACES Procedure

The `REMOVE_ACES` procedure removes all ACEs from an ACL.

##### Syntax

    XS_ACL.REMOVE_ACES (
      acl IN VARCHAR2);

##### Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                            |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `acl`     | The name of the ACL from which the ACEs are to be removed.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`. |

##### Examples

The following example removes all ACEs from the ACL called `HRACL`:

    BEGIN
      SYS.XS_ACL.REMOVE_ACES('HRACL');
    END;

#### 11.2.4.4 SET_SECURITY_CLASS Procedure

The `SET_SECURITY_CLASS` procedure sets or modifies the security class for an ACL.

##### Syntax

    XS_ACL.SET_SECURITY_CLASS (
      acl       IN VARCHAR2,
      sec_class IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                    |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `acl`       | The name of the ACL for which the security class is to be set.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`.     |
| `sec_class` | The name of the security class that defines the ACL scope or type.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`. |

##### Examples

The following example associates the `HRPRIVS` security class with the `HRACL` ACL:

    BEGIN
      SYS.XS_ACL.SET_SECURITY_CLASS('HRACL','HRPRIVS');
    END;

#### 11.2.4.5 SET_PARENT_ACL Procedure

The `SET_PARENT_ACL` sets or modifies the parent ACL for an ACL.

##### Syntax

    XS_ACL.SET_PARENT_ACL(
      acl            IN VARCHAR2,
      parent         IN VARCHAR2,
      inherit_mode   IN PLS_INTEGER);

##### Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                   |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `acl`          | The name of the ACL whose parent needs to be set.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`. |
| `parent`       | The name of the parent ACL.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`.                       |
| `inherit_mode` | The inheritance mode. This can be one of the following values:<br>`EXTENDED` (`extends from`), `CONSTRAINED` (`constrained with`)                                                                                                                                                                                                             |

##### Examples

The following example sets the `AllDepACL` ACL as the parent ACL for the `HRACL` ACL. The inheritance type is set to `EXTENDED`.

    BEGIN
      SYS.XS_ACL.SET_PARENT_ACL('HRACL','AllDepACL',XS_ACL.EXTENDED);
    END;

#### 11.2.4.6 ADD_ACL_PARAMETER Procedure

The `ADD_ACL_PARAMETER` adds an ACL parameter value for a data security policy.

##### Syntax

    XS_ACL.ADD_ACL_PARAMETER (
      acl         IN VARCHAR2,
      policy      IN VARCHAR2,
      parameter   IN VARCHAR2,
      value       IN NUMBER);

    XS_ACL.ADD_ACL_PARAMETER (
      acl         IN VARCHAR2,
      policy      IN VARCHAR2,
      parameter   IN VARCHAR2,
      value       IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                    |
|:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `acl`       | The name of the ACL to which the parameter is to be added.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`.                         |
| `policy`    | The name of the data security policy for which the ACL parameter has been created.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`. |
| `parameter` | The name of the ACL parameter as defined by the data security policy.                                                                                                                                                                                                                                                                                                          |
| `value`     | The value of the ACL parameter to be used.                                                                                                                                                                                                                                                                                                                                     |

##### Examples

The following example adds the `REGION` parameter for `ACL1`. The name of the data security policy for which the ACL parameter is created is `TEST_DS`. The value of the `REGION` parameter is `WEST`.

    BEGIN
      SYS.XS_ACL.ADD_ACL_PARAMETER('ACL1','TEST_DS','REGION', 'WEST');
    END;

#### 11.2.4.7 REMOVE_ACL_PARAMETERS Procedure

The `REMOVE_ACL_PARAMETERS` removes the specified ACL parameter for an ACL. If no parameter name is specified, then all ACL parameters for the ACL are removed.

##### Syntax

    XS_ACL.REMOVE_ACL_PARAMETERS (
      acl        IN VARCHAR2,
      parameter  IN VARCHAR2);

    XS_ACL.REMOVE_ACL_PARAMETERS (
      acl IN VARCHAR2);

##### Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                    |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `acl`       | The name of the ACL from which the parameter(s) are to be removed.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`. |
| `parameter` | The name of the parameter that needs to be removed from the ACL.                                                                                                                                                                                                                                                                                               |

##### Examples

The following example removes the `REGION` parameter from the `ACL1` ACL:

    BEGIN
      XS_ACL.REMOVE_ACL_PARAMETERS('ACL1', 'REGION');
    END;

The following example removes all ACL parameters for `ACL1`.

    BEGIN
      SYS.XS_ACL.REMOVE_ACL_PARAMETERS('ACL1');
    END;

#### 11.2.4.8 SET_DESCRIPTION Procedure

The `SET_DESCRIPTION` procedure sets a description string for an ACL.

##### Syntax

    XS_ACL.SET_DESCRIPTION (
      acl         IN VARCHAR2,
      description IN VARCHAR2);

##### Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                             |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `acl`         | The name of the ACL for which the description is to be set.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`. |
| `description` | A string description for the ACL.                                                                                                                                                                                                                                                                                                                       |

##### Examples

The following example sets a description for the `HRACL` ACL:

    BEGIN
      SYS.XS_ACL.SET_DESCRIPTION('HRACL','Grants privileges to HR representatives and
                              managers.');
    END;

#### 11.2.4.9 DELETE_ACL Procedure

The `DELETE_ACL` procedure deletes the specified ACL.

##### Syntax

    XS_ACL.DELETE_ACL (
      acl           IN VARCHAR2,
      delete_option IN PLS_INTEGER := XS_ADMIN_UTIL.DEFAULT_OPTION);

##### Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `acl`           | The name of the ACL to be deleted.<br>The name is schema qualified, for example, `SCOTT.ACL1`. When the schema part of the name is missing, the current session schema is assumed. For example, in this same example, if the name is specified as `ACL1`, and the current schema is `SCOTT`, it would resolve to `SCOTT.ACL1`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `delete_option` | The delete option to use. To the data security policy, the behavior of the following options is the same:<br>• `DEFAULT_OPTION:`<br>• The default option allows deleting an ACL only if it is not referenced elsewhere. If the ACL is referenced elsewhere, then the ACL cannot be deleted.<br>• For example, the delete operation fails if you try to delete an ACL that is part of a data security policy.<br>• `CASCADE_OPTION`:<br>• The cascade option deletes the ACL and also removes the ACL reference in a data realm constraint of a data security policy.<br>• `ALLOW_INCONSISTENCIES_OPTION: `<br>• The allow inconsistencies option lets you delete the ACL even if other entities have late binding references to it. In this mode, the ACL will be removed but the references are not removed. |

##### Examples

The following example deletes the `HRACL` ACL using the default delete option:

    BEGIN
      SYS.XS_ACL.DELETE_ACL('HRACL');
    END;
