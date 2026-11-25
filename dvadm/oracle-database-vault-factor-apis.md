The `DBMS_MACADM` PL/SQL package has factor-related Oracle Database Vault rule procedures and functions, and `DVF` has functions to manage factors.

- DBMS_MACADM Factor Procedures and Functions
  The `DBMS_MACADM` PL/SQL package provides procedures and functions to configure factors.
- Oracle Database Vault Run-Time PL/SQL Procedures and Functions
  Oracle Database Vault provides procedural interfaces to administer Database Vault security options and manage Database Vault security enforcements.
- Oracle Database Vault DVF PL/SQL Factor Functions
  Oracle Database Vault maintains the `DVF` schema functions when you use the `DBMS_MACADM` PL/SQL package to manage the various factors.

### 17.1 DBMS_MACADM Factor Procedures and Functions

The `DBMS_MACADM` PL/SQL package provides procedures and functions to configure factors.

Only users who have been granted the `DV_OWNER` or `DV_ADMIN` role can use these procedures and functions.

- ADD_FACTOR_LINK Procedure
  The `ADD_FACTOR_LINK` procedure specifies a parent-child relationship for two factors.
- ADD_POLICY_FACTOR Procedure
  The `ADD_POLICY_FACTOR` procedure specifies that the label for a factor contributes to the Oracle Label Security label for a policy.
- CHANGE_IDENTITY_FACTOR Procedure
  The `CHANGE_IDENTITY_FACTOR` procedure associates an identity with a different factor.
- CHANGE_IDENTITY_VALUE Procedure
  The `CHANGE_IDENTITY_FACTOR` procedure updates the value of an identity.
- CREATE_DOMAIN_IDENTITY Procedure
  The `CREATE_DOMAIN_IDENTITY` procedure is used for Oracle Real Application Clusters (Oracle RAC) and Oracle Label Security.
- CREATE_FACTOR Procedure
  The `CREATE_FACTOR` procedure creates a factor.
- CREATE_FACTOR_TYPE Procedure
  The `CREATE_FACTOR_TYPE` procedure creates a user-defined factor type.
- CREATE_IDENTITY Procedure
  The `CREATE_IDENTITY` procedure assigns an identity and an associated trust level for a given factor.
- CREATE_IDENTITY_MAP Procedure
  The `CREATE_IDENTITY_MAP` procedure defines tests that can derive the identity of a factor from the value of linked child factors (subfactors).
- DELETE_FACTOR Procedure
  The `DELETE_FACTOR` procedure deletes a factor.
- DELETE_FACTOR_LINK Procedure
  The `DELETE_FACTOR_LINK` procedure removes a parent-child relationship for two factors.
- DELETE_FACTOR_TYPE Procedure
  The `DELETE_FACTOR_TYPE` procedure deletes a factor type.
- DELETE_IDENTITY Procedure
  The `DELETE_IDENTITY` procedure removes an identity from an existing factor.
- DELETE_IDENTITY_MAP Procedure
  The `DELETE_IDENTITY_MAP` procedure removes an identity map for a factor.
- DROP_DOMAIN_IDENTITY Procedure
  The `DROP_DOMAIN_IDENTITY` procedure removes an Oracle Real Application Clusters database node from a domain.
- GET_SESSION_INFO Function
  The `GET_SESSION_INFO` function returns information from the `SYS.V_$SESSION` system table for the current session.
- GET_INSTANCE_INFO Function
  The `GET_INSTANCE_INFO` function returns information from the `SYS.V_$INSTANCE` system table about the current database instance.
- RENAME_FACTOR Procedure
  The `RENAME_FACTOR` procedure renames a factor; the name change takes effect everywhere the factor is used.
- RENAME_FACTOR_TYPE Procedure
  The `RENAME_FACTOR` procedure renames a factor type; the name change takes effect everywhere the factor type is used.
- UPDATE_FACTOR Procedure
  The `UPDATE_FACTOR` procedure updates the description of a factor type.
- UPDATE_FACTOR_TYPE Procedure
  The `UPDATE_FACTOR_TYPE` procedure updates a factor type.
- UPDATE_IDENTITY Procedure
  The `UPDATE_IDENTITY` procedure updates the trust level of a factor identity.

**Related Topics**

- [Configuring Factors](configuring-factors.md)
- [Oracle Database Vault Utility APIs](oracle-database-vault-utility-apis.md)

**Parent topic:** Oracle Database Vault Factor APIs

#### 17.1.1 ADD_FACTOR_LINK Procedure

The `ADD_FACTOR_LINK` procedure specifies a parent-child relationship for two factors.

##### Syntax

    DBMS_MACADM.ADD_FACTOR_LINK(
      parent_factor_name IN VARCHAR2,
      child_factor_name  IN VARCHAR2,
      label_indicator    IN VARCHAR2);

##### Parameters

Table 17-1 ADD_FACTOR_LINK Parameters

| Parameter            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:---------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `parent_factor_name` | Parent factor name.<br>To find existing parent and child factors in the current database instance, query the `DBA_DV_FACTOR_LINK` view, described in [DBA_DV_FACTOR_LINK View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `child_factor_name`  | Child factor name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `label_indicator`    | Indicates that the child factor being linked to the parent factor contributes to the label of the parent factor in an Oracle Label Security integration. Specify either `DBMS_MACUTL.G_YES` (for Yes) or `DBMS_MACUTL.G_NO` (for No).<br>To find the Oracle Label Security policies and labels associated with factors, query the following views, described in [Oracle Database Vault Data Dictionary Views](oracle-database-vault-data-dictionary-views.md):<br>• `DBA_DV_MAC_POLICY`: Lists Oracle Label Security policies defined in the current database instance.<br>• `DBA_DV_MAC_POLICY_FACTOR`: Lists the factors that are associated with Oracle Label Security policies for the current database instance.<br>• `DBA_DV_POLICY_LABEL`: Lists the Oracle Label Security label for each factor identifier in the `DBA_DV_IDENTITY` view for each policy. |

##### Example

    BEGIN
     DBMS_MACADM.ADD_FACTOR_LINK(
      parent_factor_name => 'HQ_ClientID',
      child_factor_name  => 'Div1_ClientID',
      label_indicator    => DBMS_MACUTL.G_YES);
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.2 ADD_POLICY_FACTOR Procedure

The `ADD_POLICY_FACTOR` procedure specifies that the label for a factor contributes to the Oracle Label Security label for a policy.

##### Syntax

    DBMS_MACADM.ADD_POLICY_FACTOR(
      policy_name  IN VARCHAR2,
      factor_name  IN VARCHAR2);

##### Parameters

Table 17-2 ADD_POLICY_FACTOR Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Oracle Label Security policy name.<br>To find the policies defined in the current database instance, query the `DBA_DV_MAC_POLICY` view, described in [DBA_DV_MAC_POLICY View](oracle-database-vault-data-dictionary-views.md).<br>To find factors that are associated with Oracle Label Security policies, query `DBA_DV_MAC_POLICY_FACTOR`, described in [DBA_DV_MAC_POLICY View](oracle-database-vault-data-dictionary-views.md). |
| `factor_name` | Factor name.<br>To find existing factors, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                         |

##### Example

    BEGIN
     DBMS_MACADM.ADD_POLICY_FACTOR(
      policy_name  => 'AccessData',
      factor_name  => 'Sector2_ClientID');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.3 CHANGE_IDENTITY_FACTOR Procedure

The `CHANGE_IDENTITY_FACTOR` procedure associates an identity with a different factor.

##### Syntax

    DBMS_MACADM.CHANGE_IDENTITY_FACTOR(
      factor_name     IN VARCHAR2,
      value           IN VARCHAR2,
      new_factor_name IN VARCHAR2);

##### Parameters

Table 17-3 CHANGE_IDENTITY_FACTOR Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                   |
|:------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `factor_name`     | Current factor name.<br>To find existing factors, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                          |
| `value`           | Value of the identity to update.<br>To find existing identities for each factor in the current database instance, query the `DBA_DV_IDENTITY` view, described in [DBA_DV_IDENTITY View](oracle-database-vault-data-dictionary-views.md).<br>To find current identity mappings, query the `DBA_DV_IDENTITY_MAP` view, described in [DBA_DV_IDENTITY_MAP View](oracle-database-vault-data-dictionary-views.md). |
| `new_factor_name` | Name of the factor to associate with the identity, which you can find by querying the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                |

##### Example

    BEGIN
     DBMS_MACADM.CHANGE_IDENTITY_FACTOR(
      factor_name     => 'Sector2_ClientID',
      value           => 'intranet',
      new_factor_name => 'Sector4_ClientID');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.4 CHANGE_IDENTITY_VALUE Procedure

The `CHANGE_IDENTITY_FACTOR` procedure updates the value of an identity.

##### Syntax

    DBMS_MACADM.CHANGE_IDENTITY_VALUE(
      factor_name  IN VARCHAR2,
      value        IN VARCHAR2,
      new_value    IN VARCHAR2);

##### Parameters

Table 17-4 CHANGE_IDENTITY_VALUE Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                            |
|:--------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `factor_name` | Factor name.<br>To find existing factors, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                           |
| `value`       | Current value associated with the identity.<br>To find existing identities for each factor in the current database instance, query the `DBA_DV_IDENTITY` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).<br>To find current identity mappings, query the `DBA_DV_IDENTITY_MAP` view, described in [DBA_DV_IDENTITY_MAP View](oracle-database-vault-data-dictionary-views.md). |
| `new_value`   | New identity value, up to 1024 characters in mixed-case.                                                                                                                                                                                                                                                                                                                                                               |

##### Example

    BEGIN
     DBMS_MACADM.CHANGE_IDENTITY_VALUE(
      factor_name  => 'Sector2_ClientID',
      value        => 'remote',
      new_value    => 'intranet');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.5 CREATE_DOMAIN_IDENTITY Procedure

The `CREATE_DOMAIN_IDENTITY` procedure is used for Oracle Real Application Clusters (Oracle RAC) and Oracle Label Security.

It adds an Oracle RAC database node to the domain factor identities and labels it according to an Oracle Label Security policy

##### Syntax

    DBMS_MACADM.CREATE_DOMAIN_IDENTITY(
      domain_name  IN VARCHAR2,
      domain_host  IN VARCHAR2,
      policy_name  IN VARCHAR2 DEFAULT NULL,
      domain_label IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 17-5 CREATE_DOMAIN_IDENTITY Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                      |
|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `domain_name`  | Name of the domain to which to add the host.<br>To find the logical location of the database within the network structure within a distributed database system, run the `DVF.F$DATABASE_DOMAIN` function, described in Oracle Database Vault DVF PL/SQL Factor Functions.        |
| `domain_host`  | Oracle Real Application Clusters host name being added to the domain.<br>To find host name of a database, run the `DVF.F$DATABASE_HOSTNAME` function, described in Oracle Database Vault DVF PL/SQL Factor Functions.                                                            |
| `policy_name`  | Oracle Label Security policy name. If you omit the policy name, then the domain is not associated with any policy.<br>To find the available policies, query the `DBA_DV_MAC_POLICY` view, described in [DBA_DV_MAC_POLICY View](oracle-database-vault-data-dictionary-views.md). |
| `domain_label` | Name of the domain to which to add the Oracle Label Security policy.                                                                                                                                                                                                             |

##### Examples

    BEGIN
     DBMS_MACADM.CREATE_DOMAIN_IDENTITY(
      domain_name  => 'example',
      domain_host  => 'mydom_host',
      policy_name  => 'AccessData',
      domain_label => 'sensitive');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.6 CREATE_FACTOR Procedure

The `CREATE_FACTOR` procedure creates a factor.

After you create a factor, you can give it an identity by using the `CREATE_IDENTITY` procedure, described in CREATE_IDENTITY Procedure.

##### Syntax

    DBMS_MACADM.CREATE_FACTOR(
      factor_name       IN VARCHAR2,
      factor_type_name  IN VARCHAR2,
      description       IN VARCHAR2,
      rule_set_name     IN VARCHAR2,
      get_expr          IN VARCHAR2,
      validate_expr     IN VARCHAR2,
      identify_by       IN NUMBER,
      labeled_by        IN NUMBER,
      eval_options      IN NUMBER,
      audit_options     IN NUMBER,
      fail_options      IN NUMBER);

##### Parameters

Table 17-6 CREATE_FACTOR Parameters

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `factor_name`      | Factor name, up to 128 characters in mixed-case, without spaces.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `factor_type_name` | Type of the factor, up to 128 characters in mixed-case, without spaces.<br>To find existing factor types, query the `DBA_DV_FACTOR_TYPE` view, described in [DBA_DV_FACTOR_TYPE View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `description`      | Description of the purpose of the factor, up to 1024 characters in mixed-case.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `rule_set_name`    | Rule set name if you want to use a rule set to control when and how a factor identity is set.<br>To find existing rule sets, query the `DBA_DV_RULE_SET` view, described in [Oracle Database Vault Data Dictionary Views](oracle-database-vault-data-dictionary-views.md). See also [Assigning a Rule Set to a Factor](configuring-factors.md) for more information about assigning rule sets to factors.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `get_expr`         | Valid PL/SQL expression that retrieves the identity of a factor. It can use up to 255 characters in mixed-case. See [Setting the Retrieval Method for a Factor](configuring-factors.md) for more information. See also the `audit_options` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `validate_expr`    | Name of the procedure to validate the factor. This is a valid PL/SQL expression that returns a Boolean value (`TRUE` or `FALSE`) to validate the identity of the factor. See [Setting the Validation Method for a Factor](configuring-factors.md) for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `identify_by`      | Options for determining the identity of a factor, based on the expression set for the `get_expr` parameter:<br>• `DBMS_MACUTL.G_IDENTIFY_BY_CONSTANT`: By constant<br>• `DBMS_MACUTL.G_IDENTIFY_BY_METHOD`: By method<br>• `DBMS_MACUTL.G_IDENTIFY_BY_FACTOR`: By factor<br>• `DBMS_MACUTL.G_IDENTIFY_BY_CONTEXT`: By context<br>See [Setting the Factor Identification Information](configuring-factors.md) for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `labeled_by`       | Options for labeling the factor:<br>• `DBMS_MACUTL.G_LABELED_BY_SELF`: Labels the identities for the factor directly from the labels associated with an Oracle Label Security policy (default)<br>• `DBMS_MACUTL.G_LABELED_BY_FACTORS`: Derives the factor identity label from the labels of its child factor identities.<br>See [Setting the Oracle Label Security Labeling Information for a Factor](configuring-factors.md) for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `eval_options`     | Options for evaluating the factor when the user logs on:<br>• `DBMS_MACUTL.G_EVAL_ON_SESSION`: When the database session is created (default)<br>• `DBMS_MACUTL.G_EVAL_ON_ACCESS`: Each time the factor is accessed<br>• `DBMS_MACUTL.G_EVAL_ON_STARTUP`: On start-up<br>See [Setting the Evaluation Information for a Factor](configuring-factors.md) for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `audit_options`    | Options for auditing the factor if you want to generate a custom Oracle Database Vault audit record.<br>• `DBMS_MACUTL.G_AUDIT_OFF`: Disables auditing.<br>• `DBMS_MACUTL.G_AUDIT_ALWAYS`: Always audits.<br>• `DBMS_MACUTL.G_AUDIT_ON_GET_ERROR`: Audits if `get_expr` returns an error.<br>• `DBMS_MACUTL.G_AUDIT_ON_GET_NULL`: Audits if `get_expr` is null.<br>• `DBMS_MACUTL.G_AUDIT_ON_VALIDATE_ERROR`: Audits if the validation procedure returns an error.<br>• `DBMS_MACUTL.G_AUDIT_ON_VALIDATE_FALSE`: Audits if the validation procedure is false.<br>• `DBMS_MACUTL.G_AUDIT_ON_TRUST_LEVEL_NULL`: Audits if there is no trust level set.<br>• `DBMS_MACUTL.G_AUDIT_ON_TRUST_LEVEL_NEG`: Audits if the trust level is negative.<br>The `audit_options` parameter applies to traditional auditing only. If you have enabled unified auditing, then create a unified audit policy instead of using `audit_options`.<br>See [Setting Audit Options for a Factor](configuring-factors.md) for more information. |
| `fail_options`     | Options for reporting factor errors:<br>• `DBMS_MACUTL.G_FAIL_WITH_MESSAGE`: Shows an error message (default)<br>• `DBMS_MACUTL.G_FAIL_SILENTLY`: Does not show an error message<br>See [Setting Error Options for a Factor](configuring-factors.md) for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

##### Example

    BEGIN
     DBMS_MACADM.CREATE_FACTOR(
      factor_name       => 'Sector2_DB',
      factor_type_name  => 'Instance',
      description       => ' ',
      rule_set_name     => 'Limit_DBA_Access',
      get_expr          => 'UPPER(SYS_CONTEXT(''USERENV'',''DB_NAME''))',
      validate_expr     => 'dbavowner.check_db_access',
      identify_by       => DBMS_MACUTL.G_IDENTIFY_BY_METHOD,
      labeled_by        => DBMS_MACUTL.G_LABELED_BY_SELF,
      eval_options      => DBMS_MACUTL.G_EVAL_ON_SESSION,
      audit_options     => DBMS_MACUTL.G_AUDIT_OFF,
      fail_options      => DBMS_MACUTL.G_FAIL_SILENTLY);
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.7 CREATE_FACTOR_TYPE Procedure

The `CREATE_FACTOR_TYPE` procedure creates a user-defined factor type.

##### Syntax

    DBMS_MACADM.CREATE_FACTOR_TYPE(
      name        IN VARCHAR2,
      description IN VARCHAR2);

##### Parameters

Table 17-7 CREATE_FACTOR_TYPE Parameters

| Parameter     | Description                                                                                                                                                                                                                          |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`        | Factor type name, up to 128 characters in mixed-case, without spaces.<br>To find existing factor types, query the `DBA_DV_FACTOR_TYPE` view, described in [DBA_DV_FACTOR_TYPE View](oracle-database-vault-data-dictionary-views.md). |
| `description` | Description of the purpose of the factor type, up to 1024 characters in mixed-case.                                                                                                                                                  |

##### Example

    BEGIN
     DBMS_MACADM.CREATE_FACTOR_TYPE(
      name        => 'Sector2Instance',
      description => 'Checks DB instances used in Sector 2');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.8 CREATE_IDENTITY Procedure

The `CREATE_IDENTITY` procedure assigns an identity and an associated trust level for a given factor.

After you create a factor, you must assign it an identity.

##### Syntax

    DBMS_MACADM.CREATE_IDENTITY(
      factor_name  IN VARCHAR2,
      value        IN VARCHAR2,
      trust_level  IN NUMBER);

##### Parameters

Table 17-8 CREATE_IDENTITY Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `factor_name` | Factor name.<br>To find existing factors, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                             |
| `value`       | The actual value of the factor, up to 1024 characters in mixed-case. For example, the identity of an IP_Address factor could be the IP address of 192.0.2.12.                                                                                                                                                                                                                                            |
| `trust_level` | Number that indicates the magnitude of trust relative to other identities for the same factor. In general, the higher the trust level number is set, the greater the trust. A trust level of 10 indicates "very trusted." Negative trust levels are not trusted.<br>See [Creating and Configuring a Factor Identity](configuring-factors.md) for more information about trust levels and label security. |

##### Example

    BEGIN
     DBMS_MACADM.CREATE_IDENTITY(
      factor_name  => 'Sector2_ClientID',
      value        => 'intranet',
      trust_level  => 5);
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.9 CREATE_IDENTITY_MAP Procedure

The `CREATE_IDENTITY_MAP` procedure defines tests that can derive the identity of a factor from the value of linked child factors (subfactors).

##### Syntax

    DBMS_MACADM.CREATE_IDENTITY_MAP(
      identity_factor_name  IN VARCHAR2,
      identity_factor_value IN VARCHAR2,
      parent_factor_name    IN VARCHAR2,
      child_factor_name     IN VARCHAR2,
      operation             IN VARCHAR2,
      operand1              IN VARCHAR2,
      operand2              IN VARCHAR2);

##### Parameters

Table 17-9 CREATE_IDENTITY_MAP Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                                                                                                                                      |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `identity_factor_name`  | Factor the identity map is for.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                 |
| `identity_factor_value` | Value the factor assumes if the identity map evaluates to `TRUE`.<br>To find existing factor identities, query the `DBA_DV_IDENTITY` view, described in [DBA_DV_IDENTITY View](oracle-database-vault-data-dictionary-views.md).<br>To find current factor identity mappings, use `DBA_DV_IDENTITY_MAP`, described in [DBA_DV_IDENTITY_MAP View](oracle-database-vault-data-dictionary-views.md). |
| `parent_factor_name`    | The parent factor link to which the map is related.<br>To find existing parent-child factor mappings, query the `DBA_DV_IDENTITY_MAP` view, described in [DBA_DV_IDENTITY_MAP View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                             |
| `child_factor_name`     | The child factor link to which the map is related.                                                                                                                                                                                                                                                                                                                                               |
| `operation`             | Relational operator for the identity map (for example, \<, \>, =, and so on).                                                                                                                                                                                                                                                                                                                    |
| `operand1`              | Left operand for the relational operator; refers to the low value you enter.                                                                                                                                                                                                                                                                                                                     |
| `operand2`              | Right operand for the relational operator; refers to the high value you enter.                                                                                                                                                                                                                                                                                                                   |

##### Example

    BEGIN
     DBMS_MACADM.CREATE_IDENTITY_MAP(
      identity_factor_name  => 'Sector2_ClientID',
      identity_factor_value => 'intranet',
      parent_factor_name    => 'HQ_ClientID',
      child_factor_name     => 'Div1_ClientID',
      operation             => '<',
      operand1              => '192.0.2.50',
      operand2              => '192.0.2.100');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.10 DELETE_FACTOR Procedure

The `DELETE_FACTOR` procedure deletes a factor.

##### Syntax

    DBMS_MACADM.DELETE_FACTOR(
      factor_name IN VARCHAR2);

##### Parameters

Table 17-10 DELETE_FACTOR Parameter

| Parameter     | Description                                                                                                                                                                                   |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `factor_name` | Factor name.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    EXEC DBMS_MACADM.DELETE_FACTOR('Sector2_ClientID');

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.11 DELETE_FACTOR_LINK Procedure

The `DELETE_FACTOR_LINK` procedure removes a parent-child relationship for two factors.

##### Syntax

    DBMS_MACADM.DELETE_FACTOR_LINK(
      parent_factor_name IN VARCHAR2,
      child_factor_name  IN VARCHAR2);

##### Parameters

Table 17-11 DELETE_FACTOR_LINK Parameters

| Parameter            | Description                                                                                                                                                                                                                           |
|:---------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `parent_factor_name` | Factor name.<br>To find factors that are used in parent-child mappings in the current database instance, query the `DBA_DV_FACTOR_LINK` view, described in [DBA_DV_FACTOR_LINK View](oracle-database-vault-data-dictionary-views.md). |
| `child_factor_name`  | Factor name                                                                                                                                                                                                                           |

##### Example

    BEGIN
     DBMS_MACADM.DELETE_FACTOR_LINK(
      parent_factor_name => 'HQ_ClientID',
      child_factor_name  => 'Div1_ClientID');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.12 DELETE_FACTOR_TYPE Procedure

The `DELETE_FACTOR_TYPE` procedure deletes a factor type.

##### Syntax

    DBMS_MACADM.DELETE_FACTOR_TYPE(
      name IN VARCHAR2);

##### Parameters

Table 17-12 DELETE_FACTOR_TYPE Parameters

| Parameter | Description                                                                                                                                                                      |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`    | Factor type name.<br>To find existing factor types, query the `DBA_DV_FACTOR_TYPE` view, described in [DBA_DV_FACTOR_TYPE View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    EXEC DBMS_MACADM.DELETE_FACTOR_TYPE('Sector2Instance');

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.13 DELETE_IDENTITY Procedure

The `DELETE_IDENTITY` procedure removes an identity from an existing factor.

##### Syntax

    DBMS_MACADM.DELETE_IDENTITY(
      factor_name IN VARCHAR2,
      value       IN VARCHAR2);

##### Parameters

Table 17-13 DELETE_IDENTITY Parameters

| Parameter     | Description                                                                                                                                                                                                                                   |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `factor_name` | Factor name.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                                 |
| `value`       | Identity value associated with the factor.<br>To find the identities for each factor in the current database instance, query the `DBA_DV_IDENTITY` view, described in [DBA_DV_IDENTITY View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    BEGIN
     DBMS_MACADM.DELETE_IDENTITY(
      factor_name => 'Sector2_ClientID',
      value       => 'intranet');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.14 DELETE_IDENTITY_MAP Procedure

The `DELETE_IDENTITY_MAP` procedure removes an identity map for a factor.

##### Syntax

    DBMS_MACADM.DELETE_IDENTITY_MAP(
      identity_factor_name  IN VARCHAR2,
      identity_factor_value IN VARCHAR2,
      parent_factor_name    IN VARCHAR2,
      child_factor_name     IN VARCHAR2,
      operation             IN VARCHAR2,
      operand1              IN VARCHAR2,
      operand2              IN VARCHAR2);

##### Parameters

Table 17-14 DELETE_IDENTITY_MAP Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                                                                                                                                        |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `identity_factor_name`  | Factor the identity map is for.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                   |
| `identity_factor_value` | Value the factor assumes if the identity map evaluates to `TRUE`.<br>To find existing factor identities, query the `DBA_DV_IDENTITY` view, described in [DBA_DV_IDENTITY View](oracle-database-vault-data-dictionary-views.md).<br>To find current factor identity mappings, query `DBA_DV_IDENTITY_MAP`, described in [DBA_DV_IDENTITY_MAP View](oracle-database-vault-data-dictionary-views.md). |
| `parent_factor_name`    | The parent factor link to which the map is related.<br>To find existing parent-child factors, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR_LINK View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                              |
| `child_factor_name`     | The child factor to which the map is related.                                                                                                                                                                                                                                                                                                                                                      |
| `operation`             | Relational operator for the identity map (for example, \<, \>, =, and so on).                                                                                                                                                                                                                                                                                                                      |
| `operand1`              | Left (low value) operand for the relational operator.                                                                                                                                                                                                                                                                                                                                              |
| `operand2`              | Right (high value) operand for the relational operator.                                                                                                                                                                                                                                                                                                                                            |

##### Example

    BEGIN
     DBMS_MACADM.DELETE_IDENTITY_MAP(
      identity_factor_name  => 'Sector2_ClientID',
      identity_factor_value => 'intranet',
      parent_factor_name    => 'HQ_ClientID',
      child_factor_name     => 'Div1_ClientID',
      operation             => '<',
      operand1              => '192.0.2.10',
      operand2              => '192.0.2.15');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.15 DROP_DOMAIN_IDENTITY Procedure

The `DROP_DOMAIN_IDENTITY` procedure removes an Oracle Real Application Clusters database node from a domain.

##### Syntax

    DBMS_MACADM.DROP_DOMAIN_IDENTITY(
      domain_name  IN VARCHAR2,
      domain_host  IN VARCHAR2);

##### Parameters

Table 17-15 DROP_DOMAIN_IDENTITY Parameters

| Parameter     | Description                                                                                                                                                                                                                       |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `domain_name` | Name of the domain to which the host was added.<br>To find the domain of a database as specified by the `DB_DOMAIN` initialization parameter, run the `DVF.F$DATABASE_DOMAIN` function, described in F\$DATABASE_DOMAIN Function. |
| `domain_host` | Oracle Real Application Clusters host name being that was added to the domain.<br>To find the host name for a specified database, run the `DVF.F$DATABASE_HOSTNAME` function, described in F\$DATABASE_NAME Function.             |

##### Example

    BEGIN
     DBMS_MACADM.DROP_DOMAIN_IDENTITY(
      domain_name  => 'example',
      domain_host  => 'mydom_host');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.16 GET_SESSION_INFO Function

The `GET_SESSION_INFO` function returns information from the `SYS.V_$SESSION` system table for the current session.

The `V$SESSION` data dictionary view also contains session information from this table. See [Oracle Database Reference](../refrn/V-SESSION.md) for more information.

##### Syntax

    DBMS_MACADM.GET_SESSION_INFO(
      p_parameter IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameters

Table 17-16 GET_SESSION_INFO Parameter

| Parameter     | Description                                       |
|:--------------|:--------------------------------------------------|
| `p_parameter` | Column name in the `SYS.V_$SESSION` system table. |

##### Example

    DECLARE
     session_var varchar2 := null;
    BEGIN
     session_var = DBMS_MACADM.GET_SESSION_INFO('PROCESS');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.17 GET_INSTANCE_INFO Function

The `GET_INSTANCE_INFO` function returns information from the `SYS.V_$INSTANCE` system table about the current database instance.

The `V$INSTANCE` data dictionary view also contains database instance information from this table. See [Oracle Database Reference](../refrn/V-INSTANCE.md) for more information.

##### Syntax

    DBMS_MACADM.GET_INSTANCE_INFO(
      p_parameter IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameters

Table 17-17 GET_INSTANCE_INFO Parameter

| Parameter     | Description                                       |
|:--------------|:--------------------------------------------------|
| `p_parameter` | Column name in the `SYS.V_$INSTANCE` system table |

##### Example

    DECLARE
     instance_var varchar2 := null;
    BEGIN
     instance_var = DBMS_MACADM.GET_INSTANCE_INFO('INSTANCE_NAME');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.18 RENAME_FACTOR Procedure

The `RENAME_FACTOR` procedure renames a factor; the name change takes effect everywhere the factor is used.

##### Syntax

    DBMS_MACADM.RENAME_FACTOR(
      factor_name     IN VARCHAR2,
      new_factor_name IN VARCHAR2);

##### Parameters

Table 17-18 RENAME_FACTOR Parameters

| Parameter         | Description                                                                                                                                                                                           |
|:------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `factor_name`     | Current factor name.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md). |
| `new_factor_name` | New factor name, up to 128 characters in mixed-case, without spaces.                                                                                                                                  |

##### Example

    BEGIN
     DBMS_MACADM.RENAME_FACTOR(
      factor_name     => 'Sector2_ClientID',
      new_factor_name => 'Sector2_Clients');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.19 RENAME_FACTOR_TYPE Procedure

The `RENAME_FACTOR` procedure renames a factor type; the name change takes effect everywhere the factor type is used.

##### Syntax

    DBMS_MACADM.RENAME_FACTOR_TYPE(
      old_name  IN VARCHAR2,
      new_name  IN VARCHAR2);

##### Parameters

Table 17-19 RENAME_FACTOR_TYPE Parameters

| Parameter  | Description                                                                                                                                                                                                               |
|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `old_name` | Current factor type name.<br>To find existing factor types in the current database instance, query the `DBA_DV_FACTOR_TYPE` view, described in [DBA_DV_FACTOR_TYPE View](oracle-database-vault-data-dictionary-views.md). |
| `new_name` | New factor type name, up to 128 characters in mixed-case, without spaces.                                                                                                                                                 |

##### Example

    BEGIN
     DBMS_MACADM.RENAME_FACTOR_TYPE(
      old_name  => 'Sector2Instance',
      new_name  => 'Sector2DBInstance');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.20 UPDATE_FACTOR Procedure

The `UPDATE_FACTOR` procedure updates the description of a factor type.

##### Syntax

    DBMS_MACADM.UPDATE_FACTOR(
      factor_name       IN VARCHAR2,
      factor_type_name  IN VARCHAR2,
      description       IN VARCHAR2,
      rule_set_name     IN VARCHAR2,
      get_expr          IN VARCHAR2,
      validate_expr     IN VARCHAR2,
      identify_by       IN NUMBER,
      labeled_by        IN NUMBER,
      eval_options      IN NUMBER,
      audit_options     IN NUMBER,
      fail_options      IN NUMBER);

##### Parameters

Table 17-20 UPDATE_FACTOR

| Parameter          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:-------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `factor_name`      | Factor name.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `factor_type_name` | Factor type name.<br>To find existing factor types, query the `DBA_DV_FACTOR_TYPE` view, described in [DBA_DV_FACTOR_TYPE View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `description`      | Description of the purpose of the factor, up to 1024 characters in mixed-case.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `rule_set_name`    | Name of the rule set used to control when and how a factor identity is set.<br>To find existing rule sets, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).<br>See also [Assigning a Rule Set to a Factor](configuring-factors.md) for more information about assigning rule sets to factors.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `get_expr`         | Valid PL/SQL expression that retrieves the identity of a factor. It can use up to 255 characters in mixed-case. See [Setting the Retrieval Method for a Factor](configuring-factors.md) for more information. See also the `audit_options` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `validate_expr`    | Name of the procedure to validate factor. This is a valid PL/SQL expression that returns a Boolean value (`TRUE` or `FALSE`) to validate the identity of the factor. See [Setting the Validation Method for a Factor](configuring-factors.md) for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `identify_by`      | Options for determining the identity of a factor, based on the expression set for the `get_expr` parameter:<br>• `DBMS_MACUTL.G_IDENTIFY_BY_CONSTANT`: By constant<br>• `DBMS_MACUTL.G_IDENTIFY_BY_METHOD`: By method<br>• `DBMS_MACUTL.G_IDENTIFY_BY_FACTOR`: By factor<br>• `DBMS_MACUTL.G_IDENTIFY_BY_CONTEXT`: By context<br>See [Setting the Factor Identification Information](configuring-factors.md) for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `labeled_by`       | Options for labeling the factor:<br>• `DBMS_MACUTL.G_LABELED_BY_SELF`: Labels the identities for the factor directly from the labels associated with an Oracle Label Security policy<br>• `DBMS_MACUTL.G_LABELED_BY_FACTORS`: Derives the factor identity label from the labels of its child factor identities.<br>The default for `labeled_by` is the previously set value, which you can find by querying the `DBA_DV_FACTOR` data dictionary view.<br>See [Setting the Oracle Label Security Labeling Information for a Factor](configuring-factors.md) for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `eval_options`     | Options for evaluating the factor when the user logs on:<br>• `DBMS_MACUTL.G_EVAL_ON_SESSION`: When the database session is created<br>• `DBMS_MACUTL.G_EVAL_ON_ACCESS`: Each time the factor is accessed<br>• `DBMS_MACUTL.G_EVAL_ON_STARTUP`: On start-up<br>The default for `eval_options` is the previously set value, which you can find by querying the `DBA_DV_FACTOR` data dictionary view.<br>See [Setting the Evaluation Information for a Factor](configuring-factors.md) for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `audit_options`    | Options for auditing the factor if you want to generate a custom Oracle Database Vault audit record.<br>• `DBMS_MACUTL.G_AUDIT_OFF`: Disables auditing.<br>• `DBMS_MACUTL.G_AUDIT_ALWAYS`: Always audits.<br>• `DBMS_MACUTL.G_AUDIT_ON_GET_ERROR`: Audits if `get_expr` returns an error.<br>• `DBMS_MACUTL.G_AUDIT_ON_GET_NULL`: Audits if `get_expr` is null.<br>• `DBMS_MACUTL.G_AUDIT_ON_VALIDATE_ERROR`: Audits if the validation procedure returns an error.<br>• `DBMS_MACUTL.G_AUDIT_ON_VALIDATE_FALSE`: Audits if the validation procedure is false.<br>• `DBMS_MACUTL.G_AUDIT_ON_TRUST_LEVEL_NULL`: Audits if there is no trust level set.<br>• `DBMS_MACUTL.G_AUDIT_ON_TRUST_LEVEL_NEG`: Audits if the trust level is negative.<br>The default for `audit_options` is the previously set value, which you can find by querying the `DBA_DV_FACTOR` data dictionary view.<br>The `audit_options` parameter applies to traditional auditing only. If you have enabled unified auditing, then create a unified audit policy instead of using `audit_options`.<br>See [Setting Audit Options for a Factor](configuring-factors.md) for more information. |
| `fail_options`     | Options for reporting factor errors:<br>• `DBMS_MACUTL.G_FAIL_WITH_MESSAGE`: Shows an error message.<br>• `DBMS_MACUTL.G_FAIL_SILENTLY`: Does not show an error message.<br>The default for `fail_options` is the previously set value, which you can find by querying the `DBA_DV_FACTOR` data dictionary view.<br>See [Setting Error Options for a Factor](configuring-factors.md) for more information.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

##### Example

    BEGIN
     DBMS_MACADM.UPDATE_FACTOR(
      factor_name       => 'Sector2_DB',
      factor_type_name  => 'Instance',
      description       => ' ',
      rule_set_name     => 'Limit_DBA_Access',
      get_expr          => 'UPPER(SYS_CONTEXT(''USERENV'',''DB_NAME''))',
      validate_expr     => 'dbavowner.check_db_access',
      identify_by       => DBMS_MACUTL.G_IDENTIFY_BY_METHOD,
      labeled_by        => DBMS_MACUTL.G_LABELED_BY_SELF,
      eval_options      => DBMS_MACUTL.G_EVAL_ON_ACCESS,
      audit_options     => DBMS_MACUTL.G_AUDIT_ALWAYS,
      fail_options      => DBMS_MACUTL.G_FAIL_WITH_MESSAGE);
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.21 UPDATE_FACTOR_TYPE Procedure

The `UPDATE_FACTOR_TYPE` procedure updates a factor type.

##### Syntax

    DBMS_MACADM.UPDATE_FACTOR_TYPE(
      name         IN VARCHAR2,
      description  IN VARCHAR2);

##### Parameters

Table 17-21 UPDATE_FACTOR_TYPE Parameters

| Parameter     | Description                                                                                                                                                                                                       |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`        | Factor type name.<br>To find existing factor types in the current database instance, query the `DBA_DV_FACTOR_TYPE` view, described in [DBA_DV_FACTOR_TYPE View](oracle-database-vault-data-dictionary-views.md). |
| `description` | Description of the purpose of the factor type, up to 1024 characters in mixed case.                                                                                                                               |

##### Example

    BEGIN
     DBMS_MACADM.UPDATE_FACTOR_TYPE(
      name        => 'Sector2DBInstance',
      description => 'Checks DB instances used in Sector 2');
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

#### 17.1.22 UPDATE_IDENTITY Procedure

The `UPDATE_IDENTITY` procedure updates the trust level of a factor identity.

##### Syntax

    DBMS_MACADM.UPDATE_IDENTITY(
      factor_name  IN VARCHAR2,
      value        IN VARCHAR2,
      trust_level  IN NUMBER);

##### Parameters

Table 17-22 UPDATE_IDENTITY Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `factor_name` | Factor name.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).<br>To find factors that have identities, query `DBA_DV_IDENTITY`, described in [DBA_DV_IDENTITY View](oracle-database-vault-data-dictionary-views.md).                                                     |
| `value`       | New factor identity, up to 1024 characters in mixed-case. For example, the identity of an IP_Address factor could be the IP address of 192.0.2.12.                                                                                                                                                                                                                                                       |
| `trust_level` | Number that indicates the magnitude of trust relative to other identities for the same factor. In general, the higher the trust level number is set, the greater the trust. A trust level of 10 indicates "very trusted." Negative trust levels are not trusted.<br>See [Creating and Configuring a Factor Identity](configuring-factors.md) for more information about trust levels and label security. |

##### Example

    BEGIN
     DBMS_MACADM.UPDATE_IDENTITY(
      factor_name  => 'Sector2_ClientID',
      value        => 'intranet',
      trust_level  => 10);
    END;
    /

**Parent topic:** DBMS_MACADM Factor Procedures and Functions

### 17.2 Oracle Database Vault Run-Time PL/SQL Procedures and Functions

Oracle Database Vault provides procedural interfaces to administer Database Vault security options and manage Database Vault security enforcements.

- About Oracle Database Vault Run-Tine PL/SQL Procedures and Functions
  Oracle Database Vault provides a set of PL/SQL procedures and functions that are specific to factors.
- SET_FACTOR Procedure
  The `SET_FACTOR` procedure can be exposed to an application that requires the ability to set factor identities dynamically.
- GET_FACTOR Function
  The `GET_FACTOR` function is exposed to the `DVF` schema to allow the public factor functions to resolve the identity of a factor. The return type is `VARCHAR2`.
- GET_FACTOR_LABEL Function
  The `GET_FACTOR_LABEL` function returns the label for the specified factor when the factor has a label assigned to it for the specified Oracle Label Security policy. The return type is `VARCHAR2`.
- GET_TRUST_LEVEL Function
  The `GET_TRUST_LEVEL` function returns the trust level of the current session identity for the factor requested. The return type is `VARCHAR2`.
- GET_TRUST_LEVEL_FOR_IDENTITY Function
  The `GET_TRUST_LEVEL_FOR_IDENTITY` function returns the trust level for the factor and identity requested. The return type is `VARCHAR2`.
- ROLE_IS_ENABLED Function
  The `ROLE_IS_ENABLED` function returns a boolean value that specifies whether a database role has been enabled. The return type is `BOOLEAN`.

**Parent topic:** Oracle Database Vault Factor APIs

#### 17.2.1 About Oracle Database Vault Run-Tine PL/SQL Procedures and Functions

Oracle Database Vault provides a set of PL/SQL procedures and functions that are specific to factors.

These procedures and functions that expose the logic to validate a DDL command for realm violations and command authorizations. Additional procedures and functions are provided to set the value of a factor (assuming their associated rule sets evaluate to true) (for example, from a Web application), to retrieve the trust level for a session or specific factor identity, and to get the label for a factor identity. These procedures and functions are provided so that a database administrator does not grant the `EXECUTE` privilege on all `DVSYS` package procedures to the general database account population. The procedures and functions expose only the minimum methods that are required. All of these functions and procedures are publicly available for applications that need them.

**Parent topic:** Oracle Database Vault Run-Time PL/SQL Procedures and Functions

#### 17.2.2 SET_FACTOR Procedure

The `SET_FACTOR` procedure can be exposed to an application that requires the ability to set factor identities dynamically.

It wraps the package procedure `DBMS_MACADM.SET_FACTOR`. When a factor has a rule set associated with it for assignment and if the rule set returns true, then the value is set. Normal rule set handling occurs, and the factor value (identity) validation method is called. This procedure is available (to execute) to the general database account population.

##### Syntax

    SET_FACTOR(
      p_factor IN VARCHAR2,
      p_value  IN VARCHAR2);

##### Parameters

Table 17-23 SET_FACTOR Parameters

| Parameter  | Description                                                                                                                                                                                                                                                             |
|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_factor` | Factor name.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` data dictionary view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                                           |
| `p_value`  | Identity value, up to 1024 characters in mixed case.<br>To find the identities for each factor in the current database instance, query the `DBA_DV_IDENTITY` data dictionary view, described in [DBA_DV_IDENTITY View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    EXECUTE SET_FACTOR(''Sector2_ClientID'', ''identity'');

**Parent topic:** Oracle Database Vault Run-Time PL/SQL Procedures and Functions

#### 17.2.3 GET_FACTOR Function

The `GET_FACTOR` function is exposed to the `DVF` schema to allow the public factor functions to resolve the identity of a factor. The return type is `VARCHAR2`.

This function enables the `F$` functions in the `DVF` schema. This function is available (to execute) to the general database account population.

##### Syntax

    GET_FACTOR(
      p_factor IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table 17-24 GET_FACTOR Parameter

| Parameter  | Description                                                                                                                                                                                                   |
|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_factor` | Factor name.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` data dictionary view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Get Client ID Factor Identity',
      rule_expr => 'GET_FACTOR(''Sector2_ClientID'')');
    END;
    /

**Parent topic:** Oracle Database Vault Run-Time PL/SQL Procedures and Functions

#### 17.2.4 GET_FACTOR_LABEL Function

The `GET_FACTOR_LABEL` function returns the label for the specified factor when the factor has a label assigned to it for the specified Oracle Label Security policy. The return type is `VARCHAR2`.

The function returns a label that is merged with the maximum session label for the policy if the policy is configured with Oracle Label Security. The function is available (to execute) to the general database population.

##### Syntax

    GET_FACTOR_LABEL(
      p_factor      IN VARCHAR2,
      p_policy_name IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameters

Table 17-25 GET_FACTOR_LABEL Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_factor`      | Factor name.<br>To find the available factors in the current database instance, query the `DBA_DV_FACTOR` data dictionary view. To find factors that are associated with Oracle Label Security policies, use `DBA_DV_MAC_POLICY_FACTOR`.<br>See [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md) and [DBA_DV_MAC_POLICY_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                            |
| `p_policy_name` | Oracle Label Security policy name.<br>Use the following data dictionary views to find information about policies and factors in the current database instance:<br>• `DBA_DV_MAC_POLICY`: Lists Oracle Label Security policies defined in the current database instance. See [DBA_DV_MAC_POLICY View](oracle-database-vault-data-dictionary-views.md).<br>• `DBA_DV_MAC_POLICY_FACTOR`: Lists the factors that are associated with Oracle Label Security policies for the current database instance. See [DBA_DV_MAC_POLICY_FACTOR View](oracle-database-vault-data-dictionary-views.md).<br>• `DBA_DV_POLICY_LABEL`: Lists the Oracle Label Security label for each factor identifier in the `DBA_DV_IDENTITY` view for each policy. See [DBA_DV_POLICY_LABEL View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Get the ClientID Factor Label',
      rule_expr => 'GET_FACTOR_LABEL(''Sector2_ClientID'', ''Access Locations'')');
    END;
    /

**Parent topic:** Oracle Database Vault Run-Time PL/SQL Procedures and Functions

#### 17.2.5 GET_TRUST_LEVEL Function

The `GET_TRUST_LEVEL` function returns the trust level of the current session identity for the factor requested. The return type is `VARCHAR2`.

This function is available (to execute) to the general database account population. See [Creating and Configuring a Factor Identity](configuring-factors.md) for a listing of the available trust levels.

##### Syntax

    GET_TRUST_LEVEL(
      p_factor IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameter

Table 17-26 GET_TRUST_LEVEL Parameter

| Parameter  | Description                                                                                                                                                                                                   |
|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_factor` | Factor name.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` data dictionary view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Get Client ID Trust Level',
      rule_expr => 'GET_TRUST_LEVEL(''Sector2_ClientID'')');
    END;
    /

**Parent topic:** Oracle Database Vault Run-Time PL/SQL Procedures and Functions

#### 17.2.6 GET_TRUST_LEVEL_FOR_IDENTITY Function

The `GET_TRUST_LEVEL_FOR_IDENTITY` function returns the trust level for the factor and identity requested. The return type is `VARCHAR2`.

This function is available (to execute) to the general database account population. See [Creating and Configuring a Factor Identity](configuring-factors.md) for a listing of the available trust levels.

##### Syntax

    GET_TRUST_LEVEL_FOR_IDENTITY(
      p_factor   IN VARCHAR2,
      p_identity IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameters

Table 17-27 GET_TRUST_LEVEL_FOR_IDENTITY Parameters

| Parameter    | Description                                                                                                                                                                                                                      |
|:-------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_factor`   | Factor name.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).                                    |
| `p_identity` | Identity value.<br>To find the identities for each factor in the current database instance, use the `DBA_DV_IDENTITY` data dictionary view, described in [DBA_DV_IDENTITY View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Get Client ID Identity Trust Level',
      rule_expr => 'GET_TRUST_LEVEL_FOR_IDENTITY(''Sector2_ClientID'', ''identity'')');
    END;
    /

**Parent topic:** Oracle Database Vault Run-Time PL/SQL Procedures and Functions

#### 17.2.7 ROLE_IS_ENABLED Function

The `ROLE_IS_ENABLED` function returns a boolean value that specifies whether a database role has been enabled. The return type is `BOOLEAN`.

This function is available (to execute) to the general database account population.

##### Syntax

    ROLE_IS_ENABLED(
      p_role IN VARCHAR2)
    RETURN BOOLEAN;

##### Parameter

Table 17-28 ROLE_IS_ENABLED Parameter

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_role`  | Database role name to check.<br>To find existing roles, use the following data dictionary views:<br>• `DBA_ROLES`: Finds available roles in the current database instance. See [Oracle Database Reference](../refrn/DBA_ROLES.md).<br>• `DBA_DV_REALM_AUTH`: Finds the authorization of a particular role. See [DBA_DV_REALM View](oracle-database-vault-data-dictionary-views.md).<br>• `DBA_DV_ROLE`: Finds existing secure application roles used in privilege management. See [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check if SYSADM Role Is Enabled',
      rule_expr => 'ROLE_IS_ENABLED(''SYSADM'')');
    END;
    /

**Parent topic:** Oracle Database Vault Run-Time PL/SQL Procedures and Functions

### 17.3 Oracle Database Vault DVF PL/SQL Factor Functions

Oracle Database Vault maintains the `DVF` schema functions when you use the `DBMS_MACADM` PL/SQL package to manage the various factors.

- About Oracle Database Vault DVF PL/SQL Factor Functions
  Oracle Database Vault provides DVF factor-specific functions for frequently used activities.
- F\$AUTHENTICATION_METHOD Function
  The `F$AUTHENTICATION_METHOD` function returns the method of authentication in `VARCHAR2` data type.
- F\$CLIENT_IP Function
  The `F$CLIENT_IP` function returns the IP address of the computer from which the client is connected, in `VARCHAR2` data type.
- F\$DATABASE_DOMAIN Function
  The `F$DATABASE_DOMAIN` function returns the domain of the database as specified in the `DB_DOMAIN` initialization parameter, in `VARCHAR2` data type.
- F\$DATABASE_HOSTNAME Function
  The `F$DATABASE_HOSTNAME` function returns the host name of the computer on which the instance is running, in `VARCHAR2` data type.
- F\$DATABASE_INSTANCE Function
  The `F$DATABASE_INSTANCE` function returns the instance identification number of the current database instance, in `VARCHAR2` data type.
- F\$DATABASE_IP Function
  The `F$DATABASE_IP` function returns the IP address of the computer on which the database instance is running, in `VARCHAR2` data type.
- F\$DATABASE_NAME Function
  The `F$DATABASE_NAME` function returns the name of the database as specified in the `DB_NAME` initialization parameter, in `VARCHAR2` data type.
- F\$DOMAIN Function
  The `F$DOMAIN` function returns a named collection of physical, configuration, or implementation-specific factors in the run-time environment (for example, a networked IT environment or subset of it) that operates at a specific sensitivity level. The return type is `VARCHAR2`.
- F\$DV\$\_CLIENT_IDENTIFIER Function
  The `F$DV$_CLIENT_IDENTIFIER` function returns an Oracle Database Vault client identifier.
- F\$DV\$\_DBLINK_INFO Function
  The `F$DV$_DBLINK_INFO` function returns information about an Oracle Database Vault database link.
- F\$DV\$\_MODULE Function
  The `F$DV$_MODULE` function returns information about an Oracle Database Vault module.
- F\$ENTERPRISE_IDENTITY Function
  The `F$ENTERPRISE_IDENTITY` function returns the enterprise-wide identity for a user, in `VARCHAR2` data type.
- F\$IDENTIFICATION_TYPE Function
  The `F$IDENTIFICATION_TYPE` function returns the way the schema of a user was created in the database. Specifically, it reflects the `IDENTIFIED` clause in the `CREATE`/`ALTER USER` syntax. The return type is `VARCHAR2`.
- F\$LANG Function
  The `F$LANG` function returns the ISO abbreviation for the language name, a shorter form than the existing `LANGUAGE` parameter, for the session of the user. The return type is `VARCHAR2`.
- F\$LANGUAGE Function
  The `F$LANGUAGE` function returns the language and territory currently used by a user session, along with the database character set. The return type is `VARCHAR2`.
- F\$MACHINE Function
  The `F$MACHINE` function returns the computer (host) name for the database client that established the database session. The return type is `VARCHAR2`.
- F\$NETWORK_PROTOCOL Function
  The `F$NETWORK_PROTOCOL` function returns the network protocol being used for communication, as specified in the `PROTOCOL`=`protocol` portion of the connect string. The return type is `VARCHAR2`.
- F\$PROXY_ENTERPRISE_IDENTITY Function
  The `F$PROXY_ENTERPRISE_IDENTITY` function returns the Oracle Internet Directory distinguished name (DN) when the proxy user is an enterprise user. The return type is `VARCHAR2`.
- F\$PROXY_USER Function
  The `F$PROXY_USER` function returns the name of a proxy user.
- F\$SESSION_USER Function
  The `F$SESSION_USER` function returns the database user name by which the current user is authenticated. This value remains the same throughout the session. The return type is `VARCHAR2`.

**Parent topic:** Oracle Database Vault Factor APIs

#### 17.3.1 About Oracle Database Vault DVF PL/SQL Factor Functions

Oracle Database Vault provides DVF factor-specific functions for frequently used activities.

In addition to the functions and procedures made available from the `DVSYS` schema, the `DVF` schema contains a single function for each factor defined in the system.

The functions are then available to the general database account population through PL/SQL functions and standard SQL. This enables factors to be used in Oracle Label Security, Oracle Virtual Private Database (VPD), and so on.

Typically, you can incorporate these functions into rule expressions. For example:

The functions are then available to the general database account population through PL/SQL functions and standard SQL. This enables factors to be used in Oracle Label Security, Oracle Virtual Private Database (VPD), and so on.

Typically, you can incorporate these functions into rule expressions. For example:

    BEGIN
     DBMS_MACADM.CREATE_RULE(
     rule_name => 'Not Internal DBA',
     rule_expr => 'DVF.F$SESSION_USER NOT IN (''JSMTIH'', ''TBROWN'')');
    END;
    /

To find the value of a factor function, select from the `DUAL` system table. For example:

    SELECT DVF.F$SESSION_USER FROM DUAL;

    F$SESSION_USER
    ------------------------------------------------
    SEC_ADMIN_OWEN

The name of the factor itself is case-insensitive. For example, the following statements return the same result

    select dvf.f$session_user from dual;

    SELECT DVF.F$SESSION_USER FROM DUAL;

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.2 F\$AUTHENTICATION_METHOD Function

The `F$AUTHENTICATION_METHOD` function returns the method of authentication in `VARCHAR2` data type.

In the list that follows, the type of user is followed by the method returned:

- Password-authenticated enterprise user, local database user, or `SYSDBA`/`SYSOPER` using Password File; proxy with user name using password: `PASSWORD`

- Kerberos-authenticated enterprise or external user: `KERBEROS`

- Transport Layer Security (TLS)-authenticated enterprise or external user: `SSL`

- Radius-authenticated external user: `RADIUS`

- Operating system-authenticated external user or `SYSDBA`/`SYSOPER`: `OS`

- DCE-authenticated external user: `DCE`

- Proxy with certificate, distinguished name (DN), or user name without using password: `NONE`

You can use `IDENTIFICATION_TYPE` to distinguish between external and enterprise users when the authentication method is Password, Kerberos, or TLS.

##### Syntax

    DVF.F$AUTHENTICATION_METHOD ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check TLS Authentication Method',
      rule_expr => 'DVF.F$AUTHENTICATION_METHOD = ''SSL''');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.3 F\$CLIENT_IP Function

The `F$CLIENT_IP` function returns the IP address of the computer from which the client is connected, in `VARCHAR2` data type.

##### Syntax

    DVF.F$CLIENT_IP ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

The following example shows how to use `DVF.F$CLIENT_IP` in a rule creation statement. Note that you can only enter one IP address, not a range of IP addresses.

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Client IP Address',
      rule_expr => 'DVF.F$CLIENT_IP = ''192.0.2.10''');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.4 F\$DATABASE_DOMAIN Function

The `F$DATABASE_DOMAIN` function returns the domain of the database as specified in the `DB_DOMAIN` initialization parameter, in `VARCHAR2` data type.

##### Syntax

    DVF.F$DATABASE_DOMAIN ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Client Database Domain',
      rule_expr => 'DVF.F$DATABASE_DOMAIN NOT IN (''EXAMPLE'', ''YOURDOMAIN'')');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.5 F\$DATABASE_HOSTNAME Function

The `F$DATABASE_HOSTNAME` function returns the host name of the computer on which the instance is running, in `VARCHAR2` data type.

##### Syntax

    DVF.F$DATABASE_HOSTNAME ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Host Name',
      rule_expr => 'DVF.F$DATABASE_HOSTNAME IN (''SHOBEEN'', ''MAU'')');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.6 F\$DATABASE_INSTANCE Function

The `F$DATABASE_INSTANCE` function returns the instance identification number of the current database instance, in `VARCHAR2` data type.

##### Syntax

    DVF.F$DATABASE_INSTANCE ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Database Instance ID',
      rule_expr => 'DVF.F$DATABASE_INSTANCE = ''SALES_DB''');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.7 F\$DATABASE_IP Function

The `F$DATABASE_IP` function returns the IP address of the computer on which the database instance is running, in `VARCHAR2` data type.

##### Syntax

    DVF.F$DATABASE_IP ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Database IP address',
      rule_expr => 'DVF.F$DATABASE_IP = ''192.0.2.5''');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.8 F\$DATABASE_NAME Function

The `F$DATABASE_NAME` function returns the name of the database as specified in the `DB_NAME` initialization parameter, in `VARCHAR2` data type.

##### Syntax

    DVF.F$DATABASE_NAME ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Database DB_NAME Name',
      rule_expr => 'DVF.F$DATABASE_NAME = ''ORCL''');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.9 F\$DOMAIN Function

The `F$DOMAIN` function returns a named collection of physical, configuration, or implementation-specific factors in the run-time environment (for example, a networked IT environment or subset of it) that operates at a specific sensitivity level. The return type is `VARCHAR2`.

You can identify a domain using factors such as host name, IP address, and database instance names of the Oracle Database Vault nodes in a secure access path to the database. Each domain can be uniquely determined using a combination of the factor identifiers that identify the domain. You can use these identifying factors and possibly additional factors to define the Maximum Security Label within the domain. This restricts data access and commands, depending on the physical factors about the Oracle Database Vault session. Example domains of interest may be Corporate Sensitive, Internal Public, Partners, and Customers.

##### Syntax

    DVF.F$DOMAIN ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Domain',
      rule_expr => 'DVF.F$DOMAIN = ''EXAMPLE.COM''');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.10 F\$DV\$\_CLIENT_IDENTIFIER Function

The `F$DV$_CLIENT_IDENTIFIER` function returns an Oracle Database Vault client identifier.

##### Syntax

    DVF.F$DV$_CLIENT_IDENTIFIER ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
      DBMS_MACADM.CREATE_RULE(
       rule_name => 'Check Database Vault Client Identifiers',
       rule_expr => 'DVF.F$DV$_CLIENT_IDENTIFIER = ''14903BUA765454'';
    END;/

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.11 F\$DV\$\_DBLINK_INFO Function

The `F$DV$_DBLINK_INFO` function returns information about an Oracle Database Vault database link.

##### Syntax

    DVF.F$DV$_DBLINK_INFO ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
      DBMS_MACADM.CREATE_RULE(
       rule_name => 'Check Database Vault database link info',
       rule_expr => 'DVF.F$DV$_DBLINK_INFO = ''SOURCE_GLOBAL_NAME=SALES.US.EXAMPLE.COM, DBLINK_NAME=PDB2_LINK, SOURCE_AUDIT_SESSIONID=200057'';
    END;/

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.12 F\$DV\$\_MODULE Function

The `F$DV$_MODULE` function returns information about an Oracle Database Vault module.

##### Syntax

    DVF.F$DV$_MODULE ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
      DBMS_MACADM.CREATE_RULE(
       rule_name => 'Check Database Vault modules',
       rule_expr => 'DVF.F$DV$_MODULE = ''SQL*Plus'';
    END;/

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.13 F\$ENTERPRISE_IDENTITY Function

The `F$ENTERPRISE_IDENTITY` function returns the enterprise-wide identity for a user, in `VARCHAR2` data type.

- For enterprise users: the Oracle Internet Directory DN.

- For external users: the external identity (Kerberos principal name, Radius and DCE schema names, operating system user name, certificate DN).

- For local users and `SYSDBA`/`SYSOPER` logins: NULL.

The value of the attribute differs by proxy method:

- For a proxy with DN: the Oracle Internet Directory DN of the client.

- For a proxy with certificate: the certificate DN of the client for external users; the Oracle Internet Directory DN for global users.

- For a proxy with user name: the Oracle Internet Directory DN if the client is an enterprise user; NULL if the client is a local database user.

##### Syntax

    DVF.F$ENTERPRISE_IDENTITY ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check User Enterprise Identity',
      rule_expr => 'DVF.F$ENTERPRISE_IDENTITY NOT IN (''JSMITH'', ''TSMITH'')');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.14 F\$IDENTIFICATION_TYPE Function

The `F$IDENTIFICATION_TYPE` function returns the way the schema of a user was created in the database. Specifically, it reflects the `IDENTIFIED` clause in the `CREATE`/`ALTER USER` syntax. The return type is `VARCHAR2`.

In the list that follows, the syntax used during schema creation is followed by the identification type returned:

- `IDENTIFIED BY` `password``:` `LOCAL`

- `IDENTIFIED EXTERNALLY``:` `EXTERNAL`

- `IDENTIFIED GLOBALLY``:` `GLOBAL SHARED`

- `IDENTIFIED GLOBALLY` `AS DN: GLOBAL PRIVATE`

##### Syntax

    DVF.F$IDENTIFICATION_TYPE ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check User Schema Creation Type',
      rule_expr => 'DVF.F$IDENTIFICATION_TYPE = ''GLOBAL SHARED''');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.15 F\$LANG Function

The `F$LANG` function returns the ISO abbreviation for the language name, a shorter form than the existing `LANGUAGE` parameter, for the session of the user. The return type is `VARCHAR2`.

See [Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md) for a listing of supported languages for Oracle Database.

##### Syntax

    DVF.F$LANG ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check ISO Abbreviated Language Name',
      rule_expr => 'DVF.F$LANG IN (''EN'', ''DE'', ''FR'')');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.16 F\$LANGUAGE Function

The `F$LANGUAGE` function returns the language and territory currently used by a user session, along with the database character set. The return type is `VARCHAR2`.

The return type is in the following format:

`language_territory.characterset`

See [Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md) for a listing of supported languages and territories for Oracle Database.

##### Syntax

    DVF.F$LANGUAGE ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Session Language and Territory',
      rule_expr => 'DVF.F$LANGUAGE = ''AMERICAN_AMERICA.WE8ISO8859P1''');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.17 F\$MACHINE Function

The `F$MACHINE` function returns the computer (host) name for the database client that established the database session. The return type is `VARCHAR2`.

##### Syntax

    DVF.F$MACHINE ()
    RETURN VARCHAR2;

##### Parameter

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Client Computer Host Name',
      rule_expr => 'DVF.F$MACHINE NOT IN (''SHOBEEN'', ''SEBASTIAN'')');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.18 F\$NETWORK_PROTOCOL Function

The `F$NETWORK_PROTOCOL` function returns the network protocol being used for communication, as specified in the `PROTOCOL`=`protocol` portion of the connect string. The return type is `VARCHAR2`.

##### Syntax

    DVF.F$NETWORK_PROTOCOL ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Network Protocol',
      rule_expr => 'DVF.F$NETWORK_PROTOCOL = ''TCP''');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.19 F\$PROXY_ENTERPRISE_IDENTITY Function

The `F$PROXY_ENTERPRISE_IDENTITY` function returns the Oracle Internet Directory distinguished name (DN) when the proxy user is an enterprise user. The return type is `VARCHAR2`.

##### Syntax

    DVF.F$PROXY_ENTERPRISE_IDENTITY ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Get OID DN of Enterprise User',
      rule_expr => 'DVF.F$PROXY_ENTERPRISE_IDENTITY = ''cn=Provisioning Admins''');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.20 F\$PROXY_USER Function

The `F$PROXY_USER` function returns the name of a proxy user.

##### Syntax

    DVF.PROXY_USER ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
      DBMS_MACADM.CREATE_RULE(
       rule_name => 'Check Proxy Users',
       rule_expr => 'DVF.PROXY_USER NOT IN (''ECHICHESTER'', ''PFITCH'')');
    END;/

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions

#### 17.3.21 F\$SESSION_USER Function

The `F$SESSION_USER` function returns the database user name by which the current user is authenticated. This value remains the same throughout the session. The return type is `VARCHAR2`.

##### Syntax

    DVF.F$SESSION_USER ()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Check Database User Name',
      rule_expr => 'DVF.F$SESSION_USER IN (''JSMITH'', ''TSMITH'')');
    END;
    /

**Parent topic:** Oracle Database Vault DVF PL/SQL Factor Functions
