The `DBMS_MACADM` and `DBMS_MACSEC_ROLES` PL/SQL packages manage Database Vault secure application roles.

- DBMS_MACADM Secure Application Role Procedures
  The `DBMS_MACADM` package creates, renames, assigns, unassigns, updates, and deletes Oracle Database Vault secure application roles.
- DBMS_MACSEC_ROLES Secure Application Role Procedure and Function
  The `DBMS_MACSEC_ROLES` package checks the authorization for users and sets Oracle Database Vault secure application roles.

**Related Topics**

- [Configuring Secure Application Roles for Oracle Database Vault](configuring-secure-application-roles-for-oracle-database-vault.md)
- [Oracle Database Vault Utility APIs](oracle-database-vault-utility-apis.md)

### 18.1 DBMS_MACADM Secure Application Role Procedures

The `DBMS_MACADM` package creates, renames, assigns, unassigns, updates, and deletes Oracle Database Vault secure application roles.

- CREATE_ROLE Procedure
  The `CREATE_ROLE` procedure creates an Oracle Database Vault secure application role.
- DELETE_ROLE Procedure
  The `DELETE_ROLE` procedure deletes an Oracle Database Vault secure application role.
- RENAME_ROLE Procedure
  The `RENAME_ROLE` procedure renames an Oracle Database Vault secure application role. The name change takes effect everywhere the role is used.
- UPDATE_ROLE Procedure
  The `UPDATE_ROLE` procedure updates a Oracle Database Vault secure application role.

**Parent topic:** Oracle Database Vault Secure Application Role APIs

#### 18.1.1 CREATE_ROLE Procedure

The `CREATE_ROLE` procedure creates an Oracle Database Vault secure application role.

##### Syntax

    DBMS_MACADM.CREATE_ROLE(
      role_name      IN VARCHAR2,
      enabled        IN VARCHAR2,
      rule_set_name  IN VARCHAR2);

##### Parameters

Table 18-1 CREATE_ROLE Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                             |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `role_name`     | Role name, up to 128 characters, with no spaces. In a multitenant environment, prepend the role name with `c##` or `C##`.<br>To find existing secure application roles in the current database instance, query the `DBA_DV_ROLE` view, described in [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md). |
| `enabled`       | `DBMS_MACUTL.G_YES` (Yes) makes the role available for enabling; `DBMS_MACUTL.G_NO` (No) prevents the role from being enabled. The default is `DBMS_MACUTL.G_YES`.                                                                                                                                                      |
| `rule_set_name` | Name of rule set to determine whether this secure application can be enabled.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md).                                                    |

##### Example

    BEGIN
     DBMS_MACADM.CREATE_ROLE(
      role_name      => 'Sector2_APP_MGR',
      enabled        => DBMS_MACUTL.G_YES,
      rule_set_name  => 'Check App2 Access');
    END;
    /

**Parent topic:** DBMS_MACADM Secure Application Role Procedures

#### 18.1.2 DELETE_ROLE Procedure

The `DELETE_ROLE` procedure deletes an Oracle Database Vault secure application role.

##### Syntax

    DBMS_MACADM.DELETE_ROLE(
      role_name IN VARCHAR2);

##### Parameters

Table 18-2 DELETE_ROLE Parameter

| Parameter   | Description                                                                                                                                                                                              |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `role_name` | Role name.<br>To find existing secure application roles in the current database instance, query the `DBA_DV_ROLE` view, described in [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    EXEC DBMS_MACADM.DELETE_ROLE('SECT2_APP_MGR');

**Parent topic:** DBMS_MACADM Secure Application Role Procedures

#### 18.1.3 RENAME_ROLE Procedure

The `RENAME_ROLE` procedure renames an Oracle Database Vault secure application role. The name change takes effect everywhere the role is used.

##### Syntax

    DBMS_MACADM.RENAME_ROLE(
      role_name      IN VARCHAR2,
      new_role_name  IN VARCHAR2);

##### Parameters

Table 18-3 RENAME_ROLE Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                               |
|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `role_name`     | Current role name.<br>To find existing secure application roles in the current database instance, query the `DBA_DV_ROLE` view, described in [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md).                                                                                                          |
| `new_role_name` | Role name, up to 128 characters, with no spaces. Ensure that this name follows the standard Oracle naming conventions for role creation described in [Oracle Database SQL Language Reference](../sqlrf/Database-Object-Names-and-Qualifiers.md). In a multitenant environment, prepend the role name with `c##` or `C##`. |

##### Example

    BEGIN
     DBMS_MACADM.RENAME_ROLE(
      role_name      => 'SECT2_APP_MGR',
      new_role_name  => 'SECT2_SYSADMIN');
    END;
    /

**Parent topic:** DBMS_MACADM Secure Application Role Procedures

#### 18.1.4 UPDATE_ROLE Procedure

The `UPDATE_ROLE` procedure updates a Oracle Database Vault secure application role.

##### Syntax

    DBMS_MACADM.UPDATE_ROLE(
      role_name      IN VARCHAR2,
      enabled        IN VARCHAR2,
      rule_set_name  IN VARCHAR2);

##### Parameters

Table 18-4 UPDATE_ROLE Parameters

| Parameter       | Description                                                                                                                                                                                                                                                          |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `role_name`     | Role name.<br>To find existing secure application roles in the current database instance, query the `DBA_DV_ROLE` view, described in [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md).                                                             |
| `enabled`       | `DBMS_MACUTL.G_YES` (Yes) makes the role available for enabling; `DBMS_MACUTL.G_NO` (No) prevents the role from being enabled.<br>The default for `enabled` is the previously set value, which you can find by querying the `DBA_DV_ROLE` data dictionary view.      |
| `rule_set_name` | Name of rule set to determine whether this secure application can be enabled.<br>To find existing rule sets in the current database instance, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    BEGIN
     DBMS_MACADM.UPDATE_ROLE(
      role_name      => 'SECT2_SYSADMIN',
      enabled        => DBMS_MACUTL.G_YES,
      rule_set_name  => 'System Access Controls');
    END;
    /

**Parent topic:** DBMS_MACADM Secure Application Role Procedures

### 18.2 DBMS_MACSEC_ROLES Secure Application Role Procedure and Function

The `DBMS_MACSEC_ROLES` package checks the authorization for users and sets Oracle Database Vault secure application roles.

The `DBMS_MACSEC_ROLES` package is available to all users.

- CAN_SET_ROLE Function
  The `CAN_SET_ROLE` function checks if the user invoking the method is authorized to use an Oracle Database Vault secure application role.
- SET_ROLE Procedure
  The `SET_ROLE` procedure issues the `SET ROLE` PL/SQL statement for specified roles.

**Parent topic:** Oracle Database Vault Secure Application Role APIs

#### 18.2.1 CAN_SET_ROLE Function

The `CAN_SET_ROLE` function checks if the user invoking the method is authorized to use an Oracle Database Vault secure application role.

The authorization is determined by checking the rule set associated with the role. The return type is `BOOLEAN`.

##### Syntax

    DBMS_MACSEC_ROLES.CAN_SET_ROLE(
      p_role IN VARCHAR2)
    RETURN BOOLEAN;

##### Parameters

Table 18-5 CAN_SET_ROLE Parameter

| Parameter | Description                                                                                                                                                                                              |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_role`  | Role name.<br>To find existing secure application roles in the current database instance, query the `DBA_DV_ROLE` view, described in [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    SET SERVEROUTPUT ON
    BEGIN
     IF DBMS_MACSEC_ROLES.CAN_SET_ROLE('SECTOR2_APP_MGR')
      THEN DBMS_OUTPUT.PUT_LINE('''SECTOR2_APP_MGR'' can be enabled.');
     END IF;
    END;
    /

**Parent topic:** DBMS_MACSEC_ROLES Secure Application Role Procedure and Function

#### 18.2.2 SET_ROLE Procedure

The `SET_ROLE` procedure issues the `SET ROLE` PL/SQL statement for specified roles.

This procedure includes both Oracle Database Vault secure application roles and regular Oracle Database roles in its checking process.

This procedure sets an Oracle Database Vault secure application role only if the rule set that is associated with the role evaluates to true. Before `SET ROLE` is issued, the `CAN_SET_ROLE` method is called to check the rule set associated with the role. Run-time rule set behavior such as auditing, failure processing, and event handling occur during this process.

The `SET_ROLE` procedure is available to the general database account population.

##### Syntax

    DBMS_MACSEC_ROLES.SET_ROLE(
      p_role IN VARCHAR2);

##### Parameters

Table 18-6 SET_ROLE Parameter

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_role`  | Role names. You can enter multiple roles, separated by commas (`,`), including secure application roles and regular roles.<br>To find existing secure application roles in the current database instance, query the `DBA_DV_ROLE` view, described in [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md).<br>To find all of the existing roles in the database, query the `DBA_ROLES` data dictionary view, described in [Oracle Database Reference](../refrn/DBA_ROLES.md). |

##### Example

    EXEC DBMS_MACSEC_ROLES.SET_ROLE('SECTOR2_APP_MGR, APPS_MGR');

You can enter the name of the role in any case (for example, `Sector2_APP_MGR`).

**Parent topic:** DBMS_MACSEC_ROLES Secure Application Role Procedure and Function
