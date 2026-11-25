You can use the `DBMS_MACADM` PL/SQL package to manage Oracle Label Security labels and policies in Oracle Database Vault.

- CREATE_MAC_POLICY Procedure
  The `CREATE_MAC_POLICY` procedure specifies the algorithm to merge labels when computing the label for a factor, or the Oracle Label Security Session label.
- CREATE_POLICY_LABEL Procedure
  The `CREATE_POLICY_LABEL` procedure labels an identity within an Oracle Label Security policy.
- DELETE_MAC_POLICY_CASCADE Procedure
  The `DELETE_MAC_POLICY_CASCADE` procedure deletes all Oracle Database Vault objects related to an Oracle Label Security policy.
- DELETE_POLICY_FACTOR Procedure
  The `DELETE_POLICY_FACTOR` procedure removes the factor from contributing to the Oracle Label Security label.
- DELETE_POLICY_LABEL Procedure
  The `DELETE_POLICY_LABEL` procedure removes the label from an identity within an Oracle Label Security policy.
- UPDATE_MAC_POLICY Procedure
  The `UPDATE_MAC_POLICY` procedure specifies the algorithm to merge labels when computing the label for a factor, or the Oracle Label Security Session label.

**Related Topics**

- [Integrating Oracle Database Vault with Other Oracle Products](integrating-database-vault-with-other-oracle-products.md)
- [Oracle Database Vault Utility APIs](oracle-database-vault-utility-apis.md)

### 19.1 CREATE_MAC_POLICY Procedure

The `CREATE_MAC_POLICY` procedure specifies the algorithm to merge labels when computing the label for a factor, or the Oracle Label Security Session label.

#### Syntax

    DBMS_MACADM.CREATE_MAC_POLICY(
      policy_name  IN VARCHAR2,
      algorithm    IN VARCHAR2);

#### Parameters

Table 19-1 CREATE_MAC_POLICY Parameters

| Parameter     | Description                                                                                                                                                                                                                                                        |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Name of an existing policy.<br>To find existing policies in the current database instance, query the `DBA_DV_MAC_POLICY` view, described in [DBA_DV_MAC_POLICY View](oracle-database-vault-data-dictionary-views.md).                                              |
| `algorithm`   | Merge algorithm for cases when Oracle Label Security has merged two labels. Enter the code listed in Table 19-2 that corresponds to the merge algorithm you want. For example, enter `HUU` to if you want to select the Maximum Level/Union/Union merge algorithm. |

Table 19-2 Oracle Label Security Merge Algorithm Codes

| Code  | Value                                   |
|:------|:----------------------------------------|
| `HUU` | Maximum Level/Union/Union               |
| `HIU` | Maximum Level/Intersection/Union        |
| `HMU` | Maximum Level/Minus/Union               |
| `HNU` | Maximum Level/Null/Union                |
| `HUI` | Maximum Level/Union/Intersection        |
| `HII` | Maximum Level/Intersection/Intersection |
| `HMI` | Maximum Level/Minus/Intersection        |
| `HNI` | Maximum Level/Null/Intersection         |
| `HUM` | Maximum Level/Union/Minus               |
| `HIM` | Maximum Level/Intersection/Minus        |
| `HMM` | Maximum Level/Minus/Minus               |
| `HNM` | Maximum Level/Null/Minus                |
| `HUN` | Maximum Level/Union/Null                |
| `HIN` | Maximum Level/Intersection/Null         |
| `HMN` | Maximum Level/Minus/Null                |
| `HNN` | Maximum Level/Null/Null                 |
| `LUU` | Minimum Level/Union/Union               |
| `LIU` | Minimum Level/Intersection/Union        |
| `LMU` | Minimum Level/Minus/Union               |
| `LNU` | Minimum Level/Null/Union                |
| `LUI` | Minimum Level/Union/Intersection        |
| `LII` | Minimum Level/Intersection/Intersection |
| `LMI` | Minimum Level/Minus/Intersection        |
| `LNI` | Minimum Level/Null/Intersection         |
| `LUM` | Minimum Level/Union/Minus               |
| `LIM` | Minimum Level/Intersection/Minus        |
| `LMM` | Minimum Level/Minus/Minus               |
| `LNM` | Minimum Level/Null/Minus                |
| `LUN` | Minimum Level/Union/Null                |
| `LIN` | Minimum Level/Intersection/Null         |
| `LMN` | Minimum Level/Minus/Null                |
| `LNN` | Minimum Level/Null/Null                 |

#### Example

    BEGIN
     DBMS_MACADM.CREATE_MAC_POLICY(
      policy_name  => 'Access Locations',
      algorithm    => 'HUU');
    END;
    /

**Parent topic:** Oracle Database Vault Oracle Label Security APIs

### 19.2 CREATE_POLICY_LABEL Procedure

The `CREATE_POLICY_LABEL` procedure labels an identity within an Oracle Label Security policy.

#### Syntax

    DBMS_MACADM.CREATE_POLICY_LABEL(
      identity_factor_name   IN VARCHAR2,
      identity_factor_value  IN VARCHAR2,
      policy_name            IN VARCHAR2,
      label                  IN VARCHAR2);

#### Parameters

Table 19-3 CREATE_POLICY_LABEL Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `identity_factor_name`  | Name of the factor being labeled.<br>To find existing factors in the current database instance, query the `DBA_DV_FACTOR` view, described in [DBA_DV_FACTOR View](oracle-database-vault-data-dictionary-views.md).<br>To find factors that are associated with Oracle Label Security policies, use `DBA_DV_MAC_POLICY_FACTOR`, described in [DBA_DV_MAC_POLICY_FACTOR View](oracle-database-vault-data-dictionary-views.md). |
| `identity_factor_value` | Value of identity for the factor being labeled.<br>To find the identities of existing factors in the current database instance, query the `DBA_DV_IDENTITY` view, described in [DBA_DV_IDENTITY View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                       |
| `policy_name`           | Name of an existing policy.<br>To find existing policies in the current database instance, query the `DBA_DV_MAC_POLICY` view, described in [DBA_DV_MAC_POLICY View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                        |
| `label`                 | Oracle Label Security label name.<br>To find existing policy labels for factor identifiers, query the `DBA_DV_POLICY_LABEL` view, described in [DBA_DV_POLICY_LABEL View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                   |

#### Example

    BEGIN
     DBMS_MACADM.CREATE_POLICY_LABEL(
      identity_factor_name   => 'App_Host_Name',
      identity_factor_value  => 'Sect2_Fin_Apps',
      policy_name            => 'Access Locations',
      label                  => 'Sensitive');
    END;
    /

**Parent topic:** Oracle Database Vault Oracle Label Security APIs

### 19.3 DELETE_MAC_POLICY_CASCADE Procedure

The `DELETE_MAC_POLICY_CASCADE` procedure deletes all Oracle Database Vault objects related to an Oracle Label Security policy.

#### Syntax

    DBMS_MACADM.DELETE_MAC_POLICY_CASCADE(
      policy_name  IN VARCHAR2);

#### Parameters

Table 19-4 DELETE_MAC_POLICY_CASCADE Parameter

| Parameter     | Description                                                                                                                                                                                                           |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Name of an existing policy.<br>To find existing policies in the current database instance, query the `DBA_DV_MAC_POLICY` view, described in [DBA_DV_MAC_POLICY View](oracle-database-vault-data-dictionary-views.md). |

#### Example

    EXEC DBMS_MACADM.DELETE_MAC_POLICY_CASCADE('Access Locations');

**Parent topic:** Oracle Database Vault Oracle Label Security APIs

### 19.4 DELETE_POLICY_FACTOR Procedure

The `DELETE_POLICY_FACTOR` procedure removes the factor from contributing to the Oracle Label Security label.

#### Syntax

    DBMS_MACADM.DELETE_POLICY_FACTOR(
      policy_name  IN VARCHAR2,
      factor_name  IN VARCHAR2);

#### Parameters

Table 19-5 DELETE_POLICY_FACTOR Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                 |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Name of an existing policy.<br>To find existing policies in the current database instance, query the `DBA_DV_MAC_POLICY` view, described in [DBA_DV_MAC_POLICY View](oracle-database-vault-data-dictionary-views.md).                                                       |
| `factor_name` | Name of factor associated with the Oracle Label Security label.<br>To find factors that are associated with Oracle Label Security policies, query `DBA_DV_MAC_POLICY_FACTOR`, described in [DBA_DV_MAC_POLICY_FACTOR View](oracle-database-vault-data-dictionary-views.md). |

#### Example

    BEGIN
     DBMS_MACADM.DELETE_POLICY_FACTOR(
      policy_name  => 'Access Locations',
      factor_name  => 'App_Host_Name');
    END;
    /

**Parent topic:** Oracle Database Vault Oracle Label Security APIs

### 19.5 DELETE_POLICY_LABEL Procedure

The `DELETE_POLICY_LABEL` procedure removes the label from an identity within an Oracle Label Security policy.

#### Syntax

    DBMS_MACADM.DELETE_POLICY_LABEL(
      identity_factor_name   IN VARCHAR2,
      identity_factor_value  IN VARCHAR2,
      policy_name            IN VARCHAR2,
      label                  IN VARCHAR2);

#### Parameters

Table 19-6 DELETE_POLICY_LABEL Parameters

| Parameter               | Description                                                                                                                                                                                                                                                                                |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `identity_factor_name`  | Name of the factor that was labeled.<br>To find existing factors in the current database instance that are associated with Oracle Label Security policies, query `DBA_DV_MAC_POLICY_FACTOR`, described in [DBA_DV_MAC_POLICY_FACTOR View](oracle-database-vault-data-dictionary-views.md). |
| `identity_factor_value` | Value of identity for the factor that was labeled.<br>To find the identities of existing factors in the current database instance, query the `DBA_DV_IDENTITY` view, described in [DBA_DV_IDENTITY View](oracle-database-vault-data-dictionary-views.md).                                  |
| `policy_name`           | Name of an existing policy.<br>To find existing policies in the current database instance, query the `DBA_DV_MAC_POLICY` view, described in [DBA_DV_MAC_POLICY View](oracle-database-vault-data-dictionary-views.md).                                                                      |
| `label`                 | Oracle Label Security label name.<br>To find existing policy labels for factor identifiers, query the `DBA_DV_POLICY_LABEL` view, described in [DBA_DV_POLICY_LABEL View](oracle-database-vault-data-dictionary-views.md).                                                                 |

#### Example

    BEGIN
     DBMS_MACADM.DELETE_POLICY_LABEL(
      identity_factor_name   => 'App_Host_Name',
      identity_factor_value  => 'Sect2_Fin_Apps',
      policy_name            => 'Access Locations',
      label                  => 'Sensitive');
    END;
    /

**Parent topic:** Oracle Database Vault Oracle Label Security APIs

### 19.6 UPDATE_MAC_POLICY Procedure

The `UPDATE_MAC_POLICY` procedure specifies the algorithm to merge labels when computing the label for a factor, or the Oracle Label Security Session label.

#### Syntax

    DBMS_MACADM.UPDATE_MAC_POLICY(
      policy_name  IN VARCHAR2,
      algorithm    IN VARCHAR2);

#### Parameters

Table 19-7 UPDATE_MAC_POLICY

| Parameter     | Description                                                                                                                                                                                                           |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `policy_name` | Name of an existing policy.<br>To find existing policies in the current database instance, query the `DBA_DV_MAC_POLICY` view, described in [DBA_DV_MAC_POLICY View](oracle-database-vault-data-dictionary-views.md). |
| `algorithm`   | Merge algorithm for cases when Oracle Label Security has merged two labels. See Table 19-2 for listing of the available algorithms.                                                                                   |

#### Example

    BEGIN
     DBMS_MACADM.UPDATE_MAC_POLICY(
      policy_name  => 'Access Locations',
      algorithm    => 'LUI');
    END;
    /

**Parent topic:** Oracle Database Vault Oracle Label Security APIs
